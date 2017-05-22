## Array.prototype.filter()

배열의 각 요소마다 제공된 함수를 실행해 결과가 true인 요소들로 구성된 새 배열을 반환한다.

```js
var a = [1, 2, 3];

var b = a.filter(function (x) {
  return x > 1;
});
// b -> [2, 3]
```
#### Syntax
```js
arr.filter(function callback(currentValue, index, array) {
  // do something
}[, thisArg])
```

callback의 파라미터

- currentValue : 원 배열의 현재 처리중인 요소

- index : 원 배열의 현재 처리중인 요소의 인덱스

- array : map이 실행된 원 배열

thisArg : callback이 실행될 때 `this`로 사용되는 값
