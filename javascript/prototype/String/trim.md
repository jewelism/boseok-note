# trim

```js
/**
 * String.prototype.trim()
 * 
 * this문자열의 양끝(시작과 끝)에서 공백을 제거하고 새롭게 만들어진 문자열을 리턴합니다.
 * 유사한 trimRight, trimLeft도 있습니다. 
 * trimStart, trimEnd도 있지만 node.js에서는 동작하지않습니다.
 */

 console.log('    boseok  '.trim()) //'boseok'
 console.log('    boseok  '.trimRight()) //'    boseok'
 console.log('    boseok  '.trimLeft()) //'boseok  '
```