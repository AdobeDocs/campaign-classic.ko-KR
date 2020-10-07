---
title: Adobe Campaign에서 공유 대상 통합 구성
seo-title: Adobe Campaign에서 공유 대상 통합 구성
description: Adobe Campaign에서 공유 대상 통합 구성
seo-description: null
page-status-flag: never-activated
uuid: 6ed137e4-027f-4eb0-a0b5-4beb7deef51f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: 4443b0ca-80c6-467d-a4df-50864aae8496
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 2%

---


# Configuring shared audiences integration in Adobe Campaign{#configuring-shared-audiences-integration-in-adobe-campaign}

이 요청을 제출하면 Adobe은 사용자를 위해 통합의 프로비저닝을 계속 진행하며 구성을 마무리하는 데 필요한 세부 정보와 정보를 제공합니다.

1. [1단계:Adobe Campaign에서 외부 계정 구성 또는 확인](#step-1--configure-or-check-the-external-accounts-in-adobe-campaign)
1. [2단계:데이터 소스 구성](#step-2--configure-the-data-source)
1. [3단계:캠페인 추적 서버 구성](#step-3--configure-campaign-tracking-server)
1. [4단계:방문자 ID 서비스 구성](#step-4--configure-the-visitor-id-service)

## 1단계:Adobe Campaign에서 외부 계정 구성 또는 확인 {#step-1--configure-or-check-the-external-accounts-in-adobe-campaign}

먼저 Adobe Campaign의 외부 계정을 다음과 같이 구성하거나 확인해야 합니다.

1. 아이콘을 **[!UICONTROL Explorer]** 클릭합니다.
1. 로 **[!UICONTROL Administration > Platform > External accounts]**&#x200B;이동합니다. 언급된 SFTP 계정은 Adobe에 의해 구성되어야 하며 필요한 정보는 사용자에게 전달되어야 합니다.

   * **[!UICONTROL importSharedAudience]** :대상 가져오기를 위한 SFTP 계정
   * **[!UICONTROL exportSharedAudience]** :대상 내보내기를 위한 SFTP 계정

   ![](assets/aam_config_1.png)

1. 필드를 **[!UICONTROL Server]** 채웁니다. **외부 계정 가져오기 및 외부 계정 내보내기의** ftp-in.demdex.com **도메인에 대한 ftp-out.demdex.com** 도메인

   Campaign에서 내보내기는 Audience Manager 또는 사용자 핵심 서비스에 대한 가져오기임을 기억하십시오.

   >[!NOTE]
   >
   >S3을 사용하는 경우 다음 구문을 **[!UICONTROL AWS S3 Account Server]** 입력합니다.
   >
   >`<S3bucket name>.s3.amazonaws.com/<s3object path>`
   >
   >S3 계정을 구성하는 방법에 대한 자세한 내용은 이 [페이지를 참조하십시오](../../platform/using/external-accounts.md#amazon-simple-storage-service--s3--external-account).

   ![](assets/aam_config_2.png)

1. Adobe에서 **[!UICONTROL Account]** 제공하는 및 **[!UICONTROL Password]** 를 추가합니다.

이제 외부 계정이 구성됩니다.

## Step 2: Configure the Data Source {#step-2--configure-the-data-source}

수신자 **- 방문자 ID가** Audience Manager 내에 만들어집니다. 방문자 ID에 대해 기본적으로 구성된 기본 데이터 소스입니다. 캠페인에서 만든 세그먼트는 이 데이터 소스의 일부가 됩니다.

데이터 소스를 **[!UICONTROL Recipient - Visitor ID]** 구성하려면:

1. From the **[!UICONTROL Explorer]** node, select **[!UICONTROL Administration > Platform > AMC Data sources]**.
1. **[!UICONTROL Recipient - Visitor ID]**&#x200B;을(를) 선택합니다.
1. Adobe에서 **[!UICONTROL Data Source ID]** 제공하는 및 **[!UICONTROL AAM Destination ID]** 를 입력합니다.

   ![](assets/aam_config_3.png)

## 3단계:캠페인 추적 서버 구성 {#step-3--configure-campaign-tracking-server}

People 코어 서비스 또는 Audience Manager와의 통합을 구성하려면 캠페인 추적 서버를 구성해야 합니다.

캠페인 추적 서버가 도메인(CNAME)에 등록되어 있는지 확인해야 합니다. 도메인 이름 위임에 대한 자세한 내용은 [이 문서에서 확인할 수 있습니다](https://helpx.adobe.com/kr/campaign/kb/domain-name-delegation.html).

## 4단계:방문자 ID 서비스 구성 {#step-4--configure-the-visitor-id-service}

방문자 ID 서비스가 웹 속성이나 웹 사이트에 구성되지 않은 경우 다음 [문서를](https://docs.adobe.com/content/help/en/id-service/using/implementation/setup-aam-analytics.html) 참조하여 서비스 또는 다음 [비디오를 구성하는 방법을 알아보십시오](https://helpx.adobe.com/marketing-cloud/how-to/email-marketing.html#step-two) .

구성 및 프로비저닝을 완료하면 통합으로 대상 또는 세그먼트를 가져오고 내보낼 수 있습니다.
