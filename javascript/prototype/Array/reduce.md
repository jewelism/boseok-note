# reduce

```js
// mozila reference
// 배열의 각 요소마다 누적 계산값과 함께 함수를 적용해 하나의 값으로 줄입니다.
// 쉽지않쥬?
// https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce

// accumulator: 현재 누적값
// currentValue: 배열에서 현재 요소
// currentIndex: 배열에서 현재 요소의 index
const total = [0, 1, 2, 3].reduce((accumulator, currentValue, currentIndex) => {
  return accumulator + currentValue;
});
console.log(total); //6


// reduce와 reduceRight 차이점
var a = ["1", "2", "3", "4", "5"]; 
var left  = a.reduce(function(prev, cur)      { return prev + cur; }); 
var right = a.reduceRight(function(prev, cur) { return prev + cur; }); 

console.log(left);  // "12345"
console.log(right); // "54321"
```