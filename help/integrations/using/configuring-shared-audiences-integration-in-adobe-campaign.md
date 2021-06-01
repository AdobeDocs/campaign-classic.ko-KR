---
product: campaign
title: Adobe Campaign에서 공유 대상 통합 구성
description: 공유 대상 통합을 구성하는 방법 알아보기
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: a3e26cff-9609-4d91-8976-9213a30c3fd2
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 2%

---

# Adobe Campaign{#configuring-shared-audiences-integration-in-adobe-campaign}에서 공유 대상 통합 구성

이 요청을 제출하면 Adobe이 사용자를 위한 통합 프로비저닝을 계속 진행하고 구성을 완료해야 하는 세부 정보와 정보를 제공하도록 사용자에게 문의하십시오.

1. [1단계:Adobe Campaign에서 외부 계정 구성 또는 확인](#step-1--configure-or-check-the-external-accounts-in-adobe-campaign)
1. [2단계:데이터 소스 구성](#step-2--configure-the-data-source)
1. [3단계:Campaign 추적 서버 구성](#step-3--configure-campaign-tracking-server)
1. [4단계:방문자 ID 서비스 구성](#step-4--configure-the-visitor-id-service)

>[!IMPORTANT]
>
>demdex 도메인을 사용하고 가져오기 외부 계정에 대해 **ftp-out.demdex.com** 구문을 따르고, 외부 계정 내보내기에 대해 **ftp-in.demdex.com** 구문을 따르는 경우 그에 따라 구현을 조정하고 Amazon Simple Storage Service (S3) 커넥터로 이동하여 데이터를 가져오거나 내보내야 합니다. Amazon S3를 사용하여 외부 계정을 구성하는 방법에 대한 자세한 내용은 이 [섹션](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md#step-1--configure-or-check-the-external-accounts-in-adobe-campaign)을 참조하십시오.

## 1단계:Adobe Campaign {#step-1--configure-or-check-the-external-accounts-in-adobe-campaign}에서 외부 계정을 구성하거나 확인합니다

먼저 다음과 같이 Adobe Campaign에서 외부 계정을 구성하거나 확인해야 합니다.

1. **[!UICONTROL Explorer]** 아이콘을 클릭합니다.
1. **[!UICONTROL Administration > Platform > External accounts]**(으)로 이동합니다. 언급된 SFTP 계정은 Adobe이 구성해야 하며 필요한 정보는 사용자에게 전달되어야 합니다.

   * **[!UICONTROL importSharedAudience]**:대상 가져오기에 전용 계정입니다.
   * **[!UICONTROL exportSharedAudience]**:대상 내보내기에 대한 전용 계정입니다.

   ![](assets/aam_config_1.png)

1. **[!UICONTROL Export audiences to the Adobe Marketing Cloud]** 외부 계정을 선택합니다.

1. **[!UICONTROL Type]** 드롭다운에서 **[!UICONTROL AWS S3]** 을 선택합니다.

1. 다음 세부 정보를 제공합니다.

   * **[!UICONTROL AWS S3 Account Server]**
서버의 URL은 다음과 같이 채워야 합니다.

      ```
      <S3bucket name>.s3.amazonaws.com/<s3object path>
      ```

   * **[!UICONTROL AWS access key ID]**
AWS 액세스 키 ID를 찾을 위치를 알아보려면 이  [페이지](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys) 를 참조하십시오.

   * **[!UICONTROL Secret access key to AWS]**
AWS에 대한 비밀 액세스 키를 찾을 수 있는 위치를 알아보려면 이  [페이지](https://aws.amazon.com/fr/blogs/security/wheres-my-secret-access-key/)를 참조하십시오.

   * **[!UICONTROL AWS Region]**
AWS 리전에 대한 자세한 내용은 이  [페이지](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/)를 참조하십시오.
   ![](assets/aam_config_2.png)

1. **[!UICONTROL Save]** 을 클릭하고 이전 단계에 자세히 설명된 대로 **[!UICONTROL Import audiences from the Adobe Marketing Cloud]** 외부 계정을 구성합니다.

이제 외부 계정이 구성되었습니다.

## 2단계:데이터 소스 구성 {#step-2--configure-the-data-source}

**수신자 - 방문자 ID**&#x200B;가 Audience Manager 내에 만들어집니다. 방문자 ID에 대해 기본적으로 구성된 기본 데이터 소스입니다. Campaign에서 만든 세그먼트는 이 데이터 소스의 일부가 됩니다.

**[!UICONTROL Recipient - Visitor ID]** 데이터 소스를 구성하려면:

1. **[!UICONTROL Explorer]** 노드에서 **[!UICONTROL Administration > Platform > AMC Data sources]** 을 선택합니다.
1. **[!UICONTROL Recipient - Visitor ID]**&#x200B;을(를) 선택합니다.
1. Adobe에서 제공한 **[!UICONTROL Data Source ID]** 및 **[!UICONTROL AAM Destination ID]** 을 입력합니다.

   ![](assets/aam_config_3.png)

## 3단계:캠페인 추적 서버 구성 {#step-3--configure-campaign-tracking-server}

People 핵심 서비스 또는 Audience Manager와의 통합을 구성하려면 Campaign 추적 서버를 구성해야 합니다.

Campaign 추적 서버가 도메인(CNAME)에 등록되어 있는지 확인해야 합니다. [이 문서](https://helpx.adobe.com/kr/campaign/kb/domain-name-delegation.html)에서 도메인 이름 위임에 대한 자세한 정보를 찾을 수 있습니다.

## 4단계:방문자 ID 서비스 {#step-4--configure-the-visitor-id-service} 구성

웹 속성 또는 웹 사이트에서 방문자 ID 서비스가 구성되지 않은 경우 서비스 구성 방법을 배우려면 다음 [document](https://experienceleague.adobe.com/docs/id-service/using/implementation/setup-aam-analytics.html) 를 참조하십시오 [video](https://helpx.adobe.com/marketing-cloud/how-to/email-marketing.html#step-two) .

구성 및 프로비저닝이 완료되면 통합을 사용하여 대상 또는 세그먼트를 가져오고 내보낼 수 있습니다.
