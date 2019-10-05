# rest

2000년도 =&gt; http의 주요 저자 중 한명인 로이 필딩이 창시

## 왜 이제서야 각광받게 되었나?

요즘 시대에는 디바이스의 종류가 다양하다.

pc, 스마트폰, 태블릿 등등..

디바이스마다 앱을 따로 만들어야하는데, 같은 로직을 가진 서버까지 디바이스마다 개발?

클라이언트와 서버를 분리해서 개발하는 것이 트렌드가 됨

서버는 API만 제공 =&gt; 클라이언트가 받아서 처리

API를 설계하다보니, 좋은 설계의 REST API가 이제서야 각광받게 됨.

## 특징

1\) Uniform \(유니폼 인터페이스\) Uniform Interface는 URI로 지정한 리소스에 대한 조작을 통일되고 한정적인 인터페이스로 수행하는 아키텍처 스타일을 말합니다.

2\) Stateless \(무상태성\) REST는 무상태성 성격을 갖습니다. 다시 말해 작업을 위한 상태정보를 따로 저장하고 관리하지 않습니다. 세션 정보나 쿠키정보를 별도로 저장하고 관리하지 않기 때문에 API 서버는 들어오는 요청만을 단순히 처리하면 됩니다. 때문에 서비스의 자유도가 높아지고 서버에서 불필요한 정보를 관리하지 않음으로써 구현이 단순해집니다.

3\) Cacheable \(캐시 가능\) REST의 가장 큰 특징 중 하나는 HTTP라는 기존 웹표준을 그대로 사용하기 때문에, 웹에서 사용하는 기존 인프라를 그대로 활용이 가능합니다. 따라서 HTTP가 가진 캐싱 기능이 적용 가능합니다. HTTP 프로토콜 표준에서 사용하는 Last-Modified태그나 E-Tag를 이용하면 캐싱 구현이 가능합니다.

4\) Self-descriptiveness \(자체 표현 구조\) REST의 또 다른 큰 특징 중 하나는 REST API 메시지만 보고도 이를 쉽게 이해 할 수 있는 자체 표현 구조로 되어 있다는 것입니다.

5\) Client - Server 구조 REST 서버는 API 제공, 클라이언트는 사용자 인증이나 컨텍스트\(세션, 로그인 정보\)등을 직접 관리하는 구조로 각각의 역할이 확실히 구분되기 때문에 클라이언트와 서버에서 개발해야 할 내용이 명확해지고 서로간 의존성이 줄어들게 됩니다.

6\) 계층형 구조 REST 서버는 다중 계층으로 구성될 수 있으며 보안, 로드 밸런싱, 암호화 계층을 추가해 구조상의 유연성을 둘 수 있고 PROXY, 게이트웨이 같은 네트워크 기반의 중간매체를 사용할 수 있게 합니다.

## REST API의 설계

1\) URI =&gt; 자원을 표현 =&gt; 동사를 사용하지않고 명사를 사용함 2\) 자원에 대한 행위 =&gt; HTTP Method\(GET, POST, PUT, DELETE\)로 표현

```bash
GET : 조회
POST : 생성
PUT : 수정
DELETE : 삭제
```

```bash
GET users/1 # user id 1에 해당하는 유저 정보 가져오기 
PUT users/1 # user id 1에 해당하는 유저 정보 수정
```

reference : [http://meetup.toast.com/posts/92](http://meetup.toast.com/posts/92) [https://github.com/iljun/DevNote/tree/master/common/restFulAPI](https://github.com/iljun/DevNote/tree/master/common/restFulAPI)

