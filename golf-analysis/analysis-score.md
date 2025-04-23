---
description: 완료된 골프 분석 결과를 요청하는 API입니다.
---

# 골프 분석 점수 요청

## 골프 분석 점수요청

<mark style="color:red;">`GET`</mark> `http://115.94.164.253:15003/golf/get-score/{id}/{uuid}`

사용자 id(이메일), 분석된 비디오 uuid를 파라미터로 받아 골프분석 점수 값을 리턴합니다.

**파라미터(json)**

<table><thead><tr><th>Name</th><th>Type</th><th>Description</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td><code>id</code></td><td>string</td><td>유저 이메일 주소</td><td>true</td></tr><tr><td><code>uuid</code></td><td>string</td><td>영상 uuid</td><td>true</td></tr></tbody></table>

**응답(json)**

<table><thead><tr><th width="185">Category</th><th width="126">Name</th><th width="86">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>address</code></td><td><code>stance</code></td><td>float</td><td>스탠스 폭. 만점 40점.</td></tr><tr><td></td><td><code>upper_body_tilt</code></td><td>float</td><td>상체 기울임 정도. 만점 40점.</td></tr><tr><td></td><td><code>shoulder_tilt</code></td><td>float</td><td>어깨 기울임 정도. 만점 20점.</td></tr><tr><td></td><td><code>total</code></td><td>float</td><td>address 합산.</td></tr><tr><td><code>takeback</code></td><td><code>left_shoulder_rotation</code></td><td>float</td><td>왼쪽 어깨 회전. 만점 30점.</td></tr><tr><td></td><td><code>right_hip_rotation</code></td><td>float</td><td>우측 골반 회전. 만점 30점.</td></tr><tr><td></td><td><code>left_arm_flexion</code></td><td>float</td><td>왼팔 펴짐 각도. 만점 20점.</td></tr><tr><td></td><td><code>right_arm_flexion</code></td><td>float</td><td>오른팔 펴짐 각도. 만점 20점.</td></tr><tr><td></td><td><code>total</code></td><td>float</td><td>takeback 합산.</td></tr><tr><td><code>backswing</code></td><td><code>head_location</code></td><td>float</td><td>머리 위치. 만점 30점.</td></tr><tr><td></td><td><code>left_arm_flexion</code></td><td>float</td><td>왼팔 펴짐 각도. 만점 20점.</td></tr><tr><td></td><td><code>left_shoulder_rotation</code></td><td>float</td><td>왼쪽 어깨 회전. 만점 50점.</td></tr><tr><td></td><td><code>total</code></td><td>float</td><td>backswing 합산.</td></tr><tr><td><code>backswingtop</code></td><td><code>reverse_spine</code></td><td>float</td><td>리버스 스파인. 만점 50점.</td></tr><tr><td></td><td><code>right_leg_flexion</code></td><td>float</td><td>오른 다리 펴짐 각도. 만점 10점.</td></tr><tr><td></td><td><code>head_location</code></td><td>float</td><td>머리 위치. 만점 10점.</td></tr><tr><td></td><td><code>center_of_gravity</code></td><td>float</td><td>무게 중심. 만점 10점.</td></tr><tr><td></td><td><code>right_hip_rotation</code></td><td>float</td><td>우측 골반 회전. 만점 20점.</td></tr><tr><td></td><td><code>total</code></td><td>float</td><td>backswingtop 합산.</td></tr><tr><td><code>downswing</code></td><td><code>center_of_gravity</code></td><td>float</td><td>무게 중심. 만점 30점.</td></tr><tr><td></td><td><code>right_elbow_location</code></td><td>float</td><td>오른팔꿈치 위치. 만점 20점.</td></tr><tr><td></td><td><code>right_arm_rotation</code></td><td>float</td><td>오른팔-겨드랑이 각도. 만점 50점.</td></tr><tr><td></td><td><code>total</code></td><td>float</td><td>downswing 합산.</td></tr><tr><td><code>impact</code></td><td><code>head_location</code></td><td>float</td><td>머리 위치. 만점 10점.</td></tr><tr><td></td><td><code>left_arm_flexion</code></td><td>float</td><td>왼팔 펴짐 각도. 만점 20점.</td></tr><tr><td></td><td><code>right_arm_flexion</code></td><td>float</td><td>오른팔 펴짐 각도. 만점 20점.</td></tr><tr><td></td><td><code>hanging_back</code></td><td>float</td><td>행잉백. 만점 50점.</td></tr><tr><td></td><td><code>total</code></td><td>float</td><td>impact 합산.</td></tr><tr><td><code>follow</code></td><td><code>left_line_align</code></td><td>float</td><td>왼쪽 라인 일직선 정도. 만점 40점.</td></tr><tr><td></td><td><code>chicken_wing</code></td><td>float</td><td>치킨윙(왼팔 펴짐 각도). 만점 20점.</td></tr><tr><td></td><td><code>center_of_gravity</code></td><td>float</td><td>무게 중심. 만점 30점.</td></tr><tr><td></td><td><code>total</code></td><td>float</td><td>follow 합산.</td></tr><tr><td><code>finish</code></td><td><code>left_foot_fix</code></td><td>float</td><td>왼발 고정 여부. 만점 30점.</td></tr><tr><td></td><td><code>right_foot_rotation</code></td><td>float</td><td>오른발 회전 여부. 만점 30점.</td></tr><tr><td></td><td><code>center_of_gravity</code></td><td>float</td><td>무게 중심. 만점 40점.</td></tr><tr><td></td><td><code>total</code></td><td>float</td><td>finish 합산.</td></tr><tr><td><code>total_score</code></td><td></td><td>float</td><td>전체 합산 평균.</td></tr></tbody></table>

**요청 예시**

<pre class="language-json"><code class="lang-json"><strong>http://115.94.164.253:15003/golf/get-score/example@email.com/bc692864-0243-4d41-bce3-7658c92ef0c5
</strong></code></pre>

**응답 예시**

{% tabs %}
{% tab title="200" %}
```json
{
  'address': {
    'stance': 40,
    'upper_body_tilt': 40,
    'shoulder_tilt': 0,
    'total': 80
  },
  'takeback': {
    'left_arm_flexion': 11.497,
    'left_shoulder_rotation': 0,
    'right_hip_rotation': 0,
    'right_arm_flexion': 20,
    'total': 31.497
  },
  'backswing': {
    'left_shoulder_rotation': 0,
    'head_location': 30,
    'left_arm_flexion': 11.497,
    'total': 41.496
  },
  'backswingtop': {
    'right_hip_rotation': 0,
    'reverse_spine': 6.296,
    'right_leg_flexion': -8.382,
    'head_location': 3.317,
    'center_of_gravity': 0,
    'total': 1.231
  },
  'downswing': {
    'center_of_gravity': 0,
    'right_elbow_location': 10,
    'right_arm_rotation': 50,
    'total': 60
  },
  'impact': {
    'hanging_back': 0,
    'head_location': 8.447,
    'left_arm_flexion': 14.881,
    'right_arm_flexion': 14.649,
    'total': 37.977
  },
  'follow': {
    'left_line_align': 19.272,
    'chicken_wing': 14.881,
    'center_of_gravity': 20.443,
    'total': 54.596
  },
  'finish': {
    'left_foot_fix': 0,
    'right_foot_rotation': 17.595,
    'center_of_gravity': 40,
    'total': 57.595
  },
  'total_score': 45.549
}
```
{% endtab %}
{% endtabs %}
