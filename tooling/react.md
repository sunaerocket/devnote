# React

## 핵심 개념

### JSX

자바스크립트로 UI를 작성할 때, XML 형태로 작성하여 익숙한 형태로 구조를 파악하기 쉽다. JSX 구문은 트랜스파일러가 React.createElement() 기능을 사용하는 JS 코드로 변환한다. 이를 중첩하여 React Element 기반의 fibers 객체 트리를 만들고, React는 실제 DOM과 비교하여 해야할 작업을 선정한다.

VDOM을 사용하는 이유는 선언형 UI를 가능하게 하여 코드 가독성을 개선하여 유지보수에 도움이 되기 때문이다. DOM 조작과 비교했을 때, 성능 상의 이점이 있다고 보기에는 애매하다.

- [VDOM(Virtual DOM) and internals](https://ko.reactjs.org/docs/faq-internals.html)
- [Reconciliation](https://ko.reactjs.org/docs/reconciliation.html)
- [Optimization](https://ko.reactjs.org/docs/optimizing-performance.html)

### Strict Mode

개발 모드에서 안티 패턴을 검출할 수 있는 기능이다.

- [React Strict Mode](https://ko.reactjs.org/docs/strict-mode.html)

### 멘탈모델

#### [리액트로 UI를 만드는 방법](https://beta.reactjs.org/learn/thinking-in-react)

1. 설계된 UI를 쪼개서 컴포넌트 계층으로 만든다
2. Props를 활용하여 정적 컴포넌트를 구현한다
3. 꼭 필요한 UI 상태를 찾아 구현한다
4. 상태를 담당하는 컴포넌트를 결정한다
5. 상태 변경 로직을 작성/전달한다

- [React as a UI runtime: 만든 사람이 설명하는 리액트 멘탈 모델](https://overreacted.io/ko/react-as-a-ui-runtime/)

### 렌더링과 리렌더링

- [createRoot](https://beta.reactjs.org/reference/react-dom/client/createRoot)
- [updating a root component](https://beta.reactjs.org/reference/react-dom/client/createRoot#updating-a-root-component)
- [when does react re-render?](https://velog.io/@surim014/react-rerender)
- [why react re-renders?](https://medium.com/@yujso66/%EB%B2%88%EC%97%AD-%EC%99%9C-%EB%A6%AC%EC%95%A1%ED%8A%B8%EC%97%90%EC%84%9C-%EB%A6%AC%EB%A0%8C%EB%8D%94%EB%A7%81%EC%9D%B4-%EB%B0%9C%EC%83%9D%ED%95%98%EB%8A%94%EA%B0%80-74dd239b0063)
- [answers a mostly complete guide to react rendering behavior](https://velog.io/@superlipbalm/blogged-answers-a-mostly-complete-guide-to-react-rendering-behavior)

## 참고자료

- [React 공식 문서(Beta)](https://beta.reactjs.org/)
- [React 공식 문서(Legacy)](https://ko.reactjs.org/)
