# CSS 기초 문제 해결

## 이미지를 왜곡 없이 박스 채우기

이미지의 가로세로 비율이 박스와 다를 때는 사례별로 `object-fit` 속성을 활용한다.

1. `cover`: 이미지 비율을 유지한 채로 상자를 채우고 남는 부분은 자르기
2. `contain`: 이미지를 비율을 유지한 채로 상자에 들어오게 처리하기
3. `fill`: 이미지 비율을 무시하고 상자에 꽉 차게 늘리기

해당 프리셋 중 가장 자연스러운 것을 선택하는 식으로 해결할 수 있다.

엄격하게 이미지의 비율을 관리하거나 크롭 처리를 하는 방식도 가능하다.

## 박스 모델 응용하기

### 원형 처리

`border-radius` 속성을 사용하여 박스의 모서리를 조작하는 방식으로 원형 또는 타원처리를 할 수 있다.

### 배경 처리

`background` 속성을 응용하여 박스의 배경을 캔버스처럼 다룰 수 있다.

배경 속성을 활용하기 위해서는 두가지 특성을 숙지하는 것이 좋다.

첫째, 하나의 박스에 여러개의 배경을 적용하여 층을 만들 수 있다.

둘째, 배경은 단색이나 이미지를 사용할 수 있으며 단색은 항상 전체 표면을 채우지만, 이미지는 적용할 크기와 위치를 지정할 수 있다.

특히 그라디언트 기법을 응용하여 배경을 처리하면 창의적인 표현이 가능하다.

- [Lea Verou's CSS pattern](https://projects.verou.me/css3patterns/)
- [MDN - Using CSS gradients](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_images/Using_CSS_gradients)

### 가상 요소(Pseudo-Element) 응용하기

스타일링 목적으로 박스가 필요한 때, 가상요소를 활용하면 DOM을 오염시키지 않고도 스타일링을 할 수 있다.

- [web.dev - Pseudo elements](https://web.dev/learn/css/pseudo-elements/)
- [MDN - Create fancy boxes](https://developer.mozilla.org/en-US/docs/Learn/CSS/Howto/Create_fancy_boxes)

### 투명도 처리

기본적으로 박스의 투명도는 `opacity` 속성을 사용하여 조작할 수 있으며 0은 완전 투명, 1은 불투명을 의미한다.

그러나 대부분 배경색은 투명도 처리를 하고 텍스트나 다른 요소는 그대로 두고 싶은 경우가 많기 때문에 `rgba()` 함수를 사용하여 알파 채널 값을 통해 투명도를 조작하는 것을 권장한다.

추가적으로 투명도를 조작할 때는 텍스트와 배경의 대비가 무너져 가독성을 해치지 않도록 섬세하게 처리해야 한다.

## 텍스트 처리하기

### 텍스트 그림자 효과주기

`text-shadow` 속성을 사용하여 텍스트에 그림자 효과를 줄 수 있다.

### 문단 첫 문장/글자 강조하기

`::first-line` 가상 요소를 사용하여 문단의 첫 문장을 길이에 상관없이 강조 처리할 수 있다.

`::first-letter` 가상 요소를 사용하여 문단의 첫 글자를 강조 처리할 수 있다.

### 특정 요소 다음에 나오는 요소 강조하기

`+` 선택자를 사용하여 특정 요소 다음에 나오는 요소를 강조 처리할 수 있다.

## 레이아웃 만들기

기본적으로 CSS Flexbox, Grid Layout을 활용하여 레이아웃을 만든다.

### 다단 처리하기

`column-count` / `column-width` / `column-gap` / `columns` 속성을 활용하여 다단 처리를 할 수 있다.

### CSS 콘텐츠 생성 활용하기

CSS의 기본 철학은 문서의 스타일과 콘텐츠를 분리하는 것이지만, 콘텐츠가 문서 구조와 밀접하게 결합되어 있는 경우, 스타일 시트 내에 텍스트 또는 이미지 콘텐츠를 지정하는 것이 유용할 수 있다.

이런 식으로 스타일시트에 지정된 콘텐츠는 DOM에는 존재하지 않기 때문에 주의해서 관리해야 한다. 예를 들어, 번역이 필요한 콘텐츠는 스타일시트에 지정하지 않고 별도 파일에 넣고 적절한 언어 버전과 연결되도록 구성해야한다.
반면에, 지정한 콘텐츠가 모든 언어와 문화권에 적용되는 기호나 이미지인 경우, 별 문제가 없다.

### 레이아웃 쿡북 활용하기

일반적인 레이아웃 패턴에 대한 참고서를 활용하여 레이아웃을 구성한다.

#### [Media objects](https://developer.mozilla.org/en-US/docs/Web/CSS/Layout_cookbook/Media_objects)

페이스북이나 트위터 포스트처럼 한쪽에는 이미지가 있고 다른 쪽에는 텍스트가 있는 2열 박스 구성을 의미한다.

#### [Columns](https://developer.mozilla.org/en-US/docs/Web/CSS/Layout_cookbook/Column_layouts)

다단 레이아웃을 구성하기 위해 flex, 또는 grid를 사용한다.

#### [Center an element](https://developer.mozilla.org/en-US/docs/Web/CSS/Layout_cookbook/Center_an_element)

요소를 수직/수평 중앙 정렬한다.

#### [Sticky footer](https://developer.mozilla.org/en-US/docs/Web/CSS/Layout_cookbook/Sticky_footers)

콘텐츠가 뷰포트 높이보다 짧은 경우 페이지의 바닥글을 뷰포트 하단에 고정하는 패턴이다.

#### [Split navigation](https://developer.mozilla.org/en-US/docs/Web/CSS/Layout_cookbook/Split_Navigation)

네비게이션에서 로고와 메뉴처럼 특정 항목과 나머지를 분리하는 패턴이다.

#### [Breadcrumb navigation](https://developer.mozilla.org/en-US/docs/Web/CSS/Layout_cookbook/Breadcrumb_Navigation)

웹사이트 내에서 자신의 위치를 파악하도록 돕는 경로 탐색 UI 패턴이다.

#### [List group with badges](https://developer.mozilla.org/en-US/docs/Web/CSS/Layout_cookbook/List_group_with_badges)

목록의 항목마다 개수를 알려주는 배지를 표현하는 패턴이다.

#### [Pagination](https://developer.mozilla.org/en-US/docs/Web/CSS/Layout_cookbook/Pagination)

대량의 콘텐츠 페이지 사이를 이동할 수 있도록 번호를 표시하는 패턴이다.

#### [Card](https://developer.mozilla.org/en-US/docs/Web/CSS/Layout_cookbook/Card)

정보를 표시하는 패턴으로 헤더, 이미지, 콘텐츠, 푸터 등 다양하게 구성할 수 있다.

#### [Grid wrapper](https://developer.mozilla.org/en-US/docs/Web/CSS/Layout_cookbook/Grid_wrapper)

그리드 내용물을 정렬하거나 원하는 항목을 분리하여 배치하는 패턴이다.
