## 배포 자동화

github 이전의 나의 개인 블로그의 프론트와 백엔드는 분리되어서 개발되어있었는데,

매번 소스코드를 수정하고 커밋푸시 후에는, 리눅스서버에 접속하여

프론트만해도 git pull, npm install, npm run build, service nginx restart 명령어를 실행해줘야한다.

무려 4개의 명령어를 실행해야하므로 너무 귀찮다. 당연히 &&로 명령어를 연결하여 실행하긴하는데,

항상똑같은.. 너무 기계적인 작업이라 귀찮다. 

프로젝트 초기에는 그냥 했는데 이제 너무 귀찮아져서 자동화를 결심했다.

ci를 사용하려고 했는데 그 정도까지는 아직 필요성을 못느끼겠다.

그래봤자 명령어 4개.

실력향상겸(?) 직접 만들기로했다.

첫번째는 내가 사용할 명령어를 쉘스크립트로 동작할수있게 코드를 작성했다.


```sh
## front.sh
#!/bin/sh
echo "boseok_log auto build start"

eval "cd /var/www/boseok_log && sudo git pull && sudo npm install && sudo npm run build && sudo service nginx restart"

echo "boseok_log auto build end"
```

이런식으로.. 로그도 남겼다. 핵심은 당연히 eval이 있는 2번째줄.

그리고 nodejs로 간단한 서버를 만들었다.

해당 서버를 요청하게되면 쉘스크립트를 실행하도록했다.


```js
const http = require('http');
const shell = require('shelljs');

http.createServer((req, res) => {
  const {url} = req;
  if(url === '/favicon.ico')
    return;

  console.log(`request ${url} build`);

  if(validateURL(url)){
    console.log(`start building => ${url}`);
    shell.exec(`.${url}.sh`);
    res.write(`build end => ${url}`);
    console.log('build end');
  } else {
    res.write(`${url} not found\n`);
  }
  res.end();
}).listen(8887);

const validateURL = url => ['front', 'back'].some(param => `/${param}`=== url);
```
```
서버주소:8887/front
서버주소:8887/back
```
위의 주소로 요청을 날리면 된다.

이 서버요청이 필요한 이유는,

소스코드를 github나 bitbucket을 사용하여 저장하고있는데

거기서 webhook이라는 기능을 지원한다.

소스코드를 remote repository에 푸시하면, 

webhook에 등록한 url을 요청한다.

거기에 방금 작성한 서버 url을 등록해서,

수정된 소스코드를 푸시하면, 자동으로 빌드, 배포를 할수있다.


