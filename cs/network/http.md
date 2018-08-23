## HTTP, HTTPS

### HTTP (HyperText Transfer Protocol)

기본 port : 80

2018년 현재 http프로토콜이라고 하면 기본적으로는 1.1을 의미한다.

슬슬 2버전 도입을 준비중인 단계

예전에는 http는 html문서를 주고받는데 많이 사용했다.

요즘은 [REST](../../etc/rest/rest.md)라는 개념이 대세를 이루면서,

다양한 포맷의 데이터를 주고 받는데 사용한다.

https가 이제 거의 기본이 되어가면서, http프로토콜만 단독적으로 사용하진않는다.

[REST](../../etc/rest/rest.md)에서도 소개했지만

http에는 GET, POST, PUT, DELETE 등.. 다양한 메소드들이 있다.

http로 request하면, 서버는 3자리로 된 응답코드와 함께 response한다.

그 응답코드를 http status code라고 한다.

응답코드에는 어느정도 규칙이 있는데,

많이 사용하는것만 설명하고 나머지는 링크에서 확인하길 바란다.

https://ko.wikipedia.org/wiki/HTTP_%EC%83%81%ED%83%9C_%EC%BD%94%EB%93%9C
```
2xx: 성공
200: 서버가 요청을 정상적으로 수행했고, 요청한 페이지를 제공했음을 의미한다.
```
```
301: Redirect. 요청한 페이지에서 새로운 페이지로 다시 request한다.
```
```
4xx: 주로 클라이언트 에러
400: Bad Request. 클라이언트에서 보낸 데이터가 잘못됐음을 의미한다.
401: Unauthorized. 인증이 필요함을 의미한다.
403: Forbidden. 인가 실패를 의미한다. 권한없음.
404: Not Found. 요청한 페이지를 찾을 수 없다.
```

```
500: Interval Server Error. 서버에서 오류발생으로 응답할 수 없음을 의미한다.
```

### HTTPS

기본 port : 443

쉽게 말하면 브라우저에 등록된 기관의 SSL인증서를 웹서버에 등록하게되면

보안이 강화된 http 프로토콜을 사용할 수 있다.

비대칭키 암호화방식으로 이론상으로는 해킹이 불가능하다.