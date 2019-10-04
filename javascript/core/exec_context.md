## 실행컨텍스트

실행컨텍스트란 실행 가능한 코드를 형상화하고 구분하는 추상적인 개념이다.

컴파일단계에서 전역 컨텍스트가 생기고 [호이스팅](hoisting.md)이 일어난다.

~~ES6는 함수레벨과 블록레벨의 렉시컬스코프이다.~~

함수마다 각각의 함수 컨텍스트가 생성된다.

그리고 함수가 리턴하면 그 함수의 컨텍스트가 사라진다.

전역 컨텍스트는 프로그램이 종료되면 사라진다.

각 컨텍스트객체에는 <b>VO, scope chain, this</b> 라는 3가지 프로퍼티가 생성된다.

-------------------------

VO(Variable Object) - [arguments](arguments.md), parameter를 포함한 variable이 존재

scope - 함수객체가 접근가능한 VO의 유효범위



[추가적으로 참고할만한 좋은 글](https://velog.io/@tmmoond8/%ED%94%84%EB%A1%A0%ED%8A%B8%EC%97%94%EB%93%9C-%EA%B0%9C%EB%B0%9C%EC%9E%90-%EC%9D%B8%ED%84%B0%EB%B7%B0-%ED%9B%84%EA%B8%B0-%EB%A9%B4%EC%A0%91-%EC%A7%88%EB%AC%B8-%EC%A0%95%EB%A6%AC-%EC%9E%91%EC%84%B1-%EC%A4%91#5.-%EC%8B%A4%ED%96%89%EC%BB%A8%ED%85%8D%EC%8A%A4%ED%8A%B8)