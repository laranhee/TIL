## 메서드 이름

메서드 이름은 동사나 동사구가 적합하다.

예) `getPage, Load`

접근자, 변경자, 조건자는 javabean 표준에 따라 값 앞에 get, set, is를 붙인다.
(http://www.oracle.com/technetwork/java/javase/documentation/spec-136004.html)

```java
string name = user.getName();
user.setName("cat");
if(user.isAdmin())...
```

생성자를 중복정의 할 땐 정적 팩토리 메서드를 사용하고 메서드는 인수를 설명하는 이름을 사용한다.

```java
Admin admin = Admin.fromUser(user);
```

가 밑에보다 좋다.

```java
Admin admin = new Admin("Ranhee");
```

생성자 사용을 제한하려면 해당 생성자를 private로 선언한다.
