# ES6 Map, Set

## Map

[Array.prototype.map은 여기서..](/javascript/prototype/Array/map)

es6에는 map 객체가 새로 추가됐다.

```js
new Map(iterable);
```

기존 object와 비슷하지만 여러 문제를 해결해주는객체다.

기존 object처럼 키-밸류를 요소로 갖는다.

하지만 첫번째로 다른점은 key에 string이 아닌 다른 어떠한 값이나 객체도 가능하다.

(객체의 키에는 객체를 할당할수없고, number를 넣더라도 string으로 타입캐스팅된다.)

조금 특이하게 NaN을 키로 지정할때, NaN !== NaN이지만, Map의 키에서는 동일하다고 간주한다.

나머지 값들은 === 연산자의 결과를 따른다.

두번째는 Map 객체는 iterable객체이다. 객체도 iterable을 구현하거나 비슷한 동작을 하게할수있지만, 번거롭다.

세번째는 순서보장이다. object는 브라우저마다 순서가 다를수있고, 삽입순으로 순서의 정렬이 보장되지않는다.

네번째는 속성의 숫자. size혹은 length의 판별이다. map은 size라는 프로퍼티를 제공한다. 객체는 직접 판별해야한다.

다섯번째는 객체는 프로토타입을 가져서, 키의 충돌위험성이 있다.

여섯번째로 키를 추가하거나 제거할때의 성능은 Map이 더 좋다.

## Set

es6에서 map뿐만아니라 Set 객체도 추가되었다.

map이 object와 비슷하다면, set은 array와 비슷하지다.

```js
new Set(iterable);
```

map처럼 아무값이나 넣을수있고, 순서보장을 해준다. NaN을 map과 동일하게 처리한다. 유사한 점이 많다.

다른점은 Set 내의 값은 유일하다. 동일한 값을 넣으면 무시된다.

Set을 이용해서 집합연산을 구현한 예제 (Array.from은 생략가능)

```js
// 합집합
const getCombinedSet = (list1, list2) => Array.from(new Set([...list1, ...list2]));

// 차집합
const getDifferenceSet = (list1, list2) => {
  const set2 = new Set(list2);
  return Array.from(new Set(list1.filter(x => !set2.has(x))));
};

// 교집합
const getIntersectionSet = (list1, list2) => {
  const set2 = new Set(list2);
  return Array.from(new Set(list1.filter(x => set2.has(x))));
};
```


------

Map이나 Set모두 iterable객체이므로 spread operator를 사용할수있다.

즉,

```js
[...someMap, ...someSet]
```

이런 코드가 가능.