---
product: campaign
title: Adobe Analytics 커넥터로 마이그레이션
description: Campaign - Analytics 커넥터 FAQ
hide: true
hidefromtoc: true
source-git-commit: 248bd7774c01adb44ce33d0499c2b01d013e75bd
workflow-type: tm+mt
source-wordcount: '757'
ht-degree: 6%

---

# Adobe Analytics Connector로 마이그레이션하는 방법 {#acc-aa-faq}

Campaign Classic v7 21.1.3 릴리스부터 Adobe Analytics 데이터 커넥터는 사용되지 않습니다. [자세히 알아보기](https://experienceleague.adobe.com/docs/analytics/import/dataconnectors/data-connectors-eol.html)

2021년 8월 1일부터 Adobe Campaign Classic은 기존 Data Connectors UI에서 제거되지만, 기존 Campaign 통합은 2022년 3월 1일까지 데이터를 수집하여 Adobe Analytics으로 계속 전달합니다. 2022년 3월 1일에 통합은 데이터 수집 및 Adobe Analytics에 전달을 중단합니다.

[이 페이지](../platform/using/adobe-analytics-connector.md)에 자세히 설명된 대로 레거시 Data Connectors 통합을 대체하는 Adobe Exchange에서 새 Adobe Analytics 커넥터 통합으로 마이그레이션해야 합니다.


>[!NOTE]
>
>이러한 변경 사항에 대한 질문이 있으면 [Adobe 고객 지원 센터](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)에 문의하십시오.


## 변경 사항

이제 Campaign Classic과 Adobe Analytics 간의 새로운 통합을 사용할 수 있습니다. 주요 변경 사항은 아래에 나와 있습니다.

* Adobe Campaign Classic과 Adobe Analytics 인증 간의 통합이 사용자/암호에서 IMS(Adobe Identity Management Service)로 이동되었습니다. 따라서 Analytics 커넥터 구현을 시작하기 전에 Adobe IMS를 구현하고 Adobe ID](../integrations/using/about-adobe-id.md)을 통해 Campaign [에 연결해야 합니다.

* 날짜 유형에서 사용하는 **연락처 날짜** 분류가 Adobe Analytics에서 더 이상 사용되지 않습니다. 마이그레이션된 통합의 경우 여전히 동일한 유형으로 유지됩니다. Campaign에서 만든 **연락처 날짜**&#x200B;의 경우 유형은 **String**&#x200B;입니다.

* **처리** 규칙은 새로운 통합의 일부로 Adobe Campaign에서 만듭니다. **처리 규칙**&#x200B;은 Adobe Analytics에서 수동으로 만들거나 클라이언트측 Javascript 구현을 직접 사용해야 합니다. **처리** 규칙은 기존 통합에 대해 그대로 유지됩니다.

* 내장된 기술 워크플로우와 그 동작은 동일하게 유지됩니다. 워크플로우에서 Adobe Analytics과 데이터를 푸시/가져오는 데 사용하는 백엔드 API만 변경되었습니다.

* 새 커넥터가 작동하려면 `nlserver` 프로세스를 IMS 기술 계정 사용자로 구성해야 합니다. 이 변경은 Adobe에서 수행해야 합니다. 이 기능을 구현하려면 고객 지원 센터 Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)에 문의하십시오.[

* Adobe Analytics에서 데이터를 가져오고 푸시하는 사용자 지정 워크플로우에서 Adobe Genesis API를 사용하는 경우 이제 새로운 Adobe Analytics 1.4/2.0 API를 사용해야 합니다. [자세히 알아보기](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360047148832-Replacements-for-Data-Connector-API-calls)

## 영향을 받습니까?

기존 Adobe Analytics 데이터 커넥터(이전에 Genesis 통합이라고 함)를 사용하고 통합이 Campaign 21.1.3보다 낮은 빌드에 구현된 경우 영향을 받습니다.

이 섹션](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)에서 버전 [을 확인하는 방법을 알아봅니다.

## 업데이트 방법

2022년 3월 1일 전에 Campaign 21.1.3(또는 이상) **으로 업그레이드해야 합니다**.

호스팅된 고객인 Adobe은 인스턴스와 최신 버전으로 업그레이드하도록 사용자와 협력하고 있습니다.

온-프레미스/하이브리드 고객은 새 통합을 활용하려면 최신 버전 중 하나로 업그레이드해야 합니다.

모든 인스턴스가 업그레이드되면 [새 통합](../platform/using/adobe-analytics-connector.md)을 Adobe Analytics Connector로 구현하고 원활하게 전환할 수 있습니다.


## FAQ

**로그를 가져오려면 어떻게 해야 합니까?**

사용자 인터페이스 구성 및 워크플로우에는 **세부 정보** 로깅이 제공됩니다.

세부 정보 표시 모드에서는 Adobe Analytics에 대한 각 API 요청에 대해 요청 및 응답 헤더도 인쇄됩니다.

온-프레미스 사용자는 다음과 같이 세부 정보 모드 를 구현할 수 있습니다.

* 사용자 인터페이스에 대한 세부 사항 모드를 활성화하려면세부 정보 표시 모드에서 `web` 프로세스를 다시 실행합니다.
* **webAnalytics** 워크플로우에 대한 세부 정보 표시 모드를 활성화하려면워크플로우 속성에서 **엔진에서 실행** 옵션을 선택하고 세부 정보 표시 모드로 `wfserver`를 다시 실행합니다.

**통합 소유자가 관리자가 아님**

[이 페이지](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360035167932-Adobe-Analytics-Data-Connectors-Integration-Owner-Not-Admin-Error)에 있는 Data Connectors &quot;Integration Owner Not Admin&quot; 오류에 대해 자세히 알아보십시오.

**분석에 있는 기존 evar/events/reportsuite가 Campaign에 표시되지 않습니다.**

통합은 일상적인 작업을 위해 기술 계정 토큰에 있는 데이터를 사용합니다. 기술 계정 사용자와 연결된 제품 프로필에서 차원/지표/보고서 세트에 대한 권한이 없는 경우 Adobe에서 사용하는 API는 해당 요청에 대해 단지 실패합니다.

Analytics 구성 요소의 세부 사항을 읽는 경우(지표/차원/세그먼트/보고서 세트 등) API는 결과에 이러한 구성 요소를 반환하지 않습니다(Analytics 측에서 삭제되었거나 존재하지 않을 수 있음). Analytics API는 이러한 요청 및 오류를 거부합니다.

이 솔루션은 [Adobe Admin Console](https://adminconsole.adobe.com/)에 이러한 구성 요소를 추가하여 기술 사용자 토큰의 Analytics 사용자 컨텍스트에서 제품 프로필을 새로 만들거나 누락된 구성 요소로 업데이트하는 것입니다.

## 유용한 링크

* [환경 업그레이드](../production/using/build-upgrade.md)
* [빌드 업그레이드 FAQ](../platform/using/faq-build-upgrade.md)
* [Campaign Classic 빌드 다운로드](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [새 클라이언트 콘솔을 사용자가 사용할 수 있게 만들기](../installation/using/client-console-availability-for-windows.md)
* [Campaign 클라이언트 콘솔 설치](../installation/using/installing-the-client-console.md)
