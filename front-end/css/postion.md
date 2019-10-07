# Position

relative, fixed, absolute, static 요소의 차이점은 무엇인가요?

위치가 정해진 요소는 계산된 position 속성이 relative, absolute, fixed, sticky 중 하나인 요소입니다.

static - 기본 위치. 요소가 평소와 같이 페이지에 위치합니다. top, right, bottom, left, z-index 속성은 적용되지 않습니다.

relative - 요소의 위치가 레이아웃을 변경하지 않고, 자체에 상대적으로 조정됩니다. (따라서 배치되지 않은 요소의 간격을 남겨 둡니다.)

absolute - 요소가 페이지의 평소 위치에서 제거되고, 가장 가까운 relative 부모 블록이 있는 경우 지정된 위치에 배치됩니다. 그렇지 않으면 최상위 블록에 의존됩니다. absolute로 배치된 박스는 margin을 가질 수 있으며 다른 margin과 충돌하지 않습니다. 이 요소는 다른 요소의 위치에 영향을 주지 않습니다.

fixed - 요소는 페이지의 평소 위치에서 제거되고 뷰포트를 기준으로 지정된 위치에 배치되며 스크롤 할 때 이동하지 않습니다.

sticky - sticky는 relative와 fixed의 하이브리드입니다. 요소는 지정된 임계값을 넘을 때까지 relative 위치로 처리되며, 특정 지점에서 fixed 위치로 처리됩니다.

-------

### absolute 포지셔닝 대신 translate()를 사용하는 이유가 무엇인가요? 또는 그 반대의 경우에 대해서는 어떻게 생각하시나요?, 그 이유는 무엇인가요?

translate()은 CSS transform의 값입니다. transform이나 opacity를 변경해도 브라우저의 reflow나 repaint가 다시 발생하지 않고 컴포지션만 실행되는 반면, 절대 위치를 변경하면 reflow가 발생합니다. 

transform을 사용하면 브라우저에서 이 요소를 위한 GPU 레이어가 생성되지만, 절대 위치 속성을 변경하는 것은 CPU를 사용합니다. 그러므로 translate()가 더 효율적이며, 매끄러운 애니메이션을 위한 페인트 시간이 짧아집니다.

translate()을 사용할 때는 절대 위치를 변경할 때와 달리 원래 위치(일종의 position: relative)를 그대로 사용합니다.

-----------
참고자료
https://github.com/yangshun/front-end-interview-handbook/blob/master/Translations/Korean/questions/css-questions.md
https://developer.mozilla.org/en/docs/Web/CSS/position