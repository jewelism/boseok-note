# Symbol

ES6에 새롭게 추가된 스펙이다

Symbol은 새로운 primitive 타입이며,

기존에 object의 key로는 string only였는데, Symbol도 가능하게되었다.

object의 key는 어떤값을 넣던 string으로 타입캐스팅이 되면서 여러가지 문제점들이 있었는데,

ES6가 등장하면서 Map, Symbol등이 그 이슈들을 굉장히 좋은방법들로 해결해준다.

Symbol은 생성자가 없다. 그래서 함수호출형태로만 사용한다.

new 연산자를 못쓴다는 의미이다. wrapper객체를 생성하는 방법은 있긴하지만(Object(Symbol()))

원래의 심볼 목적인 객체 프로퍼티 키로 쓰려고하는 것에 어긋난다.

파라미터는 description이 유일하다. 어떤 용도인지 간단하게 메모하는정도이다. 값은 디버깅외에는 의미없다.

실제로 같은 desc를 넣고(숫자 1), 심볼을 2개 생성해서 객체의 키로 각각 설정해주고 콘솔로그를 보면,

똑같이 생긴 심볼 2개가 각각 객체 키로 설정되어있다. 내부적으로는 키값이 다른것이다.

s1과 s2를 비교해봐도 마찬가지로 다르다.

매 함수호출마다 다른 심볼들을 생성한다.

```js
const s1 = Symbol(1);
const s2 = Symbol(1);
const obj = {
  [s1]: 1,
  [s2]: 2
}
console.log(obj); // {Symbol(1): 1, Symbol(1): 2}
s1 === s2; // false
```