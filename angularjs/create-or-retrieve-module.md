## angular.module()

```js
angular.module(name, [requires], [configFn]);
```

angular.module()은 호출할 때 인자의 갯수에 따라 모듈을 생성하거나 가져온다.

- 인자가 2개 이상일 때 : 모듈을 생성

```js
angular.module('myModule', []);
```

- 인자가 하나일 때 : 존재하는 모듈을 가져옴

```js
angular.module('myModule');
```

####
https://docs.angularjs.org/api/ng/function/angular.module
