---
description: 완료된 보행 분석 그래프 값을 요청하는 API입니다.
---

# 보행 분석 그래프 요청

## 보행 분석 그래프 요청

<mark style="color:green;">`POST`</mark> `http://api.remo.re.kr/api/analysis-walking-angle`

사용자 id(이메일), 분석된 비디오 uuid를 파라미터로 받아 그래프를 그리는 데 필요한 각도 값을 Return합니다.

**파라미터(json)**

<table><thead><tr><th>Name</th><th>Type</th><th>Description</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td><code>id</code></td><td>string</td><td>유저 이메일 주소</td><td>true</td></tr><tr><td><code>uuid</code></td><td>string</td><td>영상 uuid</td><td>true</td></tr></tbody></table>

**응답(json)**

<table><thead><tr><th width="156">Name</th><th width="84">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>state</code></td><td>int</td><td>성공 시 1, 실패 시 0</td></tr><tr><td><code>message</code></td><td>string</td><td>성공 또는 실패 관련 안내 메세지</td></tr><tr><td><code>hip</code></td><td>dict</td><td>엉덩 관절. Sagittal, Coronal, Transverse을 key로 가지고 있음.</td></tr><tr><td><code>knee</code></td><td>dict</td><td>무릎 관절. Sagittal, Coronal, Transverse을 key로 가지고 있음.</td></tr><tr><td><code>ankle</code></td><td>dict</td><td>발목 관절. Sagittal, Coronal, Transverse을 key로 가지고 있음.</td></tr><tr><td><code>Sagittal</code></td><td>dict</td><td>시상면. range, left, right을 key로 가지고 있음.</td></tr><tr><td><code>Coronal</code></td><td>dict</td><td>관상면. range, left, right을 key로 가지고 있음.</td></tr><tr><td><code>Transverse</code></td><td>dict</td><td>수평면. range, left, right을 key로 가지고 있음.</td></tr><tr><td><code>range</code></td><td>list</td><td>그래프의 축 범위. 첫 번째 값 ~ 두 번째 값까지 축 범위를 설정</td></tr><tr><td><code>left</code></td><td>dict</td><td>왼쪽. mean을 key로 가지고 있음.</td></tr><tr><td><code>right</code></td><td>dict</td><td>오른쪽. mean을 key로 가지고 있음.</td></tr><tr><td><code>mean</code></td><td>list</td><td>관절의 angle 값 list</td></tr></tbody></table>

**요청 예시**

```json
/get-angle/example@example.com/bc692864-0243-4d41-bce3-7658c92ef0c5
```

**응답 예시**

{% tabs %}
{% tab title="200" %}
```json
{
  "hip": {
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
  },
  "knee": {
    "Sagittal": {
      "range": [0, 70],
      "left": {
        "mean": [
          17.55313, 17.86393, ..., 14.62733, 14.41221
        ]
      },
      "right": {
        "mean": [
          13.89033, 13.13457, ..., 13.69133, 12.58434
        ]
      }
    },
    "Coronal": {
      "range": [-5, 5],
      "left": {
        "mean": [
          -7.38343, -7.26108, ..., -5.30595, -5.25075
        ]
      },
      "right": {
        "mean": [
          -13.48968, -13.73512, ..., -12.81147, -13.10944
        ]
      }
    },
    "Transverse": {
      "range": [-5, 5],
      "left": {
        "mean": [
          -27.87897, -27.81244, ..., -26.02685, -26.07673
        ]
      },
      "right": {
        "mean": [
          -20.35731, -20.24204, ..., -20.10835, -20.35162
        ]
      }
    }
  },
  "ankle": {
    "Sagittal": {
      "range": [-30, 20],
      "left": {
        "mean": [
          -3.91493, -3.84959, ..., -7.71493, -7.68264
        ]
      },
      "right": {
        "mean": [
          -0.98987, -0.74556, ..., -3.16904, -2.96793
        ]
      }
    },
    "Coronal": {
      "range": [-20, 20],
      "left": {
        "mean": [
          -0.77926, -0.83188, ..., -4.14389, -3.82192
        ]
      },
      "right": {
        "mean": [
          4.87106, 5.38434, ..., 2.74012, 3.34569
        ]
      }
    },
    "Transverse": {
      "range": [-20, 60],
      "left": {
        "mean": [
          5.92304, 5.62899, ..., 8.1099, 7.72117
        ]
      },
      "right": {
        "mean": [
          17.80345, 18.07364, ..., 16.68639, 17.17034
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

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>
