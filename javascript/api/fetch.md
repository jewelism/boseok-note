## Fetch API

[Promise](promise.md) 기반의 사용하기편한 XHR(XmlHttpRequest)이라고 생각하면 됩니다.

하지만 기본적으로 fetch는 쿠키를 보내거나 받지 않습니다.

또한 에러코드를 리턴받더라도, Promise는 http error status를 reject 하지 않습니다.

대신 response객체의 ok프로퍼티로 확인이 가능하며(true or false), 네트워크 장애등의 에러는 reject를 반환합니다.

Promise기반이므로 ES6이상의 환경에서 동작하며,

그 이하의 환경을 위해 polyfill도 존재합니다.

polyfill : https://github.com/github/fetch

### 사용 방법

```js
fetch(url, option?)
```
Promise를 리턴하므로 thenable합니다.

```js
fetch(...)
  .then(...)
```

```js
function parseJson(res){
  return res.json()
}

function parseHtml(res){
  return res.text()
}

fetch(...)
  .then(parseJson)
  .then(json => {
    ...some logic
  })
  .catch(err => {
    console.error(err);
  })
  .then()
```
위의 예제에서 res.json()의 리턴값은 Promise객체입니다. 그래서 다시 then으로 체이닝할수있습니다.
또한 catch로 체이닝하여, 에러핸들링을 할수있고,
catch 뒤에 then을 다시 체이닝하여 finally에 해당하는 구문을 작성할 수 있습니다.

```js
const BASE_URL = 'http://...';

function post(uriParams, body) {
    return fetch(`${BASE_URL}/${uriParams}`, {
        method: 'POST',
        headers: {'Content-Type': 'application/json'},
        body: JSON.stringify(body)
      }).then(res => res.json())
        .then(res => resolve(res))
        .catch(err => reject(err));
  }
```
간단한 post 요청을 하는 예제입니다.

promise객체로 wrapping하여 리턴하고 있습니다.

fetch의 두번째 파라미터에 여러가지 옵션을 설정할수있습니다.

Json을 전송할 때, stringify해서 보내는게 특징입니다.
