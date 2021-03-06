## 인코딩을 피하라

이름에 인코딩할 정보는 아주 많다. 유형이나 범위정보까지 인코딩에 넣으면 그만큼 해독하기 어렵다.

#### 헝가리식 표기법

과거 윈도 C API는 헝가리식 표기법을 굉장히 중요하게 여겼다. 윈도 C API는 모든 변수가 정수 핸들, long 포인터, void 포인터, (속성과 용도가 다른) 여러 문자열 중 하나였다. 당시는 컴파일러가 타입을 점검하지 않았으므로 프로그래머에게 타입을 기억할 단서가 필요했다.

요즘 나오는 프로그래밍 언어는 훨씬 많은 타입을 지원한다. 또한 컴파일러가 타입을 기억하고 강제한다.

클래스와 함수는 점차 작아지는 추세다. (즉, 변수를 선언한 위치와 사용하는 위치가 멀지 않다.)

자바는 변수 이름에 타입을 인코딩할 필요가 없다. 객체는 강한타입이고, IDE는 코드를 컴파일하지 않아도 타입 오류를 감지할 수 있다.

따라서 헝가리식 표기법이나 기타 인코딩 방식이 오히려 방해가 된다. 변수, 함수, 클래스 이름이나 타입을 바꾸기 어려워지고 읽기도 어려워진다.

#### 멤버 변수 접두어

멤버 변수에 `m_`이라는 접두어를 붙일 필요가 없다. 클래스와 함수는 접두어가 필요없을 정도로 작아야 마땅하다. 멤버 변수를 다른 색상으로 표시하거나 눈에 띄게 보여주는 IDE를 사용하야 마땅하다.

사람들은 접두어(또는 접미어)를 무시하고 이름을 해독하는 방식을 익힌다. 코드를 읽을수록 접두어는 관심 밖으로 밀려난다.

#### 인터페이스 클래스와 구현 클래스

때로는 인코딩이 필요한 경우도 있다. 인터페이스 클래스가 있고 이를 구현한 구현 클래스가 있다면, 인터페이스 클래스 이름을 인코딩하는 대신(`IAnimalFactory`) 구현 클래스 이름을 인코딩 하라(`AnimalFactoryImpl`). 옛날 코드에서 많이 사용하던 접두어 `I`는 잘해야 주의를 흐트리고 나쁘게는 과도한 정보를 제공한다.
