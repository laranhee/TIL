## Git 브랜치 여러개 삭제하기

```sh
git branch | grep PATTERN | xargs git branch -d
```

예)

![screenshot](./delete-multiple-branches_01.PNG)
