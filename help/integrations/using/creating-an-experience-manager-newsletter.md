---
product: campaign
title: Experience Manager 뉴스레터 만들기
description: Experience Manager 뉴스레터 만들기
audience: integrations
content-type: reference
exl-id: 9fa3ce08-3007-4c65-9841-bad339428b7c
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 1%

---

# Experience Manager 뉴스레터 만들기{#creating-an-experience-manager-newsletter}

이 통합은 예를 들어 Adobe Experience Manager에서 뉴스레터를 만든 후 이메일 캠페인의 일부로 Adobe Campaign에서 사용할 수 있습니다.

이 통합을 사용하는 방법에 대한 자세한 예는 이 [단계별 안내서](https://helpx.adobe.com/campaign/kb/acc-aem.html)를 참조하십시오.

**Adobe Experience Manager에서:**

1. AEM 작성자 인스턴스에서 페이지 왼쪽 상단에 있는 **Adobe Experience** 로고를 클릭하고 **[!UICONTROL Sites]**&#x200B;를 선택합니다.

   ![](assets/aem_uc_1.png)

1. **[!UICONTROL Campaigns > Name of your brand (here We.Retail) > Main Area > Email campaigns]**&#x200B;을(를) 선택합니다.
1. 페이지 오른쪽 상단에 있는 **[!UICONTROL Create]** 단추를 클릭한 다음 **[!UICONTROL Page]** 을 선택합니다.

   ![](assets/aem_uc_2.png)

1. **[!UICONTROL Adobe Campaign Email (AC 6.1)]** 템플릿을 선택하고 Newsletter 이름을 지정합니다.
1. 페이지가 만들어지면 **[!UICONTROL Page information]** 메뉴에 액세스하고 **[!UICONTROL Open Properties]** 를 클릭합니다.

   ![](assets/aem_uc_3.png)

1. **[!UICONTROL Cloud Services]** 탭에서 **[!UICONTROL Adobe Campaign]** 을 **[!UICONTROL Cloud service configuration]**(으)로 선택하고 두 번째 드롭다운에서 Adobe Campaign 인스턴스를 선택합니다.

   ![](assets/aem_uc_4.png)

1. 구성 요소를 추가하여 이메일 콘텐츠를 편집합니다(예: Adobe Campaign의 개인화 필드).
1. 전자 메일이 준비되면 **[!UICONTROL Page information]** 메뉴에 액세스하고 **[!UICONTROL Start workflow]** 를 클릭합니다.

   ![](assets/aem_uc_5.png)

1. 첫 번째 드롭다운에서 **[!UICONTROL Publish to Adobe Campaign]** 을 워크플로우 모델로 선택하고 **[!UICONTROL Start workflow]** 을(를) 클릭합니다.

   ![](assets/aem_uc_6.png)

1. 그런 다음 이전 단계로 **[!UICONTROL Approve for Campaign]** 워크플로우를 시작합니다.
1. 면책조항이 페이지 맨 위에 나타납니다. **[!UICONTROL Complete]** 을 클릭하여 검토를 확인하고 **[!UICONTROL Ok]** 를 클릭합니다.

   ![](assets/aem_uc_7.png)

1. 다시 **[!UICONTROL Complete]** 을 클릭하고 **[!UICONTROL Next Step]** 드롭다운에서 **[!UICONTROL Newsletter approval]** 을 선택합니다.

   ![](assets/aem_uc_8.png)

이제 뉴스레터가 Adobe Campaign에서 준비 및 동기화됩니다.

**Adobe Campaign에서:**

1. **[!UICONTROL Campaigns]** 탭에서 **[!UICONTROL Deliveries]** 를 클릭한 다음 **[!UICONTROL Create]** 를 클릭합니다.

   ![](assets/aem_uc_9.png)

1. **[!UICONTROL Delivery template]** 드롭다운에서 **[!UICONTROL Email delivery with AEM content (mailAEMContent)]** 템플릿을 선택합니다.

   ![](assets/aem_uc_10.png)

1. 게재에 **[!UICONTROL Label]**&#x200B;을(를) 추가하고 **[!UICONTROL Continue]**&#x200B;을(를) 클릭합니다.
1. **[!UICONTROL Synchronize]** 버튼을 클릭합니다.

   인터페이스에 이 단추가 표시되지 않으면 **[!UICONTROL Properties]** 버튼을 클릭하고 **[!UICONTROL Advanced]** 탭을 선택합니다. **[!UICONTROL Content editing mode]** 필드는 **[!UICONTROL AEM account]** 필드에 AEM 인스턴스를 사용하여 **[!UICONTROL AEM]** 로 설정해야 합니다.

   ![](assets/aem_uc_11.png)

1. Adobe Experience Manager에서 이전에 만든 게재를 선택하고 **[!UICONTROL Ok]** 을 클릭합니다.
1. AEM 게재에 일부 변경 사항이 적용되면 바로 **[!UICONTROL Refresh content]** 버튼을 클릭합니다.

   ![](assets/aem_uc_12.png)

이제 이메일을 대상자에게 보낼 준비가 되었습니다.
