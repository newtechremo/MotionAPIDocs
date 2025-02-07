---
description: 비디오를 입력 받아 사용자의 골프 자세를 분석하는 API입니다.
---

# 골프 비디오 분석 요청

### 골프 비디오 분석 요청

<mark style="color:green;">`POST`</mark> `http://115.94.164.253:15003/golf/analysis-await`

골프 비디오를 입력 받아 사용자의 자세를 분석합니다.

**파라미터(json)**

<table><thead><tr><th>Name</th><th>Type</th><th>Description</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td><code>id</code></td><td>string</td><td>유저 이메일 주소</td><td>true</td></tr><tr><td><code>bucket_url</code></td><td>string</td><td>영상 s3 주소.</td><td>true</td></tr><tr><td><code>height</code></td><td>string</td><td>분석 대상의 키(cm)</td><td>true</td></tr><tr><td><code>uuid</code></td><td>string</td><td>분석 비디오 uuid</td><td>true</td></tr><tr><td><code>credit</code></td><td>int</td><td>로직 상 필요한 더미 데이터. 정수 1000을 보내면 됨.</td><td>true</td></tr><tr><td><code>rq_url</code></td><td>string</td><td>완료 시 결과를 돌려 받을 url.</td><td>false</td></tr></tbody></table>

**응답(json)**

<table><thead><tr><th width="164">Name</th><th width="88">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>state</code></td><td>int</td><td>성공 시 1, 실패 시 0</td></tr><tr><td><code>message</code></td><td>string</td><td>성공 또는 실패 관련 안내 메세지</td></tr><tr><td><code>uuid</code></td><td>string</td><td>영상 uuid</td></tr><tr><td><code>wait_time</code></td><td>int</td><td>응답 후 결과 생성까지 대기 시간</td></tr><tr><td><code>file_exist</code></td><td>bool</td><td>이미 존재하는 파일이면 True, 아니면 False</td></tr><tr><td><code>credit</code></td><td>int</td><td>사용 예정 크레딧 수량</td></tr></tbody></table>

**요청 예시**

```json
{
  'bucket_url': "https://fourwk-public.s3.ap-northeast-2.amazonaws.com/motion-analysis-samples/golf.mp4",
  'id': "example@example.com",
  "uuid": "c37d3ce2-e9d0-45de-9656-2a730204f8ca"
  'height': "160",
  "credit": 1000
}
```

**예시 코드**

{% tabs %}
{% tab title="Python" %}
```python
import requests
import uuid

task_uuid = str(uuid.uuid4())
rq_dict = {'bucket_url':"https://fourwk-public.s3.ap-northeast-2.amazonaws.com/motion-analysis-samples/golf.mp4",'id':"example@example.com",'uuid':video_uuid,'height':"160","credit":1000}

res = requests.post("http://115.94.164.253:15003/golf/analysis-await", json=rq_dict)
```
{% endtab %}
{% endtabs %}

**응답 예시**

{% tabs %}
{% tab title="200" %}
```json
{
  'state': 1,
  'wait_time': 11,
  'file_exist': False,
  'uuid': 'c37d3ce2-e9d0-45de-9656-2a730204f8ca',
  'message': 'success',
  'credit': 4
}
```
{% endtab %}

{% tab title="400 ~" %}
```json
{
  "state": False,
  "credit": 100,
  "message": 'error from front image decoding b64',
  "status":413
}
```
{% endtab %}

{% tab title="500 ~" %}
```json
{
  "state": False,
  "credit": 100,
  "message": 'In the side image, the model is not facing side ',
  "status": 515
}
```
{% endtab %}
{% endtabs %}

**에러 코드 안내**

| 대분류          | 소분류           | 코드  |
| ------------ | ------------- | --- |
| 입력 데이터 문제 발생 | 프로토콜 에러       | 400 |
|              | 입력 데이터 없음     | 411 |
|              | 첨부 영상 에러      | 412 |
| 기타 이슈 발생     | 사용 유저 확인 안됨   | 420 |
|              | APIKey 틀림     | 421 |
|              | 크리딧 부족        | 422 |
| 프로세스 에러      | 프로세스 처리 에러    | 550 |
|              | 프로세스 처리 기타 에러 | 559 |

**webhook 응답(json)**

<table><thead><tr><th width="164">Name</th><th width="88">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>State</code></td><td>int</td><td>성공 시 1, 실패 시 0</td></tr><tr><td><code>UserID</code></td><td>string</td><td>유저 이메일 주소</td></tr><tr><td><code>VideoUUID</code></td><td>string</td><td>영상 uuid</td></tr><tr><td><code>Message</code></td><td>string</td><td>성공 또는 실패 관련 안내 메세지</td></tr></tbody></table>
