# Playwright

> Playwright enables reliable end-to-end testing for modern web apps.

최신 웹 앱을 안정적으로 E2E 테스트할 수 있도록 도와주는 테스팅 프레임워크.

## 테스팅 철학

### 사용자가 볼 수 있는 동작을 테스트한다(Test user-visible behavior)

테스트는 어플리케이션 코드가 최종 사용자에게 제대로 작동하는지 확인하는 과정이다. 따라서 구현세부사항(함수 이름, 배열 여부, 특정 요소의 CSS 클래스 등)에 의존하지 않는 테스트를 작성해야 한다. 최종 사용자는 페이지에 렌더링된 내용을 보거나 상호 작용하므로 테스트는 일반적으로 동일한 렌더링된 출력만 보거나 상호 작용해야 한다.

### 테스트를 최대한 격리한다(Make tests as isolated as possible)

재현성이 높고 디버깅이 쉬우며 연쇄적인 테스트 실패를 방지할 수 있어야 좋은 테스트다. 따라서 각 테스트는 다른 테스트와 완전히 격리되어야 하며 자체 로컬 저장소, 세션 저장소, 데이터, 쿠키 등을 사용하여 독립적으로 실행되어야 한다.

테스트마다 반복되는 로직을 처리하기 위해 before / after 훅을 사용한다. 테스트 파일 내에 비포 훅을 추가하여 특정 URL로 이동하거나 앱의 일부에 로그인하는 등 각 테스트 전에 테스트의 일부를 실행한다. 이렇게 하면 어떤 테스트도 다른 테스트에 의존하지 않으므로 테스트가 격리된다. 그러나 간단한 테스트의 경우, 중복을 유지하는 것이 가독성/유지보수 측면에서 더 나을 수 있다.

전역 설정으로 테스트에서 로그인 상태를 재사용하는 방법도 있다. 이렇게 하면 한 번만 로그인한 다음 모든 테스트에서 로그인 단계를 건너뛸 수 있다.

### 테스트 길이는 늘리고 횟수는 줄인다(Write fewer tests but longer tests)

엔드 투 엔드 테스트는 완전한 앱 흐름을 테스트할 수 있도록 테스트에 여러 개의 액션과 어설션으로 구성하는 것이 좋다. 어설션을 개별 테스트 블록으로 분리하는 것은 테스트 실행 속도만 느리게 하므로 피해야 한다.

기본적으로 테스트가 실패하면 테스트를 중단하지만, soft assertions 기능을 활용하여 테스트가 실패해도 남은 테스트를 계속 실행할 수 있다.

### 서드 파티 종속성은 테스트하지 않는다(Avoid testing third-party dependencies)

내가 제어하는 것만 테스트한다. 통제할 수 없는 외부 사이트나 타사 서버로 연결되는 링크는 테스트하지 않는다. 이는 시간이 오래 걸리고 테스트 속도가 느려질 뿐만 아니라 링크하는 페이지의 콘텐츠를 제어할 수 없거나 쿠키 배너, 오버레이 페이지 등 테스트 실패의 원인이 될 수 있다.

### 데이터베이스를 사용하여 테스트한다(Testing with a database)

데이터베이스로 작업하는 경우 데이터를 제어할 수 있는지 확인한다. 스테이징 환경에서 테스트할 때 변경사항을 확인한다. 시각적 회귀 테스트의 경우 운영 체제와 브라우저 버전이 동일한지 확인한다.

## vs. cypress

Playwright는 크로스 브라우저 테스트, 프로그래밍 언어, 자동화 기능 측면에서 더 넓은 지원범위와 다양한 기능을 제공한다. Cypress는 간단하고 직관적인 API, 강력한 디버깅 기능, 커뮤니티 성숙도 측면에서 우위가 있다. 따라서 복잡한 시나리오, 다양한 브라우저를 지원해야하는 상황에서는 Playwright를 사용하고, 상대적으로 간단한 시나리오, 단일 브라우저를 지원해야하는 상황에서는 Cypress를 사용하는 것이 적절하다.

### 브라우저 지원범위: Playwright 우세

- Playwright: Chromium, Firefox, WebKit
- Cypress: Chromium, Firefox

Playwright는 크로스 브라우징 테스트 기능이 내장되어 있지만, Cypress는 chromium 기반 브라우저만 테스트 가능하다.

### 언어/프레임워크 지원범위: Playwright 우세

- Playwright: JS, TS, Python, C#
- Cypress: focus on JS, TS

Playwright는 다양한 언어와 프레임워크를 지원하는 반면, Cypress는 JS, TS만 지원한다.

### 테스트 실행 방식: Playwright 우세

- Playwright: 별도 프로세스
- Cypress: 동일 프로세스

Playwright는 테스트 러너와 별도 프로세스로 테스트를 진행하기 때문에 테스트 러너를 통해 테스트를 병렬로 실행할 수 있다. 실행하는 테스트의 양이 많아질수록, Playwright의 테스트 실행 방식이 유리하다.

### 디버깅: Cypress 우세

Cypress는 시간 이동, 스냅샷, 장애 발생 시 자동 스크린샷 등의 기능을 통해 강력한 대화형 디버깅 환경을 제공한다. Playwright도 디버깅 기능을 제공하지만 Cypress가 더 편리하다.

### 브라우저 자동화 기능 지원 범위: Playwright 우세

Playwright는 파일 업로드, 다운로드, 디바이스 에뮬레이션 같은 복잡한 시나리오를 지원하며 웹 컴포넌트 및 Shadow DOM 같은 최신 웹 기술을 지원한다. 반면 Cypress는 일반적인 테스트 작업을 위한 간단하고 직관적인 API를 제공하는 데 중점을 두며 비교적 일반적이고 간략한 테스트에 적합하다.

### 커뮤니티/생태계: Cypress 우세

Cypress는 2014년에 출시되었고, Playwright는 2019년에 출시되었다. Cypress는 더 오래된 프로젝트이기 때문에 상대적으로 커뮤니티와 생태계가 활발하다.

## 사용사례

### Use locators

E2E 테스트를 작성하기 위한 웹 페이지에서 요소를 찾을 때, locator를 사용한다.

```js
page.getByRole('button', { name: 'submit' })
```

### Use chaining and filtering

```js
// 로케이터를 활용하여 페이지의 특정 부분으로 검색 범위를 좁힐 수 있다.
const product = page.getByRole('listitem').filter({ hasText: 'Product 2' });
```

```js
// 텍스트나 다른 로케이터를 기준으로 요소를 특정할 수 있다.
await page
    .getByRole('listitem')
    .filter({ hasText: 'Product 2' })
    .getByRole('button', { name: 'Add to cart' })
    .click();
```

```js
// 디자인이 변하면 같이 변할 가능성이 높은 CSS 클래스보다는 locator를 사용하는 것이 좋다.
👎 page.locator('button.buttonIcon.episode-actions-later')

👍 page.getByRole('button', { name: 'submit' })
```

## 참고자료

-[Playwrite: Reliable end-to-end testing for modern web apps](https://playwright.dev/)
-[GitHub/playwright: Framework for Web Testing and Automation](https://github.com/microsoft/playwright)
-[Playwrite/api: page](https://playwright.dev/docs/api/class-page)
-[Playwrite/api: selectors](https://playwright.dev/docs/api/class-selectors)
-[Playwrite/guides: best practices](https://playwright.dev/docs/best-practices)
-[Playwrite/guides: assertions](https://playwright.dev/docs/test-assertions)
-[Playwrite/guides: debugging](https://playwright.dev/docs/debug)
-[Playwrite/integrations: ci](https://playwright.dev/docs/ci)
