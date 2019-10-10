# Array.prototype.map

이 메소드는 배열을 하나씩 순회하며, callback으로 하나씩 값을 뱉어준다.
그리고 callback이 return 하는 값들로 새로운 배열을 만들어서 return한다.

```js
const arr = [1, 2, 3];
const newArr = arr.map(n => n * 2);
console.log(newArr); //[2, 4, 6]
```