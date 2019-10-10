# filter

```js
/** mock array */
const boseokList = [];
for (let i = 0; i < 10; i++) {
    boseokList.push({ id: i, name: `boseok${i}`, bool: i % 2 });
}

// console.log(boseokList);

// boseokList배열에서 bool프로퍼티의 값이 유효한가?
const oddList = boseokList.filter(boseok => boseok.bool);

// boseokList배열에서 bool프로퍼티의 값이 유효하지않은가? - js에서 0이나 false, null, undefined는 모두 false처럼 작동한다
const evenList = boseokList.filter(boseok => !boseok.bool);

console.log('true', oddList); //bool프로퍼티가 유효한것들만 뽑아서 다시만든 배열

console.log('not', evenList); //bool프로퍼티가 유효하지않은것들만 뽑아서 다시만든 배열
```