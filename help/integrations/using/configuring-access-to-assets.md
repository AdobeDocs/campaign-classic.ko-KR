---
title: 자산에 대한 액세스 구성
seo-title: 자산에 대한 액세스 구성
description: 자산에 대한 액세스 구성
seo-description: null
page-status-flag: never-activated
uuid: dc8c0016-92c8-41ab-98c6-d0fe0bfd6c41
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: asset-sharing
discoiquuid: df1b6ead-3471-404a-b43f-a68fb86cb14c
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 1%

---


# Configuring access to Assets{#configuring-access-to-assets}

이 섹션에서는 Assets 핵심 서비스 또는 Adobe Experience Manager 자산 라이브러리와 통합 기능을 사용하기 위해 Adobe Campaign에서 필요한 구성 단계에 대해 자세히 설명합니다.

>[!CAUTION]
>
>이러한 통합이 동시에 이루어집니다. 구성을 수행하기 전에 다음 정보를 자세히 읽어 보십시오.

* Experience Cloud **자산과 통합**:이 통합을 통해 Adobe Experience Cloud 라이브러리의 이미지를 삽입할 수 있습니다. 구성 및 라이선스 모델에 따라 이 라이브러리는 Assets 핵심 서비스 또는 Assets on Demand일 수 있습니다. 이 통합은 Adobe Campaign에 **[!UICONTROL Integration with the Adobe Experience Cloud]** 내장된 패키지를 설치하여 설정해야 합니다.
* **AEM Assets과 통합**:이 통합을 통해 Adobe Experience Manager 에셋 라이브러리의 이미지를 삽입할 수 있습니다. 이 통합은 Adobe Campaign에 **[!UICONTROL AEM Integration]** 내장된 패키지를 설치하여 설정해야 합니다.

>[!NOTE]
>
>두 패키지(**[!UICONTROL AEM Integration]** 및 **[!UICONTROL Integration with the Adobe Experience Cloud]** )가 설치되어 있는 경우 Adobe Experience Cloud 라이브러리에서 사용 가능한 자산만 사용할 수 있습니다. AEM Assets 라이브러리의 에셋에도 액세스하려면 AEM Assets과 Adobe Experience Cloud을 동기화해야 합니다. AEM Assets의 에셋은 Adobe Experience Cloud 도서관에서도 이용할 수 있습니다. AEM Assets 및 Adobe Experience Cloud 동기화에 대한 자세한 내용은 [자세한 설명서를 참조하십시오](https://docs.adobe.com/docs/en/aod/overview/collaborating/aem-assets-aod-sync.html).

## Experience Cloud 자산과 통합 {#integrating-with-experience-cloud-assets}

Adobe Campaign 자산과 Experience Cloud 자산 간의 통합을 사용하려면 다음을 수행해야 합니다.

* Adobe Experience Cloud 조직
* Adobe IMS 인증 모드를 활성화했습니다.

Adobe Campaign과 Adobe Experience Cloud 간의 연결을 활성화하려면 IMS(Adobe ID 연결 서비스)를 통해 연결을 구성합니다. 이 구성은 Adobe ID [를 통해 연결 문서에 자세히 설명되어](../../integrations/using/about-adobe-id.md) 있습니다. 여기에는 다음이 포함됩니다.

* 패키지를 **[!UICONTROL Integration with the Adobe Experience Cloud]** 설치하는 중입니다.
* Adobe Experience Cloud 외부 계정 구성

>[!NOTE]
>
>이 통합에 연결된 기능은 IMS를 통해 Adobe ID과 연결된 사용자만 사용할 수 있습니다.

## AEM Assets과 통합 {#integrating-with-aem-assets}

AEM Assets을 Adobe Campaign과 통합하려면 먼저 Adobe Experience Manager과 Adobe Campaign 간의 통합을 구성해야 합니다. 이 구성에는 다음이 주로 필요합니다.

* 기본 **[!UICONTROL AEM Integration]** 제공 패키지 설치
* Adobe Experience Manager 전용 외부 계정 구성

Adobe Campaign과 Adobe Experience Manager을 [자세한 문서에 통합하는 방법을 살펴보십시오](../../integrations/using/about-adobe-experience-manager.md).

이 통합이 설정되면 AEM Assets 라이브러리를 사용하도록 Adobe Campaign에서 새 배달 템플릿을 구성할 수 있습니다. 이렇게 하려면 아래 단계를 수행합니다:

1. 새 배달 템플릿을 만들거나 기존 템플릿을 복제합니다. For more on Delivery templates, refer to [this page](../../delivery/using/about-templates.md).
1. 이 템플릿 **의** 속성을 편집합니다.
1. 탭에서 을 DCE **[!UICONTROL Advanced]** 로 **[!UICONTROL Content editing mode]** 설정합니다 ****.
1. AEM Assets 라이브러리에 액세스하기 위해 사용해야 **[!UICONTROL AEM account]** 하는 외부 파일을 선택합니다.

   ![](assets/dam_aem_assets1.png)

이 템플릿을 기반으로 한 전달의 컨텐츠에 이미지를 삽입하면 이 **[!UICONTROL Select a shared asset]** 옵션을 통해 AEM Assets 라이브러리에서 이미지를 검색할 수 있습니다. 자세한 내용은 [이 섹션을 참조하십시오](../../integrations/using/inserting-a-shared-asset.md).

>[!NOTE]
>
>Adobe Campaign 인스턴스에도 **[!UICONTROL Integration with the Adobe Experience Cloud]** 패키지가 설치되어 있는 경우 Adobe Experience Cloud 라이브러리에서 사용 가능한 에셋만 사용할 수 있습니다. AEM Assets 라이브러리의 에셋에도 액세스하려면 AEM Assets과 Adobe Experience Cloud을 동기화해야 합니다. AEM Assets의 에셋은 Adobe Experience Cloud 도서관에서도 이용할 수 있습니다. 이 경우 특정 배달 템플릿을 만들 필요가 없습니다. AEM Assets과 Adobe Experience Cloud 간의 동기화에 대한 자세한 내용은 [자세한 설명서를 참조하십시오](https://docs.adobe.com/docs/en/aod/overview/collaborating/aem-assets-aod-sync.html).

