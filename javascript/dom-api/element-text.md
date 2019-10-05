# HTML Element get Text

어떤 웹사이트의 테이블에서 데이터를 크롤링하다가 공부하게 됐다.

일반적으로 사용하는 크롬브라우저의 엔진과 크롤러의 엔진이 조금 달랐던것같다.

HTML Element에서 text를 가져오려면 innerText 프로퍼티를 사용하면되는데,

undefined가 뜨는경우가 간혹있더라. 텍스트노드가 또다른 노드안에 있다던지.

그것을 해결하는것이 아래 코드이다.

```javascript
const text = el['innerText' in el ? 'innerText' : 'textContent'];
```

이렇게 텍스트를 가져오게되면, 편하다.

