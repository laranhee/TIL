package.json의 scripts에 `node_modules/.bin/`에 있는 것은 경로 지정 없이 사용 가능

```json
// node_modules/.bin/tsc test.ts가 아닌 npm run transpile로 실행 가능
{
  "scripts": {
    "transpile": "tsc est.ts"
  }
}
```
