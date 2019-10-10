# slice

```js
/**
 * String.prototype.slice(beginIndex[, endIndex])
 * 
 * this문자열을 잘라서 리턴한다.
 * beginIndex가 this문자열길이 이상이면 빈문자열을 리턴한다.
 * 만약 음수를 넣는다면 this.문자열의 길이 -음수로 처리한다.
 * 양수를 넣으면 그 인덱스부터 끝까지의 문자열을 리턴한다.
 * 두번째파라미터를 넣는경우 어디까지 자를것인지 정할수있다.
 */

 const boseok = 'boseok';
 console.log(boseok.slice(-1)); //'k'
 console.log(boseok.slice(1)); //'oseok'
 console.log(boseok.slice(1, 3)); //'os'
 console.log(boseok.slice(6)); //''

```