---
product: campaign
title: Assets에 대한 액세스 구성
description: Assets에 대한 액세스 구성
feature: Asset Sharing
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: f3897a40-b080-47e5-9e31-4d861c1bacd5
source-git-commit: b11185da8236d6100d98eabcc9dc1cf2cffa70af
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# Assets에 대한 액세스 구성 {#configuring-access-to-assets}

이 섹션에서는 Assets 또는 Adobe Experience Manager Assets(AEM Assets) 라이브러리와 통합 기능을 사용하기 위해 Adobe Campaign에서 필요한 구성 단계에 대해 자세히 설명합니다.

>[!CAUTION]
>
>이러한 통합은 동시에 수행됩니다. 구성하기 전에 다음 정보를 주의 깊게 읽으십시오.

* **Experience Cloud Assets**&#x200B;와 통합: 이 통합을 통해 Adobe Experience Cloud 라이브러리의 이미지를 삽입할 수 있습니다. Adobe Campaign에 **[!UICONTROL Integration with the Adobe Experience Cloud]** 기본 제공 패키지를 설치하여 이 통합을 설정해야 합니다.
* **AEM Assets**&#x200B;와 통합: 이 통합을 통해 Adobe Experience Manager Assets 라이브러리의 이미지를 삽입할 수 있습니다. Adobe Campaign에 **[!UICONTROL AEM Integration]** 기본 제공 패키지를 설치하여 이 통합을 설정해야 합니다. Adobe Experience Manager 6.4부터는 이 통합을 더 이상 사용할 수 없습니다.

>[!NOTE]
>
>두 패키지(**[!UICONTROL AEM Integration]** 및 **[!UICONTROL Integration with the Adobe Experience Cloud]**)가 설치된 경우 Adobe Experience Cloud 라이브러리에서 사용할 수 있는 자산만 사용할 수 있습니다.

## Experience Cloud Assets과 통합 {#integrating-with-experience-cloud-assets}

Adobe Campaign과 Experience Cloud Assets 간의 통합을 사용하려면 다음 사항이 있어야 합니다.

* Adobe Experience Cloud 조직
* Adobe IMS 인증 모드 활성화됨

Adobe Campaign과 Adobe Experience Cloud 간에 연결을 활성화하려면 IMS(Adobe ID 연결 서비스)를 통해 연결을 구성합니다. 이 구성은 [Adobe ID을 통해 연결](../../integrations/using/about-adobe-id.md) 문서에 자세히 설명되어 있습니다. 여기에는 다음이 포함됩니다.

* **[!UICONTROL Integration with the Adobe Experience Cloud]** 패키지를 설치하는 중입니다.
* Adobe Experience Cloud 외부 계정 구성.

>[!NOTE]
>
>이 통합에 연결된 기능은 IMS를 통해 Adobe ID에 연결된 사용자만 사용할 수 있습니다.

## AEM Assets과 통합 {#integrating-with-aem-assets}


>[!CAUTION]
>
>이 기능은 Adobe Experience Manager 6.4부터 사용 중단되었습니다. [자세히 알아보기](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/deprecated-removed-features.html#removed-features)

AEM Assets을 Adobe Campaign과 통합하려면 먼저 Adobe Experience Manager과 Adobe Campaign 간의 통합을 구성해야 합니다. 이 구성은 주로 다음을 필요로 합니다.

* **[!UICONTROL AEM Integration]** 기본 제공 패키지 설치 중
* Adobe Experience Manager 전용 외부 계정 구성

[자세한 설명서](../../integrations/using/about-adobe-experience-manager.md)에서 Adobe Campaign과 Adobe Experience Manager을 통합하는 방법을 알아보세요.

이 통합이 설정되면 Adobe Campaign에서 AEM Assets 라이브러리를 사용하도록 새 게재 템플릿을 구성할 수 있습니다. 이렇게 하려면 아래 단계를 수행합니다.

1. 새 게재 템플릿을 만들거나 기존 템플릿을 복제합니다. 게재 템플릿에 대한 자세한 정보는 [이 페이지](../../delivery/using/about-templates.md)를 참조하세요.
1. 이 템플릿의 **속성**&#x200B;을(를) 편집합니다.
1. **[!UICONTROL Advanced]** 탭에서 **[!UICONTROL Content editing mode]**&#x200B;을(를) **DCE**(으)로 설정합니다.
1. AEM Assets 라이브러리에 액세스하는 데 사용해야 하는 외부 **[!UICONTROL AEM account]**&#x200B;을(를) 선택하십시오.

   ![](assets/dam_aem_assets1.png)

이 템플릿을 기반으로 하여 게재 콘텐츠에 이미지를 삽입하면 **[!UICONTROL Select a shared asset]** 옵션을 사용하여 AEM Assets 라이브러리에서 이미지를 검색할 수 있습니다. [이 섹션](../../integrations/using/inserting-a-shared-asset.md)에서 자세히 알아보십시오.

>[!NOTE]
>
>**[!UICONTROL Integration with the Adobe Experience Cloud]** 패키지가 Adobe Campaign 인스턴스에도 설치된 경우 Adobe Experience Cloud 라이브러리에서 사용할 수 있는 자산만 사용할 수 있습니다. AEM Assets 라이브러리의 에셋에도 액세스하려면 AEM Assets 및 Adobe Experience Cloud을 동기화해야 합니다. 그런 다음 AEM Assets의 에셋을 Adobe Experience Cloud 라이브러리에서도 사용할 수 있습니다. 이 경우 특정 게재 템플릿을 만들 필요가 없습니다.
