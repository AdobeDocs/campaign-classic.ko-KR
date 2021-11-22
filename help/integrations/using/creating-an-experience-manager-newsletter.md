---
product: campaign
title: Experience Manager 뉴스레터 만들기
description: Experience Manager 뉴스레터 만들기
audience: integrations
content-type: reference
exl-id: 9fa3ce08-3007-4c65-9841-bad339428b7c
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 1%

---

# Experience Manager 뉴스레터 만들기{#creating-an-experience-manager-newsletter}

![](../../assets/common.svg)

이 통합은 예를 들어 Adobe Experience Manager에서 뉴스레터를 만든 후 이메일 캠페인의 일부로 Adobe Campaign에서 사용할 수 있습니다.

이 통합 사용 방법에 대한 자세한 예는 이 통합을 참조하십시오 [단계별 안내서](https://helpx.adobe.com/campaign/kb/acc-aem.html).

**Adobe Experience Manager에서:**

1. AEM 작성자 인스턴스에서 **Adobe Experience** 페이지의 왼쪽 상단에 있는 로고를 선택하고 **[!UICONTROL Sites]**.

   ![](assets/aem_uc_1.png)

1. **[!UICONTROL Campaigns > Name of your brand (here We.Retail) > Main Area > Email campaigns]**&#x200B;을(를) 선택합니다.
1. 을(를) 클릭합니다. **[!UICONTROL Create]** 페이지의 오른쪽 위에 있는 버튼을 선택한 다음 **[!UICONTROL Page]**.

   ![](assets/aem_uc_2.png)

1. 을(를) 선택합니다 **[!UICONTROL Adobe Campaign Email (AC 6.1)]** 템플릿을 사용하여 뉴스레터에 이름을 지정합니다.
1. 페이지가 만들어지면 **[!UICONTROL Page information]** 메뉴를 클릭하고 **[!UICONTROL Open Properties]**.

   ![](assets/aem_uc_3.png)

1. 에서 **[!UICONTROL Cloud Services]** 탭, 선택 **[!UICONTROL Adobe Campaign]** 로서의 **[!UICONTROL Cloud service configuration]** 및 두 번째 드롭다운에서 Adobe Campaign 인스턴스를 사용할 수 있습니다.

   ![](assets/aem_uc_4.png)

1. 구성 요소를 추가하여 이메일 콘텐츠를 편집합니다(예: Adobe Campaign의 개인화 필드).
1. 전자 메일이 준비되면 **[!UICONTROL Page information]** 메뉴를 클릭하고 **[!UICONTROL Start workflow]**.

   ![](assets/aem_uc_5.png)

1. 첫 번째 드롭다운에서 을 선택합니다. **[!UICONTROL Publish to Adobe Campaign]** 워크플로우 모델 을 클릭하고 **[!UICONTROL Start workflow]**.

   ![](assets/aem_uc_6.png)

1. 그런 다음 이전 단계로 를 실행합니다 **[!UICONTROL Approve for Campaign]** 워크플로우.
1. 면책조항이 페이지 맨 위에 나타납니다. 클릭 **[!UICONTROL Complete]** 검토를 확인하려면 **[!UICONTROL Ok]**.

   ![](assets/aem_uc_7.png)

1. 다시 클릭 **[!UICONTROL Complete]** 을(를) 선택합니다. **[!UICONTROL Newsletter approval]** 에서 **[!UICONTROL Next Step]** 드롭다운.

   ![](assets/aem_uc_8.png)

이제 뉴스레터가 Adobe Campaign에서 준비 및 동기화됩니다.

**Adobe Campaign에서:**

1. 에서 **[!UICONTROL Campaigns]** 탭, **[!UICONTROL Deliveries]** 그런 다음 **[!UICONTROL Create]**.

   ![](assets/aem_uc_9.png)

1. 에서 **[!UICONTROL Delivery template]** 드롭다운에서 **[!UICONTROL Email delivery with AEM content (mailAEMContent)]** 템플릿.

   ![](assets/aem_uc_10.png)

1. 추가 **[!UICONTROL Label]** 게재하기 위해 을(를) 클릭하고 **[!UICONTROL Continue]**.
1. **[!UICONTROL Synchronize]** 버튼을 클릭합니다.

   인터페이스에 이 단추가 표시되지 않으면 **[!UICONTROL Properties]** 버튼을 클릭하고 **[!UICONTROL Advanced]** 탭. 다음 **[!UICONTROL Content editing mode]** 필드를 (으)로 설정해야 합니다. **[!UICONTROL AEM]** 에서 AEM 인스턴스 사용 **[!UICONTROL AEM account]** 필드.

   ![](assets/aem_uc_11.png)

1. Adobe Experience Manager에서 이전에 만든 게재를 선택하고 을(를) 클릭합니다 **[!UICONTROL Ok]**.
1. 을(를) 클릭합니다. **[!UICONTROL Refresh content]** AEM 게재를 변경하는 즉시 버튼을 클릭합니다.

   ![](assets/aem_uc_12.png)

이제 이메일을 대상자에게 보낼 준비가 되었습니다.
