## data-*

HTML 엘리먼트에 `data-*` 어트리뷰트를 추가하면, `HTMLElement`의 `dataset` 프로퍼티를 통해 `data-*`를 통해 추가한 데이터를 이용할 수 있다.

```html
<div id="section" data-section-id="246">
  
</div>
```

```js
var sectionId = document.getElementById('section').dataset.sectionId;

console.log(sectionId); // 246
```

#### Reference

https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/data-*
