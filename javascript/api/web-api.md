# Web API

DOM\(Document\)

XHR\(XmlHttpRequest\) - ajax, fetch, axios

timeout - setTimeout, setInterval

이것들은 개발자가 접근할수없는, 호출만 가능한 스레드이다. \(노드의 경우 C++ API\)

별도의 스레드에서 처리하는 것은 아니다.

```javascript
function sleep(delay) {
  var start = Date.now();
  while (Date.now() < start + delay);
}

setTimeout(()=>{
    console.log('start');
    sleep(10000);
    console.log('end');
}, 10);
```

위의 코드를 보면, web api가 별도스레드에서 실행된다고 가정하면,

브라우저 콘솔에 이 코드를 붙여넣고 기능을 작동시켜보자.\(버튼을 누른다던지\)

end가 콘솔에 찍히기전에는 어떠한 동작도 실행되지않는다.

이것은 별도스레드에서 작동하는게 아니라,

싱글스레드인 이벤트루프와 큐를 통해 작동하고 있는 것을 확인할 수 있다.

어차피 나중에 코드가 실행되는 것이므로, web api에 무거운 로직이 들어가서

오래걸리는게 싫다면 아래의 워커 api를 사용하면 된다.

[worker API](worker-api.md)

이것은 js의 싱글스레드의 한계를 극복할수있게 도와주는 api이다.

별도의 워커스레드에서 스크립트를 실행한다.

