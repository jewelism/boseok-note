# 이벤트루프 \(Event Loop\)

js는 싱글스레드인데 동시에 많은 이벤트들을 어떻게 처리할까?

이벤트루프는 js의 메인스레드이고 싱글스레드이다.

이벤트루프는 콜스택과 태스크큐를 지켜보고있다가 콜스택이 비어있으면

태스크큐에서 첫번째 이벤트를 콜스택에 넣어주는 일을하고, 그것을 tick이라고한다.

콜 스택이 비어 있고 태스크 큐에 콜백 함수가 있는 경우, 함수는 큐에서 제외되고 실행될 콜 스택으로 푸시됩니다.

이벤트루프는 ECMAScript의 스펙이 아니다. 구동 환경측에서 구현해야한다.

그래서 노드는 비동기 io를 지원하기 위해 libuv라이브러리를 사용하는것이다.

브라우저도 마찬가지로 자바스크립트 엔진외에 별도 구현체가 있을것이다.

이 말은 자바스크립트 엔진은 하나의 콜스택만 사용한다는 뜻이다.

결국 자바스크립트는 싱글스레드이므로 block되는 코드가 존재한다면 그냥 block된다.

