---
product: campaign
title: 자산에 대한 액세스 구성
description: 자산에 대한 액세스 구성
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: f3897a40-b080-47e5-9e31-4d861c1bacd5
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 1%

---

# 자산에 대한 액세스 구성{#configuring-access-to-assets}

![](../../assets/common.svg)

이 섹션에서는 Assets 핵심 서비스 또는 Adobe Experience Manager Assets(AEM Assets) 라이브러리와 통합 기능을 사용하기 위해 Adobe Campaign에서 필요한 구성 단계에 대해 자세히 설명합니다.

>[!CAUTION]
>
>이러한 통합은 동시에 수행됩니다. 구성하기 전에 다음 정보를 주의 깊게 읽으십시오.

* 과 통합 **Experience Cloud 에셋**: 이 통합을 사용하면 Adobe Experience Cloud 라이브러리의 이미지를 삽입할 수 있습니다. 이 통합은 다음을 설치하여 설정해야 합니다 **[!UICONTROL Integration with the Adobe Experience Cloud]** Adobe Campaign의 기본 제공 패키지
* 과 통합 **AEM Assets**: 이 통합을 통해 Adobe Experience Manager Assets 라이브러리의 이미지를 삽입할 수 있습니다. 이 통합은 다음을 설치하여 설정해야 합니다 **[!UICONTROL AEM Integration]** Adobe Campaign의 기본 제공 패키지 Adobe Experience Manager 6.4부터는 이 통합을 더 이상 사용할 수 없습니다.

>[!NOTE]
>
>두 패키지(**[!UICONTROL AEM Integration]** 및 **[!UICONTROL Integration with the Adobe Experience Cloud]** )가 설치되어 있으면 Adobe Experience Cloud 라이브러리에서 사용할 수 있는 자산만 사용할 수 있습니다.

## Experience Cloud 에셋과 통합 {#integrating-with-experience-cloud-assets}

Adobe Campaign과 Experience Cloud Assets 간의 통합을 사용하려면 다음 권한이 있어야 합니다.

* Adobe Experience Cloud 조직
* Adobe IMS 인증 모드 활성화됨

Adobe Campaign과 Adobe Experience Cloud 간에 연결을 활성화하려면 IMS(Adobe ID 연결 서비스)를 통해 연결을 구성합니다. 이 구성은 다음에서 자세히 설명합니다. [Adobe ID을 통해 연결](../../integrations/using/about-adobe-id.md) 문서. 여기에는 다음이 포함됩니다.

* 설치 **[!UICONTROL Integration with the Adobe Experience Cloud]** 패키지.
* Adobe Experience Cloud 외부 계정 구성.

>[!NOTE]
>
>이 통합에 연결된 기능은 IMS를 통해 Adobe ID에 연결된 사용자만 사용할 수 있습니다.

## AEM Assets과 통합 {#integrating-with-aem-assets}


>[!CAUTION]
>
>이 기능은 Adobe Experience Manager 6.4부터 사용 중단되었습니다. [자세히 알아보기](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/deprecated-removed-features.html?lang=en#removed-features)

AEM Assets을 Adobe Campaign과 통합하려면 먼저 Adobe Experience Manager과 Adobe Campaign 간의 통합을 구성해야 합니다. 이 구성은 주로 다음을 필요로 합니다.

* 설치 **[!UICONTROL AEM Integration]** 기본 제공 패키지
* Adobe Experience Manager 전용 외부 계정 구성

에서 Adobe Campaign 및 Adobe Experience Manager을 통합하는 방법을 알아봅니다. [자세한 설명서](../../integrations/using/about-adobe-experience-manager.md).

이 통합이 설정되면 Adobe Campaign에서 AEM Assets 라이브러리를 사용하도록 새 게재 템플릿을 구성할 수 있습니다. 이렇게 하려면 아래 단계를 수행합니다:

1. 새 게재 템플릿을 만들거나 기존 템플릿을 복제합니다. 게재 템플릿에 대한 자세한 내용은 다음을 참조하십시오. [이 페이지](../../delivery/using/about-templates.md).
1. 편집 **속성** 이 템플릿의 일부입니다.
1. 다음에서 **[!UICONTROL Advanced]** 탭에서 다음을 설정합니다. **[!UICONTROL Content editing mode]** 끝 **DCE**.
1. 외부 선택 **[!UICONTROL AEM account]** AEM Assets 라이브러리에 액세스하는 데 사용해야 합니다.

   ![](assets/dam_aem_assets1.png)

이 템플릿을 기반으로 게재 콘텐츠에 이미지를 삽입하는 경우 **[!UICONTROL Select a shared asset]** 옵션을 사용하면 AEM Assets 라이브러리에서 이미지를 검색할 수 있습니다. 다음에서 자세히 알아보기 [이 섹션](../../integrations/using/inserting-a-shared-asset.md).

>[!NOTE]
>
>다음과 같은 경우 **[!UICONTROL Integration with the Adobe Experience Cloud]** 패키지가 Adobe Campaign 인스턴스에도 설치되므로 Adobe Experience Cloud 라이브러리에서 사용할 수 있는 에셋만 사용할 수 있습니다. AEM Assets 라이브러리의 에셋에도 액세스하려면 AEM Assets 및 Adobe Experience Cloud을 동기화해야 합니다. 그런 다음 AEM Assets의 에셋을 Adobe Experience Cloud 라이브러리에서도 사용할 수 있습니다. 이 경우 특정 게재 템플릿을 만들 필요가 없습니다.
