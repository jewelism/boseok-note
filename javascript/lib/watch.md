# Object Watch

Object의 프로토타입을 확장하는 monkey patching이라서 코드를 활용하기보다는,

getter, setter를 이용하여 watch를 구현하는 방법을 공부하는게 좋다.

```js
if (!Object.prototype.watch) {
  Object.defineProperty(Object.prototype, "watch", {
    enumerable: false
    , configurable: true
    , writable: false
    , value: function (prop, handler) {
      var
        oldval = this[prop]
        , newval = oldval
        , getter = function () {
          return newval;
        }
        , setter = function (val) {
          oldval = newval;
          return newval = handler.call(this, prop, oldval, val);
        }
        ;

      if (delete this[prop]) { // can't watch constants
        Object.defineProperty(this, prop, {
          get: getter
          , set: setter
          , enumerable: true
          , configurable: true
        });
      }
    }
  });
}

val = 2;
watch("val",function(id, old, cur) {
  console.log("Changed property: ", id);
  console.log("Original val: ", old);
  console.log("New val: ", cur);
 });

 val = 4;

```