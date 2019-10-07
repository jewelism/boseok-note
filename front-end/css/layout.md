# css layout

BFC(Block Formatting Context)는 블록 박스가 배치된 웹 페이지의 시각적 CSS 렌더링의 일부입니다. 

float, absolute로 배치된 요소, inline-blocks, table-cells, table-caption 그리고 visible(그 값이 viewport에 전파되었을 때는 제외)이 아닌 overflow가 있는 요소들이 새로운 Block Formatting Context를 만듭니다.

BFC는 다음 조건 중 하나 이상을 충족시키는 HTML 박스입니다:

float의 값이 none이 아님.
position의 값이 static도 아니고 relative도 아님.
display의 값이 table-cell, table-caption, inline-block, flex, inline-flex임.
overflow의 값이 visible이 아님.
BFC에서 각 박스의 왼쪽 바깥 모서리는 포함하는 블록의 왼쪽 모서리에 닿습니다(right-to-left 포맷에서는, 오른쪽 모서리에 닿음).

BFC collapse시에 인접한 블록 레벨 박스 사이의 수직 마진. collapsing margins에 대해 자세히 읽어보세요.


ref: https://github.com/yangshun/front-end-interview-handbook/blob/master/Translations/Korean/questions/css-questions.md