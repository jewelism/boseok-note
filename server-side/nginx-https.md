## nginx https 설정

인증서 발급이나 기본적인 인증서 설정은 [여기를 참고하세요 => letsencrypt](./letsencrypt.md)

----------------

ubuntu18 기준

```bash
sudo vi /etc/letsencrypt/sites-available/default
```

아래 코드에 섞여있는 도메인과 서버이름은 알맞게 바꾸세요~
```nginx
server {
       listen         80;
       server_name    boseok.me;
       return         301 https://$host$request_uri;
}

server {
    listen 443 ssl default_server;
	listen [::]:443 ssl default_server;
	
	ssl_certificate /etc/letsencrypt/live/boseok.me/fullchain.pem;
	ssl_certificate_key /etc/letsencrypt/live/boseok.me/privkey.pem; ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
ssl_ciphers HIGH:!aNULL:!MD5;
}
```

```bash
sudo service nginx restart
```