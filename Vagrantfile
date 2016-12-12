VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.ssh.insert_key = false
    config.vm.box_check_update = false

    config.vm.define "vagrant1" do |vagrant1|
        vagrant1.vm.box = "bento/centos-7.1"
    end

    config.vm.define "vagrant2" do |vagrant2|
        # vagrant2.vm.box = "bento/ubuntu-16.10"
        vagrant2.vm.box = "bento/centos-7.1"
    end

    config.vm.define "vagrant3" do |vagrant3|
        vagrant3.vm.box = "bento/centos-7.1"

        config.vm.provision "ansible" do |ansible|
            ansible.limit = "all"
            ansible.verbose = "v" # "v" or "vvvv"
            ansible.playbook = "tests/test_vagrant.yml"

            ansible.groups = {
                "zookeeper" => ["vagrant[1:3]"]
            }

            ansible.host_vars = {
                "vagrant1" => {"zk_myid" => 1},
                "vagrant2" => {"zk_myid" => 2},
                "vagrant3" => {"zk_myid" => 3}
            }
        end
    end
end
