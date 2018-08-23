## 성능 최적화

### 1. 컴포넌트에서 사용하는 함수정의

어느정도 react의 기본개념을 알고있는 사람만 포스트를 이해할 수 있다. 

react는 화면을 다시 그릴때, render함수를 호출한다. 

그런데 render내에서..새로운 함수를 만들어서 넘기는경우.

```js
onClick={() => doSomething()}
```

위와같은 코드가 있다고하자.

이렇게 구현하게되면 render함수를 호출할때마다(컴포넌트를 re-render할때마다)

새로운 함수를 생성하는 것인데, 이 부분에서 생각치못한 미미한 성능하락이 생긴다.

이것을 단순히 컴포넌트의 함수로 빼내면 해결된다. 

```js
doSomething = () => doSomethingAwesome();
onClick={this.doSomething}
```
 
이런식으로 컴포넌트의 함수를 binding.

겉으로 보기엔 같을지도 모르겠지만, react의 내부 메커니즘을 모른다면,

이런 사소한(?) 성능이슈는 놓치고 넘어가기 쉽다. 


### 2. react 라이프사이클 이용

react는 react만의 최적화 기법이 있다.
 
lifecycle 메소드를 이용하는 방법이다. 

우선 react는 state, props가 변경되면 해당 컴포넌트를 다시 렌더링한다. 

react의 shouldComponentUpdate lifecycle method에는 nextProps, nextState가 순서대로 파라미터에 전달된다. 

파라미터 이름만봐도 대충 짐작이 간다. 

현재 state와 props 전달받은 state와 props를 비교할수있다. 

컴포넌트를 다시 그리고싶다면 true를 리턴하면되고, 최적화를 위해 리렌더링을 하기싫다면- false를 리턴하면된다. 

더 자세히 알고싶다면 공식문서를.. 

https://reactjs.org/docs/react-component.html#shouldcomponentupdate 

state와 props 구조가 단순하고, 구현하기귀찮다면 

클래스에 Component를 상속받지말고, PureComponent를 상속받으면 된다. 

PureComponent에는 shouldComponentUpdate 메소드가 이미 구현되어있다. 

react 개발자 중 한명은 PureComponent를 사용하는것을 권장하지않는다.

곧 react가 버전업하게되면, 함수형 컴포넌트의 성능을 향상시킬 것이라고 한다. 

컴포넌트에 lifecycle이 필요없다면 함수형 컴포넌트를 사용하도록 하는것이 향후에 

성능을 좋게 하는 방법이라고 할 수 있겠다. 