---
description: 골프 분석 결과 파일의 생성 여부를 확인하는 API입니다.
---

# 골프 분석 결과 생성 여부 확인

## 골프 분석 결과 비디오 요청

<mark style="color:green;">`POST`</mark> `http://115.94.164.253:15003/golf/check-request`

사용자 id(이메일), 분석된 비디오 uuid를 파라미터로 받아 골프 결과 파일 생성 여부를 리턴합니다.

**파라미터(json)**

<table><thead><tr><th>Name</th><th>Type</th><th>Description</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td><code>id</code></td><td>string</td><td>유저 이메일 주소</td><td>true</td></tr><tr><td><code>uuid</code></td><td>string</td><td>영상 uuid</td><td>true</td></tr></tbody></table>

**응답(json)**

<table><thead><tr><th width="189">Name</th><th width="78">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>state</code></td><td>string</td><td>완료 시 1, 미완료 시 0</td></tr><tr><td><code>wait_time</code></td><td>int</td><td>대기 시간(초 단위)</td></tr><tr><td><code>message</code></td><td>string</td><td>안내 메세지</td></tr></tbody></table>

**요청 예시**

<pre class="language-json"><code class="lang-json"><strong>http://115.94.164.253:15003/golf/get-video/example@email.com/bc692864-0243-4d41-bce3-7658c92ef0c5
</strong></code></pre>

**응답 예시**
