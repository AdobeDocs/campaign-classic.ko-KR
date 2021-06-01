---
product: campaign
title: 모집단 샘플 구성
description: 전용 사용 사례를 통해 A/B 테스트를 수행하는 방법을 알아봅니다.
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: 1ca01cab-734a-4299-b112-04eec51222fb
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 6%

---

# 모집단 샘플 구성 {#step-2--configuring-population-samples}

## 쿼리 활동 구성 {#configuring-the-query-activity}

* **[!UICONTROL Query]** 활동을 두 번 클릭합니다.

   ![](assets/use_case_abtesting_createrecipients_001.png)

* **[!UICONTROL Edit query]** 링크를 클릭하고 타겟팅할 수신자를 선택합니다.

   ![](assets/use_case_abtesting_createrecipients_002.png)

* **[!UICONTROL Query]** 활동을 **[!UICONTROL Split]** 활동에 연결합니다.

   ![](assets/use_case_abtesting_createrecipients_003.png)

## 분할 활동 구성 {#configuring-the-split-activity}

이 활동을 사용하면 여러 모집단을 만들 수 있습니다.배달 A를 받는 사람, 배달 B를 받는 사람 및 나머지 모집단을 말합니다. 임의 선택을 사용하면 각 게재의 모집단의 일부만 타겟팅할 수 있습니다.

1. 모집단 A 만들기:

   * **[!UICONTROL Split]** 활동을 두 번 클릭합니다.

      ![](assets/use_case_abtesting_createrecipients_004.png)

   * 기존 탭에서 레이블을 모집단 A로 변경합니다.

      ![](assets/use_case_abtesting_createrecipients_005.png)

   * **[!UICONTROL Limit the selected records]** 옵션을 선택합니다.

      ![](assets/use_case_abtesting_createrecipients_006.png)

   * **[!UICONTROL Edit]** 링크를 클릭하고 **[!UICONTROL Activate random sampling]** 를 선택한 다음 **[!UICONTROL Next]** 를 클릭합니다.

      ![](assets/use_case_abtesting_createrecipients_007.png)

   * 임계값을 10%로 설정한 다음 **[!UICONTROL Finish]**&#x200B;을 클릭합니다.

      ![](assets/use_case_abtesting_createrecipients_008.png)

1. 모집단 B 만들기:

   * **[!UICONTROL Add]** 을 클릭하여 모집단 B에 대한 새 탭을 만듭니다.

      ![](assets/use_case_abtesting_createrecipients_009.png)

   * 모집단을 이전 10%로 제한합니다.

      ![](assets/use_case_abtesting_createrecipients_010.png)

1. 나머지 모집단 만들기:

   * **[!UICONTROL General]** 탭으로 이동합니다. 

      ![](assets/use_case_abtesting_createrecipients_011.png)

   * **[!UICONTROL Generate complement]**&#x200B;을(를) 선택합니다.

      ![](assets/use_case_abtesting_createrecipients_012.png)

   * 이 모집단에 A와 B가 포함되지 않도록 레이블을 변경하고 **[!UICONTROL OK]** 을(를) 클릭하여 활동을 닫습니다.

      ![](assets/use_case_abtesting_createrecipients_013.png)

이제 두 개의 게재 템플릿을 만들 수 있습니다( [3단계 참조).두 개의 게재 템플릿](../../delivery/using/a-b-testing-uc-delivery-templates.md))을 만듭니다.
