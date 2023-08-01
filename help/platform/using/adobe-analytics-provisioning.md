---
product: campaign
title: Adobe Analytics 커넥터 프로비저닝
description: Adobe Analytics 커넥터 프로비저닝에 대해 자세히 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용됩니다."
feature: Analytics Integration
role: User, Admin
level: Beginner
exl-id: 24e002aa-4e86-406b-92c7-74f242ee4b86
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '653'
ht-degree: 2%

---

# Adobe Analytics 커넥터 프로비저닝 {#adobe-analytics-connector-provisioning}



>[!IMPORTANT]
>
> 이러한 단계는 하이브리드 및 온프레미스 구현에서만 수행해야 합니다.
>
>호스팅 구현의 경우 다음으로 문의하십시오. [Adobe 고객 지원 센터](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 팀.

Adobe Campaign Classic과 Adobe Analytics 인증 간의 통합은 Adobe IMS(Identity Management Service)를 지원합니다.

* 마이그레이션된 외부 계정을 관리하는 경우 Adobe IMS를 구현하고 Adobe ID을 통해 Adobe Campaign에 연결해야 합니다. Adobe ID IMS를 통해 로그인한 사용자는 의 소유자여야 합니다 **데이터 커넥터** Adobe Analytics의 계정 및 **제품 프로필** 아래에 설명되어 있습니다.

* 새 커넥터를 구현하는 경우 Adobe IMS 구현은 선택 사항입니다. Adobe ID 사용자가 없으면 Adobe Campaign은 기술 사용자를 사용하여 Adobe Analytics과 동기화합니다.

이 통합이 작동하려면 Analytics 커넥터에만 사용되는 Adobe Analytics 제품 프로필을 만들어야 합니다. 그런 다음 Adobe I/O 프로젝트를 만들어야 합니다.

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

   보고서 세트가 없는 경우 다음을 통해 생성할 수 있습니다. [다음 단계](../../platform/using/adobe-analytics-connector.md#report-suite-analytics).

   ![](assets/do-not-localize/triggers_4.png)

1. 의 경우 **[!UICONTROL Metrics]** 기능, 추가 **[!UICONTROL Metrics]** 나중에 구성해야 합니다.

   필요한 경우 모든 권한 항목을 포함 목록에 추가하고 새 권한 항목을 자동으로 추가하는 자동 포함 옵션을 켤 수 있습니다.

   ![](assets/do-not-localize/triggers_13.png)

1. 의 경우 **[!UICONTROL Dimensions]** 기능, 추가 **[!UICONTROL Dimensions]** 나중에 구성해야 합니다.

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

이제 제품 프로필이 구성되었습니다. 그런 다음 Adobe I/O 프로젝트를 만들어야 합니다.

## Adobe I/O 프로젝트 만들기 {#create-adobe-io}

1. Adobe I/O 액세스 및 다음으로 로그인 **시스템 관리자** 을 참조하십시오.

   관리자 역할에 대한 자세한 내용은 다음을 참조하십시오. [페이지](https://helpx.adobe.com/enterprise/using/admin-roles.html).

1. **[!UICONTROL Create a new project]**&#x200B;를 클릭합니다.

   ![](assets/do-not-localize/triggers_5.png)

1. 클릭 **[!UICONTROL Add to Project]** 및 선택 **[!UICONTROL API]**.

   ![](assets/do-not-localize/triggers_6.png)

1. [!DNL Adobe Analytics]을(를) 선택하고 **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다 .

   ![](assets/do-not-localize/triggers_7.png)

1. 선택 **[!UICONTROL Service Account (JWT)]** 인증 유형으로 다음을 클릭: **[!UICONTROL Next]**.

   ![](assets/do-not-localize/triggers_8.png)

1. 다음 항목 선택 **[!UICONTROL Option 1: Generate a Key-Pair]** 옵션 및 클릭 **[!UICONTROL Generate a Key-Pair]**.

   그러면 config.zip 파일이 자동으로 다운로드됩니다.

   ![](assets/do-not-localize/triggers_9.png)

1. **[!UICONTROL Next]**&#x200B;를 클릭합니다.

   ![](assets/do-not-localize/triggers_10.png)

1. 다음 항목 선택 **[!UICONTROL Product profile]** 이(가) 다음에서 자세히 설명하는 이전 단계에서 생성됨 [섹션](#analytics-product-profile).

1. 그런 다음 을 클릭합니다. **[!UICONTROL Save Configured API]**.

   ![](assets/do-not-localize/triggers_11.png)

1. 프로젝트에서 을 선택합니다. [!DNL Adobe Analytics] 다음 정보를 복사합니다. **[!UICONTROL Service Account (JWT)]**:

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

   ![](assets/do-not-localize/triggers_12.png)

1. 6단계에서 생성된 개인 키를 사용합니다.

   이러한 자격 증명을 사용하여 트리거를 이미 설정한 경우 이 커넥터 구성에 대해 개인 키가 동일해야 합니다.

1. 다음 명령을 사용하여 개인 키를 인코딩합니다. `base64 ./private.key > private.key.base64`. 이렇게 하면 base64 컨텐츠가 새 파일에 저장됩니다 `private.key.base64`.

   >[!NOTE]
   >
   >개인 키를 복사/붙여넣을 때 추가 줄을 자동으로 추가할 수도 있습니다. 개인 키를 인코딩하기 전에 제거해야 합니다.

1. 파일에서 내용 복사 `private.key.base64`.

1. SSH를 통해 Adobe Campaign 인스턴스가 설치된 각 컨테이너에 로그인하고 다음 명령을 실행하여 Adobe Campaign에서 프로젝트 자격 증명을 추가합니다. `neolane` 사용자. 이렇게 하면 **[!UICONTROL Technical Account]** 인스턴스 구성 파일의 자격 증명입니다.

   ```
   nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
   ```

이제 Analytics 커넥터 사용을 시작하고 고객 행동을 추적할 수 있습니다.
