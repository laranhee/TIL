#### http://es6katas.org/

```js
// 22: class - creation
// To do: make all tests pass, leave the assert lines unchanged!

describe('class creation', () => {

  it('is as simple as `class XXX {}`', function() {
    class TestClass {}

    const instance = new TestClass();
    assert.equal(typeof instance, 'object');
  });

  it('class is block scoped', () => {
    {class Inside {}}
    assert.equal(typeof Inside, 'undefined');
  });

  it('special method is `constructor`', function() {
    class User {
      constructor(id) {
        this.id = id;
      }
    }

    const user = new User(42);
    assert.equal(user.id, 42);
  });

  it('defining a method is simple', function() {
    class User {
      writesTests() {
        return false;
      }
    }

    const notATester = new User();
    assert.equal(notATester.writesTests(), false);
  });

  it('multiple methods need no commas (opposed to object notation)', function() {
    class User {
      constructor() { this.everWroteATest = true; }
      wroteATest() { this.everWroteATest = !this.everWroteATest; }
      isLazy() { return this.everWroteATest; }
    }

    const tester = new User();
    assert.equal(tester.isLazy(), true);
    tester.wroteATest();
    assert.equal(tester.isLazy(), false);
  });

  it('anonymous class', () => {
    const classType = typeof class {};
    assert.equal(classType, 'function');
  });

});
```

```js
// 23: class - accessors
// To do: make all tests pass, leave the assert lines unchanged!

describe('class accessors (getter and setter)', () => {

  it('only a getter is defined like a method prefixed with `get`', () => {
    class MyAccount {
      get balance() { return Infinity; }
    }

    assert.equal(new MyAccount().balance, Infinity);
  });

  it('a setter has the prefix `set`', () => {
    class MyAccount {
      get balance() { return this.amount; }
      set balance(amount) { this.amount = amount; }
    }

    const account = new MyAccount();
    account.balance = 23;
    assert.equal(account.balance, 23);
  });

  describe('dynamic accessors', () => {

    it('a dynamic getter name is enclosed in [ and ]', function() {
      const balance = 'yourMoney';
      class YourAccount {
        get [balance]() { return -Infinity; }
      }

      assert.equal(new YourAccount().yourMoney, -Infinity);
    });

    it('a dynamic setter name as well', function() {
      const propertyName = 'balance';
      class MyAccount {
        get [propertyName]() { return this.amount; }
        set [propertyName](amount) { this.amount = 23; }
      }

      const account = new MyAccount();
      account.balance = 23;
      assert.equal(account.balance, 23);
    });
  });

});
```

```js
// 24: class - static keyword
// To do: make all tests pass, leave the assert lines unchanged!

describe('inside a class you can use the `static` keyword', () => {

  describe('for methods', () => {

    class IntegrationTest {}
    class UnitTest {}

    it('a static method just has the prefix `static`', () => {
      class TestFactory {
        static makeTest() { return new UnitTest(); }
      }

      assert.ok(TestFactory.makeTest() instanceof UnitTest);
    });

    it('the method name can be dynamic/computed at runtime', () => {
      const methodName = 'createTest';
      class TestFactory {
        static [methodName]() { return new UnitTest(); }
      }

      assert.ok(TestFactory.createTest() instanceof UnitTest);
    });
  });

  describe('for accessors', () => {
    it('a getter name can be static, just prefix it with `static`', () => {
      class UnitTest {
        static get testType() { return 'unit'; }
      }

      assert.equal(UnitTest.testType, 'unit');
    });

    it('even a static getter name can be dynamic/computed at runtime', () => {
      const type = 'test' + 'Type';
      class IntegrationTest {
        static get [type]() { return 'integration'; }
      }

      assert.ok('testType' in IntegrationTest);
      assert.equal(IntegrationTest.testType, 'integration');
    });
  });

});
```

```js
// 25: class - extends
// To do: make all tests pass, leave the assert lines unchanged!

describe('classes can inherit from another', () => {

  describe('the default super class is Object', () => {

    it('class A is an instance of Object', () => {
      class A {}

      assert.equal(new A() instanceof Object, true);
    });

    it('B extends A, B is also instance of Object', () => {
      class A {}
      class B extends A {}

      assert.equal(new B() instanceof A, true);
      assert.equal(new B() instanceof Object, true);
    });

    it('class can extend `null`, not an instance of Object', () => {
      class NullClass extends null {
        constructor() {
          return Object.create(NullClass.prototype);
        }
      }

      let nullInstance = new NullClass();
      assert.equal(nullInstance instanceof Object, false);
    });

  });

  describe('instance of', () => {
    it('when B inherits from A, `new B()` is also an instance of A', () => {
      class A {}
      class B extends A {}

      assert.equal(new B() instanceof A, true);
    });

    it('extend over multiple levels', () => {
      class A {}
      class B extends A {}
      class C extends B {}

      let instance = new C();
      assert.equal(instance instanceof A, true);
    });
  });
});
```

```js
// 26:
```

```js
// 27: class - super inside a method
// To do: make all tests pass, leave the assert lines unchanged!

describe('inside a class use `super` to access parent methods', () => {

  it('use of `super` without `extends` fails (already when transpiling)', () => {
    class A {hasSuper() { return false; }}

    assert.equal(new A().hasSuper(), false);
  });

  it('`super` with `extends` calls the method of the given name of the parent class', () => {
    class A {hasSuper() { return true; }}
    class B extends A {hasSuper() { return super.hasSuper(); }}

    assert.equal(new B().hasSuper(), true);
  });

  it('when overridden a method does NOT automatically call its super method', () => {
    class A {hasSuper() { return true; }}
    class B extends A {hasSuper() {}}

    assert.equal(new B().hasSuper(), void 0);
  });

  it('`super` works across any number of levels of inheritance', () => {
    class A {iAmSuper() { return this.youAreSuper; }}
    class B extends A {constructor() { super(); this.youAreSuper = true; } }
    class C extends B {
      iAmSuper() {
        return super.iAmSuper();
      }
    }

    assert.equal(new C().iAmSuper(), true);
  });

  it('accessing an undefined member of the parent class returns `undefined`', () => {
    class A {}
    class B extends A {getMethod() { return super.a; }}

    assert.equal(new B().getMethod(), void 0);
  });

});
```
