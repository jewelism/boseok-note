# toLocaleLowerCase

```js
/**
 * String.prototype.toLocaleLowerCase(option)
 * 
 * this 문자열을 모두 소문자로 바꿔서 리턴합니다.
 * option파라미터로 locale을 정할수있는데, 여러개의 locale을 넣는다면, 
 * best locale을 자동으로 선택한다고하네요.
 * 기본 locale은 해당호스트의 locale입니다.
 */

 console.log('BOSEOK'.toLocaleLowerCase('us')); //'boseok'
```