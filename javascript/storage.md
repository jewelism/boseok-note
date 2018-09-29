## Storage - localStorage, sessionStorage

window객체에 localStorage, sessionStorage 라는 두개의 key value 저장소가 있다. 

~~react-native(이하 rn)의 AsyncStorage와 같은 인터페이스이다. (사용방법이 같다. 리턴은 조금 다르지만)~~ 

value에는 문자열이나 숫자가 들어갈수있다(숫자도 문자열로 자동변환됨 => getItem하면 문자열로 리턴) 

이때 object를 저장하고싶다면 value에 object를
```js
JSON.stringify(object)
```
이런식으로 문자열로 변환하여 넣고, 

getItem할때
```js
JSON.parse(localStorage.getItem('someKey'))
```
해서 사용하면된다.

local은 로컬저장소를 비우지않는이상 계속 남아있지만 브라우저의 인터넷 사용기록 삭제하면 날라간다.

사용자에 하드디스크에 저장되므로 탭을 여러개 띄워도 공유가 가능하다.

당연히 브라우저나 컴퓨터를 종료했다가 다시 실행해도 값이 남아있다.

하지만 브라우저끼리의 호환은 안된다.

session은 페이지세션이 종료되면 사라진다.

(브라우저를 종료하거나.. 탭을 여러개 띄워놓고 공유가 안됨. 각각의 세션 스토리지가 생김)

```js
localStorage.setItem('boseok', 'boseok`s message!!!') 

console.log(localStorage.getItem('boseok')) //boseok's message!!! 
```
위와같은 결과를 얻을수있다 

rn에서는 getItem과 setItem이 Promise를 리턴한다. (비동기) 

하지만 js의 window객체- 에서는 동기적으로 리턴한다 


정리- 

localStorage, sessionStorage 키값 저장소가 있음.

비동기api가 아니라서 큰 값 저장하기에는 무리가 있음.

큰 값을 저장하고 싶다면 indexedDB등의 DB를 사용

getItem(문자열키) 

setItem(문자열키, 저장할문자열값) 

그외의 메소드들 

removeItem(key) => 아이템 한개 삭제

clear(key) => this storage 모두 삭제 