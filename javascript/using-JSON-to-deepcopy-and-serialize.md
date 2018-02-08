## JSON을 이용한 deep copy와 serialize

```js
var a = {
    b: 1,
    c: 'c'
}

var b = JSON.parse(JSON.stringify(a));

a === b // false;
```
