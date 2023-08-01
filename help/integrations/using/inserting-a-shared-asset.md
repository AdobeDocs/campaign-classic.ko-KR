---
product: campaign
title: 공유 자산 삽입
description: 공유 자산 삽입
feature: Asset Sharing
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: 30a94bce-6d96-4a6d-a62f-7451c822f0e3
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 7%

---

# 공유 자산 삽입{#inserting-a-shared-asset}

Adobe Experience Cloud에서 공유한 에셋은 다음과 같이 이메일 및 랜딩 페이지에서 사용할 수 있습니다.

1. 새 이메일 또는 새 랜딩 페이지를 만듭니다.

   Adobe Experience Manager 에셋 라이브러리의 에셋을 사용하는 경우 다음과 같은 경우에 생성된 게재 템플릿을 사용하십시오. [통합 구성](../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets).

   이 특정 템플릿이 없는 경우 게재에서 다음을 확인하십시오 **속성**, **[!UICONTROL Content editing mode]** (**[!UICONTROL Advanced]** tab)을 (으)로 설정 **DCE** 또한 AEM Assets 리소스 라이브러리에 액세스하는 데 사용할 AEM 외부 계정이 제공됩니다.

1. 편집 창에서 이미지를 추가할 옵션을 선택합니다.

   * 를 사용하는 경우 [표준 편집 모드](../../delivery/using/defining-the-email-content.md#adding-images), 선택 **[!UICONTROL Image]** > **[!UICONTROL Select a shared asset]**.

     ![](assets/dam_insert_image_standard.png)

   * 를 사용하는 경우 [고급 편집 모드](../../web/using/about-campaign-html-editor.md) (DCE), 이미지 블록으로 이동한 다음 상황별 메뉴를 통해 을 선택합니다. **[!UICONTROL Select a shared asset]**.

     ![](assets/dam_insert_image_dce.png)

     >[!NOTE]
     >
     >Adobe Campaign의 공유 이미지를 삽입할 수 없습니다. [웹 액세스](../../platform/using/adobe-campaign-workspace.md#console-and-web-access) dce를 사용하는 경우.

1. 선택 창이 열리면 이미지를 선택한 다음 확인합니다.

   Adobe Campaign 인스턴스가 구성되는 방식에 따라 사용 가능한 이미지는 Adobe Experience Cloud 라이브러리 또는 AEM Assets 라이브러리에서 제공됩니다. 다음을 참조하십시오. [자산에 대한 액세스 구성](../../integrations/using/configuring-access-to-assets.md) 섹션.

   ![](assets/dam_shared_image_selection.png)

>[!NOTE]
>
>Adobe Target과의 통합을 사용하는 경우 공유 이미지를 기본 이미지로 사용할 수 있습니다. [이 페이지](../../integrations/using/integrating-with-adobe-target.md)를 참조하십시오.
