## react-native 기본

react-native는 react기반으로 소스코드를 작성하고, 한번에 여러가지 모바일 플랫폼으로 빌드할 수 있다.

심지어 네이티브로 빌드된다. 웹뷰기반의 하이브리드앱보다는 당연히 성능이 좋다.

한마디로 react-native를 사용하면 네이티브를 몰라도 가능하지만,

결국 앱이 커지거나 복잡해지고(많은 라이브러리의 사용) 버전업이 계속된다면 네이티브를 알아야한다(...)

react native는 nodejs환경에서
간단한 명령어로 프로젝트를 생성할 수 있다.
```bash
npm install -g react-native-cli
react-native init 프로젝트이름
```

### 안드로이드
빌드하기전에..

안드로이드 sdk매니저를 통해 현 react-native에 맞는 sdk버전을 설치해줘야한다.

#### 실제 디바이스를 연결하는 경우
1. 실제 디바이스를 개발pc에서 인식할수있도록 드라이버를 설치한다.
2. 안드로이드 기기를 연결한다.

#### 가상 디바이스로 연결하는 경우
1. 안드로이드의 avd를 통해 가상디바이스를 생성하고 실행한다.

디바이스를 연결했다면 터미널 - 프로젝트가 있는곳
```bash
react-native run-android
```
명령어를 실행하면 연결된 디바이스에서 앱이 자동으로 실행된다.

### IOS
1. app store에서 xcode설치
2. ios 에뮬레이터 실행
3. 명령어 실행
```bash
react-native run-ios
```

## APK 생성
1. Debug 버전 빌드
```bash
react-native bundle --dev false --platform android --entry-file index.android.js --bundle-output ./android/app/build/intermediates/assets/debug/index.android.bundle --assets-dest ./android/app/build/intermediates/res/merged/debug
```
```bash
cd android && ./gradlew assembleDebug && cd ..
```

2. Release버전 빌드 - android-app build.gradle에서 버전관리

```bash
cd android && ./gradlew assembleRelease && cd ..  
```
***run method***
```bash
react-native run-android --variant=release
```
Generated apk will be located at android/app/build/outputs/apk
P.S. Another approach might be to modify gradle scripts.


## 기본 사용방법
react-native(이하 RN)은 reactJS기반의 문법-JSX를 따른다.
```js
export default class HelloWorldApp extends Component {
  render() {
    return (
      <Text>Hello world!</Text>
    );
  }
}
```

react에서 사용하는 문법

마치 html, 혹은 xml태그와 비슷해보이는 JSX문법이다.

JSX는 ES6으로 작성된다.

### Data Fetching

서버에서 데이터를 가져와야할일이 생기면,

[fetch api](../../javascript/es6/fetch.md)를 사용하면 된다.

물론 axios같은 라이브러리도 가능하다.

### 스타일적용하기

사실 버전업이 자주되어서 지금은 어떨지는 모르겠지만,

이 글을 작성하던 2017년 7월즈음에 사용하던 방법이다. (rn v0.4)

#### 스타일 2개 적용하기
```js
style={[styles.styleOne, styles.styleTwo]}
```
이런식으로 스타일에 배열을 끼워넣으면 된다.

이 경우의 우선순위가 배열에서 가장 뒤에있는 스타일이 적용된다.

버전업으로 동작하지않는다면..

Object.assign을 이용하면 될것같다.(추측)
```js
style={Object.assign({}, styles.styleOne, styles.styleTwo)}
```

### 터치 제어 관련

View 컴포넌트의 attr중에 pointerEvents='none'으로 설정해놓으면 그 뷰의 터치가 불가능해진다.

가능하게하고 싶으면 null로 지정하면된다.

```js
pointerEvents={this.state.enable}
```
```js
this.state = {
  Enable: null,
}
```
```js
() => this.setState({enable:'none'})
```

### Image Source

네이티브와 마찬가지로 같은폴더내에 user.png user@2x.png user@3x.png가 있다면 
```js
import userImg from '경로/user.png'
```
해주면 해상도 크기에 맞는 이미지가 자동으로 삽입된다

### 네이티브기능을 사용하는 라이브러리?

네이티브 기능을 사용하는 라이브러리라면,

ios는 cocoapods를 사용하면 되고, 안드로이드는 gradle을 사용하면 된다.

그 외에 라이브러리는 npm으로.

### 유용한 라이브러리 15가지

https://codingislove.com/top-15-react-native-libraries/

