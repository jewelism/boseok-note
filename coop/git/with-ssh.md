## ssh key 사용하기

bitbucket에서 mac 사용시.. (linux도 해당됨)

```bash
ssh-keygen
```

passphase는 입력하지말고 그냥 빈값으로 계속 엔터만 눌러주자.

그래야 나중에 안귀찮아진다.

```bash
cat ~/.ssh/id_rsa.pub
```

이걸 프로젝트의 access keys가 아닌, 자신의 계정의 bitbucket의 SSH key에 가서 추가한다.

```bash
eval 'ssh-agent'
```

```bash
#mac
ssh-add -K ~/.ssh/id_rsa

vi ~/.ssh/config
```
아래내용을 붙여넣는다
```
Host *
  UseKeychain yes
```

```bash
#linux
ssh-add ~/.ssh/id_rsa
```