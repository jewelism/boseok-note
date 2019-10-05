## Chrome 브라우저

크롬 브라우저는 구글에서 개발한 크로미움기반 브라우저이다.

javascript 엔진으로 v8을 사용하고 있다.

레이아웃 엔진으로는 블링크(웹킷기반)를 사용하고 있다.

크롬은 멀티프로세스 아키텍쳐이다.

각 크롬 프로세스는 몇 개의 스레드로 구성된 스레드풀이 있다.

대표적으로 main thread(UI thread), IO thread(handling IPC)로 구분된다.

그래서 기본적으로 내부적인 멀티스레드다.

비동기처리를 위한 태스크큐(혹은 이벤트큐)가 구현되어있다.

-----------------------

thread간 shared resource의 synchronize access를 위해서는 Lock이라는 방법도 있지만

SequencedTaskRunner를 사용한 sequences to locks이 강력하게 권장된다.

-----------

레퍼런스: https://chromium.googlesource.com/chromium/src/+/master/docs/threading_and_tasks.md