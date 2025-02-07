---
description: 완료된 보행 분석 결과 영상을 요청하는 API입니다.
---

# 보행 분석 결과 영상 요청

## 보행 분석 결과 영상 요청

<mark style="color:green;">`POST`</mark>`http://api.remo.re.kr/api/analysis-walking-draw`

사용자 id(이메일), 분석된 비디오 uuid를 파라미터로 원본 영상에 결과를 그린 비디오(base64)를 Return합니다.

**파라미터(json)**

<table><thead><tr><th>Name</th><th>Type</th><th>Description</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td><code>id</code></td><td>string</td><td>유저 이메일 주소</td><td>true</td></tr><tr><td><code>uuid</code></td><td>string</td><td>영상 uuid</td><td>true</td></tr></tbody></table>

**응답(json)**

<table><thead><tr><th width="172">Name</th><th width="84">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>state</code></td><td>int</td><td>성공 시 1, 실패 시 0</td></tr><tr><td><code>message</code></td><td>string</td><td>성공 또는 실패 관련 안내 메세지</td></tr><tr><td><code>base64_video</code></td><td>string</td><td>원본 영상에 결과를 그려 base64로 인코딩된 비디오</td></tr></tbody></table>

**요청 예시**

```json
/get-draw/example@example.com/bc692864-0243-4d41-bce3-7658c92ef0c5
```

**응답 예시**

{% tabs %}
{% tab title="200" %}
```json
{
  "state": 1,
  "base64_video": "AAAAIGZ0eXBpc29tAAACAGlzb21pc28yYXZjMW1wNDEAAAAIZnJlZQAK/7BtZGF0AAACugYF … (이하 생략)",
  "message": "success"
}
```
{% endtab %}

{% tab title="400" %}
```json
{
  "state": 0,
  "message": "An error occurred in returning results due to video file being created"
}
```
{% endtab %}

{% tab title="400" %}
```json
{
  "state": 0,
  "message": "base64 encoding error"
}
```
{% endtab %}
{% endtabs %}
