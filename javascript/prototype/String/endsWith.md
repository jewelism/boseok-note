# endsWith

```js
/**
 * 
 * String.prototype.endsWith(string[, length])
 * this문자열이 파라미터의 string으로 끝나는지 true, false로 리턴.
 * this문자열의 길이를 두번째파라미터인 length로 제한할수도있음.(옵션)
 */

console.log('boseok!'.endsWith('!')); // true
console.log('boseok!'.endsWith('!', 4)); // false
```