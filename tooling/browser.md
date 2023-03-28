# 브라우저

## 핵심 개념

### Fetch API

브라우저에서 HTTP 요청/응답을 처리하는 API로 서버와 통신할 때 사용한다. 서버 응답은 데이터를 `ReadableStream` 객체로 받아서 `TextDecoder` 객체를 사용하여 문자열로 변환할 수 있다. 최종적으로 json 문자열을 자바스크립트 객체로 변환하여 사용하는 패턴을 사용한다.

- [Web API - Fetch](https://developer.mozilla.org/ko/docs/Web/API/Fetch_API)
- [Web API - Fetch 사용하기](https://developer.mozilla.org/ko/docs/Web/API/Fetch_API/Using_Fetch)
- [Web API - ReadableStream](https://developer.mozilla.org/ko/docs/Web/API/ReadableStream)
- [텍스트 디코더/인코더](https://ko.javascript.info/text-decoder)

### CORS

웹브라우저의 보안장치. 서버가 정의하지 않은 출처에서 가져오는 리소스는 위험하다고 가정하여 막는다.
