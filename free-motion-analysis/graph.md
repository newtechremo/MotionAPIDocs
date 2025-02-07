---
description: 완료된 보행 분석 그래프 값을 요청하는 API입니다.
---

# 자유 모션 분석 그래프 요청

## 자유 모션 분석 그래프 요청

<mark style="color:green;">`POST`</mark> `http://api.remo.re.kr/api/analysis-FreeMotion-angle`

사용자 id(이메일), 분석된 비디오 uuid, joint(각도 출력을 원하는 부위)를 파라미터로 받아 그래프를 그리는 데 필요한 각도 값을 Return합니다.

**파라미터(json)**

<table><thead><tr><th width="110">Name</th><th width="88">Type</th><th>Description</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td><code>id</code></td><td>string</td><td>유저 이메일 주소</td><td>true</td></tr><tr><td><code>uuid</code></td><td>string</td><td>영상 uuid</td><td>true</td></tr><tr><td><code>joint</code></td><td>string</td><td>"Hip", "Knee", "Ankle", "Shoulder", "Elbow", "Wrist", "Spine", "Neck" 중 택1</td><td>true</td></tr></tbody></table>

**응답(json)**

<table><thead><tr><th width="156">Name</th><th width="84">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>state</code></td><td>int</td><td>성공 시 1, 실패 시 0</td></tr><tr><td><code>message</code></td><td>string</td><td>성공 또는 실패 관련 안내 메세지</td></tr><tr><td><code>Hip</code></td><td>dict</td><td>엉덩 관절. Sagittal, Coronal, Transverse을 key로 가지고 있음.</td></tr><tr><td><code>Knee</code></td><td>dict</td><td>무릎. Sagittal, Coronal, Transverse을 key로 가지고 있음.</td></tr><tr><td><code>Ankle</code></td><td>dict</td><td>발목. Sagittal, Coronal, Transverse을 key로 가지고 있음.</td></tr><tr><td><code>Shoulder</code></td><td>dict</td><td>어깨. Sagittal, Coronal, Transverse을 key로 가지고 있음.</td></tr><tr><td><code>Elbow</code></td><td>dict</td><td>팔꿈치. Sagittal, Coronal, Transverse을 key로 가지고 있음.</td></tr><tr><td><code>Wrist</code></td><td>dict</td><td>손목. Sagittal, Coronal, Transverse을 key로 가지고 있음.</td></tr><tr><td><code>Spine</code></td><td>dict</td><td>몸통. Sagittal, Coronal, Transverse을 key로 가지고 있음.</td></tr><tr><td><code>Neck</code></td><td>dict</td><td>목. Sagittal, Coronal, Transverse을 key로 가지고 있음.</td></tr><tr><td><code>Sagittal</code></td><td>dict</td><td>시상면. range, left, right을 key로 가지고 있음.</td></tr><tr><td><code>Coronal</code></td><td>dict</td><td>관상면. range, left, right을 key로 가지고 있음.</td></tr><tr><td><code>Transverse</code></td><td>dict</td><td>수평면. range, left, right을 key로 가지고 있음.</td></tr><tr><td><code>range</code></td><td>list</td><td>그래프의 축 범위. 첫 번째 값 ~ 두 번째 값까지 축 범위를 설정</td></tr><tr><td><code>left</code></td><td>dict</td><td>왼쪽. mean을 key로 가지고 있음.</td></tr><tr><td><code>right</code></td><td>dict</td><td>오른쪽. mean을 key로 가지고 있음.</td></tr><tr><td><code>mean</code></td><td>list</td><td>관절의 angle 값 list</td></tr><tr><td><code>min</code></td><td>int</td><td>mean의 최소 값</td></tr><tr><td><code>max</code></td><td>int</td><td>mean의 최대 값</td></tr></tbody></table>

**요청 예시**

```json
{
  “id”: “example@example.com”,
  “uuid”: "d4147f2c-b5cc-4289-9325-94dbbef26d67"
  “joint”: “Hip”
}
```

**응답 예시**

{% tabs %}
{% tab title="200" %}
```json
{
  "state": 1,
  "message": success,
  "Hip": {
    "Sagittal": {
      "range": [-30, 30],
      "left": {
        "mean": [
          33.51917, 33.46679, ..., 32.01168, 32.21679
        ]
      },
      "right": {
        "mean": [
          24.58494, 24.49458, ..., 24.13248, 24.09185
        ]
      }
    },
    "Coronal": {
      "range": [-10, 30],
      "left": {
        "mean": [
          5.11125, 4.98427, ..., 7.69327, 7.41942
        ]
      },
      "right": {
        "mean": [
          2.69405, 2.44131, ..., 4.99395, 4.70155
        ]
      }
    },
    "Transverse": {
      "range": [-90, 20],
      "left": {
        "mean": [
          0.27234, 0.15604, ..., -0.07908, -0.08991
        ]
      },
      "right": {
        "mean": [
          2.62555, 2.66186, ..., 2.39876, 2.47905
        ]
      }
    }
  }
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
{% endtabs %}

<figure><img src="../.gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>
