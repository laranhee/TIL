#### test시 private 메서드 실행하기

```java
// 메서드 가져오기
Method method = Class객체.getDeclaredMethod("메서드이름", parameterTypes...);
// 메서드 accessible true로
method.setAccessible(true);
// 실행
method.invoke(메서드가실행될객체, 매개변수...);
```

#### Reference

https://docs.oracle.com/javase/8/docs/api/java/lang/Class.html
https://docs.oracle.com/javase/8/docs/api/java/lang/reflect/Method.html
https://docs.oracle.com/javase/8/docs/api/java/lang/reflect/AccessibleObject.html
