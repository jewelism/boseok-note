# 렌더링 트리\(Rendering Tree\)

[DOM](dom.md) 및 [CSSOM](cssom.md) 트리는 결합되어 렌더링 트리를 형성합니다.

![](../../.gitbook/assets/render-tree-construction.png)

렌더링 트리에는 페이지를 렌더링하는 데 필요한 노드만 포함됩니다.

레이아웃은 각 객체의 정확한 위치 및 크기를 계산합니다.

마지막 단계는 최종 렌더링 트리에서 수행되는 페인트이며, 픽셀을 화면에 렌더링합니다.

여기에서 reflow와, repaint라는 용어가 등장하는데,

[그 설명은 여기에서..](reflow-repaint.md)

reference : [https://developers.google.com/web/fundamentals/performance/critical-rendering-path/render-tree-construction?hl=ko](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/render-tree-construction?hl=ko)

