---
description: 완료된 축구 분석 결과를 요청하는 API입니다.
---

# 축구 분석 점수 요청

## 축구 분석 점수요청

<mark style="color:red;">`GET`</mark> `http://115.94.164.253:15003/soccer/get-score/{id}/{uuid}`

사용자 id(이메일), 분석된 비디오 uuid를 파라미터로 받아 축구 분석 점수 값을 리턴합니다.

**파라미터(json)**

<table><thead><tr><th>Name</th><th>Type</th><th>Description</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td><code>id</code></td><td>string</td><td>유저 이메일 주소</td><td>true</td></tr><tr><td><code>uuid</code></td><td>string</td><td>영상 uuid</td><td>true</td></tr></tbody></table>

**응답(json)**

<table><thead><tr><th width="126">Category</th><th>Name</th><th width="86">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>before_impact</code></td><td><code>stepping_foot_position</code></td><td>float</td><td>디딤발 위치. 공 중심에서 발목까지 공 1.5배 거리가 이상적. LeftAnkleBallDistance 참고. 만점 25점.</td></tr><tr><td></td><td><code>upper_pelvis_shoulder_y</code></td><td>float</td><td>백스윙 시 골반-어깨의 y축 각도가 0보다 커야 하고, 임팩트 시에는 0보다 작아야 함. PelvisShoulder(y) 참고. 만점 25점.</td></tr><tr><td></td><td><code>upper_left_shoulder_y</code></td><td>float</td><td>백스윙 시 어깨의 y축 관절각도는 60보다 커야 하고, 임팩트 이후에는 0보다 작아야 함. LeftShoulder(y) 참고. 만점 25점.</td></tr><tr><td></td><td><code>kick_right_knee_pelvis_x</code></td><td>float</td><td>백스윙 시 차는 쪽 무릎 x축의 각도는 -90도 정도, 피니쉬 시에는 80도 정도가 적당함. PelvisKnee(x) 참고. 만점 25점.</td></tr><tr><td></td><td><code>total</code></td><td>float</td><td>임팩트 이전 시점 점수 합. 만점 100점.</td></tr><tr><td><code>impact</code></td><td><code>stepping_knee_global_y</code></td><td>float</td><td>디딤발 각도. 디딤발이 지면에서 45도 각도로 기울어져 있어야 함. GLeftKnee(y) 참고. 만점 20점.</td></tr><tr><td></td><td><code>stepping_knee_x</code></td><td>float</td><td>디딤발 무릎 각도. 임팩트 시 무릎의 각도는 40~60도가 적절함. LeftKnee(x) 참고. 만점 20점.</td></tr><tr><td></td><td><code>upper_pelvis_shoulder_x</code></td><td>float</td><td>임팩트 시 무게중심이 앞으로 가야 함. 이때 골반-어깨 x축 각도가 0보다 커야 함. PelvisShoulder(x) 참고. 만점 20점.</td></tr><tr><td></td><td><code>impact_right_knee_global_y</code></td><td>float</td><td>임팩트 시 차는 발의 각도도 디딤발과 마찬가지로 지면과 45도 정도 되는 것이 적당함. GRightKnee(x) 참고. 만점 20점.</td></tr><tr><td></td><td><code>kick_right_hip_x</code></td><td>float</td><td>차는 발의 엉덩관절 각속도. 각속도가 빠를수록 빠른 킥임. RightHip(x) 참고. 만점 20점.</td></tr><tr><td></td><td><code>total</code></td><td>float</td><td>임팩트 시점 점수 합. 만점 100점.</td></tr><tr><td><code>after_impact</code></td><td><code>upper_pelvis_shoulder_y</code></td><td>float</td><td>백스윙 시 골반-어깨의 y축 각도가 0보다 커야 하고, 임팩트 시에는 0보다 작아야 함. PelvisShoulder(y) 참고. 만점 30점.</td></tr><tr><td></td><td><code>upper_left_shoulder_y</code></td><td>float</td><td>백스윙 시 어깨의 y축 관절각도는 60보다 커야 하고, 임팩트 이후에는 0보다 작아야 함. LeftShoulder(y) 참고. 만점 30점.</td></tr><tr><td></td><td><code>kick_right_knee_pelvis_x</code></td><td>float</td><td>백스윙 시 차는 쪽 무릎 x축의 각도는 -90도 정도, 피니쉬 시에는 80도 정도가 적당함. PelvisKnee(x) 참고. 만점 40점.</td></tr><tr><td></td><td><code>total</code></td><td>float</td><td>임팩트 이후 시점 점수 합. 만점 100점.</td></tr><tr><td><code>total_score</code></td><td></td><td>float</td><td>전체 합산 평균.</td></tr></tbody></table>

**요청 예시**

```json
http://115.94.164.253:15003/soccer/get-score/example@email.com/bc692864-0243-4d41-bce3-7658c92ef0c5
```

**응답 예시**

{% tabs %}
{% tab title="200" %}
```json
{
  'before_impact': {
    'stepping_foot_position': 25,
    'upper_pelvis_shoulder_y': 18.701,
    'upper_left_shoulder_y': 25,
    'kick_right_knee_pelvis_x': 14.0,
    'total': 82.701
  },
  'impact': {
    'stepping_knee_global_y': 0,
    'stepping_knee_x': 18.018,
    'upper_pelvis_shoulder_x': 0,
    'impact_right_knee_global_y': 0,
    'kick_right_hip_x': 20,
    'total': 38.018
  },
  'after_impact': {
    'upper_pelvis_shoulder_y': 0,
    'upper_left_shoulder_y': 50,
    'kick_right_knee_pelvis_x': 28.19,
    'total': 78.19
  },
  'total_score': 66.303
}

```
{% endtab %}
{% endtabs %}
