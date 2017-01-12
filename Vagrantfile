Vagrant.configure("2") do |config|

  config.vm.box = "bento/ubuntu-16.04"

  config.vm.provider "virtualbox" do |v|
      v.memory = 4096
      v.cpus = 2
  end

  # TODO: ideally this would work, but the ownership
  # of the dest folder needs to be sonarqube, which
  # doesn't exist yet at this point.
  #config.vm.synced_folder "/Users/timw/sonar-plugins",
  #  "/opt/sonarqube/sonarqube-6.2/extensions/plugins",
  #  create: true

  #
  # Use ansible_local on the guest, so you can
  # run this on like...Windows..
  #
  config.vm.provision "ansible_local" do |ansible|
    ansible.verbose = "v"
    ansible.playbook = "provisioning/playbook.yml"
  end

  # expose the webapp port (9062 for sonarqube v6.2)
  config.vm.network "forwarded_port", guest: 9000, host: 9062

end
