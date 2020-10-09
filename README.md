# 1. 목적
* vagrant+Ansible환경에서 kubernetes설치
* 현재 단점: IP를 수정하거나 워커노드를 수정하면 초기화 후 다시 실행

<br>

# 2. 환경
* windwos 10
  * vagrant
  * virtualbox
    * guest -> ubuntu 16.04 LTS
      * masternode 1개
      * workernode n개
      * 
<br>

![](imgs/arch.png)

<br>

# 3. 문서 목차
1. [vargrant 게스트 원격접속](documentation/vagrant_ssh원격접속.md)
2. [VM게스트 사양 등 설정](documentation/vagrant_게스트설정.md)
3. [IP수정, 워커노드 추가](documentation/마스터&워커노드_IP수정.md)


<br>

# 4. 참고자료
* [1] ansible와 vargrant로 kuberenes설치 공식문서: https://kubernetes.io/blog/2019/03/15/kubernetes-setup-using-ansible-and-vagrant/
* [2] vagrant+ansible 설치 블로그: https://daddyprogrammer.org/post/7369/ansible-vagrant/
* [3] ansible 스크립트 파일: https://gist.github.com/hi1280/69a76141450ff047764801a3d3db05b4
* [4] 우분투에 ansible 설치설명: https://dev-yakuza.github.io/ko/environment/install-ansible/
* [5] vargrant provision.file: https://www.vagrantup.com/docs/provisioning/file
* [6] vagrant network 설정: https://www.vagrantup.com/docs/providers/virtualbox/networking