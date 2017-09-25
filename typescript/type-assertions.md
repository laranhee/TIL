## Type assertions

#### 타입 캐스팅

런타임에 영향 x, 오직 컴파일에 사용

#### 두가지 방식

- angle-bracket

```ts
let str: any = 'hello';
let strLength: number = (<string>str).length;
```

- `as`

```ts
let str: any = 'hello';
let strLength: number = (str as string).length;
```

#### 둘 다 사용 가능

단, `JSX`에는 `as`만 가능

#### Reference

https://www.typescriptlang.org/docs/handbook/basic-types.html