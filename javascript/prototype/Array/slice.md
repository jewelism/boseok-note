# slice

```js
// mozila의 설명 : slice() 메소드는 어떤 배열의 begin부터 end까지(end는 불포함)에 대한 
// shallow copy를 새로운 배열 객체로 반환합니다. 원본 배열은 수정되지 않습니다.
// 여기서 shallow copy라는건 배열의 요소의 copy방법을 뜻한다.
// 증거와 예제는 아래의 arr, newArr 를 참고하자
// 예제를 봐도 shallow copy가 헷갈리거나 혼동되면 나중에 다시 공부하세요

// 배열을 copy하여 새로운 배열을 생성한다.
// 파라미터로 시작과 끝을 정할수있는데, 끝은 포함되지않는다
// 이해되지않는다면, 예제에서..

const o = { name: 'boseok' };
const o2 = { name: 'boseok2' };
const arr = [o, o2];
const newArr = arr.slice(1,2);
console.log('기존배열', arr);
console.log('복사한배열', newArr);
o2.id = 1; //배열의 객체를 수정해보자.
console.log('==========================');
console.log('기존배열', arr); //기존배열은 당연히 o를 포함하기때문에 배열의 값이 같이 바뀌어야한다.
console.log('복사한배열', newArr); //deep copy였다면 내부의 값까지 통째로 복사했기때문에 바뀌지않아야하는데, shallow라서 배열의 요소 객체의 프로퍼티가 변경된다

```