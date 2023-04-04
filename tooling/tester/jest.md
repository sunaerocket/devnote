# Jest

테스트를 작성하고 실행하기 위한 도구.

## React Testing Library

사용자 입장에서 리액트 컴포넌트를 테스트할 수 있는 기능을 제공하는 도구.

기존에 테스트러너가 동작하는 node 환경에서 DOM 테스트를 할 수 있도록 도와주는 DOM Testing Library가 있었고, 이를 확장하여 React 컴포넌트를 테스트할 수 있도록 만들어진 도구다.

- [GitHub/React Testing Library](https://github.com/testing-library/react-testing-library)
- [GitHub/jest-dom](https://github.com/testing-library/jest-dom)

## 사용 사례

### 모듈 모킹하기

외부 의존성이 큰 코드를 테스트하기 위해 가짜를 만든다.

```javascript
import { render, screen } from '@testing-library/react';

import App from './App';

// jest.mock을 활용하여 가짜 모듈 만들기
jest.mock('./hooks/useFetchProducts', () => () => [
  {
    category: 'Fruits', price: '$1', stocked: true, name: 'Apple',
  },
]);

test('App', () => {
  render(<App />);

  screen.getByText('Apple');
});
```

### 타입스크립트 사용을 위한 설정

```javascript
// jest.config.js

module.exports = {
  testEnvironment: 'jsdom',
  setupFilesAfterEnv: [
    '@testing-library/jest-dom/extend-expect',
  ],
  transform: {
    '^.+\\.(t|j)sx?$': ['@swc/jest', {
      jsc: {
        parser: {
          syntax: 'typescript',	
          jsx: true,
          decorators: true,
        },
        transform: {	
          react: {
            runtime: 'automatic',
          },
        },
      },
    }],
  },
};
```

- [Jest: Delightful JavaScript Testing Framework with a focus on simplicity](https://jestjs.io/)