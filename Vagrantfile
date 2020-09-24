# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
# Run this first: vagrant plugin install vagrant-vbguest
VAGRANTFILE_API_VERSION = "2"


# Check if we have the ssh keyfile
if ENV['AWS_KEYFILE'] && !File.exist?('aws-key.pem')
  FileUtils.cp(ENV['AWS_KEYFILE'], 'aws-key.pem')
end

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.


  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "centos/7"
  config.vm.box_check_update = false

  config.vm.define :control do |control|
     control.vm.host_name = "control.dev.loc"
     control.vm.provision "ansible_local" do |ansible|
         ansible.playbook = "setup.yml"
     end
  end

end
