## Promise

ES6에서 표준이 된 스펙입니다.

비동기 동작이 완료된 후 결과 값이나 실패를 handling하기 유용합니다.

#### Promise의 상태

1. 대기(pending): 이행되거나 거부되지 않은 초기 상태.
2. 이행(fulfilled): 연산이 성공적으로 완료됨.
3. 거부(rejected): 연산이 실패함.

***Promise는 thenable 하다***

Promise는 then 메소드로 결과값을 받을 수 있습니다.

이것을 thenable하다고 표현합니다.

```js
Promise.prototype.then(onFulfilledCallback, onRejectedCallback)
```

promise객체는 then메소드로 체이닝하여 값을 반환 받을 수 있고 에러 콜백 또한 존재합니다.

then은 promise객체를 반환합니다

```js
Promise.prototype.catch(onRejectedCallback)
```
에러제어를 위한 catch 메소드도 존재합니다.

then처럼 체이닝할수있습니다.

catch도 then처럼 promise객체를 반환합니다.

#### Promise 생성 방법

```js
function post(uriParams, body) {
    return new Promise((resolve, reject) => {
      fetch(`${BASE_URL}/${uriParams}`, {
        method: 'POST',
        headers: {'Content-Type': 'application/json'},
        body: JSON.stringify(body)
      }).then(res => res.json())
        .then(res => resolve(res))
        .catch(err => reject(err));
    });
  }
```

[fetch API](fetch.md)에서 설명했던 예제 코드입니다.

Promise의 생성자에 Callback이 있죠?

파라미터로는 resolve, reject가 있습니다.

원하는 결과값을 resolve하면 되고, 에러는 reject하면 됩니다.

reject는 보통 오류객체를 반환합니다.

#### 더 간단한 예제

```js
const myPromise = () => {
  return new Promise(resolve => {
    setTimeout(() => {
      resolve('2second');
    }, 2000);
  });
};

myPromise()
  .then(res => console.log('myPromise', res))
```
약 2초후 myPromise 2second가 콘솔에 찍히는 예제입니다.

간단하면서도 아주 강력하죠?

#### 그 외 메소드들
```js
Promise.all(iterable)
/*
iterable 내의 모든 프로미스가 이행한 뒤 이행하고, 어떤 프로미스가 거부하면 즉시 거부하는 프로미스를 반환합니다.
이 말은 reject가 있으면 reject를 반환하고, resolve되면 resolve된 값들을 배열로 반환한다는 의미입니다.
이 메서드는 여러 프로미스의 결과를 모을 때 유용합니다.
아래 예제가 있습니다.
*/
Promise.race(iterable)
//iterable 내의 어떤 프로미스가 이행하거나 거부하는 즉시 스스로 이행하거나 거부하는 프로미스를 반환합니다. 
Promise.reject(reason)
//주어진 이유로 거부하는 Promise 객체를 반환합니다.
Promise.resolve(value)
/*
주어진 값으로 이행하는 Promise 객체를 반환합니다.
*/
```
아래의 스크린샷은 Promise.all을 사용한 예제입니다.
<img src="images/promise-all-resolve.png">
<img src="images/promise-all-reject.png">

reference: https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Promise