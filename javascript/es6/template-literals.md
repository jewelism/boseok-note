## 템플릿 리터럴(Template literals)

#### ES6 스펙

백틱(`) - 숫자 1 왼편에 있는 특수문자

자바스크립트에서 백틱내에 작성한 문자열들은

표현식(expression)이 포함될 수 있습니다.

```js
`string` //string

const boseok = 'Boseok123';
`string ${boseok} end` //string Boseok123 end
```
이런식으로 변수를 끼워넣을수도 있고,

```js
const boseok = 'boseok';

`some ${boseok.toUpperCase()} end` //string BOSEOK end
```
이런식으로 메소드 사용도 가능합니다.

표현식이라면 뭐든지 넣을 수 있습니다.

개행도 가능합니다.

```js
'boseok1\n'+
'boseok2'

`boseok1
boseok2`
```
### Tagged Templates

태그를 사용하면 템플릿 리터럴을 함수로 파싱 할 수 있습니다.

```js
const var1 = 'some var1';
const var2 = 'some var2';
function someTag(strings, ...params) {
  //strings => ['some ', ' is ', ' end']
  //params => [var1, var2]
  return 'something';
}
const someOutput = someTag`some ${var1} is ${var2} end`;
console.log(someOutput); //something
```

위의 예제처럼 파라미터로 문자열과 표현식이 넘어옵니다.

함수를 선언해두고 특이한 방식으로 호출하고 있네요.

react styled-component에서 tagged template을 사용하기때문에,

react개발자라면 알아두는게 좋습니다.
