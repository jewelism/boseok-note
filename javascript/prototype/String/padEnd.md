# padEnd

```js
/**
 * ES2017 스펙
 * 
 * String.prototype.padEnd(int, string)
 * 
 * 문자열에서 int-문자열길이만큼 string을 뒤에 붙여서 리턴한다.
 * string이 주어지지않았다면 ' '로 표기된다.
 */

const str = '100';
console.log(str.padEnd(4), ','); //'100,'
console.log(str.padEnd(4)); //'100 '
console.log(str.padEnd(2)); //'100'
console.log(str.padEnd(0)); //'100'
console.log(str.padEnd(-1)); //'100'
```