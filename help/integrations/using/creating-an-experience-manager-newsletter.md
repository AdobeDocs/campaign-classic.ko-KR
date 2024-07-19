---
product: campaign
title: Experience Manager 뉴스레터 만들기
description: Experience Manager 뉴스레터 만들기
feature: Experience Manager Integration
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
audience: integrations
content-type: reference
exl-id: 9fa3ce08-3007-4c65-9841-bad339428b7c
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 1%

---

# Experience Manager 뉴스레터 만들기{#creating-an-experience-manager-newsletter}



예를 들어 이 통합을 사용하여 Adobe Experience Manager에서 뉴스레터를 생성하고 이메일 캠페인의 일부로 Adobe Campaign에서 사용할 수 있습니다.

**Adobe Experience Manager에서:**

1. AEM 작성자 인스턴스에서 페이지의 왼쪽 상단에 있는 **Adobe 경험** 로고를 클릭하고 **[!UICONTROL Sites]**&#x200B;을(를) 선택합니다.

   ![](assets/aem_uc_1.png)

1. **[!UICONTROL Campaigns > Name of your brand (here We.Retail) > Main Area > Email campaigns]**&#x200B;을(를) 선택합니다.
1. 페이지의 오른쪽 상단에 있는 **[!UICONTROL Create]** 단추를 클릭한 다음 **[!UICONTROL Page]**&#x200B;을(를) 선택합니다.

   ![](assets/aem_uc_2.png)

1. **[!UICONTROL Adobe Campaign Email (AC 6.1)]** 템플릿을 선택하고 뉴스레터 이름을 지정합니다.
1. 페이지가 만들어지면 **[!UICONTROL Page information]** 메뉴에 액세스하고 **[!UICONTROL Open Properties]**&#x200B;을(를) 클릭합니다.

   ![](assets/aem_uc_3.png)

1. **[!UICONTROL Cloud Services]** 탭에서 **[!UICONTROL Adobe Campaign]**&#x200B;을(를) **[!UICONTROL Cloud service configuration]**(으)로 선택하고 두 번째 드롭다운에서 Adobe Campaign 인스턴스를 선택합니다.

   ![](assets/aem_uc_4.png)

1. 구성 요소(예: Adobe Campaign의 개인화 필드)를 추가하여 이메일 콘텐츠를 편집합니다.
1. 전자 메일이 준비되면 **[!UICONTROL Page information]** 메뉴에 액세스하고 **[!UICONTROL Start workflow]**&#x200B;을(를) 클릭합니다.

   ![](assets/aem_uc_5.png)

1. 첫 번째 드롭다운에서 **[!UICONTROL Publish to Adobe Campaign]**&#x200B;을(를) 워크플로 모델로 선택하고 **[!UICONTROL Start workflow]**&#x200B;을(를) 클릭합니다.

   ![](assets/aem_uc_6.png)

1. 그런 다음 이전 단계로 **[!UICONTROL Approve for Campaign]** 워크플로우를 시작합니다.
1. 페이지 맨 위에 면책조항이 나타납니다. **[!UICONTROL Complete]**&#x200B;을(를) 클릭하여 검토를 확인하고 **[!UICONTROL Ok]**&#x200B;을(를) 클릭합니다.

   ![](assets/aem_uc_7.png)

1. **[!UICONTROL Complete]**&#x200B;을(를) 다시 클릭하고 **[!UICONTROL Next Step]** 드롭다운에서 **[!UICONTROL Newsletter approval]**&#x200B;을(를) 선택합니다.

   ![](assets/aem_uc_8.png)

이제 뉴스레터가 준비되었으며 Adobe Campaign에서 동기화되었습니다.

**Adobe Campaign에서:**

1. **[!UICONTROL Campaigns]** 탭에서 **[!UICONTROL Deliveries]**&#x200B;을(를) 클릭한 다음 **[!UICONTROL Create]**&#x200B;을(를) 클릭합니다.

   ![](assets/aem_uc_9.png)

1. **[!UICONTROL Delivery template]** 드롭다운에서 **[!UICONTROL Email delivery with AEM content (mailAEMContent)]** 템플릿을 선택합니다.

   ![](assets/aem_uc_10.png)

1. 게재에 **[!UICONTROL Label]**&#x200B;을(를) 추가하고 **[!UICONTROL Continue]**&#x200B;을(를) 클릭합니다.
1. **[!UICONTROL Synchronize]** 버튼을 클릭합니다.

   이 단추가 인터페이스에 표시되지 않으면 **[!UICONTROL Properties]** 단추를 클릭하고 **[!UICONTROL Advanced]** 탭을 선택하십시오. **[!UICONTROL AEM account]** 필드에 AEM 인스턴스가 있는 **[!UICONTROL Content editing mode]** 필드를 **[!UICONTROL AEM]**(으)로 설정해야 합니다.

   ![](assets/aem_uc_11.png)

1. Adobe Experience Manager에서 이전에 만든 게재를 선택하고 **[!UICONTROL Ok]**&#x200B;을(를) 클릭합니다.
1. AEM 게재를 변경하는 즉시 **[!UICONTROL Refresh content]** 단추를 클릭합니다.

   ![](assets/aem_uc_12.png)

이제 이메일을 대상자에게 보낼 준비가 되었습니다.
