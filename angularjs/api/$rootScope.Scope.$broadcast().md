## $broadcast


### `$broadcast(name, args);`

`name`이벤트를 모든 자식 `scope`들에게(계층구조상 아래로, 그들의 자식들에게도) 전달하고 등록된 `listener`들에게 통지한다.

이벤트 라이프 사이클은 `$broadcast`가 호출된 `scope`에서부터 시작된다. 이 `scope`에 있는 `name`이벤트를 수신하는 모든 `listener`들은 통지를 받는다. 그 후에, 이벤트는 현재 `scope`에 직접적이거나 간접적인 `scope`들에게(자식이나 자식의 자식) 전파되며 등록된 모든 `listener`들을 호출한다. 이벤트는 취소되지 않는다.

`listener`로부터 방출되는 예외는 `$exceptionHandler` service에 전달된다.


### reference

[API Reference : $rootScope.Scope#$broadcast](https://docs.angularjs.org/api/ng/type/$rootScope.Scope#$broadcast)
