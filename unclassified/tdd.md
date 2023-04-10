# TDD(Test Driven Development)

인터페이스와 스펙을 테스트로 먼저 정의하고 나서 구현해나가는 개발 방식이다. 여기서 인터페이스란 소프트웨어가 작동하는 방식을 정의한 것이고 입력, 출력, 동작이 포함된다. 스펙은 말그대로 상세한 설명이다. 따라서 구현 전에 테스트를 작성하는 것은 소프트웨어가 작동하는 방식을 상세하게 설명하여 개발자가 요구사항을 숙지할 수 있게 도와주고 비교적 집중력을 잃지 않고 개발해 나갈 수 있다. 그리고 테스트 성공/실패 여부를 통해 구현체가 요구사항을 충족하는지 확인할 수 있어서 디버깅 시간을 줄일 수 있다.

## TDD Cycle

Red -> Green -> Refactor 사이클을 반복하면서 구현한다. 만약 해당 사이클에 따라 구현을 하기 어렵다면 일반적인 개발이나 클린 코드를 작성하는 것 역시 힘들 가능성이 높다.

### Red

구현 없이 인터페이스와 스펙을 나타내는 실패하는 테스트를 작성한다.

### Green

테스트를 통과하는 최소한의 코드를 작성한다. 올바른 방법이 아니어도 괜찮다. 만약 테스트를 통과하는 코드를 작성하기 어렵다면, Red 단계로 돌아가 기존에 정의한 문제를 더 작고 쉬운 문제로 분할하고 테스트를 작성한 뒤에 구현을 시작한다.

### Refactor

리팩터링을 통해 코드를 개선한다. 의도를 드러내고 중복을 찾아 제거하는 작업을 수행한다.

## Describe-Context-It 패턴

테스트 코드를 작성하기 위한 템플릿이다. 테스트 코드를 작성할 때 테스트 대상이 되는 함수를 `describe`로 감싸고, `context`로 테스트 대상이 되는 함수의 상황을 구분하고, `it`으로 테스트 대상이 되는 함수의 기대하는 결과를 작성한다.

- [GitHub/ahastudio: Given When Then 패턴](https://github.com/ahastudio/til/blob/main/blog/2018/12-08-given-when-then.md)

## 참고자료

- [GitHub/ahastudio: TDD](https://github.com/ahastudio/til/blob/main/agile/test-driven-development.md)
- [GitHub/ahastudio: TDD, FAQ](https://github.com/ahastudio/til/blob/main/blog/2016/12-03-tdd-faq.md)
- [GitHub/ahastudio: Simple Example](https://github.com/ahastudio/til/blob/main/jest/20201204-simple-tdd-example.md)
