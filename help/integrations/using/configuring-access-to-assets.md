---
product: campaign
title: 자산에 대한 액세스 구성
description: 자산에 대한 액세스 구성
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: f3897a40-b080-47e5-9e31-4d861c1bacd5
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 2%

---

# 자산에 대한 액세스 구성{#configuring-access-to-assets}



이 섹션에서는 Assets 핵심 서비스 또는 Adobe Experience Manager 자산(AEM Assets) 라이브러리와 통합 기능을 사용하기 위해 Adobe Campaign에서 필요한 구성 단계에 대해 자세히 설명합니다.

>[!CAUTION]
>
>이러한 통합은 동시에 수행됩니다. 구성을 수행하기 전에 다음 정보를 자세히 읽어보십시오.

* 통합 **자산 Experience Cloud**: 이 통합을 통해 Adobe Experience Cloud 라이브러리의 이미지를 삽입할 수 있습니다. 이 통합은 **[!UICONTROL Integration with the Adobe Experience Cloud]** Adobe Campaign에 내장된 패키지
* 통합 **AEM Assets**: 이 통합을 통해 Adobe Experience Manager Assets 라이브러리의 이미지를 삽입할 수 있습니다. 이 통합은 **[!UICONTROL AEM Integration]** Adobe Campaign에 내장된 패키지 이 통합은 Adobe Experience Manager 6.4부터 더 이상 사용할 수 없습니다.

>[!NOTE]
>
>두 패키지(**[!UICONTROL AEM Integration]** 및 **[!UICONTROL Integration with the Adobe Experience Cloud]** )가 설치되면 Adobe Experience Cloud 라이브러리에서 사용할 수 있는 자산만 사용할 수 있습니다.

## Experience Cloud 자산과 통합 {#integrating-with-experience-cloud-assets}

Adobe Campaign과 Experience Cloud 자산 간의 통합을 사용하려면 다음이 있어야 합니다.

* Adobe Experience Cloud 조직
* Adobe IMS 인증 모드 활성화

Adobe Campaign과 Adobe Experience Cloud 간에 연결을 활성화하려면 IMS(Adobe ID 연결 서비스)를 통해 연결을 구성합니다. 이 구성은 [Adobe ID을 통해 연결](../../integrations/using/about-adobe-id.md) 문서. 여기에는 다음이 포함됩니다.

* 설치 **[!UICONTROL Integration with the Adobe Experience Cloud]** 패키지.
* Adobe Experience Cloud 외부 계정 구성

>[!NOTE]
>
>이 통합에 연결된 기능은 IMS를 통해 Adobe ID에 연결된 사용자만 사용할 수 있습니다.

## AEM Assets과 통합 {#integrating-with-aem-assets}


>[!CAUTION]
>
>이 기능은 Adobe Experience Manager 6.4부터 사용 중단되었습니다. [추가 정보](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/deprecated-removed-features.html?lang=en#removed-features)

AEM Assets을 Adobe Campaign과 통합하려면 먼저 Adobe Experience Manager과 Adobe Campaign 간의 통합을 구성해야 합니다. 이 구성에는 주로 다음이 필요합니다.

* 설치 **[!UICONTROL AEM Integration]** 기본 제공 패키지
* Adobe Experience Manager에만 해당하는 외부 계정 구성

에서 Adobe Campaign과 Adobe Experience Manager을 통합하는 방법을 알아봅니다. [세부 설명서](../../integrations/using/about-adobe-experience-manager.md).

이 통합이 설정되면 AEM Assets 라이브러리를 사용하도록 Adobe Campaign에서 새 게재 템플릿을 구성할 수 있습니다. 이렇게 하려면 아래 단계를 수행합니다:

1. 새 게재 템플릿을 만들거나 기존 게재 템플릿을 복제합니다. 게재 템플릿에 대한 자세한 내용은 [이 페이지](../../delivery/using/about-templates.md).
1. 편집 **속성** Analytics JavaScript에서 지원됩니다.
1. 에서 **[!UICONTROL Advanced]** 탭에서 설정합니다. **[!UICONTROL Content editing mode]** to **DCE**.
1. 외부 선택 **[!UICONTROL AEM account]** 타사 시스템(AEM Assets 라이브러리에 액세스하는 데 사용)을

   ![](assets/dam_aem_assets1.png)

이 템플릿을 기반으로 게재 콘텐츠에 이미지를 삽입하면 **[!UICONTROL Select a shared asset]** 옵션을 사용하면 AEM Assets 라이브러리에서 이미지를 검색할 수 있습니다. [이 섹션](../../integrations/using/inserting-a-shared-asset.md)에서 자세히 알아보십시오.

>[!NOTE]
>
>만약 **[!UICONTROL Integration with the Adobe Experience Cloud]** 패키지는 Adobe Campaign 인스턴스에도 설치되므로 Adobe Experience Cloud 라이브러리에서 사용할 수 있는 자산만 사용할 수 있습니다. AEM Assets 라이브러리의 자산에도 액세스하려면 AEM Assets과 Adobe Experience Cloud을 동기화해야 합니다. 그러면 AEM Assets의 자산을 Adobe Experience Cloud 라이브러리에서도 사용할 수 있습니다. 이 경우 특정 게재 템플릿을 만들 필요가 없습니다.
