# static_from

```js
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