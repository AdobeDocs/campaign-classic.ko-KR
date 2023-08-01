---
product: campaign
title: Experience Manager 뉴스레터 만들기
description: Experience Manager 뉴스레터 만들기
feature: Experience Manager Integration
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
audience: integrations
content-type: reference
exl-id: 9fa3ce08-3007-4c65-9841-bad339428b7c
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 2%

---

# Experience Manager 뉴스레터 만들기{#creating-an-experience-manager-newsletter}



예를 들어 이 통합을 사용하여 Adobe Experience Manager에서 뉴스레터를 생성하고 이메일 캠페인의 일부로 Adobe Campaign에서 사용할 수 있습니다.

**Adobe Experience Manager에서:**

1. AEM 작성자 인스턴스에서 **Adobe 경험** 로고는 페이지의 왼쪽 상단에 있으며 **[!UICONTROL Sites]**.

   ![](assets/aem_uc_1.png)

1. **[!UICONTROL Campaigns > Name of your brand (here We.Retail) > Main Area > Email campaigns]**&#x200B;을(를) 선택합니다.
1. 다음을 클릭합니다. **[!UICONTROL Create]** 페이지의 오른쪽 상단에 있는 버튼을 선택한 다음 을 선택합니다. **[!UICONTROL Page]**.

   ![](assets/aem_uc_2.png)

1. 다음 항목 선택 **[!UICONTROL Adobe Campaign Email (AC 6.1)]** 템플릿을 만들고 뉴스레터 이름을 지정합니다.
1. 페이지가 만들어지면 **[!UICONTROL Page information]** 메뉴 및 클릭 **[!UICONTROL Open Properties]**.

   ![](assets/aem_uc_3.png)

1. 다음에서 **[!UICONTROL Cloud Services]** 탭, 선택 **[!UICONTROL Adobe Campaign]** 다음으로: **[!UICONTROL Cloud service configuration]** 두 번째 드롭다운에서 Adobe Campaign 인스턴스를 탐색합니다.

   ![](assets/aem_uc_4.png)

1. 구성 요소(예: Adobe Campaign의 개인화 필드)를 추가하여 이메일 콘텐츠를 편집합니다.
1. 이메일이 준비되면 **[!UICONTROL Page information]** 메뉴 및 클릭 **[!UICONTROL Start workflow]**.

   ![](assets/aem_uc_5.png)

1. 첫 번째 드롭다운에서 **[!UICONTROL Publish to Adobe Campaign]** 워크플로우 모델로 사용하고 클릭 **[!UICONTROL Start workflow]**.

   ![](assets/aem_uc_6.png)

1. 그런 다음 이전 단계로 을(를) 실행합니다. **[!UICONTROL Approve for Campaign]** 워크플로입니다.
1. 페이지 맨 위에 면책조항이 나타납니다. 클릭 **[!UICONTROL Complete]** 검토를 확인하고 **[!UICONTROL Ok]**.

   ![](assets/aem_uc_7.png)

1. 다시 클릭 **[!UICONTROL Complete]** 및 선택 **[!UICONTROL Newsletter approval]** 다음에서 **[!UICONTROL Next Step]** 드롭다운.

   ![](assets/aem_uc_8.png)

이제 뉴스레터가 준비되었으며 Adobe Campaign에서 동기화되었습니다.

**Adobe Campaign에서:**

1. 다음에서 **[!UICONTROL Campaigns]** 탭을 클릭하고 **[!UICONTROL Deliveries]** 그러면 **[!UICONTROL Create]**.

   ![](assets/aem_uc_9.png)

1. 다음에서 **[!UICONTROL Delivery template]** 드롭다운에서 **[!UICONTROL Email delivery with AEM content (mailAEMContent)]** 템플릿.

   ![](assets/aem_uc_10.png)

1. 추가 **[!UICONTROL Label]** 게재 후 클릭 **[!UICONTROL Continue]**.
1. **[!UICONTROL Synchronize]** 버튼을 클릭합니다.

   이 단추가 인터페이스에 표시되지 않으면 **[!UICONTROL Properties]** 버튼을 클릭하고 다음을 선택합니다. **[!UICONTROL Advanced]** 탭. 다음 **[!UICONTROL Content editing mode]** 필드는 로 설정해야 합니다. **[!UICONTROL AEM]** 에 AEM 인스턴스 포함 **[!UICONTROL AEM account]** 필드.

   ![](assets/aem_uc_11.png)

1. Adobe Experience Manager에서 이전에 만든 게재를 선택하고 **[!UICONTROL Ok]**.
1. 다음을 클릭합니다. **[!UICONTROL Refresh content]** AEM 게재가 변경되는 즉시 버튼화합니다.

   ![](assets/aem_uc_12.png)

이제 이메일을 대상자에게 보낼 준비가 되었습니다.
