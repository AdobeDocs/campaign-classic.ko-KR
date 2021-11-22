---
product: campaign
title: 게재 보고서
description: 게재 보고서
audience: reporting
content-type: reference
topic-tags: accessing-built-in-reports
exl-id: 69b810f3-aa8b-4ab5-95c1-831257d7fcb9
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 6%

---

# 사람 및 수신자 {#person-people-and-recipients}

![](../../assets/common.svg)

이 샘플은 Adobe Campaign의 개인/사람과 수신자 간의 차이를 이해하는 데 도움이 됩니다. 다음 지표에 대한 계산 방법을 자세히 설명하면서 사람과 수신자 간의 차이를 강조 표시하기 위해 여러 사람에게 게재를 보냅니다.

* **[!UICONTROL Clicks]**
* **[!UICONTROL Distinct clicks for the population reached]**
* **[!UICONTROL Distinct opens for the population reached]**
* **[!UICONTROL Estimation of forwards]**
* **[!UICONTROL Raw reactivity]**

>[!NOTE]
>
>이러한 표시기는 **[!UICONTROL Tracking indicators]** 보고서 세트에 대해 설명합니다. 자세한 내용은 [지표 추적](../../reporting/using/delivery-reports.md#tracking-indicators).

게재에 세 개의 링크가 추가됩니다. 4명의 수신자에게 전송됩니다.

![](assets/s_ncs_user_indicators_example_1.png)

* **[!UICONTROL John Davis]** : 이 수신자는 이메일을 열지 않으므로 링크가 클릭되지 않습니다.
* **[!UICONTROL Marie Stuart]** : 이메일을 열지만 링크를 클릭하지 않습니다.
* **[!UICONTROL Florian David]** : 이메일을 열고 링크를 9번 클릭합니다. 그는 또한 이메일을 열고 두 번 클릭하는 사람에게 전자 메일을 전달하기도 합니다.
* **[!UICONTROL Henry Macdonald]** : 이 수신자는 쿠키를 거부하도록 인터넷 브라우저를 구성했습니다. 이메일을 열고 링크를 4번 클릭합니다.

다음 추적 로그가 반환됩니다.

![](assets/s_ncs_user_indicators_example_2.png)

사람과 수신자의 계산 방법을 보다 명확하게 이해하기 위해 각 프로필의 로그를 분석하려고 합니다.

## 1단계: 존 {#step-1--john}

**[!UICONTROL John Davis]** 은 이메일을 열지 않으므로 링크가 클릭되지 않습니다.

![](assets/s_ncs_user_indicators_example_8.png)

John은 이메일을 열거나 클릭하지 않았으므로 로그에 표시되지 않습니다.

**중간 계산:**

|  | 클릭한 수신자 | 클릭한 사람 | 연 수신자 |
|---|---|---|---|
| 존 | - | - | - |
| 중간 합계 | 0 | 0 | 0 |

## 2단계: 마리 {#step-2--marie}

**[!UICONTROL Marie Stuart]** 이메일을 열지만 링크를 클릭하지 않습니다.

![](assets/s_ncs_user_indicators_example_7.png)

Marie의 열기 항목이 다음 로그에 표시됩니다.

![](assets/s_ncs_user_indicators_example_4bis.png)

열기가 수신자에게 지정됩니다. 마리 따라서 Adobe Campaign은 카운트에 새 수신자를 추가합니다.

**중간 계산:**

|  | 클릭한 수신자 | 클릭한 사람 | 연 수신자 |
|---|---|---|---|
| 존 | - | - | - |
| 마리 | - | - | +1 |
| 중간 합계 | 0 | 0 | 1 |

## 3단계: 플로리안 {#step-3--florian}

**[!UICONTROL Florian David]** 이메일을 열고 링크를 9번 클릭합니다. 그는 또한 이메일을 열고 두 번 클릭하는 사람에게 전자 메일을 전달하기도 합니다.

![](assets/s_ncs_user_indicators_example_9.png)

플로리안의 작업(한 번의 열기 및 9번의 클릭)은 다음 로그에 표시됩니다.

![](assets/s_ncs_user_indicators_example_3bis.png)

**수신자**: 열기와 클릭이 동일한 수신자(플로리안)에게 할당됩니다. 이 수신자는 이전 수신자(마리)와 다르므로 Adobe Campaign은 새 수신자를 개수에 추가합니다.

사람: 이 수신자의 브라우저가 쿠키를 허용하므로 동일한 UUID(식별자)가 모든 클릭 로그에 할당되었음을 알 수 있습니다. **`fe37a503 [...]`**. Adobe Campaign은 이러한 클릭을 동일한 사람에게 속하는 것으로 올바르게 식별합니다. 새 사람이 카운트에 추가됩니다.

**중간 계산:**

|  | 클릭한 수신자 | 클릭한 사람 | 연 수신자 |
|---|---|---|---|
| 존 | - | - | - |
| 마리 | - | - | +1 |
| 플로리안 | +1 | +1 | +1 |
| 중간 합계 | 1 | 1 | 2 |

다음 로그는 Florida가 e-메일을 전달했던 사람이 수행한 두 번의 클릭과 오픈과 일치합니다.

![](assets/s_ncs_user_indicators_example_6bis.png)

**수신자**: 열기 및 클릭 수가 이메일을 전달한 수신자(플로리안)에게 할당됩니다. 이 수신자가 이미 계산되었으므로 수신자 수는 동일하게 유지됩니다.

![](assets/s_ncs_user_indicators_example_12.png)

**사람**: 클릭과 관련하여 동일한 식별자(UUID)가 모든 로그에 할당되어 있음을 알 수 있습니다. **`9ab648f9 [...]`**. 이 식별자는 아직 계산되지 않았습니다. 따라서 새 사람이 카운트에 추가됩니다.

![](assets/s_ncs_user_indicators_example_13.png)

**중간 계산:**

|  | 클릭한 수신자 | 클릭한 사람 | 연 수신자 |
|---|---|---|---|
| 존 | - | - | - |
| 마리 | - | - | +1 |
| 플로리안 | +1 | +1 | +1 |
| 알 수 없는 사람 | - | +1 | - |
| 중간 합계 | 1 | 2개 | 2개 |

## 4단계: 헨리 {#step-4--henry}

**[!UICONTROL Henry Macdonald]** 이(가) 쿠키를 거부하도록 인터넷 브라우저를 구성했습니다. 이메일을 열고 링크를 4번 클릭합니다.

![](assets/s_ncs_user_indicators_example_10.png)

Henry가 수행한 열기 및 4번의 클릭이 다음 로그에 표시됩니다.

![](assets/s_ncs_user_indicators_example_5bis.png)

**수신자**: 열기 및 클릭이 동일한 수신자(Henry)에게 할당됩니다. 이 수신자가 아직 카운트되지 않았으므로 Adobe Campaign에서 수신자를 카운트에 추가합니다.

**사람**: Henry의 브라우저가 쿠키를 승인하지 않으므로 각 클릭에 대해 새 식별자(UUID)가 생성됩니다. 4번의 클릭마다 다른 사람이 한 클릭으로 해석됩니다. 이러한 식별자가 아직 계산되지 않았으므로 개수에 추가됩니다.

**중간 계산:**

|  | 클릭한 수신자 | 클릭한 사람 | 연 수신자 |
|---|---|---|---|
| 존 | - | - | - |
| 마리 | - | - | +1 |
| 플로리안 | +1 | +1 | +1 |
| 알 수 없는 사람 | - | +1 | - |
| 헨리 | +1 | +4 | +1 |
| 중간 합계 | 2개 | 6 | 3 |

## 요약 {#summary}

게재 수준에서 다음 결과가 있습니다.

![](assets/s_ncs_user_indicators_example.png)

* **[!UICONTROL Clicks]** (클릭한 수신자): 2개
* **[!UICONTROL Distinct clicks for the population reached]** (클릭한 사람): 6
* **[!UICONTROL Distinct opens for the population reached]** (연 수신자): 3

원시 반응성 및 전달 추정은 다음과 같이 계산됩니다.

![](assets/s_ncs_user_indicators_example11.png)

* **[!UICONTROL Estimation of forwards]** = **B - A** (따라서 6 - 2 = 4)
* **[!UICONTROL Raw reactivity]** = **A / C** (따라서 2 / 3 = 66,67%)

>[!NOTE]
>
>다음 공식:
>
>* 는 를 나타냅니다 **[!UICONTROL Clicks]** 표시기(클릭한 수신자).
>* B는 **[!UICONTROL Distinct clicks for the population reached]** 지표(클릭한 사람)
>* C는 **[!UICONTROL Distinct opens for the population reached]** 표시기(연 수신자)

