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
