---
product: campaign
title: 게재 템플릿 만들기
description: 전용 사용 사례를 통해 A/B 테스트를 수행하는 방법에 대해 알아봅니다
role: User
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: A/B Testing
exl-id: 77b3a906-b76e-49e1-b524-b6f1ae537259
TQID: https://experienceleague.adobe.com/eble-fTf8Rk7fFGnKNh5pLUhMaLdZlJrG-vjrhbHx1I
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: e739ee2b-6228-412e-878f-45de0791417d
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 104
ht-degree: 5%

---

# AB 테스트: 게재 템플릿 만들기 {#step-3--creating-two-delivery-templates}

이제 두 개의 게재 템플릿을 만들겠습니다. 각 템플릿은 **[!UICONTROL Split]** 활동에 연결된 **[!UICONTROL Email delivery]** 활동에서 참조됩니다. [Campaign v8 설명서](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-templates.html){target="_blank"}를 참조하세요.

1. **[!UICONTROL Resources > Delivery template]** 폴더를 찾습니다.
1. **[!UICONTROL Email]** 게재 템플릿을 복제합니다.

   ![](assets/use_case_abtesting_deliverymodel_001.png)

1. 게재 A에 사용할 콘텐츠를 만듭니다.

   ![](assets/use_case_abtesting_deliverymodel_002.png)

1. 이 프로세스를 반복하여 게재 B에 대한 템플릿을 만듭니다.

   ![](assets/use_case_abtesting_deliverymodel_003.png)

이제 워크플로우에서 게재를 구성할 수 있습니다. [자세히 알아보기](a-b-testing-uc-configuring-deliveries.md).
