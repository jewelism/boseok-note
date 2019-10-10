# some

```js
/** mock array */
const boseokList = [];
for (let i = 0; i < 10; i++) {
    boseokList.push({ id: i, name: `boseok${i}`, bool: i % 2 });
}

console.log(boseokList);

// 리스트에서 값을 하나씩 뽑아낸 객체(boseok) 에서 id값을 비교해서 하나라도 일치하면 true, 이경우에는 true
const hasId = boseokList.some(boseok => boseok.id === 1);
// 리스트에서 값을 하나씩 뽑아낸 객체(boseok) 에서 id값을 비교해서 하나라도 일치하면 true, 이경우에는 false
const hasId2 = boseokList.some(boseok => boseok.id === 11);

console.log(hasId, hasId2);
```