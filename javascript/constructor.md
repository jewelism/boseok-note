# Constructor \(생성자\)

```javascript
function Boseok(age) {
    this.age = age;
}
```

그냥 함수로 호출하는것과, new 연산자로 객체를 생성하는것에 무슨 차이가 있는지 볼까여?

```javascript
const boseok = Boseok(123);
console.log(boseok.age); //error
```

당연히 예상처럼 함수에 리턴하는게 없으므로 boseok객체는 undefined입니다.

그래서 age를 참조할수없는 에러를 뿜어냅니다.

하지만 new 연산자를 사용하면 다르게 작동합니다.

```javascript
const boseok = new Boseok(123);
console.log(boseok.age); //123
```

new 연산자를 사용하면 함수를 생성자로 호출합니다. 명시적인 return 구문이 없다면, this가 가리키는 객체를 반환합니다.

new Boseok\(\)은 Boseok.prototype을 상속받은 new 연산자를 사용하여 Boseok 객체의 인스턴스를 생성합니다.

그래서 또 다른 방법으로 인스턴스를 생성하는 방법은 아래와 같습니다.

```javascript
Object.create(Boseok.prototype)
```

생성자에 객체를 만들어서 명시적으로 return하면 new 연산자에 관계없이 동작하는 생성자를 만들 수 있습니다.

new 키워드가 빠졌을때 발생하는 this 참조 에러를 예방할 수 있습니다.

팩토리를 사용했을때는 위처럼 장점도 있지만, 단점도 존재합니다.

```text
prototype으로 메소드를 공유하지 않으므로 메모리를 좀 더 사용한다.
팩토리를 상속하려면 모든 메소드를 복사하거나 객체의 prototype에 객체를 할당해 주어야 한다.
new 키워드를 누락시켜서 prototype chain을 끊어버리는 것은 아무래도 언어의 의도에 어긋난다.
```

