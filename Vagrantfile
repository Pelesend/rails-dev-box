Vagrant::Config.run do |config|
  config.vm.box       = 'precise32'
  config.vm.box_url   = 'http://files.vagrantup.com/precise32.box'
  config.vm.host_name = 'rails-dev-box'

  config.vm.forward_port 3000, 3000

  Vagrant.configure("2") do |config|
    config.vm.synced_folder "/Users/kiote/www/", "/home/vagrant/www"
  end

  config.vm.provision :puppet,
    :manifests_path => 'puppet/manifests',
    :module_path    => 'puppet/modules'

  config.vm.provision :shell, inline: <<-EOF
sudo -u vagrant -H bash -l -c 'rvm autolibs enable'
sudo -u vagrant -H bash -l -c 'rvm install 1.9.3'
  EOF
end
