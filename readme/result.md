---
description: 완료된 보행 분석 결과를 요청하는 API입니다.
---

# 보행 분석 결과 요청

## 보행 분석 결과 요청

<mark style="color:green;">`POST`</mark> `http://api.remo.re.kr/api/analysis-walking-result`

사용자 id(이메일), 분석된 비디오 uuid를 파라미터로 받아 보행 분석 결과 값을 Return합니다.

**파라미터(json)**

<table><thead><tr><th>Name</th><th>Type</th><th>Description</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td><code>id</code></td><td>string</td><td>유저 이메일 주소</td><td>true</td></tr><tr><td><code>uuid</code></td><td>string</td><td>영상 uuid</td><td>true</td></tr></tbody></table>

**응답(json)**

<table><thead><tr><th width="132">Name</th><th width="86">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>state</code></td><td>int</td><td>성공 시 1, 실패 시 0</td></tr><tr><td><code>message</code></td><td>string</td><td>성공 또는 실패 관련 안내 메세지</td></tr><tr><td><code>uuid</code></td><td>string</td><td>파라미터로 전달 받은 uuid</td></tr><tr><td><code>result</code></td><td>list</td><td>차례로 분속수, 보행속도(m/s), 보장(cm), 입각기(%), 유각기(%), 양발지지기(%)의 dict 값을 가지고 있음.</td></tr><tr><td><code>total</code></td><td>float</td><td>왼쪽과 오른쪽의 평균</td></tr><tr><td><code>left</code></td><td>float</td><td>왼쪽 값</td></tr><tr><td><code>right</code></td><td>float</td><td>오른쪽 값</td></tr></tbody></table>

**요청 예시**

```json
/get-result/example@example.com/bc692864-0243-4d41-bce3-7658c92ef0c5
```

**응답 예시**

{% tabs %}
{% tab title="200" %}
```json
{
  "state": 1,
  "result": [
    {
      "total": 89.1473000683527,
      "left": 86.3961038961039,
      "right": 91.8984962406015
    },
    {
      "total": 0.3213670029837894,
      "left": 0.2981104250341651,
      "right": 0.34462358093341366
    },
    {
      "total": 21.573702360911454,
      "left": 20.658755943773752,
      "right": 22.488648778049154
    },
    {
      "total": 61.49912039714671,
      "left": 63.38291642567958,
      "right": 59.61532436861384
    },
    {
      "total": 38.50087960285329,
      "left": 36.61708357432042,
      "right": 40.38467563138616
    },
    {
      "total": 26.8069512724118,
      "left": 26.797582899556588,
      "right": 26.816319645267015
    }
  ],
  "uuid": "bc692864-0243-4d41-bce3-7658c92ef0c5",
  "message": "success"
}

```
{% endtab %}

{% tab title="400" %}
```json
{
  "state": 0,
  "message": "file does not exist"
}
```
{% endtab %}

{% tab title="400" %}
```json
{
  "state": 0,
  "message": "not a walking video"
}
```
{% endtab %}
{% endtabs %}

<figure><img src="../.gitbook/assets/Screenshot from 2024-05-10 17-29-33.png" alt=""><figcaption></figcaption></figure>
