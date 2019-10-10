# statc_of

```js
// ES6
// 가변인자를 받는 of메소드
const newArr = Array.of(1, 2, 3);
const newArr2 = Array.of(1);

console.log(newArr); //[1,2,3]
console.log(newArr2); //[1]

//ES5 이하 환경에서의 polyfill
if (!Array.of) {
    Array.of = function () {
        return Array.prototype.slice.call(arguments);
    };
}
//를 먼저 실행해주면 of를 정상적으로 사용할수있다.
```