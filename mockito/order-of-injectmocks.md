## @InjectMocks의 주입방식 순서

1. Constructor Injection
2. Property Setter Injection
3. Field Injection

의 순서대로 `Mock`주입을 시도하며, 주입이 성공해 `@InjectMocks`로 마크된 객체가 생성되면, 다음 단계는 실행되지 않는다.

#### Constructor Injection

인수를 받는 생성자가 있으면 해당 생성자를 통해 `Mock`을 주입한다. 객체가 성공적으로 생성되면, 다른 주입전략은 시도하지 않는다. 가장 큰 생성자가 선택된다 ~~(크다는게 인수를 말하는 거라면, 인수 개수가 같은 생성자가 2개 이상이면 어떻게 될까).~~ ~~타입보고 선택되겠지..~~
#### Property Setter Injection

`@InjectMock` 인스턴스가 초기화되지 않았고, 인수가 없는 생성자가 있으면
Setter를 통한 주입 시도.

#### Field Injection


`@InjectMock` 인스턴스가 초기화되지 않았고, 인수가 없는 생성자가 있으면
Field를 통한 주입 시도.

#### Reference

http://static.javadoc.io/org.mockito/mockito-core/1.10.19/org/mockito/InjectMocks.html
