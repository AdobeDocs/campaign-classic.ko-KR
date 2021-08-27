---
product: campaign
title: 차원 변경
description: 차원 변경
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: c3de99f8-089f-4c7c-be11-f375a9463eaa
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 2%

---

# 차원 변경{#change-dimension}

![](../../assets/common.svg)

차원 변경 활동을 사용하면 타겟 구성 주기 동안 타겟팅 차원을 변경할 수 있습니다. 축 이동은 데이터 템플릿과 입력 차원에 따라 다릅니다. 예를 들어 &quot;계약&quot; 차원에서 &quot;클라이언트&quot; 차원으로 전환할 수 있습니다.

이 활동을 사용하여 새 대상의 추가 열을 정의할 수도 있습니다.

데이터 중복 제거 기준을 정의할 수 있습니다.

## 구성 모드 {#configuration-mode}

차원 변경 활동을 구성하려면 다음 단계를 적용합니다.

1. **[!UICONTROL Change dimension]** 필드를 통해 새 타겟팅 차원을 선택합니다.

   ![](assets/s_user_change_dimension_param1.png)

1. 차원 변경 중에 모든 요소를 유지하거나 출력에 유지할 요소를 선택할 수 있습니다. 다음 예에서는 최대입니다. 중복 수는 2로 설정됩니다.

   ![](assets/s_user_change_dimension_limit.png)

   하나의 레코드만 유지하도록 선택하면 컬렉션이 작업 스키마에 표시됩니다. 이 컬렉션은 하나의 레코드만 유지되므로 최종 결과에 타깃팅되지 않는 모든 레코드를 나타냅니다. 다른 모든 컬렉션과 마찬가지로 이 컬렉션에서도 합계를 계산하거나 정보를 열에 복구할 수 있습니다.

   예를 들어 **[!UICONTROL Customers]** 차원을 **[!UICONTROL Recipients]** 차원으로 변경하는 경우 구매 횟수를 추가하는 동안 특정 스토어의 고객을 타깃팅할 수 있습니다.

1. 이 정보를 모두 보존하지 않도록 선택하는 경우 중복 관리 모드를 구성할 수 있습니다.

   ![](assets/s_user_change_dimension_param2.png)

   파란색 화살표를 사용하여 중복 처리 우선순위를 정의할 수 있습니다.

   위의 예에서 수신자는 먼저 이메일 주소에 복제되고 필요한 경우 계좌 번호에 복제됩니다.

1. **[!UICONTROL Result]** 탭에서는 추가 정보를 추가할 수 있습니다.

   예를 들어 **Substring** 유형 함수를 사용하여 우편 번호를 기준으로 군을 복구할 수 있습니다. 방법은 다음과 같습니다.

   * **[!UICONTROL Add data...]** 링크를 클릭하고 **[!UICONTROL Data linked to the filtering dimension]** 을 선택합니다.

      ![](assets/wf_change-dimension_sample_01.png)

      >[!NOTE]
      >
      >추가 열 만들기 및 관리에 대한 자세한 내용은 [데이터 추가](query.md#adding-data)를 참조하십시오.

   * 이전 타겟팅 차원(축 전환 전)을 선택하고 수신자의 **[!UICONTROL Location]** 하위 트리에서 **[!UICONTROL Zip Code]**&#x200B;을(를) 선택한 다음 **[!UICONTROL Edit expression]**&#x200B;를 클릭합니다.

      ![](assets/wf_change-dimension_sample_02.png)

   * **[!UICONTROL Advanced selection]** 을 클릭하고 **[!UICONTROL Edit the formula using an expression]** 을 선택합니다.

      ![](assets/wf_change-dimension_sample_03.png)

   * 목록에서 제공되는 함수를 사용하고 수행할 계산을 지정합니다.

      ![](assets/wf_change-dimension_sample_04.png)

   * 마지막으로 방금 만든 열의 레이블을 입력합니다.

      ![](assets/wf_change-dimension_sample_05.png)

1. 워크플로우를 실행하여 이 구성 결과를 확인합니다. 차원 변경 활동 전후의 테이블의 데이터를 비교하고 다음 예와 같이 워크플로우 테이블의 구조를 비교합니다.

   ![](assets/wf_change-dimension_sample_06.png)

   ![](assets/wf_change-dimension_sample_07.png)
