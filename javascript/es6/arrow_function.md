# 화살표함수 - arrow function

화살표함수는 ES6 스펙이다

람다의 자바스크립트버전이다.

```js
const v = a => a + 1;
v(1); //2
```

```js
function v(a) {
  return a + 1;
}
```

위 두 코드는 '거의' 동일한 코드이다.

차이점이라면 생성자로 쓸수없다는것,

this, arguments, super, new.target을 바인딩하지않는것.

그리고 화살표함수는 항상 익명함수이다.

첫 코드에서는 단순히 v라는 변수에 함수를 대입한것뿐이다.

또한, 미미한 성능차이가 있다. (arrow function이 조금 더 느리다)

----------

위의 첫번째코드를 보면, v(1)의 리턴값이 2이다.

블럭으로 감싸지않으면, expression을 리턴한다.

그 말은 블럭으로 감싸고 리턴을 하지 않으면, undefined를 리턴한다는 뜻이다.

```js
const v = a => { a + 1 };
v(1); //undefined
```

-------

그리고 위의 코드에서는 매개변수를 괄호로 감싸지않았는데, 한개인경우에만 괄호를 생략할수있고

매개변수가없거나 여러개면 괄호를 생략할 수 없다.

또한 매개변수에 rest parameter나 destructuring이 가능하다.

```js
const v = (a, ...rest) => rest;
v(1, 2, 3); //[2, 3]
```

```js
const v = ([a, b]) => a + b;
v([1, 2]); //3
```