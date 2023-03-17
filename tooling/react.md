# React

{% hint style="warning" %}
설명 편의상 이 문서에서는 웹브라우저 환경을 가정하고 글을 전개한다
{% endhint %}

React는 개발자가 작성한 컴포넌트 - 즉, UI 명세 - 를 입력받아 React Fiber 객체 트리를 만들고, 이를 사용하여 DOM에 필요한 변경 사항을 반영하는 프로그램이다.

React에서는 JSX 사용을 권장하여 개발자가 UI 명세를 쉽게 작성할 수 있도록 한다. JSX는 HTML과 유사한 형태라서 비교적 읽기 쉽기 때문에 컴포넌트를 중첩하여 복잡한 UI를 만들 때 유리하다는 점과 다른 로직과 UI를 쉽게 구분할 수 있는 장점이 있다. 직접 React.createElement() 함수를 사용하는 것과 비교했을 때 간결하고 가독성이 좋은 코드를 작성할 수 있다.

React에서는 브라우저에서 컴포넌트를 렌더링하기 위해 react-dom/client API를 사용한다. 이 API는 React Tree의 진입점을 알려주는 기능을 제공한다. createRoot는 브라우저 DOM 노드 안으로 React component를 표시하기 위해 root를 생성하는 기능이다. hydrateRoot는 react-dom/server에서 생성된 HTML을 기반으로 React component를 표시하기 위해 root를 생성하는 기능이다.

앞선 과정을 거쳐 출력된 Tree를 통해 React Fiber 엔진이 변경 사항을 감지하고 브라우저 DOM에 반영하는 것을 재조정(reconciliation)이라고 부른다.

React에서는 두가지 핵심 요소로 재조정 효율을 높인다. 첫째, 컴포넌트 유형이 다르면 이전 UI 상태와 이질적인 구조를 생성한다고 가정하여 기존 트리를 완전히 대체한다. 컴포넌트 유형이 같은 경우는 diff를 수행하여 필요한 부분만 변경한다. 둘째, 목록인 경우에는 키를 기준으로 변경 사항을 감지한다. 키가 달라지면 기존 트리를 대체하고, 키가 같으면 diff를 수행한다.

## 작업 흐름

1. 설계된 UI를 쪼개서 컴포넌트 계층으로 만든다
2. Props를 활용하여 정적 컴포넌트를 구현한다
3. 꼭 필요한 UI 상태를 찾아 구현한다
4. 상태를 담당하는 컴포넌트를 결정한다
5. 상태 변경 로직을 작성/전달한다

## 참고자료

- [React 공식 문서(Beta)](https://beta.reactjs.org/)
- [React 공식 문서(Legacy)](https://ko.reactjs.org/)
- [VDOM(Virtual DOM) and internals](https://ko.reactjs.org/docs/faq-internals.html)
- [Reconciliation](https://ko.reactjs.org/docs/reconciliation.html)
- [Optimization](https://ko.reactjs.org/docs/optimizing-performance.html)
- [Preserving and Resetting State](https://beta.reactjs.org/learn/preserving-and-resetting-state)
- [Reconciliation](https://ko.reactjs.org/docs/reconciliation.html)
- [React Strict Mode](https://ko.reactjs.org/docs/strict-mode.html)
- [createRoot](https://beta.reactjs.org/reference/react-dom/client/createRoot)
- [updating a root component](https://beta.reactjs.org/reference/react-dom/client/createRoot#updating-a-root-component)
- [when does react re-render?](https://velog.io/@surim014/react-rerender)
- [why react re-renders?](https://medium.com/@yujso66/%EB%B2%88%EC%97%AD-%EC%99%9C-%EB%A6%AC%EC%95%A1%ED%8A%B8%EC%97%90%EC%84%9C-%EB%A6%AC%EB%A0%8C%EB%8D%94%EB%A7%81%EC%9D%B4-%EB%B0%9C%EC%83%9D%ED%95%98%EB%8A%94%EA%B0%80-74dd239b0063)
- [answers a mostly complete guide to react rendering behavior](https://velog.io/@superlipbalm/blogged-answers-a-mostly-complete-guide-to-react-rendering-behavior)
- [react fiber architecture](https://github.com/acdlite/react-fiber-architecture)
