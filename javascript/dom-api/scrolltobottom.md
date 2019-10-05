# scrollToBottom

프론트어플리케이션을 개발하다보면, 특정 엘리먼트 위치로 스크롤하거나, 제일 하단, 상단스크롤이 필요할때가 많죠.

거기에 바로 이동되는게 아니라, 스크롤이되면서 부드럽게 이동하려면.. 구현방법을 모르면 머리아파집니다.

쉽게 구현해봅시다.

우선 제일 하단으로 스크롤하는 함수입니다.

```javascript
export const scrollToBottom = element => {
  const el = element ? element : window;
  el.scrollBy({top: el.scrollHeight || 99999, behavior: 'smooth'});
};
```

스크롤영역을 가진 엘리먼트를 파라미터로 넘기면 그 엘리먼트가 스크롤되고, 아니면 전체화면이 스크롤되도록 구현했습니다.

아래함수는 특정 엘리먼트가 가장 상단에 보이도록 스크롤합니다.

```javascript
export const scrollToElement = (element, block = 'start') => {
  if(!element)
    throw Error('no element');
  element.scrollIntoView({ block,  behavior: 'smooth' });
};
```

파라미터로 엘리먼트, block이 있는데, 엘리먼트는 화면에 보여져야할 엘리먼트이고,

블록은 start, end 문자열을 넣으면 됩니다. 안넣으면 디폴트로 start입니다.

end옵션을 주면, 해당엘리먼트가 스크롤영역 가장 하단에 보이게됩니다.

신기\(?\)하게도 스크롤영역이 여러개여도, 알아서 해당엘리먼트가 있는 스크롤영역을 찾아서 스크롤합니다.

