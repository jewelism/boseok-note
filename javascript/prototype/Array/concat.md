# concat

```js
//ES5 이하의 환경이라면 const를 var로..
const arr1 = [1, 2];
const arr2 = [3, 4];

// 배열을 합친다
console.log(arr1.concat(arr2)); // [1,2,3,4]

//ES6 환경이라면 
const newArr = [...arr1, ...arr2];
console.log(newArr); // [1,2,3,4]
```