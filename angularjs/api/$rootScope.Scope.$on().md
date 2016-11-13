## $on


### `$on(name, listener);`

특정한 타입의 이벤트를 수신한다 (이벤트 `listener` 등록). `$emit`문서에서 이벤트 라이프 사이클에 대해 논의한다.

이벤트 리스너 함수의 형태는 `function(event, args...)`이다. 리스너에 전달되는 `event`객체는 다음의 어트리뷰트를 가지고 있다:

- `targetScope` - `{Scope}` : 이벤트가 `$emit`되거나 `$broadcast`된 스코프.
- `currentScope` - `{Scope}` : 이벤트를 핸들링하는 현재 스코프. 이벤트가 스코프 계층을 통해 전파되면 이 프로퍼티는 null로 설정된다.
- `name` - `{string}` : 이벤트의 이름.
- `stopPropagation` - `{function=}` : `stopPropagation`을 호출하면 더 이상의 이벤트 전파를 막는다 (`$emit`된 이벤트에만 이용할 수 있다).
- `preventDefault` - `{function}` : `preventDefault` 호출은 `defaultPrevented`를 true로 만든다.
- `defaultPrevented` - `{boolean}` : `preventDefault`가 호출되면 true (기본값 : false).


### reference

[API Reference : $rootScope.Scope#$on](https://docs.angularjs.org/api/ng/type/$rootScope.Scope#$on)
