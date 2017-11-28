### 1. TypeScript Overview

타입스크립트는 프로그래밍 언어다.

자바스크립트는 인터프리터 언어지만, 타입스크립트는 컴파일 언어다.

전통적인 컴파일은 컴파일, 링크 등의 작업을 하지만 타입스크립트는 아니다.

따라서 `Transpile`이라는 용어를 사용하기도 함.

메타 프로그래밍이라고도 함.

컴파일 과정에 타입을 체크하는 것이 특징.

동적 타입 언어인 자바스크립트에 정적 타입 언어의 장점만 가져온 것이 타입스크립트

동적 타입 언어의 단점을 커버하려면 테스트 커버리지를 올릴 수 있으나 할수록 힘들고 정적 타입 언어는 타입 체킹을 통해 어느정도 해소

보통의 컴파일은 코드가 작아지지만 타입스크립트의 Transpile은 코드가 더 커짐.

TS -> compiler -> JS

### 2. 개발 환경 구축 및 컴파일러 사용

- A. 실행 환경
- B. 컴파일러
- C. 에디터

실행 환경
- node

타입스크립트 설치
- npm
```sh
npm install typescript
```

에디터 설치
- 아무거나

컴파일하기
- cli 명령어로 컴파일
```sh
tsc test.ts
```
- ts 컴파일러 설정(tsconfig.json)에 맞춰 컴파일
```sh
tsc
```
- tsconfig.json 자동생성
```sh
tsc --init
```
- ts 컴파일러 설정(tsconfig.json)에 맞춰 컴파일 (watch 모드)
```sh
tsc -w
```

VSCode나 IntelliJ 등의 IDE에는 tsc가 내장되어 있음. 그걸 써도 되고 따로 적용해도 됨.

### 3. IDE 활용

tslint
```sh
npm install tslint

tslint --init // tslint.json 생성
```

IDE에 플러그인을 통해 lint를 IDE에서 활용

### 4. compiler Options

최상위 프로퍼티 : tsconfig.json에 들어있는 최상위 프로퍼티
- compileOnSave
- extends
- compileOptions
- files
- include
- exclude
- typeAcquisition

### 5. TypeScript Basic Types
- TypeScript에서 프로그램 작성을 위해 기본 제공하는 데이터타입
- JavaScript 기본 자료형을 포함 (superset)
  - ECMAScript 표준에 따른 기본 자료형은 6가지
    - Boolean
    - Number
    - String
    - Null
    - Undefined
    - Symbol (ECMAScript 6에 추가)
    - Array : object 형
  - 프로그래밍을 도울 몇 가지 타입이 더 제공
    - Any
    - Void
    - Never
    - Enum
    - Tuple : object 형

Undefined & Null
- TypeScript에서 'undefined'와 'null'은 실제로 각각 'undefined'와 'null'이라는 고유한 타입을 가진다.
- 'void'와 마찬가지로, undefined와 null은 그 자체로는 쓸모가 없다.
- 둘다 소문자만 존재한다.

undefined & null are subtypes of all other types
- 모든 타입에 대입이 가능하다.

null in JavaScript
- null이라는 값으로 할당된 것을 null이라 한다.
- 무언가가 있는데, 사용할 준비가 덜 된 상태
- undefined는 아예 없는 상태

Any
- 적폐
- 컴파일 옵션 중에 `noImplicitAny`를 주면 any쓰면 오류를 뱉음

Never
- 리턴에 주로 사용
- 아래 3가지 정도의 경우가 대부분
```ts
// function returning never must have unreachable end point
function error(message: string): never {
  throw new Error(message);
}

// Inferred return type is never
function fail() {
  return error('Something failed');
}

// function returning never must have unreachable end point
function infiniteLoop(): never {
  while (true) {
  }
}
```

Array
- string[]
- Array<string>

Tuple
- 배열인데 타입이 한가지가 아닌 경우
- 마찬가지로 객체
- 꺼내 사용할 때 주의가 필요

Enum
- c에서 보던것과 같다.
- enum의 값은 String

Symbol
- ECMAScript 2015의 Symbol
