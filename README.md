# 1. 목적
vagrant+Ansible환경에서 kubernetes설치

<br>

# 2. 환경
* windwos 10
  * vagrant
  * virtualbox
    * guest -> ubuntu 16.04 LTS
      * masternode 1개
      * workernode n개

<br>

# 3. 주의사항
* ansible 윈도우 설치 불가 -> 윈도우용 ansible은 node관리 불가

<br>

# 4. 참고자료
* [1] ansible와 vargrant로 kuberenes설치 공식문서: https://kubernetes.io/blog/2019/03/15/kubernetes-setup-using-ansible-and-vagrant/
* [2] vagrant+ansible 설치 블로그: https://daddyprogrammer.org/post/7369/ansible-vagrant/
* [3] ansible 스크립트 파일: https://gist.github.com/hi1280/69a76141450ff047764801a3d3db05b4
* [4] 우분투에 ansible 설치설명: https://dev-yakuza.github.io/ko/environment/install-ansible/
* [5] vargrant provision.file: https://www.vagrantup.com/docs/provisioning/file