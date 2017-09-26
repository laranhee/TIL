## Mixed Mode

`embedded mode`에서 multiple connection이 가능하게 하려면 `mixed mode`로 이용해야 한다.

![](http://www.h2database.com/html/images/connection-mode-mixed-2.png)

embedded db로 h2 서버를 시작해 외부 어플리케이션에서도 이 db에 접속할 수 있다.

db url에 `AUTO_SERVER=TRUE`를 붙이면 자동으로 `mixed mode`가 된다.

```
jdbc:h2:/data/test;AUTO_SERVER=TRUE
```

해당 방식으로 처음 접속 할 때 서버가 시작된다.

이후의 접속은 이 서버에 붙는다.

웹어플리케이션이 embedded db에 붙을 때, db client에서도 해당 db에 붙기 위해 사용했다.

#### Reference

http://www.h2database.com/html/features.html#connection_modes
