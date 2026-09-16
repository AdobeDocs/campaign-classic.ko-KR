---
product: campaign
title: Adobe Analytics 2.0 API로 마이그레이션
description: Campaign Classic - Adobe Analytics 2.0 API 마이그레이션 안내서
feature: Technote, Analytics Integration
hide: true
source-git-commit: 64460d51b002a7821bba9c2998d9ccccab3046ad
workflow-type: tm+mt
source-wordcount: '874'
ht-degree: 1%
---
# Adobe Analytics 2.0 API로 마이그레이션 {#analytics-2-migration}

Adobe Analytics 1.4 API가 [수명이 종료됨](https://developer.adobe.com/analytics-apis/docs/1.4/guides/eol){target="_blank"}입니다. Campaign 인스턴스를 Adobe Analytics에 연결하는 [Web Analytics 커넥터](../../integrations/using/gs-aa.md)는 이러한 API를 사용하므로 통합을 계속 실행하려면 새 Analytics 2.0 API를 사용하는 빌드로 업그레이드해야 합니다.

>[!CAUTION]
>
>업그레이드를 하면 커넥터 [!UICONTROL webAnalyticsSendMetrics]과(와) [!UICONTROL webAnalyticsGetWebEvents]을(를) 구동하는 기본 제공 기술 워크플로우 두 개를 다시 가져옵니다([Web Analytics 워크플로우 참조](../../workflow/using/web-analytics.md)에서 수행하는 작업 참조). 이러한 워크플로우 위에서 만든 모든 사용자 지정은 다시 가져오기로 덮어씁니다. 이러한 기본 제공 워크플로를 직접 수정하지 마십시오. 대신 별도의 사용자 지정 워크플로에서 사용자 지정을 빌드하십시오. 이렇게 하면 향후 업그레이드시 덮어쓰지 않습니다. 또한 업그레이드는 기본 제공 Analytics JavaScript 파일도 업데이트합니다. 사용자 지정 워크플로우가 이러한 파일을 참조하는 경우 이들 파일은 중단되고 새 코드에 맞게 조정되어야 합니다.

## 영향을 받습니까? {#are-you-impacted}

인스턴스가 다음 중 하나에 대해 [!UICONTROL Web Analytics] 외부 계정을 사용하는 경우 영향을 받습니다.

* 이메일 캠페인 지표 및 속성을 지표로 Adobe Analytics에 전송.
* Adobe Analytics에 분류 데이터 보내기.
* 리마케팅 흐름(캠페인 후 전환된 연락처 식별).
* 처음으로 구성할 [!UICONTROL Web Analytics] 외부 계정입니다.

이 중 어떤 것이 당신에게 적용되는지 확실하지 않습니까? 인스턴스에서 활성화된 위의 기술 워크플로를 확인하고 [!UICONTROL Administration > Platform > External accounts]에서 [!UICONTROL Web Analytics] 외부 계정 구성을 검토하십시오([Web Analytics 외부 계정](../../installation/using/external-accounts.md#web-analytics-external-account) 참조).

## 마이그레이션 방법 {#how-to-migrate}

**Adobe이 호스팅하는** 인스턴스를 사용하는 경우 Adobe은 업그레이드의 일부로 SFTP 프로비저닝, IP 허용 목록 및 주요 구성을 처리합니다. 새 빌드가 라이브된 후에만 사용 사례를 확인해야 합니다.

**온-프레미스 또는 하이브리드** 배포에 있는 경우 다음 단계를 완료하세요.

1. [Adobe Analytics 2.0 변경 내용이 포함된 빌드로 Campaign 환경을 업그레이드](../../production/using/build-upgrade.md)합니다. [!UICONTROL Help > About...]에서 실행 중인 빌드를 확인할 수 있습니다([Campaign 버전을 확인하는 방법](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) 참조).
1. 다음 단계가 인스턴스에 따라 다르므로 위의 사용 사례 중 인스턴스에 적용되는 사례를 검토하십시오.
1. 리마케팅 흐름을 사용하는 경우 [!UICONTROL webAnalyticsFindConverted] 워크플로우에는 Adobe Analytics 2.0과 데이터를 교환하기 위한 전용 SFTP 채널이 필요합니다. 이를 다음과 같이 설정합니다. 그렇지 않으면 다음 단계로 건너뜁니다.
   1. 다른 외부 SFTP 통합에 적용해야 하는 것과 동일한 [SFTP 서버 모범 사례](../../platform/using/sftp-server-usage.md)를 따라 키 기반 인증을 사용하여 인스턴스에 SFTP 서버를 구축합니다. Adobe은 시작하는 데 도움이 되는 [샘플 SFTP 설정 스크립트](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html?package=/content/software-distribution/en/details.html/content/dam/campaign/public/setup_sftp.zip){target="_blank"}를 제공합니다.
   1. 새 빌드와 함께 제공된 스크립트를 실행하여 Adobe Analytics에서 해당 서버의 연결 세부 사항을 등록합니다.

      ```
      nlserver javascript -instance:<instance_name> -arg:host=<sftp_host_url>#user=<sftp_user> -file <path_to_the_file>/aaremarketingLocation.js
      ```

      예:

      ```
      nlserver javascript -instance:test_mkt_stage2 -arg:host=test-mkt-stage1.campaign.adobe.com#user=test -file ./nl6/datakit/nms/eng/js/aaremarketingLocation.js
      ```

   1. 리마케팅 내보내기는 고정된 Adobe IP 범위 집합에서만 시작되므로 SFTP 서버의 Adobe Analytics 허용 목록:
      * [현재 Adobe Analytics 데이터 수집 IP 주소를 검색하고](https://experienceleague.adobe.com/en/docs/core-services/interface/data-collection/ip-addresses){target="_blank"} SFTP 서버의 허용 목록에 추가하십시오. FTP 기반 Analytics 내보내기(데이터 피드 포함)는 런던, 오레곤 및 싱가포르 지역의 IPv4 주소에서만 시작됩니다.
      * [Adobe Analytics 공개 키를 검색](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-18141){target="_blank"}하고 SFTP 서버의 `authorized_keys` 파일에 추가하여 Analytics에서 인증할 수 있도록 합니다.
1. Campaign 탐색기 트리의 **[!UICONTROL Administration]> [!UICONTROL Platform] >[!UICONTROL Options]**&#x200B;에서 [!UICONTROL xtkOption]에 옵션의 `longvalue`을(를) `1`(으)로 만들거나 설정하여 인스턴스에서 `FEATUREFLAG_USE_ANALYTICS_20_API` 기능 플래그를 사용하도록 설정합니다. 위의 사용 사례가 사용자에게 적용되는 것과 상관없이 이 단계는 필수입니다.
1. 기존 연결을 종료하기 전에 인스턴스에 적용되는 각 사용 사례를 연습하여 마이그레이션을 확인합니다(테스트 캠페인을 보내고, 지표가 Analytics에 도착하는지 확인하고, 해당되는 경우 리마케팅 데이터를 확인).

## 새 웹 분석 외부 계정 설정 {#setting-up-a-new-web-analytics-external-account}

다음은 인스턴스가 Adobe에서 호스팅되는지 또는 온-프레미스/하이브리드인지에 적용됩니다.

기존 계정을 마이그레이션하지 않고 처음으로 [!UICONTROL Web Analytics] 외부 계정을 구성하는 경우 [외부 계정 설정 단계](../../installation/using/external-accounts.md#web-analytics-external-account) 및 [커넥터 시작 안내서](../../integrations/using/gs-aa.md)를 따르십시오.

Analytics 2.0에서는 새로운 분류 처리가 도입되었기 때문에 외부 계정에서 보고서 세트의 분류 데이터를 선택하려면 Adobe Analytics에서 분류 세트를 만들어야 합니다. 이는 새 단계입니다. 전환 변수 및 성공 이벤트를 구성한 후 Campaign에서 외부 계정을 구성하기 전에 만듭니다.

분류 세트를 만들려면:

1. [!DNL Adobe Analytics] 상단 메뉴 모음에서 **[!UICONTROL Components]** > **[!UICONTROL Classification sets]**&#x200B;을(를) 선택한 다음 **[!UICONTROL New]**&#x200B;을(를) 클릭합니다.

   ![](assets/analytics-classification-set-menu.png)

1. **[!UICONTROL Add New Classification Set]** 대화 상자에서:

   ![](assets/analytics-classification-set-dialog.png)

   * 분류 집합에 대한 **[!UICONTROL Name]**&#x200B;을(를) 입력하십시오.
   * **[!UICONTROL Type]**&#x200B;을(를) **[!UICONTROL Primary]**(으)로 설정합니다.
   * **[!UICONTROL Job notifications]**&#x200B;에서 분류 세트 작업의 성공 또는 실패에 대한 알림을 받을 사용자를 선택하고 해당 전자 메일 주소를 제공합니다.
   * **[!UICONTROL Subscriptions]**&#x200B;에서 이전 단계에서 내부 캠페인 이름에 대해 만든 보고서 세트와 전환 변수를 선택합니다.

1. **[!UICONTROL Save]**&#x200B;을(를) 클릭합니다.

이 분류 세트는 다음 단계에서 외부 계정을 구성할 때 Campaign에서 자동으로 검색됩니다. 분류 세트에 대한 자세한 내용은 [Adobe Analytics 설명서](https://experienceleague.adobe.com/en/docs/analytics/components/classifications/sets/create-set){target="_blank"}를 참조하세요.

## 도움이 필요하십니까? {#need-help}

마이그레이션하는 동안 문제가 발생하면 [Adobe 고객 지원 센터](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"}에 문의하십시오.
