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

개인화 필드 및 블록 관리와 같은 고급 구성용. Adobe Experience Manager 참조 [설명서](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html).

### Adobe Campaign에 AEM 통합 패키지 설치 {#install-the-aem-integration-package-in-adobe-campaign}

먼저 다음을 설치해야 합니다. **[!UICONTROL AEM integration]** 패키지.

1. Adobe Campaign 인스턴스에서 을 선택합니다 **[!UICONTROL Tools]** 을 클릭합니다.
1. **[!UICONTROL Tools > Advanced > Import package...]**&#x200B;을(를) 선택합니다.

   ![](assets/aem_config_1.png)

1. **[!UICONTROL Install a standard package]**&#x200B;을(를) 선택합니다.
1. 확인 **[!UICONTROL AEM integration]** 그런 다음 **[!UICONTROL Next]** 단추를 클릭합니다.

   ![](assets/aem_config_2.png)

1. 다음 창에서 **[!UICONTROL Start]** 단추를 클릭하여 패키지 설치를 시작합니다. 설치가 완료되면 창을 닫습니다.

### AEM 연산자에 대한 보안 영역 구성 {#configure-the-security-zone-for-aem-operator}

다음 **[!UICONTROL AEM integration]** 패키지가 **[!UICONTROL aemserver]** Campaign의 연산자입니다. 이 연산자는 Adobe Experience Manager 서버를 Adobe Campaign에 연결하는 데 사용됩니다.

Adobe Experience Manager을 통해 Adobe Campaign에 연결하려면 이 연산자에 대한 보안 영역을 구성해야 합니다.

>[!CAUTION]
>
>보안 문제를 방지하기 위해 AEM 전용 보안 영역을 만드는 것이 좋습니다. 자세한 내용은 설치 를 참조하십시오. [안내서](../../installation/using/security-zones.md).

Campaign 인스턴스가 Adobe에 의해 호스팅되는 경우 [Adobe 고객 지원 센터](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 팀. Campaign 온-프레미스를 사용하는 경우 아래 단계를 따르십시오.

1. 를 엽니다. **serverConf.xml** 구성 파일입니다.
1. 액세스 **allowUserpassword** 선택한 보안 영역의 속성 및 설정 **true**.

   이렇게 하면 Adobe Experience Manager에서 로그인/암호를 통해 Adobe Campaign에 연결할 수 있습니다.

### 외부 계정 구성 {#configure-the-external-account}

다음 **[!UICONTROL AEM integration]** 패키지가 Adobe Experience Cloud에 대한 외부 계정을 만들었습니다. 이제 Adobe Experience Manager 인스턴스와 연결하도록 구성해야 합니다.

AEM 외부 계정을 구성하려면 아래 단계를 수행합니다.

1. **[!UICONTROL Explorer]** 버튼을 클릭합니다.

   ![](assets/aem_config_3.png)

1. **[!UICONTROL Administration > Platform > External accounts]**&#x200B;을(를) 선택합니다.
1. 다음에서 **[!UICONTROL External account]** 목록, 선택 **[!UICONTROL AEM instance]**.
1. AEM 작성 인스턴스에 대한 매개 변수를 입력합니다.

   * **[!UICONTROL Server]**
   * **[!UICONTROL Account]**
   * **[!UICONTROL Password]**

   >[!NOTE]
   >
   >다음을 확인하십시오. **[!UICONTROL Server]** 주소는 뒤쪽 슬래시로 끝나지 않습니다.

   ![](assets/aem_config_4.png)

1. 다음 확인: **[!UICONTROL Enabled]** 상자.
1. **[!UICONTROL Save]** 버튼을 클릭합니다.

### AEM 리소스 필터링 구성 {#configure-aem-resources-filtering}

다음 **AEMResourceTypeFilter** 옵션은 Adobe Campaign에서 사용할 수 있는 Experience Manager 리소스 유형을 필터링하는 데 사용됩니다. 이를 통해 Adobe Campaign은 Adobe Campaign에서만 사용하도록 특별히 설계된 Experience Manager 컨텐츠를 검색할 수 있습니다.

다음을 확인하십시오. **[!UICONTROL AEMResourceTypeFilter]** 옵션이 구성됨:

1. **[!UICONTROL Explorer]** 버튼을 클릭합니다.
1. **[!UICONTROL Administration > Platform > Options]**&#x200B;을(를) 선택합니다.
1. 다음에서 **[!UICONTROL Options]** 목록, 선택 **[!UICONTROL AEMResourceTypeFilter]**.
1. 다음에서 **[!UICONTROL Value (text)]** 필드, 경로는 다음과 같아야 합니다.

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

1. 구성 **복제** 를 사용하여 AEM 작성 인스턴스에서 AEM 게시 인스턴스로 복제할 수 있습니다.

   복제를 구성하는 방법에 대해 알아보려면 Adobe Experience Manager 를 참조하십시오. [설명서](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/replication.html).

1. 전용 을 구성하여 Adobe Experience Manager을 Adobe Campaign에 연결 **Cloud Service**.

   Cloud Service을 통해 두 솔루션을 모두 연결하는 방법은 Adobe Experience Manager 를 참조하십시오 [설명서](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html#ConfiguringAdobeExperienceManager) .

1. 구성 **Externalizer 서비스**.

   구성 방법에 대해 알아보려면 Adobe Experience Manager 를 참조하십시오. [설명서](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/externalizer.html).
