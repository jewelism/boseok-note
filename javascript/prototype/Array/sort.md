# sort

```js
// 배열을 정렬한다
// callback으로 정렬방법을 지정할수도있다

const numArr = [3, 2, 1];
numArr.sort();
console.log(numArr); // [1,2,3]

const objArr = [
  { id: 1, name: 'boseok1', age: 15 },
  { id: 2, name: 'boseok2', age: 16 },
  { id: 3, name: 'boseok3', age: 17 },
  { id: 4, name: 'boseok4', age: 18 },
  { id: 5, name: 'boseok5', age: 19 },
];

objArr.sort((obj, obj2) => {
  return obj.id < obj2.id; //값이 큰것을 앞으로 보낸다.
});
console.log(objArr); // id가 5인것부터 1까지 순서대로 나온다.

/////////////////////////////////////

const objArr2 = [
  { id: 1, name: 'boseok1', age: 15 },
  { id: 2, name: 'boseok2', age: 16 },
  { id: 3, name: 'boseok3', age: 17 },
  { id: 4, name: 'boseok4', age: 18 },
  { id: 5, name: 'boseok5', age: 19 },
];
objArr2.sort((o, o2) => o.age < o2.age); //나이가 많은순서로 정렬
console.log(objArr2);
```