## 동기와 비동기

javascript에는 Worker API를 제외하면 멀티스레드를 활용할 수 없다.

애초에 설계가 싱글스레드기반이다.

싱글스레드이기때문에, 한번에 한가지 작업밖에 할수없는데,

DOM을 제어하다가 시간이 오래걸리는 로직을 만나게되면,

ui가 멈추게된다. 이런 문제를 해결하기위해 비동기라는 기술이 생겼다.

먼저 동기, 비동기의 장단점을 보자.

----------------

### 비동기의 장점

```
한정된 자원을 효율적으로 사용할 수 있다.
```

### 비동기 단점

```
동기식 코드보다는 복잡하다.
상대적으로 가독성이 떨어진다.
설계가 어렵다
```

### 동기의 장점

```
프로그램의 흐름을 순차적으로 코딩할 수 있다.
디버깅이 쉽다.
```


### 동기의 단점
```
비동기에 비해 한정된 자원을 효율적으로 사용하지 못한다.
```

----------------

다시 돌아와서 비동기는 싱글스레드인데,

어떻게 많은 작업을 처리할 수 있을까.

비동기함수는 단순히 작업을 뒤로 미루는것이다.

자바스크립트라고해서 모든 코드가 비동기로 작동하는 것은 아니고,

비동기함수만 비동기로 작동한다.

이 말은 js에서 동기적인 코드는 순차적으로 실행되다가,

비동기 함수를 만나게되면, 그냥 뒤로 미뤄버린다. (비동기끼리도 순서가 있는데, 아래에서 소개하겠다)

그래서 동기적인 코드들이 먼저 다 실행되고, 비동기가 실행되므로,

ui blocking을 해결할 수 있다.

동기적인 로직들이 너무너무 커서, 다른 스레드의 힘을 빌려야할때 [Worker API](../javascript/api/worker-api.md)를 사용하면 된다.