# array-like

아래 예시의 likeArray처럼 배열처럼 생긴 객체를 유사배열이라고 한다.

유사배열은 length프로퍼티와 숫자프로퍼티로 구성됨.

```javascript
// 유사배열 - 배열이 아닌 객체인데 length 프로퍼티가 있고 배열처럼 생겼다
const likeArray = {
    length: 3,
    0: 'boseok',
    1: 'boseok1',
    2: 'boseok2',
};
// 유사배열이 배열인가?
console.log('likeArray === array?', Array.isArray(likeArray)); //false
// 유사배열을 배열로 바꿔주는 Array의 from이라는 static 메소드
const arr = Array.from(likeArray);
// from으로 변경한 배열이 진짜 배열인가?
console.log('arr === array?', Array.isArray(arr)); //true
```

중간에 인덱스가 빠져있는 것은 undefined로 처리됨을 주의.

length프로퍼티가 없는 객체는 유사배열로 바꿔도 빈 배열로 변형됨.

그래서 아래와 같은 약간의 트릭을 쓰면 유사배열을 안전하게 배열로 변형할수있다.

```javascript
const newArray = 유사배열;
newArray.length = Object.keys(유사배열).length;
Array.from(newArray); //정상적인 배열이 리턴됨
```

