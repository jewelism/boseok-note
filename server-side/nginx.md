## nginx

static 파일을 제공할 수 있는 웹서버이다.

대표적인 웹서버 아파치와는 다르게 비동기로 작동한다.

서버에 많은 부하가 생길 경우의 성능을 예측하기 쉽게 해준다.

### 설치

```
sudo apt-get update
sudo apt-get install nginx
```
웹브라우저에 ip주소를 입력하고 접속하면 welcome to nginx 화면이 나온다.

```
1. 서비스 목록을 확인
 - service --status-all|grep +
2. 방화벽 확인
 - sudo ufw app list
 - sudo ufw allow 'Nginx HTTP'
 - sudo ufw status
3. 서비스되는지 확인
 - systemctl status nginx
4. 서비스 정지
 - sudo systemctl stop nginx
 - stop 외에 start, restart, reload, disable, enable 명령어가 있다.
5. cd /var/www/html => build 된 project를 deploy하면 된다.
6. 로그 확인
 - /var/log/nginx/access.log 혹은 error.log 
```

### 간단한 설정 방법

ubuntu 16버전 이상 기준 설정파일이 있는곳
```
vi /etc/nginx/sites-available/default
vi /etc/nginx/nginx.conf
```
nginx에 여러개의 웹이 올라갈거라면

default 대신에 도메인을 정의하고

정의한 도메인을 default에 설정해주면 된다.

모듈로 관리해서 편해진다.
```
server {
  listen  80;
  server_name boseok.me;
  return 301 https://$host$request_uri;
  # https로 redirect. or proxy_pass를 사용하자.
}

server {
  # SSL configuration
  listen 443 ssl default_server;
  listen [::]:443 ssl default_server;
  # https 기본포트로 설정. 다른 포트를 입력하면 접속할때 도메인 뒤에 포트번호가 붙어야한다.

  ssl_certificate /인증서경로/fullchain.pem;
  ssl_certificate_key /인증서경로/privkey.pem; ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
  ssl_ciphers HIGH:!aNULL:!MD5;
  # 인증서 설정

  root /var/www/boseok_log/build;
  # 설정한 포트로 접속할때, 기본 path

  server_name boseok.me;

  #path뒤에 param을 설정할 수 있다. ex) location /boseok {...} 
  location / { 
    try_files $uri $uri/ /index.html;
  }

}
```