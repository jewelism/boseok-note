## letsencrypt

letsencrypt 라는 서비스는,

https를 사용하기위한 인증서를 무료로 사용할 수 있게 해줍니다!

하지만 3개월마다 갱신을 해줘야하는데~ 쉘스크립트&크론탭을 사용하면 자동화시킬수있습니다.

ubuntu18 lts 기준으로 작성하였습니다~

```bash
sudo apt update && sudo apt install letsencrypt
```

혹시 80, 443 포트가 사용중이라면 안전한 ssl 세팅을 위해 잠시 중지해주세요.

```bash
sudo letsencrypt certonly --standalone -d 도메인
```

끝

---------------------------

맥에서는 방법이 조금 다릅니다.

homebrew에 letsencrypt 모듈이 없고,

certbot을 대신 사용하면 됩니다.

-----------------------

### 트러블슈팅
```
To fix these errors, please make sure that your domain name was
   entered correctly and the DNS A/AAAA record(s) for that domain
   contain(s) the right IP address. Additionally, please check that
   your computer has a publicly routable IP address and that no
   firewalls are preventing the server from communicating with the
   client. If you're using the webroot plugin, you should also verify
   that you are serving files from the webroot path you provided.
```

이런 에러메시지와 마주치게된다면..

```bash
certbot certonly -d 도메인 --manual --preferred-challenges dns
```

```
NOTE: The IP of this machine will be publicly logged as having requested this
certificate. If you're running certbot in manual mode on a machine that is not
your server, please ensure you're okay with that.
 
Are you OK with your IP being logged?
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
(Y)es/(N)o: Y
```

```
Please deploy a DNS TXT record under the name
_acme-challenge.somedomain.com with the following value:
 
여기에 나오는 키를 복사해두세요!!
sadfadsf6a8s7df67a8sd6f78 <<요런거
 
Before continuing, verify the record is deployed.
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Press Enter to Continue
```

DNS 서버에 TXT 레코드를 등록하는데, 호스트의 prefix로 _acme-challenge를 쓰는걸 빼먹지마세요!!

```
host => _acme-challenge.somedomain.com
```
TXT의 value에 아까 복사한걸 붙여넣으시면 됩니다.

새로운 터미널에서 등록됐는지 먼저 확인한다음에
```
nslookup -q=TXT _acme-challenge.somedomain.com
```

원래 진행하던 터미널에서 엔터누르고 발급하면 끝

트러블슈팅 reference: https://www.lesstif.com/pages/viewpage.action?pageId=59343172