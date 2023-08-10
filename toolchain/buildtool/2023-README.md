# Build Tool

브라우저에서 구동하는 웹 애플리케이션을 만드는 작업을 수행하는 도구.

1. **번들링**: SPA을 구성하는 여러 파일들을 하나의 JS 파일로 묶어주는 작업
2. **트랜스파일링**: 최신 문법으로 작성된 코드를 구형 브라우저에서도 동작할 수 있도록 변환하는 작업(e.g. babel, TypeScript)
3. **최적화**: minify, uglify, tree-shaking 등을 통해 파일 크기를 줄이는 작업

2023년 현재, 빌드 속도를 개선하기 위해 esbuild, swc 같은 도구들을 활용하는 추세에서 vite, turbopack, parcel, webpack 같은 도구가 인기를 얻고 있다.
