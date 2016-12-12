VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.ssh.insert_key = false
    config.vm.box_check_update = false

    config.vm.define "vagrant1" do |vagrant1|
        # 在centos7.1上, 设置private_network后ip需要重启网络才能生效;ubuntu-16.10可以正常获得静态ip。所以"bento/centos-7.1"这个box需要加上手工重启网络的命令
        vagrant1.vm.box = "bento/centos-7.1"
        vagrant1.vm.provision "shell", inline: "sudo systemctl restart network"

        vagrant1.vm.network "private_network", ip: "192.168.168.201"
    end

    config.vm.define "vagrant2" do |vagrant2|
        # vagrant2.vm.box = "bento/ubuntu-16.10"
        # 在centos7.1上, 设置private_network后ip需要重启网络才能生效;ubuntu-16.10可以正常获得静态ip。所以"bento/centos-7.1"这个box需要加上手工重启网络的命令
        vagrant2.vm.box = "bento/centos-7.1"
        vagrant2.vm.provision "shell", inline: "sudo systemctl restart network"
        vagrant2.vm.network "private_network", ip: "192.168.168.202"
    end

    config.vm.define "vagrant3" do |vagrant3|
        # 在centos7.1上, 设置private_network后ip需要重启网络才能生效;ubuntu-16.10可以正常获得静态ip。所以"bento/centos-7.1"这个box需要加上手工重启网络的命令
        vagrant3.vm.box = "bento/centos-7.1"
        vagrant3.vm.provision "shell", inline: "sudo systemctl restart network"
        vagrant3.vm.network "private_network", ip: "192.168.168.203"

        config.vm.provision "ansible" do |ansible|
            ansible.limit = "all"
            ansible.verbose = "v" # "v" or "vvvv"
            ansible.playbook = "tests/test_vagrant.yml"

            ansible.groups = {
                "zookeeper" => ["vagrant[1:3]"]
            }

            ansible.host_vars = {
                "vagrant1" => {"zk_myid" => 1, "zk_ip" => "192.168.168.201"},
                "vagrant2" => {"zk_myid" => 2, "zk_ip" => "192.168.168.202"},
                "vagrant3" => {"zk_myid" => 3, "zk_ip" => "192.168.168.203"}
            }
        end
    end


end
