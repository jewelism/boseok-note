# Proxy

첫번째 예제

```js
var arrayChangeHandler = {
  get: function(target, property) {
    // console.log('getting ' + property + ' for ' + target);
    // property is index in this case
    return target[property];
  },
  set: function(target, property, value, receiver) {
    console.log('setting ' + property + ' for ' + target + ' with value ' + value);
    target[property] = value;
    // you have to return true to accept the changes
    return true;
  }
};

var originalArray = [];
var proxyToArray = new Proxy( originalArray, arrayChangeHandler );

proxyToArray.push('Test');
console.log(proxyToArray[0]);

// pushing to the original array won't go through the proxy methods
originalArray.push('test2');
originalArray.boseok = 'new val';

// the will however contain the same data, 
// as the items get added to the referenced array
console.log('Both proxy and original array have the same content? ' 
  + (proxyToArray.join(',') === originalArray.join(',')));

  console.log(proxyToArray);
```

-----------------

두번째 예제

```js
var handler = {
  get: function (target, property) {
    // console.log('getting ' + property + ' for ' + target);
    // property is index in this case
    return target[property];
  },
  set: function (target, property, value) {
    target[property] = value;
    // you have to return true to accept the changes
    return true;
  }
};

this.test = 'test old val';
var origin = { boseok: 'old val', test: this.test };
var proxy = new Proxy(origin, handler);

origin.boseok = 'new val';
this.test = 'test new val';
// proxyToArray.push('Test');
// console.log(proxyToArray[0]);

// // pushing to the original array won't go through the proxy methods
// originalArray.push('test2');
// originalArray.boseok = 'new val';

// // the will however contain the same data, 
// // as the items get added to the referenced array
// console.log('Both proxy and original array have the same content? ' 
//   + (proxyToArray.join(',') === originalArray.join(',')));

console.log(proxy, 'origin', origin);
```