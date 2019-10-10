# substring

```js
/**
 * String.prototype.substring(startIndex[, endIndex])
 * 우선 substr은 deprecated입니다. 대신에 이 메소드를 사용하세요.
 * 기본적인 사용방법은 slice와 동일합니다.
 * 대신에 startIndex가 endIndex보다 크면 내부적으로 startIndex와 endIndex를 swap합니다. (slice는 그렇지않음)
 * 그리고 음수를 넣으면 차이점이 보입니다.
 */
console.log('boseok'.substring(0, 1)); //'b'
console.log('boseok'.substring(0)); //'boseok'

console.log('boseok'.substring(-1)); //'boseok'
console.log('boseok'.slice(-1)); //'k'
console.log('boseok'.substring(1, 0)); //'b'
console.log('boseok'.slice(1, 0)); //''


```