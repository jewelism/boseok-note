# prototype

보통 클래스 스타일의 상속 모델을 사용하는데, 자바스크립트는 역시나 특이하게도 프로토타입 상속모델을 사용합니다.

스코프에도 체인이 있듯이, 프로토타입에도 체인이 있습니다.

이것으로 상속을 구현합니다.

## 프로토타입 체인

자바스크립트 콘솔에서 객체를 열어본적 있으신가요?

```javascript
console.log(window);
```

이렇게 객체를 콘솔로그를 남기고 열어보시면,

window객체의 수많은 프로퍼티들과 프로토타입, `__proto__` 프로퍼티가 있는걸 확인할수있습니다! \(예제에서는 빈 객체이므로 프로토타입 체인만 보입니다.\)

아래는 자바스크립트로 구현한 Linked List의 일부분입니다.

```javascript
function LinkedList() {
  this.head = null;
  this.length = 0;
}

LinkedList.prototype.add = function (data) {
  const node = new Node(data);
  let current = this.head;
  if (current) {
    while (current.next) {
      current = current.next;
    }
    current.next = node;
  } else {
    this.head = node;
  }
  this.length++;
  return this;
}
```

6라인을 보시면 LinkedList function 프로토타입에 add라는 프로퍼티가 있죠?

프로토타입은 보통 이런식으로 사용합니다.

add에 함수를 할당했으니, add라는 _인스턴스메소드_가 생긴거죠.

```javascript
new LinkedList().add()
```

이런식으로 인스턴스메소드를 사용할 수 있겠구요.

프로토타입 체인은,

```javascript
LinkedList.prototype = 1;
```

프로토타입 체인을 만드는데 사용하고 어떤값이든 넣어도 괜찮지만,

위 코드처럼 primitive 값을 대입하면 무시됩니다.

당연한 이야기겠지만 위의 사용법이 좋다고해서 인스턴스 프로퍼티를 막 만들면 좋지않습니다.

프로퍼티 탐색시간이 있기때문이죠

```javascript
const {document} = window;
```

## 프로토타입 탐색

객체의 프로퍼티를 참조하려고하면 js엔진은 해당 이름을 가진 프로퍼티를 찾을때까지

프로토타입 체인을 거슬러 올라가면서 탐색합니다.

없는 프로퍼티를 참조하려고하면, 프로토타입 체인 전체를 탐색합니다.

## hasOwnProperty

어떤 객체의 프로퍼티가 자기 자신의 프로퍼티인지, 프로토타입 체인에 있는것인지 확인하는 메소드입니다.

hasOwnProperty메소드는 프로토타입 체인을 탐색하지 않고 프로퍼티를 다룰수있는 유일한 방법입니다.

for in 문으로 객체를 탐색할때, 적절히 사용할 수 있다.

```javascript
//공통코드
Object.prototype.c = 3;
const obj = { a: 1, b: 2 };
```

```javascript
// 예제1
for(let key in obj) {
  if(obj.hasOwnProperty(key)) {
    console.log(key);
  }
}
// output
// a
// b
```

```javascript
// 예제2
for(let key in obj) {
  console.log(key);
}
console.log(obj); // { a: 1, b: 2 }
// output
// a
// b
// c
```

브라우저마다 객체 순회 방법이 달라서 iteration 순서는 중요하지않지만, c가 출력되는것이 문제가 되는 경우도 있다.

## 프로토타입을 사용할때 주의해야할점

프로토타입 체인이 너무 길지 않도록 적절히 사용하고

polyfill이나 ponyfill 같은 목적이 아니라면 네이티브 프로토타입을 확장하지말것 =&gt; Monkey Patching =&gt; 캡슐화를 망친다.

