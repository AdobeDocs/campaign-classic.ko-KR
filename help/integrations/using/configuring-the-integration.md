---
title: 통합 구성
seo-title: 통합 구성
description: 통합 구성
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Configuring the integration{#configuring-the-integration}

## Adobe Campaign에서 구성 {#configuring-in-adobe-campaign}

이 두 솔루션을 함께 사용하려면 서로 연결하도록 구성해야 합니다.

아래 절차에 따라 Adobe Campaign에서 구성을 시작합니다.

1. [Adobe Campaign에서 AEM 통합 패키지 설치](#install-the-aem-integration-package-in-adobe-campaign)
1. [외부 계정 구성](#configure-the-external-account)
1. [AEM 리소스 필터링 구성](#configure-aem-resources-filtering)

개인화 필드 및 블록 관리와 같은 고급 구성의 경우 Adobe Experience Manager [설명서를](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html)참조하십시오.

### Adobe Campaign에서 AEM 통합 패키지 설치 {#install-the-aem-integration-package-in-adobe-campaign}

먼저 **[!UICONTROL AEM integration]** 패키지를 설치해야 합니다.

1. Adobe Campaign 인스턴스의 상단 도구 모음에서 **[!UICONTROL Tools]** 을 선택합니다.
1. 을 **[!UICONTROL Tools > Advanced > Import package...]**&#x200B;선택합니다.

   ![](assets/aem_config_1.png)

1. 을 **[!UICONTROL Install a standard package]**&#x200B;선택합니다.
1. 그런 **[!UICONTROL AEM integration]** 다음 **[!UICONTROL Next]** 단추를 클릭합니다.

   ![](assets/aem_config_2.png)

1. 다음 창에서 **[!UICONTROL Start]** 단추를 클릭하여 패키지 설치를 시작합니다. 설치가 완료되면 창을 닫습니다.

### AEM 연산자에 대한 보안 영역 구성 {#configure-the-security-zone-for-aem-operator}

패키지는 Campaign에서 **[!UICONTROL AEM integration]** **[!UICONTROL aemserver]** 연산자를 설정합니다. 이 연산자는 Adobe Experience Manager 서버를 Adobe Campaign에 연결하는 데 사용됩니다.

이 운영자가 Adobe Experience Manager를 통해 Adobe Campaign에 연결하도록 보안 영역을 구성해야 합니다.

>[!CAUTION]
>
>보안 문제를 방지하려면 AEM 전용 보안 영역을 만드는 것이 좋습니다. 자세한 내용은 설치 [안내서를](../../installation/using/configuring-campaign-server.md#defining-security-zones)참조하십시오.

Adobe에서 캠페인 인스턴스를 호스팅하는 경우 Adobe 지원 팀에 문의하십시오. Campaign 온프레미스를 사용하는 경우 아래 단계를 따르십시오.

1. serverConf. **xml** 구성 파일을 엽니다.
1. 선택한 보안 **영역의 allowUserPassword** 특성에 액세스하고 **true로 설정합니다**.

   그러면 Adobe Experience Manager가 로그인/암호를 통해 Adobe Campaign을 연결할 수 있습니다.

### 외부 계정 구성 {#configure-the-external-account}

패키지가 **[!UICONTROL AEM integration]** Adobe Experience Cloud에 대한 외부 계정을 만들었습니다. 이제 Adobe Experience Manager 인스턴스와 연결하도록 구성해야 합니다.

AEM 외부 계정을 구성하려면 아래 단계를 따르십시오.

1. 단추를 **[!UICONTROL Explorer]** 클릭합니다.

   ![](assets/aem_config_3.png)

1. 을 **[!UICONTROL Administration > Platform > External accounts]**&#x200B;선택합니다.
1. 목록에서 **[!UICONTROL External account]** 선택합니다 **[!UICONTROL AEM instance]**.
1. AEM 작성 인스턴스에 대한 매개 변수를 입력합니다.

   * **[!UICONTROL Server]**
   * **[!UICONTROL Account]**
   * **[!UICONTROL Password]**
   >[!NOTE]
   >
   >주소가 뒤에 슬래시로 끝나지 않도록 **[!UICONTROL Server]** 하십시오.

   ![](assets/aem_config_4.png)

1. 체크 **[!UICONTROL Enabled]** 상자를 선택합니다.
1. 단추를 **[!UICONTROL Save]** 클릭합니다.

### AEM 리소스 필터링 구성 {#configure-aem-resources-filtering}

**AEMResourceTypeFilter **옵션은 Adobe Campaign에서 사용할 수 있는 Experience Manager 리소스 유형을 필터링하는 데 사용됩니다. 이를 통해 Adobe Campaign은 Adobe Campaign에서만 사용하도록 특별히 설계된 Experience Manager 컨텐츠를 검색할 수 있습니다.

옵션이 구성되어 있는지 확인하려면 **[!UICONTROL AEMResourceTypeFilter]** 다음을 수행하십시오.

1. 단추를 **[!UICONTROL Explorer]** 클릭합니다.
1. 을 **[!UICONTROL Administration > Platform > Options]**&#x200B;선택합니다.
1. 목록에서 **[!UICONTROL Options]** 선택합니다 **[!UICONTROL AEMResourceTypeFilter]**.
1. 필드에서 **[!UICONTROL Value (text)]** 경로는 다음과 같아야 합니다.

   ```
   mcm/campaign/components/newsletter,mcm/campaign/components/campaign_newsletterpage,mcm/neolane/components/newsletter
   ```

   또는 경우에 따라 다음을 수행합니다.

   ```
   mcm/campaign/components/newsletter
   ```

   ![](assets/aem_config_5.png)

## Adobe Experience Manager에서 구성 {#configuring-in-adobe-experience-manager}

아래 절차에 따라 Adobe Experience Manager에서 구성을 시작하십시오.

1. AEM 작성 인스턴스에서 AEM 게시 인스턴스로 복제할 **복제를** 구성합니다.

   복제를 구성하는 방법에 대한 자세한 내용은 Adobe Experience Manager [설명서를](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/replication.html)참조하십시오.

1. 제작 인스턴스에 통합 **FeaturePack** 을 설치한 다음 게시 인스턴스에 설치를 복제합니다. (AEM 버전 5.6.1 및 6.0에만 해당).

   Feature Pack 설치 방법에 대한 자세한 내용은 Adobe Experience Manager [설명서를](https://helpx.adobe.com/experience-manager/aem-previous-versions.html)참조하십시오.

1. 전용 클라우드 서비스를 구성하여 Adobe Experience Manager를 Adobe Campaign에 **연결합니다**.

   클라우드 서비스를 통해 두 솔루션을 연결하는 방법에 대한 자세한 내용은 Adobe Experience Manager [설명서를](https://helpx.adobe.com/experience-manager/6-4/sites/administering/using/campaignonpremise.html#ConfiguringAdobeExperienceManager) 참조하십시오.

1. Externalizer **서비스를**&#x200B;구성합니다.

   구성 방법에 대한 자세한 내용은 Adobe Experience Manager [설명서를](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/externalizer.html)참조하십시오.

