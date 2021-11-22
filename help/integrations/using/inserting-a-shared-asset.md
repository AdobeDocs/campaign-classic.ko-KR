---
product: campaign
title: 공유 자산 삽입
description: 공유 자산 삽입
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: 30a94bce-6d96-4a6d-a62f-7451c822f0e3
source-git-commit: d399c4800fe6c5b128a6ccb5fec15262cbef5ee8
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 7%

---

# 공유 자산 삽입{#inserting-a-shared-asset}

Adobe Experience Cloud에서 공유한 자산은 다음과 같이 이메일 및 랜딩 페이지에서 사용할 수 있습니다.

1. 새 이메일 또는 새 랜딩 페이지를 만듭니다.

   Adobe Experience Manager 자산 라이브러리의 자산을 사용하는 경우 [통합 구성](../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets).

   이 특정 템플릿이 없는 경우 게재에서 확인합니다 **속성**, **[!UICONTROL Content editing mode]** (**[!UICONTROL Advanced]** 탭)이 **DCE** AEM Assets 리소스 라이브러리 액세스에 사용할 AEM 외부 계정이 제공되는지 확인합니다.

1. 편집 창에서 옵션을 선택하여 이미지를 추가합니다.

   * 를 사용하는 경우 [표준 편집 모드](../../delivery/using/defining-the-email-content.md#adding-images), 선택 **[!UICONTROL Image]** > **[!UICONTROL Select a shared asset]**.

      ![](assets/dam_insert_image_standard.png)

   * 를 사용하는 경우 [고급 편집 모드](../../web/using/about-campaign-html-editor.md) (DCE)를 선택하고 이미지 블록으로 이동한 다음, 상황별 메뉴를 통해 **[!UICONTROL Select a shared asset]**.

      ![](assets/dam_insert_image_dce.png)

      >[!NOTE]
      >
      >에 Adobe Campaign의 공유 이미지를 삽입할 수 없습니다 [웹 액세스](../../platform/using/adobe-campaign-workspace.md#console-and-web-access) DCE를 사용할 때 사용됩니다.

1. 열리는 선택 창에서 이미지를 선택한 다음 확인합니다.

   사용 가능한 이미지는 Adobe Campaign 인스턴스가 구성되는 방법에 따라 Adobe Experience Cloud 라이브러리 또는 AEM Assets 라이브러리에서 제공됩니다. 자세한 내용은 [자산에 대한 액세스 구성](../../integrations/using/configuring-access-to-assets.md) 섹션을 참조하십시오.

   ![](assets/dam_shared_image_selection.png)

>[!NOTE]
>
>Adobe Target과의 통합을 사용하는 경우 공유 이미지를 기본 이미지로 사용할 수 있습니다. [이 페이지](../../integrations/using/integrating-with-adobe-target.md)를 참조하십시오.
