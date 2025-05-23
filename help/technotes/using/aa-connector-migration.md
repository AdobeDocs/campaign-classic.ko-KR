---
product: campaign
title: Adobe Analytics 커넥터로 마이그레이션
description: Campaign - Analytics 커넥터 FAQ
feature: Technote, Analytics Integration
badge-v7-prem: label="온-프레미스/하이브리드만" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="v7 온-프레미스 및 하이브리드 배포에만 적용"
exl-id: 5bf61654-3d68-4560-a93f-7a768a2c5be4
hide: true
hidefromtoc: true
source-git-commit: a1dbef3e1feca1e3347de013db8bd7809d315016
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 2%

---

# 기존 Genesis 통합을 Adobe Analytics Connector로 마이그레이션하는 방법 {#acc-aa-faq}

Campaign Classic v7 21.1.3 릴리스부터 Adobe Analytics 데이터 커넥터는 사용 중단됩니다. [자세히 알아보기](https://experienceleague.adobe.com/docs/analytics/import/dataconnectors/data-connectors-eol.html?lang=ko)

2021년 8월 1일에 Adobe Campaign Classic이 기존 Data Connectors UI에서 제거되었지만 기존 Campaign 통합은 2022년 8월 17일까지 데이터를 계속 수집하여 Adobe Analytics에 전달합니다. 이 날짜 이후, 통합은 데이터를 수집하고 Adobe Analytics에 전달하는 것을 중단합니다.

기존 Adobe Analytics 통합을 대체하는 Adobe Exchange에서 새 Data Connectors Connector 통합을 **구현해야** 합니다. Adobe Analytics 커넥터에 대한 자세한 내용은 [이 페이지](../../integrations/using/gs-aa.md)를 참조하세요.

이러한 변경 사항에 대한 질문이 있으면 [FAQ](#faq-aa)를 읽어 보세요. 자세한 내용은 [고객 지원 Adobe](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)에 문의하십시오.

>[!NOTE]
>
>기존 Adobe Analytics 데이터 커넥터(이전의 Genesis 통합)에서 마이그레이션하고 Adobe Analytics에서 새 분류 아키텍처를 사용하는 경우 새 Adobe Analytics 커넥터로 마이그레이션하려면 7.3.1 또는 8.4.1부터 빌드 버전이 필요합니다.

## 변경 사항

이제 Campaign Classic v7과 Adobe Analytics 간의 새로운 통합을 사용할 수 있습니다. 주요 변경 사항은 아래에 나열되어 있습니다.

* Date 형식이어야 하는 **Contact Date** 분류는 Adobe Analytics에서 더 이상 사용되지 않습니다. 마이그레이션된 통합의 경우 여전히 동일한 유형으로 유지됩니다. Campaign에서 만든 **연락 날짜**&#x200B;의 유형은 **문자열**&#x200B;입니다.

* **처리 규칙**&#x200B;은(는) 새로운 통합의 일부로 Adobe Campaign에서 만듭니다. **처리 규칙**&#x200B;은(는) Adobe Analytics에서 수동으로 만들거나 클라이언트측 Javascript 구현을 직접 사용해야 합니다. **처리 규칙**&#x200B;은(는) 기존 통합에 그대로 유지됩니다.

* 기본 제공 기술 워크플로우와 그 동작은 동일하게 유지됩니다. 워크플로우에서 Adobe Analytics으로 데이터를 푸시/풀하기 위해 사용하는 백엔드 API만 변경되었습니다.

* 새 커넥터가 작동하려면 IMS 기술 계정 사용자로 `nlserver` 프로세스를 구성해야 합니다. 이 변경은 Adobe이 수행해야 합니다. 이를 구현하려면 [고객 지원 Adobe](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)에 문의하십시오.

* Adobe Analytics에서 데이터를 가져오고 푸시하기 위한 사용자 지정 워크플로우의 Adobe Genesis API였다면 이제 새로운 Adobe Analytics 1.4/2.0 API를 사용해야 합니다. [자세히 알아보기](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360047148832-Replacements-for-Data-Connector-API-calls)

## 영향을 받습니까?

기존 Adobe Analytics 데이터 커넥터(이전 이름: Genesis 통합)를 사용 중이며 통합이 Campaign 21.1.3보다 낮은 빌드에서 구현된 경우 영향을 받습니다.

이 섹션[&#128279;](../../integrations/using/launching-adobe-campaign.md#getting-your-campaign-version)에서 사용 중인 버전 을(를) 확인하는 방법을 알아보세요.

## 업데이트 방법

2022년 8월 17일 이전 **Campaign 21.1.3(또는 이상)으로 업그레이드해야 합니다**.

호스팅된 Adobe은 사용자와 함께 인스턴스를 최신 버전으로 업그레이드합니다. 그러면 [Adobe Analytics 커넥터](../../platform/using/gs-aa.md)를 사용할 수 있습니다.

온-프레미스/하이브리드 고객은 새 통합의 이점을 활용하려면 최신 버전 중 하나로 업그레이드해야 합니다.
모든 인스턴스가 업그레이드되면 [Adobe Analytics 커넥터에 새 통합을 구현](../../integrations/using/adobe-analytics-provisioning.md)하고 원활하게 전환할 수 있습니다.

## FAQ{#faq-aa}

**로그를 얻는 방법은 무엇입니까?**

사용자 인터페이스 구성 및 워크플로에 **verbose** 로깅이 적용됩니다.

상세 표시 모드에서는 Adobe Analytics에 대한 각 API 요청에 대해 요청 및 응답 헤더도 인쇄됩니다.

온-프레미스 사용자는 다음과 같이 세부 정보 표시 모드를 구현할 수 있습니다.

* 사용자 인터페이스에 자세한 정보 표시 모드를 사용하려면 자세한 정보 표시 모드로 `web` 프로세스를 다시 실행하십시오.
* **webAnalytics** 워크플로에 대한 세부 정보 표시 모드를 활성화하려면 워크플로 속성에서 **엔진에서 실행** 옵션을 선택한 다음 세부 정보 표시 모드에서 `wfserver`을(를) 다시 실행하십시오.

**관리자가 아닌 통합 소유자 오류는 무엇을 의미합니까?**

[이 페이지](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360035167932-Adobe-Analytics-Data-Connectors-Integration-Owner-Not-Admin-Error)에서 Data Connectors `Integration Owner Not Admin` 오류에 대해 자세히 알아보세요.

**새 커넥터로 마이그레이션이 완료되면 이전 데이터 및 보고서 세트가 어떻게 됩니까?**

마이그레이션 후 새 커넥터(이전 커넥터에서 마이그레이션됨)가 데이터를 동일한 보고서 세트에 푸시하기 시작하며 기존 데이터는 영향을 받지 않습니다. 기존 데이터에 추가됩니다.

**Analytics에 있는 일부 기존 evar/이벤트/보고서 세트가 Campaign에 표시되지 않습니다. 어떻게 해야 합니까?**

통합은 일상적인 작업을 위해 기술 계정 토큰의 데이터를 사용합니다. 기술 계정 사용자와 연결된 제품 프로필에서 차원/지표/보고서 세트에 대한 권한이 없는 경우 사용하는 API는 해당 요청에 대해 흔들릴 뿐입니다.

지표/차원/세그먼트/보고서 세트와 같은 Analytics 구성 요소에 대한 세부 정보를 읽는 경우, API는 결과에서 이러한 구성 요소를 반환하지 않습니다(Analytics 측에서 삭제된 것처럼 보이거나 존재하지 않음). Analytics API가 해당 요청을 거부하고 오류가 발생합니다.

해결 방법은 [Adobe Admin Console](https://adminconsole.adobe.com/){_blank}에서 이러한 구성 요소를 추가하여 기술 사용자 토큰의 Analytics 사용자 컨텍스트에서 **제품 프로필**&#x200B;을 새로 만들었거나 누락된 구성 요소로 업데이트하는 것입니다. 자세한 지침은 [고객 지원 Adobe](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)에 문의하십시오.

## 유용한 링크

* [환경 업그레이드](../../production/using/build-upgrade.md)
* [빌드 업그레이드 FAQ](../../platform/using/faq-build-upgrade.md)
* [Campaign Classic 빌드 다운로드](https://experience.adobe.com/#/downloads/content/software-distribution/ko/campaign.html)
* [사용자가 새 클라이언트 콘솔을 사용할 수 있도록 설정](../../installation/using/client-console-availability-for-windows.md)
* [Campaign 클라이언트 콘솔 설치](../../installation/using/installing-the-client-console.md)
