## Certbot, aws https setting with wildcard

```bash
sudo apt update && sudo apt install certbot

sudo certbot certonly --manual --preferred-challenges dns -d "*.{domain}" -d "{domain}" --server https://acme-v02.api.letsencrypt.org/directory
```

과정들을 따라하다보면...

```
Please deploy a DNS TXT record under the name
_acme-challenge.{domain} with the following value:

{요기 나오는 문자들!}

Before continuing, verify the record is deployed.
```

요기나오는 문자들을 복사하여, 

_acme-challenge 라는 이름으로 TXT레코드를 생성하고 붙여넣으면된다.

그리고나서 아래 명령어로 DNS TXT가 변경됐는지 확인

```bash
nslookup -q=TXT _acme-challenge.{domain}
```

변경되고나면 아까 진행하던 커맨드라인에서 엔터를 누르면 된다.

이것이 DNS로 인증하는방법.

---------------------------


pem인코딩 내용들은 아래서 확인한다.

```bash
sudo cat /etc/letsencrypt/live/{domain}/privkey.pem
sudo cat /etc/letsencrypt/live/{domain}/cert.pem
sudo cat /etc/letsencrypt/live/{domain}/chain.pem
```

aws NLB에서 사용했다.

로드밸런서를 구성할때 참 편-안한 방법인것같다