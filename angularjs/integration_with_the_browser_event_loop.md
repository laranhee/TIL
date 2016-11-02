## Integration with the browser event loop

![Angular concepts-runtime](./integration_with_the_browser_event_loop__concepts-runtime.png)

다이어그램과 밑에 묘사된 예제는 Angular가 어떻게 브라우저 이벤트 루프와 상호작용하는지를 나타낸다.

1. 브라우저의 이벤트-루프는 이벤트가 도착하기를 기다린다. 이벤트는 유저 상호 작용, 타이머 이벤트, 또는 네트워크 이벤트가 있다(서버로부터의 응답).
2. 이벤트의 콜백이 실행된다. 이것은 자바스크립트 컨텍스트로 진입한다. 콜백은 DOM 구조를 수정할 수 있다.
3. 콜백이 실행되고나면 브라우저는 자바스크립트 컨텍스트를 떠나고 DOM 변경에 기초해 뷰를 다시 렌더링한다.

Angular는 자체 이벤트 처리 루프를 제공하여 일반적인 자바스크립트 플로우를 수정한다. 이것은 자바스크립트를 고전적인 컨텍스트와 Angular 실행 컨텍스트로 분할한다. 오직 Angular 실행 컨텍스트에 적용되는 작업만이 Angular 데이터 바인딩, 예외 핸들링, 프로퍼티 감시 등에서 이득을 본다. 또한 자바스크립트로부터 Angular 실행 컨텍스트에 진입하기 위해`$apply()`를 사용할 수 있다. 대부분의 장소에서(controller, service)에서 `$apply`는 이벤트를 처리하는 directive에 의해 이미 호출되고 있는 것을 유의하라. `$apply`의 명시적 호출은 커스텀 이벤트 콜백을 구현하거나 서드파티 라이브러리 콜백과 작업할 때만 필요하다.

1. `scope.$apply(stimulusFn)` 호출을 통해 Angular 실행 컨텍스트로 진입한다. `stimulusFn`은 Angular 실행 컨텍스트에서 수행하고자 하는 작업이다.
2. Angular는 일반적으로 어플리케이션의 상태를 수정하는 `stimulusFn()`을 실행한다.
3. Angular는 `$digest` 루프에 진입한다. 루프는 `$evalAsync` 큐를 처리하는 루프와 `$watch` 리스트를 처리하는 루프, 두 개의 작은 루프로 구성되어 있다. 모델이 안정화(`$evalAsync` 큐가 비거나 `$watch` 리스트가 어떠한 변경도 감지 못 할 때) 될 때까지 `$digest` 루프는 반복을 유지한다.
4. `$evalAsync` 큐는 브라우저의 뷰가 렌더되기 전에 현재 스택 프레임의 외부에서 발생해야하는 작업을 스케줄 할 때 사용된다. 이는 보통 `setTimeout(0)`으로 완료된다. 하지만 `setTimeout(0)`은 접근 방식은 속도 저하를 겪고, 브라우저가 매 이벤트 후에 뷰를 렌더하기 때문에 뷰 깜빡거림을 야기할 수 있다.
5. `$watch` 리스트는 마지막 반복 이후 변경될 수 있는 표현식의 집합이다. 만약 변경이 감지된다면 일반적으로 새 값으로 DOM을 업데이트하는 `$watch` 함수(`listener`)가 호출된다.
6. Angular `$digest`루프가 끝나고 나면 실행은 Angular와 자바스크립트 컨텍스트를 떠난다. 이는 변경을 반영하기 위한 브라우저의 DOM 렌더링 뒤에 이루어진다.

텍스트 필드에 텍스트를 입력하는 `hello world` 예제가 어떻게 데이터 바인딩 결과를 내는지에 대한 설명

1. compilation 단계 동안
  1. `ng-model`과 `input directive`는 `<input>` 컨트롤에 `keydown` listener를 설정한다.
  2. `interpolation`은 `name`이 변경됐을 때 통지받을 수 있게 `$watch`를 설정한다.

2. runtime 단계 동안
  1. 'x'키를 누르면 브라우저가 input 컨트롤의 `keydown` 이벤트를 방출한다.
  2. `input` directive는 input 값의 변경을 포착하고 Angular 실행 컨텍스트 내부의 어플리케이션 모델을 업데이트하기 위해 `$apply ("name = 'x';")`를 호출한다.
  3. Angular는 모델에 `name = 'x';`를 적용한다.
  4. `$digest` 루프가 시작된다.
  5. `$watch` 리스트는 `name` 프로퍼티의 변경을 감지하고 차례로 DOM을 업데이트하는 `interpolation`에게 통지한다.
  6. Angular는 차례로 `keydown` 이벤트를 종료하는 실행 컨텍스트를 자바스크립트 실행 컨텍스트와 함께 종료한다.
  7. 브라우저는 업데이트된 텍스트와 함께 뷰를 렌더링한다.

### reference

[Developer Guide / Scope : Integration with the browser event loop](https://docs.angularjs.org/guide/scope#integration-with-the-browser-event-loop)
