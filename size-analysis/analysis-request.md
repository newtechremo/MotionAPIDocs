---
description: 이미지에 있는 측정 대상의 체형과 신체 치수를 분석하는 API입니다.
---

# 이미지 체형 치수 분석 요청

## 이미지 체형 치수 분석 요청

<mark style="color:green;">`POST`</mark> `http://api.remo.re.kr/api/analysis-shape`

사진(front, side)과 키(height), 몸무게(weight), 나이(age), 성별(gender), 생년월일(birthday)를 입력 받아 신체 체형과 치수를 측정합니다.

**파라미터(json)**

<table><thead><tr><th>Name</th><th>Type</th><th>Description</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td><code>Email</code></td><td>string</td><td>유저 이메일 주소</td><td>true</td></tr><tr><td><code>UserKey</code></td><td>string</td><td>발급 받은 유저 키 값</td><td>true</td></tr><tr><td><code>APIKey</code></td><td>string</td><td>발급 받은 API 키 값</td><td>true</td></tr><tr><td><code>forigimg</code></td><td>string(base64)</td><td>base64로 인코딩 된 정면 사진</td><td>true</td></tr><tr><td><code>sorigimg</code></td><td>string(base64)</td><td>base64로 인코딩 된 측면 사진</td><td>true</td></tr><tr><td><code>gender</code></td><td>int</td><td>성별(남자:1, 여자:2)</td><td>true</td></tr><tr><td><code>height_mm</code></td><td>int</td><td>분석 대상의 키(mm 단위)</td><td>true</td></tr><tr><td><code>weight_g</code></td><td>int</td><td>분석 대상의 몸무게(g 단위)</td><td>true</td></tr><tr><td><code>age</code></td><td>int</td><td>분석 대상의 나이</td><td>true</td></tr><tr><td><code>birthday</code></td><td>string</td><td>분석 대상의 생년월일 8글자</td><td>true</td></tr></tbody></table>

**응답(json)**

<table><thead><tr><th width="173">Name</th><th width="88">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>state</code></td><td>bool</td><td>분석성공 시 True, 실패 시 False</td></tr><tr><td><code>statue_code</code></td><td>int</td><td>분석 성공 시 200, 실패 시 에러 코드 값 참조</td></tr><tr><td><code>credit_change</code></td><td>int</td><td>분석 성공 시 사용된 크리딧 수량, 실패 시 0</td></tr><tr><td><code>message</code></td><td>string</td><td>요청관련 안내 메시지</td></tr><tr><td><code>shape_class</code></td><td>int</td><td>0: 사각형, 1: 둥근형, 2: 삼각형, 3: 역삼각형, 4: 모래시계형</td></tr><tr><td><code>shape_size</code></td><td>int</td><td>0 ~ 4까지 값으로 구성. 0 매우 마름, 1: 마름, 2:표준, 3: 과체중, 4: 비만</td></tr><tr><td><code>BMI</code></td><td>float</td><td>사용자의 체질양 지수 값을 나타냄</td></tr><tr><td><code>WHR</code></td><td>float</td><td>사용자의 허리둘레와 엉덩이 둘레 비율</td></tr><tr><td><code>height_per</code></td><td>float</td><td>신장의 표준 분포 비율을 나타냄, 중위값은 50(단위%)</td></tr><tr><td><code>weight_per</code></td><td>float</td><td>몸무게의 표준 분포 비율을 나타냄, 중위값은 50(단위%)</td></tr><tr><td><code>chest</code></td><td>float</td><td>가슴둘레 예측 평균 값(단위 mm)</td></tr><tr><td><code>chest_max</code></td><td>float</td><td>가슴둘레 예측 최대 값(단위 mm)</td></tr><tr><td><code>chest_min</code></td><td>float</td><td>가슴둘레 예측 최소 값(단위 mm)</td></tr><tr><td><code>chest_per</code></td><td>float</td><td>가슴 둘레의 표준 분포 비율을 나타냄, 중위값은 50(단위%)</td></tr><tr><td><code>hip</code></td><td>float</td><td>엉덩이 둘레 예측 평균 값(단위 mm)</td></tr><tr><td><code>hip_max</code></td><td>float</td><td>엉덩이 둘레 예측 최대 값(단위 mm)</td></tr><tr><td><code>hip_min</code></td><td>float</td><td>엉덩이 둘레 예측 최소 값(단위 mm)</td></tr><tr><td><code>hip_per</code></td><td>float</td><td>엉덩이 둘레의 표준 분포 비율을 나타냄, 중위값은 50(단위%)</td></tr><tr><td><code>waist</code></td><td>float</td><td>허리 둘레 예측 평균 값(단위 mm)</td></tr><tr><td><code>waist_max</code></td><td>float</td><td>허리 둘레 예측 최대 값(단위 mm)</td></tr><tr><td><code>waist_min</code></td><td>float</td><td>허리 둘레 예측 최소 값(단위 mm)</td></tr><tr><td><code>waist_per</code></td><td>float</td><td>허리 둘레의 표준 분포 비율을 나타냄, 중위값은 50(단위%)</td></tr><tr><td><code>thigh</code></td><td>float</td><td>허벅지 둘레 예측 평균 값(단위 mm)</td></tr><tr><td><code>thigh_max</code></td><td>float</td><td>허벅지 둘레 예측 최대 값(단위 mm)</td></tr><tr><td><code>thigh_min</code></td><td>float</td><td>허벅지 둘레 예측 최소 값(단위 mm)</td></tr><tr><td><code>thigh_per</code></td><td>float</td><td>허벅지 둘레의 표준 분포 비율을 나타냄, 중위값은 50(단위%)</td></tr><tr><td><code>arm_length</code></td><td>float</td><td>팔의 평균 측정 길이(단위 mm)</td></tr><tr><td><code>arm_per</code></td><td>float</td><td>팔의 측정 길이 표준 평차(단위 %)</td></tr><tr><td><code>leg_length</code></td><td>float</td><td>다리의 평균 측정 길이(단위 mm)</td></tr><tr><td><code>leg_per</code></td><td>float</td><td>다리의 측정 길이 표준 평차(단위 %)</td></tr><tr><td><code>head_length</code></td><td>float</td><td>머리의 높이 측정 값(단위 mm)</td></tr><tr><td><code>trunk_length</code></td><td>float</td><td>머리 아래 상반신의 길이 측정 값(단위 mm)</td></tr><tr><td><code>lower_body_length</code></td><td>float</td><td>발목 위 하반신의 길이 측정 값(단위 mm)</td></tr><tr><td><code>left_arm_length</code></td><td>float</td><td>왼쪽 팔의 길이 측정 값(mm)</td></tr><tr><td><code>left_up_arm_length</code></td><td>float</td><td>왼쪽 팔 상완의 길이 측정 값(mm)</td></tr><tr><td><code>left_down_arm_length</code></td><td>float</td><td>왼쪽 팔 하완의 길이 측정 값(mm)</td></tr><tr><td><code>right_arm_length</code></td><td>float</td><td>오른쪽 팔의 길이 측정 값(mm)</td></tr><tr><td><code>right_up_arm_length</code></td><td>float</td><td>오른쪽 팔 상완의 길이 측정 값(mm)</td></tr><tr><td><code>right_down_arm_length</code></td><td>float</td><td>오른쪽 팔 하완의 길이 측정 값(mm)</td></tr><tr><td><code>left_down_leg_length</code></td><td>float</td><td>왼쪽 다리의 길이 측정 값(mm)</td></tr><tr><td><code>left_up_leg_length</code></td><td>float</td><td>왼쪽 다리 허벅지의 길이 측정 값(mm)</td></tr><tr><td><code>left_down_leg_length</code></td><td>float</td><td>왼쪽 다리 종아리의 길이 측정 값(mm)</td></tr><tr><td><code>right_leg_length</code></td><td>float</td><td>오른쪽 다리의 길이 측정 값(mm)</td></tr><tr><td><code>right_up_leg_length</code></td><td>float</td><td>오른쪽 다리 허벅지의 길이 측정 값(mm)</td></tr><tr><td><code>right_down_leg_length</code></td><td>float</td><td>오른쪽 다리 종아리의 길이 측정 값(mm)</td></tr></tbody></table>

**요청 예시**

```json
{
  "Email": “your_email”,
  "UserKey": “your_user_key”,
  "APIKey": “your_api_key”,
  "forigimg": "/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAIBAQEBAQIBAQECAgICAgQDAgICAgUEBAMEBgUGBgYFBgYGBw ... (생략)(이미지를 바이트로 변환한 결과)",
  "sorigimg": "/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAIBAQEBAQIBAQECAgICAgQDAgICAgUEBAMEBgUGBgYFBgYGBw ... (생략)(이미지를 바이트로 변환한 결과)"
  "gender": 2,
  "height_mm": 1650,
  "weight_g": 65000,
  "age": 100,
  "birthday": “20101010”
 }
```

**예시 코드**

{% tabs %}
{% tab title="curl" %}
```bash
curl -X POST "http://api.remo.re.kr/api/analysis-shape" \
-H "Content-Type: application/json" \
-d '{
    "Email": "your_email",
    "UserKey": "your_user_key",
    "APIKey": "your_api_key",
    "forigimg": "'$(base64 -w 0 path/to/your/front/image)'",
    "sorigimg": "'$(base64 -w 0 path/to/your/side/image)'",
    "gender": 2,
    "height_mm": 1650,
    "weight_g": 65000,
    "age": 15,
    "birthday": "20101010"
}'
```
{% endtab %}

{% tab title="Python" %}
```python
import requests
import uuid
import base64

fimg_path = "path/to/your/front/image"
simg_path = "path/to/your/side/image"

with open(fimg_path, "rb") as img_file:
    fimg_b64 = base64.b64encode(img_file.read()).decode('utf-8')
with open(simg_path, "rb") as img_file:
    simg_b64 = base64.b64encode(img_file.read()).decode('utf-8')

task_uuid = str(uuid.uuid4())
rq_dict = {'Email': "your_email", "UserKey": "your_user_key", "APIKey": "your_api_key", "forigimg": fimg_b64, "sorigimg": simg_b64, "gender": 2, "height_mm": 1650, "weight_g": 65000, "age": 15, "birthday": "20101010"}

res = requests.post("http://api.remo.re.kr/api/analysis-shape", json=rq_dict)
```
{% endtab %}

{% tab title="javascript" %}
```javascript
import fetch from 'node-fetch';
import fs from 'fs';
import { v4 as uuidv4 } from 'uuid';

const fimg_path = "path/to/your/front/image";
const simg_path = "path/to/your/side/image";

const fimg_b64 = fs.readFileSync(fimg_path, 'base64');
const simg_b64 = fs.readFileSync(simg_path, 'base64');

const task_uuid = uuidv4();
const rq_dict = {
  Email: "your_email",
  UserKey: "your_user_key",
  APIKey: "your_api_key",
  forigimg: fimg_b64,
  sorigimg: simg_b64,
  gender: 2,
  height_mm: 1650,
  weight_g: 65000,
  age: 15,
  birthday: "20101010"
};

fetch("http://api.remo.re.kr/api/analysis-shape", {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify(rq_dict)
})
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.error('Error:', error));

```
{% endtab %}
{% endtabs %}

**응답 예시**

{% tabs %}
{% tab title="200" %}
```json
{
  'state': True, 
  'status_code': 200, 
  'APIName': 'Analysis-shape', 
  'credit_change': -1, 
  'credit': 99, 
  'uuid': '3b255cb1-ba71-4264-a52a-3bee7fe5b5c9', 
  'BMI': 238.751, 
  'WHR': 0.809, 
  'arm_length': 527.7, 
  'arm_per': 100, 
  'body_length': 1650.0, 
  'chest': 857.1, 
  'chest_max': 859.3, 
  'chest_min': 829.3, 
  'chest_per': 100, 
  'head_length': 265.8, 
  'height_per': 100, 
  'hip': 870.1, 
  'hip_max': 877.4, 
  'hip_min': 819.2, 
  'hip_per': 100, 
  'left_arm_length': 530.7, 
  'left_down_arm_length': 251.1, 
  'left_down_leg_length': 407.3, 
  'left_leg_length': 792.0, 
  'left_up_arm_length': 279.6, 
  'left_up_leg_length': 384.7, 
  'leg_length': 790.1, 
  'leg_per': 100, 
  'lower_body_length': 887.0, 
  'right_arm_length': 524.7, 
  'right_down_arm_length': 248.6, 
  'right_down_leg_length': 405.5, 
  'right_leg_length': 788.1, 
  'right_up_arm_length': 276.1, 
  'right_up_leg_length': 382.6, 
  'shape_class': 0, 
  'shape_size': 2, 
  'thigh': 478.1, 
  'thigh_max': 482.3, 
  'thigh_min': 397.1, 
  'thigh_per': 100, 
  'trunk_length': 466.8, 
  'waist': 704.2, 
  'waist_max': 724.0, 
  'waist_min': 694.9, 
  'waist_per': 100, 
  'weight_per': 100, 
  'shape_data': {'BMI': 238.751, 'WHR': 0.809, 'arm_length': 527.7, 'arm_per': 100, 'body_length': 1650.0, 'chest': 857.1, 'chest_max': 859.3, 'chest_min': 829.3, 'chest_per': 100, 'head_length': 265.8, 'height_per': 100, 'hip': 870.1, 'hip_max': 877.4, 'hip_min': 819.2, 'hip_per': 100, 'left_arm_length': 530.7, 'left_down_arm_length': 251.1, 'left_down_leg_length': 407.3, 'left_leg_length': 792.0, 'left_up_arm_length': 279.6, 'left_up_leg_length': 384.7, 'leg_length': 790.1, 'leg_per': 100, 'lower_body_length': 887.0, 'right_arm_length': 524.7, 'right_down_arm_length': 248.6, 'right_down_leg_length': 405.5, 'right_leg_length': 788.1, 'right_up_arm_length': 276.1, 'right_up_leg_length': 382.6, 'shape_class': 0, 'shape_size': 2, 'thigh': 478.1, 'thigh_max': 482.3, 'thigh_min': 397.1, 'thigh_per': 100, 'trunk_length': 466.8, 'waist': 704.2, 'waist_max': 724.0, 'waist_min': 694.9, 'waist_per': 100, 'weight_per': 100}, 'message': 'success'}
}
```
{% endtab %}

{% tab title="400~" %}
```json
{
    'state': False, 
    'status_code': 413, 
    'credit_change': 0, 
    'credit': 100, 
    'message': 'error from front image decoding b64'
}
```
{% endtab %}

{% tab title="500~" %}
```json
{
    'state': False, 
    'status_code': 515, 
    'credit_change': 0, 
    'credit': 100, 
    'message': 'In the side image, the model is not facing side '
}
```
{% endtab %}
{% endtabs %}

**에러 코드 안내**

| 대분류          | 소분류                           | 코드  |
| ------------ | ----------------------------- | --- |
| 입력 데이터 문제 발생 | 프로토콜 에러                       | 400 |
|              | 입력 데이터 없음                     | 411 |
|              | 첨부 이미지 에러                     | 412 |
|              | 첨부 이미지 에러(정면)                 | 413 |
|              | 첨부 이미지 에러(측면)                 | 414 |
|              | 입력 이미지 위아래 반전(정면, 측면 모두)      | 415 |
|              | 입력 이미지 위아래 반전(정면)             | 416 |
|              | 입력 이미지 위아래 반전(측면)             | 417 |
| 기타 이슈 발생     | 사용 유저 확인 안됨                   | 420 |
|              | APIKey 틀림                     | 421 |
|              | 크리딧 부족                        | 422 |
|              | 정면 사진 사람 인식 안됨                | 511 |
|              | 측면 사진 사람 인식 안됨                | 512 |
|              | 정면,측면 사진 모두 사람 인식 안됨          | 513 |
|              | 정면 사진에서 정면을 바라보지 않고 있음        | 514 |
|              | 측면 사진에서 측면을 바라보지 않고 있음        | 515 |
|              | 정면/측면 대상자가 정면/측면을 바라보고 있지 않음. | 516 |
|              | 정면 이미지의 대상자가 A자 자세가 아님        | 517 |
|              | 측면 이미지의 대상자가 차렷 자세가 아님        | 518 |
|              | 체형 측정 자세가 바르지 않음              | 519 |
