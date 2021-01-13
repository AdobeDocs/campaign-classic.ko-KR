---
solution: Campaign Classic
product: campaign
title: 자산에 대한 액세스 구성
description: 자산에 대한 액세스 구성
audience: integrations
content-type: reference
topic-tags: asset-sharing
translation-type: tm+mt
source-git-commit: 5d5d4b87bae44ce0a93458f79179434a5bf315c3
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 1%

---


# 자산{#configuring-access-to-assets}에 대한 액세스 구성

이 섹션에서는 Assets 핵심 서비스 또는 Adobe Experience Manager 자산 라이브러리와 통합 기능을 사용하기 위해 Adobe Campaign에서 필요한 구성 단계에 대해 자세히 설명합니다.

>[!CAUTION]
>
>이러한 통합은 동시에 이루어집니다. 구성을 수행하기 전에 다음 정보를 자세히 읽으십시오.

* **Experience Cloud 자산**&#x200B;과의 통합:이 통합을 통해 Adobe Experience Cloud 라이브러리의 이미지를 삽입할 수 있습니다. 구성 및 라이선스 모델에 따라 이 라이브러리는 Assets 핵심 서비스 또는 Assets on Demand일 수 있습니다. 이 통합은 Adobe Campaign에 **[!UICONTROL Integration with the Adobe Experience Cloud]** 내장 패키지를 설치하여 설정해야 합니다.
* **AEM Assets**&#x200B;과의 통합:이 통합을 통해 Adobe Experience Manager 에셋 라이브러리의 이미지를 삽입할 수 있습니다. 이 통합은 Adobe Campaign에 **[!UICONTROL AEM Integration]** 내장 패키지를 설치하여 설정해야 합니다.

>[!NOTE]
>
>두 패키지(**[!UICONTROL AEM Integration]** 및 **[!UICONTROL Integration with the Adobe Experience Cloud]** )가 설치된 경우 Adobe Experience Cloud 라이브러리에서 사용할 수 있는 자산만 사용할 수 있습니다. AEM Assets 라이브러리의 에셋도 액세스하려면 AEM Assets과 Adobe Experience Cloud을 동기화해야 합니다. 그러면 AEM Assets의 에셋을 Adobe Experience Cloud 라이브러리에서도 사용할 수 있습니다. AEM Assets 및 Adobe Experience Cloud 동기화에 대한 자세한 내용은 [자세한 설명서](https://docs.adobe.com/docs/en/aod/overview/collaborating/aem-assets-aod-sync.html)를 참조하십시오.

## Experience Cloud 자산 {#integrating-with-experience-cloud-assets}과 통합

Adobe Campaign과 Experience Cloud 자산 간의 통합을 사용하려면 다음이 있어야 합니다.

* Adobe Experience Cloud 조직
* Adobe IMS 인증 모드를 활성화했습니다.

Adobe Campaign과 Adobe Experience Cloud 간의 연결을 활성화하려면 IMS(Adobe ID 연결 서비스)를 통해 연결을 구성합니다. 이 구성은 [Adobe ID](../../integrations/using/about-adobe-id.md) 문서를 통해 연결에 설명되어 있습니다. 여기에는 다음이 포함됩니다.

* **[!UICONTROL Integration with the Adobe Experience Cloud]** 패키지를 설치하는 중입니다.
* Adobe Experience Cloud 외부 계정 구성

>[!NOTE]
>
>이 통합에 연결된 기능은 IMS를 통해 Adobe ID과 연결된 사용자만 사용할 수 있습니다.

## AEM Assets {#integrating-with-aem-assets}과 통합

AEM Assets을 Adobe Campaign과 통합하려면 먼저 Adobe Experience Manager과 Adobe Campaign 간의 통합을 구성해야 합니다. 이 구성에는 다음이 주로 필요합니다.

* **[!UICONTROL AEM Integration]** 내장 패키지 설치
* Adobe Experience Manager 전용 외부 계정 구성

[자세한 설명서](../../integrations/using/about-adobe-experience-manager.md)에서 Adobe Campaign 및 Adobe Experience Manager을 통합하는 방법을 알아봅니다.

이 통합이 설정되면 AEM Assets 라이브러리를 사용하도록 Adobe Campaign에서 새 배달 템플릿을 구성할 수 있습니다. 이렇게 하려면 아래 단계를 수행합니다:

1. 새 배달 템플릿을 만들거나 기존 배달 템플릿을 복제합니다. 배달 템플릿에 대한 자세한 내용은 [이 페이지](../../delivery/using/about-templates.md)를 참조하십시오.
1. 이 템플릿의 **속성**&#x200B;을 편집합니다.
1. **[!UICONTROL Advanced]** 탭에서 **[!UICONTROL Content editing mode]**&#x200B;을 **DCE**&#x200B;로 설정합니다.
1. AEM Assets 라이브러리에 액세스하는 데 사용할 외부 **[!UICONTROL AEM account]**&#x200B;을 선택합니다.

   ![](assets/dam_aem_assets1.png)

이 템플릿을 기반으로 한 전달의 컨텐츠에 이미지를 삽입하면 AEM Assets 라이브러리에서 이미지를 검색할 수 있게 됩니다. **[!UICONTROL Select a shared asset]** [이 섹션](../../integrations/using/inserting-a-shared-asset.md)에서 자세히 알아보십시오.

>[!NOTE]
>
>Adobe Campaign 인스턴스에도 **[!UICONTROL Integration with the Adobe Experience Cloud]** 패키지가 설치되어 있는 경우 Adobe Experience Cloud 라이브러리에서 사용 가능한 에셋만 사용할 수 있습니다. AEM Assets 라이브러리의 에셋도 액세스하려면 AEM Assets과 Adobe Experience Cloud을 동기화해야 합니다. 그러면 AEM Assets의 에셋을 Adobe Experience Cloud 라이브러리에서도 사용할 수 있습니다. 이 경우 특정 배달 템플릿을 만들 필요가 없습니다. AEM Assets과 Adobe Experience Cloud 간의 동기화에 대한 자세한 내용은 [자세한 설명서](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/configure-assets-cc-integration.html#integration)를 참조하십시오.


