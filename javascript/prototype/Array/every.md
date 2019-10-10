# every

```js
/** mock array */
const boseokList = [];
for (let i = 0; i < 10; i++) {
    boseokList.push({ id: i, name: `boseok${i}`, bool: i % 2, realName: 'boseok' });
}

console.log(boseokList);
// boseokList 배열의 모든 realName 프로퍼티가 'boseok' 문자열인가?
const isAllBoseok = boseokList.every(boseok => boseok.realName === 'boseok');
// boseokList 배열의 모든 name 프로퍼티가 'boseok1' 문자열인가?
const isAllBoseok1 = boseokList.every(boseok => boseok.name === 'boseok1');

console.log(isAllBoseok); //true
console.log(isAllBoseok1); //false
```