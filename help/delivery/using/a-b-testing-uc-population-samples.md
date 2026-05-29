---
product: campaign
title: 모집단 샘플 구성
description: 전용 사용 사례를 통해 A/B 테스트를 수행하는 방법에 대해 알아봅니다
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: A/B Testing
role: User
exl-id: 1ca01cab-734a-4299-b112-04eec51222fb
TQID: https://experienceleague.adobe.com/HWbHtS5F-je1GiNdr25dD17W-MpJ-K3xp-T8kKC-c10
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
feature_v2: id: b631758a-142d-425f-b9aa-f756d85cb979id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2: id: d5bbe3da-ba85-4242-817e-54f7c4b943e0id: e739ee2b-6228-412e-878f-45de0791417d
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 185
ht-degree: 8%

---

# AB 테스트: 모집단 샘플 구성 {#step-2--configuring-population-samples}

## 쿼리 활동 구성 {#configuring-the-query-activity}

* **[!UICONTROL Query]** 활동을 두 번 클릭합니다.

  ![](assets/use_case_abtesting_createrecipients_001.png)

* **[!UICONTROL Edit query]** 링크를 클릭하고 타겟팅할 수신자를 선택합니다.

  ![](assets/use_case_abtesting_createrecipients_002.png)

* **[!UICONTROL Query]** 활동을 **[!UICONTROL Split]** 활동에 연결합니다.

  ![](assets/use_case_abtesting_createrecipients_003.png)

## 분할 활동 구성 {#configuring-the-split-activity}

이 활동을 사용하면 게재 A를 받는 모집단과 게재 B를 받는 모집단과 나머지 모집단을 만들 수 있습니다. 무작위 선택을 사용하면 각 게재의 모집단 일부를 타깃팅할 수 있습니다.

1. 모집단 A 만들기:

   * **[!UICONTROL Split]** 활동을 두 번 클릭합니다.

     ![](assets/use_case_abtesting_createrecipients_004.png)

   * 기존 탭에서 레이블을 모집단 A로 변경합니다.

     ![](assets/use_case_abtesting_createrecipients_005.png)

   * **[!UICONTROL Limit the selected records]** 옵션을 선택합니다.

     ![](assets/use_case_abtesting_createrecipients_006.png)

   * **[!UICONTROL Edit]** 링크를 클릭하고 **[!UICONTROL Activate random sampling]**&#x200B;을(를) 선택한 다음 **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다.

     ![](assets/use_case_abtesting_createrecipients_007.png)

   * 임계값을 10%로 설정한 다음 **[!UICONTROL Finish]**&#x200B;을(를) 클릭합니다.

     ![](assets/use_case_abtesting_createrecipients_008.png)

1. 모집단 B 만들기:

   * 모집단 B에 대한 새 탭을 만들려면 **[!UICONTROL Add]**&#x200B;을(를) 클릭합니다.

     ![](assets/use_case_abtesting_createrecipients_009.png)

   * 이전처럼 모집단을 10%로 제한합니다.

     ![](assets/use_case_abtesting_createrecipients_010.png)

1. 나머지 모집단 만들기:

   * **[!UICONTROL General]** 탭으로 이동합니다.

     ![](assets/use_case_abtesting_createrecipients_011.png)

   * **[!UICONTROL Generate complement]**&#x200B;을(를) 선택합니다.

     ![](assets/use_case_abtesting_createrecipients_012.png)

   * 이 모집단에 A와 B가 모두 포함되지 않도록 레이블을 변경하고 **[!UICONTROL OK]**&#x200B;을(를) 클릭하여 활동을 닫습니다.

     ![](assets/use_case_abtesting_createrecipients_013.png)

이제 두 개의 게재 템플릿을 만들 수 있습니다. [자세히 알아보기](a-b-testing-uc-delivery-templates.md)).
