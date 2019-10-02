## export, import

### es6 모듈

export, import

es6모듈의 import 키워드와 webpack, parcel같은 번들러의 dynamic import 메소드를 구분하자.

### nodejs 모듈

commonJS와 거의 동일하지만 자체적인 모듈을 사용

module.exports

require()

---------------------------

## export와 코드의 실행순서

constants들을 따로따로 구분지어서 작성해놓았을때, 서로 import해야하는 상황이 온다.

그럴때 import를 해도 undefined가 나오는경우가 간혹있는데,

당연히 실행순서에 문제가 있기때문이다.

```js
console.log('1');
export * from './someConstants';
```

```js
// someConstants.js
console.log('2');
```

콘솔에는 1 2 가 나올것으로 기대하겠지만,
2 1로 나온다.

export에 우선순위가 있다.

-----------------------

## import * as {Alias}, import {Alias} 차이

```js
// a.js
export const a = 1;
export const b = 2;
export default 3;
```

```js
import A from './a';
import * as B from './a';
console.log(A); //3
console.log(B); //Module {a:1, b:2, default:3, ...}
```
