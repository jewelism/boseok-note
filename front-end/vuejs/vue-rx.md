## vue-rx 라이브러리

### v-stream 디렉티브

스트림의 시작점으로 사용할 수 있다.
```js
v-stream:click="myStream$"
```

### domStream

템플릿에서 사용한 스트림을
```js
domStreams: [‘myStream$’]
```
이런식으로 props처럼 써주면 인스턴스내에서 this.myStream$으로 사용할 수 있다.

vue-rx의 내부적으로 domStreams의 배열의 값들로 subject 인스턴스를 생성해주고 있다.

### subscriptions()

subscriptions 메소드는 computed라고 생각하면되는데,

observable을 subscribe하고, 데이터를 받아온다는점.

this.$watchAsObservable은 vue-rx의 내부적으로 vue의 watch를 사용하여

값이 변하는지 확인하고, observer의 next메소드를 통해 값이 변화한것을 알려준다.

$watchAsObservable를 사용하면, 데이터의 변화를 감지하여 observable로 변환시켜준다.
