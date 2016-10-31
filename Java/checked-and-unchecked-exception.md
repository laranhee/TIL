## Checked Exception

`Exception` 클래스의 서브클래스이면서 `RuntimeException` 클래스를 상속하지 않은 것들.

일반적인 예외를 다루기에(말그대로 복구할 가능성이 조금이라도 있는), 이를 처리하는 catch 블록이나 throws선언을 강제

`checked exception`의 예외처리 강제로 예외 블랙홀이나 무책임한 throws 같은 코드 남발로 `checked exception`의 불필요성 주장이 나오기도 함.

- 무책임한 throws 코드
```java
throws Exception
```

최근에 새로 등장하는 자바 표준 스펙의 API들은 예상 가능한 예외상황을 다루는 예외를 `checked exception`으로 만들지 않는 경향이 있기도 함.

## Unchecked Exception

`RuntimeException` 클래스를 상속한 클래스들.

명시적인 예외처리를 강제하지 않음.

`unchecked exception`은 주로 프로그램의 오류가 있을 때 발생하도록 의도된 것들(`NullPointerException`, `IndexOutOfBoundsException`).

피할 수 있지만 개발자의 부주의로 발생할 수 있는 경우에 발생하도록 만든 것.

Java EE 서버환경에서는 수많은 사용자가 동시에 요청을 보내고 각 요청이 독립적인 작업으로 취급. 하나의 요청을 처리 중 예외가 발생하면 해당 작업만 중단시키면 그만. 독립형 어플리케이션과 달리 서버의 특정 계층에서 예외가 발생했을 때 작업을 일시 중지하고 사용자와 커뮤니케이션을 통해 예외상황을 복구할 수 있는 방법이 없다.

프로그램의 오류나 외부 환경으로 인해 예외가 발생하는 경우, 해당 요청 작업을 취소하고 관리자나 개발자에게 통보하는 편이 낫다.

Java의 환경이 서버로이동하며 `checked exception`의 활용도와 가치는 점점 떨어지고 있다. 무책임한 throws 같은 코드를 낳을 뿐. 대응이 불가능한 `checked exception`이라면 `unchecked exception`으로 던지는게(예외 전환) 낫다.
