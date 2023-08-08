# 렌더링 또는 재렌더링

사용자에게 UI를 제공하기 위한 절차를 의미한다. 브라우저는 다음 과정을 거쳐 리액트 애플리케이션을 UI로 표시한다.

1. **HTML Parsing & DOM Creation**: 브라우저가 가장 먼저 하는 일은 서버에서 받은 HTML 파일을 구문 분석하여 DOM을 생성하는 것이다.
2. **JavaScript Execution**: script 태그를 만나면 브라우저가 자바스크립트 코드를 실행하고, 이 단계에서 React 라이브러리가 실행된다.
3. **React Element Creation**: 자바스크립트 코드를 실행하는 과정에서, UI 컴포넌트 구조와 속성을 설명하는 객체인 `React Element`를 생성한다.
4. **Component Rendering**: `React Element`로 UI 컴포넌트 트리인 VDOM을 표현한다.
5. **Reconciliation & Diffing**: VDOM 변경 사항을 비교하여 최소한의 변경 사항만 DOM에 적용한다.
6. **DOM Update**: 변경 사항에 따라  DOM 요소를 추가, 갱신, 제거한다.
7. **Event Handling**: 사용자가 UI와 상호작용할 때, 리액트 컴포넌트에 정의된 이벤트 핸들러를 실행하여 상태를 갱신하거나 재렌더링을 발생시킨다.
8. **State Update & Re-Reconciliation**: 컴포넌트 상태가 변경되면, 다시 VDOM 변경 사항을 비교하여 최소한의 변경 사항만 DOM에 적용한다. 이 작업들은 비동기적으로 수행하여 불필요한 DOM 조작을 최소화한다.
