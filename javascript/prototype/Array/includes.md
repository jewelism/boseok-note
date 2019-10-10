# includes

```js
const arr = [1, 2, 3];
// this 배열이 파라미터의 값을 포함하는가?
console.log(arr.includes(1)); // true 
console.log(arr.includes(4)); // false

// indexOf로 includes를 구현해보고,
// indexOf로 쉽게 구현할수있는데 왜 이 메소드가 필요한지 생각해보자!

console.log(arr.indexOf(1) > -1);
// 위의 문장으로 indexOf를 대체할수있는데, 왜 includes가 필요할까?
// 개인적인 생각으로는, 코드를 작성하고 나면 여러사람들이 코드를 보게된다.
// arr.indexOf(1) > -1 이런 식은 익숙하지않다면 한눈에 잘 안들어온다
// arr.includes(1) 이것은 어떤의미인지 명확하다. 혼동될일이 없으며
// indexOf로 includes를 구현하다가 실수 할 일이없다.
// 예를들어서 어떤 개발자는 arr.indexOf(1) > 0 으로 구현할수도있다.
// 대부분의 경우에는 작동하지만 찾고있는 1이라는 숫자가 0번째 index에 위치해있다면,
// arr.indexOf(1) > 0는 0을 return 할 것이고, 그것을 만약에 if 문 내에 작성했다면..
// if(arr.indexOf(1) > 0) //이 구문은 결국
// if(0) //이므로 false처럼 작동하므로 if내부의 코드가 실행되지않아 버그를 유발하게된다
```