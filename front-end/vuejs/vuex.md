## vuex

facebook의 flux 패턴과 매우 유사하다.
 
단방향 데이터흐름을 갖고있으며, 용어도 거의 같다.

흐름을 정리하자면, 

컴포넌트 => 비동기로직 => 동기로직 => 상태 이다. 

다시 정리하면, 

Component(View) => Actions => Mutations => State 

vue에서 컴포넌트의 상태를 data라고 한다. 

vuex에서 어플리케이션의 상태를 state라고 한다. 

비동기 로직은 actions에서. 

component에서 비동기로직(actions)을 dispatch 한다. 

비동기로직에서 동기로직으로 commit 한다. 

이 과정들을 통해서 app의 state가 바뀌면 re-render한다. 

간단한 counter를 만들어놓은 예제

https://github.com/jewelism/vuex_vue-router_example/tree/master/src/store