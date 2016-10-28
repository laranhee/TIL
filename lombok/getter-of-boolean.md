## boolean 필드의 @Getter 적용

- primitive type인 boolean 필드의 getter 생성의 경우, prefix로 `get`을 붙이지 않고 `is`를 붙인다. boolean 필드 명 앞에 `is`가 붙어있다면 추가로 `is`를 붙이지 않는다.

```java
private boolean isMan;
```
이라면 lombok의 @Getter 적용시 생성된 getter 메소드는

```java
isMan();
```

- `Boolean`일 경우는 다른 타입처럼 `get`이 붙는다.
