## BeanUtils.copyProperties()

#### BeanUtils

빈 생성, 빈 프로퍼티 타입 체크, 빈 프로퍼티 복사 등에 쓰이는 static 메소드들이 있는 클래스.

#### copyProperties()

```java
static void copyProperties(Object source, Object target)
```
`source` 객체의 값을 `target` 객체에 복사.

```java
static void copyProperties(Object source, Object target, Class<?> editable)
static void copyProperties(Object source, Object target, String... ignoreProperties)
```
도 있다.

#### Reference

http://docs.spring.io/spring/docs/current/javadoc-api/org/springframework/beans/BeanUtils.html
