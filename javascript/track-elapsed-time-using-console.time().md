## 수행시간 측정하기

```javascript
console.time(label); // 새 타이머 시작

console.timeEnd(label); // 타이머 종료
```

`label` : 만들어질 타이머의 식별 이름

`console.time(label)`을 통해 타이머를 생성하고,

`console.timeEnd(label)` 호출로 타이머를 종료하면,

 해당 타이머의 생성 시간부터 종료 시간까지의 경과시간이 console에 출력된다.

#### 예시

```javascript
console.time('A');

for (var i = 0; i < 100; i++) {

}

console.timeEnd('A');
```

![screenshot](./track-elapsed-time-using-console.time().png)
