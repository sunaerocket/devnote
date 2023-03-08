# Parcel

- 설정이 거의 없이 사용 가능한 빌드 도구
- 진입점이나 정적파일 제공을 위한 설정은 하는 것이 편하다

## 설정 예시

{% code title="package.json" overflow="wrap" %}
```json
"source": "./index.html",
```
{% endcode %}

{% code title=".parcelrc" overflow="wrap" %}
```json
{
  "extends": ["@parcel/config-default"],
  "reporters":  ["...", "parcel-reporter-static-files-copy"]
}
```
{% endcode %}


