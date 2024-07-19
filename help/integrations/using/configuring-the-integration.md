---
product: campaign
title: Adobe Experience Manager 통합 구성
description: Campaign-AEM 통합 구성 방법 알아보기
feature: Experience Manager Integration
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
audience: integrations
content-type: reference
exl-id: 54ee88b2-e646-4fb9-abec-957f0096f15f
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 2%

---

# Campaign-AEM 통합 구성{#configuring-the-integration}



## Adobe Campaign의 구성 단계 {#configuring-in-adobe-campaign}

이 두 솔루션을 함께 사용하려면 서로 연결하도록 구성해야 합니다.

Adobe Campaign에서 구성을 시작하려면 아래 단계를 따르십시오.

1. [Adobe Campaign에 AEM 통합 패키지 설치](#install-the-aem-integration-package-in-adobe-campaign)
1. [외부 계정 구성](#configure-the-external-account)
1. [AEM 리소스 필터링 구성](#configure-aem-resources-filtering)

개인화 필드 및 블록 관리와 같은 고급 구성용. Adobe Experience Manager [설명서](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html)를 참조하세요.

### Adobe Campaign에 AEM 통합 패키지 설치 {#install-the-aem-integration-package-in-adobe-campaign}

먼저 **[!UICONTROL AEM integration]** 패키지를 설치해야 합니다.

1. Adobe Campaign 인스턴스의 위쪽 도구 모음에서 **[!UICONTROL Tools]**&#x200B;을(를) 선택합니다.
1. **[!UICONTROL Tools > Advanced > Import package...]**&#x200B;을(를) 선택합니다.

   ![](assets/aem_config_1.png)

1. **[!UICONTROL Install a standard package]**&#x200B;을(를) 선택합니다.
1. **[!UICONTROL AEM integration]**&#x200B;을(를) 선택한 다음 **[!UICONTROL Next]** 단추를 클릭합니다.

   ![](assets/aem_config_2.png)

1. 다음 창에서 **[!UICONTROL Start]** 단추를 클릭하여 패키지 설치를 시작합니다. 설치가 완료되면 창을 닫습니다.

### AEM 연산자에 대한 보안 영역 구성 {#configure-the-security-zone-for-aem-operator}

**[!UICONTROL AEM integration]** 패키지는 Campaign에서 **[!UICONTROL aemserver]** 연산자를 설정합니다. 이 연산자는 Adobe Experience Manager 서버를 Adobe Campaign에 연결하는 데 사용됩니다.

Adobe Experience Manager을 통해 Adobe Campaign에 연결하려면 이 연산자에 대한 보안 영역을 구성해야 합니다.

>[!CAUTION]
>
>보안 문제를 방지하기 위해 AEM 전용 보안 영역을 만드는 것이 좋습니다. 자세한 내용은 설치 [안내서](../../installation/using/security-zones.md)를 참조하세요.

Campaign 인스턴스가 Adobe에 의해 호스팅되는 경우 [고객 지원 Adobe](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 팀에 문의하십시오. Campaign 온-프레미스를 사용하는 경우 아래 단계를 따르십시오.

1. **serverConf.xml** 구성 파일을 엽니다.
1. 선택한 보안 영역의 **allowUserPassword** 특성에 액세스하여 **true**(으)로 설정하십시오.

   이렇게 하면 Adobe Experience Manager에서 로그인/암호를 통해 Adobe Campaign에 연결할 수 있습니다.

### 외부 계정 구성 {#configure-the-external-account}

**[!UICONTROL AEM integration]** 패키지가 Adobe Experience Cloud에 대한 외부 계정을 만들었습니다. 이제 Adobe Experience Manager 인스턴스와 연결하도록 구성해야 합니다.

AEM 외부 계정을 구성하려면 아래 단계를 수행합니다.

1. **[!UICONTROL Explorer]** 버튼을 클릭합니다.

   ![](assets/aem_config_3.png)

1. **[!UICONTROL Administration > Platform > External accounts]**&#x200B;을(를) 선택합니다.
1. **[!UICONTROL External account]** 목록에서 **[!UICONTROL AEM instance]**&#x200B;을(를) 선택합니다.
1. AEM 작성 인스턴스에 대한 매개 변수를 입력합니다.

   * **[!UICONTROL Server]**
   * **[!UICONTROL Account]**
   * **[!UICONTROL Password]**

   >[!NOTE]
   >
   >**[!UICONTROL Server]** 주소가 뒤쪽 슬래시로 끝나지 않아야 합니다.

   ![](assets/aem_config_4.png)

1. **[!UICONTROL Enabled]** 상자를 선택합니다.
1. **[!UICONTROL Save]** 버튼을 클릭합니다.

### AEM 리소스 필터링 구성 {#configure-aem-resources-filtering}

**AEMResourceTypeFilter** 옵션은 Adobe Campaign에서 사용할 수 있는 Experience Manager 리소스 유형을 필터링하는 데 사용됩니다. 이를 통해 Adobe Campaign은 Adobe Campaign에서만 사용하도록 특별히 설계된 Experience Manager 컨텐츠를 검색할 수 있습니다.

**[!UICONTROL AEMResourceTypeFilter]** 옵션이 구성되어 있는지 확인하려면:

1. **[!UICONTROL Explorer]** 버튼을 클릭합니다.
1. **[!UICONTROL Administration > Platform > Options]**&#x200B;을(를) 선택합니다.
1. **[!UICONTROL Options]** 목록에서 **[!UICONTROL AEMResourceTypeFilter]**&#x200B;을(를) 선택합니다.
1. **[!UICONTROL Value (text)]** 필드의 경로는 다음과 같아야 합니다.

   ```
   mcm/campaign/components/newsletter,mcm/campaign/components/campaign_newsletterpage,mcm/neolane/components/newsletter
   ```

   또는 경우에 따라:

   ```
   mcm/campaign/components/newsletter
   ```

   ![](assets/aem_config_5.png)

## Adobe Experience Manager의 구성 단계 {#configuring-in-adobe-experience-manager}

Adobe Experience Manager에서 구성을 시작하려면 아래 단계를 따르십시오.

1. AEM 작성 인스턴스에서 AEM 게시 인스턴스로 복제하도록 **복제**&#x200B;를 구성하십시오.

   복제를 구성하는 방법에 대해 알아보려면 Adobe Experience Manager [설명서](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/replication.html)를 참조하세요.

1. 전용 **Cloud Service**&#x200B;을(를) 구성하여 Adobe Experience Manager을 Adobe Campaign에 연결합니다.

   Cloud Service을 통해 두 솔루션을 모두 연결하는 방법은 Adobe Experience Manager [설명서](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html#ConfiguringAdobeExperienceManager) 를 참조하십시오.

1. **외부화 서비스**&#x200B;를 구성하십시오.

   구성 방법에 대해 알아보려면 Adobe Experience Manager [설명서](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/externalizer.html)를 참조하세요.
