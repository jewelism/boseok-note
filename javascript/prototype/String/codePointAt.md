# codePointAt

```js
/**
 * String.prototype.codePointAt(index)
 * 
 * fromCodePoint와 반대되는 프로토타입 메소드
 */

var icons = '☃★♲';

console.log(icons.codePointAt(1)); //9733

console.log(String.fromCodePoint(9733)); //★
```