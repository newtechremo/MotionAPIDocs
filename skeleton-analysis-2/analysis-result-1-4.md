---
description: 완료된 축구 분석 멘트를 요청하는 API입니다.
---

# 축구 분석 멘트 요청

## 축구 분석 멘트 요청

<mark style="color:red;">`GET`</mark> `http://115.94.164.253:15003/soccer/get-ment/{id}/{uuid}`

사용자 id(이메일), 분석된 비디오 uuid를 파라미터로 받아 축구 분석 멘트 값을 리턴합니다.

**파라미터(json)**

<table><thead><tr><th>Name</th><th>Type</th><th>Description</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td><code>id</code></td><td>string</td><td>유저 이메일 주소</td><td>true</td></tr><tr><td><code>uuid</code></td><td>string</td><td>영상 uuid</td><td>true</td></tr></tbody></table>

**응답(json)**

<table><thead><tr><th width="134">Name</th><th width="86">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>good</code></td><td>list</td><td>2차원 리스트. 좋은 자세를 세 개 뽑아서 멘트를 리턴. [3, 3]의 사이즈를 가짐. 각 자세 별로 분리되어 있으며, 자세 리스트 내부에는 [시점 인덱스, 평가 항목 인덱스, 멘트 인덱스]가 있음. 현재는 알고리즘이 완성되지 않아 더미 데이터로 응답.</td></tr><tr><td><code>bad</code></td><td>list</td><td>2차원 리스트. 나쁜 자세를 세 개 뽑아서 멘트를 리턴. [3, 3]의 사이즈를 가짐. 각 자세 별로 분리되어 있으며, 자세 리스트 내부에는 [시점 인덱스, 평가 항목 인덱스, 멘트 인덱스]가 있음. 현재는 알고리즘이 완성되지 않아 더미 데이터로 응답.</td></tr></tbody></table>

**요청 예시**

<pre class="language-json"><code class="lang-json"><strong>http://115.94.164.253:15003/soccer/get-ment/example@email.com/bc692864-0243-4d41-bce3-7658c92ef0c5
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

<table><thead><tr><th width="114">시점(인덱스)</th><th width="105">평가 항목(인덱스)</th><th width="80">단위</th><th width="111">멘트 인덱스</th><th>멘트(한국어)</th><th>멘트(영어)</th></tr></thead><tbody><tr><td>준비 및 접근(1)</td><td>디딤발 위치 (공과의 거리)(1)</td><td>-</td><td>1</td><td>디딤발이 공과 적절한 거리에 위치했습니다.</td><td>The planting foot is positioned at an appropriate distance from the ball.</td></tr><tr><td></td><td></td><td></td><td>2</td><td>디딤발이 공과 너무 멀리 떨어졌습니다. 공에 좀더 가깝게 디딤발을 놓아보세요.</td><td>The planting foot is too far from the ball. Place your planting foot closer to the ball.</td></tr><tr><td></td><td></td><td></td><td>3</td><td>디딤발이 공에 너무 가깝습니다. 공에서 좀 더 멀리 디딤발을 놓아보세요.</td><td>The planting foot is too close to the ball. Place your planting foot farther away from the ball.</td></tr><tr><td></td><td>어깨 회전 (골반-어깨 각도)(2)</td><td>각도(º)</td><td>1</td><td>상체가 적절하게 열려있습니다.</td><td>The upper body is properly open.</td></tr><tr><td></td><td></td><td></td><td>2</td><td>상체가 열리지 않았습니다. 공을 차기 전 상체를 좀 더 열어주세요.</td><td>The upper body is not open. Open your upper body more before kicking the ball.</td></tr><tr><td></td><td>반대팔 어깨 각도 (ab/adduction)(3)</td><td>각도(º)</td><td>1</td><td>반대쪽 팔이 적절하게 벌려졌습니다.</td><td>The opposite arm is properly extended.</td></tr><tr><td></td><td></td><td></td><td>2</td><td>반대쪽 팔이 벌려지지 않았습니다. 공을 차기 전 팔을 벌려 상체를 열어주세요</td><td>The opposite arm is not extended. Extend your arm to open your upper body before kicking the ball.</td></tr><tr><td></td><td>차는 발 높이 - 백스윙(4)</td><td>각도(º)</td><td>1</td><td>백스윙 발높이가 적당합니다.</td><td>The height of the backswing leg is appropriate.</td></tr><tr><td></td><td></td><td></td><td>2</td><td>백스윙 발높이가 너무 높습니다. 뒤로 차는 힘을 조금 빼주세요.</td><td>The height of the backswing leg is too high. Reduce the power of the backward swing.</td></tr><tr><td></td><td></td><td></td><td>3</td><td>백스윙이 너무 낮습니다. 좀 더 높이 들어올려주세요.</td><td>The backswing is too low. Lift it higher.</td></tr><tr><td>임팩트(2)</td><td>디딤발 각도 (지면과의 각도)(1)</td><td>각도(º)</td><td>1</td><td>디딤발이 옆으로 잘 기울어져 있습니다.</td><td>The planting foot is well tilted to the side.</td></tr><tr><td></td><td></td><td></td><td>2</td><td>디딤발이 너무 서있습니다. 좀 더 기울여주세요.</td><td>The planting foot is too upright. Tilt it more.</td></tr><tr><td></td><td></td><td></td><td>3</td><td>디딤발이 너무 기울어져있습니다. 좀 더 세워주세요.</td><td>The planting foot is too tilted. Straighten it a bit.</td></tr><tr><td></td><td>디딤발 무릎각도(2)</td><td>각도(º)</td><td>1</td><td>디딤발이 적당히 굽혀졌습니다.</td><td>The planting foot is appropriately flexed.</td></tr><tr><td></td><td></td><td></td><td>2</td><td>디딤발이 굽혀지지 않았습니다. 좀 더 굽혀주세요.</td><td>The planting foot is not flexed. Bend it more.</td></tr><tr><td></td><td></td><td></td><td>3</td><td>디딤발이 너무 굽혀졌습니다. 좀 더 펴주세요.</td><td>The planting foot is too flexed. Straighten it a bit.</td></tr><tr><td></td><td>상체 기울임 (전방으로)(3)</td><td>각도(º)</td><td>1</td><td>상체를 앞으로 적당히 숙인 상태로 슈팅했습니다.</td><td>You shot the ball while bending the upper body forward appropriately.</td></tr><tr><td></td><td></td><td></td><td>2</td><td>슈팅 시 상체를 숙이지 않았습니다. 상체를 앞으로 숙인채로 슈팅해주세요.</td><td>You did not bend your upper body when shooting. Shoot while bending your upper body forward.</td></tr><tr><td></td><td></td><td></td><td>3</td><td>상체가 너무 숙여진 상태로 슈팅했습니다. 상체를 좀 더 세워주세요.</td><td>You shot the ball with your upper body bent too much. Straighten your upper body a bit.</td></tr><tr><td></td><td>차는 발 각도 (지면과의 각도)(4)</td><td>각도(º)</td><td>1</td><td>차는발이 옆으로 잘 기울어져 있습니다.</td><td>The kicking foot is well tilted to the side.</td></tr><tr><td></td><td></td><td></td><td>2</td><td>차는발이 너무 서있습니다. 좀 더 기울여주세요.</td><td>The kicking foot is too upright. Tilt it more.</td></tr><tr><td></td><td></td><td></td><td>3</td><td>차는발이 너무 기울어져있습니다. 좀 더 세워주세요.</td><td>The kicking foot is too tilted. Straighten it a bit.</td></tr><tr><td></td><td>엉덩관절 각속도(5)</td><td>각속도(º/sec)</td><td>1</td><td>차는발의 속도가 충분히 빠릅니다.</td><td>The speed of the kicking foot is sufficiently fast.</td></tr><tr><td></td><td></td><td></td><td>2</td><td>차는발이 너무 느립니다. 더 빠르게 차주세요.</td><td>The kicking foot is too slow. Kick faster.</td></tr><tr><td>피니쉬(3)</td><td>어깨 회전 (골반-어깨 각도)(1)</td><td>각도(º)</td><td>1</td><td>상체가 잘 모였습니다.</td><td>The upper body is well gathered.</td></tr><tr><td></td><td></td><td></td><td>2</td><td>상체가 잘 모이지 않았습니다. 공을 차면서 상체를 모아주세요.</td><td>The upper body is not well gathered. Gather your upper body when kicking the ball.</td></tr><tr><td></td><td>반대팔 어깨 각도 (ab/adduction)(2)</td><td>각도(º)</td><td>1</td><td>반대쪽 팔이 적절하게 굽혀졌습니다.</td><td>The opposite arm is appropriately bent.</td></tr><tr><td></td><td></td><td></td><td>2</td><td>반대쪽 팔이 굽혀지지 않았습니다. 공을 차면서 팔을 굽혀 상체를 모아주세요</td><td>The opposite arm is not bent. Bend your arm while kicking to gather the upper body.</td></tr><tr><td></td><td>차는 발 높이 - 피니시(3)</td><td>각도(º)</td><td>1</td><td>공을 찬 후 발높이가 적당합니다.</td><td>The height of the foot after kicking the ball is appropriate.</td></tr><tr><td></td><td></td><td></td><td>2</td><td>공을 찬 후 발이 너무 높습니다. 좀 더 낮게 마무리 해 주세요.</td><td>The foot is too high after kicking the ball. Finish with a lower foot.</td></tr><tr><td></td><td></td><td></td><td>3</td><td>공을 찬 후 발이 너무 낮습니다. 좀 더 높게 들어주세요.</td><td>The foot is too low after kicking the ball. Lift it higher.</td></tr></tbody></table>
