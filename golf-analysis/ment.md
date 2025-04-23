---
description: 완료된 골프 분석 멘트를 요청하는 API입니다.
---

# 골프 분석 멘트 요청

## 골프 분석 멘트 요청

<mark style="color:red;">`GET`</mark> `http://115.94.164.253:15003/golf/get-ment/{id}/{uuid}`

사용자 id(이메일), 분석된 비디오 uuid를 파라미터로 받아 골프분석 멘트 값을 리턴합니다.

**파라미터(json)**

<table><thead><tr><th>Name</th><th>Type</th><th>Description</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td><code>id</code></td><td>string</td><td>유저 이메일 주소</td><td>true</td></tr><tr><td><code>uuid</code></td><td>string</td><td>영상 uuid</td><td>true</td></tr></tbody></table>

**응답(json)**

<table><thead><tr><th width="134">Name</th><th width="86">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>good</code></td><td>list</td><td>2차원 리스트. 좋은 자세를 세 개 뽑아서 멘트를 리턴. [3, 3]의 사이즈를 가짐. 각 자세 별로 분리되어 있으며, 자세 리스트 내부에는 [시점 인덱스, 평가 항목 인덱스, 멘트 인덱스]가 있음. 현재는 알고리즘이 완성되지 않아 더미 데이터로 응답.</td></tr><tr><td><code>bad</code></td><td>list</td><td>2차원 리스트. 나쁜 자세를 세 개 뽑아서 멘트를 리턴. [3, 3]의 사이즈를 가짐. 각 자세 별로 분리되어 있으며, 자세 리스트 내부에는 [시점 인덱스, 평가 항목 인덱스, 멘트 인덱스]가 있음. 현재는 알고리즘이 완성되지 않아 더미 데이터로 응답.</td></tr></tbody></table>

**요청 예시**

<pre class="language-json"><code class="lang-json"><strong>http://115.94.164.253:15003/golf/get-ment/example@email.com/bc692864-0243-4d41-bce3-7658c92ef0c5
</strong></code></pre>

**응답 예시**

{% tabs %}
{% tab title="200" %}
```json
{
  'good': [
    [
      0,
      1,
      1
    ],
    [
      1,
      0,
      1
    ],
    [
      2,
      2,
      1
    ]
  ],
  'bad': [
    [
      2,
      1,
      2
    ],
    [
      1,
      0,
      2
    ],
    [
      1,
      2,
      2
    ]
  ]
}
```
{% endtab %}
{% endtabs %}

**멘트 상세**

<table><thead><tr><th width="116">시점(인덱스)</th><th width="119">평가 항목(인덱스)</th><th width="70">단위</th><th width="113">멘트 인덱스</th><th>멘트(한국어)</th><th>멘트(영어)</th></tr></thead><tbody><tr><td>어드레스(1)</td><td>어깨 기울기(1)</td><td>각도</td><td>1</td><td>기울기가 잘 유지돼요!</td><td>The tilt is well maintained!</td></tr><tr><td></td><td></td><td></td><td>2</td><td>기울기가 너무 커요! 조금 줄여볼까요?</td><td>The tilt is too steep! Shall we reduce it a bit?</td></tr><tr><td></td><td></td><td></td><td>3</td><td>오른쪽이 높은건 좋지 않아요.. 조금 각도를 바꿔볼까요?</td><td>The right side being high is not good.. Shall we adjust the angle a little?</td></tr><tr><td></td><td>스탠스(2)</td><td>단위 없음</td><td>1</td><td>스탠스가 딱 좋아요</td><td>The stance is just right.</td></tr><tr><td></td><td></td><td></td><td>2</td><td>스탠스가 너무 좁아요. 조금 넓혀볼까요?</td><td>The stance is too narrow. Shall we widen it a bit?</td></tr><tr><td></td><td></td><td></td><td>3</td><td>스탠스가 너무 넓어요. 조금 좁혀볼까요?</td><td>The stance is too wide. Shall we narrow it a bit?</td></tr><tr><td></td><td>상체 기울임 정도(3)</td><td>단위 없음</td><td>1</td><td>상체 기울임이 적당해요!</td><td>Your upper body tilt is just right!</td></tr><tr><td></td><td></td><td></td><td>2</td><td>상체 기울임이 부족해요. 상체를 더 기울여 볼까요?</td><td>Your upper body tilt is insufficient. Shall we try tilting it a bit more?</td></tr><tr><td></td><td></td><td></td><td>3</td><td>상체 기울임이 너무 커요. 상체를 살짝 세워 볼까요?</td><td>Your upper body tilt is too much. Shall we try straightening up a bit?</td></tr><tr><td>테이크백(2)</td><td>왼어깨 회전(1)</td><td>각도</td><td>1</td><td>어깨 회전이 딱 좋아요! 이대로 유지해볼까요?</td><td>The shoulder rotation is just right! Shall we maintain it like this?</td></tr><tr><td></td><td></td><td></td><td>2</td><td>어깨 회전이 너무 많아요.. 조금 줄여볼까요?</td><td>The shoulder rotation is too much.. Shall we reduce it a bit?</td></tr><tr><td></td><td></td><td></td><td>3</td><td>어깨를 조금 더 회전해볼까요?</td><td>Shall we rotate the shoulders a little more?</td></tr><tr><td></td><td>왼팔 펴짐(2)</td><td>각도</td><td>1</td><td>왼쪽 팔이 잘 펴져있어요! Good!</td><td>The left arm is well extended! Good!</td></tr><tr><td></td><td></td><td></td><td>2</td><td>왼팔이 너무 펴져있어요! 자연스럽게 구부려볼까요?</td><td>The left arm is too straight! Shall we bend it a little naturally?</td></tr><tr><td></td><td></td><td></td><td>3</td><td>왼팔이 다소 구부러져 있어요! 쭉 펴볼까요?</td><td>The left arm is a bit bent! Shall we extend it fully?</td></tr><tr><td></td><td>오른팔 펴짐(3)</td><td>각도</td><td>1</td><td>오른쪽 팔이 잘 펴져있어요! Good!</td><td>The right arm is well extended! Good!</td></tr><tr><td></td><td></td><td></td><td>2</td><td>오른팔이 너무 펴져있어요! 자연스럽게 구부려볼까요?</td><td>The right arm is too straight! Shall we bend it a little naturally?</td></tr><tr><td></td><td></td><td></td><td>3</td><td>오른팔이 다소 구부러져 있어요! 쭉 펴볼까요?</td><td>The right arm is a bit bent! Shall we extend it fully?</td></tr><tr><td></td><td>우측 골반 회전(4)</td><td>각도</td><td>1</td><td>골반 회전이 딱 적당해요! Good!</td><td>The pelvis rotation is just right! Good!</td></tr><tr><td></td><td></td><td></td><td>2</td><td>골반 회전이 다소 부족해요! 조금 더 골반을 움직여볼까요?</td><td>The pelvis rotation is a bit lacking! Shall we move the pelvis a bit more?</td></tr><tr><td></td><td></td><td></td><td>3</td><td>골반 회전이 너무 과해요! 골반 가동범위를 조금 줄여볼까요?</td><td>The pelvis rotation is too much! Shall we reduce the pelvis range of motion?</td></tr><tr><td>백스윙(3)</td><td>머리위치(1)</td><td>%</td><td>1</td><td>머리 위치가 잘 고정되어 있어요!</td><td>Your head position is well stabilized!</td></tr><tr><td></td><td></td><td></td><td>2</td><td>머리 위치가 너무 위에 있어요!</td><td>Your head position is too high!</td></tr><tr><td></td><td></td><td></td><td>3</td><td>머리 위치가 너무 아래에 있어요!</td><td>Your head position is too low!</td></tr><tr><td></td><td>왼쪽 어깨 회전(2)</td><td>%</td><td>1</td><td>어깨 회전이 딱 적당해요! Good!</td><td>The shoulder rotation is just perfect! Good!</td></tr><tr><td></td><td></td><td></td><td>2</td><td>어깨 회전이 너무 많아요.. 조금 줄여볼까요?</td><td>The shoulder rotation is too much.. Shall we reduce it a bit?</td></tr><tr><td></td><td></td><td></td><td>3</td><td>어깨를 조금 더 회전해볼까요?</td><td>Shall we rotate the shoulders a little more?</td></tr><tr><td></td><td>왼팔 펴짐(3)</td><td>각도</td><td>1</td><td>왼쪽 팔이 잘 펴져있어요! Good!</td><td>The left arm is well extended! Good!</td></tr><tr><td></td><td></td><td></td><td>2</td><td>왼팔이 너무 펴져있어요! 자연스럽게 구부려볼까요?</td><td>The left arm is too straight! Shall we bend it a little naturally?</td></tr><tr><td></td><td></td><td></td><td>3</td><td>왼팔이 다소 구부러져 있어요! 쭉 펴볼까요?</td><td>The left arm is a bit bent! Shall we extend it fully?</td></tr><tr><td>백스윙탑(4)</td><td>리버스스파인(1)</td><td>%</td><td>1</td><td>리버스스파인이 발생하지 않았어요! Good!</td><td>There's no reverse spine tilt! Good job!</td></tr><tr><td></td><td></td><td></td><td>2</td><td>몸이 너무 뒤로 젖혀지거나 앞으로 굽혀졌어요!</td><td>Your body is leaning too far back or bending too far forward!</td></tr><tr><td></td><td>오른 다리 펴짐(2)</td><td>각도</td><td>1</td><td>오른쪽 다리가 잘 펴져있어요! Good!</td><td>The right leg is well extended! Good!</td></tr><tr><td></td><td></td><td></td><td>2</td><td>오른쪽 다리가 다소 구부러져 있어요! 쭉 펴볼까요?</td><td>The right leg is a bit bent! Shall we extend it fully?</td></tr><tr><td></td><td>머리 위치(3)</td><td>%</td><td>1</td><td>머리 위치가 잘 고정되어 있어요!</td><td>Your head position is well stabilized!</td></tr><tr><td></td><td></td><td></td><td>2</td><td>머리 위치가 너무 위에 있어요!</td><td>Your head position is too high!</td></tr><tr><td></td><td></td><td></td><td>3</td><td>머리 위치가 너무 아래에 있어요!</td><td>Your head position is too low!</td></tr><tr><td></td><td>우측 골반 회전(4)</td><td>각도</td><td>1</td><td>골반 회전이 딱 적당해요! Good!</td><td>The pelvis rotation is just right! Good!</td></tr><tr><td></td><td></td><td></td><td>2</td><td>골반 회전이 다소 부족해요! 조금 더 골반을 움직여볼까요?</td><td>The pelvis rotation is a bit lacking! Shall we move the pelvis a bit more?</td></tr><tr><td></td><td></td><td></td><td>3</td><td>골반 회전이 너무 과해요! 골반 가동범위를 조금 줄여볼까요?</td><td>The pelvis rotation is too much! Shall we reduce the pelvis range of motion?</td></tr><tr><td></td><td>무게중심(5)</td><td>각도</td><td>1</td><td>체중이동이 너무 좋네요! 자연스러워요!</td><td>The weight shift is very good! Natural!</td></tr><tr><td></td><td></td><td></td><td>2</td><td>체중이 오른발쪽에 남아있어요. 자연스럽게 넘겨볼까요?</td><td>The weight is remaining on the right foot. Shall we shift it naturally?</td></tr><tr><td></td><td></td><td></td><td>3</td><td>스웨이가 발생했어요. 조금 오른발 쪽에 체중을 남겨볼까요?</td><td>There is a sway happening. Shall we leave some weight on the right foot?</td></tr><tr><td>다운스윙(5)</td><td>무게중심(1)</td><td>각도</td><td>1</td><td>체중이동이 너무 좋네요! 자연스러워요!</td><td>The weight shift is very good! Natural!</td></tr><tr><td></td><td></td><td></td><td>2</td><td>체중이 오른발쪽에 남아있어요. 자연스럽게 넘겨볼까요?</td><td>The weight is remaining on the right foot. Shall we shift it naturally?</td></tr><tr><td></td><td></td><td></td><td>3</td><td>스웨이가 발생했어요. 조금 오른발 쪽에 체중을 남겨볼까요?</td><td>There is a sway happening. Shall we leave some weight on the right foot?</td></tr><tr><td></td><td>오른팔꿈치 위치(2)</td><td>각도</td><td>1</td><td>오른팔꿈치가 왼팔꿈치보다 아래에 있어요! Good!</td><td>Your right elbow is below your left elbow! Good job!</td></tr><tr><td></td><td></td><td></td><td>2</td><td>오른팔꿈치를 더 내려 볼까요?</td><td>Shall we lower your right elbow a bit more?</td></tr><tr><td></td><td>오른팔 각도(3)</td><td>각도</td><td>1</td><td>오른팔이 몸과 잘 붙어 있어요!</td><td>Your right arm is well aligned with your body!</td></tr><tr><td></td><td></td><td></td><td>2</td><td>오른팔이 몸과 떨어져 있어요! 팔을 몸에 더 붙여 볼까요?</td><td>Your right arm is away from your body! Shall we try bringing it closer?</td></tr><tr><td>임팩트(6)</td><td>머리위치(1)</td><td>%</td><td>1</td><td>머리 위치가 잘 고정되어 있어요!</td><td>Your head position is well stabilized!</td></tr><tr><td></td><td></td><td></td><td>2</td><td>머리 위치가 너무 위에 있어요!</td><td>Your head position is too high!</td></tr><tr><td></td><td></td><td></td><td>3</td><td>머리 위치가 너무 아래에 있어요!</td><td>Your head position is too low!</td></tr><tr><td></td><td>행잉백(2)</td><td>%</td><td>1</td><td>무게 중심이 잘 이동되었어요!</td><td>Your weight shift is well executed!</td></tr><tr><td></td><td></td><td></td><td>2</td><td>무게 중심이 아직 오른쪽에 많이 남아 있어요! 더 이동해 볼까요?</td><td>Your weight is still mostly on the right side! Shall we try shifting it more?</td></tr><tr><td></td><td>왼팔 펴짐(3)</td><td>각도</td><td>1</td><td>왼쪽 팔이 잘 펴져있어요! Good!</td><td>The left arm is well extended! Good!</td></tr><tr><td></td><td></td><td></td><td>2</td><td>왼팔이 너무 펴져있어요! 자연스럽게 구부려볼까요?</td><td>The left arm is too straight! Shall we bend it a little naturally?</td></tr><tr><td></td><td></td><td></td><td>3</td><td>왼팔이 다소 구부러져 있어요! 쭉 펴볼까요?</td><td>The left arm is a bit bent! Shall we extend it fully?</td></tr><tr><td></td><td>오른팔 펴짐(4)</td><td>각도</td><td>1</td><td>오른쪽 팔이 잘 펴져있어요! Good!</td><td>The right arm is well extended! Good!</td></tr><tr><td></td><td></td><td></td><td>2</td><td>오른팔이 너무 펴져있어요! 자연스럽게 구부려볼까요?</td><td>The right arm is too straight! Shall we bend it a little naturally?</td></tr><tr><td></td><td></td><td></td><td>3</td><td>오른팔이 다소 구부러져 있어요! 쭉 펴볼까요?</td><td>The right arm is a bit bent! Shall we extend it fully?</td></tr><tr><td>팔로우스루(7)</td><td>왼다리 수직(1)</td><td>각도</td><td>1</td><td>왼쪽다리가 잘 펴졌어요! Good!</td><td>The left leg is well extended! Good!</td></tr><tr><td></td><td></td><td></td><td>2</td><td>왼쪽 다리가 살짝 구부러져 있어요. 쭉 펴볼까요?</td><td>The left leg is slightly bent. Shall we extend it fully?</td></tr><tr><td></td><td></td><td></td><td>3</td><td>왼쪽 다리가 다소 구부러져 있어요! 쭉 펴볼까요?</td><td>The left leg is a bit bent. Shall we extend it fully?</td></tr><tr><td></td><td>치킨윙(2)</td><td>각도</td><td>1</td><td>왼쪽 팔이 잘 펴져있어요! Good!</td><td>The left arm is well extended! Good!</td></tr><tr><td></td><td></td><td></td><td>2</td><td>왼팔이 너무 펴져있어요! 자연스럽게 구부려볼까요?</td><td>The left arm is too straight! Shall we bend it a little naturally?</td></tr><tr><td></td><td></td><td></td><td>3</td><td>왼팔이 다소 구부러져 있어요! 쭉 펴볼까요?</td><td>The left arm is a bit bent! Shall we extend it fully?</td></tr><tr><td></td><td>무게중심 이동(3)</td><td>%</td><td>1</td><td>체중이동이 아주 자연스럽네요! Good!</td><td>The weight shift is very natural! Good!</td></tr><tr><td></td><td></td><td></td><td>2</td><td>무게중심이 아직 오른발에 남아있어요. 자연스럽게 넘겨볼까요?</td><td>The weight is still on the right foot. Shall we shift it naturally?</td></tr><tr><td></td><td></td><td></td><td>3</td><td>체중이동이 너무 많이 진행되었어요. 조금 남겨볼까요?</td><td>The weight shift has progressed too much. Shall we leave a bit behind?</td></tr><tr><td>피니쉬(8)</td><td>무게중심(1)</td><td>%</td><td>1</td><td>왼쪽 발목과 오른쪽 골반의 정렬이 딱 좋아요! Good!</td><td>The alignment of the left ankle and right pelvis is just right! Good!</td></tr><tr><td></td><td></td><td></td><td>2</td><td>왼쪽 발목과 오른쪽 골반의 정렬에 조금 신경 써볼까요?</td><td>Shall we pay a little attention to the alignment of the left ankle and right pelvis?</td></tr><tr><td></td><td>오른발 회전 각도(2)</td><td>각도</td><td>1</td><td>오른발의 각도가 딱 좋아요! 이대로 계속 쳐 볼까요?</td><td>The angle of the right foot is perfect! Shall we keep hitting like this?</td></tr><tr><td></td><td></td><td></td><td>2</td><td>오른쪽 발 각도가 다소 아쉬워요! 오른발 각도에 신경써볼까요?</td><td>The right foot angle is a bit off! Shall we pay attention to the right foot angle?</td></tr><tr><td></td><td>왼발 고정(3)</td><td>각도</td><td>1</td><td>왼발이 안정적으로 고정되어있어요!</td><td>The left foot is stably fixed!</td></tr><tr><td></td><td></td><td></td><td>2</td><td>왼발이 더 고정되어야 해요! 왼발 고정에 더 신경써볼까요?</td><td>The left foot needs to be more fixed! Shall we pay more attention to fixing the left foot?</td></tr></tbody></table>
