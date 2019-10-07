# 클로져\(Closure\)

함수와 그 함수가 선언될 당시의 환경정보 사이의 조합이라고 설명합니다.

최초 선언시의 정보들을 유지할 수 있습니다.

클로저는 자바스크립트에서 함수를 만들면 생성된다.

함수내에 inner함수를 만들고, outer함수의 변수를 참조하게만들면,

outer함수가 리턴되더라도, outer함수내의 변수가 살아있게된다.

클로저가 형성되면, 그 내부의 환경을 기억하는 것이다. =&gt; 스코프와 밀접한 관련

\(참고 - java언어에서는, final로 선언된 constant만 내부함수에서 참조가 가능하게 되어있다\)

아래는 아주 간단한 예제이다.

```javascript
function createClosure(v) {
  var v1 = v;
  return function() {
    return v1;
  }
}

var c1 = createClosure(1);
console.log(c1()); //1
var c2 = createClosure('boseok');
console.log(c2()); //"boseok"
```

이렇게 구현하면 형성된 클로저의 v1변수값을 얻을수있는데,

v1변수를 직접 참조할 수는 없다. =&gt; private 변수

## 메모리와 GC

가비지콜렉터가 그 변수를 회수하지않기때문에, 메모리관리에 주의해야한다.

왜 가비지 콜렉터가 그 변수를 회수하지않을까?

직접 접근하지는 못하지만, 닿을 수 있는 오브젝트이기 때문이다.

닿을 수 있는 오브젝트는 gc의 대상이 아니다.

"더 이상 필요없는 오브젝트" == "닿을 수 없는 오브젝트"

아래는 클로저를 이용한 모듈패턴으로,

private변수를 만들수있고, 클로저를 설명하는 대표적인 예시이다.

```javascript
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
counter.increment(2);
counter.value(); //2
counter.privateCounter; //undefined
```

하지만 클로저를 활용하는동안 GC가 메모리를 회수할수없다.

카운터를 만들때마다 각각의 카운터의 인스턴스는 privateCounter를 생성하므로 메모리낭비이다.

그러므로 다 사용하고나면 counter에 null을 대입하여 gc가 작동할수 있도록 해줘야한다.

```javascript
counter = null;
```

