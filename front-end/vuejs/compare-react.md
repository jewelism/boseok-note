## react.js와 비교

react는 css를 한번 import하면 전역으로 적용된다. 
그 말은 각각 컴포넌트가 다른 css file을 import하더라도 적용되어야 할 css의 className, 
기존에 있던 css의 className이 같다면, 중복되어서 원하는 결과가 안나온다는 것. 
className을 유니크한 값으로 해줘야함. 어차피 클래스이름을 유니크하게 하기때문에 큰 문제는 안 된다. 
그리고 component의 state가 immutable하다. 
페이스북처럼 대형 어플리케이션에서는 성능이 중요하므로 이점이 있다.
그런데 대부분의 어플리케이션에서는 state가 immutable하면 귀찮을것 같다 
별로 중요하지도않으면서 immutable.js같은 라이브러리를 사용해야하거나, 
참조를 복사하여 다시 덮어쓰는식으로 구현해야 생각하는대로 작동할것이다. 

간단하게 react와 vue에서 state의 배열에 newVal이라는 문자열을 추가해보겠습니다.
```js
//react
this.state = {
  myArr: ['oldVal']
};
this.setState({myArr: [...this.state.myArr, 'newVal']});
//vue
data: () => ({
  myArr: ['oldVal']
})
this.myArr.push('newVal');
```
차이점이 보이시나요?
하지만 js의 한계로 push하지않고 index로 배열 항목을 직접 설정하는경우
vue는 변경을 감지할 수 없습니다.

마찬가지로 js의 한계로 depth가 깊다면.. 예를 들어서
```js
//react
this.state = {
  myObj: {
    someVal: 'some',
    myArr: ['oldVal']  
  }
};
//vue
data: () => ({
  myObj: {
    someVal: 'some',
    myArr: ['oldVal']
  }
})
```
이런식이라면, vue의 경우에도 myArr.push를 하더라도,
변경을 감지할 수 없어서 다른 구현방법을 선택해야 합니다.
vue는 Vue.set을 이용할 수도 있고,
react는 immutable.js 라이브러리를 사용하면 됩니다.
혹은 첫번째 예제에서 react배열을 변경하듯이,
immutable하게 구현하면 되는 것이구요.

immutable에 대해 모르거나 헷갈린다면, 아래 링크를 참고.
https://wecodetheweb.com/2016/02/12/immutable-javascript-using-es6-and-beyond/


그렇다면 왜 react는 번거로운 방법을 선택했는가? 
object가 immutable 한것은 shallow compare를 해서 성능상 우위를 점할 수 있다. 
성능이냐 개발자편의냐 차이인데.. vue가 개발자가 편한데 성능도 더 좋다고 한다.. 
내가 react를 선택한 이유는 더 많은 개발자들이 선택했기 때문에 레퍼런스가 많다는 점이다. 
라이브러리도 당연 많고 회사에서 react를 쓸 가능성이 더 높다.
그런데 현시점(2018년 7월말)은 vue가 react의 github star수를 뛰어넘었다.
vue.js로 마음이 조금씩 넘어가는 시점이었는데, 다른 사람들도 그랬나보다. 


vue는 배우기쉽지만 아직 레퍼런스가 조금 부족한 느낌이고 
라이브러리의 선택 폭이 그닥 넓지않다. -는 몇개월전 글인데,
이제는 나름 충분한것같다. 사용하다보니 없는게 '아직'은 없다.
하지만 vuex나 vue router처럼 공식 라이브러리가 지정된 경우에는
더 편안한 느낌이다.
react같은 경우에는 상태관리라이브러리나 라우터조차도 여러개여서,
선택할때 고민을 해야한다.
vue는 대부분의 경우에는 고민할 필요없이 공식 라이브러리를 선택하면 된다.

편-안