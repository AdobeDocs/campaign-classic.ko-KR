---
solution: Campaign Classic
product: campaign
title: 모집단 샘플 구성
description: 전용 사용 사례를 통해 A/B 테스트를 수행하는 방법을 살펴볼 수 있습니다.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 177b4e74c75e4fcca70dc90b5ff2c0406181e0f7
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 3%

---


# 모집단 샘플 구성 중 {#step-2--configuring-population-samples}

## 쿼리 활동 {#configuring-the-query-activity} 구성

* **[!UICONTROL Query]** 활동을 두 번 클릭합니다.

   ![](assets/use_case_abtesting_createrecipients_001.png)

* **[!UICONTROL Edit query]** 링크를 클릭하고 타깃팅할 수신자를 선택합니다.

   ![](assets/use_case_abtesting_createrecipients_002.png)

* **[!UICONTROL Query]** 활동을 **[!UICONTROL Split]** 활동에 연결합니다.

   ![](assets/use_case_abtesting_createrecipients_003.png)

## 분할 활동 구성 {#configuring-the-split-activity}

이 활동을 통해 다음과 같은 여러 모집단을 만들 수 있습니다.배달 A를 받는 사람, 배달 B를 받는 사람 및 나머지 모집단을 말합니다. 임의 선택을 사용하면 각 게재의 모집단의 일부만 타깃팅할 수 있습니다.

1. 모집단 A 만들기:

   * **[!UICONTROL Split]** 활동을 두 번 클릭합니다.

      ![](assets/use_case_abtesting_createrecipients_004.png)

   * 기존 탭에서 레이블을 인구 A로 변경합니다.

      ![](assets/use_case_abtesting_createrecipients_005.png)

   * **[!UICONTROL Limit the selected records]** 옵션을 선택합니다.

      ![](assets/use_case_abtesting_createrecipients_006.png)

   * **[!UICONTROL Edit]** 링크를 클릭하고 **[!UICONTROL Activate random sampling]**&#x200B;을 선택한 다음 **[!UICONTROL Next]**&#x200B;를 클릭합니다.

      ![](assets/use_case_abtesting_createrecipients_007.png)

   * 임계값을 10%로 설정한 다음 **[!UICONTROL Finish]**&#x200B;을 클릭합니다.

      ![](assets/use_case_abtesting_createrecipients_008.png)

1. 모집단 생성 B:

   * **[!UICONTROL Add]**&#x200B;을 클릭하여 모집단 B에 대한 새 탭을 만듭니다.

      ![](assets/use_case_abtesting_createrecipients_009.png)

   * 모집단 수를 이전에 비해 10%로 제한합니다.

      ![](assets/use_case_abtesting_createrecipients_010.png)

1. 나머지 채우기 만들기:

   * **[!UICONTROL General]** 탭으로 이동합니다. 

      ![](assets/use_case_abtesting_createrecipients_011.png)

   * **[!UICONTROL Generate complement]**&#x200B;을(를) 선택합니다.

      ![](assets/use_case_abtesting_createrecipients_012.png)

   * 이 모집단에는 A와 B가 포함되지 않도록 레이블을 변경하고 **[!UICONTROL OK]**&#x200B;을 클릭하여 활동을 닫습니다.

      ![](assets/use_case_abtesting_createrecipients_013.png)
