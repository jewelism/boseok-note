## 텍스트 끝처리 / ... 으로 표시하기!

바로 그냥 코드를 공개합니다. 셜명할것도 없는데.

```css
.some-class {
  display: -webkit-box;
  -webkit-box-orient: vertical;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: normal;
  -webkit-line-clamp: 3;
  height: 3.6rem;
  line-height: 1.2rem;
}
```

중요한건 웹킷이 아니면, line clamp를 처리못하므로,

3줄이 넘어가도 작동합니다.

그래서 height를 line height의 3배로 줘서, 3줄이 넘어가면

자동으로 자르게 했습니다. 크기는 동적으로줘서 크기변경에 상관없이 작동하도록 구현.

그리고 overflow속성을 없애면, 그냥 설정해놓은 태그영역을 벗어나므로 주의하세요!