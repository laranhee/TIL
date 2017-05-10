## Array.prototype.map()

배열의 각 요소마다 제공된 함수를 호출한 결과로 새로운 배열을 만든다.

```js
var a = [1, 2, 3];

var b = a.map(function (x) {
  return a * 2;
});
// b = [2, 4, 6]
```
#### Syntax
```js
var new_array = arr.map(callback[, thisArg])
```

callback의 파라미터

- currentValue : 원 배열의 현재 처리중인 요소

- index : 원 배열의 현재 처리중인 요소의 인덱스

- array : map이 실행된 원 배열

thisArg : callback이 실행될 때 `this`로 사용되는 값
