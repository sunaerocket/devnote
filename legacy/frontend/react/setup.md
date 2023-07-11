# React 프로젝트 시작하기

React 어플리케이션을 개발하기 위한 준비물을 설치/설정하는 과정을 나열한다.

1. 정적분석 도구 - `typescript`, `eslint` - 를 설정하여 작성할 코드의 일관성을 유지하고 오류를 방지한다.
2. 유닛 테스트 도구 - `jest`, `react testing library` - 를 설정하여 코드 품질 개선과 원하는 경우, TDD 적용이 가능하도록 구성한다.
3. 리액트 + 빌드 도구 - `parcel`, `vite`, `webpack` , etc. - 조합을 선택하여 모듈 번들링을 통해 앱을 빌드한다.
4. TODO: E2E 테스트 도구 - `codeceptjs`, `cypress`, etc. - 를 선택하여 사용자 입장에서 앱의 인터페이스를 정의하고 테스트한다.

## 패키지 생성

```bash
npm init -y
```

명령어 실행 후, `package.json` 파일을 적절하게 수정한다.

## TypeScript 설정

앞으로 작성할 코드를 정적 분석하기 위해 먼저 설치한다.

```bash
npm i -D typescript
```

`tsconfig.json` 파일을 생성한다.

```bash
npx tsc --init
```

`tsconfig.json` 파일을 적절하게 수정한다.

```plain text
"jsx": "react-jsx",
```

## ESLint 설정

앞으로 작성할 코드 스타일의 일관성을 유지하기 위해 먼저 설치한다.

```bash
npm i -D eslint
```

`.eslintrc.js` 파일을 생성한다.

```bash
npx eslint --init
```

### [선택] airbnb 스타일 적용하기

airbnb, google 스타일은 [TypeScript를 공식 지원하지 않는다는 이유](https://github.com/eslint/create-config/pull/33)로 초기화 옵션에서 제거되었다.

따라서 초기화 옵션에서 선택한 xo 의존성을 제거하고 비공식 airbnb-typescript 스타일을 설치하는 과정이 필요하다.

```bash
npm uninstall eslint-config-xo \
    eslint-config-xo-typescript

npm i -D eslint-config-airbnb-typescript \
    @typescript-eslint/eslint-plugin \
    @typescript-eslint/parser \
    eslint-plugin-import \
    eslint-plugin-react \
    eslint-plugin-react-hooks \
    eslint-plugin-jsx-a11y
```

`.eslintrc.js` 파일을 적절하게 수정한다.

```javascript
module.exports = {
  env: {
    browser: true,
    es2021: true,
    jest: true,
  },
  extends: [
    'airbnb',
    'airbnb-typescript',
    'plugin:@typescript-eslint/recommended',
    'plugin:react/recommended',
    'plugin:react/jsx-runtime',
  ],
  parser: '@typescript-eslint/parser',
  parserOptions: {
    ecmaVersion: 'latest',
    sourceType: 'module',
    project: './tsconfig.json',
  },
  plugins: [
    'react',
    'react-hooks',
    '@typescript-eslint',
  ],
  settings: {
    'import/resolver': {
      node: {
        extensions: ['.js', '.jsx', '.ts', '.tsx'],
      },
    },
  },
  rules: {
    indent: ['error', 2],
    'no-trailing-spaces': 'error',
    curly: 'error',
    'brace-style': 'error',
    'no-multi-spaces': 'error',
    'space-infix-ops': 'error',
    'space-unary-ops': 'error',
    'no-whitespace-before-property': 'error',
    'func-call-spacing': 'error',
    'space-before-blocks': 'error',
    'keyword-spacing': ['error', { before: true, after: true }],
    'comma-spacing': ['error', { before: false, after: true }],
    'comma-style': ['error', 'last'],
    'comma-dangle': ['error', 'always-multiline'],
    'space-in-parens': ['error', 'never'],
    'block-spacing': 'error',
    'array-bracket-spacing': ['error', 'never'],
    'object-curly-spacing': ['error', 'always'],
    'key-spacing': ['error', { mode: 'strict' }],
    'arrow-spacing': ['error', { before: true, after: true }],
    'import/no-extraneous-dependencies': ['error', {
      devDependencies: [
        '**/*.test.js',
        '**/*.test.jsx',
        '**/*.test.ts',
        '**/*.test.tsx',
      ],
    }],
    'import/extensions': ['error', 'ignorePackages', {
      js: 'never',
      jsx: 'never',
      ts: 'never',
      tsx: 'never',
    }],
    'react/jsx-filename-extension': [2, {
      extensions: ['.js', '.jsx', '.ts', '.tsx'],
    }],
    'jsx-a11y/label-has-associated-control': ['error', { assert: 'either' }],
  },
};
```

### VS Code 설정 파일 추가

`.vscode` 디렉토리 생성

```bash
mkdir .vscode
```

`.vscode/settings.json` 파일 생성

```bash
touch .vscode/settings.json
```

`.vscode/settings.json` 파일에 설정 추가

```json
{
    "editor.rulers": [
        80
    ],
    "editor.codeActionsOnSave": {
        "source.fixAll.eslint": true
    },
    "trailing-spaces.trimOnSave": true
}
```

## Jest 설정

유닛 테스트 도구로 Jest를 사용하기 위해 먼저 설치한다. SWC를 사용하면 테스트 수행 속도가 더 빨라지기 때문에 지원 패키지를 같이 설치한다.

```bash
npm i -D jest @types/jest @swc/core @swc/jest
```

`jest.config.js` 파일을 생성한다.

```javascript
module.exports = {
  transform: {
    '^.+\\.(t|j)sx?$': ['@swc/jest', {
      jsc: {
        parser: {
          syntax: 'typescript',
        },
      },
    }],
  },
};
```

## React, Parcel 설정

React 앱을 만들기 위한 패키지와 번들러를 설치한다.

React 의존성 설치

```bash
npm i react react-dom
```

```bash
npm i -D @types/react @types/react-dom
```

Parcel 설치

```bash
npm i -D parcel
```

`package.json` 파일에 `source` 항목 추가

```plain text
"source": "index.html"
```

index.html 파일 생성

```bash
touch index.html
```

```html
<!DOCTYPE html>
<html lang="ko">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
  </head>
  <body>
    <div id="root"></div>
    <script type="module" src="./src/main.tsx"></script>
  </body>
</html>
```

`src` 디렉토리 생성

```bash
mkdir src
```

`src/main.tsx` 파일 생성

```bash
touch src/main.tsx
```

`src/main.tsx` 파일 작성

```typescript jsx
import ReactDOM from 'react-dom/client';

import App from './App';

function main() {
  const container = document.getElementById('root');
  if (!container) {
    return;
  }

  const root = ReactDOM.createRoot(container);
  root.render(<App />);
}

main();
```

`src/App.tsx` 파일 생성

```bash
touch src/App.tsx
```

```typescript jsx
export default function App() {
  return (
    <p>Hello, world!</p>
  );
}
```

### React Testing Library 설정

더 직관적인 코드를 작성하기 위해 React Testing Library를 설치한다.

```bash
npm i -D @testing-library/react jest-environment-jsdom
```

`jest.config.js` 파일에 설정 추가

```javascript
module.exports = {
  testEnvironment: 'jsdom',
  transform: {
    '^.+\\.(t|j)sx?$': ['@swc/jest', {
      jsc: {
        parser: {
          syntax: 'typescript',
          jsx: true,
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

src/App.test.tsx 파일 생성

```bash
touch src/App.test.tsx
```

```typescript jsx
import { render, screen } from '@testing-library/react';

import App from './App';

test('App', () => {
  render(<App />);

  screen.getByText(/Hello, world/);
});
```
