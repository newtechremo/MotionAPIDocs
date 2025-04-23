---
description: 완료된 ROM 분석 결과를 요청하는 API입니다.
---

# ROM 비디오 결과 요청

### ROM 비디오 결과 요청

<mark style="color:red;">`GET`</mark> `http://115.94.164.253:15003/ROM/get-result/{id}/{uuid}`

사용자 id(이메일), 분석된 비디오 uuid를 파라미터로 받아 ROM 분석 결과 값을 리턴합니다.



**파라미터(json)**

<table><thead><tr><th>Name</th><th>Type</th><th>Description</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td><code>id</code></td><td>string</td><td>유저 이메일 주소</td><td>true</td></tr><tr><td><code>uuid</code></td><td>string</td><td>영상 uuid</td><td>true</td></tr></tbody></table>



**응답(json)**

**\***&#xC608;시 스키마(motionDetail = neckLateralFlexion)

<table><thead><tr><th width="164">Name</th><th width="88">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>state</code></td><td>int</td><td>성공 시 True, 실패 시 False.</td></tr><tr><td><code>message</code></td><td>string</td><td>성공 또는 실패 관련 안내 메세지.</td></tr><tr><td><code>uuid</code></td><td>string</td><td>영상 uuid.</td></tr><tr><td><code>motionDetail</code></td><td>string</td><td>파라미터로 전달 받았던 영상 종류.</td></tr><tr><td><code>neckLeftLateralFlexionAngle</code></td><td>float</td><td>왼쪽으로 목을 굽혔을 때 최대 각도.</td></tr><tr><td><code>neckRightLateralFlexionAngle</code></td><td>float</td><td>오른쪽으로 목을 굽혔을 때 최대 각도.</td></tr><tr><td><code>neckLeftLateralFlexionIndex</code></td><td>int</td><td>왼쪽으로 목을 굽혔을 때 최대 각도 시점의 인덱스.</td></tr><tr><td><code>neckRightLateralFlexionIndex</code></td><td>int</td><td>오른쪽으로 목을 굽혔을 때 최대 각도 시점의 인덱스.</td></tr><tr><td><code>neckLeftLateralFlexionImage</code></td><td>string</td><td>왼쪽으로 목을 굽혔을 때 최대 각도 시점의 이미지. base64 인코딩 됨.</td></tr><tr><td><code>neckRightLateralFlexionImage</code></td><td>string</td><td>오른쪽으로 목을 굽혔을 때 최대 각도 시점의 이미지. base64 인코딩 됨.</td></tr></tbody></table>

\*항상 응답

<table><thead><tr><th width="164">Name</th><th width="88">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>state</code></td><td>int</td><td>성공 시 True, 실패 시 False.</td></tr><tr><td><code>message</code></td><td>string</td><td>성공 또는 실패 관련 안내 메세지.</td></tr><tr><td><code>uuid</code></td><td>string</td><td>영상 uuid.</td></tr><tr><td><code>motionDetail</code></td><td>string</td><td>파라미터로 전달 받았던 영상 종류.</td></tr></tbody></table>

**\***&#x6D;otionDetail 값에 따른 응답

1. motionDetail = neckLateralFlexion

<table><thead><tr><th width="164">Name</th><th width="88">Type</th><th>Description</th></tr></thead><tbody><tr><td>neckLeftLateralFlexionAngle</td><td>float</td><td>왼쪽으로 목을 굽혔을 때 최대 각도.</td></tr><tr><td>neckRightLateralFlexionAngle</td><td>float</td><td>오른쪽으로 목을 굽혔을 때 최대 각도.</td></tr><tr><td>neckLeftLateralFlexionIndex</td><td>int</td><td>왼쪽으로 목을 굽혔을 때 최대 각도 시점의 인덱스.</td></tr><tr><td>neckRightLateralFlexionIndex</td><td>int</td><td>오른쪽으로 목을 굽혔을 때 최대 각도 시점의 인덱스.</td></tr><tr><td>neckLeftLateralFlexionImage</td><td>string</td><td>왼쪽으로 목을 굽혔을 때 최대 각도 시점의 이미지. base64 인코딩 됨.</td></tr><tr><td>neckRightLateralFlexionImage</td><td>string</td><td>오른쪽으로 목을 굽혔을 때 최대 각도 시점의 이미지. base64 인코딩 됨.</td></tr></tbody></table>

2. motionDetail = neckRotation

<table><thead><tr><th width="164">Name</th><th width="88">Type</th><th>Description</th></tr></thead><tbody><tr><td>neckLeftRotationAngle</td><td>float</td><td>왼쪽으로 목을 돌렸을 때 최대 각도.</td></tr><tr><td>neckRightRotationAngle</td><td>float</td><td>오른쪽으로 목을 돌렸을 때 최대 각도.</td></tr><tr><td>neckLeftRotationIndex</td><td>int</td><td>왼쪽으로 목을 돌렸을 때 최대 각도 시점의 인덱스.</td></tr><tr><td>neckRightRotationIndex</td><td>int</td><td>오른쪽으로 목을 돌렸을 때 최대 각도 시점의 인덱스.</td></tr><tr><td>neckLeftRotationImage</td><td>string</td><td>왼쪽으로 목을 돌렸을 때 최대 각도 시점의 이미지. base64 인코딩 됨.</td></tr><tr><td>neckRightRotationImage</td><td>string</td><td>오른쪽으로 목을 돌렸을 때 최대 각도 시점의 이미지. base64 인코딩 됨.</td></tr></tbody></table>

3. motionDetail = neckFlexion

<table><thead><tr><th width="164">Name</th><th width="88">Type</th><th>Description</th></tr></thead><tbody><tr><td>neckFlexionAngle</td><td>float</td><td>목을 폈을 때 최대 각도.</td></tr><tr><td>neckExtensionAngle</td><td>float</td><td>목을 접었을 때 최대 각도.</td></tr><tr><td>neckFlexionIndex</td><td>int</td><td>목을 폈을 때 최대 각도 시점의 인덱스.</td></tr><tr><td>neckExtensionIndex</td><td>int</td><td>목을 접었을 때 최대 각도 시점의 인덱스.</td></tr><tr><td>neckFlexionImage</td><td>string</td><td>목을 폈을 때 최대 각도 시점의 이미지. base64 인코딩 됨.</td></tr><tr><td>neckExtensionImage</td><td>string</td><td>목을 접었을 때 최대 각도 시점의 이미지. base64 인코딩 됨.</td></tr></tbody></table>

4. motionDetail = leftArmLateralFlexion

<table><thead><tr><th width="164">Name</th><th width="88">Type</th><th>Description</th></tr></thead><tbody><tr><td>leftArmInLateralFlexionAngle</td><td>float</td><td>왼쪽 팔을 안으로 당겼을 때 최대 각도.</td></tr><tr><td>leftArmOutLateralFlexionAngle</td><td>float</td><td>왼쪽 팔을 밖으로 밀었을 때 최대 각도.</td></tr><tr><td>leftArmInLateralFlexionIndex</td><td>int</td><td>왼쪽 팔을 안으로 당겼을 때 최대 각도 시점의 인덱스.</td></tr><tr><td>neleftArmOutLateralFlexionIndex</td><td>int</td><td>왼쪽 팔을 밖으로 밀었을 때 최대 각도 시점의 인덱스.</td></tr><tr><td>leftArmInLateralFlexionImage</td><td>string</td><td>왼쪽 팔을 안으로 당겼을 때 최대 각도 시점의 이미지. base64 인코딩 됨.</td></tr><tr><td>leftArmOutLateralFlexionImage</td><td>string</td><td>왼쪽 팔을 밖으로 밀었을 때 최대 각도 시점의 이미지. base64 인코딩 됨.</td></tr></tbody></table>

5. motionDetail = leftArmFlexion

<table><thead><tr><th width="164">Name</th><th width="88">Type</th><th>Description</th></tr></thead><tbody><tr><td>leftArmFrontFlexionAngle</td><td>float</td><td>왼쪽 팔을 앞으로 올렸을 때 최대 각도.</td></tr><tr><td>leftArmBackFlexionAngle</td><td>float</td><td>왼쪽 팔을 뒤로 올렸을 때 최대 각도.</td></tr><tr><td>leftArmFrontFlexionIndex</td><td>int</td><td>왼쪽 팔을 앞으로 올렸을 때 최대 각도 시점의 인덱스.</td></tr><tr><td>leftArmBackFlexionIndex</td><td>int</td><td>왼쪽 팔을 뒤로 올렸을 때 최대 각도 시점의 인덱스.</td></tr><tr><td>leftArmFrontFlexionImage</td><td>string</td><td>왼쪽 팔을 앞으로 올렸을 때 최대 각도 시점의 이미지. base64 인코딩 됨.</td></tr><tr><td>leftArmBackFlexionImage</td><td>string</td><td>왼쪽 팔을 뒤로 올렸을 때 최대 각도 시점의 이미지. base64 인코딩 됨.</td></tr></tbody></table>

6. motionDetail = leftShoulderRotation

<table><thead><tr><th width="164">Name</th><th width="88">Type</th><th>Description</th></tr></thead><tbody><tr><td>leftShoulderFrontRotationAngle</td><td>float</td><td>왼쪽 팔을 앞으로 돌렸을 때 최대 각도.</td></tr><tr><td>leftShoulderBackRotationAngle</td><td>float</td><td>왼쪽 팔을 뒤로 돌렸을 때 최대 각도.</td></tr><tr><td>leftShoulderFrontRotationIndex</td><td>int</td><td>왼쪽 팔을 앞으로 돌렸을 때 최대 각도 시점의 인덱스.</td></tr><tr><td>leftShoulderBackRotationIndex</td><td>int</td><td>왼쪽 팔을 뒤로 돌렸을 때 최대 각도 시점의 인덱스.</td></tr><tr><td>leftShoulderFrontRotationImage</td><td>string</td><td>왼쪽 팔을 앞으로 돌렸을 때 최대 각도 시점의 이미지. base64 인코딩 됨.</td></tr><tr><td>leftShoulderBackRotationImage</td><td>string</td><td>왼쪽 팔을 뒤로 돌렸을 때 최대 각도 시점의 이미지. base64 인코딩 됨.</td></tr></tbody></table>

7. motionDetail = rightArmLateralFlexion

<table><thead><tr><th width="164">Name</th><th width="88">Type</th><th>Description</th></tr></thead><tbody><tr><td>rightArmInLateralFlexionAngle</td><td>float</td><td>오른쪽 팔을 안으로 당겼을 때 최대 각도.</td></tr><tr><td>rightArmOutLateralFlexionAngle</td><td>float</td><td>오른쪽 팔을 밖으로 밀었을 때 최대 각도.</td></tr><tr><td>rightArmInLateralFlexionIndex</td><td>int</td><td>오른쪽 팔을 안으로 당겼을 때 최대 각도 시점의 인덱스.</td></tr><tr><td>rightArmOutLateralFlexionIndex</td><td>int</td><td>오른쪽 팔을 밖으로 밀었을 때 최대 각도 시점의 인덱스.</td></tr><tr><td>rightArmInLateralFlexionImage</td><td>string</td><td>오른쪽 팔을 안으로 당겼을 때 최대 각도 시점의 이미지. base64 인코딩 됨.</td></tr><tr><td>rightArmOutLateralFlexionImage</td><td>string</td><td>오른쪽 팔을 밖으로 밀었을 때 최대 각도 시점의 이미지. base64 인코딩 됨.</td></tr></tbody></table>

8. motionDetail = rightArmFlexion

<table><thead><tr><th width="164">Name</th><th width="88">Type</th><th>Description</th></tr></thead><tbody><tr><td>rightArmFrontFlexionAngle</td><td>float</td><td>오른쪽 팔을 앞으로 올렸을 때 최대 각도.</td></tr><tr><td>rightArmBackFlexionAngle</td><td>float</td><td>오른쪽 팔을 뒤로 올렸을 때 최대 각도.</td></tr><tr><td>rightArmFrontFlexionIndex</td><td>int</td><td>오른쪽 팔을 앞으로 올렸을 때 최대 각도 시점의 인덱스.</td></tr><tr><td>rightArmBackFlexionIndex</td><td>int</td><td>오른쪽 팔을 뒤로 올렸을 때 최대 각도 시점의 인덱스.</td></tr><tr><td>rightArmFrontFlexionImage</td><td>string</td><td>오른쪽 팔을 앞으로 올렸을 때 최대 각도 시점의 이미지. base64 인코딩 됨.</td></tr><tr><td>rightArmBackFlexionImage</td><td>string</td><td>오른쪽 팔을 뒤로 올렸을 때 최대 각도 시점의 이미지. base64 인코딩 됨.</td></tr></tbody></table>

9. motionDetail = rightShoulderRotation

<table><thead><tr><th width="164">Name</th><th width="88">Type</th><th>Description</th></tr></thead><tbody><tr><td>rightShoulderFrontRotationAngle</td><td>float</td><td>오른쪽 팔을 앞으로 돌렸을 때 최대 각도.</td></tr><tr><td>rightShoulderBackRotationAngle</td><td>float</td><td>오른쪽 팔을 뒤로 돌렸을 때 최대 각도.</td></tr><tr><td>rightShoulderFrontRotationIndex</td><td>int</td><td>오른쪽 팔을 앞으로 돌렸을 때 최대 각도 시점의 인덱스.</td></tr><tr><td>rightShoulderBackRotationIndex</td><td>int</td><td>오른쪽 팔을 뒤로 돌렸을 때 최대 각도 시점의 인덱스.</td></tr><tr><td>rightShoulderFrontRotationImage</td><td>string</td><td>오른쪽 팔을 앞으로 돌렸을 때 최대 각도 시점의 이미지. base64 인코딩 됨.</td></tr><tr><td>rightShoulderBackRotationImage</td><td>string</td><td>오른쪽 팔을 뒤로 돌렸을 때 최대 각도 시점의 이미지. base64 인코딩 됨.</td></tr></tbody></table>



**요청 예시**

```
http://115.94.164.253:15003/ROM/get-result/example@email.com/bc692864-0243-4d41-bce3-7658c92ef0c5
```



**응답 예시**

{% tabs %}
{% tab title="Success" %}
```
{
  "message": "success",
  "neckLeftLateralFlexionAngle": 0.986171066827481,
  "neckRightLateralFlexionAngle": -10.564659513465642,
  "neckLeftLateralFlexionIndex": 16,
  "neckRightLateralFlexionIndex": 106,
  "state": true,
  "neckLeftLateralFlexionImage": "/9j/4AAQSkZJR ...(생략)... PNZoD/2Q==",
  "neckRightLateralFlexionImage": "/9j/4AAQSkZJRgABAQA ...(생략)... PfPfGamLM+h//9k=",
  "uuid": "2aa1fc62-0b47-4d9e-8efd-415631a4ea9f",
  "motionDetail": "neckLateralFlexion"
}
```
{% endtab %}

{% tab title="Fail" %}
```
{
  "state": false,
  "message": "undefined motion detail",
  "uuid": "5bef3100-2b02-4a29-bc3f-03cba9ea776e",
  "motionDetail": "test"
}
```
{% endtab %}
{% endtabs %}
