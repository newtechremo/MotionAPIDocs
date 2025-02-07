---
description: 완료된 골프 분석 각도를 요청하는 API입니다.
---

# 골프 분석 각도 요청

## 골프 분석 각도 요청

<mark style="color:red;">`GET`</mark> `http://115.94.164.253:15003/golf/get-angle/{id}/{uuid}`

사용자 id(이메일), 분석된 비디오 uuid를 파라미터로 받아 골프분석 각도 값을 리턴합니다.

**파라미터(json)**

<table><thead><tr><th>Name</th><th>Type</th><th>Description</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td><code>id</code></td><td>string</td><td>유저 이메일 주소</td><td>true</td></tr><tr><td><code>uuid</code></td><td>string</td><td>영상 uuid</td><td>true</td></tr></tbody></table>

**응답(json)**

<table><thead><tr><th width="134">Name</th><th width="86">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>KneeLine</code></td><td>list</td><td>2차원 리스트. 시간에 따른 무릎 라인의 각도 변화. [인식 프레임 수, 3]의 사이즈를 가짐. 3은 각 x축 각도, y축 각도, z축 각도임.</td></tr><tr><td><code>Pelvis</code></td><td>list</td><td>2차원 리스트. 시간에 따른 골반의 각도 변화. [인식 프레임 수, 3]의 사이즈를 가짐. 3은 각 x축 각도, y축 각도, z축 각도임.</td></tr><tr><td><code>ShoulderLine</code></td><td>list</td><td>2차원 리스트. 시간에 따른 어깨 라인의 각도 변화. [인식 프레임 수, 3]의 사이즈를 가짐. 3은 각 x축 각도, y축 각도, z축 각도임.</td></tr></tbody></table>

**요청 예시**

<pre class="language-json"><code class="lang-json"><strong>http://115.94.164.253:15003/golf/get-angle/example@email.com/bc692864-0243-4d41-bce3-7658c92ef0c5
</strong></code></pre>

**응답 예시**

{% tabs %}
{% tab title="200" %}
```json
{
  'KneeLine': [
    [
      0.0,
      -1.657,
      2.209
    ],
    ...,
    [
      0.0,
      -11.276,
      59.668
    ]
  ],
  'Pelvis': [
    [
      -17.104,
      1.751,
      -2.743
    ],
    ...,
    [
      1.61,
      -1.527,
      135.763
    ]
  ],
  'ShoulderLine': [
    [
      31.057,
      5.993,
      3.145
    ],
    ...,
    [
      -171.215,
      170.146,
      9.76
    ]
  ]
}
```
{% endtab %}
{% endtabs %}
