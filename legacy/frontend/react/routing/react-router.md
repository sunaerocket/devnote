# React Router

리액트 앱에서 URL에 매핑되는 유저 인터페이스를 관리하는 도구. 브라우저의 history stack 구독 및 관리 기능과 함께, URL과 경로 매칭 기능, 매칭된 경로의 컴포넌트를 렌더링하는 기능을 제공한다.

Next에서 사용하는 파일 시스템 기반 라우팅은 직관적이고 간단하지만, React Router는 라우팅을 컴포넌트 단위로 관리할 수 있어서 더 강력한 커스터마이징을 할 수 있다.

최근 데이터를 가져오기 위해 쓰는 React Query, SWR 같은 도구들은 적절하게 UI를 렌더링하기 위해 `pending`, `error` 같은 상태를 반환한다. React Router도 이런 기능들을 지원하기 위해 6.4 버전부터 새로운 Data API를 도입했다. 이번 업데이트로 `useNavigation` 훅을 사용하여 데이터 대기 상태, 낙관적 업데이트, 오류 상태 UI를 기존보다 편리하게 렌더링할 수 있다.

주의할 점은 React Router와 React Query/SWR 같은 데이터 관리 도구의 영역을 구분하는 것이다. React Router는 상태 전환이나 데이터 로딩 타이밍, 데이터 뮤테이션에 사용한다. 반면에 데이터 관리 도구는 데이터를 가져오고 갱신하고, 저장하고, 캐싱하는 실질적인 로직을 담당한다.

## 테스트 주의점

### 메모리 라우터를 사용한다

```tsx
describe('routes', () => {
  function renderRouter(path: string) {
    const router = createMemoryRouter(routes, { initialEntries: [path] });
    render(<RouterProvider router={router} />);
  }

  context('when the current path is “/”', () => {
    it('renders the home page', () => {
      renderRouter('/');
      screen.getByText(/Home/);
    });
  });

  context('when the current path is “/about”', () => {
    it('renders the about page', () => {
      renderRouter('/about');
      screen.getByText(/About/);
    });
  });
});
```

### fetch polyfill을 사용한다

```tsx
// setupTests.ts

import 'whatwg-fetch';
```

## 참고자료

- [React Router: A lightweight, fully-featured routing library for the React](https://reactrouter.com/en/main)
- [React Router/docs/concepts](https://reactrouter.com/en/main/start/concepts)
- [React Router/docs/data-libs](https://reactrouter.com/en/main/guides/data-libs)
- [React Router/docs/components: `<Routes>`](https://reactrouter.com/en/main/components/routes)
- [React Router/docs/components: `<Route>`](https://reactrouter.com/en/main/components/route)
