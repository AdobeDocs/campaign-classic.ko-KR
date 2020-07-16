---
title: Adobe Campaign Classic 설명서 업데이트
description: 이 페이지에는 Adobe Campaign Classic의 각 릴리스에 대한 모든 새로운 기능과 설명서 업데이트가 나열됩니다.
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 64b31b8d4f88023f4285bf161d236973a7d63107
workflow-type: tm+mt
source-wordcount: '6939'
ht-degree: 8%

---


# 설명서 업데이트 정보{#documentation-updates}

이 페이지에는 월별 및 Campaign 릴리스의 모든 새로운 기능과 설명서 업데이트가 나열됩니다.

또한 [Adobe Campaign Classic 릴리스 정보에서 더 많은 업데이트를](../../rn/using/latest-release.md) 확인할 수 있습니다.

## 2020년 7월 {#july-2020}

릴리스 [노트가](../../rn/using/latest-release.md) 재구성되었습니다. 빌드 상태, 업그레이드 프로세스, 권장 사항 및 중요 링크에 대한 정보가 포함된 [개요 페이지가](../../rn/using/latest-release.md) 추가되었습니다. Gold [Standard 릴리스에](../../rn/using/gold-standard.md) 대한 전용 페이지가 추가되었으며 [호환성 매트릭스가](../../rn/using/compatibility-matrix.md) 통합되었습니다.

Campaign Classic 모니터링과 관련된 지침과 함께 새 섹션이 추가되었습니다. [자세한 내용](../../production/using/monitoring-guidelines.md)

개인정보 보호 및 동의 섹션은 보다 자세한 정보와 유용한 링크로 개선되었습니다. [자세한 내용](../../platform/using/privacy-and-recommendations.md)

Campaign Classic의 개인 정보 관리 페이지가 자동 개인 정보 요청 프로세스를 설정할 수 있는 API를 사용할 때 사용 가능한 &#39;규제&#39; 필드에 대한 정보로 업데이트되었습니다. [자세한 내용](https://helpx.adobe.com/ie/campaign/kb/acc-privacy.html#ManagingPrivacyRequests)

개인 정보 관리 개요 페이지는 태국 개인정보 보호법(Personal Data Protection Act)(PDPA) 및 브라질 레이제랄 데 프로테카앙 데 도도스(LGPD)에 대한 정보를 포함하도록 업데이트되었습니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/campaign-privacy-overview.html#whatisgdpr)

하위 워크플로우 로그 및 오류 발생 시 동작에 정보가 추가되었습니다. [자세한 내용](../../workflow/using/sub-workflow.md)

작업 섹션에 우수 사례가 **[!UICONTROL Scheduler]** 추가되었습니다. [자세한 내용](../../workflow/using/scheduler.md)

## 2020년 6월 {#june-2020}

격리된 주소 제거 섹션이 업데이트되었습니다. 여기에는 격리 목록에서 주소가 자동으로 제거되는 경우가 포함됩니다. [자세한 내용](../../delivery/using/understanding-quarantine-management.md#removing-a-quarantined-address)

Campaign 컨트롤 패널 및 캠페인 워크플로우를 사용하여 데이터를 [암호화하고](../../workflow/using/how-to-use-workflow-data.md#use-case-gpg-encrypt) [해독하는](../../workflow/using/importing-data.md#use-case-gpg-decrypt) 방법에 사용 사례가 추가되었습니다.

&#39;화이트 리스트&#39;와 &#39;블랙 리스트&#39; 용어 모두 Adobe Campaign 문서에서 제거되었습니다. 이러한 용어의 일부 항목은 여전히 제품 UI, 옵션 이름 및 내부 코드에 존재할 수 있지만, 향후 캠페인 릴리스에서 &#39;차단 목록&#39; 과 &#39;허용 목록으로 대체될 것입니다.

Experience Cloud 트리거 및 Adobe Campaign Classic 통합 페이지가 [여기로 이동되었습니다](../../integrations/using/about-triggers.md).

## 20.2 - 08/06/2020{#release-20-2}

**릴리스에 포함된 새로운 기능**

이모티콘 지원 - [자세한 내용](../../delivery/using/customizing-emoticon-list.md)

Azure Synapse FDA 커넥터 - [자세한 내용](../../platform/using/specific-configuration-database.md#configure-access-to-azure-synapse)

태국 및 브라질 개인정보 보호 법 - [자세한 내용](https://helpx.adobe.com/campaign/kb/acc-privacy.html#ManagingPrivacyRequests)

**릴리스와 함께 제공되는 기타 설명서 업데이트**

트랜잭션 메시지 템플릿의 게시를 취소할 수 있는 새 옵션이 이 섹션에[설명되어 있습니다](../../message-center/using/template-unpublication.md).

개인화된 URL과 첨부 파일에서 다운로드한 이미지가 포함된 이메일을 보낼 때 제한을 설정할 수 있는 새로운 옵션이 Campaign Classic 옵션 목록에 추가되었습니다. [자세한 내용](../../installation/using/configuring-campaign-options.md#delivery)

데이터베이스의 **배달 부분 준비** 옵션은 [이 섹션에 설명되어 있습니다](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis).

배달 유효성 확인 섹션이 명확하고 업데이트되었습니다. [자세한 내용](../../delivery/using/steps-validating-the-delivery.md)

새로운 추적 링크 서명 메커니즘과 관련된 매개 변수가 [서버 구성 파일](../../installation/using/the-server-configuration-file.md) 섹션에 추가되었습니다.

호환성 매트릭스가 업데이트되었습니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

정리 워크플로우 섹션이 업데이트되었습니다. [자세한 내용](../../production/using/database-cleanup-workflow.md)

캠페인 네트워크 끝점이 이 [섹션으로 이동되었습니다](../../installation/using/campaign-network-endpoints.md).

스팸 암살자 설치 섹션이 새 설치 파일 이름으로 업데이트되었습니다. [자세한 내용](../../installation/using/configuring-spamassassin.md#installing-spamassassin)

중복 환경에 대한 섹션이 업데이트되었습니다. [자세한 내용](../../production/using/duplicating-environments.md#step-2---export-the-target-environment-configuration--dev-)

## 2020년 5월 {#may-2020}

모니터링 배달 기능 섹션이 이동되고 개선되었습니다. [자세한 내용](../../delivery/using/monitoring-deliverability.md)

전달 능력 문제 해결 섹션이 이동되고 개선되었습니다. [자세한 내용](../../delivery/using/deliverability-faq.md)

새 플랫폼 섹션을 시작할 때의 전달 가능성 가이드라인이 개선되었습니다. [자세한 내용](../../delivery/using/starting-new-platform.md)

첨부 파일이 있는 트랜잭션 이메일 전송 섹션이 이동 및 업데이트되었습니다. [자세한 내용](../../message-center/using/transactional-email-with-attachments.md)

데이터 패키지 우수 사례 섹션이 이동 및 업데이트되었습니다. [자세한 내용](../../platform/using/working-with-data-packages.md#data-package-best-practices)

## 2020년 4월 {#april-2020}

FDA 권한 테이블이 외부 데이터베이스 액세스(FDA) 문서로 이동되었습니다. [자세한 내용](../../platform/using/remote-database-access-rights.md)

FAQ는 소프트 및 하드 캐시를 삭제하는 방법에 대한 팁으로 업데이트되었습니다. [자세한 내용](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear)

색인에 대한 추가 정보를 통해 데이터 모델 모범 사례를 개선했습니다. [자세한 내용](../../configuration/using/data-model-best-practices.md#indexes)

Adobe Campaign 내장 데이터 모델을 설명하는 섹션이 각 표에 대한 자세한 내용으로 업데이트되었습니다. [자세한 내용](../../configuration/using/data-model-description.md)

워크플로우 사용 사례는 주제별로 업데이트되고 재구성되었습니다. [자세한 내용](../../workflow/using/about-workflow-use-cases.md)

바운스 [메일 자격](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification) 및 [이메일 관리 규칙](../../delivery/using/understanding-delivery-failures.md#email-management-rules) 섹션이 업데이트된 정보로 향상되었습니다.

Adobe Campaign 향상된 MTA 아티클이 업데이트되었습니다. 이제 Campaign Classic에만 적용됩니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/acc-campaign-enhanced-mta.html)

## 2020년 3월 {#march-2020}

데이터 모델 우수 사례는 시퀀스, [성능](../../configuration/using/data-model-best-practices.md#sequences)및 [큰 표](../../configuration/using/data-model-best-practices.md#performance) 등 [의 새로운 섹션으로](../../configuration/using/data-model-best-practices.md#large-tables)업데이트되었습니다. [자세한 내용](../../configuration/using/data-model-best-practices.md)

이제 Adobe Campaign 내장 데이터 모델과 테이블 간의 상호 작용을 설명하는 새 섹션을 사용할 수 있습니다. [자세한 내용](../../configuration/using/data-model-description.md)

설명서 홈 페이지에 추가 키 링크가 추가되었습니다. [자세한 내용](../../campaign-classic-home.md)

Adobe Target의 동적 오퍼를 Adobe Campaign의 이메일에 통합하는 방법에 대한 사용 사례가 추가되었습니다. [자세한 내용](../../integrations/using/inserting-a-dynamic-image.md)

이제 Adobe Campaign에서 사용할 수 있는 다양한 언어를 설명하는 새 섹션을 사용할 수 있습니다. [자세한 내용](../../platform/using/adobe-campaign-workspace.md#languages)

지정된 권한에 대한 추가 정보가 있는 액세스 관리 가이드라인이 업데이트되었습니다. [자세한 내용](../../platform/using/access-management.md#named-rights)

## 2020년 2월 {#february-2020}

Adobe Campaign 데이터 모델을 디자인하는 동안 모범 사례와 주요 권장 사항에 대한 개요를 제공하는 새로운 섹션을 사용할 수 있습니다. [자세한 내용](../../configuration/using/data-model-best-practices.md)

기술 이메일 구성에 대한 새 섹션이 제공됩니다. [자세한 내용](../../installation/using/email-deliverability.md)

&quot;할당량이 충족됨&quot; 오류 메시지에 대한 자세한 내용이 포함된 제공 기능 FAQ가 업데이트되었습니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/acc-deliverability-faq.html#FAQ)

AMP for Email은 이제 새로운 이메일 제공업체에서 지원합니다. 관련 문서가 업데이트되었습니다. [자세한 내용](../../delivery/using/defining-interactive-content.md)

이메일 보관 섹션이 향상되었습니다. [자세한 내용](../../installation/using/email-archiving.md#recommendations-and-limitations)

## 20.1 - 17/02/2020{#release-20-1}

**릴리스에 포함된 새로운 기능**

Snowflake FDA 커넥터 - [자세한 내용](../../platform/using/specific-configuration-database.md#configure-access-to-snowflake)

Hadoop FDA 커넥터 개선 사항 - [자세한 내용](../../platform/using/specific-configuration-database.md#configure-access-to-hadoop-3)

**릴리스와 함께 제공되는 기타 설명서 업데이트**

설치 [,](../../installation/using/before-reading.md)프로덕션 [및](../../production/using/foreword.md) 구성 [가이드는 nlserver 서비스 시작 시 사용하는 새 시스템 단위로 업데이트되었습니다](../../configuration/using/additional-parameters.md) . 여전히 /etc/init.d/nlserver6를 사용할 수 있지만, 이제 nlserver 서비스와 상호 작용하기 위해 systemctl 명령을 사용하는 것이 좋습니다.

설치 가이드가 업데이트 및 최신 버전의 호환성 매트릭스와 동기화되었습니다. 지원되는 새 시스템이 추가되었습니다. 사용되지 않는 시스템 및 지원되지 않는 시스템에 대한 항목이 제거되었습니다. [자세한 내용](../../installation/using/before-reading.md)

호환성 매트릭스가 Hadoop 3.0 및 Snowflake FDA 커넥터로 업데이트되었습니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

설치 안내서에 IP 친화성에 대한 우수 사례가 추가되었습니다. [자세한 내용](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

데이터베이스 정리 워크플로 섹션이 업데이트되었습니다. 이제 제공된 배치 숫자가 코드 구현을 반영합니다. [자세한 내용](../../production/using/database-cleanup-workflow.md)

HTTP를 통한 FDA에 대한 제한이 트랜잭션 메시지 안내서에 추가되었습니다. [자세한 내용](../../production/using/database-cleanup-workflow.md)

새 옵션에 시간 초과 기간을 정의할 수 있는 정보가 **[!UICONTROL JavaScript code]** 추가되었습니다. 이 경우 **[!UICONTROL Advanced JavaScript code]** 및워크플로우 활동을 위한 기간이 사용됩니다. [자세한 내용](../../workflow/using/sql-code-and-javascript-code.md)

> > 노드 **[!UICONTROL Start Pending]** 에서 사용할 수 있는 새 **[!UICONTROL Administration]** 보기에 정보가 **[!UICONTROL Audit]** **[!UICONTROL Workflows Status]** 추가되었습니다. [자세한 내용](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

푸시 알림 [전송](../../delivery/using/about-mobile-app-channel.md) 안내서가 이동, 재구성 및 명확해진 정보로 개선되었습니다.

URL 보고서 구성에 대한 새 매개 변수가 [여기에 설명되어 있습니다](../../reporting/using/properties-of-the-report.md#defining-additional-settings).

온-프레미스 및 **호스팅 기능 매트릭스** 페이지가 새로운 FDA 커넥터로 업데이트되었습니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html)

Campaign Classic **기능 매트릭스** 페이지가 업데이트되었습니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

새 **[!UICONTROL Cleanup of Nmsaddress]** 워크플로우는 [여기에](../../production/using/database-cleanup-workflow.md#cleanup-of-nmsaddress)문서화되었습니다.

워크플로우에서 쿼리 활동을 사용할 때 제한이 추가되었습니다. [자세한 내용](../../workflow/using/query.md)

소프트 오류가 발생하는 경우 격리할 주소를 보내기 위해 향상된 이메일 주소 유효성 검사 규칙을 자세히 설명하는 새 섹션이 추가되었습니다. [자세한 내용](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

인스턴스가 향상된 MTA를 사용 중임을 나타내는 구성 파일의 매개 변수 [자세한 내용](../../installation/using/the-server-configuration-file.md#mta)

## 2020년 1월 {#january-2020}

제공 능력 섹션이 업데이트된 컨텐츠로 이동, 재구성 및 향상되었습니다. [자세한 내용](../../delivery/using/about-deliverability.md)

이제 Adobe Campaign Classic 데이터 모델의 기본 사항과 각 테이블의 설명에 액세스하는 방법을 설명하는 새 섹션을 사용할 수 있습니다. [자세한 내용](../../configuration/using/about-data-model.md)

모든 메시지에 필요한 향상된 MTA 헤더를 추가하지 않는 인스턴스에 특정 Typical 패키지를 설치하는 방법에 대한 자세한 정보가 포함된 Adobe Campaign Enhanced MTA 아티클이 업데이트되었습니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/acc-campaign-enhanced-mta.html#impacts)

쿼리 디자인과 관련된 사용 사례가 별도의 섹션으로 재구성되었습니다. [자세한 내용](../../workflow/using/querying-recipient-table.md)

이제 Adobe Campaign Classic에서 오퍼 관리 및 상호 작용 모듈 사용에 대한 팁과 트릭에 대한 새 섹션을 사용할 수 있습니다. [자세한 내용](../../interaction/using/interaction-best-practices.md#tips-managing-offers)

상호 작용 설명서는 오퍼를 보다 효율적으로 관리하는 방법을 이해하는 데 도움이 되는 여러 비디오에 대한 링크로 보강되었습니다. [자세한 내용](../../interaction/using/interaction-and-offer-management.md)

인스턴스에서 실행되는 쿼리를 최적화하는 방법에 대한 우수 사례 문서가 설명서에 통합되었습니다. [자세한 내용](../../workflow/using/query.md#optimizing-queries)

보고 가이드가 업데이트되고 재구성되었습니다. [자세한 내용](../../reporting/using/about-adobe-campaign-reporting-tools.md)

워크플로우에서 인스턴스 변수를 사용하는 방법의 예가 추가되었습니다. [자세한 내용](../../workflow/using/javascript-scripts-and-templates.md)

## 2019년 12월 {#december-2019}

&quot;WdbcOptions_TempDbName&quot; 옵션이 캠페인 옵션 목록에 추가되었습니다. [자세한 내용](../../installation/using/configuring-campaign-options.md)

FDA 매트릭스 페이지가 [여기에](../../platform/using/remote-database-access-rights.md)옮겨졌습니다

액세스 권한 지표 페이지가 [여기에](https://docs.adobe.com/content/help/en/campaign-classic/using/getting-started/administration-basics/assets/accessrights.pdf)이동되었습니다.

AMP를 사용하여 대화형 내용을 정의하는 방법을 설명하는 섹션이 이동되었습니다. [자세한 내용](../../delivery/using/defining-interactive-content.md)

## 19.2 - 02/12/2019{#release-19-2}

**릴리스에 포함된 새로운 기능**

CPA(California Consumer Privacy Act) - [자세한 내용](https://helpx.adobe.com/campaign/kb/acc-privacy.html)

AMP를 사용한 인터랙티브한 컨텐츠 - [자세한 내용](../../delivery/using/defining-interactive-content.md)

워크플로우 라이브 모니터링 - [자세한 내용](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

TLS(안전한 SMS 메시지) - [자세한 내용](https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html)

**릴리스와 함께 제공되는 기타 설명서 업데이트**

Adobe Campaign 향상된 MTA 설명서를 사용할 수 있습니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/acc-campaign-enhanced-mta.html)

캠페인 내의 &quot;가능한 한 빨리 시작&quot; 상태에 있는 워크플로우 문제 해결 방법에 대한 새 섹션이 추가되었습니다. [Read more](../../production/using/workflow-execution.md#start-as-soon-as-possible-in-campaigns)

새로운 &quot;NmsOperation_DeliveryPreparationWindow&quot; 및 &quot;WdbcKillSessionPolicy&quot; 옵션이 캠페인 옵션 목록에 추가되었습니다. [자세한 내용](../../installation/using/configuring-campaign-options.md)

이제 Adobe Campaign Classic 데이터 모델의 기본 사항을 설명하는 새 문서를 사용할 수 있습니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/acc-datamodel.html)

전달 속성의 새로운 **최대 개인화 실행 시간** 옵션이 이 [섹션에 설명되어 있습니다](../../delivery/using/personalization-fields.md#timing-out-personalization).

logon() 및 query()와 함께 **HttpServletRequest** 를 사용하는 API 호출에 대한 예가 업데이트되었습니다. [자세한 내용](../../configuration/using/web-service-calls.md)

스키마 정의에 **sqlDefault** 특성에 대한 권장 사항이 추가되었습니다. [자세한 내용](../../configuration/using/elements-and-attributes.md#attribute-description)

Adobe Campaign과 Adobe 실시간 고객 데이터 Platform 간의 통합이 이제 Adobe Experience Cloud와 통합 **안내서에서** 참조됩니다. [자세한 내용](../../integrations/using/about-campaign-integrations.md)

## 2019년 11월 {#november-2019}

중간 소싱 서버 [및](../../installation/using/mid-sourcing-server.md#multiplexing-the-mid-sourcing-server) 여러 제어 인스턴스 [](../../message-center/using/transactional-messaging-architecture.md#supporting-several-control-instances) 지원 섹션에 이러한 배포가 완전 호스팅 및 하이브리드 클라이언트에 대해 지원되지 않는다는 내용의 경고가 추가되었습니다.

이메일을 보낼 때 사용되는 문자 인코딩을 강제 적용하는 방법을 설명하는 새 섹션이 추가되었습니다. [자세한 내용](../../delivery/using/sending-messages.md#character-encoding)

액세스 관리 섹션이 개인 정보 **데이터 권한으로 업데이트되었습니다**. [자세한 내용](../../platform/using/access-management.md#named-rights)

개인화 필드 컨텐츠가 1024자를 초과할 수 없음을 지정하는 정보가 추가되었습니다. [자세한 내용](../../delivery/using/personalization-fields.md)

Campaign 컨트롤 패널 문서는 새로운 공동 문서 세트에 통합되었습니다. [자세한 내용](https://docs.adobe.com/content/help/ko-KR/control-panel/using/control-panel-home.html)

배포 우수 사례 시작 안내서가 업데이트되었습니다. [자세한 내용](https://helpx.adobe.com/kr/campaign/kb/delivery-best-practices.html)

## 2019년 10월 {#october-2019}

Campaign Standard 및 Campaign Classic에 대한 오류 메시지 목록이 업데이트되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

GDPR 시작 가이드가 향상되어 더욱 풍부해졌습니다. 이제 GDPR 및 CPA를 비롯한 개인 정보 관리 문서입니다. [자세한 내용](https://helpx.adobe.com/content/help/en/campaign/kb/campaign-privacy.html)

Campaign Classic에서 추적을 위해 새로운 문제 해결 페이지가 추가되었습니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/classic-tracking-troubleshooting.html)

Adobe Analytics 데이터 커넥터에 대한 새 우수 사례 페이지가 추가되었습니다. [Adobe Analytics 데이터 커넥터에 대한 자세한 내용](../../platform/using/adobe-analytics-data-connector.md)

게재 모범 사례 시작 안내서가 이동 및 업데이트되었습니다. [자세한 내용](https://helpx.adobe.com/kr/campaign/kb/delivery-best-practices.html)

동일한 공급자 계정의 확장 일반 SMPP 커넥터를 사용하는 여러 외부 계정을 사용하는 경우 발생하는 문제를 방지하기 위해 SMS 채널 문서에 권장 사항이 추가되었습니다. [자세한 내용](../../delivery/using/sms-channel.md#automatic-reply)

워크플로우의 동시 실행을 방지하는 방법에 대한 정보가 스케줄러 활동 문서에 추가되었습니다. [자세한 내용](../../workflow/using/scheduler.md)

온-프레미스 설치에 대한 받은 편지함 렌더링을 구성하는 단계가 설명서에 추가되었습니다. [자세한 내용](../../delivery/using/inbox-rendering.md#activating-inbox-rendering)

## 2019년 9월 {#september-2019}

Campaign Classic 유지를 위한 일반적인 지침을 제공하기 위해 새 페이지가 추가되었습니다. [자세한 내용](../../production/using/monitoring-guidelines.md)

워크플로우 모니터링과 관련된 정보는 새로운 전용 섹션에 중앙 집중화되었습니다. [자세한 내용](../../workflow/using/monitoring-workflow-execution.md)

Adobe Campaign Classic에서 추적을 위한 일반 지침에 대한 새 페이지가 추가되었습니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/acc-tracking.html)

워크플로우 및 게재 성능 향상에 대한 우수 사례가 업데이트되었습니다. [게재에 대한 자세한 내용](../../workflow/using/workflow-best-practices.md) 및 [자세한 내용을 살펴볼 수 있습니다](../../delivery/using/monitoring-a-delivery.md#best-practices-performance).

## 19.1 - 30/05/2019{#release-19-1}

**릴리스에 포함된 새로운 기능**

Campaign 컨트롤 패널 - [자세한 내용 보기](https://docs.adobe.com/content/help/ko-KR/control-panel/using/control-panel-home.html)

감사 추적 - [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Audit_trail.html)

**릴리스와 함께 제공되는 기타 설명서 업데이트**

새로운 빌드 업그레이드 FAQ가 생성되었습니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/build-upgrade-faq.html)

호환성 [매트릭스가](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) 업데이트되었습니다. 지원되는 데이터베이스 시스템 목록은 Android/iOS 버전 및 관련 SDK뿐만 아니라 업데이트되었습니다. The [19.0 Compatibility matrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix-19-0.html) has been archived.

&#39;Campaign Classic에서 더 이상 사용되지 않음 및 제거된 기능&#39; 페이지가 업데이트되었습니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

서버 구성 파일에 대한 설명이 설치 안내서에 추가되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_The_server_configuration_file.html)

호스팅 및 하이브리드 모델의 설치 및 구성 단계를 설명하는 섹션이 추가되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/INS_Hybrid_and_Hosted_models_Introduction.html)

캠페인 서버 제거 단계를 설명하는 섹션이 추가되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Uninstalling_Campaign.html)

보안 [,](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html)전달 [](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) 능력 [및](https://helpx.adobe.com/campaign/kb/acc-privacy.html) 개인 정보가처음 시작하는 안내서가 업데이트되었습니다.

제품 변경 사항을 반영하도록 프로세스 전 워크플로우 옵션에 대한 설명이 업데이트되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Action_activities.html#Data_loading__file_)

Marketing Cloud 트리거 기술 정보가 업데이트되었습니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html)

오류 메시지 목록이 업데이트되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

트랜잭션 메시징을 위한 SOAP 인증 방법에 대한 자세한 내용을 추가했습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/MCE_Introduction_Event_description.html)

Apache 구성 단계가 업데이트되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/INS_Installing_Campaign_in_Linux__Integration_into_a_Web_server.html#Configuring_Apache_web_server_in_RHEL)

Campaign Standard 및 Classic의 끝점 목록을 포함하여 새 페이지가 추가되었습니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/campaign-endpoints.html)

데이터 패키지 우수 사례 아티클이 업데이트되었습니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/data-package-best-practices.html)

오퍼 관리 설명서가 우수 사례를 나열하는 새 섹션으로 업데이트되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/ITA_Interaction_Overview_Interaction_best_practices.html)

Adobe Campaign Classic에서 오퍼 카탈로그를 사용하는 방법에 대한 새 기술 자료 문서가 만들어졌습니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/offer-best-practices.html)

사용 예로 하위 워크플로우 활동 섹션이 향상되었습니다. [자세한 내용](../../workflow/using/sub-workflow.md)

온-프레미스 및 호스팅 기능 매트릭스 [](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html) 기술 자료 문서가 이메일 보관 관련 정보로 업데이트되었습니다.

템플릿 게시에 대한 메모로 트랜잭션 메시징 설명서를 업데이트했습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/MCE_Template_publication.html)

처리되지 않은 바운스 메일 섹션이 오류 필드에 대한 전달 주소 및 주소에 대한 자세한 정보로 업데이트되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/INS_Initial_configuration_Deploying_an_instance.html#Unprocessed_bounce_mails)

워크플로우 계획 우수 사례에 대한 새 섹션이 추가되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Workflow_best_practices.html#Execution_and_performance)

캠페인 옵션 목록에 두 개의 새 옵션이 추가되었습니다. XtkSecurity_Restrict_EditXML 및 NmsOperation_OperationMgtDebug입니다.
[자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Configuring_Campaign_options.html)

Campaign Classic에서 사용할 수 있는 다른 외부 계정 및 이를 구성하는 방법에 대한 정보가 추가되었습니다.
[자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_External_accounts.html)

인터페이스 변경 사항을 반영하도록 Analytics 데이터 커넥터 섹션이 업데이트되었습니다.
[자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Adobe_Analytics_Data_Connector.html)

청구 보고서에 정보가 추가되었습니다.
[자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#Billing_report)

공유 대상 통합에 대한 설명서를 업데이트했습니다.
[자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Configuring_shared_audiences_integration_in_Adobe_Campaign.html)

다음 기술 정보가 업데이트되었습니다. [SMS 커넥터 프로토콜 및 설정](https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html) 및 [시퀀스 자동 생성](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence).

기술 워크플로우 섹션이 업데이트되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/WKF_Technical_workflows_About_technical_workflows.html)

캠페인 도메인 이름 설정 절차가 개선되고 업데이트되었습니다. [자세한 내용](https://helpx.adobe.com/kr/campaign/kb/domain-name-delegation.html)

GCM(Google Cloud Messaging)에서 Firebase Cloud Messaging(FCM)으로의 Android 앱에 대한 마이그레이션 절차가 업데이트되었습니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/migrate-to-fcm.html)

캠페인 하드웨어 크기 조정 안내서가 업데이트되었습니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/hardware-sizing-guide.html)

Teradata 외부 계정에 대한 쿼리 배너에 정보가 추가되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_External_accounts.html#External_database_external_account)

## 2019년 1월{#release-doc-16-01-2019}

Marketing Cloud 트리거 기술 정보가 업데이트되었습니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html)

오퍼 승인 섹션에 &quot;승인된 컨텐츠&quot; 언급에 모든 오퍼가 활성화/승인되었는지 여부에 상관없이 컨텐츠 승인 프로세스가 달성되었음을 나타내는 메모가 추가되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/ITA_Managing_an_offer_catalog_Approving_and_activating_an_offer.html#Approving_offer_content)

설치 안내서에 새 섹션이 추가되어 관리 / Platform / 옵션 노드의 옵션을 나열합니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Configuring_Campaign_options.html)

메일링 목록을 보호하기 위해 시드 주소의 사용에 대한 정보가 추가되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/DLV_Using_seed_addresses_About_seed_addresses.html)

배달을 만들고 전송할 때 주요 단계는 필요한 경우 다양한 채널에 대한 참조를 사용하여 새 섹션으로 다시 그룹화되었습니다. [자세한 내용](../../delivery/using/steps-about-delivery-creation-steps.md)

e- [메일 아카이빙](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html) 섹션이 명확한 정보로 이동, 재구성 및 개선되었습니다.

* 연결당 이메일 및 BCC 전송 IP 매개 변수에 대한 우수 사례가 추가되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Best_practices)

* 이전 빌드(Adobe Campaign 17.2 이전 - 빌드 8795)로 이메일 보관을 이미 사용하고 있는 경우 새 BCC(이메일 보관 시스템)로 업그레이드하는 단계를 업데이트했습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Updated_email_archiving_system__BCC_)

워크플로우 자동화 안내서에 사용 사례가 추가되었습니다. 운영자에게 개인화된 경고 전송 [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Sending_personalized_alerts_to_operators.html)

&quot;새 버전으로 마이그레이션&quot; 섹션이 업데이트되었습니다. 이제 Adobe Campaign v6.11로 더 이상 마이그레이션할 수 없으므로 설명서에는 모든 이전 버전에서 Adobe Campaign Classic v7으로 마이그레이션하는 단계만 자세히 설명되어 있습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/MIG_Migration_overview_About_migration.html)

배달 임시 실패 후 다시 시도&quot; 섹션이 명확해졌습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_delivery_failures.html#Retries_after_a_delivery_temporary_failure)

&quot;Digital Content Editor&quot; 섹션에 대한 링크가 &quot;이메일 컨텐츠 정의&quot; 섹션에 추가되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Defining_the_email_content.html#Message_content)

&quot;트랜잭션 메시징 아키텍처&quot; 섹션이 컨트롤 및 실행 인스턴스를 동일한 컴퓨터에 설치할 수 없다는 경고 메시지와 함께 업데이트되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/MCE_Introduction_Transactional_messaging_architecture.html)

이러한 빌드에 대한 Workflow HeatMap 패키지 설치 방법에 대한 기술 문서에 대한 링크를 포함하여, &quot;워크플로우 모니터링&quot; 섹션이 8700과 8977(18.10) 사이의 빌드에 대한 메모로 업데이트되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#About_the_Workflow_HeatMap)

워크플로우에서 데이터 강화 활동을 사용하여 사용자 지정 필드가 있는 이메일을 보내는 방법에 대한 사용 사례를 추가했습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Email_enrichment_with_custom_date_fields.html)

기능 비디오가 [여기로 이동되었습니다](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/overview.html).

Teradata와 [MySQL](https://helpx.adobe.com/campaign/kb/campaign_fda_teradata.html) 5.7 [에 두 가지 기술 정보가 추가되었습니다](https://helpx.adobe.com/campaign/kb/campaign_fda_mysql.html).

## 18.10 - 05/11/2018{#release-18-10}

**릴리스에 포함된 새로운 기능**

향상된 푸시 알림 - [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_push_notifications_Setting_up_mobile_app_channel.html#Integrating_the_SDK_into_the_mobile_application)

SQL 데이터 관리 활동 - [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Action_activities.html#SQL_Data_Management)

워크플로우 모니터링 - [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#Workflow_monitoring)

**릴리스와 함께 제공되는 기타 설명서 업데이트**

이제 [전용 페이지에서 Campaign Classic API를 사용할 수 있습니다](https://docs.campaign.adobe.com/doc/AC/en/jsapi/index.html). jsapi.chm 파일을 사용하는 경우 이제 새로운 온라인 버전을 참조해야 합니다.

호환성 매트릭스가 업데이트되었습니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

&#39;Campaign Classic에서 더 이상 사용되지 않음 및 제거된 기능&#39; 페이지가 업데이트되었습니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

릴리스 [노트](https://docs.campaign.adobe.com/doc/AC/en/RN.html) 및 [기존 릴리스 노트에서는](https://docs.campaign.adobe.com/doc/AC/en/RN_legacy.html)회수된 빌드에 대한 경고가 추가되었습니다. 17.9, 18.4 및 18.6에 대한 누적 빌드도 추가되었습니다.

보안 [,](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html)제공 [및](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) 빌드 업그레이드 [시작 안내서가 업데이트되었습니다](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) .

API를 외부에서 호출하는 방법과 queryDef를 사용하여 상태를 쿼리하고 GDPR 파일을 다운로드하는 방법에 대한 정보가 [개인정보 보호](https://helpx.adobe.com/campaign/kb/acc-privacy.html) 시작 안내서로 업데이트되었습니다.

아웃바운드 디스패치에 이메일 첨부 파일을 즉시 추가하는 트랜잭션 메시지 사용 사례를 추가했습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/MCE_Use_case_Purpose.html)

연결 임계값 문제 해결 섹션을 업데이트했습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/PRO_Troubleshooting_Connection_thresholds.html)

프록시 연결을 구성하는 방법에 대한 섹션이 추가되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html#Proxy_connection_configuration)

허가된 외부 명령 제한에 대한 섹션을 업데이트했습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html#Restricting_authorized_external_commands)

SFTP 사용과 관련된 문제 해결 섹션이 추가되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/PTF_Importing_and_exporting_data_SFTP_server_usage.html)

메시지 전송 안내서의 개요 섹션이 다시 구성되었습니다. 배달 생성 글로벌 프로세스 및 다른 배달 유형에 정보가 추가되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/DLV_About_deliveries_and_channels_Communication_channels.html)

오류 메시지 목록이 업데이트되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

시드 주소를 사용하는 방법에 대한 섹션이 메시지 전송 안내서 개요 장으로 이동되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/DLV_Using_seed_addresses_About_seed_addresses.html)

새로운 워크플로우 사용 사례를 추가했습니다. 관련 워크플로우 실행에서 업데이트 관리 [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Coordinating_data_updates.html)

&quot;받은 편지함 렌더링&quot; 섹션은 리트머스 및 보다 자세한 절차에 대한 추가 정보로 업데이트되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_Inbox_rendering.html#Multiplexing_the_mid-sourcing_server)

&#39;스팸차단기&#39; 섹션이 향상되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_SpamAssassin.html)

&quot;압력 규칙으로 마케팅 피로도 관리&quot; 섹션에 사용 사례가 추가되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/CMP_Campaign_Optimization_Pressure_rules.html#Sending_only_the_highest-weighted_messages)

이제 크로스 채널 전달 워크플로우를 만드는 방법을 설명하는 새로운 사용 사례를 사용할 수 있습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Cross-channel_delivery_workflow.html)

일부 권장 사항이 &quot;이메일 보관&quot; 섹션에 추가되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_deliverability.html#Activating_emails_BCC_archiving)

Adobe Campaign 최적 사용을 위한 최소 화면 해상도에 대해 새로운 권장 사항이 추가되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Adobe_Campaign_workspace.html#Screen_resolution)

이 통합의 구성에 일부 설명이 추가되어 Experience Manager 통합 가이드가 업데이트되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/ITG_Adobe_Experience_Manager_About_Adobe_Experience_Manager.html)

그룹 유형 목록과 목록 유형 목록 간의 차이에 대한 정보가 추가되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/PTF_Profile_management_Creating_and_managing_lists.html#About_lists_in_Adobe_Campaign)

보고서 추출을 이메일로 첨부 파일로 전송하도록 코드를 업데이트했습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Sending_a_report_to_a_list.html#Step_3-_Creating_the_workflow)

지난 7일 동안 이메일을 열지 않은 수신자를 필터링하는 쿼리를 만드는 방법에 대한 예가 추가되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Designing_queries.html#Recipients_who_did_not_open_any_delivery)

Adobe Experience Cloud를 사용하여 대상 공유 통합 안내서를 업데이트했습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Sharing_audiences_with_Adobe_Experience_Cloud.html)

이제 일반 질문 도움말 페이지에는 Campaign 사용 가능한 언어, 웹 양식 번역 및 다국어 이메일에 대한 정보가 포함되어 있습니다. [자세한 내용](../../platform/using/common-questions.md)

영어 및 영국 영어 인스턴스 간의 차이는 이제 전용 섹션에 나열됩니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Adobe_Campaign_workspace.html#Formats_and_units)

이제 [일반적인 질문](../../platform/using/common-questions.md) 도움말 페이지가 오류 메시지 페이지로 링크됩니다.

&#39;열기&#39; 추적 모드에 대한 정보가 추가되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/DLV_Tracking_messages_Personalizing_URL_tracking.html)

웹 애플리케이션 및 웹 양식의 최소 해상도에 대한 정보를 추가할 수 있습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/WEB_Web_forms_About_web_forms.html)

Campaign 및 Adobe Experience Cloud 솔루션 통합 안내서가 업데이트 및 재구성되었습니다. [자세한 내용](../../integrations/using/about-campaign-integrations.md)

웹 양식의 텍스트 변수 사용에 대한 섹션이 추가되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/WEB_Web_forms_Static_elements_in_a_web_form.html#Using_text_variables)

이제 메시지의 URL 추적 모드가 자세히 표시됩니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/DLV_Tracking_messages_How_to_configure_tracked_links.html)

인스턴스 생성 섹션이 재구성되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/INS_Initial_configuration_Creating_an_instance_and_logging_on.html)

일본의 모바일에 이메일 전송을 기록한 문서가 새로 추가되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Defining_the_email_content.html#Sending_emails_on_Japanese_mobiles)

&quot;개인화 최적화&quot; 섹션이 자세한 정보로 업데이트되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalization_fields.html#Optimizing_personalization)

## 18.6 - 09/07/2018{#release-18-6}

**릴리스에 포함된 새로운 기능**

호환성 매트릭스가 업데이트되었습니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

JSAPI 설명서가 업데이트되었습니다. [자세한 내용](https://support.neolane.net/webApp/extranetLogin)

더 이상 사용되지 않음 및 제거된 기능 페이지가 업데이트되었습니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

**릴리스와 함께 제공되는 기타 설명서 업데이트**

Campaign Classic 사용자 가이드의 이름이 탐색 단순화, 사용자 경험 개선, 정보 액세스 및 자가 도움말로 변경되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/browseAC.html)

표현식 편집기에서 사용할 수 있는 함수 목록이 업데이트되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/PTF_Creating_queries_Defining_filter_conditions.html#List_of_functions)

PI가 포함된 페이지를 보호하는 방법에 대한 정보가 포함된 보안 시작 안내서가 업데이트되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html)

오류 메시지 목록이 업데이트되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

문제 해결 섹션이 IMS 통합 문서에 추가되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/ITG_Connecting_via_an_Adobe_ID_IMS_troubleshooting.html)

업그레이드 빌드 시작 안내서가 업데이트되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html)

IP 친화성 구성 섹션이 업데이트되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Mid-sourcing_server.html#Multiplexing_the_mid-sourcing_server)

성능 및 처리량 문제 해결 섹션이 추가되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/PRO_Troubleshooting_Performance_and_throughput_issues.html)

내장된 개인화 블록 목록이 예제로 업데이트되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalization_blocks.html#Out-of-the-box_personalization_blocks)

배달 실패 이유 목록이 업데이트되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_delivery_failures.html#Delivery_failure_types_and_reasons)

패키지 정의 관리에 대한 새 섹션이 추가되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_Working_with_data_packages.html#Managing_package_definitions)

Adobe Analytics - 데이터 커넥터 섹션과의 캠페인 통합이 개선되고 재구성되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Adobe_Analytics_Data_Connector.html)

단계별 가이드 및 사용 방법 비디오에 대한 링크가 포함된 새로운 자습서 섹션이 추가되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Tutorials.html)

SMS 커넥터 프로토콜 및 설정에 대한 새 기술 문서가 만들어졌습니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html)

게재 모범 사례 시작 안내서가 업데이트되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html)

웹 API 배포가 포함된 Microsoft Dynamics 365 계정 구성이 업데이트되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_CRM_Connectors.html#Example_for_Microsoft_Dynamics)

Windows 플랫폼에 Adobe Campaign Classic을 설치하는 절차가 업데이트되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/INS_Installing_Campaign_in_Windows__Installing_the_server.html)

Adobe Experience Cloud와 Campaign Classic 간의 고객 공유 일정이 자세히 설명되어 있습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Importing_and_exporting_audiences.html)

Campaign Classic 목록에 대한 기술 자료 아티클이 업데이트되었습니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/article-list.html)

성능 개선 및 모범 사례에 대한 새로운 기술 문서가 라이브됩니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/best-practices-for-performance-improvement.html)

A/B 테스트 샘플이 업데이트되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_A-B_testing.html)

Campaign Classic 일반 질문/FAQ 페이지가 업데이트되었습니다. [자세한 내용](../../platform/using/common-questions.md)

## 18.4 - 24/04/2018{#release-18-4}

**릴리스에 포함된 새로운 기능**

EU 개인 정보 보호 규정(GDPR) - [자세한 내용](https://helpx.adobe.com/campaign/kb/acc-privacy.html)

활성 프로필 - [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/PTF_Profile_management_About_profiles.html#Active_profiles)

Android 푸시 커넥터 개선 - [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_push_notifications_Setting_up_mobile_app_channel.html#Android_connectors)

**릴리스와 함께 제공되는 기타 설명서 업데이트**

릴리스 노트는 향상된 사용자 경험을 위해 개선되었으며 이제 고객 요청과 관련된 모든 패치를 포함하고 있습니다.  [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/RN.html)

Campaign Classic에 대한 가장 일반적인 질문과 함께 새 페이지가 추가되었습니다. [자세한 내용](../../platform/using/common-questions.md)

오류 메시지 목록이 업데이트되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Marketing Cloud 트리거 기술 정보가 업데이트되었습니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html)

기존 Campaign Classic 버전에 개인 정보(GDPR) 패키지를 설치하고 배포하는 방법에 대한 기술 문서가 추가되었습니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/how-to-install-gdpr-package-on-legacy-versions.html)

새로운 시퀀스 자동 생성 메커니즘에 대한 기술 자료가 추가되었습니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html)

JSAPI 설명서가 업데이트되었습니다. [자세한 내용](https://support.neolane.net/webApp/extranetLogin)

호환성 매트릭스가 업데이트되었습니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

이제 더 이상 사용되지 않는 기능 및 버전을 나열하는 새 페이지를 사용할 수 있습니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

RDBMS에 대한 몇 가지 알려진 제한 사항과 우수 사례가 추가되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/INS_Prerequisites_and_recommendations__Database.html)

SFTP 사용과 관련된 우수 사례를 살펴보십시오. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/PTF_Importing_and_exporting_data_SFTP_server_usage.html)

기술 워크플로우 목록이 업데이트되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/WKF_Technical_workflows_About_technical_workflows.html)

기술 자료 문서(이전의 &#39;기술 문서&#39;라고 함) 목록은 이제 여기에서 사용할 수 있습니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/article-list.html)

방법 [비디오가](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html) 업데이트되었습니다.

LINE 패키지 감가상각 후 LINE 설명서를 갱신했습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_messages_on_mobiles_LINE_channel.html)

보고서 표시기 계산 설명서를 업데이트했습니다. [자세한 내용](../../reporting/using/indicator-calculation.md)

Oracle과 표준 시간대 파일 정렬에 대한 정보가 추가되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/MIG_Configuration_General_configurations.html#Oracle)

배송 오류 및 검역소 관리에 대한 업데이트된 정보가 포함된 새로운 &quot;배달 모니터링&quot; 섹션을 추가했습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Monitoring_a_delivery.html)

즉시 사용 가능한 개인화 블록에 대한 새로운 정보로 &quot;개인화 블록&quot; 섹션을 재구성합니다.
[자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalization_blocks.html)

파일 구성에 대한 새 정보로 이메일 보관 섹션을 다시 ```config-<instance name>.xml``` 정리했습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Activating_email_archiving__on_premise_)

메시지 센터(제어) 기술 워크플로우에 대한 정보가 업데이트되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/WKF_Technical_workflows_Message_Center__Control_.html)

SMTP 릴레이를 설정할 때 처리량 제한에 대한 정보가 추가되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html#Personalizing_delivery_parameters)

## 17.12 - 14/12/2017{#release-doc-14-12-2017}

향상된 유용성을 위해 [Adobe Campaign Classic 설명서](https://helpx.adobe.com/support/campaign/classic.html) 세트가 재구성되었습니다.

핵심 캠페인 기능 도움말 자료, 사용 방법, 샘플 및 비디오에 쉽게 액세스할 수 있도록 새로운 자습서 섹션이 추가되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Tutorials.html)

배달 상태를 모니터링하면서도 가능한 오류를 파악하고 이를 수정하는 방법을 학습하는 데 도움이 되는 새 섹션이 추가되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Monitoring_a_delivery.html)

오류 메시지 목록이 업데이트되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Marketing Cloud 트리거 기술 정보가 업데이트되었습니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html)

Campaign Classic 마이그레이션 안내서가 컬렉션에 추가되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/MIG_Migration_overview_About_migration.html)

캠페인 호환성 매트릭스가 업데이트되었습니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

적용 가능한 경우 구성 및 설치 지침에 따라 적용되는 호스팅 모델이 언급됩니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html)

온-프레미스, 하이브리드 및 Managed Services 배포 간의 구성 및 기능 차이점을 강조 표시하는 새로운 기술 자료 문서입니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html)

표준 패키지를 설치하는 방법에 대한 지침을 추가했습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/INS_Initial_configuration_Installing_packages.html)

Audience Manager 또는 사용자 핵심 서비스와의 통합을 구성하는 방법에 대한 세부 정보가 추가되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Configuring_shared_audiences_integration_in_Adobe_Campaign.html)

PowerSQL을 사용하는 경우 이제 Campaign을 설치하려면 Crypto가 필요하다는 사실을 알려주는 설치 설명서를 업데이트했습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/INS_Installing_Campaign_in_Linux__Prerequisites.html#Database_access_layers)

## 17.9 - 25/09/2017{#release-17-9}

**릴리스에 포함된 새로운 기능**

ACS 커넥터 개선 사항

SAP HANA 커넥터 - [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Accessing_an_external_database.html#SAP_HANA)

HiveSQL을 통한 Hadoop 커넥터 - [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Accessing_an_external_database.html#Hadoop)

LINE 채널: 향상된 메시지 기능 - [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_messages_on_mobiles_LINE_channel.html)

**릴리스와 함께 제공되는 기타 설명서 업데이트**

새 쿼리 샘플이 추가되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Designing_queries.html#Filtering_duplicated_recipients)

배달 우수 사례 안내서가 업데이트되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html)

A/B 테스트 샘플이 누락된 명령으로 업데이트되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_A-B_testing.html)

방법 비디오가 업데이트되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html)

이메일 보관 섹션을 업데이트합니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html)

워크플로우에서 스케줄러 사용을 명확하게 합니다. [자세한 내용](../../workflow/using/scheduler.md)

일시 중지된 워크플로우 추가 우수 사례 [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Executing_a_workflow.html)

워크플로우에서 데이터를 내보낼 때 파일을 가져올 때 및 사후 처리에 대한 새 절차입니다. 여기 [에서](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Importing_data.html)읽으세요

확장 일반 SMPP 커넥터에 대한 오류 관리 특성을 반영하도록 SMS 메시지 문서에 대한 격리 메커니즘이 업데이트되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_quarantine_management.html#SMS_quarantines)

Android에서 풍부한 알림을 전송하는 세부 절차를 통해 모바일 앱 채널 문서가 향상되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_push_notifications_Setting_up_mobile_app_channel.html#Rich_notifications)

받은 편지함 렌더링 설명서가 업데이트되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_Inbox_rendering.html)

웹 추적 설정 설명서가 업데이트된 예와 참고로 개선되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/CFG_Setting_up_web_tracking_Additional_parameters.html#Redirection_server_configuration)

SMS 채널 설명서는 확장된 일반 SMPP 커넥터에 적용되는 자동 회신 섹션에 몇 가지 명확히 추가되어 업데이트되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_messages_on_mobiles_SMS_channel.html#Creating_an_SMPP_external_account)

Social 마케팅 설명서가 업데이트되었습니다. [자세한 내용](../../social/using/about-social-marketing.md)

IP 온난화에 대한 새로운 기술이 추가되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/Technotes/AdobeCampaign_Deliverability_IP_Warming_overview.pdf)

빌드 업그레이드를 시작하는 새 버전이 추가되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html)

## 2017년 5월{#release-doc-30-05-2017}

새 시작 안내서를 사용할 수 있습니다. 여기에는 생성, 타깃팅, 전송 및 모니터링에서 Adobe Campaign과 함께 전달하는 데 사용할 수 있는 몇 가지 우수 사례가 나와 있습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html)

시작 가이드가 업데이트되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html)

&quot; [이메일 보관&quot; 문서](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html) 가 [&quot;이메일 BCC&quot;](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Configuring_the_BCC_email_address__on_premise_) 섹션 [및 기능을 활성화하기 위한](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Sending_messages.html#Archiving_emails)자세한 단계로 업데이트되었습니다.

일부 비디오가 추가되고 업데이트되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html)

데이터베이스를 업데이트하지 않고 외부 파일에서 로드한 수신자에게 배달을 보내는 방법을 알아봅니다. [자세한 내용](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients)

이중 옵트인 예가 업데이트되었습니다. [자세한 내용](../../web/using/use-cases--web-forms.md)

## 2017년 3월{#release-doc-31-03-2017}

제공 가능성: 시작 안내서 [가](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) 업데이트되었습니다. 제공 기능 설명서에는 보다 자세한 [개요](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_About_deliverability.html) 및 [구현 프로세스 및 기본 단계에 대한 설명이 포함되어 있습니다](../../delivery/using/deliverability-key-points.md).

&quot;파도를 사용하여 보내기&quot; 섹션이 자세한 예제, 추천 및 사용 사례와 함께 이동되고 개선되었습니다.    [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Sending_messages.html#Sending_using_multiple_waves)

&quot;격리 관리&quot; 섹션에 SMS 메시지 관련 오류를 설명하는 표가 추가되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_quarantine_management.html#SMS_quarantines)

워크플로우: 새로운 다중 채널 워크플로우 예가 추가되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Action_activities.html#Cross-channel_deliveries)

Marketing Cloud 트리거: Adobe Campaign과 함께 구성 및 사용하는 방법에 대한 기술 문서가 추가되었습니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html)

워크플로우 가이드가 다시 구성 및 확장되었습니다. 작업 과정을 [만들고](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Building_a_workflow.html) [실행하는](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Executing_a_workflow.html) 방법, [대상](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Targeting_data.html) 을 [만들고](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Targeting_data.html#Data_Management) 관리하는 방법, 데이터를 [타깃팅하고](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Importing_data.html) 관리하는 방법, 데이터를 가져오는 방법, 데이터를 가져오는 방법, 워크플로 데이터를 사용하는 방법, 데이터베이스를 업데이트하는 방법, 데이터베이스 업데이트 또는 전달을 보내는 방법 [을 쉽게 찾을](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_How_to_use_workflow_data.html#Updating_the_database) [](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_How_to_use_workflow_data.html#Delivering_via_a_workflow)수 있습니다.

가져오기 [우수 사례](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_How_to_use_workflow_data.html#Delivering_via_a_workflow) 에 따라 작성된 가져오기 작업 과정 [의 예를](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Importing_data.html#Import_best_practices) 사용할 수 있습니다.
설치 가이드가 이 새 버전에 대해 업데이트되었습니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/INS_Architecture_and_hosting_models_General_architecture.html)

호환성 매트릭스가 업데이트되었습니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

받는 사람은 이메일 배달에 쿠폰을 포함할 때 값이 추가됩니다. [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalized_coupons.html)

## Adobe Campaign v7 - 2017년 16월 03일{#release-17-2}

**릴리스에 포함된 새로운 기능**

ACS 커넥터

Microsoft Dynamics용 웹 API - [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_CRM_Connectors.html#Example_for_Microsoft_Dynamics)

이메일 보관 BCC 방법 - [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Updated_email_archiving_system__BCC_)

Amazon Simple Storage Service (S3) 커넥터 - [자세한 내용](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Event_activities.html#File_transfer)

