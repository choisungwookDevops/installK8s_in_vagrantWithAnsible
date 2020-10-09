# 연결된 host확인
* 준비: /etc/ansible/hosts에 설정되어 있어야 함

```sh
ansible all --list-hosts
```

<br>

![](../imgs/ansible_allhosts.png)
<br>명령어 실행결과

<br>

# ansible 변수 조회
```sh
ans -m setup [ip]
```