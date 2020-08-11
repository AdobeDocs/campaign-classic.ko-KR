---
title: Experience Manager 뉴스레터 만들기
seo-title: Experience Manager 뉴스레터 만들기
description: Experience Manager 뉴스레터 만들기
seo-description: null
page-status-flag: never-activated
uuid: 75cf4891-06a6-42d2-9b22-b4d93e0dc64a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 627ade78-96b3-4a6e-9ace-74610a3c8d1a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: bc54cef4c44be4c694e062f56685dbb09d2fcf8e
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 1%

---


# Experience Manager 뉴스레터 만들기{#creating-an-experience-manager-newsletter}

이 통합을 사용하여 Adobe Experience Manager에서 뉴스레터를 만든 다음 이메일 캠페인의 일부로 Adobe Campaign에서 사용할 수 있습니다.

이 통합 사용 방법에 대한 자세한 예는 이 [단계별 가이드를 참조하십시오](https://helpx.adobe.com/campaign/kb/acc-aem.html).

**Adobe Experience Manager에서:**

1. AEM 작성자 인스턴스의 왼쪽 상단에 있는 **Adobe Experience** 로고를 클릭하고 선택합니다 **[!UICONTROL Sites]**.

   ![](assets/aem_uc_1.png)

1. **[!UICONTROL Campaigns > Name of your brand (here We.Retail) > Main Area > Email campaigns]**&#x200B;을(를) 선택합니다.
1. 페이지 오른쪽 위에 있는 **[!UICONTROL Create]** 단추를 클릭한 다음 선택합니다 **[!UICONTROL Page]**.

   ![](assets/aem_uc_2.png)

1. 템플릿을 선택하고 **[!UICONTROL Adobe Campaign Email (AC 6.1)]** 뉴스레터의 이름을 지정합니다.
1. 페이지가 만들어지면 **[!UICONTROL Page information]** 메뉴에 액세스하여 클릭합니다 **[!UICONTROL Open Properties]**.

   ![](assets/aem_uc_3.png)

1. 탭 **[!UICONTROL Cloud Services]** 에서 두 번째 드롭다운에서 **[!UICONTROL Adobe Campaign]** as **[!UICONTROL Cloud service configuration]** 와 사용자의 Adobe Campaign 인스턴스를 선택합니다.

   ![](assets/aem_uc_4.png)

1. 구성 요소(예: Adobe Campaign의 개인화 필드)를 추가하여 이메일 컨텐츠를 편집할 수 있습니다.
1. 이메일이 준비되면 **[!UICONTROL Page information]** 메뉴에 액세스하고 을 클릭합니다 **[!UICONTROL Start workflow]**.

   ![](assets/aem_uc_5.png)

1. 첫 번째 드롭다운에서 워크플로우 모델 **[!UICONTROL Publish to Adobe Campaign]** 으로 선택하고 을 클릭합니다 **[!UICONTROL Start workflow]**.

   ![](assets/aem_uc_6.png)

1. 그런 다음 이전 단계로 워크플로우를 **[!UICONTROL Approve for Campaign]** 시작합니다.
1. 고지 사항이 페이지 상단에 표시됩니다. 을 클릭하여 검토 **[!UICONTROL Complete]** 를 확인하고 를 클릭합니다 **[!UICONTROL Ok]**.

   ![](assets/aem_uc_7.png)

1. 다시 **[!UICONTROL Complete]** 클릭하고 **[!UICONTROL Newsletter approval]** **[!UICONTROL Next Step]** 드롭다운에서 선택합니다.

   ![](assets/aem_uc_8.png)

이제 뉴스레터가 Adobe Campaign에서 준비 및 동기화됩니다.

**Adobe Campaign에서:**

1. From the **[!UICONTROL Campaigns]** tab, click **[!UICONTROL Deliveries]** then **[!UICONTROL Create]**.

   ![](assets/aem_uc_9.png)

1. 드롭다운 **[!UICONTROL Delivery template]** 에서 템플릿을 **[!UICONTROL Email delivery with AEM content (mailAEMContent)]** 선택합니다.

   ![](assets/aem_uc_10.png)

1. 게재에 **[!UICONTROL Label]** 를 추가하고 을 클릭합니다 **[!UICONTROL Continue]**.
1. **[!UICONTROL Synchronize]** 버튼을 클릭합니다.

   인터페이스에 이 단추가 표시되지 않으면 단추를 클릭하고 **[!UICONTROL Properties]** **[!UICONTROL Advanced]** 탭을 선택합니다. 필드 **[!UICONTROL Content editing mode]** 는 필드에 AEM 인스턴스 **[!UICONTROL AEM]** 와 함께 설정되어야 **[!UICONTROL AEM account]** 합니다.

   ![](assets/aem_uc_11.png)

1. Adobe Experience Manager에서 이전에 만든 배달을 선택하고 을 클릭합니다 **[!UICONTROL Ok]**.
1. AEM 배달이 변경되면 **[!UICONTROL Refresh content]** 단추를 클릭합니다.

   ![](assets/aem_uc_12.png)

이제 고객에게 이메일을 보낼 준비가 되었습니다.
