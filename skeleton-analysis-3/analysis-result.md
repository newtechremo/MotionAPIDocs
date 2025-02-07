---
description: 완료된 달리기 분석 결과를 요청하는 API입니다.
---

# 달리기 분석 결과 요청

## 달리기 분석 결과 요청

<mark style="color:red;">`GET`</mark> `http://115.94.164.253:15003/running/get-val/{id}/{uuid}`

사용자 id(이메일), 분석된 비디오 uuid를 파라미터로 받아 달리기분석 결과 값을 리턴합니다.

**파라미터(json)**

<table><thead><tr><th>Name</th><th>Type</th><th>Description</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td><code>id</code></td><td>string</td><td>유저 이메일 주소</td><td>true</td></tr><tr><td><code>uuid</code></td><td>string</td><td>영상 uuid</td><td>true</td></tr></tbody></table>

**응답(json)**

<table><thead><tr><th width="126">Category</th><th width="157">Name</th><th width="86">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>right_contact</code></td><td><code>ankle_location</code></td><td>list</td><td>컨택 시 발 위치는 몸 중심보다 뒤로 가있어야 함. 해당 값은 발목 위치에서 몸 중심 위치를 뺀 값. RightAnkleCoordX - CenterCoordX 참고.</td></tr><tr><td></td><td><code>ankle_angle</code></td><td>list</td><td>컨택 시 발목 각도가 0도에 가까워야 함. RightAnkle(z) 참고.</td></tr><tr><td></td><td><code>opposite_thigh_angle</code></td><td>list</td><td>컨택 시 반대쪽 다리의 대퇴부 각도는 지면과 90도 이상. GLeftHip(z) 참고.</td></tr><tr><td><code>left_contact</code></td><td><code>ankle_location</code></td><td>list</td><td>컨택 시 발 위치는 몸 중심보다 뒤로 가있어야 함. 해당 값은 발목 위치에서 몸 중심 위치를 뺀 값. LeftAnkleCoordX - CenterCoordX 참고.</td></tr><tr><td></td><td><code>ankle_angle</code></td><td>list</td><td>컨택 시 발목 각도가 0도에 가까워야 함. LeftAnkle(z) 참고.</td></tr><tr><td></td><td><code>opposite_thigh_angle</code></td><td>list</td><td>컨택 시 반대쪽 다리의 대퇴부 각도는 지면과 90도 이상. GRightHip(z) 참고.</td></tr><tr><td><code>right_off</code></td><td><code>opposite_knee_angle</code></td><td>list</td><td>오프 시 앞쪽 다리 무릎 각도 90도 이상. LeftKnee(x) 참고.</td></tr><tr><td></td><td><code>opposite_elbow_angle</code></td><td>list</td><td>오프 시 뒤쪽 팔꿈치 각도 110도. LeftElbow(x) 참고.</td></tr><tr><td></td><td><code>elbow_angle</code></td><td>list</td><td>오프 시 앞쪽 팔꿈치 각도 90도. RightElbow(x) 참고.</td></tr><tr><td></td><td><code>opposite_shoulder_angle</code></td><td>list</td><td>오프 시 뒤쪽 상완 지면 수직선과 80도. LeftShoulder(x) 참고.</td></tr><tr><td><code>left_off</code></td><td><code>opposite_knee_angle</code></td><td>list</td><td>오프 시 앞쪽 다리 무릎 각도 90도 이상. RightKnee(x) 참고.</td></tr><tr><td></td><td><code>opposite_elbow_angle</code></td><td>list</td><td>오프 시 뒤쪽 팔꿈치 각도 110도. RightElbow(x) 참고.</td></tr><tr><td></td><td><code>elbow_angle</code></td><td>list</td><td>오프 시 앞쪽 팔꿈치 각도 90도. LeftElbow(x) 참고.</td></tr><tr><td></td><td><code>opposite_shoulder_angle</code></td><td>list</td><td>오프 시 뒤쪽 상완 지면 수직선과 80도. RightShoulder(x) 참고.</td></tr></tbody></table>

**요청 예시**

```json
http://115.94.164.253:15003/running/get-result/example@email.com/bc692864-0243-4d41-bce3-7658c92ef0c5
```

**응답 예시**

{% tabs %}
{% tab title="200" %}
```json
{
  'right_contact': {
    'ankle_location': [
      198.05,
      95.57,
      96.26,
      11.195,
      49.315
    ],
    'ankle_angle': [
      4.3,
      -0.094,
      1.577,
      -3.672,
      -2.294
    ],
    'opposite_thigh_angle': [
      -94.808,
      -92.87,
      -93.904,
      -92.706,
      -93.149
    ]
  },
  'left_contact': {
    'ankle_location': [
      134.79,
      298.795,
      197.08,
      96.055
    ],
    'ankle_angle': [
      5.66,
      7.749,
      5.779,
      3.856
    ],
    'opposite_thigh_angle': [
      -87.813,
      -80.298,
      -87.931,
      -87.589
    ]
  },
  'right_off': {
    'opposite_knee_angle': [
      85.818,
      94.801,
      97.391,
      80.922,
      92.15
    ],
    'opposite_elbow_angle': [
      76.819,
      76.846,
      81.198,
      76.662,
      78.036
    ],
    'elbow_angle': [
      86.774,
      87.598,
      82.074,
      84.719,
      91.12
    ],
    'opposite_shoulder_angle': [
      -44.214,
      -43.156,
      -41.096,
      -44.929,
      -43.327
    ]
  },
  'left_off': {
    'opposite_knee_angle': [
      81.118,
      85.272,
      67.549,
      78.179
    ],
    'opposite_elbow_angle': [
      113.614,
      98.385,
      101.382,
      96.331
    ],
    'elbow_angle': [
      55.16,
      59.837,
      56.092,
      56.605
    ],
    'opposite_shoulder_angle': [
      -26.022,
      -24.678,
      -36.57,
      -39.193
    ]
  }
}
```
{% endtab %}
{% endtabs %}
