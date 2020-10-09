# 1. 워커 노드의 개수를 수정하는 상황
## 1.1 Vargrantfile 설정
* 상단 변수 "N"의 값을 수정
```yaml
# 워커 노드 수
N = 1 <--수정
```

## 1.2 ansible이 관리하는 노드 IP 수정
* ansible_playbooks/setup-ansible.yml에서 node-xx 수정
```yaml
- name: Setup for the Ansible's Environment
  hosts: localhost
  gather_facts: no

  tasks:
    - name: Add "/ect/ansible/hosts"
      blockinfile:
        path: /etc/ansible/hosts
        block: |
            [master]
            172.16.10.10
            이 부분에 IP추가 또는 수정
```

## 1.3 수정한 yml 실행
```
vagrant destroy -f ; 기존의 모든 vagrant 삭제
vagrant up
```

<br>

# 2. 마스터 노드의 IP를 수정하는 경우
## 2.1 Vargrantfile 설정
* 상단 변수 "N"의 값을 수정
```yaml
# 우분투 이미지
IMAGE_NAME = "bento/ubuntu-16.04"
MASTER_IP = "172.16.10.10" <-- 수정
```

## 2.2 ansible이 관리하는 노드 IP 수정
* ansible_playbooks/setup-ansible.yml에서 node-xx 수정
```yaml
- name: Setup for the Ansible's Environment
  hosts: localhost
  gather_facts: no

  tasks:
    - name: Add "/ect/ansible/hosts"
      blockinfile:
        path: /etc/ansible/hosts
        block: |
            [master]
            172.16.10.10 <-- IP 수정
```

## 2.3 쿠버네티스 설치 스크립트 수정
* ansible_playbooks/kubernetes_masternode_install.yml 수정(93번째 줄)
  * --apiserver-advertise-address와 --apiserver-cert-extra-sans를 수정
```yaml
- name: Initialize the Kubernetes cluster using kubeadm
  command: kubeadm init --apiserver-advertise-address="172.16.10.10" --apiserver-cert-extra-sans="172.16.10.10" --node-name master --pod-network-cidr=192.168.0.0/16
```

## 2.4 수정한 yml 실행
```
vagrant destroy -f ; 기존의 모든 vagrant 삭제
vagrant up
```