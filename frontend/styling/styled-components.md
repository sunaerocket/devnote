# styled components

React 컴포넌트 시스템의 스타일을 지정하기 위한 도구로 주요 마케팅 포인트는 다음과 같다.

- `필수 CSS 자동화 기능(Automatic critical CSS)`: 코드 스플리팅 기술과 결합하여 사용자가 필요한 최소량의 코드만 로딩하도록 한다
- `클래스 이름 버그 방지(No class name bugs)`: 고유한 클래스 이름을 자동으로 생성하여 클래스 이름 중복이나 오타 버그를 방지한다
- `쉬운 스타일 제거(Easier deletion of CSS)`: 스타일은 컴포넌트와 생사를 같이한다
- `간단한 동적 스타일링(Simple dynamic styling)`: props 또는 theme 기반으로 쉽게 조건부 스타일링이 가능하다
- `편안한 유지보수(Painless maintenance)`: 코드베이스가 커져도 컴포넌트에 영향을 미치는 스타일을 찾아 헤멜 필요가 없다
- `벤더사 접두어 자동화(Automatic vendor prefixing)`: 크로스 브라우징을 위한 벤더사 접두어를 자동으로 적용한다

- [styled components motivation](https://styled-components.com/docs/basics)

## 권장사항

- 구문 하이라이팅을 위해 텍스트 에디터에 vscode-styled-components 확장 설치를 권장한다
- 다양한 기능 지원을 위해 swc 사용하는 경우, 바벨 플러그인 설치를 권장한다

## 스타일드 컴포넌트 만들기

1. HTML 요소를 스타일드 컴포넌트로 만들기
2. 스타일드 컴포넌트를 확장하기
3. 기존 컴포넌트를 스타일드 컴포넌트로 만들기

단, 기존 컴포넌트를 스타일드 컴포넌트로 만드려면 class를 잡아줘야 한다.

## 조건부 렌더링

- 스타일드 컴포넌트에 props를 전달하여 조건부 스타일링을 처리한다
- 요소의 속성을 attrs로 전달하여 조건부 스타일링을 처리한다
- 에디터가 제공하는 syntax 하이라이팅을 위해 styled-components에서 제공하는 `css` 함수를 래핑한다
