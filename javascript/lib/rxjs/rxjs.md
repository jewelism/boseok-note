## Reactive extension

### Reactive programming?
```js
var a = 1;

var b = 2;

var c = a + b;

b = 3;

//c == 3????
```


reactive에서는 4…



마치 js 클로저를 설명하기위해 counter와 모듈패턴을 예로 하듯이..

reactive를 설명하기위한 대표적인 예시인 엑셀


rx는 data flow-stream 에만 관심이 있다.

Stream - 어떤 글에서는 어떤 기간동안 다루게 되는 이벤트나 데이터의 컬렉션이라고 설명하고있는데

심플하게 표현하면 => data flow

참고) 자바에도 8버전에 Stream API가 나옴! 자바도 데이터플로우와 함수형의 개념을 수용 => 패러다임의 변화



------------------------------------------------------------------------------------------

### rx의 필요성

js개발 => callback hell => promise, async/await

하지만 근본적인 해결책은 아니다.

에러처리도 마찬가지. Promise의 catch는 좋다.

하지만 async/await를 사용했는데 에러핸들링이 필요하다면?

Try catch로 wrapping 해야함.

정리하면 rx를 사용하게 되면 비동기 로직, 에러 핸들링에 유리하고,

마치 함수형처럼 stateless하고, clean한 input, output으로 사이드이펙트를 최소화하고 코드를 간결하고 유지보수하기 좋은 구조로 설계할 수 있다.

공식문서에도 functional이라는 단어가 포함되어있다.


현 프로젝트에서는 Vue를 사용하여 다소 복잡할 수 있는 UI는 vue에게 맡겨버린다.

데이터플로우와 로직에만 집중할 수 있다.

그런데 데이터플로우와 로직도 rx라는 라이브러리의 힘을 빌려서 clean하게 작성할 수 있다.

### 편리함

웹소켓은 열면 닫아줘야하고, api통신은 도중에 중단할 수 없고, 이벤트리스너는 사용하고 삭제해야한다.

rx를 사용하여 원하는 타이밍에 웹소켓을 닫고, api통신을 중단하고, 이벤트리스너를 자동으로 삭제하여 해제하거나 중단하는데 수고를 덜어준다.

 

### js array의 문제점

const myArray = someArray.filter().map().reduce()…

메소드마다 배열을 iterate해야하고, 다시 할당하고, 해제한다(GC)

이런 방식이 다소 비효율적이다.

이런문제는 rxjs로 해결가능하다.

iterate, 할당 횟수를 줄여준다. 이렇게 되면 당연히 GC도 덜한다.


--------------------------------------------------------
### Observer 패턴의 주요 용어

#### Observer
관찰자

Observable을 관찰하는 주체

#### Observable
관찰 할 수 있는

Observer가 바라보고 있는 대상

Observable은 Subscribable의 구현체이다.

Observable을 extends한 구현체들

```js
ConnectableObservable
GroupedObservable
Subject
BehaviorSubject
ReplaySubject
AsyncSubject
```
 

#### Subscribe
구독하다

Observer와 Observable을 이어주는

Observer가 Observable을 subscribe할때, Observable에서 이벤트가 발생하면, Observer가 알 수 있게 된다.


---------------------------------------------------------------------------------------------------------

### 사용법


js 메소드와 유사함
```js
import {of} from 'rxjs';

of(1,2,3);
```

js의 
```js
Array.of(1,2,3) //[1, 2, 3]
```

이것만 유사한게아니라 map, filter, reduce등등.. 네이밍이 같거나 아주 유사하다.

 

Promise와 유사함
```js
myObservable.subscribe(successFn, errorFn, completeFn)

promise.then(successFn, errorFn)
```

Promise의 구조와도 유사하쥬?

## 몇가지 오퍼레이터 소개
```js
fromEvent(inputElement, 'keyup') //엘리멘트의 이벤트 발생을 관찰한다.
pluck('target', 'value') //위에서 관찰하는 엘리먼트의 값을 가져온다.
filter(callback) /* js의 filter와 유사하다. callback에 (text)=> text.length>=3 이런식으로 작성하여 조건을 걸수있다.*/
debounceTime(ms) /* ms에는 ms단위로 숫자를 적어준다. lodash의 debounce와 유사하다. 시간만큼 지난후 리턴. debounceTime은 input에 뭔가 입력하고, 자동으로 request를 하는것을 구현할때 유용하다.
*/
distinctUntilChanged //중복된 이벤트 제거
flatMapLatest() /* 이전에 만들어진 observable을 무시하고 가장 마지막의 observable을 새로운 observable로 만들어준다. param의 예제로는 Promise가 가능하다. 이말은 Promise도 "스트림화"가 가능하다는것이다.*/
```
그 외 여러가지 객체들이나 오퍼레이터를 사용하고 싶다면..

https://rxjs-dev.firebaseapp.com/api

-----------------------------------------------------------------------

### rxjs를 vue에서 더 편하게 사용하도록 도와주는 vue-rx

[는 여기서 소개한다.](../../../front-end/vuejs/vue-rx.md)

---------------------------------------------------------
기타 참고사항


### Hot(eager), Cold(lazy) observable
observable은 Subscriber가 있을때 이벤트가 발생하면, 이벤트를 전달한다

Hot observable은 subscriber가 없어도, 이벤트를 전달하는 로직을 실행한다

Cold observable은 subscriber가 없으면, 이벤트를 전달하는 로직을 실행하지않는다.

 

### rxjs6버전부터 바뀐 문법들
rxjs6버전 이상은 문법이 조금 바뀌었다.

operators는 이제 pipe를 통해 묶어서 사용하면된다.



Ex)
```js
myObservable
  .map(data => data * 2) //이 부분을 보세요
  .subscribe(...);
```
이런식으로 map같은 오퍼레이터들을 체이닝했지만,

rxjs6버전이상은

pipe를 통해 묶어서 써야한다.



Ex)
```js
import { map } from 'rxjs/operators';

myObservable
  .pipe(map(data => data * 2)) //이 부분이 달라졌쥬?
  .subscribe(...);
```


메소드가 아닌 함수가 되어서 import해야하고 오퍼레이터 사용도 달라졌다.

1. catch() => catchError()
2. do() => tap()
3. finally() => finalize()
4. switch() => switchAll()
5. throw() => throwError()
6. fromPromise() => from()


등등...

이전 버전을 사용하려면 npm install --save rxjs-compat 를 해주면 된다고 한다.

### Subject, Observable 차이
1. Subject는 Observable처럼 구독할수있다.
2. Subject는 Observable을 extends했다.
3. Subject는 다른 Observable을 구독할수있다는 점에서 다름.

### Reference

https://www.slideshare.net/benlesh1/rx-js-and-reactive-programming-may-2015

https://www.slideshare.net/sunhyouplee/vuejs-reactive-programming-vuetiful-korea-2nd