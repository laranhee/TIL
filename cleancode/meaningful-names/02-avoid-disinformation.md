## 그릇된 정보를 피하라

코드에 그릇된 단서를 남겨서는 안 된다. 그릇된 단서는 코드 의미를 흐린다.

---

나름대로 널리 쓰이는 의미가 있는 단어를 다른 의미로 사용해도 안 된다.

운영체제를 나타내는 `OS`를 다른 의미로 사용하면 `OS`라는 변수는 프로그래머에게 그릇된 정보를 제공한다.

---

여러 음악을 그룹으로 묶을 때, 실제 `List`가 아니라면, `musicList`라 명명하지 않는다.

프로그래머에게 List라는 단어는 특수한 의미로, 음악을 담는 컨테이너가 실제 List가 아니라면 프로그래머에게 그릇된 정보를 제공하는 셈이다. (나중에 보겠지만 실제 컨테이너가 List인 경우라도 컨테이너 유형을 이름에 넣지 않는 편이 바람직하다.)

그러므로 `musicGroup`이나 `musics`라 명명한다.

---

서로 흡사한 이름을 사용하지 않도록 주의한다.

한 모듈이 `ABCServiceForEffectiveHandlingOfIntegers`라는 이름을 사용하고, 다른 모듈이 `ABCServiceForEffectiveStorageOfStrings`라는 이름을 사용한다면 두 이름은 너무 비슷하다.

---

유사한 개념은 유사한 표기법을 사용한다. 이것도 정보이고, 일관성이 떨어지는 표기법은 그릇된 정보다.

IDE 자동완성 기능을 통해 후보 목록에 유사한 개념이 알파벳 순으로 나오고 각 개념 차이가 명백히 드러난다면, 코드 자동 완성 기능은 굉장히 유용해진다.

객체에 달린 상세한 주석이나 클래스가 제공하는 메서드 목록을 살펴보지 않은체 이름만 보고 객체를 선택할 수 있다.

---

이름으로 그릇된 정보를 제공하는 진짜 끔찍한 예가 소문자 L과 대문자 O 변수이다.

소문자 L은 숫자 1처럼 보이고 대문자 O는 숫자 0처럼 보인다.

```java
int a = l;
if (O == l) {
  a = O1;
} else {
  l = 01;
}
```

글꼴을 바꿔 차이를 드러낼 수도 있지만, 문서나 구전으로 미래 개발자 모두에게 이를 알려야한다. 이름만 바꾸면 해결된 문제일 뿐인데 괜히 일을 만들 필요가 없다.
