---
solution: Campaign Classic
product: campaign
title: Adobe Analytics 커넥터
description: Adobe Analytics 커넥터에 대해 자세히 알아보십시오. 프로비저닝
feature: Overview
role: User, Admin
level: Beginner
source-git-commit: 5f596c14639e085edab9c08c2e3abba36e76acd3
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 4%

---

# Adobe Analytics 커넥터 프로비저닝 {#adobe-analytics-connector-provisioning}

![](../../assets/v7-only.svg)

>[!IMPORTANT]
>
> 이러한 단계는 하이브리드 및 온-프레미스 구현에서만 수행해야 합니다.
>
>호스팅된 구현의 경우 고객 지원 센터 Adobe](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 팀에 문의하십시오.[

Adobe Campaign Classic과 Adobe Analytics 인증 간의 통합은 IMS(Adobe Identity Management Service)를 지원합니다. Analytics 커넥터 구현을 시작하기 전에 Adobe IMS를 구현하고 Adobe ID](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/connect-to-campaign/connecting-via-an-adobe-id/about-adobe-id.html?lang=en)를 통해 Campaign [에 연결해야 합니다.

이 통합이 작동하려면 Analytics 커넥터에만 사용되는 Adobe Analytics 제품 프로필을 만들어야 합니다. 그런 다음 Adobe I/O 프로젝트를 만들어야 합니다.

## Adobe Analytics 제품 프로필 만들기 {#analytics-product-profile}

제품 프로필은 사용자의 다른 Analytics 구성 요소에 대한 액세스 수준을 결정합니다.

이미 Analytics 제품 프로필이 있는 경우 Analytics 커넥터에만 사용되는 새 Adobe Analytics 제품 프로필을 만들어야 합니다. 이렇게 하면 제품 프로필이 이 통합에 대한 올바른 권한으로 설정되어 있는지 확인할 수 있습니다.

제품 프로필에 대한 자세한 내용은 [Admin Console 설명서](https://helpx.adobe.com/mt/enterprise/admin-guide.html) 를 참조하십시오.

1. [Admin Console](https://adminconsole.adobe.com/)에서 Adobe Analytics **[!UICONTROL Product]**&#x200B;를 선택합니다.

   ![](assets/do-not-localize/triggers_1.png)

1. **[!UICONTROL New Profile]**&#x200B;를 클릭합니다.

   ![](assets/do-not-localize/triggers_2.png)

1. **[!UICONTROL Product profile name]**&#x200B;을(를) 추가하는 것이 좋습니다. 구문은 다음과 같습니다. `reserved_campaign_classic_<Company Name>`. 그런 다음 **[!UICONTROL Next]** 을 클릭합니다.

   이 **[!UICONTROL Product profile]**&#x200B;은 잘못된 구성 오류를 방지하기 위해 Analytics 커넥터에만 사용해야 합니다.

1. 새로 만든 **[!UICONTROL Product profile]** 을 열고 **[!UICONTROL Permissions]** 탭을 선택합니다.

   ![](assets/do-not-localize/triggers_3.png)

1. **[!UICONTROL Edit]** 을(를) 클릭하고 더하기(+) 아이콘을 클릭하여 **[!UICONTROL Product profile]**&#x200B;에 할당할 권한을 선택합니다.

   권한 관리 방법에 대한 자세한 내용은 [Admin Console 설명서](https://helpx.adobe.com/mt/enterprise/using/manage-permissions-and-roles.html) 를 참조하십시오.

1. **[!UICONTROL Report Suites]** 기능의 경우 나중에 사용해야 하는 **[!UICONTROL Report Suites]**&#x200B;을 추가합니다.

   보고서 세트가 없는 경우 다음 [절차에 따라 만들 수 있습니다](../../platform/using/adobe-analytics-connector.md#report-suite-analytics).

   ![](assets/do-not-localize/triggers_4.png)

1. **[!UICONTROL Metrics]** 기능의 경우 나중에 구성해야 할 **[!UICONTROL Metrics]** 을 추가합니다.

   필요한 경우 모든 권한 항목을 포함된 목록에 추가하고 새 권한 항목을 자동으로 추가하는 자동 포함 옵션 을 전환할 수 있습니다.

   ![](assets/do-not-localize/triggers_13.png)

1. **[!UICONTROL Dimensions]** 기능의 경우 나중에 구성해야 할 **[!UICONTROL Dimensions]** 을 추가합니다.

1. **[!UICONTROL Report Suite Tools]** 기능에 대해 다음 권한을 추가합니다.

   * **[!UICONTROL Report suite Mgmt]**
   * **[!UICONTROL Conversion variables]**
   * **[!UICONTROL Success events]**
   * **[!UICONTROL Custom data Warehouse report]**
   * **[!UICONTROL Data sources manager]**
   * **[!UICONTROL Classifications]**

1. **[!UICONTROL Analytics Tools]** 기능에 대해 다음 권한을 추가합니다.

   * **[!UICONTROL Code Manager - Web services]**
   * **[!UICONTROL Logs - Web services]**
   * **[!UICONTROL Web services]**
   * **[!UICONTROL Web service access]**
   * **[!UICONTROL Calculated metric creation]**
   * **[!UICONTROL Segment creation]**

이제 제품 프로필이 구성되었습니다. 그런 다음 Adobe I/O 프로젝트를 만들어야 합니다.

## Adobe I/O 프로젝트 만들기 {#create-adobe-io}

1. Adobe I/O에 액세스하여 IMS 조직의 **시스템 관리자**&#x200B;로 로그인합니다.

   관리자 역할에 대한 자세한 내용은 이 [페이지](https://helpx.adobe.com/enterprise/using/admin-roles.html)를 참조하십시오.

1. **[!UICONTROL Create a new project]**&#x200B;를 클릭합니다.

   ![](assets/do-not-localize/triggers_5.png)

1. **[!UICONTROL Add to Project]** 을 클릭하고 **[!UICONTROL API]** 을 선택합니다.

   ![](assets/do-not-localize/triggers_6.png)

1. [!DNL Adobe Analytics]을(를) 선택하고 **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다 .

   ![](assets/do-not-localize/triggers_7.png)

1. 인증 유형으로 **[!UICONTROL Service Account (JWT)]**&#x200B;을(를) 선택하고 **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다.

   ![](assets/do-not-localize/triggers_8.png)

1. **[!UICONTROL Option 1: Generate a Key-Pair]** 옵션을 선택하고 **[!UICONTROL Generate a Key-Pair]** 를 클릭합니다.

   그러면 config.zip 파일이 자동으로 다운로드됩니다.

   ![](assets/do-not-localize/triggers_9.png)

1. **[!UICONTROL Next]**&#x200B;를 클릭합니다.

   ![](assets/do-not-localize/triggers_10.png)

1. 이 [섹션](#analytics-product-profile)에 자세히 설명된 이전 단계에서 생성된 **[!UICONTROL Product profile]**&#x200B;을 선택합니다.

1. 그런 다음 **[!UICONTROL Save Configured API]** 을 클릭합니다.

   ![](assets/do-not-localize/triggers_11.png)

1. 프로젝트에서 [!DNL Adobe Analytics] 을 선택하고 **[!UICONTROL Service Account (JWT)]** 아래에 다음 정보를 복사합니다.

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

   ![](assets/do-not-localize/triggers_12.png)

1. 다음 명령을 사용하여 이 서비스 계정 자격 증명을 nlserver에 붙여 넣습니다.

   ```
   nlserver config -instance:<instanceName> -setimsjwtauth::<ImsOrgId>/<ClientId>/<TechnicalAccountId>/<ClientSecret>/<$(base64 -w0 /path/to/private.key)>
   ```

이제 Analytics 커넥터 사용을 시작하고 고객 행동을 추적할 수 있습니다.
