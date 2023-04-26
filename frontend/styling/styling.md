# Styling

프론트엔드 개발에서 빈번하게 발생하는 문제를 해결하기 위해 등장한 개념들이 있으며, 주로 사용자의 경험을 향상시키는 것을 목표로 한다.

## Responsive Web Design

반응형 웹 디자인은 하나의 웹사이트로 다양한 장치에서 최적화된 사용자 경험을 제공하기 위한 개념으로 `Fluid Grid`, `Flexible Image`, `Media Query` 3가지 아이디어를 중심으로 구성한다.

Fluid Grid 개념은 뷰포트의 너비에 비례하여 그리드 안에 있는 요소들의 크기가 조절하는 것을 의미한다. 데스크탑, 태블릿, 모바일 등 다양한 장치에서도 최적화된 레이아웃을 제공할 수 있다. 유사하게 Flexible Image 개념은 뷰포트 크기에 적절하게 이미지 크기를 조절하는 것을 의미한다. Media Query는 이런 개념들을 적용하는 CSS3 기능이다.

### 등장배경

고전적인 웹 디자인은 인쇄 매체에서 사용하던 개념들을 가져와서 사용했다. 인쇄 매체와는 다르게 웹은 사용자가 뷰포트를 조절할 수 있어서 화면 너비가 달라지면 레이아웃이 깨지는 문제가 발생했다. 모바일 기기가 대중화되면서 뷰포트 문제와 더불어 터치 인터페이스, 브라우저 같은 다양한 환경을 지원해야 했고, 이런 맥락에서 `반응형 웹 디자인`이 등장했다.

### Media Query

다양한 기기에서 웹사이트를 이용할 수 있도록 뷰포트의 너비, 높이, 방향, 해상도 등을 기준으로 스타일을 적용할 수 있도록 하는 CSS3 기능이다.

- [Responsive Web Design by Ethan Marcotte](https://alistapart.com/article/responsive-web-design/)

## Design System

`규격화`(component, theme, pattern)를 통해 재사용성을 높여 대규모 디자인을 관리하는 개념이다.

### Atomic Design

디자인 시스템을 만들기위한 방법론으로 제시된 개념으로 페이지를 더 작은 계층으로 나눠서 구성하는 방식이다.(Page, Template, Organism, Molecule, Atom)

초창기 인터넷은 학술 문서를 공유하기 위한 목적이었기 때문에 `페이지` 은유를 중심으로 구성됐다. 이후 회사들이 인쇄 매체로 관리하던 브로셔를 정적인 웹사이트로 옮기는 것이 유행하던 시기까지 페이지 개념은 문제가 없었다. 그러나 현대 웹사이트는 다양한 인터랙션을 제공하기 때문에 더이상 페이지 개념으로는 프로젝트 공수 산정이 어렵다. 공수 산정은 페이지 개수보다는 `페이지를 구성하는 컴포넌트와 기능`에 강력한 영향을 받는다.

모듈화된 `컴포넌트` 중심으로 페이지를 구성하면 컴포넌트를 조립해서 더 빠르게 인터페이스를 만들 수 있고, 문제가 발생했을 때 범위를 좁혀서 원인을 더 빨리 파악할 수 있게 도움을 준다.

### 사례

- [Atlassian Design System](https://atlassian.design/)
- [Material Design by Google](https://material.io/design)
- [Base Web by Uber](https://baseweb.design/)
- [Polaris by Shopify](https://polaris.shopify.com/)
- [Lightning Design System by Salesforce](https://www.lightningdesignsystem.com/)
- [Mailchimp Pattern Library](https://ux.mailchimp.com/patterns)
- [Microsoft Fluent Design System](https://www.microsoft.com/design/fluent/#/)
- [Carbon Design System by IBM](https://www.carbondesignsystem.com/)
- [Ant Design by Alibaba](https://ant.design/)

## CSS in JS

JavaScript를 사용해서 CSS를 작성하는 방식으로, 스타일 객체를 생성하여 각 요소의 style 속성에 바인딩한다. 대안으로는 CSS Module이 있다.

### "대규모 어플리케이션에서 CSS는 근본적인 결함이 있으며 JS 스타일링이 많은 문제를 해결한다"

1. Global Namespace: CSS는 전역 네임스페이스를 사용하기 때문에 이름이 충돌하는 경우가 있다
2. Dependencies: 스타일시트 간에 의존성이 존재하는 경우, 로드 순서에 따라 스타일이 달라질 수 있다
3. Dead Code Elimination: 사용하지 않는 스타일을 식별하고 제거하는 것이 어렵다
4. Minification: CSS는 압축되지 않기 때문에 불필요한 공백이나 주석이 포함되어 있다
5. Sharing Constants: CSS와 JS는 상수를 공유할 수 없다
6. None Deterministic Resolution: 비동기적으로 로딩되어 순서가 보장되지 않아 동일한 스타일 규칙이 다르게 렌더링 될 수도 있다
7. Breaking Isolation: CSS는 스타일 규칙이 전역 네임스페이스를 공유하기 때문에 스타일 규칙이 의도치 않게 덮어쓰여질 수 있다

CSS in JS는 조건부 또는 커스텀 스타일링을 쉽게 구현할 수 있고, 스타일을 컴포넌트와 함께 캡슐화할 수 있어서 재사용성을 높일 수 있다. 또한, 스타일을 동적으로 생성하기 때문에 런타임에 스타일을 변경할 수 있다는 장점이 있다.

- [2014, React: CSS in JS](https://blog.vjeux.com/2014/javascript/react-css-in-js-nationjs.html)

### "CSS in JS는 다섯 가지 관점에서 혁신의 가능성이 있다"

1. Scoped Style: 클래스 이름이 충돌하지 않도록 스타일을 캡슐화할 수 있다
2. Critical CSS: 서버사이드 렌더링 과정에서 페이지에 필요한 스타일만 쉽게 추출하여 로드할 수 있다
3. Smarter Optimizations: 스타일을 요소에 적용할 때, 필요한 CSS 코드만을 생성하는 기법이다
4. Package Management: CSS를 작고 재사용성 있는 패키지로 만들어 서로 조합하여 거대한 스타일 컬렉션을 구성한다면 생태계가 더 커질 것이다
5. None Browser Styling: 브라우저 이외의 환경에서도 일관적인 스타일을 적용할 수 있다(ex: RN의 StyleSheet API)

- [2017, "A Unified Styling Language"](https://blog.rhostem.com/posts/2017-06-24-unified-styling-language)

### "CSS in JS는 컴포넌트 기반의 웹 개발에 적합하다"

CSS는 웹이 페이지 기반으로 작성될 때를 기준으로 발전해왔지만, 현대 웹은 컴포넌트 기반으로 작성되고 있고 자연스럽게 컴포넌트의 상태에 따라 스타일이 변경되는 경우가 많다. CSS in JS는 컴포넌트 상태를 기반으로 조건부 스타일링을 쉽게 구현할 수 있게 해주고, 컴포넌트를 스타일과 함께 캡슐화하여 재사용성을 높일 수 있다.

- [2017, "All You Need To Know About CSS-in-JS"](https://d0gf00t.tistory.com/22)

### "CSS in JS는 장점과 단점이 갈린다"

#### 장점

1. Scoped Style: 스타일을 지역 변수로 지정하여 이름 충돌 문제를 방지한다
2. Colocation: 단일 컴포넌트에 관련된 모든 것을 같은 위치에 둘 수 있다
3. Work w/ JS Variable: JS 변수를 CSS에 공유하기 쉽다

#### 단점

1. Runtime Overhead: JS로 작성된 스타일을 일반 CSS로 변환하는 과정이 필요하다
2. Bundle Size: 사이트 사용자는 CSS-in-JS 라이브러리를 다운로드해야 한다
3. React DevTools: 스타일 컴포넌트에 파묻혀 디버깅 대상을 찾기 어렵다

- [2019, Colocation](https://kentcdodds.com/blog/colocation)
- [2021, "CSS-in-JS와 성능"](https://hyeonseok.com/blog/877)
- [2022, "Why We're Breaking Up with CSS-in-JS"](https://junghan92.medium.com/%EB%B2%88%EC%97%AD-%EC%9A%B0%EB%A6%AC%EA%B0%80-css-in-js%EC%99%80-%ED%97%A4%EC%96%B4%EC%A7%80%EB%8A%94-%EC%9D%B4%EC%9C%A0-a2e726d6ace6)
