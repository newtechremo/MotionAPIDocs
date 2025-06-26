---
description: 이미지에서 인체 세그멘테이션을 수행하는 API입니다.
---

# 이미지 세그멘테이션 분석 요청

## 이미지 세그멘테이션 분석 요청

<mark style="color:green;">`POST`</mark> `http://???/analyze/segmentation-v2`

S3에 저장된 이미지를 입력받아 인체 세그멘테이션 마스크를 생성합니다.

**파라미터(json)**

<table><thead><tr><th>Name</th><th>Type</th><th>Description</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td><code>imgSrc</code></td><td>string</td><td>S3에 저장된 이미지 경로</td><td>true</td></tr></tbody></table>

**응답(json)**

<table><thead><tr><th width="173">Name</th><th width="88">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>data</code></td><td>list</td><td>성공 시 세그멘테이션 마스크 배열, 실패 시 에러 정보 객체</td></tr><tr><td><code>state</code></td><td>int</td><td>처리 상태 (-1: 실패)</td></tr><tr><td><code>message</code></td><td>string</td><td>요청관련 안내 메시지</td></tr><tr><td><code>errors</code></td><td>string</td><td>요청 처리 중 발생한 에러 메시지</td></tr></tbody></table>

**요청 예시**

```json
{
  "imgSrc": "path/to/your/image/in/s3/bucket"
}
```

**예시 코드**

{% tabs %}
{% tab title="curl" %}
```bash
curl -X POST "/analyze/segmentation-v2" \
-H "Content-Type: application/json" \
-d '{
    "imgSrc": "path/to/your/image/in/s3/bucket"
}'
```
{% endtab %}

{% tab title="Python" %}
```python
import requests
import json

rq_dict = {
    "imgSrc": "path/to/your/image/in/s3/bucket"
}

res = requests.post("/analyze/segmentation-v2", json=rq_dict)
response_data = res.json()
print(response_data)
```
{% endtab %}

{% tab title="javascript" %}
```javascript
import fetch from 'node-fetch';

const rq_dict = {
  imgSrc: "path/to/your/image/in/s3/bucket"
};

fetch("/analyze/segmentation-v2", {
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
  "state": 1,
  "data": [
    [0, 0, 1, 1, 0, 0],
    [0, 1, 1, 1, 1, 0],
    [1, 1, 1, 1, 1, 1],
    [0, 1, 1, 1, 1, 0],
    [0, 0, 1, 1, 0, 0]
  ]
}
```
{% endtab %}

{% tab title="400~" %}
```json
{
  "state": 0,
  "message": "image load error"
}
```
{% endtab %}
{% endtabs %}

**에러 코드 안내**
