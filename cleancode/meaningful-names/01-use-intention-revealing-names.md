## 의도를 분명히 밝혀라

좋은 이름을 지으려면 시간이 걸리지만 좋은 이름으로 절약하는 시간이 훨씬 더 많다.

이름을 주의 깊게 살펴 더 나은 이름이 떠오르면 개선하라. (나 자신을 포함해 코드를 읽는 사람이 좀 더 행복해진다.)

변수, 함수, 클래스 이름이 다음과 같은 질문에 답할 수 있는가.

- 변수(혹은 함수나 클래스)의 존재 이유는?
- 수행 기능은?
- 사용 방법은?

따로 주석이 필요하다면 의도를 분명히 드러내지 못했다는 말.

---

```java
int h; 경과 시간(단위: 시)
```

이름 h는 아무 의미가 없다. 경과 시간이라는 느낌이 안든다.

```java
int elapsedHours;
int fileAgeInHours;
```

의도가 드러나는 이름을 사용하면 코드 이해와 변경이 쉬워진다.

---

```java
public List<int[]> getThem(List<int[]> list) {
  List<int[]> resultList = new ArrayList<int[]>();
  for (int[] x : list)
    if (x[2] == 1)
    list.add(x);
  return resultList;
}
```

공백이나 들여쓰기가 적당하고 복잡한 문장이 없지만 코드가 하는 일을 짐작하기 어렵다.

문제는 코드의 `단순성`이 아닌 코드의 `함축성`.

코드 맥락이 코드 자체에 명시적으로 드러나지 않는다.

- list에 무엇이 들어있는지
- `int[] x`에서 index 2의 값이 왜 중요한지
- 값 1은 무슨 의미인지
- 함수가 반환하는 resultList를 어떻게 사용하는지

이런 정보가 드러나지 않는다.

---

하지만 이렇다면,

```java
public List<Block> getCheckedBlocks(List<Block> blockList) {
  List<Block> checkedBlocks = new ArrayList<Block>();
  for (Block block : blockList)
    if (block.isChecked())
      checkedBlocks.add(block);
  return checkedBlocks;
}
```

코드의 `단순성`은 변하지 않았지만 코드는 더욱 명확해진다.

단순히 이름만 고쳐도 함수가 하는 일을 이해하기 쉬워졌다. (그 외 `int[]` 대신 `Block` 클래스를 사용하고, if 문에서 메소드를 추가했지만)
779849865a1a516946ccb50abee3bf7238c8537a

이것이 좋은 이름이 주는 위력이다.
