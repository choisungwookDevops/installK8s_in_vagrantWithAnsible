# 우분투 이미지
IMAGE_NAME = "bento/ubuntu-16.04"
# 워커 노드 수
N = 1

Vagrant.configure("2") do |config|
    config.ssh.insert_key = false

    # 게스트 사양
    # 램 2GB
    # CPU 코어 2
    config.vm.provider "virtualbox" do |v|
        v.memory = 2048
        v.cpus = 2
    end

    # 마스터 노드
    config.vm.define "master" do |master|
        master.vm.box = IMAGE_NAME
        master.vm.network "private_network", ip: "192.168.50.10"
        master.vm.hostname = "master"
    end

    # 워커 노드
    # (1..N).each do |i|
    #     config.vm.define "node-#{i}" do |node|
    #         node.vm.box = IMAGE_NAME
    #         node.vm.network "private_network", ip: "192.168.50.#{i + 10}"
    #         node.vm.hostname = "node-#{i}"           
    #     end
    # end

    # ansible 서버
    config.vm.define "ansible-server" do |node|
        node.vm.box = IMAGE_NAME
        node.vm.network "private_network", ip: "192.168.50.240"
        node.vm.hostname = "ansible-server"           
        node.vm.provision "shell", inline: <<-SHELL
            sudo apt-get update
            sudo apt-get install software-properties-common
            sudo apt-add-repository --yes --update ppa:ansible/ansible
            sudo apt-get install ansible --yes
        SHELL
        # ansible 설정
        node.vm.provision "file", source: "./ansible_playbooks/setup-ansible.yml", destination: "setup.yml"
        node.vm.provision "shell", inline: "ansible-playbook setup.yml"
        # ssh 설정
        node.vm.provision "file", source: "./ansible_playbooks/configure_ssh.yml", destination: "configure_ssh.yml"
        node.vm.provision "shell", inline: "ansible-playbook configure_ssh.yml", privileged: false
    end
end