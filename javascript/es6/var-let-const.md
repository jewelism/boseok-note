# var-let-const

var는 함수레벨 스코프를 가져서 블록레벨스코프에 변수를 선언해도 함수레벨어디서나 사용해도된다. \(레퍼런스에러가 안난다는 의미\)

그리고 재선언과 재할당이 가능하다.

ES6를 사용할수있는 환경이라면, 쓰지말도록하자.

let과 const로 완벽대체 가능.

let은 블록레벨 스코프의 변수이다. 다른언어들처럼.. const와 다르게 재할당 가능.

선언시 값을 대입해줄 필요가없음.

없는것을 참조하려고하면 레퍼런스에러가난다.

const도 블록레벨 스코프의 변수이고, 재할당이 불가능하다.

선언시 값을 대입해줘야함

```javascript
let a; //ok
const b; //error
const c = 1; //ok
```

const는 primitive에 대해서는 immutable이다.

object을 대입하면, immutable object는 아니다.

하지만 주소값은 변경할 수 없음. \(재할당할수없음\)

예를 들면 const 에 숫자나 문자열을 대입하면, 변경할수없다.

하지만 배열이나 오브젝트를 대입하고, 배열이나 오브젝트에 값을 추가하거나 뺄수있다.

```javascript
const numA = 1;
numA = 2; //에러

const objA = {};
objA = {name: '보석'}; //에러
objA.name = '보석'; //에러아님
```

