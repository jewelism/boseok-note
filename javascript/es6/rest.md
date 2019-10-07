# rest, spread

## rest

디스트럭쳐링이나 함수 파라미터에서 나머지 변수들을 유용하게 컨트롤할 수 있습니다.

아래 예제 2개에서는 destructuring과 함께 썼지만, rest라는 변수 이름에 주목하시면 됩니다.

```js
const [a, b, ...rest] = [1, 2, 3, 4]; //a: 1 b: 2, rest: [3, 4]
```
객체의 경우는 키 이름이 중요합니다.
```js
const {b, a, ...rest} = {a: 1, b: 2, c: 3, d: 4}; //a: 1, b: 2, rest: { c: 3, d: 4 }
```

함수 파라미터에도 rest 구문을 사용할 수 있습니다.
```js
function A(a, ...rest) {
  return rest;
}
A(1, 2, 3, 4); //[2, 3, 4]
```

## spread

spread는 rest와 반대로 생각하시면 편리합니다.
```js
const obj = {
  a: 1,
  b: 2,
  c: 3,
};

const extObj = {
  ...obj, //spread
  d: 4
};

console.log(extObj); // {a: 1, b: 2, c: 3, d: 4}
```
배열도 당연히 같은 방법으로 사용합니다.

```js
const arr1 = [1, 2];
const arr2 = [...arr1, 3, 4]; // [1, 2, 3, 4]
```