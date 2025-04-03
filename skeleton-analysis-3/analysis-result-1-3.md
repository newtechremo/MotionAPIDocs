---
description: 완료된 달리기 분석 각도를 요청하는 API입니다.
---

# 달리기 분석 각도 요청

## 달리기 분석 각도 요청

<mark style="color:red;">`GET`</mark> `http://115.94.164.253:15003/running/get-angle/{id}/{uuid}`

사용자 id(이메일), 분석된 비디오 uuid를 파라미터로 받아 달리기 분석 각도 값을 리턴합니다.

**파라미터(json)**

<table><thead><tr><th>Name</th><th>Type</th><th>Description</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td><code>id</code></td><td>string</td><td>유저 이메일 주소</td><td>true</td></tr><tr><td><code>uuid</code></td><td>string</td><td>영상 uuid</td><td>true</td></tr></tbody></table>

**응답(json)**

<table><thead><tr><th width="134">Name</th><th width="86">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>RightHip</code></td><td>list</td><td>2차원 리스트. 시간에 따른 오른 힙의 각도 변화. [인식 프레임 수, 3]의 사이즈를 가짐. 3은 각 x축 각도, y축 각도, z축 각도임</td></tr><tr><td><code>LeftHip</code></td><td>list</td><td>2차원 리스트. 시간에 따른 왼 힙의 각도 변화. [인식 프레임 수, 3]의 사이즈를 가짐. 3은 각 x축 각도, y축 각도, z축 각도임.</td></tr><tr><td><code>RightKnee</code></td><td>list</td><td>2차원 리스트. 시간에 따른 오른 무릎의 각도 변화. [인식 프레임 수, 3]의 사이즈를 가짐. 3은 각 x축 각도, y축 각도, z축 각도임.</td></tr><tr><td><code>LeftKnee</code></td><td>list</td><td>2차원 리스트. 시간에 따른 왼 무릎의 각도 변화. [인식 프레임 수, 3]의 사이즈를 가짐. 3은 각 x축 각도, y축 각도, z축 각도임.</td></tr></tbody></table>

**요청 예시**

<pre class="language-json"><code class="lang-json"><strong>http://115.94.164.253:15003/running/get-angle/example@email.com/bc692864-0243-4d41-bce3-7658c92ef0c5
</strong></code></pre>

**응답 예시**

{% tabs %}
{% tab title="200" %}
```json
{
  'KneeLine': [
    [
      0.0,
      169.4,
      -141.94
    ],
    ...,
    [
      0.0,
      -375.487,
      -23.819
    ]
  ],
  'Pelvis': [
    [
      -1.029,
      10.759,
      -96.665
    ],
    ...,
    [
      -5.217,
      12.246,
      -85.496
    ]
  ],
  'ShoulderLine': [
    [
      61.789,
      61.491,
      -79.746
    ],
    ...,
    [
      140.205,
      136.012,
      -74.952
    ]
  ]
}
```
{% endtab %}
{% endtabs %}
