---
description: 완료된 골프 분석 결과를 요청하는 API입니다.
---

# 골프 분석 결과 요청

## 골프 분석 결과 요청

<mark style="color:red;">`GET`</mark> `http://115.94.164.253:15003/golf/get-val/{id}/{uuid}`

사용자 id(이메일), 분석된 비디오 uuid를 파라미터로 받아 골프분석 결과 값을 리턴합니다.

**파라미터(json)**

<table><thead><tr><th>Name</th><th>Type</th><th>Description</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td><code>id</code></td><td>string</td><td>유저 이메일 주소</td><td>true</td></tr><tr><td><code>uuid</code></td><td>string</td><td>영상 uuid</td><td>true</td></tr></tbody></table>

**응답(json)**

<table><thead><tr><th width="185">Category</th><th width="126">Name</th><th width="86">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>address</code></td><td><code>frame</code></td><td>int</td><td>구간 대표 프레임 인덱스</td></tr><tr><td></td><td><code>stance</code></td><td>float</td><td>스탠스 폭. AnkleShoulderRatio 참고.</td></tr><tr><td></td><td><code>upper_body_tilt</code></td><td>float</td><td> 상체 기울임 정도. HipNeckRatio 참고.</td></tr><tr><td></td><td><code>shoulder_tilt</code></td><td>float</td><td>어깨 기울임 정도. UpperBody(z) 참고.</td></tr><tr><td></td><td><code>head_location</code></td><td>float</td><td>기준 머리 위치. 점수에는 반영하지 않음.</td></tr><tr><td><code>takeback</code></td><td><code>frame</code></td><td>int</td><td>구간 대표 프레임 인덱스</td></tr><tr><td></td><td><code>left_shoulder_rotation</code></td><td>float</td><td>왼쪽 어깨 회전.</td></tr><tr><td></td><td><code>right_hip_rotation</code></td><td>float</td><td>우측 골반 회전.</td></tr><tr><td></td><td><code>left_arm_flexion</code></td><td>float</td><td>왼팔 펴짐 각도. LeftElbow(x) 참고.</td></tr><tr><td></td><td><code>right_arm_flexion</code></td><td>float</td><td>오른팔 펴짐 각도. RightElbow(x) 참고.</td></tr><tr><td><code>backswing</code></td><td><code>frame</code></td><td>int</td><td>구간 대표 프레임 인덱스</td></tr><tr><td></td><td><code>head_location</code></td><td>float</td><td>머리 위치. { HeadLocation(backswing) - HeadLocation(address) } / height 참고.</td></tr><tr><td></td><td><code>left_shoulder_rotation</code></td><td>float</td><td>왼쪽 어깨 회전.</td></tr><tr><td></td><td><code>left_arm_flexion</code></td><td>float</td><td>왼팔 펴짐 각도. LeftElbow(x) 참고.</td></tr><tr><td><code>backswingtop</code></td><td><code>frame</code></td><td>int</td><td>구간 대표 프레임 인덱스</td></tr><tr><td></td><td><code>reverse_spine</code></td><td>float</td><td>리버스 스파인. -Spine2(x) 참고.</td></tr><tr><td></td><td><code>right_hip_rotation</code></td><td>float</td><td>우측 골반 회전.</td></tr><tr><td></td><td><code>right_leg_flexion</code></td><td>float</td><td>오른 다리 펴짐 각도. RightKnee(x) 참고.</td></tr><tr><td></td><td><code>head_location</code></td><td>float</td><td>머리 위치. { HeadLocation(top) - HeadLocation(address) } / height 참고.</td></tr><tr><td></td><td><code>center_of_gravity</code></td><td>float</td><td>무게 중심. AnkleHipRatio 참고.</td></tr><tr><td><code>downswing</code></td><td><code>frame</code></td><td>int</td><td>구간 대표 프레임 인덱스</td></tr><tr><td></td><td><code>center_of_gravity</code></td><td>float</td><td>무게 중심. AnkleHipRatio 참고.</td></tr><tr><td></td><td><code>right_elbow_location</code></td><td>float</td><td>오른팔꿈치 위치. LeftElbowCoordY - RightElbowCoordY > 0 참고.</td></tr><tr><td></td><td><code>right_arm_rotation</code></td><td>float</td><td>오른팔-겨드랑이 각도. RightShoulder(y) 참고.</td></tr><tr><td><code>impact</code></td><td><code>frame</code></td><td>int</td><td>구간 대표 프레임 인덱스</td></tr><tr><td></td><td><code>head_location</code></td><td>float</td><td>머리 위치. { HeadLocation(impact) - HeadLocation(address) } / height 참고.</td></tr><tr><td></td><td><code>left_arm_flexion</code></td><td>float</td><td>왼팔 펴짐 각도. LeftElbow(x) 참고.</td></tr><tr><td></td><td><code>right_arm_flexion</code></td><td>float</td><td>오른팔 펴짐 각도. RightElbow(x) 참고.</td></tr><tr><td></td><td><code>hanging_back</code></td><td>float</td><td>행잉백.</td></tr><tr><td><code>follow</code></td><td><code>frame</code></td><td>int</td><td>구간 대표 프레임 인덱스</td></tr><tr><td></td><td><code>left_line_align</code></td><td>float</td><td>왼쪽 라인 일직선 정도. LAnkleLHipHori 참고.</td></tr><tr><td></td><td><code>chicken_wing</code></td><td>float</td><td>치킨윙(왼팔 펴짐 각도). LeftElbow(x) 참고.</td></tr><tr><td></td><td><code>center_of_gravity</code></td><td>float</td><td>무게 중심. AnkleHipRatio 참고.</td></tr><tr><td><code>finish</code></td><td><code>frame</code></td><td>int</td><td>구간 대표 프레임 인덱스</td></tr><tr><td></td><td><code>left_foot_fix</code></td><td>float</td><td>왼발 고정 여부. GLeftAnkle(y) 참고.</td></tr><tr><td></td><td><code>right_foot_rotation</code></td><td>float</td><td>오른발 회전 여부. GRightHip(y) 참고.</td></tr><tr><td></td><td><code>center_of_gravity</code></td><td>float</td><td>무게 중심. LAnkleRHipHori 참고.</td></tr></tbody></table>

**요청 예시**

```json
http://115.94.164.253:15003/golf/get-result/example@email.com/bc692864-0243-4d41-bce3-7658c92ef0c5
```

**응답 예시**

{% tabs %}
{% tab title="200" %}
```json

  "address": {
    "stance": 1.555,
    "upper_body_tilt": 0.487,
    "shoulder_tilt": -1.125,
    "head_location": 1350.07,
    "left_foot_fix": 0.0,
    "frame": 30
  },
  "takeback": {
    "left_shoulder_rotation": 40.847,
    "right_hip_rotation": 1.847,
    "left_arm_flexion": 169.687,
    "right_arm_flexion": 144.502,
    "frame": 56
  },
  "backswing": {
    "left_shoulder_rotation": 22.838,
    "head_location": 3.493,
    "left_arm_flexion": 117.072,
    "frame": 64
  },
  "backswingtop": {
    "right_hip_rotation": 2.144,
    "reverse_spine": -13.399,
    "right_leg_flexion": 26.797,
    "head_location": 1.981,
    "center_of_gravity": 59.455,
    "frame": 67
  },
  "downswing": {
    "center_of_gravity": 60.382,
    "right_elbow_location": 26.246,
    "right_arm_rotation": 23.512,
    "frame": 76
  },
  "impact": {
    "hanging_back": 73.224,
    "head_location": -4.328,
    "left_arm_flexion": 161.494,
    "right_arm_flexion": 164.273,
    "frame": 80
  },
  "follow": {
    "left_line_align": 10.301,
    "chicken_wing": 142.121,
    "center_of_gravity": 72.225,
    "frame": 86
  },
  "finish": {
    "left_foot_fix": 0.0,
    "right_foot_rotation": 50.196,
    "center_of_gravity": 5.354,
    "frame": 122
  }
}
```
{% endtab %}
{% endtabs %}
