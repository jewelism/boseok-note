## for in, for of 차이

#### 참고로 for of 는 ES6 스펙입니다.

아래 예제에서 보이는 것처럼,

for in 구문은 프로토타입을 포함한 모든것을 순회하고,

for of 는 콜렉션에 대해서만 순회합니다. 

~~[Symbol.iterator] 속성이 있는 모든 컬렉션 요소~~

```js
Array.prototype.someArrayFunc = () => {};

let someArray = [1, 2, 3];
someArray.boseok = 'boseok123';

for (let i in someArray) {
  console.log(i); // 1,2,3 'boseok', 'someArrayFunc'
}

for (let i of someArray) {
  console.log(i); //1,2,3
}
```
