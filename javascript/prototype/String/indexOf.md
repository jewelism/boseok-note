# indexOf

```js
/**
 * 
 * String.prototype.indexOf(searchString[, fromIndex])
 * 
 * this문자열에서 첫번째로 나타나는 searchString문자열을 찾고, 그 위치를 반환한다. 
 * fromIndex옵션은 어디서부터 찾을지 위치를 정할수있다.
 * 
 * 문자열이 없으면 -1 리턴
 */

console.log('boseok'.indexOf('b')); //0
console.log('boseok'.indexOf('b', 1)); //-1
```