---
solution: Campaign Classic
product: campaign
title: Experience Manager 뉴스레터 만들기
description: Experience Manager 뉴스레터 만들기
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 1%

---


# Experience Manager 뉴스레터 만들기{#creating-an-experience-manager-newsletter}

이 통합을 예로 들어 Adobe Experience Manager에서 뉴스레터를 만든 다음 Adobe Campaign에서 이메일 캠페인의 일부로 사용할 수 있습니다.

이 통합을 사용하는 방법에 대한 자세한 예제는 이 [단계별 안내서](https://helpx.adobe.com/campaign/kb/acc-aem.html)를 참조하십시오.

**Adobe Experience Manager에서:**

1. AEM 작성자 인스턴스에서 페이지 왼쪽 상단에 있는 **Adobe Experience** 로고를 클릭하고 **[!UICONTROL Sites]**&#x200B;를 선택합니다.

   ![](assets/aem_uc_1.png)

1. **[!UICONTROL Campaigns > Name of your brand (here We.Retail) > Main Area > Email campaigns]**&#x200B;을(를) 선택합니다.
1. 페이지 오른쪽 위에 있는 **[!UICONTROL Create]** 단추를 클릭한 다음 **[!UICONTROL Page]**&#x200B;을 선택합니다.

   ![](assets/aem_uc_2.png)

1. **[!UICONTROL Adobe Campaign Email (AC 6.1)]** 템플릿을 선택하고 뉴스레터 이름을 지정합니다.
1. 페이지가 만들어지면 **[!UICONTROL Page information]** 메뉴에 액세스하여 **[!UICONTROL Open Properties]**&#x200B;을 클릭합니다.

   ![](assets/aem_uc_3.png)

1. **[!UICONTROL Cloud Services]** 탭에서 **[!UICONTROL Adobe Campaign]**&#x200B;을 **[!UICONTROL Cloud service configuration]**&#x200B;로 선택하고 두 번째 드롭다운에서 Adobe Campaign 인스턴스를 선택합니다.

   ![](assets/aem_uc_4.png)

1. 구성 요소(예: Adobe Campaign의 개인화 필드)를 추가하여 이메일 컨텐츠를 편집합니다.
1. 전자 메일이 준비되면 **[!UICONTROL Page information]** 메뉴에 액세스하고 **[!UICONTROL Start workflow]**&#x200B;을 클릭합니다.

   ![](assets/aem_uc_5.png)

1. 첫 번째 드롭다운에서 워크플로우 모델로 **[!UICONTROL Publish to Adobe Campaign]**&#x200B;을 선택하고 **[!UICONTROL Start workflow]**&#x200B;을 클릭합니다.

   ![](assets/aem_uc_6.png)

1. 그런 다음 이전 단계로 **[!UICONTROL Approve for Campaign]** 작업 과정을 시작합니다.
1. 면책사항이 페이지 상단에 표시됩니다. **[!UICONTROL Complete]**&#x200B;을 클릭하여 검토를 확인하고 **[!UICONTROL Ok]**&#x200B;을 클릭합니다.

   ![](assets/aem_uc_7.png)

1. **[!UICONTROL Complete]**&#x200B;을 다시 클릭하고 **[!UICONTROL Next Step]** 드롭다운에서 **[!UICONTROL Newsletter approval]**&#x200B;을 선택합니다.

   ![](assets/aem_uc_8.png)

이제 뉴스레터가 Adobe Campaign에서 준비 및 동기화됩니다.

**Adobe Campaign에서:**

1. **[!UICONTROL Campaigns]** 탭에서 **[!UICONTROL Deliveries]**, **[!UICONTROL Create]**&#x200B;를 차례로 클릭합니다.

   ![](assets/aem_uc_9.png)

1. **[!UICONTROL Delivery template]** 드롭다운에서 **[!UICONTROL Email delivery with AEM content (mailAEMContent)]** 템플릿을 선택합니다.

   ![](assets/aem_uc_10.png)

1. 배달에 **[!UICONTROL Label]**&#x200B;을(를) 추가하고 **[!UICONTROL Continue]**&#x200B;을 클릭합니다.
1. **[!UICONTROL Synchronize]** 버튼을 클릭합니다.

   인터페이스에 이 단추가 표시되지 않으면 **[!UICONTROL Properties]** 단추를 클릭하고 **[!UICONTROL Advanced]** 탭을 선택합니다. **[!UICONTROL Content editing mode]** 필드는 **[!UICONTROL AEM account]** 필드에 AEM 인스턴스와 함께 **[!UICONTROL AEM]**&#x200B;으로 설정해야 합니다.

   ![](assets/aem_uc_11.png)

1. Adobe Experience Manager에서 이전에 만든 배달을 선택하고 **[!UICONTROL Ok]**&#x200B;을 클릭합니다.
1. AEM 전달에 대한 일부 변경 사항이 있는 즉시 **[!UICONTROL Refresh content]** 단추를 클릭합니다.

   ![](assets/aem_uc_12.png)

이제 고객에게 이메일을 보낼 준비가 되었습니다.
