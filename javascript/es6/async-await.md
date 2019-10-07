# async-await

## 스펙

node.js는 8버전 이상부터 공식적으로 지원하고 있고, ES8 스펙입니다.

## 기본 설명

async, await를 사용하면 비동기로직을 마치 동기적인것처럼 작성할 수 있습니다.

기본적으로 async 라는 '키워드'는 함수 앞에 선언합니다.

```javascript
async function(){}

async () => {}
```

await는 async 함수내에서만 사용할 수 있습니다.

await는 'Promise'의 해결을 기다리고 반환한후 다시 async 함수를 실행합니다.

await 뒤의 표현식은 Promise객체가 와야겠죠?

그리고 async function은 Promise를 반환합니다.

```javascript
const somefunction = async () => {
  const myNum = await Promise.resolve(111);
  return myNum + 222;
}
somefunction()
  .then(console.log) //333
```

글을 이해하셨다면, 333이 나올거란걸 예상하셨겠죠?

하지만 아래의 예제를 봅시다

```javascript
const somefunction = async () => {
  const myNum = await 111;
  return myNum + 222;
}

somefunction()
  .then(console.log) //???
```

다 같은데, await뒤의 표현식이 promise가 아니라 Number입니다.

await는 Promise객체를 기다리는 것인데.. 숫자가오면 어떻게 될까요?

async function에서 await 뒤의 표현식은 암묵적으로 Promise.resolve\(\)로

wrapping되기 때문에, 첫번째 예제와 같은 333이 콘솔에 찍히게 됩니다.

동기적으로 작동하는 것처럼 보여서 가독성이 향상됩니다.

하지만 사실 비동기로 작동한다는 점,

에러핸들링을 하려면, try-catch를 사용하여야 한다는 점에서 오히려 불편할 수도 있습니다.

Mozila의 문서에 await를 잘 이해할 수 있을만한 좋은 예제가 있습니다

```javascript
function resolveAfter2Seconds(x) {
  return new Promise(resolve => {
    setTimeout(() => {
      resolve(x);
    }, 2000);
  });
}

async function add1(x) {
  const a = await resolveAfter2Seconds(20);
  const b = await resolveAfter2Seconds(30);
  return x + a + b;
}

add1(10).then(v => {
  console.log(v);  // prints 60 after 4 seconds.
});

async function add2(x) {
  const p_a = resolveAfter2Seconds(20);
  const p_b = resolveAfter2Seconds(30);
  return x + await p_a + await p_b;
}

add2(10).then(v => {
  console.log(v);  // prints 60 after 2 seconds.
});
```

add2는 타이머를 먼저 생성하고있죠?

add1은 첫번째 타이머를 생성하고 2초를 기다려서 결과값을 받아옵니다.

add2에서는 생성해둔 타이머를 동시에 시작합니다.

그래서 거의 비슷해보이는데도, 시간에 차이가 있죠.

두 개 이상의 Promise를 동시에 await 시키고 싶다면,

Promise.all을 사용하면 됩니다.

[그 예제는 여기에 있습니다.](../api/promise.md)

## Tip - for문과 promise

어떠한 상황에서는 어떤 iterable객체에서 iterate하며

promise를 사용하고 싶을때가 있습니다.

예를들어

```javascript
const API_LIST = [url1, url2, url3, ...];
```

이런식으로 호출해야할 api가 여러개라고 한다면,

for문을 사용해서 promise를 호출하는데,

가독성을 위해 async await를 사용하고 싶다고 가정합니다.

```javascript
async function someFunction(urls) {
  for (const url of urls) {
    const res = await fetch(url);
    // do something
  }
}
```

이런식으로 코드를 작성하게되면, 깔끔하군요!

하지만 한가지 문제가 있습니다.

첫번째 api를 호출하고, 기다렸다가 두번째 api를 호출합니다.

그 이후로도 마찬가지겠죠..

이렇게 되면 의미가 없죠? 그래서 해결방법을 가져왔습니다.

```javascript
async function someFunction(urls) {
  const somePromises = urls.map(url => {
    return fetch(url);
  });

  for (const apiPromise of somePromises) {
    const res = await apiPromise;
    //do something with res
  }
}
```

이런식으로 작성하게된다면, 순차적으로 기다릴일은 없겠네요!

reference : [https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/async\_function](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/async_function)

