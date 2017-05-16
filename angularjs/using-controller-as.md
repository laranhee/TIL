## controller as 사용하기

```html
<div ng-controller="HeaderController as header">
  <input type="text" ng-model="header.title"></input>
</div>
```

```js
angular.module('HeaderControllerExample', [])
  .controller('HeaderController', HeaderController);

function HeaderController() {
  this.title = 'Subject';
}
```

`ng-controller="HeaderController"` 대신 `ng-controller="HeaderController as header"`를 사용하면,

`$scope`에 `as` 뒤의 지정한 이름의 프로퍼티가 생긴다.

`$scope`에 프로퍼티를 추가하는 것이 아닌 `this`를 이용해 컨트롤러에 프로퍼티를 바인드.

(여러 컨트롤러가 있을 때, ) `$scope`를 이용하는 것에 비해 템플릿에서 어느 컨트롤러를 이용하고 관련되어 있는지 명확히 알 수 있다.
