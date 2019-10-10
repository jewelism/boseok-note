# entries

```js
// ES6
// entries() 메서드는 배열의 각 인덱스에 대한 key/value 쌍을 가지는 새로운 Array Iterator 객체를 반환합니다.
// 가끔 필요한데.. 어려울수있음..! iterator객체는 그냥 쉽게 말해서 for of 문법에 사용가능한 객체라고 이해하면 편함

const a = ['a', 'b', 'c'];
const iterator = a.entries();

console.log(iterator.next().value);

for (let e of iterator) {
    console.log('in for', e);
}

console.log(iterator.next().value);

  // [0, 'a']
  // [1, 'b']
  // [2, 'c']
```