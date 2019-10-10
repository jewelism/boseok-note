# startWith

```js
/**
 * 
 * String.prototype.startWith(string[, position])
 * 
 * this문자열이 첫번째파라미터로 주어진 string으로 시작하는지 판단해줍니다.
 * true, false리턴.
 * 
 * position은 옵션인데, 주어지지않으면 0으로 시작하고, 주어지면
 * 해당하는 인덱스부터 찾기 시작합니다.
 */

console.log('boseok'.startsWith('b')); //true
console.log('boseok'.startsWith('bo')); //true
console.log('boseok'.startsWith('o')); //false
console.log('boseok'.startsWith('o', 1)); //true
```