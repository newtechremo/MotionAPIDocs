---
description: 완료된 축구 분석 각도를 요청하는 API입니다.
---

# 축구 분석 각도 요청

## 축구 분석 각도 요청

<mark style="color:red;">`GET`</mark> `http://115.94.164.253:15003/soccer/get-angle/{id}/{uuid}`

사용자 id(이메일), 분석된 비디오 uuid를 파라미터로 받아 축구 분석 각도 값을 리턴합니다.

**파라미터(json)**

<table><thead><tr><th>Name</th><th>Type</th><th>Description</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td><code>id</code></td><td>string</td><td>유저 이메일 주소</td><td>true</td></tr><tr><td><code>uuid</code></td><td>string</td><td>영상 uuid</td><td>true</td></tr></tbody></table>

**응답(json)**

<table><thead><tr><th width="134">Name</th><th width="86">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>KneeLine</code></td><td>list</td><td>2차원 리스트. 시간에 따른 무릎 라인의 각도 변화. [인식 프레임 수, 3]의 사이즈를 가짐. 3은 각 x축 각도, y축 각도, z축 각도임.</td></tr><tr><td><code>Pelvis</code></td><td>list</td><td>2차원 리스트. 시간에 따른 골반의 각도 변화. [인식 프레임 수, 3]의 사이즈를 가짐. 3은 각 x축 각도, y축 각도, z축 각도임.</td></tr><tr><td><code>ShoulderLine</code></td><td>list</td><td>2차원 리스트. 시간에 따른 어깨 라인의 각도 변화. [인식 프레임 수, 3]의 사이즈를 가짐. 3은 각 x축 각도, y축 각도, z축 각도임.</td></tr></tbody></table>

**요청 예시**

<pre class="language-json"><code class="lang-json"><strong>http://115.94.164.253:15003/soccer/get-angle/example@email.com/bc692864-0243-4d41-bce3-7658c92ef0c5
</strong></code></pre>

**응답 예시**

{% tabs %}
{% tab title="200" %}
```json
{
  'KneeLine': [
    [
      0.0,
      -165.674,
      -126.883
    ],
    ...,
    [
      0.0,
      190.741,
      -145.579
    ]
  ],
  'Pelvis': [
    [
      -8.982,
      -165.871,
      -40.316
    ],
    ...,
    [
      -3.49,
      -179.608,
      3.327
    ]
  ],
  'ShoulderLine': [
    [
      -22.913,
      -160.476,
      36.85
    ],
    ...,
    [
      -2.148,
      -179.173,
      -13.319
    ]
  ]
}
```
{% endtab %}
{% endtabs %}
