## boxing, unboxing

js의 primitive type
```
boolean
string
number
null
undefined
```
null과 undefined를 제외한 3가지는 primitive wrapper가 존재한다.

단순히 첫글자가 대문자일뿐이다.

```js
Boolean
String
Number
```

new String('boseok')

이런식으로도 문자열객체를 생성할수있다는뜻이다.

------------------

박싱 언박싱은.. 예를 들자면
```js
1 === new Number(1) //false
1 == new Number(1) //true
typeof new Number(1) //object
```
== 연산자는 내부적으로 형변환해서 비교하기때문에 아예 안쓰는 연산자이지만 예를 들기위해서 사용하였음.

여튼 위의 코드를 보면, wrapper클래스로 생성한 Number의 객체의 타입은 당연히 숫자가 아니라 객체다.

그렇다면 아래와 같은 코드를 보자.

```js
const one = new Number(1);
const two = 2;
const three = one + two;
console.log(three, typeof three); //3 number
```
one은 객체고, two는 숫자이다.

객체와 숫자를 + 연산자로 합칠수있나?

콘솔로그를 보면 3이 찍히는걸 확인할 수 있다. 그리고 타입도 숫자이다.

이 말은 자동으로 형변환이 이루어진 것인데, wrapper가 벗겨져서 숫자가 된것이므로,
언박싱이라고 한다.

반대로 숫자가 객체로 변환된다면 그것은 박싱이다.

참고 - 박싱, 언박싱은 자바에서도 마찬가지다.
