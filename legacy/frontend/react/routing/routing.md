# Routing

라우팅은 웹 애플리케이션에서 사용자가 요청한 URL을 처리하여 적합한 콘텐츠를 제공하는 개념이다.

## 배경

고전적인 웹 어플리케이션은 사용자가 URL을 요청할 때마다 서버에서 적절한 콘텐츠를 응답하고 브라우저에서 렌더링을 하는 과정을 반복했다. 따라서 사용자가 콘텐츠를 보기 위해 네트워크 요청/응답 시간과 렌더링 시간을 매번 기다려야 하는 것이 일반적이었다.

시간이 지나면서 웹 어플리케이션의 복잡도가 점차 증가하면서, 다양한 페이지/뷰가 추가되었고 기존 문제는 더 악화되었다. 따라서 사람들은 UI 갱신을 효율적으로 처리하기 위한 방법을 연구하기 시작했다. 이런 맥락에서 라우팅 기술은 웹 어플리케이션에서 다양한 URL 경로를 인식하고 처리하여 적절한 콘텐츠를 빠르게 제공하는 것을 목표로 발전했다.

이후 새로고침 없이 웹 어플리케이션의 일부만 갱신할 수 있는 Client Side Routing 기술이 등장했다. 이 기술은 페이지 전환 시 서버 요청이 없고 브라우저에서 UI를 갱신하기 때문에 페이지 전환 속도가 빠르고 데이터 트래픽이 감소한다는 장점이 있다.

## 특성

### 장점

#### 빠른 페이지 전환

Client Side Routing은 페이지 전환할 때 서버 요청이 가지 않고 브라우저에서 UI를 갱신하기 때문에 페이지 전환 속도가 빠르다.

#### 데이터 트래픽 감소

서버로의 요청이 없거나 최소화되기 때문에 데이터 트래픽이 감소한다. 또한 전체 페이지를 로드하는 Server Side Routing에 비해 전송할 데이터 량이 감소한다.

#### 원활한 사용자 경험

페이지 전환이 부드럽고 빠르게 이뤄져 사용자 경험을 향상시킨다.

### 단점

#### 초기 로딩 속도

초기에 모든 자원을 다운로드 받아야 하므로 Server Side Routing에 비해 초기 로딩 속도가 느릴 수 있다. 코드스플리팅이나 자원 최적화 기술을 사용하면 개선할 수 있다.

#### SEO 문제

클라이언트 사이드 라우팅은 페이지 전환이 JavaScript를 통해 동적으로 처리되어 검색 엔진 크롤러가 페이지를 인식하기 어려울 수 있다. 이를 해결하기 위해 서버 사이드 렌더링이나 프리 렌더링을 사용할 수 있다.

#### 브라우저 호환성

구형 브라우저나 일부 특정 환경에서 동작하지 않을 수 있다. 이를 해결하기 위해 폴리필을 사용하거나 서버 사이드 렌더링을 고려할 수 있다.
