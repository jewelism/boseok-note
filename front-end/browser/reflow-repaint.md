## reflow, repaint

리플로우라는것은 렌더링 트리의 일부(또는 전부)의 변경이 있을때 발생한다.

첫 페이지의 레이아웃이 표시될때 리플로우가 일어난다.


렌더링 트리를 구성하는데 사용된 입력 정보의 어떤 변경도 리플로우와 리페인트를 발생시킨다. 구체적으로는 다음과 같은 경우이다.

```
DOM 노드의 추가, 삭제 및 업데이트
display: none(리플로우와 리페인트) 또는 visibility: hidden(위치 변경은 일어나지 않기 때문에, 리페인트만) 등과 같은 DOM 노드 숨김
페이지상에서 DOM 노드의 위치 이동 및 애니메이션
스타일 속성의 약간의 변화를 위해 스타일 시트 추가
윈도우 크기를 변경하거나 폰트 크기 변경, 그리고 스크롤 등 사용자의 액션
```

이러한 일들이 자주 일어나기때문에, 브라우저는 작업을 큐에 밀어넣고 업데이트가 필요할때 큐를 플러시하여 리플로우를 최소화한다.

아래와 같은 작업의 get set은 큐를 플러시해야하는 작업들이다. 그러므로 for루프등 내부에 사용하게되면 루프를 돌때마다 리플로우가 일어나기때문에,

루프 바깥 블록에 할당해놓고 사용하는것이 유리하다.

```
offsetTop, offsetLeft, offsetWidth, offsetHeight
scrollTop, scrollLeft, scrollWidth, scrollHeight
clientTop, clientLeft, clientWidth, clientHeight
getComputedStyle() 또는 IE의 currentStyle
```


http://www.mimul.com/pebble/default/2013/07/07/1373183724195.html

https://github.com/wonism/TIL/blob/master/front-end/browser/reflow-repaint.md