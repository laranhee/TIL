## ng-options

#### ng-options="comprehension_expression"

기본적인 형식

`select as label for value in array`

- `array` : `expression`, 반복할 배열 또는 객체
- `label` : `expression`, `<option>`엘리먼트의 label. 생략가능
- `select` : `expression`, `<option>`엘리먼트의 value. 생략가능

#### ng-repeat를 통한 option 생성과 비교한 ng-options의 장점

- `select as`를 통해 유연하게 `<select>`의 모델이 할당됨.
- 생성된 `<option>`마다 스코프가 생기지 않아 메모리를 덜 먹는다.
- 각각 생성되는 것이 아닌 `documentFragment`를 통한 생성으로 렌더링 속도가 빠르다.

#### Reference

https://docs.angularjs.org/api/ng/directive/ngOptions
