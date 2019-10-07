# flux

flux는 페이스북에서 어떤 문제를 해결하기위해(논란의 여지가 있다고함) 고안된 디자인패턴입니다.

양방향데이터흐름은 어플리케이션이 거대해질수록 예측하기힘듭니다.

FLUX

Action => Dispatcher => Store => View => ...

이러한 패턴은 데이터변화를 훨씬 예측하기쉽게 만들어줍니다.

redux나 vuex같은 라이브러리들이 flux의 구현체입니다.

Action을 dispatch하고, store의 state를 조작하여, view에 반영합니다.