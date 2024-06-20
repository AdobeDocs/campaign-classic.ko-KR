---
product: campaign
title: Adobe Analytics 커넥터 프로비저닝
description: Adobe Analytics 커넥터 프로비저닝에 대해 자세히 알아보기
badge-v7-prem: label="온-프레미스/하이브리드만" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="v7 온-프레미스 및 하이브리드 배포에만 적용"
feature: Analytics Integration
role: User, Admin
level: Beginner
exl-id: 24e002aa-4e86-406b-92c7-74f242ee4b86
source-git-commit: a38d53f4b37aadbc53446b5e399af2eae56c12af
workflow-type: tm+mt
source-wordcount: '631'
ht-degree: 1%

---

# Adobe Analytics 커넥터 프로비전 {#adobe-analytics-connector-provisioning}

>[!CAUTION]
>
> 이러한 단계는 하이브리드 및 온프레미스 구현에서만 수행해야 합니다.
>
>호스팅 및 Campaign Managed Services 구현의 경우 다음으로 문의하십시오. [Adobe 고객 지원 센터](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 팀.

Adobe Campaign Classic과 Adobe Analytics 인증 간의 통합은 Adobe IMS(Identity Management Service)를 지원합니다.

* 마이그레이션된 외부 계정을 관리하는 경우 Adobe IMS를 구현하고 Adobe ID을 통해 Adobe Campaign에 연결해야 합니다.

  Adobe ID IMS를 통해 로그인한 사용자는 의 소유자여야 합니다. **데이터 커넥터** Adobe Analytics 계정 및 다음에 대한 권한이 있습니다. **제품 프로필** 언급 [아래](#analytics-product-profile).

문제는 데이터 커넥터 소유자가 Campaign에 로그인하여 Analytics와의 통합을 시도한 사용자와 다른 사용자라는 것이었습니다.

* 새 커넥터를 구현하는 경우 Adobe IMS 구현은 선택 사항입니다. Adobe ID 사용자가 없으면 Adobe Campaign은 기술 사용자를 사용하여 Adobe Analytics과 동기화합니다.

이 통합이 작동하려면 Analytics 커넥터에만 사용되는 Adobe Analytics 제품 프로필을 만들어야 합니다. 그런 다음 Developer Console 프로젝트를 만들어야 합니다.

>[!AVAILABILITY]
>
> 서비스 계정(JWT) 자격 증명은 Adobe에서 더 이상 사용되지 않으며, Adobe 솔루션 및 앱과 Campaign 통합은 이제 OAuth 서버 간 자격 증명을 사용해야 합니다. </br>
>
> * Campaign과 인바운드 통합을 구현하면에 자세히 설명된 대로 기술 계정을 마이그레이션해야 합니다. [이 설명서](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#_blank). 기존 서비스 계정(JWT) 자격 증명은 2025년 1월 27일까지 계속 작동합니다.</br>
>
> * Campaign-Analytics 통합 또는 Experience Cloud 트리거 통합과 같은 아웃바운드 통합을 구현한 경우 2025년 1월 27일까지 계속 작동합니다. 그러나 해당 날짜 이전에 Campaign 환경을 v7.4.1로 업그레이드하고 기술 계정을 OAuth로 마이그레이션해야 합니다.

## Adobe Analytics 제품 프로필 만들기 {#analytics-product-profile}

제품 프로필은 사용자가 다른 Analytics 구성 요소에 액세스할 수 있는 수준을 결정합니다.

Analytics 제품 프로필이 이미 있는 경우 Analytics 커넥터에만 사용되는 새 Adobe Analytics 제품 프로필을 만들어야 합니다. 이렇게 하면 제품 프로필이 이 통합에 대한 올바른 권한으로 설정됩니다.

제품 프로필에 대한 자세한 내용은 [Admin Console 설명서](https://helpx.adobe.com/mt/enterprise/admin-guide.html).

1. 다음에서 [관리 콘솔](https://adminconsole.adobe.com/), Adobe Analytics 선택 **[!UICONTROL Product]**.

   ![](assets/do-not-localize/triggers_1.png)

1. **[!UICONTROL New Profile]**&#x200B;를 클릭합니다.

   ![](assets/do-not-localize/triggers_2.png)

1. 추가 **[!UICONTROL Product profile name]**, 다음 구문을 사용하는 것이 좋습니다. `reserved_campaign_classic_<Company Name>`. 그런 다음 을 클릭합니다. **[!UICONTROL Next]**.

   이 **[!UICONTROL Product profile]** 잘못된 구성 오류를 방지하기 위해 Analytics 커넥터에만 사용해야 합니다.

1. 새로 만든 을 엽니다. **[!UICONTROL Product profile]** 및 선택 **[!UICONTROL Permissions]** 탭.

   ![](assets/do-not-localize/triggers_3.png)

1. 다양한 기능을 구성하려면 다음을 클릭하십시오. **[!UICONTROL Edit]** 및에 할당할 권한을 선택합니다. **[!UICONTROL Product profile]** 더하기(+) 아이콘을 클릭합니다.

   권한 관리 방법에 대한 자세한 내용은 [Admin Console 설명서](https://helpx.adobe.com/mt/enterprise/using/manage-permissions-and-roles.html).

1. 의 경우 **[!UICONTROL Report Suites]** 기능, 추가 **[!UICONTROL Report Suites]** 나중에 를 사용해야 합니다.

   보고서 세트가 없는 경우 다음을 통해 생성할 수 있습니다. [다음 단계](../../integrations/using/gs-aa.md).

   ![](assets/do-not-localize/triggers_4.png)

1. 의 경우 **[!UICONTROL Metrics]** 기능, 추가 **[!UICONTROL Metrics]** 나중에 구성해야 합니다.

   필요한 경우 모든 권한 항목을 포함 목록에 추가하고 새 권한 항목을 자동으로 추가하는 자동 포함 옵션을 켤 수 있습니다.

   ![](assets/do-not-localize/triggers_13.png)

1. 의 경우 **[!UICONTROL Dimensions]** 기능, 추가 **[!UICONTROL Dimensions]** 향후 구성에 필요합니다.

   선택한 Dimension이 외부 계정에서 구성할 eVar와 일치하고 Adobe Analytics의 해당 eVar 번호와 일치하는지 확인합니다.

1. 의 경우 **[!UICONTROL Report Suite Tools]** 기능을 사용하려면 다음 권한을 추가하십시오.

   * **[!UICONTROL Report suite Mgmt]**
   * **[!UICONTROL Conversion variables]**
   * **[!UICONTROL Success events]**
   * **[!UICONTROL Custom data Warehouse report]**
   * **[!UICONTROL Data sources manager]**
   * **[!UICONTROL Classifications]**

1. 의 경우 **[!UICONTROL Analytics Tools]** 기능을 사용하려면 다음 권한을 추가하십시오.

   * **[!UICONTROL Code Manager - Web services]**
   * **[!UICONTROL Logs - Web services]**
   * **[!UICONTROL Web services]**
   * **[!UICONTROL Web service access]**
   * **[!UICONTROL Calculated metric creation]**
   * **[!UICONTROL Segment creation]**

이제 제품 프로필이 구성되었습니다. 그런 다음 OAuth 프로젝트를 만들어야 합니다.

## OAuth 프로젝트 만들기 {#create-adobe-io}

Adobe Analytics 커넥터 구성을 계속하려면 Adobe Developer 콘솔에 액세스하고 OAuth 서버 간 프로젝트를 만듭니다.

을(를) 참조하십시오 [이 페이지](oauth-technical-account.md#oauth-service) 을 참조하십시오.

## 구성 및 사용 {#adobe-analytics-connector-usage}

에서 Adobe Campaign 및 Adobe Analytics을 사용하여 작업하는 방법을 알아봅니다. [Adobe Campaign v8 설명서](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/connect/ac-aa){target="_blank"}.