## 의미 있게 구분하라

컴파일러나 인터프리터만 통과하려는 코드의 프로그램은 문제를 일으킨다.

컴파일러를 통과할지라도 연속된 숫자를 덧붙이거나 불용어를 추가하는 방식은 적절하지 못하다.

이름이 달라야한다면 의미도 달라져야 한다.

---

연속적인 숫자를 덧붙인 이름 ``(b1, b2, …, bN)``은 의도적인 이름과 정반대다.

이런 이름은 그릇된 정보를 제공하는 이름도 아니며, 아무런 정보를 제공하지 못하는 이름일 뿐이다.

저자 의도가 전혀 드러나지 않는다.

```java
public static void copyInts(int a1[], int a2[]) {
  for (int i = 0; i < a1.length; i++) {
    a2[i] = a1[i];
  }
}
```
에서 함수 파라미터를 `source`와 `destination`으로 바꾸면
```java
public static void copyInts(int source[], int destination[]) {
  for (int i = 0; i < source.length; i++) {
    destination[i] = source[i];
  }
}
```
코드 읽기가 훨씬 더 쉬어진다.

---

불용어`(a, an, the와 같은 의미가 불분명한 단어)`를 추가한 이름 역시 아무런 정보도 제공하지 못한다.

`Reserve`라는 클래스가 있고 `ReserveInfo`나 `ReserveData`라는 클래스가 있다면, 개념을 구분하지 않은 채이름만 달리한 경우다.`Info`나 `Data`는 `a, an, the`와 마찬가지로 의미가 불분명한 불용어다.

의미가 분명히 다르다면 `a`나 `the`같은 접두어를 사용해도 무방하다. `book`이라는 변수가 있다는 이유로 `theBook`라 이름을 지어서는 안된다는 말이다.

---


불용어는 중복이다. 변수 이름에 `variable`이라는 단어는 단연코 금물이다. 색 이름에 `color`라는 단어도 마찬가지다. 

`priceInt`가 `price`보다 뭐가 나은가? `price`가 문자열이 될 가능성이 있는가? 그렇다면 `그릇된 정보를 피하라` 규칙을 위반한다.

`Reserve`라는 클래스와 `ReserveObject`라는 클래스가 있다면 차이를 알겠는가?

```java
getActiveReserve();
getActiveReserves();
getActiveReserveInfo();
```

이런 함수들이 있을때, 예매 이력을 찾으려면 어느 함수를 호출할지 어떻게 알까?

---

명확한 관례가 없다면 `reserveInfo`는 `reserve`와, `theBook`은 `book`과 구분이 안된다.

읽는 사람이 차이를 알도록 이름을 지어라.
