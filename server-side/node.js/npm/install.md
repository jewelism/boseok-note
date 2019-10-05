# npm install

npm install은 package.json에 작성해놓은 dependency를 모두 설치하는 명령어이다.

서버환경에서 npm install 했을때, permission 관련 에러가 났을때 해결방법

```bash
sudo npm install --unsafe-perm=true --allow-root
```

```bash
sudo npm install ${name} --unsafe-perm=true --allow-root
```

