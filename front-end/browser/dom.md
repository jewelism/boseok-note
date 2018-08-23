## DOM(Document Object Model)

DOM은 HTML과 XML의 인터페이스다.

웹 페이지를 스크립트 또는 프로그래밍 언어들에서 사용될 수 있게 연결시켜주는 역할을 담당

웹 페이지는 일종의 문서같은 것인데,

웹 브라우저는 그 문서를 해석하여 화면에 그려준다.

W3C DOM는 대부분의 브라우저에서 DOM을 구현하는 기준이다. [(웹표준)](web-standard.md)

많은 브라우저들이 표준 규약에서 제공하는 기능 외에도 추가적인 기능들을 제공하기 때문에

사용자가 작성한 문서들이 각기 다른 DOM 이 적용된 다양한 브라우저 환경에서 동작할 수 있다는 사실을 항상 인지하고 있어야 한다.

### 오해할 수 있는 부분

DOM과 자바스크립트는 별개다.

초창기에는 밀접한 관련이 있지만,

요즘은 js의 많은 발전으로(node.js등과 같은 서버사이드 스크립트) 독립되었다.

페이지 컨텐츠는 DOM으로 표현되고, 자바스크립트를 통해 접근하거나 조작할 수 있다.

웹페이지 = DOM + js

reference : https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction