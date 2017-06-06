## src/

#### `src/` 밖

빌드, 배포, 테스트와 관련. 설정파일 및 외부 의존성 포함.

#### `src/` 안

앱에 속함. 기본적으로 ts, html, css 파일은 `src/app` 안에 위치한다.

## 기본적인 세 개의 ts 파일

#### app/app.component.ts

`AppCompoment`를 정의. 다른 컴퍼넌트들의 루트 컴퍼넌트.

#### app/app.module.ts

`AppModule`을 정의. Angular에게 어플리케이션을 어떻게 구성할지 알려주는 루트 모듈.

#### main.ts

JIT 컴파일러로 어플리케이션을 컴파일하고, 어플리케이션을 브라우저에서 실행하기 위해 메인 모듈(AppModule)을 부트스트랩한다. JIT 외 AOT(로드타임 감소 및 성능 향상)도 가능.
