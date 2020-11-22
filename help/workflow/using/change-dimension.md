---
solution: Campaign Classic
product: campaign
title: 차원 변경
description: 차원 변경
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 2%

---


# 차원 변경{#change-dimension}

차원 변경 활동을 사용하면 대상 구성 주기 동안 타깃팅 차원을 변경할 수 있습니다. 축 시프팅은 데이터 템플릿 및 입력 차원에 따라 다릅니다. 예를 들어 &quot;계약&quot; 차원에서 &quot;고객&quot; 차원으로 전환할 수 있습니다.

이 활동을 사용하여 새 대상의 추가 열을 정의할 수도 있습니다.

데이터 중복 제거 기준을 정의할 수 있습니다.

## 구성 모드 {#configuration-mode}

차원 변경 활동을 구성하려면 다음 단계를 적용합니다.

1. 필드를 통해 새 타깃팅 차원을 **[!UICONTROL Change dimension]** 선택합니다.

   ![](assets/s_user_change_dimension_param1.png)

1. 치수 변경 중에 모든 요소를 유지하거나 출력에서 유지할 요소를 선택할 수 있습니다. 다음 예에서 최대. 중복 수는 2로 설정됩니다.

   ![](assets/s_user_change_dimension_limit.png)

   하나의 레코드만 유지하도록 선택하면 작업 스키마에 컬렉션이 표시됩니다.이 컬렉션은 하나의 레코드만 유지되므로 최종 결과에서 타깃팅되지 않을 모든 레코드를 나타냅니다. 다른 모든 컬렉션과 마찬가지로 이 컬렉션도 집계 정보를 계산하거나 열의 정보를 복구할 수 있습니다.

   예를 들어 차원을 **[!UICONTROL Customers]** **[!UICONTROL Recipients]** 차원으로 변경하는 경우 특정 스토어의 고객을 타깃팅하고 구매 수를 추가할 수 있습니다.

1. 이 정보를 모두 유지하지 않도록 선택하는 경우 복제 관리 모드를 구성할 수 있습니다.

   ![](assets/s_user_change_dimension_param2.png)

   파란색 화살표를 사용하면 중복 처리 우선 순위를 정의할 수 있습니다.

   위의 예에서 수신자는 먼저 이메일 주소에 대한 중복을 제거한 다음 필요한 경우 계정 번호로 복제됩니다.

1. 이 **[!UICONTROL Result]** 탭에서는 추가 정보를 추가할 수 있습니다.

   예를 들어, Substring **유형 함수를 사용하여 우편번호에 따라 카운티를 복구할 수** 있습니다. 방법은 다음과 같습니다.

   * 링크를 **[!UICONTROL Add data...]** 클릭하고 선택합니다 **[!UICONTROL Data linked to the filtering dimension]**.

      ![](assets/wf_change-dimension_sample_01.png)

      >[!NOTE]
      >
      >추가 열 만들기 및 관리에 대한 자세한 내용은 데이터 [추가를 참조하십시오](../../workflow/using/query.md#adding-data).

   * 이전 타깃팅 차원(축 전환 전)을 선택하고 수신자 하위 트리 **[!UICONTROL Zip Code]** 에서 을 선택한 다음 을 **[!UICONTROL Location]** 클릭합니다 **[!UICONTROL Edit expression]**.

      ![](assets/wf_change-dimension_sample_02.png)

   * 을 클릭하고 **[!UICONTROL Advanced selection]** 선택합니다 **[!UICONTROL Edit the formula using an expression]**.

      ![](assets/wf_change-dimension_sample_03.png)

   * 목록에 제공된 함수를 사용하고 수행할 계산을 지정합니다.

      ![](assets/wf_change-dimension_sample_04.png)

   * 마지막으로 방금 만든 열의 레이블을 입력합니다.

      ![](assets/wf_change-dimension_sample_05.png)

1. 워크플로우를 실행하여 이 구성 결과를 확인합니다. 다음 예에서 보듯이 차원 변경 활동 전과 후 테이블의 데이터를 비교하고 워크플로우 테이블의 구조를 비교합니다.

   ![](assets/wf_change-dimension_sample_06.png)

   ![](assets/wf_change-dimension_sample_07.png)

