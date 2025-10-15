---
product: campaign
title: 공유 자산 삽입
description: 공유 자산 삽입
feature: Asset Sharing
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: 30a94bce-6d96-4a6d-a62f-7451c822f0e3
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 1%

---

# 공유 자산 삽입{#inserting-a-shared-asset}

Adobe Experience Cloud에서 공유한 Assets을 이메일 및 랜딩 페이지에서 다음과 같이 사용할 수 있습니다.

1. 새 이메일 또는 새 랜딩 페이지를 만듭니다.

   Adobe Experience Manager 자산 라이브러리의 자산을 사용하는 경우 [통합을 구성](../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets)할 때 만들어진 게재 템플릿을 사용하십시오.

   이 특정 템플릿이 없는 경우 게재 **속성**&#x200B;에서 **[!UICONTROL Content editing mode]**(**[!UICONTROL Advanced]** 탭)이 **DCE**(으)로 설정되어 있고 AEM Assets 리소스 라이브러리에 액세스하는 데 사용할 AEM 외부 계정이 제공되었는지 확인하십시오.

1. 편집 창에서 이미지를 추가할 옵션을 선택합니다.

   * [표준 편집 모드](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-the-email-content.html?lang=ko#adding-images){target="_blank"}를 사용하는 경우 **[!UICONTROL Image]** > **[!UICONTROL Select a shared asset]**&#x200B;을(를) 선택하십시오.

     ![](assets/dam_insert_image_standard.png)

   * [고급 편집 모드](../../web/using/about-campaign-html-editor.md)(DCE)를 사용하는 경우 이미지 블록으로 이동한 다음 상황별 메뉴를 통해 **[!UICONTROL Select a shared asset]**&#x200B;을(를) 선택합니다.

     ![](assets/dam_insert_image_dce.png)

     >[!NOTE]
     >
     >DCE를 사용할 때는 [웹 액세스](../../platform/using/adobe-campaign-workspace.md#console-and-web-access)에서 Adobe Campaign의 공유 이미지를 삽입할 수 없습니다.

1. 선택 창이 열리면 이미지를 선택한 다음 확인합니다.

   Adobe Campaign 인스턴스가 구성되는 방식에 따라 사용 가능한 이미지는 Adobe Experience Cloud 라이브러리 또는 AEM Assets 라이브러리에서 제공됩니다. [Assets에 대한 액세스 구성](../../integrations/using/configuring-access-to-assets.md) 섹션을 참조하십시오.

   ![](assets/dam_shared_image_selection.png)

>[!NOTE]
>
>Adobe Target과의 통합을 사용하는 경우 공유 이미지를 기본 이미지로 사용할 수 있습니다. [이 페이지](../../integrations/using/integrating-with-adobe-target.md)를 참조하십시오.
