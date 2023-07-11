# External Store

리액트 앱에서 직접 관리하지 않고 외부에서 관리하는 상태를 의미한다. React에서 직접 관리하는 상태는 useState 훅을 이용하여 리렌더링까지 자동으로 해주지만, 외부에서 관리하는 상태는 React가 자동으로 리렌더링해주지 않기 때문에, 상태 변경 후 React API를 호출하여 수동으로 리렌더링 처리를 해줘야 한다.

직접 외부 상태 관리 라이브러리를 만드려면 그 외에도, 불필요한 리렌더링을 방지하기 위한 최적화 기법이 필요하다. 이를 위해 React에서 제공하는 다양한 API(useState, useCallback, useRef, etc.)를 사용할 수 있다.

## 관심사의 분리(SoC, Separation of Concerns)

시스템을 작은 부품으로 나눠서 구성하는 방식으로, 작은 컴포넌트를 합성하여 큰 컴포넌트를 만드는 방식도 SoC 사례다. 분리 기준은 기능 단위, 설계 단위 등 여러가지가 있을 수 있다.

코드레벨에서 Input -> Process -> Output 3단계로 코드를 적절히 구분하기만 해도 가독성과 유지보수성에 도움이 된다. 하나의 Output은 다시 사용자에게 Input을 요청하게 되고, 일반적인 프로그램은 순환 구조를 가지게 된다.

```plaintext
# Input -> Process -> Output 관심사 분리 예시

1. Input: 프로그램 시작
2. Process: 프로그램 초기화
3. Output: 사용자에게 초기 UI 보여주기
4. Input: 사용자의 입력
5. Process: 사용자의 입력을 처리
6. Output: 사용자에게 처리 결과 보여주기
7. Input: 사용자의 또 다른 입력
8. ...반복...
```

MVC 패턴 역시 관심사의 분리를 기반으로 한다. Model은 데이터를 관리하고, View는 사용자에게 보여주는 역할을 하고, Controller는 Model과 View를 연결하는 역할을 한다. 완벽하게 대응시킬 수 없지만, 앞서 언급한 3단계 구분법을 적용하면 다음과 같다.

```plaintext
Model -> Process
View -> Output
Controller -> Input
```

- [wikipedia/separation of concern](https://ko.wikipedia.org/wiki/%EA%B4%80%EC%8B%AC%EC%82%AC_%EB%B6%84%EB%A6%AC)

### Layered Architecture

사용자와의 거리를 기준으로 나누는 방식으로, 사용자와 가까운 UI Layer, 중간의 Business Logic Layer, 사용자와 먼 Data Layer 등으로 나누는 방식이다.

***TODO: Layered Architecture 내용 보강***

### Flux Architecture

React에서 상태를 관리하는 방식으로, Facebook(현 Meta) MVC 패턴의 대안으로 제안한 구조다. 기존에 양방향 데이터 바인딩을 사용하면서 생긴 복잡한 Model-View간 관계를 단순화한다.

```plaintext
1. Action -> 이벤트/메시지 객체 같은 역할
2. Dispatcher -> 메시지 브로커와 유사한 역할로 Action을 받아서 특정 Store에 전달
3. Store -> 데이터를 관리하고, Dispatcher로부터 Action을 받아서 상태 변경을 알림. 여러개로 구성할 수 있다.
4. View -> 구독하는 Store로부터 상태 변경을 받아서 화면을 갱신
```

Redux는 단일 Store를 사용함으로써 더 단순한 구조를 제안한다.

```plaintext
1. Action
2. Store -> dispatch를 통해 Action 받고, 사용자가 정의한 reducer를 통해 상태 변경
3. View -> Store 상태를 반영
```

앞서 언급한 3단계 분리를 거칠게 적용하면 다음과 같다.

```plaintext
Input -> Action + dispatch
Process -> reducer
Output -> View(React)
```

- [Flux/docs: overview](https://haruair.github.io/flux/docs/overview.html)
- [Redux/tutorial: overview concepts](https://ko.redux.js.org/tutorials/essentials/part-1-overview-concepts/)

### 테스트와 관심사의 분리

리액트 컴포넌트는 UI와 비즈니스 로직을 모두 포함하고 있기 때문에 관심사의 분리를 적용하면 테스트하기 쉬운 컴포넌트를 만들 수 있다. 자주 바뀌는 UI 요소에 대한 테스트는 최소화하고, 바뀌면 치명적인 비즈니스 로직에 대한 테스트를 중점적으로 테스트를 작성하면 비교적 치밀하게 유지보수에 도움이 되는 테스트를 작성할 수 있다.

## TSyringe

Props Drilling 문제 해결에 사용할 수 있는 의존성 주입(Dependency Injection, DI) 라이브러리.
사용하기 위해서는 React, Jest 엔트리포인트에 reflect-metadata를 import하고 tsconfig의 데코레이터 옵션을 활성화해야 한다.

### 싱글톤 객체로 스토어 생성하기

```typescript
import { singleton } from 'tsyringe';

@singleton()
class Store {
  private count = 0;

  increment() {
    this.count += 1;
  }

  getCount() {
    return this.count;
  }
}
```

- [GitHub/tsyringe: Lightweight dependency injection container for JavaScript/TypeScript](https://github.com/microsoft/tsyringe)
- [GitHub/reflect-metadata](https://github.com/rbuckton/reflect-metadata)
- [React/docs: useSyncExternalStore](https://react.dev/reference/react/useSyncExternalStore)
- [Youtube/FEConf Korea: 2022 상태관리 이 전재을 끝내러 왔다](https://www.youtube.com/watch?v=KEDUqA9JeIo)
