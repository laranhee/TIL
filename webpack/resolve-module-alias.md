## resolve module alias

```js
alias: {
  Utilities: path.resolve(__dirname, "src/utilities/");
}
```

```js
// import Utility from '../../utilities/utility';
import Utility from "Utilities/ajax-util";
```
