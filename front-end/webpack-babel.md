# Webpack과 babel

## Webpack 등장배경

현대 브라우저나 자바스크립트는 자체적으로 모듈시스템이 있습니다.

하지만 그것이 없던 시절.. IIFE을 활용한 모듈패턴 외에는 딱히 파일단위 모듈시스템을 사용하는게 쉽지않았고..

그리고 웹 프로젝트가 커질수록, 자바스크립트 파일을 하나로 관리하는데 한계가 있었으므로, 여러개의 자바스크립트로 나눠서 개발을 하는데

그마저도 각 파일들의 스코프 침범이나, 변수 충돌등에서 자유롭지 못했습니다.

또, 자바스크립트의 파일이 여러개 생기고, 사이즈가 커질수록 네트워크통신에서 불리하기때문에, 비용을 최소화할 방법이 필요했죠.

그것을 webpack이 해결해줍니다.

## Webpack

Webpack은 쉽게말하면 번들러입니다.

webpack은 설정에 따라 정적파일을 합쳐주고 관리하는등 여러가지 일을 자동으로 해주는 모듈번들러입니다.

보통 라이브러리들을 합친 js파일, 작성한 코드 파일. 이렇게 두개의 작은 사이즈로 번들링된 파일을 제공합니다.

웹팩이 관리하기 힘든 부분은 *로더*라는 친구가 도와준다.(번들링전 헬퍼) css-loader가 대표적이다.

*플러그인*은 번들링 후 헬퍼이다. 로더와 비슷하게 여러가지일들을 할수있다. uglify라던지.

## Babel

바벨은 트랜스파일러이자 컴파일러다. (컴파일이라는 용어가 더 큰 범주이다.)

보통, ES6+문법을 ES5문법으로 바꿔서, 기존 브라우저의 호환성을 목적으로 사용한다.

그외에는 stage단계에 있는 문법들(표준 제안)이나 jsx, typescript를 위해 사용하기도 한다.

https://babeljs.io/ => REPL을 구현해놨으니 간단한 문법을 테스트해볼수도 있다.

