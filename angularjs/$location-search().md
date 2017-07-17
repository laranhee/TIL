## $location.search()

```js
search(search, [paramValue]);
```

```
example URL http://example.com?foo=a&bar=b
```

#### get search value

```js
var searchObject = $location.search();
// => {foo: 'a', bar: 'b'}
```

#### set search value

```js
// set foo to 'A'
$location.search('foo', 'A');
// $location.search() => {foo: 'A', bar: 'b'}
```

#### delete specified search value

```js
// delete foo
$location.search('foo', null);
// $location.search() => {bar: 'b'}
```
