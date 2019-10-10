# join

```js
//mozila의 예제
var a = ['바람', '비', '불'];
var myVar1 = a.join();      // myVar1에 '바람,비,불'을 대입
var myVar2 = a.join(', ');  // myVar2에 '바람, 비, 불'을 대입
var myVar3 = a.join(' + '); // myVar3에 '바람 + 비 + 불'을 대입
var myVar4 = a.join('');    // myVar4에 '바람비불'을 대입
//여기까지 mozila의 예제

a.push(undefined, '1');
console.log(a);
var myVar5 = a.join('');
console.log(myVar5); //undefined는 무시되고, 합쳐진다
```