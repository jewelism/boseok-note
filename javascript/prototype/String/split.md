# split

```js
/**
 * String.prototype.split(string[, limit])
 * 
 * this문자열을 첫번째파라미터인 string으로 각각 잘라서 배열로 리턴한다.
 * 두번째 파라미터인 limit은 잘라진 배열의 길이를 제한할 수 있습니다.
 */
 console.log('boseok'.split('')); //[ 'b', 'o', 's', 'e', 'o', 'k' ]
 /**
  * 위의 예제에서 문자열을 간단하게 배열로 변경했습니다.
  * 하지만 이 방법은 좋지않습니다. UTF-16 codeunit기준으로 자르기때문이지요.
  * 아래의 끔찍한 결과를 확인해보시져!
  */
  console.log('𨭎'.split('')); //[ '�', '�' ]

/**
 *   아래의 방법들이 더 적절합니다.
 *  4개의 결과 모두 콘솔에 [ '𨭎', '1' ] 이 나올것입니다.
 * 제일 마지막 방법은 babel에 의해 트랜스파일링된 것입니다.
 */
 console.log(Array.from('𨭎1'));
 console.log([...'𨭎1']);
 console.log('𨭎1'.split(/(?=[\s\S])/u));
 console.log('𨭎1'.split(/(?=(?:[\0-\uD7FF\uE000-\uFFFF]|[\uD800-\uDBFF][\uDC00-\uDFFF]|[\uD800-\uDBFF](?![\uDC00-\uDFFF])|(?:[^\uD800-\uDBFF]|^)[\uDC00-\uDFFF]))/));
```