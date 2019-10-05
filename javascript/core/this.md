# this와 arrow function

자바스크립트에서는 특이하게도 this가 원하지않는대로 작동할수도있다.

대부분의 경우 this의 값은 함수를 호출한 방법이 결정한다.

```js
function a() {
  this.p1 = 1;
  this.p2 = 2;
  console.log(this);
}

const A = a();
const B = new a();

console.log(A); // undefined
console.log(B); // {p1:1, p2:2}
```

첫번째로 함수가 constructor로 작동할때, 그렇지않을때의 차이이다.

a함수의 리턴값이 없으므로 A의 경우는 undefined이고,

B의 경우에는 new 연산자를 사용하였으므로 constructor로 작동하면서

인스턴스 객체의 프로퍼티가 보여진다.

두번째로 A의 경우, a함수 내부의 this는 global객체이다.

위의 예제가 일반적이지만 엄격모드(use strict)에서는 this는 글로벌객체가 아닌 undefined를 나타낸다.

세번째로, 전역 실행 문맥(global execution context)에서는 this는 global객체이다.

네번째로, 함수를 어떤 객체의 메서드로 호출하면 this의 값은 그 객체를 사용한다.

```js
const obj = {
  p1: 1,
  getP1: function() {
    return this.p1;
  }
};
obj.getP1(); //1
```

다섯번째로, 메소드 내부에 함수가 또 있으면 그 내부의 this는 또 다르다.

```js
const obj = {
  p1: 1,
  getP1: function() {
    function someFunction() {
      console.log(this); // global
    }
    return this.p1;
  }
};
obj.getP1(); //1
```
다른 언어에 익숙한 사람은 function대신 arrow function을 사용하는게 원하는대로 작동해서 정신건강에 이롭다.

혹은 ES5 스펙의 Function.prototype.bind를 써도 좋다.
