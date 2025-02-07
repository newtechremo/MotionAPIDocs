---
description: 완료된 달리기 분석 멘트를 요청하는 API입니다.
---

# 달리기 분석 멘트 요청

## 달리기 분석 멘트 요청

<mark style="color:red;">`GET`</mark> `http://115.94.164.253:15003/running/get-ment/{id}/{uuid}`

사용자 id(이메일), 분석된 비디오 uuid를 파라미터로 받아 달리기 분석 멘트 값을 리턴합니다.

**파라미터(json)**

<table><thead><tr><th>Name</th><th>Type</th><th>Description</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td><code>id</code></td><td>string</td><td>유저 이메일 주소</td><td>true</td></tr><tr><td><code>uuid</code></td><td>string</td><td>영상 uuid</td><td>true</td></tr></tbody></table>

**응답(json)**

<table><thead><tr><th width="134">Name</th><th width="86">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>good</code></td><td>list</td><td>2차원 리스트. 좋은 자세를 세 개 뽑아서 멘트를 리턴. [3, 3]의 사이즈를 가짐. 각 자세 별로 분리되어 있으며, 자세 리스트 내부에는 [시점 인덱스, 평가 항목 인덱스, 멘트 인덱스]가 있음. 현재는 알고리즘이 완성되지 않아 더미 데이터로 응답.</td></tr><tr><td><code>bad</code></td><td>list</td><td>2차원 리스트. 나쁜 자세를 세 개 뽑아서 멘트를 리턴. [3, 3]의 사이즈를 가짐. 각 자세 별로 분리되어 있으며, 자세 리스트 내부에는 [시점 인덱스, 평가 항목 인덱스, 멘트 인덱스]가 있음. 현재는 알고리즘이 완성되지 않아 더미 데이터로 응답.</td></tr></tbody></table>

**요청 예시**

<pre class="language-json"><code class="lang-json"><strong>http://115.94.164.253:15003/running/get-ment/example@email.com/bc692864-0243-4d41-bce3-7658c92ef0c5
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

<table><thead><tr><th width="88">시점(인덱스)</th><th width="110">평가 항목(인덱스)</th><th width="73">단위</th><th width="86">멘트 인덱스</th><th>멘트(한국어)</th><th>멘트(영어)</th></tr></thead><tbody><tr><td>컨택(1)</td><td>컨택 각도<br>(지면-발목 각도)(1)</td><td>각도(º)</td><td>1</td><td>발바닥으로 지면을 잘 차고있어요.</td><td>You are pushing off the ground well with the soles of your feet.</td></tr><tr><td></td><td></td><td></td><td>2</td><td>발 뒤꿈치부터 지면에 닿고있어요. 무릎 보호를 위해 발바닥 전체가 닿도록 해주세요.</td><td>You are landing on the ground with your heels first. To protect your knees, make sure your whole foot touches the ground.</td></tr><tr><td></td><td></td><td></td><td>3</td><td>발 앞꿈치부터 지면에 닿고있어요. 종아리 근육에 무리가 갈 수 있으니 발바닥 전체가 닿도록 해주세요.</td><td>You are landing on the ground with your toes first. To avoid strain on your calf muscles, make sure your whole foot touches the ground.</td></tr><tr><td><br></td><td>컨택 위치<br>(컨택 시 발 위치)(2)</td><td>%</td><td>1</td><td>체중심 바로 아래에서 지면을 차고있어요.</td><td>You are pushing off the ground directly under your center of gravity.</td></tr><tr><td></td><td></td><td></td><td>2</td><td>발을 너무 앞으로 뻗어서 지면에 닿고있어요. 감속을 피하기 위해 좀 더 몸 아래쪽에서 지면에 닿도록 해주세요.</td><td>You are reaching too far forward when touching the ground. To avoid deceleration, try to land closer to your body.</td></tr><tr><td></td><td></td><td></td><td>3</td><td>발이 너무 뒤에서 지면에 닿고있어요. 좀 더 몸 아래쪽에서 지면에 닿도록 해주세요.</td><td>You are landing too far behind your body. Try to touch the ground closer to your body.</td></tr><tr><td></td><td>반대쪽 대퇴부 각도(3)</td><td>각도(º)</td><td>1</td><td>반대쪽 다리가 충분히 앞으로 전진했어요.</td><td>The opposite leg is advancing forward sufficiently.</td></tr><tr><td></td><td></td><td></td><td>2</td><td>반대쪽 다리가 아직 앞으로 나오지 못했어요. 빠른 달리기를 위해 허벅지를 더 빠르게 앞으로 당겨 주세요.</td><td>The opposite leg has not moved forward enough. To run faster, pull your thigh forward more quickly.</td></tr><tr><td>도약(2)</td><td>뛰는쪽 팔꿈치 각도(1)</td><td>각도(º)</td><td>1</td><td>앞쪽 팔꿈치를 적절하게 굽히고 있어요.</td><td>Your front elbow is bent properly.</td></tr><tr><td></td><td></td><td></td><td>2</td><td>앞쪽 팔꿈치가 너무 펴져있어요. 좀 더 굽혀주세요.</td><td>The front elbow is too straight. Bend it a bit more.</td></tr><tr><td></td><td></td><td></td><td>3</td><td>앞쪽 팔꿈치가 너무 굽혀져있어요. 좀 더 펴주세요.</td><td>The front elbow is too bent. Straighten it a bit.</td></tr><tr><td></td><td>반대쪽 무릎각도(2)</td><td>각도(º)</td><td>1</td><td>반대쪽 다리가 적당하게 굽혀져서 컨택을 준비하고있어요.</td><td>The opposite leg is bent properly, preparing for contact.</td></tr><tr><td></td><td></td><td></td><td>2</td><td>반대쪽 다리가 너무 펴져있어요. 좀 더 굽혀서 감속이 일어나지 않게 해주세요.</td><td>The opposite leg is too straight. Bend it a bit more to avoid deceleration.</td></tr><tr><td></td><td></td><td></td><td>3</td><td>반대쪽 다리가 너무 굽혀져있어요. 좀 더 펴서 보폭을 늘려주세요.</td><td>The opposite leg is too bent. Straighten it a bit more to increase your stride.</td></tr><tr><td></td><td>반대쪽 팔꿈치 각도(3)</td><td>각도(º)</td><td>1</td><td>반대쪽 팔꿈치가 적절하게 펴져있어요.</td><td>The opposite elbow is extended properly.</td></tr><tr><td></td><td></td><td></td><td>2</td><td>반대쪽 팔꿈치가 너무 펴져있어요. 좀 더 굽혀주세요.</td><td>The opposite elbow is too straight. Bend it a bit more.</td></tr><tr><td></td><td></td><td></td><td>3</td><td>반대쪽 팔꿈치가 너무 굽혀져있어요. 좀 더 펴주세요.</td><td>The opposite elbow is too bent. Straighten it a bit more.</td></tr><tr><td></td><td>반대쪽 어깨 각도(4)</td><td>각도(º)</td><td>1</td><td>반대쪽 어깨를 적절하게 뒤로 펼치고 있어요.</td><td>The opposite shoulder is properly extended backward.</td></tr><tr><td></td><td></td><td></td><td>2</td><td>반대쪽 어깨가 뒤로 덜 펼쳐졌어요. 더 뒤로 펼쳐주세요.</td><td>The opposite shoulder is not extended backward enough. Extend it further back.</td></tr></tbody></table>
