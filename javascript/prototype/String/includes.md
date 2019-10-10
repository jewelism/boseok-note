# includes

```js
/**
 * ES6 스펙
 * String.prototype.includes(searchString[, position])
 * 
 * this문자열에서 searchString이 포함되어있으면 true, 아니면 false 리턴.
 * 두번째파라미터는 옵션인데, position에 해당하는 index부터 찾는다.
 * 
 * 사실 이 메소드는 indexOf로 대체가 가능하긴하다.
 * 이 메소드가 나온이유를 추측해보면 당연히 편리성이다.
 * 
 * 예를들면 아래와 같은 코드를 보자.
 * 
 * const isIncludes = 'boseok'.indexOf('b');
 * if(isIncludes) {
 *  console.log('문자열 찾음');
 * } else {
 *  console.log('문자열 없음');
 * }
 * 
 * 헷갈리쥬?
 * 문자열을 찾았는데 해당 인덱스가 0이라서, if가 true가 아니고, false에 해당하므로
 * 문자열이 없다고 콘솔에 찍히는데, 이런 사소한 실수를 범할수있기때문에, includes가 나온것이 아닌가..ㅎㅎ
 * 
 * if에 -1같은걸 비교하는 로직이 들어가면 가독성이 살짝 불편해질수도있다.
 * 그래서 ES6환경에서는 includes를 선호한다. 
 */

 console.log('boseok'.includes('b'));
 console.log('boseok'.includes('b', 1));
```