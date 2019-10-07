# destructuring

배열의 경우 순서가 중요합니다.
```js
const [a, b] = [1, 2]; //a: 1 b: 2
```
객체의 경우는 키 이름이 중요합니다.
```js
const {b, a} = {a: 1, b: 2}; //a: 1, b: 2
```

함수 파라미터도 destructuring 할 수 있습니다.
```js
function A({a, b}) {
  return a + b;
}
A({a:1, b:2}); //3
```