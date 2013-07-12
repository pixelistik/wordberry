Vagrant::Config.run do |config|
	# Every Vagrant virtual environment requires a box to build off of.
	config.vm.box = "precise32"

	# The url from where the 'config.vm.box' box will be fetched if it
	# doesn't already exist on the user's system.
	config.vm.box_url = "http://files.vagrantup.com/precise32.box"

	# Fix DNS, see http://serverfault.com/a/496612
	config.vm.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]

	# Forward a port from the guest to the host, which allows for outside
	# computers to access the VM, whereas host only networking does not.
	config.vm.forward_port 80, 8080

	# Share an additional folder to the guest VM. The first argument is
	# an identifier, the second is the path on the guest to mount the
	# folder, and the third is the path on the host to the actual folder.
	#config.vm.share_folder "www", "/var/www", ".", :owner => "www-data", :group => "www-data"

	config.vm.provision :ansible do |ansible|
		# point Vagrant at the location of your playbook you want to run
		ansible.playbook = "wordberry.yaml"

		# the Vagrant VM will be put in this host group change this should
		# match the host group in your playbook you want to test
		ansible.hosts = "local"
	end
end
