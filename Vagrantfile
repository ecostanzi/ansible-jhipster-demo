Vagrant.configure(2) do |config|
  
  config.vm.box = "centos/7"

  config.ssh.insert_key = false

  config.vm.network "forwarded_port", guest: 8080, host: 8080
  config.vm.network "forwarded_port", guest: 3306, host: 3307

end
