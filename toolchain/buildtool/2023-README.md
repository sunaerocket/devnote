# Build Tool

브라우저에서 구동하는 웹 애플리케이션을 만드는 작업을 수행하는 도구.

1. **번들링**: SPA을 구성하는 여러 파일들을 하나의 JS 파일로 묶어주는 작업
2. **트랜스파일링**: 최신 문법으로 작성된 코드를 구형 브라우저에서도 동작할 수 있도록 변환하는 작업(e.g. babel, TypeScript)
3. **최적화**: minify, uglify, tree-shaking 등을 통해 파일 크기를 줄이는 작업

2023년 현재, 빌드 속도를 개선하기 위해 esbuild, swc 같은 도구들을 활용하는 추세에서 vite, turbopack, parcel, webpack 같은 도구가 인기를 얻고 있다.

## 웹사이트 빌드 과정이 표준이 된 이유

초기 웹사이트는 `index.html` 파일 내부에 `<script>` 태그를 사용하여 필요한 자바스크립트 파일을 추가했다. 이후 Node.js가 등장하면서 서버와 백엔드도 자바스크립트로 작성할 수 있는 환경이 되었다. 이때까지는 웹사이트를 구성하는 파일들을 서버에서 렌더링하여 클라이언트에 전달하는 방식이었다.

그런던 중 누군가가 "서버 측 자바스크립트 코드를 브라우저에서 작성할 수 있다면 어떨까?"라는 생각을 던졌고, 사람들은 아이디어를 실험하기 위해 몇가지 문제들을 해결해야 했다.

우선 클라이언트와 서버 양측 자바스크립트의 호환성 문제가 있었다. 브라우저는 URL을 통해 필요한 리소스를 비동기적으로 가져오기 위해 탄생했고, 노드는 파일 시스템을 기반으로 서버사이드에서 자바스크립트를 실행하려고 만들었다. 웹사이트 빌드 과정은 다양한 호환성 문제를 해결하기 위해 탄생했다.

1. 브라우저에는 `Package Manager`가 없었지만, 프론트엔드 개발자들이 브라우저에서 쉽게 종속성을 관리할 수 있는 도구를 강력하게 원했기 때문에 npm이 서버와 클라이언트 양측을 위한 패키지 관리자로 자리잡았다.
2. 그러나 npm 모듈과 이를 임포트하는 방법인 `CommonJS`는 브라우저에서 지원하지 않았다.
3. 2009년 이후 상대적으로 브라우저 자바스크립트는 꾸준히 발전해왔으나(Promise, async/await, ES Module, class 등) 노드는 이런 변화를 지원하지 않았다.
4. 서버에서 사용하는 자바스크립트는 여러가지 옵션이 있었다 - 파이썬과 루비와 유사한 스타일을 도입한 CoffeeScript, HTML 마크업 작성을 허용한 JSX, 타입 안정성을 구현한 TypeScript - 그러나 브라우저에서 사용하려면 결국 일반 자바스크립트로 변환해야 했다.
5. 노드는 모듈화 되어 있으므로, 클라이언트로 전송하는 코드의 양을 줄이려면 `bundle`, `minify` 과정이 필수적이었다.
6. 또한 원본 코드에서 사용한 기능 중 일부는 구형 브라우저에서 지원하지 않았기 때문에 `polyfill`이 필요했다.
7. 복잡한 CSS를 관리하기 위한 도구인 `CSS Framework`나 `CSS Preprocessor` 역시 브라우저에서 구문 분석이 가능한 일반 CSS로 변환해야 했다.
8. `Static Site Generator`가 동적 데이터를 렌더링하려면 배포 이전에 작업을 처리해야 했다.

프레임워크와 메타 프레임워크는 복잡한 앱을 더 쉽게 작성하고 관리하도록 DX 개선을 이뤄냈지만, 반대 급부로 복잡한 빌드 단계로 이어졌다. 최종 사용자를 위한 성능 최적화 작업도 추가되면서 앞서 말한 코드 변환 작업을 수행하게 되는데, 이것이 오늘날 우리가 겪는 빌드 단계다.

## 자바스크립트 빌드 도구 타임라인

* [Browserify](https://browserify.org/) - 2011
* [Grunt](https://gruntjs.com/) - 2012
* [Bower](https://bower.io/) - 2012
* [Gulp](https://gulpjs.com/) - 2013
* [Babel](https://babeljs.io/) - 2014
* [Webpack](https://webpack.js.org/) - 2014
* [Rollup](https://rollupjs.org/) - 2015
* [Parcel](https://parceljs.org/) - 2017
* [SWC](https://swc.rs/) - 2019
* [Vite](https://vitejs.dev/) - 2020
* [ESBuild](https://esbuild.github.io/) - 2020
* [Turbopack](https://turbo.build/pack) - 2022

2020년대에 접어들면서, 빌드 도구들은 개발자가 선호하는 기술을 지원하기 위한 자체 플러그인, 로더 생태계를 갖추기 시작했다. 따라서 개발자는 더 유연하게 자신만의 빌드 스택을 선택할 수 있다(e.g. 모듈 번들러 = 웹팩, TS 트랜스파일러 = 바벨, 스타일링 = Tailwind용 포스트css 로더).

## Next.JS 빌드 프로세스

서버사이드 자바스크립트를 브라우저에서 실행하기 위해 거치는 NextJS 빌드 단계는 다음과 같다.

* Compiling
* Minifying
* Bundling
* Code Splitting

### Compiling

현대 웹 개발에서는 생산성과 개발자 경험을 중시하며, Next.JS는 이를 위해 React, ESM 모듈, JSX, async/await, TypeScript 같은 문법을 사용한다. 따라서 브라우저가 코드를 실행하기 위해서는 바닐라 자바스크립트로 변환하는 과정이 필요하다.

1. 코드를 구문 분석하여 AST(Abstract Syntax Tree)로 변환
2. AST를 목표 언어 표현으로 수정
3. 수정된 AST를 기반으로 코드 생성

### Minifying

최종 사용자의 성능을 개선하기 위해 함수 및 컴포넌트 이름을 단일 문자로 대체하여 브라우저에 전송하는 정보량을 줄인다.

### Bundling

브라우저에 제공할 단일 자바스크립트 파일을 생성하는 과정으로, 코드 진입점을 기준으로 의존성 그래프를 생성한다. 보통 진입점은 `index.js` 파일이며 이를 의존하는 파일들을 찾아내고, 찾아낸 파일들을 의존하는 파일들을 의존하는 파일들을 찾는 식의 작업을 거친다. 이렇게 생성된 의존성 그래프를 기반으로 코드를 결합한다.

프로젝트 복잡도가 커질수록 빌드 시간이 증가하는 경향을 보이는 이유는 종속성 그래프를 탐색하고 생성한 다음 클라이언트에 전송하는 데 필요한 것을 단일 번들로 추가하는 시간이 증가하기 때문이다.

### Code Splitting

필요한 코드만 우선 호출하기 위한 `지연 로딩` 기법으로, 진입점을 페이지 또는 컴포넌트 별로 구분하여 번들 파일을 분할한다.

## No-Build-Step Framework

`Deno` 진영에서는 빌드 과정이 없는 프레임워크인 [Fresh](https://fresh.deno.dev/)를 대안으로 제시하고 있다.

## 참고자료

* [You Don't Need a Build Step](https://deno.com/blog/you-dont-need-a-build-step)
