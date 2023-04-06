# TDD(Test Driven Development)

개발을 진행하는 도구로 테스트를 활용하는 방법론이다. Red -> Green -> Refactor 사이클을 반복하면서 개발 명세를 구체화하고 코드의 의도를 선명하게 드러내거나 중복을 제거하는 탈고 작업을 거친다. 이러면 구현에 앞서 인터페이스와 스펙을 정의하기 때문에 비교적 집중력을 잃지 않고 개발해 나갈 수 있다.

## Describe-Context-It 패턴

테스트 코드를 작성하기 위한 템플릿이다. 테스트 코드를 작성할 때 테스트 대상이 되는 함수를 `describe`로 감싸고, `context`로 테스트 대상이 되는 함수의 상황을 구분하고, `it`으로 테스트 대상이 되는 함수의 기대하는 결과를 작성한다.

- [GitHub/ahastudio: Given When Then 패턴](https://github.com/ahastudio/til/blob/main/blog/2018/12-08-given-when-then.md)


## 참고자료

- [GitHub/ahastudio: TDD](https://github.com/ahastudio/til/blob/main/agile/test-driven-development.md)
- [GitHub/ahastudio: TDD, FAQ](https://github.com/ahastudio/til/blob/main/blog/2016/12-03-tdd-faq.md)
- [GitHub/ahastudio: Simple Example](https://github.com/ahastudio/til/blob/main/jest/20201204-simple-tdd-example.md)