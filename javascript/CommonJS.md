##### CommonJS 모듈화의 세 부분

- 스코프(Scope): 모든 모듈은 자신만의 독립적인 실행 영역이 있어야 한다.
- 정의(Definition): 모듈 정의는 exports 객체를 이용한다.
- 사용(Usage): 모듈 사용은 require 함수를 이용한다.

##### 스코프

- 서로 다른 스코프

```js
// one.js
var a = 2;
```

```js
// two.js
var a = 'a';
```

##### 정의와 사용

```js
// A.js
exports.printHello = function () {
  console.log('Hello');
};
```

```js
// B.js
var moduleA = require('A');
moduleA.printHello(); // Hello
```
