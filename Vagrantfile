#ENV['VAGRANT_DEFAULT_PROVIDER'] ='docker'
#vagrant plugin install vagrant-vbguest

IMAGE = "ubuntu/xenial64"
N = 1
Vagrant.configure("2") do |config|
    config.ssh.insert_key = false

    config.vm.provider "virtualbox" do |v|
        v.memory = 1024
	    v.cpus = 2
    end
     
    #config.hostmanager.enabled = true
    #config.hostmanager.manage_guest = true
    
    config.vm.define "k8s-master" do |k|
        k.vm.box = IMAGE
        k.vm.network "private_network", ip: "192.168.50.10"
        #k.vm.network :forwarded_port, guest: 8001, host: 8080
        k.vm.hostname = "k8s-master"
        k.vm.provision "ansible" do |ansible|
	    ansible.extra_vars = {ansible_python_interpreter: "/usr/bin/python3", node_ip: "192.168.50.10", }
            ansible.playbook = "scripts/master.yml"
        end
    end

    (1..N).each do |i|
        config.vm.define "slave-#{i}" do |slave|
            slave.vm.box = IMAGE
            slave.vm.network "private_network", ip: "192.168.50.#{i + 10}"
            slave.vm.hostname = "slave-#{i}"
            slave.vm.provision "ansible" do |ansible|
                ansible.extra_vars = {ansible_python_interpreter: "/usr/bin/python3", node_ip: "192.168.50.#{i + 10}", }
                ansible.playbook = "scripts/slave.yml"
            end
        end
    end
end
