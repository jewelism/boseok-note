# 4. 컴포넌트 고급 & 이벤트

저번에 컴포넌트 추가하는방법을 익혔습니다!

그렇다면 이제 컴포넌트에 대해 좀 더 자세히 알아보도록 합시다.

### 배경지식

컴포넌트 기본에서 언급했던 것과 같이, vue.js에서 컴포넌트는 vue객체일뿐입니다.

싱글파일컴포넌트로 컴포넌트를 생성할때,

```js
export default {
  ...
};
```
이런식으로 객체를 생성하고, export 합니다.

그냥 객체일뿐인데, 메소드나 라이프싸이클훅에서 this를 콘솔에 찍어보면,

vue객체가 됩니다.

export 하고나서 컴포넌트를 바인딩하기전에,

vue 라이브러리 내부에서 뭔가 처리해주는게 틀림없습니다.

-------------------

### 단방향 데이터 플로우

최신 ui 라이브러리(react, vue)가 채택하고있는 데이터플로우는 단방향입니다.

기본적으로는 부모컴포넌트에서 자식으로 데이터를 내려주고, 자식은 받아서 렌더링만 하는게

권장되는방법입니다.

그런데 개발하다보면, 꼭 그렇게만 할수없을때도 있습니다.

자식에서 부모컴포넌트로 데이터를 돌려줘야할때도있고.. props로 받은 데이터를 수정하고 싶을때도 있습니다.


### 이벤트버스

이렇게 난처할때, 사용할 수 있는게 vue.js에서는 이벤트입니다.

vue.js는 친절하게도 이벤트 인터페이스를 아주 편하게 구현해놨습니다. 사용만 하면됩니다.

@input, @change 이런걸 보신적있나요? 이런게 모두 이벤트입니다.

@가 v-on의 축약형이란걸 알게되는순간, 아~ 하고 이해하게됩니다.

아래서 설명하고있지만 이벤트는 emit으로 쏘고, on으로 받거든요.

```js
this.$emit('change')
```

를 통해서 상위컴포넌트로 이벤트를 전달할 수도 있죠.
(상위컴포넌트에서 @change, 혹은 $on으로 받습니다)

여기에서 this는, vue객체겠죠. 여기서 이벤트버스를 사용할 수 있는 힌트를 얻었습니다.

$emit으로 이벤트를 전달하고 $on으로 받는다고했죠?

그리고 그 두개의 메소드는 vue객체의 메소드죠.

그러면 이제 main.js처럼 entry point에 이벤트버스를 생성해보겠습니다.

```js
// ...some code
import Vue from 'vue';
Vue.prototype.$eventBus = new Vue();
// ...some code
```

쨘! 이렇게하면 모든 vue객체에서 $eventBus로 접근하여 이벤트버스를 사용할수 있습니다!

```js
this.$eventBus.$emit
this.$emit
```


이렇게 두개의 이벤트를 사용할 수 있게 됐습니다.

프로토타입에 등록한 $eventBus는 부모자식 상관없이 이벤트를 주고 받을 수 있습니다.

그런데 this.$emit은 자기 자신의 부모컴포넌트 '인스턴스'로만 이벤트를 쏘게됩니다.