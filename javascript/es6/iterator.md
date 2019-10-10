# Iterable, Iterator Protocol

직역하면 반복가능한(객체), 반복자 규약이다.

즉, 반복에 대한 내용이다.

iterable하다는 것은 객체가 @@iterator 메소드를 구현했다는 것이다.

이 말은 객체가 Symbol.iterator 키의 속성을 가져야한다는 것이다.

## Iterator Protocol

객체가 next() 메소드를 갖고 있고, next 메소드는 done, value라는 속성을 가진 객체이다.

done은 생긴것처럼 마지막 반복을 마쳤다면 true, 아니면 false이다.

value는 iterator로부터 반환되는 값이다. done이 true일경우 undefined.

```js
const arr = [1, 2, 3];
const iterator = arr[Symbol.iterator]();
iterator.next(); // {value: 1, done: false}
iterator.next(); // {value: 2, done: false}
iterator.next(); // {value: 3, done: false}
iterator.next(); // {value: undefined, done: true}
```

### Iterable 객체의 구현

```js
const obj = { a: 1, b: 2, c: 3 };

obj[Symbol.iterator] = function() {
  const keys = Object.keys(obj);
  return {
    index: -1,
    next() {
      this.index++;
      return { value: obj[keys[this.index]], done: this.index >= keys.length };
    }
  };
}

for(const v of obj) {
  console.log(v);
}
```

iterable 구현을 위한 예시일뿐이다..

실제로 for of 에서 객체를 쓰고싶다면 Object.entries() 메소드를 사용하도록하자.

```js
for(const [key, value] of Object.entries(obj)) {
  // ...some code
}
```

제너레이터를 통해서도 iterable 객체를 구현할 수 있다.

```js
const obj = {};
obj[Symbol.iterator] = function* () {
  yield 1;
  yield 2;
  yield 3;
};
[...obj]; // [1, 2, 3]

const iterator = obj[Symbol.iterator]();
iterator.next(); // {value: 1, done: false}
```

```js
const generatorObj = function* () {
  yield 1;
  yield 2;
  yield 3;
}();
[...generatorObj]; // [1, 2, 3]
```

이렇게 만들어진 iterable 객체는 Array.from() 메소드로 쓰거나,

Map, Set 등에 활용할 수 있습니다.

------------

