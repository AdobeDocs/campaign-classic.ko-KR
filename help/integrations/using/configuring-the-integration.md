---
title: ' 통합 구성'
seo-title: ' 통합 구성'
description: ' 통합 구성'
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 4%

---


#  통합 구성{#configuring-the-integration}

## Configuring in Adobe Campaign {#configuring-in-adobe-campaign}

이 두 솔루션을 함께 사용하려면 서로 연결하도록 구성해야 합니다.

아래 절차에 따라 Adobe Campaign에서 구성을 시작하십시오.

1. [Adobe Campaign에 AEM 통합 패키지 설치](#install-the-aem-integration-package-in-adobe-campaign)
1. [외부 계정 구성](#configure-the-external-account)
1. [AEM 리소스 필터링 구성](#configure-aem-resources-filtering)

개인화 필드 및 블록 관리와 같은 고급 구성의 경우 Adobe Experience Manager [설명서를 참조하십시오](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html).

### Adobe Campaign에 AEM 통합 패키지 설치 {#install-the-aem-integration-package-in-adobe-campaign}

먼저 **[!UICONTROL AEM integration]** 패키지를 설치해야 합니다.

1. Adobe Campaign 인스턴스의 상단 도구 모음 **[!UICONTROL Tools]** 에서 선택합니다.
1. **[!UICONTROL Tools > Advanced > Import package...]**&#x200B;을(를) 선택합니다.

   ![](assets/aem_config_1.png)

1. **[!UICONTROL Install a standard package]**&#x200B;을(를) 선택합니다.
1. 그런 **[!UICONTROL AEM integration]** 다음 **[!UICONTROL Next]** 단추를 클릭합니다.

   ![](assets/aem_config_2.png)

1. 다음 창에서 **[!UICONTROL Start]** 단추를 클릭하여 패키지 설치를 시작합니다. 설치가 완료되면 창을 닫습니다.

### AEM 연산자에 대한 보안 영역 구성 {#configure-the-security-zone-for-aem-operator}

이 **[!UICONTROL AEM integration]** 패키지는 Campaign에서 **[!UICONTROL aemserver]** 연산자를 설정합니다. 이 연산자는 Adobe Experience Manager 서버를 Adobe Campaign에 연결하는 데 사용됩니다.

이 연산자가 Adobe Experience Manager을 통해 Adobe Campaign에 연결되도록 보안 영역을 구성해야 합니다.

>[!CAUTION]
>
>보안 문제를 방지하기 위해 AEM 전용 보안 영역을 만드는 것이 좋습니다. For more on this, refer to the Installation [guide](../../installation/using/configuring-campaign-server.md#defining-security-zones).

Adobe에서 캠페인 인스턴스를 호스팅하는 경우 Adobe 지원 팀에 문의하십시오. 온-프레미스 캠페인을 사용하는 경우 아래 단계를 따르십시오.

1. serverConf.xml **구성 파일을** 엽니다.
1. 선택한 보안 영역의 **allowUserPassword** 특성에 액세스하여 **true로 설정합니다**.

   그러면 Adobe Experience Manager이 로그인/암호를 통해 Adobe Campaign에 연결할 수 있습니다.

### 외부 계정 구성 {#configure-the-external-account}

패키지 **[!UICONTROL AEM integration]** 가 Adobe Experience Cloud에 대한 외부 계정을 만들었습니다. 이제 Adobe Experience Manager 인스턴스와 연결되도록 구성해야 합니다.

AEM 외부 계정을 구성하려면 아래 단계를 따르십시오.

1. **[!UICONTROL Explorer]** 버튼을 클릭합니다.

   ![](assets/aem_config_3.png)

1. **[!UICONTROL Administration > Platform > External accounts]**&#x200B;을(를) 선택합니다.
1. From the **[!UICONTROL External account]** list, select **[!UICONTROL AEM instance]**.
1. AEM 작성 인스턴스의 매개 변수를 입력합니다.

   * **[!UICONTROL Server]**
   * **[!UICONTROL Account]**
   * **[!UICONTROL Password]**

   >[!NOTE]
   >
   >주소가 슬래시로 끝나지 않도록 **[!UICONTROL Server]** 하십시오.

   ![](assets/aem_config_4.png)

1. 체크 **[!UICONTROL Enabled]** 상자를
1. **[!UICONTROL Save]** 버튼을 클릭합니다.

### AEM 리소스 필터링 구성 {#configure-aem-resources-filtering}

AEMResourceTypeFilter **** 옵션은 Adobe Campaign에서 사용할 수 있는 Experience Manager 리소스 유형을 필터링하는 데 사용됩니다. Adobe Campaign은 Adobe Campaign에서만 사용하도록 특별히 고안된 Experience Manager 콘텐츠를 검색할 수 있습니다.

옵션이 구성되어 있는지 **[!UICONTROL AEMResourceTypeFilter]** 확인하려면:

1. **[!UICONTROL Explorer]** 버튼을 클릭합니다.
1. **[!UICONTROL Administration > Platform > Options]**&#x200B;을(를) 선택합니다.
1. From the **[!UICONTROL Options]** list, select **[!UICONTROL AEMResourceTypeFilter]**.
1. 필드에서 **[!UICONTROL Value (text)]** 경로는 다음과 같아야 합니다.

   ```
   mcm/campaign/components/newsletter,mcm/campaign/components/campaign_newsletterpage,mcm/neolane/components/newsletter
   ```

   또는 경우에 따라:

   ```
   mcm/campaign/components/newsletter
   ```

   ![](assets/aem_config_5.png)

## Adobe Experience Manager에서 구성 {#configuring-in-adobe-experience-manager}

아래 절차에 따라 Adobe Experience Manager에서 구성을 시작하십시오.

1. AEM **제작 인스턴스에서 AEM 게시 인스턴스로 복제할** 복제를 구성합니다.

   복제 구성 방법을 알아보려면 Adobe Experience Manager [설명서를 참조하십시오](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/replication.html).

1. 제작 인스턴스에 통합 **FeaturePack** 을 설치한 다음 게시 인스턴스에 설치를 복제합니다. (AEM 버전 5.6.1 및 6.0에만 해당).

   Feature Pack 설치 방법에 대한 자세한 내용은 Adobe Experience Manager [설명서를 참조하십시오](https://helpx.adobe.com/experience-manager/aem-previous-versions.html).

1. 전용 **Cloud Service을 구성하여 Adobe Experience Manager을 Adobe Campaign에 연결합니다**.

   Cloud Services을 통해 두 솔루션을 연결하는 방법을 알아보려면 Adobe Experience Manager [설명서를 참조하십시오](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html#ConfiguringAdobeExperienceManager) .

1. Externalizer **서비스를 구성합니다**.

   구성 방법을 알려면 Adobe Experience Manager [설명서를 참조하십시오](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/externalizer.html).

