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

### 6. var, let, const

let 과 const 의 타입 추론

```ts
let a: string = '에이';
let b = '비이';

const c: string = '씨이';
const d = '디이';

/*
1. a는 명시적으로 지정된 타입인 string
2. b는 타입추론에 의한 타입인 string
3. c는 명시적으로 지정된 타입인 String
4. d는 타입추론에 의한 타입인 리터럴타입 '디이'
*/
```

### 7. Type assertions, Type alias

Type assertion
- 형변환과는 다르다.
- `타입이 이것이다`라고 컴파일러에게 알려주는 것 뿐. 런타임에 영향 x
- 문법
 - `변수 as 강제할타입`
 - `<강제할타입>변수`

Type alias
- 타입 별칭
- 인터페이스랑 비슷해보임
- 주로 Union Type, Tuple에 쓰임

Interface와의 차이점
```ts
type Alias = { num: number }

inferface Interface {
  num: number;
}

declare function aliased(arg: Alias): Alias;
declare function interfaced(arg: Interface): Interface;
/*
1. type alias 는 object literal type으로
2. interface 는 interface로
*/
```

### 8. Interface
```ts
interface Person {
  name: string;
  age?: number;  // optional
}
```

function in interface
```ts
interface Person {
  name: string;
  age: number;
  hello(): void;
}

const p1: Person = {
  name: 'me',
  age: 1,
  hello: function (): void {
    console.log(this);
  }
}
```

class implements interface
```ts
interface IPerson {
  name: string;
  age?: number;
  hello(): void;
}

class Person implements IPerson {
  name: string;

  constructor(name: string) {
    this.name = name;
  }

  hello(): void {
    console.log(`hello I'm ${this.name}.`);
  }
}

const person = new Person('me');
person.hello();
```

interface extends interface
```ts
interface Person {
  name: string;
  age?: number;
}

interface Korean extends Person {
  city: string;
}

const k: Korean = {
  name: '나',
  city: '서울'
}
```

Indexable Types

```ts
// string or Number

interface StringArray {
    [index: number]: string;
}

const sa: StringArray = {}; // 옵셔널하다
sa[100] = '백';

interface StringDictionary {
    [index: string]: string;
}

const sd: StringDictionary = {}; // 옵셔널하다
sd.hundred = '백';

interface StringArrayDictionary {
    [index: number]: string;
    [index: string]: string;
}

const sad: StringArrayDictionary = {};
// 당연히 옵셔널하다.
sad[100] = '백';
sad.hundred = '백';
}
```

string index = optional property

```ts
interface StringDictionary {
    [index: string]: string;
    name: string;
}

const sd: StringDictionary = {
    name: '이름' // 필수
};

sd.any = 'any'; // 어떤 프로퍼티도 가능
```

### 9. Class (1)

클래스 만들기
```ts
class Person {
    name: string;
    age: number;
}

const person: Person = new Person();
console.log(person); // Person {}
person.age = 35;
console.log(person.name); // undefined

/*

1. 생성자 함수가 없으면, 디폴트 생성자가 불린다.

2. 클래스의 프로퍼티 혹은 멤버 변수가 정의되어 있지만, 값을 대입하지 않으면 undefined 이다.
=> 오브젝트에 프로퍼티가 아예 존재하지 않는다.

3. 접근제어자 (Access Modifier) 는 public 이 디폴트 이다.

*/
```

클래스와 프로퍼티 (1)
```ts
class Person {
    name: string;
    age: number;

    constructor() {
        console.log(this.name === null); // false
        console.log(this.name === undefined); // true
    }
}
```

클래스와 프로퍼티 (2)
```ts
class Person {
    name: string = 'Mark';
    age: number = 35;

    constructor() {
        console.log(this.name); // 'mark'
    }
}

const person: Person = new Person();
console.log(person); // Person {name: 'Mark', age: 35}

/*

1. 클래스의 프로퍼티를 선언과 동시에 값을 할당하는 방법도 있다.

2. 생성자가 불리기 전에 이미 프로퍼티의 값이 저장되어 있음을 알 수 있다.

*/
```

클래스와 프로퍼티의 접근 제어자 (1)
```ts
class Person {
    public name: string;
    private _age: number;

    constructor(age: number) {
        this._age = age;
    }
}

const person: Person = new Person(35);
person.name = 'Mark';
// person._age (X)
console.log(person); // Person {name: 'Mark', _age: 35}

/*

1. private 으로 설정된 프로퍼티는 dot 으로 접근할 수 없다.

2. 클래스 내부에서는 private 프로퍼티를 사용할 수 있다.

3. private 이 붙은 변수나 함수는 _ 를 이름앞에 붙이는데,
이는 문법이 아니라 널리 쓰이는 코딩 컨벤션이다.

*/
```

클래스와 프로퍼티의 접근 제어자 (2)
```ts
class Parent {
    private privateProp: string;
    protected protectedProp: string;

    constructor() {

    }
}

class Child extends Parent {
    constructor() {
        super();

        this.protectedProp = 'protected';
        // this.privateProp = 'private'; // (X)
    }
}

/*

1. 부모에서 private 으로 설정된 프로퍼티는 상속을 받은 자식에서도 접근할 수 없다.

2. 부모에서 protected 로 설정된 프로퍼티는 상속을 받은 자식에서 접근이 가능하다.

3. 상속을 받은 자식 클래스에서 부모 클래스에 this 를 통해 접근하려면, 생성자에서 super(); 를 통해 초기화 해야한다.
*/
```

클래스와 디폴트 생성자
```ts
class Person {
    public name: string;
    private _age: number;

    constructor(age: number) {
        this._age = age;
    }
}

const person: Person = new Person();

/*

1. 디폴트 생성자는 프로그래머가 만든 생성자가 없을 때 사용할 수 있다.
=> 사용자가 만든 생성자가 하나라도 있으면, 디폴트 생성자는 사라진다.

*/
```

클래스와 메서드
```ts
class Person {
    constructor(private _name: string, private _age: number) { }

    print(): void {
        console.log(`이름은 ${this._name} 이고, 나이는 ${this._age} 살 입니다.`);
    }

    printName = (): void => {
        console.log(`이름은 ${this._name} 입니다.`);
    }

    private printAge(): void  {
        console.log(`나이는 ${this._age} 살 입니다.`);
    }
}

const person: Person = new Person('Mark', 35);
person.print(); // 이름은 Mark 이고, 나이는 35 살 입니다.
person.printName(); // 이름은 Mark 입니다.
// person.printAge(); // (X)

/*

1. 클래스 내부에 작성된 메서드는 public 이 디폴트
2. arrow function 으로 작성 가능
3. private 을 이용하면 클래스 외부애서 접근 불가

*/
```

클래스와 상속 (1)
```ts
class Parent {
    constructor(protected _name: string, protected _age: number) { }

    print(): void {
        console.log(`이름은 ${this._name} 이고, 나이는 ${this._age} 살 입니다.`);
    }

    printName = (): void => {
        console.log(`이름은 ${this._name} 입니다.`);
    }

    private printAge(): void  {
        console.log(`나이는 ${this._age} 살 입니다.`);
    }
}

class Child extends Parent {
    _name = 'Mark Jr.';
}

// const p: Child = new Child(); // (X)
const p: Child = new Child('', 5);
p.print(); // 이름은 Son 이고, 나이는 5 살 입니다.

/*

1. 상속은 extends 키워드를 이용한다.
2. 자식 클래스에서 디폴트 생성자는 부모의 생성자와 입력 형태가 같다.

*/
```

클래스와 상속 (2)
```ts
class Parent {
    constructor(protected _name: string, private _age: number) { }

    print(): void {
        console.log(`이름은 ${this._name} 이고, 나이는 ${this._age} 살 입니다.`);
    }

    protected printName = (): void => {
        console.log(`이름은 ${this._name} 입니다.`);
    }

    protected printAge(): void  {
        console.log(`나이는 ${this._age} 살 입니다.`);
    }
}

class Child extends Parent {
    constructor(age: number) {
        super('Mark Jr.', age);

        this.printName();
        this.printAge();
    }
}

const p: Child = new Child(1);
// 이름은 Son 입니다.
// 나이는 1 살 입니다.

/*

1. 생성자를 정의하고, this 를 사용하려면, super 를 통해 부모의 생성자를 호출해줘야 한다.
2. super 를 호출할때는 부모 생성자의 입력 타입이 같아야 한다.
3. super 를 호출하는 것은 클래스 외부에서 호출하는 것과 같다.
4. protected 함수를 호출해서 그 안의 private 을 출력하는 것에 주의한다.

*/
```

### 10. Class(2)

클래스와 getter, setter
```ts
class Person {
    private _name: string;
    private _age: number;

    constructor(name: string, age: number) {
        this._name = name;
        this._age = age;
     }

    get name() {
        return this._name;
    }

    set name(name: string) {
        // 작업
        this._name = `${name} Lee`;
    }
}

const person: Person = new Person('Mark', 35);

console.log(person.name);
person.name = 'Woongjae';
console.log(person.name);

/*

1. _ 를 변수명 앞에 붙이고, 내부에서만 사용한다.
2. getter 를 함수처럼 설정하면, 프로퍼티처럼 꺼내쓸수있다.
3. 마찬가지로 setter 를 함수처럼 설정하면, 추가 작업을 하고 셋팅할 수 있다.

*/
```

클래스와 static 프로퍼티 => 클래스 멤버 변수
```ts
class Person {
    public static CITY = "";
    private static lastName: string = 'Lee';
    private _name: string;
    private _age: number;

    constructor(name: string, age: number) {
        this._name = name;
        this._age = age;
     }

    public print() {
        console.log(`${this._name} ${Person.lastName} in ${Person.CITY}.`);
    }
}

const person: Person = new Person('Mark', 35);
Person.CITY = 'Seoul';
person.print(); // Mark Lee in Seoul.

/*

1. static 키워드를 붙힌 프로퍼티는 클래스.프로퍼티로 사용한다.
2. static 프로퍼티에 private, protected 를 붙히면 똑같이 동작한다.

*/
```

클래스와 static 메서드 => 클래스 멤버 함수
```ts
class Person {
    public static Talk(): void {
        console.log('안녕하세요.');
    }
}

Person.Talk(); // 안녕하세요.
```

모듈에서 private static 프로퍼티 혹은 메서드 (뭐가 좋은지 생각해보기)
```ts
class Person {
    private static PROPERTY = '프라이빗 프로퍼티';
    private static METHOD() {
        console.log('프라이빗 메서드');
    }

    constructor() {
        console.log(Person.PROPERTY);
        Person.METHOD();
    }
}

//////////////////////////////////////////////

const PROPERTY = '모듈 내 변수';
function METHOD() {
    console.log('모듈 내 함수');
}

export class Person {
    constructor() {
        console.log(PROPERTY);
        METHOD();
    }
}
```

Abstract Class
```ts
abstract class APerson {
    protected _name: string = 'Mark';
    abstract setName(name: string): void;
}

class Person extends APerson {
    setName(name: string): void {
        this._name = name;
    }
}

// const person = new APerson(); // (X)
const person = new Person();

/*

1. abstract 키워드가 사용된 클래스는 new 로 생성할 수 없다.
2. abstract 키워드가 사용된 클래스를 상속하면 abstract 키워드가 붙은 함수를 구현해야 한다.

*/
```

Class 와 private constructor
```ts
class Preference {
    private constructor() {

    }
}

// const p: Preference = new Preference(); (X)

/*

1. 생성자 함수 앞에 접근제어자인 private 을 붙일 수 있다.
2. 외부에서 생성이 불가능하다.

*/
```

Class 와 싱글톤 패턴
```ts
class Preference {
    public static getInstance() {
        if (Preference.instance === null) {
            Preference.instance = new Preference();
        }

        return Preference.instance;
    }
    private static instance: Preference = null;
    private constructor() {

    }
}

const p: Preference = Preference.getInstance();

/*

1. private 생성자를 이용해서 내부에서만 인스턴스 생성이 가능하도록 함.
2. pubilc static 메서드를 통해 private static 인스턴스 레퍼런스를 획득한다.
3. Lazy Loading (Initialization) : 최초 실행시가 아니라, 사용시에 할당을 함

*/
```

Class 와 readonly
```ts
class Person {
    private readonly _name: string = null;
    public readonly age: number = 35;

    constructor(name: string) {
        this._name = name;
    }

    public setName(name: string) {
        // this._name = name; (X)
    }
}

const p: Person = new Person('Mark');
console.log(p.age);
// p.age = 36; // (X)

/*

1. private readonly 로 선언된 경우, 생성자에서는 할당이 가능하다.
2. private readonly 로 선언된 경우, 생성자 이외에서는 할당이 불가능하다.
3. public readonly 로 선언된 경우, 클래스 외부에서는 다른값을 할당할 수 없다.
4. 마치 getter 만 있는 경우와 같다.
*/
```

### 11. Generic
