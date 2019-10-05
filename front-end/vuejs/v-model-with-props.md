# v-model-with-props

vuetify 라이브러리를 사용하여 개발하는도중, 문제가 생겼다.

v-text-field라는 vuetify에서 제공하는 컴포넌트를 사용하고싶었다.

그리고 그 컴포넌트를 감싸고있는 똑같은 모양의 검색바를 만들고 사용하는데,

```text
<div class="searchBarWrapper">
  <div></div>
  <div class="searchBar">
    <v-text-field
            v-model="propModel"
            :label="placeholder || '검색'"
            box/>
  </div>
</div>
```

이런모양의 템플릿을 매번 게시판마다 넣어줘야해서, 컴포넌트화를 시켰다.

v-model으로 받는 데이터\(상태\)가 바뀌어야하는데,

그 데이터를 props로 받기때문에, 변경할수없는문제가 생겼다.

그래서 v-model을 삭제하고 @change="handleChangeText" 를 추가하여, 부모컴포넌트에서 메소드를 만들고

props로 내려서 문자열 변경을 감지하는 방법을 사용했다.

그런데, @change가 트리거되는 시점이, 입력하다가 엔터를 치거나, 포커스아웃되면 그때 트리거되는 방식이다.

입력값이 변동되면 바로바로 검색되게하는 기획인데, 기능이 어긋난다.

그래서 바로바로 입력에 반응하는 양방향바인딩 v-model 디렉티브를 props와 함께 사용하는 방법을 아래에서 소개한다.

우선 검색바 컴포넌트이다. 템플릿은 위에 작성되어있다.

```javascript
export default {
    name: 'SearchBar',
    props: {
      placeholder: String,
      handleChangeText: Function,
    },
    data: () => ({
      text: '',
    }),
    computed: {
      propModel: {
        get() {
          return this.text;
        },
        set(value) {
          this.text = value;
          this.handleChangeText(value);
        }
      }
    }
  };
```

v-model을 computed로 바인딩했다.

그러면 검색바에 뭔가 입력하면 셋팅되어있는 text라는 상태에 저장되고,

가져올때 가져온다. 이건 그냥 템플릿에 보여주기위한 페이크라고 보면된다.

실제 부모한테 바뀐 입력값을 전달하는것이 이제 computed의 set함수이다.

첫번째라인은 페이크로 보여주기위한 값을 설정하는것이고,

두번째라인, props로 받은 handleChangeText함수를 호출하는데, 파라미터로 입력값을 전달한다.

그러면 이제 부모컴포넌트에서 검색바 객체를 생성할때,

props로 handleChangeText메소드만 간단하게 구현해주면된다.

부모컴포넌트의 템플릿

```markup
<search-bar :handle-change-text="handleChangeSearchText"/>
```

메소드

```javascript
handleChangeSearchText(text) {
  this.searchInputText = text;
},
```

이런식이다. 이렇게 구현하면, v-model에 props를 바인딩하는것과 유사한 기능을 구현할수있다.

