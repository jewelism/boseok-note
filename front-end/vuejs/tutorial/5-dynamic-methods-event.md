# 5-dynamic-methods-event

쨘.. 이런식으로 컴포넌트 state가 있는데, 각 state가 바뀔때마다, 이벤트버스로 데이터변경을 알리고싶을때,

메소드를 동적으로 만들때! vuex의 mapMutations처럼!!! 이럴때 유용합니다.

하나하나 event emit하고, 받는곳에서는 on으로 하나하나 다 받기 귀찮잖아요.

자바스크립트니까 동적으로 구현해봅시다.

먼저 state!

```javascript
const SURVEY_INFO_STATE = {
  surveyName: '',
  startDate: '',
  startTime: '',
  endDate: '',
  endTime: '',
  surveyOrgan: '',
  surveyDescription: '',
};
```

뷰 컴포넌트 data에 맵핑하고싶다면 ...SURVEY\_INFO\_STATE 이런식으로 스프레드 오퍼레이터를 쓰면됩니다.

이해가 잘 안 되실까봐 친절하게 아래 예제코드도 있어여!ㅎㅎ

```javascript
data: vm => ({
  ...SURVEY_INFO_STATE,
}),
```

이제 동적으로 메소드를 만들어봅시다.

```javascript
const surveyInfoMethods = {};
Object.keys(SURVEY_INFO_STATE).forEach(stateName => {
  surveyInfoMethods[`handleChange${capitalizeFirstLetter(stateName)}`] = function (v) {
    this[stateName] = v;
    this.$eventBus.$emit(`change-${stateName}`, v);
  };
});
```

위에서 생성한 메소드도 뷰 컴포넌트에 아래와 같이 맵핑하면 됩니다

```javascript
methods: {
  ...surveyInfoMethods,
},
```

capitalizeFirstLetter가 뭔지 모르실까봐...아래 또 구현체를 드립니다.

```javascript
export const capitalizeFirstLetter = (string = '') => {
  return string.charAt(0).toUpperCase() + string.slice(1);
}
```

이벤트는 아래와 같이 on으로 받을수있습니다.

```javascript
Object.keys(SURVEY_INFO_STATE).forEach(stateName => {
  this.$eventBus.$on(`change-${stateName}`, v => {
    this[stateName] = v;
  })
});
```

간단하쥬?

