---
description: 완료된 골프 분석 결과 비디오를 요청하는 API입니다.
---

# 골프 분석 결과 비디오 요청

## 골프 분석 결과 비디오 요청

<mark style="color:red;">`GET`</mark> `http://115.94.164.253:15003/golf/get-video/{id}/{uuid}`

사용자 id(이메일), 분석된 비디오 uuid를 파라미터로 받아 골프분석 점수 값을 리턴합니다.

**파라미터(json)**

<table><thead><tr><th>Name</th><th>Type</th><th>Description</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td><code>id</code></td><td>string</td><td>유저 이메일 주소</td><td>true</td></tr><tr><td><code>uuid</code></td><td>string</td><td>영상 uuid</td><td>true</td></tr></tbody></table>

**응답(json)**

<table><thead><tr><th width="189">Name</th><th width="78">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>base64_video</code></td><td>string</td><td>base64로 인코딩 된 결과 비디오 문자열</td></tr></tbody></table>

**요청 예시**

<pre class="language-json"><code class="lang-json"><strong>http://115.94.164.253:15003/golf/get-video/example@email.com/bc692864-0243-4d41-bce3-7658c92ef0c5
</strong></code></pre>

**응답 예시**
