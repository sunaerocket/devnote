# React

{% hint style="warning" %}
설명 편의상 이 문서에서는 웹브라우저 환경을 가정하고 글을 전개한다
{% endhint %}

React는 개발자가 작성한 UI 명세인 컴포넌트를 입력받아 React Fiber 객체 트리를 만들고, 이를 사용하여 DOM에 필요한 변경 사항을 반영하는 프로그램이다.

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

## React Hooks

React Hooks는 React 16.8 버전부터 도입된 기능으로, 함수 컴포넌트에서도 상태 관리를 할 수 있게 해준다. 이전에는 클래스 컴포넌트를 사용했고, HoC 패턴으로 인한 Wrapper Hell 문제, 컴포넌트 비대화, 컨텍스트에 따라 this가 혼란스러워지는 등의 문제가 있었다. 이러한 문제를 해결하기 위해 React Hooks는 함수형 컴포넌트에서도 상태 관리를 할 수 있게 해주고, 컴포넌트를 재사용하기 쉽게 만들어준다.

도입기에는 상태를 가진 컴포넌트는 클래스 컴포넌트로 만들고, props만 사용하는 재사용이 쉬운 작은 컴포넌트는 함수 컴포넌트로 작성하는 것을 권장했다. 지금은 함수 컴포넌트를 주로 사용하며 복잡한 요소는 전부 Hook으로 격리하여 재사용한다. 결과적으로 컴포넌트의 코드량이 줄어들고 가독성이 좋아졌다.

- [React: Hooks](https://ko.reactjs.org/docs/hooks-intro.html)
- [React: Hooks at a Glance](https://ko.reactjs.org/docs/hooks-overview.html)
- [React: Hooks API Reference](https://ko.reactjs.org/docs/hooks-reference.html)
- [Presentational and Container Components, Dan Abramov](https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0)

### useState

React에서 관리하는 상태 값으로, 직접 값을 변경하지 않고 setState() 함수로 변경한다. 값이 변경되면 컴포넌트를 리렌더링 하기 위해 사용한다.

### useEffect

***Synchonizing with effects 정리 필요***

#### 실행 조건 설정하기

서버 데이터 가져오기처럼 React 외부의 값과 관련된 일을 처리할 때 사용한다. 기본적으로 렌더링 이후에 실행되며, 의존성 배열에 빈 배열을 전달하면 마운트 이후에 한 번만 실행된다. 의존성 배열에 특정 값이 있으면 해당 값이 변경될 때마다 실행된다. useEffect는 컴포넌트가 언마운트되기 전에 실행되는 clean-up 함수를 반환할 수 있다.

#### 개발 모드에서 Effect가 두 번 실행되는 문제

React Strict Mode 적용한 경우, 예상치 못한 side effect를 찾기 위해 effect 등을 두번씩 실행하지만 의도된 정상 동작이다.

- [React: Synchronizing with effects(beta)](https://react.dev/learn/synchronizing-with-effects)
- [React: You might not need an effect(beta)](https://react.dev/learn/you-might-not-need-an-effect)
- [React: Using the Effect Hook](https://ko.reactjs.org/docs/hooks-effect.html)
- [React: useEffect(beta)](https://react.dev/reference/react/useEffect)
- [Overreacted: A complete guide to useEffect](https://overreacted.io/ko/a-complete-guide-to-useeffect/)

### useRef

React 상태관리와 다르게 로직에서 값을 변경해도 렌더링에 영향을 주지 않는다. 보통 DOM에 직접 접근할 때 사용한다.
React는 ref.current 속성을 변경(mutate)해도 컴포넌트 리렌더링을 하지 않는다. 변경 시 렌더링에 영향을 주는 React state 값과는 구분해서 사용해야 한다. ref.current 속성은 컴포넌트가 마운트되고 언마운트되기 전까지 유지된다. 렌더링 도중에 초기화 이외의 write/read 작업을 권장 하지 않는다. 컴포넌트 동작을 예측할 수 없게 만들기 때문이다.

#### 사용 사례

***useRef 사용 사례 수집 필요***

- [React: useRef(beta)](https://react.dev/reference/react/useRef)
- [React: useRef](https://ko.reactjs.org/docs/hooks-reference.html#useref)

### Custom Hooks

특정 로직을 컴포넌트에서 재사용하기 위해 사용. 컴포넌트 내부의 코드량이 줄어들고 식별자만 읽어도 내용을 알 수 있어 가독성이 좋아진다. use로 시작하는 함수 이름을 camelCase로 작성한다.

- [React: Reusing Logic with Custom Hooks(beta)](https://react.dev/learn/reusing-logic-with-custom-hooks)
- [React: Custom Hooks](https://ko.reactjs.org/docs/hooks-custom.html)

### Hook 규칙

1. 최상위에서만 Hook을 호출해야 한다. 반복문, 조건문, 중첩 함수 내에서 Hook을 호출하면 안된다.
2. React 함수 컴포넌트 내에서만 Hook을 호출해야 한다. 일반 JavaScript 함수 내에서 Hook을 호출하면 안된다.

- [React: Hooks Rules](https://ko.reactjs.org/docs/hooks-rules.html)

### usehook-ts

다양한 커스텀 훅을 제공하고, 코드를 참고 할 수 있어 커스텀 훅을 만들기 전 참고하기 좋다.
다만 데이터 요청하기는 더 다양하고 강력한 기능을 지원하는 swr, react-query 등의 라이브러리를 사용하는 것을 권장한다.

- useInterval: setInterval을 직접 사용하는 것보다 유용하다.
- useEventListener: 모든 종류의 이벤트를 확인할 수 있고, 특히 dispatchEvent로 전달되는 커스텀 이벤트에 반응하기 좋다.
- useLocalStorage: localStorage, JSON 조합으로 객체 영속화. 이벤트를 통해(dispatchEvent + useEventListner) 다른 컴포넌트와 동기화하는 게 매우 중요한 특징.

- [usehooks-ts: Documetation](https://usehooks-ts.com/)
- [SWR: 데이터 가져오기를 위한 React Hooks](https://swr.vercel.app/ko)
- [React Query: Powerful asynchronous state management for TS/JS, React, Solid, Vue and Svelte](https://tanstack.com/query/latest)
- [Youtube: React에서의 타이머 part 1 : setInterval 말고 이것!](https://www.youtube.com/watch?v=2tUdyY5uBSw)

## React Strict Mode

개발 모드에서만 작동하는 컴포넌트로, 애플리케이션 내의 잠재적인 문제를 식별하는 데 도움을 준다. StrictMode는 다음과 같은 기능을 제공한다.

useEffect, useRef 사용 시, 예상치 못한 side effect를 찾기 위해 effect 등을 두번씩 실행한다. 이는 의도된 정상 동작이다.

- [React: detecting-unexpected-side-effects](https://ko.reactjs.org/docs/strict-mode.html#detecting-unexpected-side-effects)

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
