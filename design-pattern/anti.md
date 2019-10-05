# README

좋은 소프트웨어에는 다양하고 공통적인 디자인패턴들이 적용되어있는데,

나쁜 소프트웨어도 마찬가지로 다양하고 안 좋은 패턴들이 있다.

여기에선 구조상 좋지 않고 피해야할 패턴들을 소개한다.

## 첫번째 사례

```javascript
var a = 1;
console.log(a);

// some code

function someAddFunc(b) {
  a = a + b;
}

// ...some code

console.log(a);
```

위 코드는 함수내에 선언된 변수나 파라미터변수가 아닌 외부 변수의 값을 변경하고 있다.

위와 같은 구조의 코드는 상당히 나쁜 패턴이고 피해야한다.

변수 선언과 함수선언 사이에 a값을 변경하거나,

나중에 a 값을 사용하려고 했을때 함수 선언과 그 변수의 사용하는 시점 사이의 코드가 많다면

결과값을 예측하기가 쉽지 않고 사이드이펙트 우려가 크다.

## 두번째 사례

```javascript
function someAddFunc2(a, b) {
  a = a || 1;
  b = b || 2;
  return a + b;
}

console.log(someAddFunc2()); //3
console.log(someAddFunc2(2, 2)); //4
```

예제에서는 괜찮아 보일 수 있지만, 가독성이 떨어지고 사이드이펙트 우려도 있습니다.

\(paramter 변수가 primitive type이 아닌 경우를 생각해보세요.\)

es6에서는 default paramter를 제공합니다.

```javascript
function someAddFunc2(a = 1, b = 2) {
  return a + b;
}

console.log(someAddFunc2()); //3
console.log(someAddFunc2(2, 2)); //4
```

코드가 훨씬 간결하고 가독성도 더 좋으며,

사이드이펙트에 대한 우려도 줄어들었습니다.

