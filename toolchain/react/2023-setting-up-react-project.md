# 2023 리액트 개발 환경 세팅하기

개발 환경을 구성하는 것은 꾸준한 노력이 필요하다. 개발 생태계가 진화해나가는 방향을 파악하고 필요한 부분을 도입하는 판단이 필요하기 때문이다.

## 0: 개발 환경 개요

* [fnm: JavaScript 개발 환경 관리](#01-fnmfast-node-manager)
* [TypeScript: 타입 시스템 강화](#02-typescript)
* [ESLint: 코드 스타일 및 품질 관리](#03-eslint)
* [React: 컴포넌트 기반 웹 FE 작성](#04-react)
* [Jest: 유닛 테스트 실행](#05-jest)
* [Parcel: 빌드 도구](#06-parcel)

### [0.1: fnm(fast node manager)](https://github.com/Schniz/fnm)

웹 FE 개발은 JavaScript를 중심으로 구성한다. 다양한 런타임 환경이 있지만, Node.js를 기반으로 하는 개발 환경을 구성하는 것이 일반적이다. fnm은 필요에 따라 node.js 버전을 쉽고 빠르게 변경할 수 있도록 도와준다.

OS나 Shell에 따라 설치 방법이 달라지기 때문에 [공식 문서](https://github.com/Schniz/fnm)를 꼼꼼하게 읽어보고 사용법은 [usage](https://github.com/Schniz/fnm/blob/master/docs/commands.md) 문서를 참고한다.

### [0.2: TypeScript](https://www.typescriptlang.org/)

JavaScript를 확장하여 타입 시스템을 강화한 언어로, 트랜스파일링을 통해 JavaScript로 변환된다. TypeScript는 앱의 복잡도가 증가할수록 높아지는 타입 오류의 위험을 줄여준다. 오류도 상대적으로 구체적인 메시지를 제공하므로 디버깅이 쉽다.

실질적으로 텍스트 에디터에서 제공하는 실시간 오류 검사와 자동 완성 기능으로 개발 생산성을 향상시킨다.

#### TypeScript 참고자료

* [TypeScript for JavaScript Programmers](https://www.typescriptlang.org/ko/docs/handbook/typescript-in-5-minutes.html)
  * [타입 정의하기](https://www.typescriptlang.org/ko/docs/handbook/typescript-in-5-minutes.html#%ED%83%80%EC%9E%85-%EC%A0%95%EC%9D%98%ED%95%98%EA%B8%B0-defining-types)
  * [타입 별칭과 인터페이스의 차이](https://www.typescriptlang.org/ko/docs/handbook/2/everyday-types.html#%ED%83%80%EC%9E%85-%EB%B3%84%EC%B9%AD%EA%B3%BC-%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4%EC%9D%98-%EC%B0%A8%EC%9D%B4%EC%A0%90)
* [Generics](https://www.typescriptlang.org/docs/handbook/2/generics.html)
* [Utility Types](https://www.typescriptlang.org/docs/handbook/utility-types.html)
* [(번역)더 좋은 타입스크립트 프로그래머로 만드는 11가지 팁](https://velog.io/@lky5697/11-tips-that-help-you-become-a-better-typescript-programmer)

### [0.3: ESLint](https://eslint.org/)

코드 작성에 도움이 되는 가이드를 제공한다. 코드 스타일을 정의하는 [규칙](https://eslint.org/docs/latest/rules/)을 기반으로 검사를 수행하고, 다양한 [플러그인](https://eslint.org/docs/latest/use/configure/plugins)을 통해 규칙을 확장할 수 있다.

### [0.4: React](https://reactjs.org/)

react는 UI를 만들기 위한 라이브러리로, 웹앱으로 빌드하기 위해서 react-dom 패키지를 같이 사용한다. 대부분의 렌더링 작업을 JSX를 통해 추상화하기 때문에 개발자가 DOM 조작보다는 UI를 구성하는 컴포넌트 작성에 집중할 수 있다.

#### React 참고자료

* [Thinking in React](https://react.dev/learn/thinking-in-react)
* [UI 런타임으로서의 React](https://overreacted.io/ko/react-as-a-ui-runtime/)
* [createRoot](https://react.dev/reference/react-dom/client/createRoot)
* [Updating a root component](https://react.dev/reference/react-dom/client/createRoot#updating-a-root-component)
* [(번역) React는 컴포넌트를 언제 다시 리렌더링 할까요?](https://velog.io/@surim014/react-rerender)
* [[번역] 왜 리액트에서 리렌더링이 발생하는가](https://medium.com/@yujso66/%EB%B2%88%EC%97%AD-%EC%99%9C-%EB%A6%AC%EC%95%A1%ED%8A%B8%EC%97%90%EC%84%9C-%EB%A6%AC%EB%A0%8C%EB%8D%94%EB%A7%81%EC%9D%B4-%EB%B0%9C%EC%83%9D%ED%95%98%EB%8A%94%EA%B0%80-74dd239b0063)
* [(번역) React 렌더링 동작에 대한 (거의) 완벽한 가이드](https://velog.io/@superlipbalm/blogged-answers-a-mostly-complete-guide-to-react-rendering-behavior)

### [0.5 Jest](https://jestjs.io/)

코드 품질을 유지하기 위한 유닛 테스트를 실행하기 위한 라이브러리로, 테스트 작성에 도움이 되는 기능을 제공하는 react testing library와 함께 사용하는 것을 권장한다. @swc/jest 적용으로 성능을 크게 향상시킬 수 있다.

최근 vitest 등장으로 경쟁 구도를 형성했다. 설정이 간편하다는 점에서 vitest를 사용하는 것도 좋은 방법이다.

#### Testing 참고자료

* [RSpec 모범 사례 모음(참고용)](https://www.betterspecs.org/)
* [프론트엔드도 테스트를 해야 하나요?](https://www.youtube.com/watch?v=-kUmsKRmOnA)
* [Mocking 때문에 테스트 작성이 어렵나요](https://www.youtube.com/watch?v=RoQtNLl-Wko)

### [0.6: Parcel](https://parceljs.org/)

웹 앱을 구동하기 위한 js 파일을 최적화하는 작업 담당하는 도구로 설정이 간편하고 빠른 속도를 제공할수록 좋다. parcel은 소규모 프로젝트에 적합하다.

기존에는 webpack이 시장을 장악했었지만 최근에는 vite, turbopack(next.js)이 인기를 얻고있다.

Parcel 사용할 때 권장하는 설정은 두가지다.

package.json 파일에 다음과 같이 source를 지정한다.

```json
"source": "./index.html",
```

[parcel-reporter-static-files-copy](https://github.com/elwin013/parcel-reporter-static-files-copy) 패키지를 설치하고 .parcelrc 파일을 작성한다.

```json
{
  "extends": ["@parcel/config-default"],
  "reporters":  ["...", "parcel-reporter-static-files-copy"]
}
```

빌드 명령어와 정적 서버 실행은 다음과 같다.

[servor?](https://github.com/lukejacksonn/servor)

```bash
npx parcel build

npx servor ./dist
```

## 1: 레시피

### 1.0: fnm 및 node.js 설치

1.0.1: 자동 설치 스크립트를 실행

```bash
curl -fsSL https://fnm.vercel.app/install | bash
```

1.0.2: 쉘 셋업하기

지원범위: bash, zsh, fish, powershell

```bash
fnm completions --shell <SHELL>
```

1.0.3: 쉘 프로파일 추가

[지원하는 쉘의 명령어](https://github.com/Schniz/fnm#shell-setup) 찾아서 실행

1.0.4: node.js 설치

```bash
fnm install --lts
fnm use lts-latest
fnm default $(fnm current)
```

### 1.1: 프로젝트 폴더 생성

```bash
mkdir my-app

cd my-app
```

### 1.2: npm 패키지 초기화

```bash
npm init -y
```

### 1.3: .gitignore 파일 작성

최소한 `node_modules` 폴더 커밋을 방지하되, 필요한 파일이나 경로를 추가한다.

[gitignore.io](https://www.toptal.com/developers/gitignore/) 서비스를 활용하는 것도 추천한다.

```bash
touch .gitignore
```

```gitignore
### .gitignore 예시 ###

# dependencies
/node_modules

# build output
/build

# environment variables
/.env.local
/.env.development.local
/.env.test.local
/.env.production.local

# misc
.DS_Store
*.log
npm-debug.log*
yarn-debug.log*
yarn-error.log*
```

### 1.4: TypeScript 설정

```bash
npm i -D typescript

npx tsc --init
```

상황에 맞게 설정하는 것을 권장하며, 최소한 [jsx 속성](https://www.typescriptlang.org/docs/handbook/jsx.html#basic-usage)은 필수적으로 활성화한다.

```json
{
  "compilerOptions": {
    "jsx": "react-jsx",
  }
}
```

### 1.5: ESLint 설정

```bash
npm i -D eslint

npx eslint --init
```

아직 설치하지 않았지만 미리 `jest:true` 설정을 잡아두면 편하다.

```javascript
// .eslintrc.js 예시

env: {
  ...
  jest: true,
},
```

eslintignore 파일을 작성하고 필요한 경로를 추가한다.

```plaintext
### .eslintignore 예시 ###

/node_modules/
/dist/
/.parcel-cache/
```

### 1.6: React 설치

```bash
npm i react react-dom

npm i -D @types/react @types/react-dom
```

### 1.7: 테스트 도구 설치

```bash
npm i -D jest @types/jest @swc/core @swc/jest \
    jest-environment-jsdom \
    @testing-library/react @testing-library/jest-dom
```

더 빠른 테스트 실행을 위해 swc 설정을 추가한다.

```js
// jest.config.js 예시

module.exports = {
  testEnvironment: 'jsdom',
  setupFilesAfterEnv: [
    '@testing-library/jest-dom/extend-expect',
    './jest.setup',
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
  testPathIgnorePatterns: [
    '<rootDir>/node_modules/',
    '<rootDir>/dist/',
  ],
};
```

### 1.8: Parcel 설치

```bash
npm i -D parcel
```

### 1.9: 패키지 스크립트 수정

package.json 예시 파일을 참고하여 웹프로젝트의 엔트리 파일을 정의하기 위한 `source` 속성을 추가하고, 필요한 스크립트를 추가한다.

```json
{
  "name": "react",
  "version": "1.0.0",
  "description": "",
  "source": "./index.html",
  "scripts": {
    "start": "parcel --port 8080",
    "build": "parcel build",
    "check": "tsc --noEmit",
    "lint": "eslint --fix --ext .js,.jsx,.ts,.tsx .",
    "test": "jest",
    "coverage": "jest --coverage --coverage-reporters html",
    "watch:test": "jest --watchAll"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "@swc/core": "^1.2.218",
    "@swc/jest": "^0.2.22",
    "@testing-library/jest-dom": "^5.16.4",
    "@testing-library/react": "^13.3.0",
    "@types/jest": "^28.1.6",
    "@types/react": "^18.0.15",
    "@types/react-dom": "^18.0.6",
    "@typescript-eslint/eslint-plugin": "^5.31.0",
    "@typescript-eslint/parser": "^5.31.0",
    "eslint": "^8.20.0",
    "eslint-config-airbnb": "^19.0.4",
    "eslint-plugin-import": "^2.26.0",
    "eslint-plugin-jsx-a11y": "^6.6.1",
    "eslint-plugin-react": "^7.30.1",
    "eslint-plugin-react-hooks": "^4.6.0",
    "jest": "^28.1.3",
    "jest-environment-jsdom": "^28.1.3",
    "parcel": "^2.8.0",
    "process": "^0.11.10",
    "typescript": "^4.7.4"
  },
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "reflect-metadata": "^0.1.13",
    "tsyringe": "^4.7.0",
    "usestore-ts": "^0.0.3"
  }
}
```

### 1.10: 기본 코드 작성

* `index.html`
* `src/main.tsx`
* `src/App.tsx`
* `src/App.test.tsx`
* `src/components/Greeting.test.tsx`
* `src/components/Greeting.tsx`

### Appendix: VSCode 설정

* JS/TS 파일을 저장할 때마다 ESLint 실행 후 문제점을 고치도록 수정하기

```json
{
    "editor.codeActionsOnSave": {
        "source.fixAll.eslint": true
    }
}
```

* 설정 예시

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
