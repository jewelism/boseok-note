# match

```js
/**
 * String.prototype.match(regex)
 * 
 * 파라미터는 정규식이다.
 * new RegExp() 를 넣어도 되고, /정규식/g 이런식으로 넣어도 된다.
 * /ab+c/i;
 * new RegExp('ab+c', 'i');
 * 같은 결과를 나타낸다. 
 * ES6 에서는 new RegExp(/ab+c/, 'i'); 이렇게도 사용할수있다.
 * 두가지 방법이 있는이유는 생성자 방식은 어떤패턴을 사용할지 정확히 알수없는경우- 사용자입력 등으로 생성되어서, 런타임방식으로 컴파일되게 한다.
 * g라는 위치는 정규식을 문자로 나타냈을때의 flag인데,
 * 아래의 의미를 나타낸다. /식/gi 이런식으로 이어서쓴다.
g
global match; 일치하는 첫 번째 문자에서 멈추지 않고 전체에서 일치하는 모든 문자를 검색합니다.
i
ignore case(대소문자를 구별하지 않습니다.)
m
multiline; 시작 혹은 끝 문자 탐색(^ and $)이 다중행에 적용되도록 합니다.  (예로,  \n 혹은 \r로 개행된 각각의 라인 시작 혹은 끝 뿐만 아니라, 전체 입력 문자의 시작 혹은 끝에서 일치합니다.
y 
sticky; matches only from the index indicated by the lastIndex property of this regular expression in the target string (and does not attempt to match from any later indexes).

 * 이 메소드를 이해하려면 정규식에 대한 이해가 먼저 필요하다.
 * 
 * 문자열에 패턴이 매칭되면 배열에 일치하는 값을 담아서 리턴해준다.
 * 일치하는 문자열이 없으면 null을 반환한다.
 */


if('boseokA'.match(/[A-Z]/gim)){
  console.log('matched');
} else {
  console.log('not matched');
}





```