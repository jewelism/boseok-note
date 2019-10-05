# ssh key 사용하기

bitbucket에서 mac 사용시.. \(linux도 해당됨\)

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

```text
Host *
  UseKeychain yes
```

```bash
#linux
ssh-add ~/.ssh/id_rsa
```

ubuntu 에서 사용할 쉘스크립트를 작성해보았다.

주의할점은 ssh-keygen의 default path가 mac과는 다르게\(home\) /root 이다.

```bash
#!/bin/bash

ssh-keygen;

eval 'ssh-agent';
ssh-add /root/.ssh/id_rsa;
cat /root/.ssh/id_rsa.pub;
exit;
```

