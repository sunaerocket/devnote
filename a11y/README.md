# Accessibility

모든 사용자가 웹 프로젝트를 사용할 수 있도록 책임감 있는 개발을 하기 위한 개념으로 인본주의적 사상을 기반으로 한다.

휠체어를 탄다는 이유로 건물에서 누군가를 배제하는 것이 잘못된 것처럼, 능력이나 환경에 관계없이 모든 사람에게 동등한 대우와 기회를 제공해야 한다는 생각이 기본 이념이다.

접근성이 모두에게 유익하다는 주장은 다양한 관점을 제시한다.

* [인지 접근성](https://developer.mozilla.org/en-US/docs/Web/Accessibility/Cognitive_accessibility) 개념을 적용한 설계는 자연스럽게 모두가 이해하고 사용하기 쉬운 설계로 이어진다

* 인지 장애와 신체적 장애를 함께 가진 경우가 많으므로 W3C가 제공하는 [웹 콘텐츠 접근성 지침](https://www.w3.org/WAI/standards-guidelines/wcag/)을 준수하면 모든 장애를 가진 사용자에게 동등한 서비스를 제공하여 더 많은 사용자를 확보할 수 있다

* 접근성을 보장하기 위한 `Semantic HTML` 개념은 SEO를 개선하여 유입을 늘리는 효과가 있다

* `Lean Semantic Markup`은 스크린 리더가 잘 읽을 수 있으며, 로딩 속도도 빠르기 때문에 모바일 기기나 느린 연결 속도를 가진 사용자에게도 유익하다

* 대중에게 윤리적인 이미지를 심어주어 브랜드 이미지를 향상시킨다

* 표적 이용자를 확장할 수 있다 - 장애인, 노인, 저시력자, 저음성자, 저지능자, 저해상도 기기 사용자, 저속 인터넷 사용자 등

* 접근성을 법으로 강제하는 국가에서 법을 준수하며 영업할 수 있다

접근성을 고려한 코드를 도입하기 까다로운 경우가 존재한다.

* 접근성 개념이 없던 고전적 웹사이트에 도입하는 경우

* 프로젝트 후반부를 지나서 접근성을 고려하는 경우

즉, 접근성은 처음부터 고려해야 제공하는 데 드는 비용을 최소화할 수 있다.

## 접근성 검토 항목

* 시각장애자를 위한 스크린리더의 크로스 브라우징 지원 여부

* 청각장애자를 위한 텍스트 대체 콘텐츠 지원 여부(동영상 -> 자막, 오디오 -> 대본 제공)

* 거동장애자를 위한 키보드 지원 여부(특히 사용자 입력 양식의 컨트롤 이동)

* 인지장애자를 위한 광범위한 지원 여부
  * 표준어를 적절하게 사용한 텍스트 콘텐츠 제공
  * 더 알기 쉬운 방식으로 콘텐츠 제공(텍스트를 음성으로 변환, 비디오)
  * 중요한 콘텐츠에 적절한 강조 처리
  * 불필요한 콘텐츠나 광고 같은 방해 요소 최소화
  * 일관성 있는 레이아웃과 페이지 네비게이션
  * 진행률을 표시하여 프로세스를 논리적인 단계로 분할
  * 쉬우면서도 보안성이 높은 인증 방식 제공
  * 사용자 입력 양식에 적절한 오류 메시지와 복구 기능 제공

* 웹사이트의 유해성 여부(e.g. 모션 기능 악용으로 편두통이나 간질 발작을 유발)

* 열악한 인터넷 환경에 노출된 사용자도 사용성이 보장되는지 여부

## Accessibility APIs

웹 브라우저는 운영 체제에서 제공하는 접근성 API를 기반으로 접근성 트리라는 정보 구조를 만들어 관리한다.

* Windows: MSAA/IAccessible, UIAExpress, IAccessible2
* macOS: NSAccessibility
* Linux: AT-SPI
* Android: Accessibility framework
* iOS: UIAccessibility

웹 어플리케이션의 HTML 요소가 제공하는 의미(Semantics)가 풍성하지 못한 경우, WAI-ARIA 스펙으로 기능을 보충한다

## 참고자료

* [MDN: Accessibility](https://developer.mozilla.org/en-US/docs/Learn/Accessibility)
* [MDN: WAI-ARIA Basics](https://developer.mozilla.org/en-US/docs/Learn/Accessibility/WAI-ARIA_basics)