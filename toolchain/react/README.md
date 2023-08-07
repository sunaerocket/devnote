# React Ecosystem

리액트는 UI를 만들기위한 라이브러리지만, 웹사이트를 만들기 위한 생태계를 구축하고 있어 웹FE 개발 도구를 선택하는데 매우 많은 영향을 준다. 경쟁 제품인 vue, angular, svelte 역시 독자적인 생태계로 발전하고 있다.

## Build tools

- vite
- next.js(turbopack)
- webpack

## Routing

- React Router
- Tanstack Router

## Client State Management

앱이 성장할수록, 컴포넌트 사이를 흐르는 데이터를 정돈하고 제어하는 것이 복잡해지며 그 작업을 효과적으로 수행하기 위해 상태 관리 도구

- Redux Toolkit
- Zustand

## Server State Management

서버와 통신하여 가져오는 상태를 전문적으로 관리하는 도구

- Tanstack Query
- RTK Query
- Apollo Client w/ GraphQL API

## Form Handling

사용자 입력 양식을 처리하는 것은 지루하고 오류가 발생하기 쉬운 작업이지만, 이를 효과적으로 처리하기 위한 도구가 있다

- React Hook Form
- Formik

## Testing

코드 품질을 유지하고, 버그를 최소화하며, 코드를 리팩토링하는 데 도움을 주는 테스트 도구
기본적으로 유닛 테스트는 react testing library를 사용하고, e2e 테스트는 playwright를 권장한다

- Vitest
- React Testing Library w/ Jest
- Playwright

## Styling

- Tailwind CSS
- Styled Components
- Emotion

## UI Component Libraries

UI를 구현하는데 많은 시간을 줄여주는 컴포넌트 라이브러리

- Material UI
- Mantine UI
- Ant Design
- Chakra UI

Tailwind CSS 기반의 컴포넌트 라이브러리

- Headless UI
- Daisy UI
- Shadcn UI

## Animation

UI의 매력도와 몰입감을 높이는데 도움을 주는 애니메이션 라이브러리

- React Spring
- Framer Motion

## Data Visualization

복잡한 데이터셋에 의존하는 리액트 어플리케이션을 구축할 때 도움을 주는 라이브러리

- rechart
- Victory
- react-chartjs-2

## Table

도표는 종종 복잡하고 구현하기 까다로운 UI 요소이며, 커스터마이징은 물론 정렬, 필터, 페이지네이션 기능을 함께 제공해야 하는 경우가 종종 있다

- Tanstack Table

## i18n

비즈니스 표적 고객을 국제적 범위로 확장하기 위해 필수적인 작업을 도와주는 라이브러리

- react-i18next
- Format.js

## Devtools

- React Devtool
- Redux Devtool
- Testing Playground for React Testing Library
- React Hook Form Devtool
- Tanstack Query Devtool
- Axe Devtool (Accessibility)

## Documentation

- Docusaurus
- Nextra

## Component DEV Environment

디자인 시스템에 속한 컴포넌트를 개발하고 테스트하는 데 도움을 주는 도구

- Storybook

## Type Checking

- TypeScript

## Mobile Apps

- React Native

## ETC

- dnd kit - drag and drop functionality
- react dropzone - file upload
- Firebase or Supabase - authentication, database, storage, hosting...
