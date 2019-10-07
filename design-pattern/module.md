# Module 패턴

초기 자바스크립트의 설계에는 없던 모듈시스템덕(?)에 생겨난 디자인패턴이다.

자바스크립트 파일을 하나로 관리하는데는 한계가 있었으므로, 여러개로 나눌수밖에없었는데

각 파일들은 서로의 스코프를 침법하거나 변수의 충돌이 일어나면 안된다.

그래서 IIFE를 통해 모듈패턴을 적용하여, 모듈을 만들어서 사용한다.

예제를 보면 클로져와 매우 밀접한 관계가 있음을 알수있다.

[요기있던 예제..](../javascript/core/closure#gc)

```js
var counter = (function() { 
  var privateCounter = 0; 
  function changeBy(val) { 
    privateCounter += val; 
  } 
  return { 
    increment: function(val) { 
      changeBy(val); 
    }, 
    value: function() { 
      return privateCounter; 
    } 
  }; 
})();

counter.value(); //0
counter.increment(2)
counter.value(); //2
counter.privateCounter; //undefined
```

특정 변수들의 접근을 제한할 수도 있고, 내부안으로 다른 변수들이 접근하는것 또한 막을수있다.