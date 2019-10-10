# replace

```js
/**
 * String.prototype.replace(string|regex, string|function)
 * 
 * 첫번째 파라미터에 regex와 string을 넣는것의 활용차이는 this문자열에서 매칭되는 모든 문자열을 바꿀것인가 이다.
 * 정규식의 flag에 g옵션으로 replace하면 replaceAll과 같다.
 * 문자열을 넣으면 매칭되는 첫번째문자열만 바꿔치기한다.
 * 
 * 두번째파라미터의 function을 넣을수도있다.
 * 
 * 파라미터로는 순서대로 (찾는 문자열, 찾은 인덱스, 원래 문자열)이 넘어온다.
 * 여러번 찾으면 콜백이 여러번 실행된다. 두번째파라미터인 찾은 인덱스만 바뀜.
 */

console.log('boseok'.replace('boseok', '123')); //123
console.log('boseok'.replace('o', '123')); //b123seok
console.log('boseok'.replace(/o/g, '123')); //b123se123k
console.log('boseok'.replace(/o/g, (...a) => {
  console.log(a); //[ 'o', 1, 'boseok' ] and [ 'o', 4, 'boseok' ]
  return '123';
}));  //b123se123k
```