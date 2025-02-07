---
description: 비디오를 입력 받아 사용자의 보행을 분석하는 API입니다.
---

# 보행 비디오 분석 요청

## 보행 비디오 분석 요청

<mark style="color:green;">`POST`</mark> `http://api.remo.re.kr/api/analysis-walking`

보행 비디오를 입력 받아 분석 완료 시까지 대기할 시간을 Return합니다.

**파라미터(json)**

<table><thead><tr><th>Name</th><th>Type</th><th>Description</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td><code>base64_video</code></td><td>string(base64 )</td><td>base64로 인코딩 된 보행 비디오 문자열</td><td>true</td></tr><tr><td><code>id</code></td><td>string</td><td>유저 이메일 주소</td><td>true</td></tr><tr><td><code>height</code></td><td>string</td><td>분석 대상의 키(cm)</td><td>true</td></tr></tbody></table>

**응답(json)**

<table><thead><tr><th width="164">Name</th><th width="88">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>state</code></td><td>int</td><td>성공 시 1, 실패 시 0</td></tr><tr><td><code>message</code></td><td>string</td><td>성공 또는 실패 관련 안내 메세지</td></tr><tr><td><code>uuid</code></td><td>string</td><td>영상 uuid</td></tr><tr><td><code>wait_time</code></td><td>int</td><td>응답 후 결과 생성까지 대기 시간</td></tr></tbody></table>

**요청 예시**

<pre class="language-html"><code class="lang-html">{
<strong>    “base64_video”: “AAAAIGZ0eXBpc29tAAACAGlzb21pc28yYXZjMW1wNDEAAAAIZnJlZQAK/7BtZGF0AAACugYF … (이하 생략)”,
</strong>    “id”: “example@example.com”,
    “height”: “170”
}
</code></pre>

**응답 예시**

{% tabs %}
{% tab title="200" %}
```json
{
  "state": 1,
  "wait_time": 13,
  "uuid": "d4147f2c-b5cc-4289-9325-94dbbef26d67",
  "message": "success"
}
```
{% endtab %}

{% tab title="400" %}
```json
{
  "state": 0,
  "message": "person not detected"
}
```
{% endtab %}

{% tab title="400" %}
```json
{
  "state": 0,
  "message": "keypoint estimation error"
}
```
{% endtab %}
{% endtabs %}
