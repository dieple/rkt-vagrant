Vagrant.configure('2') do |config|
    # grab Ubuntu 14.10 official image
    config.vm.box = "ubuntu/trusty64" # Ubuntu 14.10

    # fix issues with slow dns http://serverfault.com/a/595010
    config.vm.provider :virtualbox do |vb, override|
        vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
        vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
        # add more ram, the default isn't enough for the build
        vb.customize ["modifyvm", :id, "--memory", "2048"]
    end

    # install Build Dependencies (GOLANG)
    config.vm.provision :shell, :privileged => false, :path => "scripts/vagrant/install-go.sh"

    # Install rkt
    config.vm.provision :shell, :privileged => false, :path => "scripts/vagrant/install-rkt.sh"
    
    # sync external host
    config.vm.synced_folder "/Users/devops/sandboxes/", "/home/vagrant/sandboxes"
end
