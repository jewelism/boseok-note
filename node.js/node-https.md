## node에서 간편하게 letsencrypt를 사용하여 https 구현하는 방법

먼저 인증서를 생성합니다.

인증서를 생성하기위해서는 먼저 도메인이 필요한데, 해당 과정은 여기서는 생략합니다.

[ubuntu에서 letsencrypt 인증서발급방법](../server-side/letsencrypt.md)


greenlock 라이브러리를 사용합니다.

설명은 express기준으로 작성하였습니다만

express외에 koa, hapi 등의 모듈도 준비되어있습니다.

```bash
npm i greenlock-express
```

app.js에서,

```js
module.exports = app;
```

위의 코드 바로 전 라인에 아래 코드를 추가하면 된다.

```js
require('greenlock-express').create({
  version: 'draft-11',
  configDir: '/etc/letsencrypt/',
  server: 'https://acme-v02.api.letsencrypt.org/directory',
  email: '이메일',
  agreeTos: true,
  approvedDomains: ['도메인'],
  app,
  renewWithin: 81 * 24 * 60 * 60 * 1000,
  renewBy: 80 * 24 * 60 * 60 * 1000,
}).listen(80, 443);
```

reference : https://git.coolaj86.com/coolaj86/greenlock-express.js

------------------------------

또 다른방법은 nginx로 reverse proxy를 구현하고, ssl을 붙이는 방법이 있긴하다. 그런데 위에 방법이 더 간편함..