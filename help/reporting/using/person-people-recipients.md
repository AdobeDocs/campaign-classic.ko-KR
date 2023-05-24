---
product: campaign
title: 개인, 사용자 및 수신자
description: 개인, 사용자 및 수신자
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Reporting
exl-id: 69b810f3-aa8b-4ab5-95c1-831257d7fcb9
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '703'
ht-degree: 9%

---

# 사람 및 수신자 {#person-people-and-recipients}



이 샘플은 Adobe Campaign의 개인/사용자와 수신자 간의 차이를 이해하는 데 도움이 됩니다. 다음 지표에 대한 계산 방법을 자세히 설명하면서 사용자와 수신자의 차이를 강조 표시하기 위해 여러 사람에게 게재를 보냅니다.

* **[!UICONTROL Clicks]**
* **[!UICONTROL Distinct clicks for the population reached]**
* **[!UICONTROL Distinct opens for the population reached]**
* **[!UICONTROL Estimation of forwards]**
* **[!UICONTROL Raw reactivity]**

>[!NOTE]
>
>다음 지표는에서 사용됩니다 **[!UICONTROL Tracking indicators]** 보고서. 자세한 내용은 다음을 참조하십시오. [지표 추적](../../reporting/using/delivery-reports.md#tracking-indicators).

세 개의 링크가 게재에 추가됩니다. 4명의 수신자에게 전송됩니다.

![](assets/s_ncs_user_indicators_example_1.png)

* **[!UICONTROL John Davis]** : 이 수신자는 이메일을 열지 않습니다(따라서 링크를 클릭하지 않음).
* **[!UICONTROL Marie Stuart]** : 이메일을 열지만 링크를 클릭하지 않습니다.
* **[!UICONTROL Florian David]** : 이메일을 열고 링크를 9번 클릭합니다. 또한 이메일을 열고 두 번 클릭하는 사람에게 이메일을 전달합니다.
* **[!UICONTROL Henry Macdonald]** : 이 수신자는 쿠키를 거부하도록 인터넷 브라우저를 구성했습니다. 그는 이메일을 열고 링크를 4번 클릭합니다.

다음 추적 로그가 반환됩니다.

![](assets/s_ncs_user_indicators_example_2.png)

어떻게 인원과 수신자가 집계되는지 더 명확하게 이해하기 위해, 우리는 각 프로필의 로그를 분석할 것입니다.

## 1단계: John {#step-1--john}

**[!UICONTROL John Davis]** 이메일을 열지 않습니다(따라서 링크를 클릭하지 않음).

![](assets/s_ncs_user_indicators_example_8.png)

John은 이메일을 열지도 클릭도 하지 않았기 때문에 로그에 표시되지 않습니다.

**중간 계산:**

|  | 클릭한 수신자 | 클릭한 사람 | 열람한 수신자 |
|---|---|---|---|
| John | - | - | - |
| 중간 합계 | 0 | 0 | 0 |

## 2단계: 마리 {#step-2--marie}

**[!UICONTROL Marie Stuart]** 이메일을 열지만 링크를 클릭하지 않습니다.

![](assets/s_ncs_user_indicators_example_7.png)

Marie&#39;s open은 다음 로그에 표시됩니다.

![](assets/s_ncs_user_indicators_example_4bis.png)

열림은 수신자 Marie에게 할당됩니다. 따라서 Adobe Campaign은 새 수신자를 카운트에 추가합니다.

**중간 계산:**

|  | 클릭한 수신자 | 클릭한 사람 | 열람한 수신자 |
|---|---|---|---|
| John | - | - | - |
| 마리 | - | - | +1 |
| 중간 합계 | 0 | 0 | 1 |

## 3단계: 플로리안 {#step-3--florian}

**[!UICONTROL Florian David]** 이메일을 열고 링크를 9번 클릭합니다. 또한 이메일을 열고 두 번 클릭하는 사람에게 이메일을 전달합니다.

![](assets/s_ncs_user_indicators_example_9.png)

Florian의 작업(한 번의 열린 클릭과 9번의 클릭)은 다음 로그에 표시됩니다.

![](assets/s_ncs_user_indicators_example_3bis.png)

**수신자**: 열기 및 클릭 수가 동일한 수신자에게 할당됩니다(Florian). 이 수신자는 이전 수신자(Marie)와 다르므로 Adobe Campaign은 새 수신자를 카운트에 추가합니다.

사람: 이 수신자의 브라우저가 쿠키를 승인하므로 동일한 UUID(식별자)가 모든 클릭 로그에 할당되었음을 알 수 있습니다. **`fe37a503 [...]`**. Adobe Campaign은 이러한 클릭이 동일한 사람에 속하는 것으로 올바르게 식별합니다. 새 사용자가 카운트에 추가됩니다.

**중간 계산:**

|  | 클릭한 수신자 | 클릭한 사람 | 열람한 수신자 |
|---|---|---|---|
| John | - | - | - |
| 마리 | - | - | +1 |
| 플로리안 | +1 | +1 | +1 |
| 중간 합계 | 1 | 1 | 2 |

다음 로그는 Florian이 이메일을 전달한 사람이 수행한 두 번의 클릭 및 열기 작업과 일치합니다.

![](assets/s_ncs_user_indicators_example_6bis.png)

**수신자**: 이메일을 전달한 수신자(Florian)에게 열기 및 클릭 수가 할당됩니다. 이 수신자는 이미 계산되었으므로 수신자 수는 동일하게 유지됩니다.

![](assets/s_ncs_user_indicators_example_12.png)

**사람**: 클릭과 관련하여 동일한 UUID(식별자)가 모든 로그에 할당되어 있음을 알 수 있습니다. **`9ab648f9 [...]`**. 이 식별자는 아직 계산되지 않았습니다. 따라서 새 사용자가 카운트에 추가됩니다.

![](assets/s_ncs_user_indicators_example_13.png)

**중간 계산:**

|  | 클릭한 수신자 | 클릭한 사람 | 열람한 수신자 |
|---|---|---|---|
| John | - | - | - |
| 마리 | - | - | +1 |
| 플로리안 | +1 | +1 | +1 |
| 알 수 없는 사람 | - | +1 | - |
| 중간 합계 | 1 | 2 | 2 |

## 4단계: 헨리 {#step-4--henry}

**[!UICONTROL Henry Macdonald]** 이(가) 자신의 인터넷 브라우저에서 쿠키를 거부하도록 구성했습니다. 그는 이메일을 열고 링크를 4번 클릭합니다.

![](assets/s_ncs_user_indicators_example_10.png)

Henry가 수행한 열린 클릭과 4번의 클릭은 다음 로그에 표시됩니다.

![](assets/s_ncs_user_indicators_example_5bis.png)

**수신자**: 열기 및 클릭 수가 동일한 수신자에게 할당됩니다(Henry). 이 수신자는 아직 카운트되지 않았으므로 Adobe Campaign은 해당 카운트에 수신자를 추가합니다.

**사람**: Henry의 브라우저가 쿠키를 허용하지 않으므로 클릭할 때마다 새 식별자(UUID)가 생성됩니다. 4번의 클릭은 각각 다른 사람으로부터 온 것으로 해석됩니다. 이러한 식별자는 아직 카운트되지 않았으므로 카운트에 추가됩니다.

**중간 계산:**

|  | 클릭한 수신자 | 클릭한 사람 | 열람한 수신자 |
|---|---|---|---|
| John | - | - | - |
| 마리 | - | - | +1 |
| 플로리안 | +1 | +1 | +1 |
| 알 수 없는 사람 | - | +1 | - |
| 헨리 | +1 | +4 | +1 |
| 중간 합계 | 2 | 6 | 3 |

## 요약 {#summary}

게재 수준에는 다음과 같은 결과가 있습니다.

![](assets/s_ncs_user_indicators_example.png)

* **[!UICONTROL Clicks]** (클릭한 수신자): 2
* **[!UICONTROL Distinct clicks for the population reached]** (클릭한 사람): 6
* **[!UICONTROL Distinct opens for the population reached]** (열람한 수신자): 3

원시 반응성 및 전방 추정은 다음과 같이 계산됩니다.

![](assets/s_ncs_user_indicators_example11.png)

* **[!UICONTROL Estimation of forwards]** = **B - A** (따라서 6 - 2 = 4)
* **[!UICONTROL Raw reactivity]** = **A / C** (따라서 2 / 3 = 66,67%)

>[!NOTE]
>
>다음 공식을 참조하십시오.
>
>* A는 **[!UICONTROL Clicks]** 표시기(클릭한 수신자).
>* B는 **[!UICONTROL Distinct clicks for the population reached]** 표시기(클릭한 사람).
>* C 는 **[!UICONTROL Distinct opens for the population reached]** 표시기(열람한 수신자).

