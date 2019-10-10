# indexOf

```js
// mozila reference
// 배열에서 지정된 요소를 찾을 수있는 첫 번째 index를 return, 존재하지 않으면 -1을 return (앞에서부터 순서대로)
// lastIndexOf는 indexOf와 같지만, 뒤에서부터 순서대로 찾는다는점이 다르다
var a = [2, 9, 9]; 
a.indexOf(2); // 0 
a.indexOf(7); // -1

if (a.indexOf(7) === -1) {
  // 요소가 배열에 존재하지 않습니다.
}
```