# splice

```js
// 배열에 있는 요소를 제거하거나, 추가한다.
// 추가하는방법은 deleteCount에 0을 넣고, 뒤에 넣을 요소들을 추가하면 된다.
// array.splice(start, deleteCount, item1, item2, ...)
// 삭제한 배열이 있다면, 그것을 리턴한다

// mozila의 예제

var myFish = ['angel', 'clown', 'mandarin', 'surgeon'];
// index 2자리에 drum을 넣는다
var removed = myFish.splice(2, 0, 'drum'); // ['angel', 'clown', 'drum', 'mandarin', 'surgeon']
console.log(myFish, removed);
```