#### MDN

화살표 함수는 자신만의 this를 생성하지 않습니다. this는 감싸고 있는 컨텍스트(스코프)로 부터 원래의 의미를 갖습니다. 그래서 다음 코드는 기대한대로 작동합니다.

```js
function Person(){
  this.age = 0;

  setInterval(() => {
    this.age++; // |this| 는 정확히 person 객체를 참조
  }, 1000);
}

var p = new Person(); // p.age > 0

/* */

var p = Person(); // 이 경우 age는 window에 생성되고 증가한다. Person()의 this는 window가 되니까.
```

#### http://es6katas.org/
```js
// 5: arrow functions - basics
// To do: make all tests pass, leave the asserts unchanged!

describe('arrow functions', function() {

  it('are shorter to write', function() {
    var func = () => {
      return 'I am func';
    };
    assert.equal(func(), 'I am func');
  });

  it('a single expression, without curly braces returns too', function() {
    var func = () => 'I return too';
    assert.equal(func(), 'I return too');
  });

  it('one parameter can be written without parens', () => {
    var func = p => p - 1;
    assert.equal(func(25), 24);
  });

  it('many params require parens', () => {
    var func = (param, param1) => param + param1;
    assert.equal(func(23, 42), 23+42);
  });

  it('body needs parens to return an object', () => {
    var func = () => {
      return {iAm: 'an object'};
    }
    assert.deepEqual(func(), {iAm: 'an object'});
  });

});
```

```js
// 6: arrow functions - binding
// To do: make all tests pass, leave the asserts unchanged!

class LexicallyBound {
  getFunction() {
    return () => {
      return this;
    }
  }

  getArgumentsFunction() {
    return () => arguments;
  }

}

describe('arrow functions have lexical `this`, no dynamic `this`', () => {

  it('bound at definition time, use `=>` ', function() {
    var bound = new LexicallyBound();
    var fn = bound.getFunction();

    assert.strictEqual(fn(), bound);
  });

  it('can NOT bind a different context', function() {
    var bound = new LexicallyBound();
    var fn = bound.getFunction();
    var anotherObj = {};
    var expected = bound;

    assert.strictEqual(fn.call(anotherObj), expected);
  });

  it('`arguments` doesnt work inside arrow functions', function() {
    var bound = new LexicallyBound();
    var fn = bound.getArgumentsFunction();

    assert.equal(fn(1, 2).length, 0);
  });

});
```
