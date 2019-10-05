# worker-api

웹워커 API는 메인스레드외에 별도의 워커스레드에서\(백그라운드\) 스크립트를 실행할 수 있게 해준다.

ui를 위한 메인스레드에서 무거운 동작을 하게되면 ui의 멈춤이나 속도 저하가 발생하는데, 그것을 위해 탄생했다.

앞으로 클라이언트에서 동작하는 코드가 점점 많아질텐데, 그것을 대비해서 사용법을 알아두면 좋을 것 같다.

워커스레드에서 작동하는 코드들은 모든 메소드를 사용할 수 있는 것이 아니다.

아래 링크는 사용가능한 함수들이 정리되어있다.

[https://developer.mozilla.org/en-US/docs/Web/API/Web\_Workers\_API/Functions\_and\_classes\_available\_to\_workers](https://developer.mozilla.org/en-US/docs/Web/API/Web_Workers_API/Functions_and_classes_available_to_workers)

## 서비스워커 \(Service Worker\)

웹 어플리케이션 사이의 Proxy Server와 브라우저로서 역할을 하며 \(만약 가능하다면\)통신을 구축합니다. 이를 통해 효율적인 오프라인 경험을 구축하고, 네트워크 요청을 가로채어 통신이 가능한지 여부에 따라 적절한 동작을 수행하며, 서버에 존재하는 자원들을 갱신할 수 있습니다. 또한 푸시 알림이나 백그라운드 동기화 API에 접근을 허용합니다.

## Channel Messaging API

### 이 API는 웹 워커안에서만 동작합니다

채널 메시징 API는 동일한 문서에 첨부 된 서로 다른 브라우징 컨텍스트에서 실행되는 두 개의 개별 스크립트가 양방향 포트 \(또는 파이프\)를 통해 양 끝의 포트를 통해 메시지를 직접 전달할 수 있도록합니다.

### Reference

[https://developer.mozilla.org/ko/docs/Web/API/Web\_Workers\_API](https://developer.mozilla.org/ko/docs/Web/API/Web_Workers_API)

[https://developer.mozilla.org/ko/docs/Web/API/Worker](https://developer.mozilla.org/ko/docs/Web/API/Worker)

[https://developer.mozilla.org/ko/docs/Web/API/Channel\_Messaging\_API](https://developer.mozilla.org/ko/docs/Web/API/Channel_Messaging_API)

