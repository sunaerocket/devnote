# React 프로젝트 환경 구성

개발을 원활하게 하기 위한 도구 조합을 구성한다.

- 모듈 번들링
- 정적분석
- 스타일링
- 라우팅
- 테스팅

## 모듈 번들링(Module Bundling)

웹 개발에서 JavaScript나 스타일시트, 이미지 등 웹에서 사용하는 모든 자원을 모듈로 간주하여 서로간의 의존 관계를 파악한 뒤, 필요한 요소만 하나의 파일로 묶어서 처리하는 기술이다.

대표적인 장점은 다음과 같다.

1. `유지보수가 편리`: 모듈 단위로 코드를 분리하면 문제 범위도 격리되는 효과가 있다
2. `네트워크 요청 감소`: 모든 자원을 하나의 파일로 번들링하여 파일 요청 수가 감소하여 성능 향상에 기여 한다
3. `파일 크기 최적화`: 중복없이 필요한 모듈만을 가져와서 하나의 파일로 번들링한다

대표적인 단점은 다음과 같다.

1. `번들링 시간 증가`: 복잡도가 높은 프로젝트의 경우 번들링 시간이 길어질 수 있다
2. `초기 로딩 시간 증가`: 번들 파일의 크기가 클수록 다운로드를 포함한 초기 로딩 시간이 길어진다
3. `학습 곡선`: 도구에 따라 학습에 시간이 많이 걸릴 수 있다

최신 도구들은 번들링이나 초기 로딩 시간을 줄이거나 학습 곡선을 낮추는 방향으로 발전하고 있다.

### 선택지

#### Parcel

> "The zero configuration build tool for the web"

2018년에 출시한 모듈 번들러로 설정이 간편하다는 것을 강조하며, 성능 측면에서는 JS 컴파일러로 SWC를 채택한 것과 모든 작업을 캐싱 처리하여 필요한 부분만 빌드한다는 것이 특징이다.

#### Vite

> "Next Generation Frontend Tooling"

2020년에 출시한 프론트엔드 도구로 Vue 진영의 Evan You가 개발한 도구로, 개발 모드에서 번들링 작업이 필요하지 않다는 점을 지적한다.

대규모 프로젝트에서 기존 번들러들로 개발 서버를 구동하면 번들링 시간으로 몇 분에 걸친 긴 대기 시간을 거쳐야하며, HMR 기술을 사용하더라도 변경 사항이 브라우저에 반영되는 데 몇 초가 걸린다.

vite는 개발 서버를 구동할 때, 변경이 거의 없는 종속성 모듈과 소스 코드를 구분한다. 종속성 모듈은 esbuild를 사용하여 빠르게 번들링하고, 소스코드는 브라우저 요청이 있을 때마다 실시간으로 소스코드를 트랜스파일(JSX 등)하여 ES모듈 형태로 브라우저에 전달한다. 결과적으로 번들링 속도를 개선하고 횟수를 줄여 속도를 높였다.

개발 서버가 갱신 작업을 할 때 vite는 번들링된 파일을 다시 빌드하는 대신, 변경된 모듈만 무효화하기 때문에 어플리케이션의 복잡도가 증가해도 일관되게 빠른 갱신 속도를 유지한다.

그러나 프로덕션에서는 번들링이 필요하다. 번들되지 않은 ESM을 가져오기 위해서 네트워크 요청 수가 폭증하고, 네트워크 오버헤드 때문에 종합적인 성능이 떨어지기 때문이다. 따라서 프로덕션 환경에서는 번들링을 하되 트리 쉐이킹, 지연 로딩, 청크 분할을 통한 캐싱 개선을 통해 성능 최적화를 하는 것을 권장한다.

#### Webpack

2014년에 출시한 모듈 번들러로 널리 사용되고 있는 도구. 설정이 복잡하다는 단점이 있지만, 다양한 플러그인을 제공하고 있어서 특정 기능 구현에 유리하다는 평판이다.

## 정적분석(Static Analysis)

정적분석이란 소스코드를 실행하지 않고 코드 상태로 분석하는 것을 말한다. 정적분석을 통해 개발자의 실수를 사전에 발견할 수 있으며, 코드의 가독성을 높이고 일관성을 유지할 수 있다.

`TypeScript`, `ESLint`를 함께 사용하면 타입 오류를 비롯한 다양한 오류를 발견하고 바람직한 코드 스타일을 유지하는데 도움이 된다.
