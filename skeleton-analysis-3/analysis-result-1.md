---
description: 완료된 달리기 분석 결과를 요청하는 API입니다.
---

# 달리기 분석 점수 요청

## 달리기분석 점수요청

<mark style="color:red;">`GET`</mark> `http://115.94.164.253:15003/running/get-score/{id}/{uuid}`

사용자 id(이메일), 분석된 비디오 uuid를 파라미터로 받아 달리기분석 점수 값을 리턴합니다.

**파라미터(json)**

<table><thead><tr><th>Name</th><th>Type</th><th>Description</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td><code>id</code></td><td>string</td><td>유저 이메일 주소</td><td>true</td></tr><tr><td><code>uuid</code></td><td>string</td><td>영상 uuid</td><td>true</td></tr></tbody></table>

**응답(json)**

\*항목 별 만점은 10점입니다.

<table><thead><tr><th width="126">Category</th><th width="157">Name</th><th width="86">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>right_contact</code></td><td><code>ankle_location</code></td><td>float</td><td>컨택 시 발 위치는 몸 중심보다 뒤로 가있어야 함. 해당 값은 발목 위치에서 몸 중심 위치를 뺀 값. RightAnkleCoordX - CenterCoordX 참고.  값이 50보다 크거나 같으면 만점. 그렇지 않으면 0.1당 1점씩 차감. 만점 40점.</td></tr><tr><td></td><td><code>ankle_angle</code></td><td>float</td><td>컨택 시 발목 각도가 0도에 가까워야 함. RightAnkle(z) 참고. 값이 0~6 사이면 만점. 그렇지 않으면 1당 1점씩 차감. 만점 30점.</td></tr><tr><td></td><td><code>opposite_thigh_angle</code></td><td>float</td><td>컨택 시 반대쪽 다리의 대퇴부 각도는 지면과 90도 이상. GLeftHip(z) 참고. 값이 90 이상이면 만점. 그렇지 않으면 1당 1점씩 차감. 만점 30점.</td></tr><tr><td></td><td><code>total</code></td><td>float</td><td>오른 발 컨택 시점 점수 합. 만점 100점.</td></tr><tr><td><code>left_contact</code></td><td><code>ankle_location</code></td><td>float</td><td>컨택 시 발 위치는 몸 중심보다 뒤로 가있어야 함. 해당 값은 발목 위치에서 몸 중심 위치를 뺀 값. LeftAnkleCoordX - CenterCoordX 참고. 값이 50보다 크거나 같으면 만점. 그렇지 않으면 0.1당 1점씩 차감. 만점 40점.</td></tr><tr><td></td><td><code>ankle_angle</code></td><td>float</td><td>컨택 시 발목 각도가 0도에 가까워야 함. LeftAnkle(z) 참고. 값이 0~6 사이면 만점. 그렇지 않으면 1당 1점씩 차감. 만점 30점.</td></tr><tr><td></td><td><code>opposite_thigh_angle</code></td><td>float</td><td>컨택 시 반대쪽 다리의 대퇴부 각도는 지면과 90도 이상. GRightHip(z) 참고. 값이 90 이상이면 만점. 그렇지 않으면 1당 1점씩 차감. 만점 30점.</td></tr><tr><td></td><td><code>total</code></td><td>float</td><td>왼 발 컨택 시점 점수 합. 만점 100점.</td></tr><tr><td><code>right_off</code></td><td><code>opposite_knee_angle</code></td><td>float</td><td>오프 시 앞쪽 다리 무릎 각도 90도 이상. LeftKnee(x) 참고. 값이 90 이상이면 만점. 그렇지 않으면 1당 1점씩 차감. 만점 25점.</td></tr><tr><td></td><td><code>opposite_elbow_angle</code></td><td>float</td><td>오프 시 뒤쪽 팔꿈치 각도 110도. LeftElbow(x) 참고. 값이 107~113이면 만점. 그렇지 않으면 1당 1점씩 차감. 만점 25점.</td></tr><tr><td></td><td><code>elbow_angle</code></td><td>list</td><td>오프 시 앞쪽 팔꿈치 각도 90도. RightElbow(x) 참고. 값이 87~93이면 만점. 그렇지 않으면 1당 1점씩 차감. 만점 25점.</td></tr><tr><td></td><td><code>opposite_shoulder_angle</code></td><td>float</td><td>오프 시 뒤쪽 상완 지면 수직선과 80도. LeftShoulder(x) 참고. 값이 47~53이면 만점. 그렇지 않으면 1당 1점씩 차감. 만점 25점.</td></tr><tr><td></td><td><code>total</code></td><td>float</td><td>오른 발 오프 시점 점수 합. 만점 100점.</td></tr><tr><td><code>left_off</code></td><td><code>opposite_knee_angle</code></td><td>float</td><td>오프 시 앞쪽 다리 무릎 각도 90도 이상. RightKnee(x) 참고. 값이 90 이상이면 만점. 그렇지 않으면 1당 1점씩 차감. 만점 25점.</td></tr><tr><td></td><td><code>opposite_elbow_angle</code></td><td>float</td><td>오프 시 뒤쪽 팔꿈치 각도 110도. RightElbow(x) 참고. 값이 107~113이면 만점. 그렇지 않으면 1당 1점씩 차감. 만점 25점.</td></tr><tr><td></td><td><code>elbow_angle</code></td><td>float</td><td>오프 시 앞쪽 팔꿈치 각도 90도. LeftElbow(x) 참고. 값이 87~93이면 만점. 그렇지 않으면 1당 1점씩 차감. 만점 25점.</td></tr><tr><td></td><td><code>opposite_shoulder_angle</code></td><td>float</td><td>오프 시 뒤쪽 상완 지면 수직선과 80도. RightShoulder(x) 참고. 값이 47~53이면 만점. 그렇지 않으면 1당 1점씩 차감. 만점 25점.</td></tr><tr><td></td><td><code>total</code></td><td>float</td><td>왼 발 오프 시점 점수 합. 만점 100점.</td></tr><tr><td><code>total_score</code></td><td></td><td>float</td><td>전체 합산 평균.</td></tr></tbody></table>

**요청 예시**

```json
http://115.94.164.253:15003/running/get-score/example@email.com/bc692864-0243-4d41-bce3-7658c92ef0c5
```

**응답 예시**

{% tabs %}
{% tab title="200" %}
```json
{
  'right_contact': {
    'ankle_location': 39.21,
    'ankle_angle': 28.788,
    'opposite_thigh_angle': 0,
    'total': 67.998
  },
  'left_contact': {
    'ankle_location': 40.0,
    'ankle_angle': 29.563,
    'opposite_thigh_angle': 0,
    'total': 69.563
  },
  'right_off': {
    'opposite_knee_angle': 22.348,
    'opposite_elbow_angle': 0,
    'elbow_angle': 23.513,
    'opposite_shoulder_angle': 0,
    'total': 45.861
  },
  'left_off': {
    'opposite_knee_angle': 13.03,
    'opposite_elbow_angle': 18.621,
    'elbow_angle': 0,
    'opposite_shoulder_angle': 0,
    'total': 31.651
  },
  'total_score': 53.768
}
```
{% endtab %}
{% endtabs %}
