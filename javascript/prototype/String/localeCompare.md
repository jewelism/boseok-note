# localeCompare

```js
/**
 * String.prototype.localeCompare(string)
 * 
 * 문자열끼리 비교하는데, 문자열을 순서대로 비교하여 같으면 0을 리턴,
 * 뒤에있으면 양수, 앞에있으면 음수를 리턴한다.
 * 앞, 뒤의 기준이 명확하진않지만 UTF-16기준인듯하다.
 * 
 * 사실 두번째, 세번째 파라미터도 있지만 내용이 많고 헷갈리기쉽다.
 * 공식문서를 참고할것
 * 
 * https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/localeCompare
 */

var a = 'réservé';
var b = 'RESERVE';
var c = 'reserve';
var d = 'reserve';

console.log(a.localeCompare(b)); //1
console.log(c.localeCompare(b)); //-1
console.log(d.localeCompare(b)); //0
```