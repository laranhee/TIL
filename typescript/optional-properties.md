## Optional Properties

인터페이스에 필수가 아니지만 가능한 프로퍼티를 선언할 수 있음

```ts
interface Member {
  name: string;
  age?: number;
}
```

```ts
const member1: Member = {name: 'Odd'}; // OK
const member2: Member = {name: 'Odd', age: 1}; // OK
const member3: Member = {name: 'Odd', phone: 11111}; // compile error
```

#### Reference

https://www.typescriptlang.org/docs/handbook/interfaces.html
