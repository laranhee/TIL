## Array.prototype.splice()

splice() 메소드는 배열에 있는 요소를 삭제하고(하거나) 배열에 새 요소를 추가한다.

```js
var myFish = ['angel', 'clown', 'mandarin', 'sturgeon'];

myFish.splice(2, 0, 'drum'); // 'drum'을 두번째 인덱스에 삽입
// myFish is ["angel", "clown", "drum", "mandarin", "sturgeon"]

myFish.splice(2, 1); // 두번째 인덱스에서 하나의 항목('drum')을 삭제
// myFish is ["angel", "clown", "mandarin", "sturgeon"]
```

### Reference
https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/splice
