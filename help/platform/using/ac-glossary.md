---
product: campaign
title: Adobe Campaign 용어집
description: Adobe Campaign 용어집
role: User, Data Architect
level: Beginner
exl-id: 81f207a0-bb72-450b-abe4-0b229b6b1f3a
source-git-commit: 978da934b483a54509ad806f375d9b2bb0577dac
workflow-type: tm+mt
source-wordcount: '5974'
ht-degree: 4%

---

# Adobe Campaign 용어{#ac-glossary}

다음은 관련 설명서에 대한 링크와 함께 Adobe Campaign의 주요 용어 및 개념에 대한 정의입니다. 용어를 클릭하여 정의를 표시합니다.

## A - D{#sec-1}

+++**A/B 테스트**

A/B 테스트는 사용자가 2~3개의 이메일 변형을 정의할 수 있는 기능입니다. 각 변형은 최고의 결과를 결정하기 위해 모집단 샘플로 전송됩니다. 일단 결정되면 채택된 변형은 나머지 모집단으로 전송됩니다.

자세히 알아보기 [A/B 테스트](../../delivery/using/get-started-a-b-testing.md).
+++

+++**액세스 관리**

액세스 관리를 통해 관리자는 Adobe Campaign 사용자에게 액세스 및 권한을 할당할 수 있습니다. 권한에는 워크플로우 실행, 스키마 정의 및 대상자 관리와 같은 Adobe Campaign 기능을 보거나 사용할 수 있는 기능이 포함됩니다.

자세히 알아보기 [액세스 관리](access-management.md).
+++

<!--
+++**ACS Connector**

ACS Connector (Prime Offering) bridges Adobe Campaign v7 and Adobe Campaign Standard. It is an integrated feature in Campaign v7 that automatically replicates data to Campaign Standard, uniting the best of both applications. Campaign v7 has advanced tools to manage the primary marketing database. The data replication from Campaign v7 allows Campaign Standard to leverage the rich data in a user-friendly environment. 

Learn more about [ACS Connector](../../integrations/using/acs-connector-principles-and-data-cycle.md).
+++
-->

+++**활동**

활동은 실행 기능을 정의하기 위해 워크플로우에 추가되는 팔레트 항목입니다. 활동은 작업을 실행하는 컨테이너입니다. 워크플로우에서 특정 활동은 여러 작업, 특히 루프 또는 반복적인(주기적) 작업이 있는 경우 여러 작업을 생성할 수 있습니다.

자세히 알아보기 [워크플로우 활동](../../workflow/using/about-activities.md).
+++

+++**활성 프로필**

지난 12개월 동안 어느 채널을 통해 프로필을 타겟팅하거나 통신한 경우 프로필이 활성 상태로 간주됩니다. 계약에 따라 각 Campaign 인스턴스에는 청구 용도로 계산되는 특정 수의 활성 프로필이 제공됩니다.

자세히 알아보기 [활성 프로필](../../platform/using/about-profiles.md#active-profiles).
+++

+++**승인 워크플로우 활동**

*컨텍스트: Campaign 분산 마케팅*

로컬 승인 활동은 메시지를 보내기 전에 게재 승인 프로세스를 설정하는 데 사용되는 워크플로우 활동입니다.

에 대해 자세히 알아보기 [로컬 승인 활동](../../workflow/using/local-approval.md).
+++

+++**대상자**

대상자는 규칙과 속성을 기반으로 필터 정의의 기준을 충족하는 결과 프로필 세트입니다.

자세히 알아보기 [대상](../../campaign/using/marketing-campaign-target.md).
+++

+++**감사 추적**

감사 추적은 Adobe Campaign 인스턴스 내에서 발생하는 작업 및 이벤트의 포괄적인 목록을 실시간으로 캡처합니다. 여기에는 워크플로우에 발생한 사항, 워크플로우를 마지막으로 업데이트한 사람 또는 사용자가 인스턴스에서 수행한 작업 등의 질문에 답변하는 데 도움이 되는 데이터 기록에 액세스하는 셀프서비스 방법이 포함되어 있습니다.

자세히 알아보기 [감사 추적](../../production/using/audit-trail.md).
+++

<!--
----DUPLICATE WITH THE "CAMPAIGN" ENTRY?---
+++**Automated campaigns**

Campaigns that run on a schedule, such as for targeting recipients who have a birthday or an anniversary. Can also be used to execute look-ahead and look-back logic, such as who purchased yesterday or who has a payment due tomorrow.

Learn more about [Campaigns](../../campaign/using/designing-marketing-campaigns.md).
+++
-->

+++**배치 모드**

*컨텍스트: 캠페인 상호 작용*

Campaign 상호 작용 컨텍스트에서 배치 모드를 사용하면 오퍼 엔진에서 연락처 세트에 대한 최상의 오퍼(또는 오퍼)를 선택할 수 있습니다. 자격/우선 순위 규칙은 해당 집합의 모든 연락처에 적용됩니다.

자세히 알아보기 [상호 작용](../../interaction/using/interaction-and-offer-management.md).
+++

+++**캠페인**

Campaign은 마케팅 캠페인을 조정, 정의 및 실행하는 인터페이스입니다. 캠페인에는 하나 이상의 워크플로우, 게재, 문서 및 기타 관련 데이터 포인트를 사용하기 쉬운 단일 인터페이스에 포함할 수 있습니다.

자세히 알아보기 [캠페인](../../campaign/using/designing-marketing-campaigns.md).
+++

<!--
-----NOT USEFUL HERE?-----
+++**Changeover process**

*Context: Campaign Interaction*

In the context of Campaign Interaction, the changeover process is an activated process in an identified environment, responsible for directing the call to an anonymous environment if the contact has not been explicitly and/or implicitly identified.

Learn more about [Interaction](../../interaction/using/interaction-and-offer-management.md).
+++
-->

+++**채널**

채널은 통신을 전송하는 매체입니다. Adobe Campaign의 기본 제공 채널에는 이메일, SMS, DM, 푸시 알림, LINE 및 Twitter이 있습니다. 비표준 채널 요구 사항에 맞게 사용자 지정 채널을 구현할 수 있습니다.

자세히 알아보기 [채널](../../delivery/using/communication-channels.md).
+++

+++**클라이언트 콘솔**

Campaign 클라이언트 콘솔은 Campaign 애플리케이션 서버에 연결할 수 있는 리치 클라이언트입니다. 클라이언트 콘솔 실행 파일(.exe) 응용 프로그램은 Microsoft Windows 운영 체제가 설치된 컴퓨터에 설치됩니다. Campaign 클라이언트 콘솔은 모든 기능과 설정을 중앙 집중화합니다.

자세히 알아보기 [클라이언트 콘솔](../../platform/using/adobe-campaign-workspace.md).
+++

+++**콘텐츠 승인**

콘텐츠 승인은 게재를 보내기 전에 별도의 운영자 또는 운영자 그룹이 게재 콘텐츠를 승인하도록 하는 프로세스입니다.

자세히 알아보기 [콘텐츠 승인](../../campaign/using/marketing-campaign-approval.md).
+++

+++**컨트롤 그룹**

컨트롤 그룹을 사용하여 대상의 일부를 제외하여 캠페인의 영향을 측정합니다. 운영자는 메시지를 받은 대상 모집단의 행동과 타겟팅되지 않은 연락처의 행동을 비교할 수 있습니다. 전송 로그를 기반으로 운영자는 향후 캠페인에서 컨트롤 그룹을 타겟팅할 수도 있습니다.

자세히 알아보기 [컨트롤 그룹](../../campaign/using/marketing-campaign-target.md#defining-a-control-group).
+++

+++**컨트롤 패널**

이 Campaign 컨트롤 패널은 Adobe Campaign 제품 관리자가 각 인스턴스에 대한 설정을 관리하고 사용을 추적할 수 있도록 함으로써 작업의 효율성을 높이는 데 도움이 됩니다. 컨트롤 패널의 직관적인 인터페이스를 활용하면 주요 자산의 사용을 손쉽게 모니터링할 수 있을 뿐만 아니라 IP 주소 허용 목록 추가, SFTP 스토리지 모니터링, 키 관리 등의 관리 작업도 수행할 수 있습니다.

자세히 알아보기 [Campaign 컨트롤 패널](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=ko).
+++

+++**큐브**

*컨텍스트: Marketing Analytics*

큐브는 사용자가 동적 보고서를 만들고 공유할 수 있도록 지원하는 Adobe Campaign 직관적인 데이터 탐색 도구입니다.

자세히 알아보기 [큐브](../../reporting/using/ac-cubes.md).
+++

+++**사용자 정의 리소스**

Adobe Campaign에는 다양한 패키지 설치를 통해 데이터 유형을 정의하는 사전 정의된 데이터 모델이 포함되어 있습니다. 연산자는 리소스를 확장하여 제공되는 데이터 모델을 보강하여 트랜잭션 또는 제품 테이블과 같은 사용자 지정 필드 또는 사용자 지정 테이블을 추가할 수 있습니다.

자세히 알아보기 [사용자 정의 리소스](../../configuration/using/about-schema-edition.md).
+++

+++**데이터 모델**

Campaign 데이터 모델은 데이터 유형 및 해당 관계(링크)를 정의하는 스키마 세트입니다. 데이터 모델은 실제 데이터가 포함된 데이터베이스로 물리적으로 구현된 추상적인 정의입니다.

자세히 알아보기 [데이터 모델](../../configuration/using/about-data-model.md).
+++

+++**데이터베이스 정리 워크플로우**

데이터베이스 정리 워크플로우는 데이터베이스의 기하급수적인 증가를 방지하기 위해 오래된 데이터를 삭제합니다. 워크플로우는 사용자의 개입 없이 자동으로 트리거됩니다.

자세히 알아보기 [데이터베이스 정리 워크플로우](../../production/using/database-cleanup-workflow.md).
+++

<!--
----UNCLEAR----
+++**Dedicated server**

*Context: Transactional Messaging*

Dedicated execution server(s) to leverage Transactional Messaging. A server can typically process up to 50,000 Engine Calls per hour. The “Per-Dedicated Server” designation does not necessarily have a 1:1 correlation with a physical server as Adobe may utilize virtualization technologies to achieve the equivalent effect.

Learn more about [Transactional Messaging](../../message-center/using/about-transactional-messaging.md).
+++
-->

+++**게재 가능성**

*컨텍스트: 이메일 전달성*

전달성을 사용하면 캠페인이 바운스 없이 또는 스팸으로 표시되지 않고 수신자의 받은 편지함에 도달했는지 측정할 수 있습니다. 더 정확히 말하면 이메일 전달성이란 메시지가 개인 이메일 주소를 통해, 짧은 시간 내에, 그리고 콘텐츠와 형식 측면에서 예상되는 품질로 대상에 도달할 수 있는지를 결정하는 일련의 특성을 의미합니다.

자세히 알아보기 [전달성](../../delivery/using/about-deliverability.md).
+++

+++**게재**

게재는 특정 채널(이메일, SMS, 푸시 알림 등)의 대상자에게 전송되는 특정 마케팅 커뮤니케이션 항목입니다. 마케팅 용어로 &quot;터치&quot;라고도 합니다.

자세히 알아보기 [게재](../../delivery/using/communication-channels.md).
+++

+++**게재 분석**

게재 분석은 게재를 준비하는 것입니다. 이 프로세스는 콘텐츠를 수신자 프로필 데이터와 결합하여 수신자가 수신하는 개인화된 이메일을 생성합니다. 게재 분석 논리는 정의된 논리를 기반으로 수신자를 대상에서 제외하거나 게재를 완전히 중단할 수 있습니다. 이 프로세스에는 동적 콘텐츠 논리 평가 및 개별 수신자 프로필에 대한 오퍼 삽입도 포함됩니다.

자세히 알아보기 [게재 분석](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).
+++

+++**게재 로그**

게재 로그에는 메시지를 보낼 때 생성된 정보가 포함됩니다. 이러한 로그는 메시지가 준비, 무시, 전송 또는 실패한 세부 전송 정보를 보여 줍니다. 게재 대시보드에서 바로 액세스할 수 있습니다.

자세히 알아보기 [게재 로그](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history).
+++

<!--
----STRANGE IN DOCS?----
+++**Delivery fundamentals**

*Context: Email Deliverability*

Adobe Campaign Deliverability Fundamentals Consulting Service provides email deliverability consultation and reputation management to support customers using Adobe Campaign deliveries.

Learn more about [Deliverability](../../delivery/using/about-deliverability.md).
+++
-->

+++**게재 개요**

*컨텍스트: DM*

게재 개요는 구조화된 요소 세트(문서, 스토어, 프로모션 쿠폰 등)입니다. 회사에서 만든 다음 특정 캠페인을 위해 만듭니다. DM 게재 컨텍스트에서 사용됩니다.

자세히 알아보기 [다이렉트 메일](../../delivery/using/about-direct-mail-channel.md).
+++

+++**배포 마법사**

배포 마법사는 기본 네임스페이스, 데이터베이스 정리 일정, 데이터 보존 기간 및 기타 기술 설정과 같은 Campaign 인스턴스의 매개 변수를 정의합니다.

자세히 알아보기 [배포 마법사](../../installation/using/deploying-an-instance.md#deployment-wizard).
+++

+++**설명 분석**

설명 분석 은 워크플로우의 작업 테이블에서 데이터, 폴더에서 선택한 데이터를 검사하거나 선택한 게재의 대상 및 제외에 대해 심도 있는 분석을 수행하는 데 사용할 수 있는 상황에 맞는 보고 도구입니다.

자세히 알아보기 [설명 분석](../../reporting/using/about-descriptive-analysis.md)
+++

+++**분산 마케팅**

*컨텍스트: Distributed Marketing*

Distributed Marketing 추가 기능은 중앙 엔터티(본사, 마케팅 부서 등) 간의 캠페인을 구현하기 위한 공동 작업 영역을 캠페인 운영자에게 제공합니다 공동 캠페인을 실시할 수 있습니다. 이러한 협력은 다음과 같은 공유 작업 영역을 기반으로 합니다. **캠페인 패키지 목록**: 중앙에서 생성된 캠페인 템플릿과 인스턴스가 로컬 엔티티에 제공됩니다.

자세히 알아보기 [분산 마케팅](../../distributed/using/about-distributed-marketing.md)
+++

+++**값 분포**

값 분포는 데이터베이스에 현재 존재하는 스키마 속성에 대한 값 분포를 보여 주는 도구입니다. 이렇게 하면 사용 가능한 값, 해당 개수 및 백분율을 결정하고, 쿼리나 표현식을 만들 때 값의 대문자 및 맞춤법에 문제가 발생하지 않도록 하는 데 도움이 됩니다.

자세히 알아보기 [값 분포](../../platform/using/defining-filter-conditions.md#selecting-data-to-extract)
+++

+++**도메인 위임**

하위 도메인 구성을 사용하면 Adobe Campaign에서 사용할 도메인의 하위 섹션(기술적 명칭은 &quot;DNS 영역&quot;)을 구성할 수 있습니다.
도메인 위임을 통해 Adobe은 이메일 캠페인 게재, 렌더링 및 추적에 필요한 DNS의 모든 측면을 제어하고 유지 관리할 수 있습니다.

자세히 알아보기 [도메인 위임](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html?lang=ko)
+++

## E - H {#sec-2}

<!--
----DEPRECATED------>
+++**E4X**

E4X는 Adobe Campaign Classic에서 사용되는 Javascript 버전입니다. ECMAScript라고도 하며, 동일한 코드에서 Javascript와 XML 프리미티브를 혼합할 수 있는 Javascript의 확장입니다. E4X는 더 이상 사용되지 않는 언어로 분류됩니다.
+++


+++**자격 규칙**

*컨텍스트: 캠페인 상호 작용*

자격 규칙은 유효 기간, 대상 및 가중치와 관련하여 환경, 카테고리 또는 오퍼에 적용되는 제약 조건입니다. 운영자는 오퍼가 타겟팅된 연락처와 일치하는지 확인할 수 있습니다. 오퍼 환경에서 자격 규칙에는 오퍼와 타깃팅할 수신자에 적용되는 프레젠테이션 규칙이 포함됩니다. 카테고리에서는 자격 규칙을 사용하여 운영자가 카테고리의 유효성을 제시간에 제한하고 애플리케이션 테마를 정의하며 타겟팅할 수신자를 결정할 수 있습니다. 또한 주어진 기간 동안 승수 가중치를 정의할 수 있습니다. 이렇게 하면 운영자가 다른 범주의 오퍼에 대한 규칙을 공유할 수 있으므로 관리가 간단해집니다. 오퍼에서 자격 규칙을 사용하면 운영자가 오퍼의 유효성을 제시간에 제한하고 수신자를 타겟팅할 수신자를 결정할 수 있습니다.

자세히 알아보기 [자격 규칙](../../interaction/using/interaction-and-offer-management.md).
+++

+++**적격 오퍼**

*컨텍스트: 캠페인 상호 작용*

적격 오퍼는 타겟에 일관되게 오퍼할 수 있는 업스트림에 정의된 제약 조건을 충족하는 오퍼입니다.

자세히 알아보기 [상호 작용](../../interaction/using/interaction-and-offer-management.md).
+++

+++**이메일 BCC**

이메일 BCC 기능은 전달된 해당 이메일의 정확한 사본을 EML 형식으로 전송하며, 이 사본은 외부 시스템에서 발신자가 이메일을 처리하고 보관할 수 있는 전용 BCC 이메일 주소에 저장됩니다.

자세히 알아보기 [이메일 BCC](../../delivery/using/email-parameters.md#email-bcc).
+++

<!--
-----STRANGE FOR DOCS?----
+++**Email volume commitment**

The anticipated emails sent per year as set forth in the Sales Order. This is the total annual email volume commitment, including emails sent but not delivered due to delivery errors such as: non-delivery of a message including but not limited to email address errors, hard bounces, soft bounces, email filters of mail clients, and email blacklists. 
+++
-->

<!--
-----USEFUL FOR DOCS?----
+++**Engine call**

An engine call is a server call that starts real-time processing on server side for the extraction of data, such as data relating to surveys, WebApps, JSSP, APIs, mobile app registrations, etc. Engine calls must be licensed in packs of 5,000 Engine Calls per day.
+++
-->

+++**보강 활동**

데이터 보강 활동은 워크플로우에서 처리될 생성된 작업 테이블 데이터를 운영자가 보강할 수 있도록 하는 고급 워크플로우 활동입니다. 이 활동은 일반적으로 타겟팅 활동 다음이나 파일을 가져온 후 타겟팅된 데이터를 사용하는 활동 전에 사용됩니다. 보강은 인바운드 전환 데이터를 변환하고 향상된 데이터로 출력 전환을 완료하도록 활동을 구성할 수 있습니다. 이를 통해 운영자는 여러 데이터 세트의 데이터를 결합하거나 임시 리소스에 대한 링크를 만들 수 있습니다.

자세히 알아보기 [데이터 보강 활동](../../workflow/using/enrichment.md).
+++

+++**열거형**

열거형은 필드에 대한 올바른 입력 값을 정의하는 스키마 또는 플랫폼 수준에서 정의된 데이터 형식입니다. 열거형은 사용자 인터페이스 및 쿼리 빌더에 선택 목록으로 표시됩니다.

자세히 알아보기 [열거형](../../platform/using/managing-enumerations.md).
+++

+++**탐색기 보기**

Explorer 보기는 Adobe Campaign 아티팩트와 데이터를 포함하는 폴더의 계층 구조 표시입니다. Adobe Campaign의 폴더 시스템은 각 폴더에 게재, 워크플로우 또는 오퍼와 같은 특정 유형의 데이터가 저장되므로 일반적인 트리뷰처럼 작동하지 않습니다.

자세히 알아보기 [탐색기 보기](../../platform/using/adobe-campaign-explorer.md).
+++

+++**외부 계정**

외부 계정은 제품이 다른 환경 및 기술에 연결하기 위한 시작 및 종료 지점입니다. 외부 계정은 제품이 데이터를 다른 소스로 보내거나 다른 소스에서 데이터를 받는 데 사용하는 연결 매개 변수를 정의합니다. 일반적인 외부 계정 유형은 SFTP 사이트에 대한 연결, SMS 전송을 지원하는 원격 통신, 처리 바운스를 위한 사서함 또는 외부 데이터베이스에 대한 연결입니다.

자세히 알아보기 [외부 계정](../../installation/using/external-accounts.md).
+++

+++**피로도 관리**

*컨텍스트: 캠페인 최적화*

피로도 관리는 수신자의 과도한 요청을 방지하기 위해 메시지 빈도와 수량을 제어하는 데 도움이 되며, 종종 유형화 규칙을 사용하여 적용됩니다.

자세히 알아보기 [피로도 관리](../../campaign-opt/using/pressure-rules.md).
+++

+++**FDA(Federated Data Access)**

Federated Data Access는 타사 데이터베이스를 포함하도록 클라이언트 데이터 모델의 확장을 지원합니다. 대상 테이블의 구조를 자동으로 감지하고 SQL 소스의 데이터를 사용합니다. Adobe Campaign 데이터의 구조를 변경하지 않고 외부 데이터에 액세스할 수 있습니다.

자세히 알아보기 [페더레이션 데이터 액세스](../../installation/using/about-fda.md).
+++

+++**파일 추출 승인**

*컨텍스트: DM*

파일 추출 승인은 DM(Direct Mail) 게재와 같이, 추출한 파일을 외부 공급업체에 보내기 전에 별도의 운영자 또는 운영자 그룹이 해당 파일의 내용과 구성을 승인하도록 하는 프로세스입니다.

자세히 알아보기 [파일 추출 승인](../../delivery/using/validating.md).
+++

+++**필터링 차원**

필터링 차원은 원하는 행을 필터링하기 위해 쿼리에서 사용하는 데이터 또는 속성을 포함하는 스키마입니다. Adobe Campaign이 데이터베이스 조인을 교차하고 응답자 행을 반환할 수 있도록 하려면 필터링 차원 스키마를 정의된 타겟팅 차원에 직접 연결해야 합니다.

자세히 알아보기 [필터링 차원](../../workflow/using/building-a-workflow.md#targeting-and-filtering-dimensions).
+++

+++**폴더**

폴더는 특정 데이터 유형의 데이터베이스 레코드를 포함하는 Explorer 보기 항목입니다. 단, 구성 요소로 사용되며 데이터 자체는 포함되지 않고 다른 폴더만 포함하는 일반 폴더 유형은 예외입니다.

자세히 알아보기 [폴더](../../platform/using/adobe-campaign-explorer.md).
+++

+++**폴더 보기**

폴더 보기는 데이터 유형이 속한 폴더와 관계없이 선택한 데이터 유형의 모든 레코드를 표시하는 데 사용되는 특수 Explorer 폴더 유형입니다. 폴더 보기는 여러 폴더에 분산된 데이터 또는 분할된 데이터를 관리하는 관리 도구로 사용됩니다.

자세히 알아보기 [폴더 보기](../../platform/using/adobe-campaign-explorer.md).
+++

+++**양식**

Forms은 특정 스키마 유형에 대한 인터페이스 표현을 정의합니다. Forms은 수신자, 게재 및 캠페인과 같이 제품에서 데이터 요소를 쉽게 만들고 편집하는 데 사용되는 수단입니다. Adobe Campaign의 모든 인터페이스 요소는 Forms을 사용하여 제품 자체에서 만들어집니다. 양식은 선택 사항이며 모든 스키마에 양식이 있는 것은 아닙니다.

자세히 알아보기 [Forms](../../configuration/using/identifying-a-form.md).
+++

<!--
-----USEFUL HERE?-----
+++**Generated SQL query**

The SQL code generated for the underlying database when an operator manipulates a schema. Schemas define the data types that are then implemented using database tables and columns. The SQL generated for schema manipulation (such as in a query) is based on the installed database type. Thus, the database can be swapped to a different type and the queries in Campaign remain unchanged. Adobe refers to this functionality as being database-agnostic.

Learn more about [Generated SQL queries](../../platform/using/steps-to-create-a-query.md#step-6---preview-data).
+++
-->

+++**열 지도**

Campaign Heatmap은 24시간 동안의 워크플로우 실행 정보를 보여주는 테이블입니다. 이 보고서는 시간 및 5분 간격으로 기간 전체에 걸쳐 워크플로우의 분포를 표시합니다. Heatmap은 서버 로드를 평가하고 가장 많은 리소스를 사용하는 워크플로우 활동을 확인하는 데 사용됩니다.

자세히 알아보기 [열 지도](../../workflow/using/heatmap.md).
+++

+++**하이브리드 배포**

하이브리드 배포는 온 디맨드 서비스와 온-프레미스 소프트웨어가 함께 작동하도록 배포하는 것입니다.

자세히 알아보기 [하이브리드 배포](../../installation/using/hosting-models.md#hybrid).

+++

## I - L {#sec-3}

<!-- added more details but maybe still not clear/useful here? -->
+++**식별 모드**

*컨텍스트: 캠페인 상호 작용*

식별 모드는 연락처의 상태를 나타냅니다. 명시적이거나 암시적이거나 익명적일 수 있습니다.

* **명시적**: 연락처는 채널 인터페이스에 로그인한 후 식별됩니다.
* **암시적**: 연락처가 쿠키(영구 또는 세션)로 식별되었습니다. 익명 또는 식별된 연락처로 처리할 수 있습니다.
* **익명**: 연락처를 식별할 수 없습니다.

자세히 알아보기 [상호 작용](../../interaction/using/interaction-and-offer-management.md).
+++

<!--
----NOT USEFUL HERE?----
+++**Image serving**

The functionality that supplies the images embedded in emails to the delivery’s recipients. The insertion of the images based on an emails system’s “download images” functionality is what generates an “open” entry in Campaign’s tracking logs.

Learn more about [Image serving](../../delivery/using/defining-the-email-content.md#adding-images).
+++
-->

+++**인바운드 상호 작용**

*컨텍스트: 캠페인 상호 작용*

인바운드 상호 작용은 웹, 콜 센터 또는 모바일과 같은 채널에서 연락처의 동작으로 생성된 수신 전화 다음에 이어지는 상호 작용입니다. 이러한 유형의 상호 작용은 일반적으로 단일 모드에서(즉, 수신자마다) 처리된다.

자세히 알아보기 [인바운드 상호 작용](../../interaction/using/about-inbound-channels.md).
+++

+++**받은 편지함 렌더링**

받은 편지함 렌더링은 전자 메일 미리 보기를 생성하여 메시지가 다양한 웹 클라이언트, 웹 메일 및 디바이스에서 최적의 방식으로 수신자에게 표시되도록 합니다. Adobe Campaign은 이메일 콘텐츠 작성자가 Gmail 받은 편지함 또는 Apple Mail 클라이언트와 같은 70개 이상의 이메일 렌더러에서 메시지 콘텐츠를 미리 볼 수 있는 Litmus를 활용합니다.

자세히 알아보기 [받은 편지함 렌더링](../../delivery/using/delivery-dashboard.md#delivery-rendering).
+++

+++**인스턴스 설정**

인스턴스 설정은 Adobe Campaign 인스턴스의 구성 세부 정보입니다. 이러한 설정은 배포 마법사(도구>고급>배포 마법사) 또는 서버 및/또는 인스턴스 구성 파일에 정의됩니다.

자세히 알아보기 [인스턴스 설정](../../installation/using/about-initial-configuration.md).

+++

+++**작업(가져오기 및 내보내기)**

작업은 제품에서 들어오고 나가는 데이터를 간편하게 가져오고 내보내는 마법사 시스템을 통해 관리됩니다. 작업은 단순성과 일관성을 위해 템플릿 시스템을 사용하며 일정에 따라 실행되도록 정의할 수 있습니다.

자세히 알아보기 [가져오기 및 내보내기 작업](../../platform/using/get-started-data-import-export.md).
+++

+++**목록**

목록은 정적 데이터 세트입니다. 목록은 다른 소스(Audience Manager, Experience Platform, 데이터베이스 등)에서 Campaign으로 가져온 대상자 또는 세그먼트이며, 인터페이스에서 가져온 목록으로 표시됩니다.

자세히 알아보기 [목록](../../platform/using/creating-and-managing-lists.md).
+++

+++**로컬 캐시**

로컬 캐시는 운영자의 컴퓨터에 로컬로 저장되는 정보입니다. 캐시된 정보는 콘솔에서 사용하여 서버에 대한 필수 트래픽을 줄이고 성능을 향상시킵니다. 파일 메뉴에서 로컬 캐시를 정기적으로 지우면 저장된 정보가 업데이트되고 성능과 안정성이 향상됩니다.

자세히 알아보기 [로컬 캐시](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear).
+++

## M - P {#sec-4}

+++**마케팅 리소스 관리(MRM)**

*컨텍스트: 마케팅 리소스 관리(MRM)*

다음 **마케팅 리소스 관리(MRM)** Adobe Campaign의 모듈을 사용하면 관련된 작업, 예산 및 마케팅 리소스에 대한 완전한 관리 및 실시간 추적을 제공하여 공동 작업 모드에서 마케팅 작업을 제어할 수 있습니다. Adobe Campaign 운영자는 보고, 승인 추적, 알림, 토론 포럼 등 완벽한 유효성 검사 프로세스 및 적절한 추적 도구를 통해 모든 단계에서 작업을 조정하고 진행 상황을 승인할 수 있습니다.

자세히 알아보기 [MRM](../../mrm/using/about-marketing-resource-management.md).
+++

<!--
----ACS?----
+++**Localization**

This template type is used to manage multilingual messages.  It is available for Email and SMS messages and useable in standalone mode, within a workflow or in a recurring delivery. In the multilingual feature templates, the language management is based on variants. Each variant represents one language.  This functionality is available only in Adobe Campaign Standard.  
+++
-->

+++**명명된 권한**

운영자 그룹 액세스 및 권한(롤)을 정의하는 데 사용되는 세분화된 데이터베이스 액세스 권한입니다. 명명된 권한은 제품 설치 중에, 도구의 특정 기능을 정의하는 다양한 패키지를 가져와서 채워집니다. 클라이언트 비즈니스 요구 사항을 지원하도록 사용자 지정 명명된 권한을 만들 수 있습니다.

자세히 알아보기 [명명된 권한](../../platform/using/access-management-named-rights.md).
+++

+++**네임스페이스**

네임스페이스는 데이터 모델에서 고객 데이터 유형을 Adobe Campaign의 기본 데이터 유형과 구분하는 파티션입니다. 개발 인스턴스에서 프로덕션 인스턴스로 스키마 또는 템플릿을 이동하는 것과 같이 한 인스턴스에서 다른 인스턴스로 정의를 쉽게 마이그레이션하는 데에도 사용됩니다.

자세히 알아보기 [네임스페이스](../../configuration/using/about-schema-reference.md#identification-of-a-schema).
+++

<!--
----generic, not specific to campaign----
+++**Navigation bar**

The navigation bar is the navigation element running across the top of the interface. The navigation bar regroups the various core capabilities of the platform. Click a navigation bar link to display the set of functionalities related to this capability. The list of core capabilities you can access depends on the packages and add-ons you have installed and on your access rights. The purpose of the Navigation bar is to simplify screen management and increase productivity.

Learn more about [Navigation Bar](../../platform/using/adobe-campaign-workspace.md#browsing-pages).
+++
-->

+++**탐색 트리**

탐색 트리는 Adobe Campaign의 Explorer 보기에서 기본 탐색입니다. 탐색 트리는 파일 브라우저(예: Windows 탐색기)처럼 작동합니다. 폴더에는 하위 폴더가 포함될 수 있습니다. 노드를 선택하면 해당 노드에 해당하는 보기가 표시됩니다. 표시된 보기는 선택한 줄을 편집하기 위한 스키마 및 입력 양식과 관련된 목록입니다. 탐색 트리를 사용자 정의하고 폴더에 대한 권한을 설정할 수 있습니다.

자세히 알아보기 [탐색 트리](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarch).
+++

+++**목표**

*컨텍스트: 마케팅 리소스 관리(MRM)*

캠페인, 프로그램 또는 계획 내에서 운영자는 목표 목록을 표시할 수 있습니다. 도달할 수량화된 값입니다. 캠페인, 프로그램 또는 계획이 끝날 때 MRM 모듈을 사용하여 운영자는 전용 보고서에서 목표와 결과를 비교할 수 있습니다.

자세히 알아보기 [목표](../../mrm/using/creating-and-managing-tasks.md#expenses-and-revenues).
+++

+++**오퍼 카탈로그**

*컨텍스트: 캠페인 상호 작용*

오퍼 카탈로그는 Adobe Campaign에 정의된 오퍼 세트로 상호 작용 중에 선택할 수 있습니다. 카탈로그는 카테고리에 해당하는 각 노드와 계층적으로 구성됩니다.

자세히 알아보기 [오퍼 카탈로그](../../interaction/using/offer-catalog-overview.md).
+++

+++**오퍼 연락처**

*컨텍스트: 캠페인 상호 작용*

오퍼 연락처는 인바운드 상호 작용의 연락처입니다. 엔진 호출 처리 중에 연락처는 타겟팅 차원과 연결됩니다. 식별되지 않는 익명의 연락처는 방문자 타겟팅 차원으로 인한 것입니다. 연락처에는 식별과 익명의 두 가지 유형이 있습니다.

* **확인된 연락처**: 채널에서 자발적으로 식별된 연락처. 아웃바운드 상호 작용에서 연락처는 자동으로 식별됩니다.
* **익명 연락처**: 채널을 통해 자발적으로 구독한 것은 아니지만 쿠키를 통해 암묵적으로 식별할 수 있는 연락처입니다. 이 용어는 수신 상호 작용에만 사용됩니다.

자세히 알아보기 [상호 작용](../../interaction/using/interaction-and-offer-management.md).
+++

+++**오퍼 디자인 환경**

*컨텍스트: 캠페인 상호 작용*

오퍼 **디자인 환경** 은 운영자가 오퍼를 만들고 유형화 규칙을 정의하고 오퍼가 타깃팅할 스키마를 선택하는 환경입니다. 생성된 오퍼 제안을 저장하는 테이블은 환경에 의해서도 정의됩니다. 기본적으로 상호 작용 추가 기능에는 **디자인** 환경 및 **라이브** 연결된 환경입니다. 두 환경 모두 기본 제공 수신자 테이블을 타깃팅하도록 사전 구성되어 있습니다.

자세히 알아보기 [오퍼 디자인 환경](../../interaction/using/fundamental-principles.md).
+++

+++**오퍼 엔진 차익**

*컨텍스트: 캠페인 상호 작용*

오퍼 엔진은 환경에 표시될 오퍼를 선택합니다(적격 오퍼). 차익거래 원칙은 범주 및 오퍼에 정의된 기준에 따라 우선 순위별로 오퍼에 순위를 매긴다.

자세히 알아보기 [상호 작용](../../interaction/using/interaction-and-offer-management.md).
+++

+++**오퍼 엔진 정리**

*컨텍스트: 캠페인 상호 작용*

오퍼 엔진 정리는 선택에 적합하지 않은 오퍼를 삭제하는 프로세스입니다. 오퍼 엔진 중재 단계 전에 실행됩니다.

자세히 알아보기 [상호 작용](../../interaction/using/interaction-and-offer-management.md).
+++

+++**오퍼 환경**

*컨텍스트: 캠페인 상호 작용*

오퍼 환경은 오퍼 카탈로그, 사용 가능한 공간 및 환경의 사전 정의된 필터를 정의하는 루트 폴더입니다. 연산자는 각 타겟팅 차원에 대해 하나의 환경을 생성해야 합니다. 오퍼 환경에는 디자인과 라이브의 두 가지 유형이 있습니다.

자세히 알아보기 [오퍼 환경](../../interaction/using/fundamental-principles.md).
+++

+++**오퍼 라이브 환경**

*컨텍스트: 캠페인 상호 작용*

오퍼 라이브 환경이 Campaign에 연결되어 있습니다 **디자인 환경**. 여기에는 를 통해 콘텐츠 및 자격이 승인된 읽기 전용 오퍼가 포함되어 있습니다. **디자인 환경**. 웹 사이트에 프레젠테이션하거나 아웃바운드 메시지에 삽입하도록 선택할 수 있습니다.

자세히 알아보기 [오퍼 라이브 환경](../../interaction/using/fundamental-principles.md).
+++

+++**오퍼 표시 규칙**

*컨텍스트: 캠페인 상호 작용*

오퍼 표시 규칙은 오퍼 환경에서 참조되는 유형화 규칙이며, 이를 통해 운영자는 수신자의 제안 내역을 고려하여 특정 오퍼를 제외할 수 있습니다.

자세히 알아보기 [오퍼 표시 규칙](../../interaction/using/managing-offer-presentation.md#presentation-rules-overview).
+++

+++**오퍼 미리보기**

*컨텍스트: 캠페인 상호 작용*

폴더에 표시되는 오퍼의 미리보기입니다. 오퍼 미리보기 탭 또는 연락처 프로필에서 액세스할 수 있습니다.

자세히 알아보기 [오퍼 미리보기](../../interaction/using/creating-an-offer.md#previewing-the-offer).
+++

+++**오퍼 제안**

*컨텍스트: 캠페인 상호 작용*

오퍼 제안은 주어진 오퍼 공간(예: 웹 사이트의 배너, 이메일 또는 SMS 콘텐츠)에서 담당자에게 오퍼를 제시하는 것으로 구성된 작업의 결과입니다. 이 결과는 오퍼, 수신자 및 타임스탬프를 정의하는 오퍼 제안 테이블에 저장되며, 수신자가 받은 모든 오퍼에 대한 레코드를 제공합니다.

자세히 알아보기 [오퍼 제안](../../interaction/using/creating-offer-spaces.md#offer-proposition-statuses).
+++

+++**오퍼 표시**

*컨텍스트: 캠페인 상호 작용*

오퍼 표현은 오퍼를 표시하기 위해 채널에서 사용하는 정보입니다. 오퍼 표현은 오퍼가 표현되거나 (예를 들어, HTML 블록에서) 인터페이스에 직접 입력된 공간의 렌더링 함수로부터 구성될 수 있다. 오퍼는 공백으로 표시될 수 있습니다.

자세히 알아보기 [상호 작용](../../interaction/using/interaction-and-offer-management.md).
+++

+++**오퍼 시뮬레이션**

*컨텍스트: 캠페인 상호 작용*

오퍼 시뮬레이션을 사용하면 운영자가 정의된 범위(게재 날짜, 타겟 세그먼트, 오퍼 수, 테마 등)에 걸쳐 오퍼 배포를 테스트할 수 있습니다. 오퍼를 실제로 보내기 전에. 오퍼 효율성을 극대화하기 위해 오퍼 우선 순위 및 자격 규칙을 조정하는 데 사용할 수 있습니다.

자세히 알아보기 [오퍼 시뮬레이션](../../interaction/using/about-offers-simulation.md).
+++

+++**오퍼 공간**

*컨텍스트: 캠페인 상호 작용*

오퍼 공간은 오퍼가 노출되는 위치를 정의하는 폴더입니다. 공간을 정의하면 사용되는 채널을 지정하고, 오퍼의 콘텐츠를 작성하고, 제공된 오퍼를 지정할 수 있습니다. 오퍼 공간은 채널과 오퍼 엔진 간의 인터페이스입니다.

자세히 알아보기 [오퍼 공간](../../interaction/using/creating-offer-spaces.md).
+++

+++**오퍼 테마**

*컨텍스트: 캠페인 상호 작용*

오퍼 테마는 카테고리에 정의된 키워드이며, 이를 통해 운영자는 오퍼가 표시될 때 오퍼를 필터링할 수 있습니다. 테마를 사용하면 카탈로그 구조에서 오퍼를 계층적이지 않게 선택할 수 있습니다.

자세히 알아보기 [오퍼 테마](../../interaction/using/integrating-an-offer-via-the-wizard.md).
+++

+++**오퍼 가중치**

*컨텍스트: 캠페인 상호 작용*

오퍼 가중치는 엔진에서 가장 연관성이 높은 오퍼를 선택할 수 있도록 오퍼의 관련성을 정확하게 정의하는 수식을 기반으로 합니다. 가중치는 오퍼에 정의되어 있으며 승수는 카테고리에 정의되어 있습니다. 적격 오퍼는 체중 감소 순서로 고려됩니다.

자세히 알아보기 [오퍼 가중치](../../interaction/using/creating-an-offer.md#offer-weight).
+++

+++**운영자**

운영자는 로그인하고 작업을 수행할 수 있는 권한이 있는 Adobe Campaign 사용자입니다. 연산자는 연산자 그룹과 연결되고 이러한 그룹의 권한과 권한을 상속합니다. 명명된 권한을 연산자에 직접 지정할 수도 있습니다.

자세히 알아보기 [연산자](../../platform/using/access-management-operators.md).
+++

+++**운영자 그룹**

연산자 그룹을 사용하면 Campaign 연산자의 역할을 관리할 수 있습니다. 권한을 지정할 연산자 그룹을 정의한 다음 연산자를 하나 이상의 그룹에 연결합니다. 이렇게 하면 권한을 재사용하고 운영자 프로필을 보다 일관되게 만들 수 있습니다. 또한 프로필 관리 및 유지 관리를 용이하게 합니다.

자세히 알아보기 [연산자 그룹](../../platform/using/access-management-groups.md).
+++

+++**옵션**

옵션은 Campaign 인스턴스의 설정을 정의하는 데 사용되는 플랫폼 수준 변수입니다. 옵션은 플랫폼 수준에서 시간대(예: 데이터베이스 정리 워크플로우)나 기타 전역 정의를 정의할 수 있습니다.

자세히 알아보기 [옵션](../../installation/using/configuring-campaign-options.md).
+++

+++**아웃바운드 상호 작용**

*컨텍스트: 캠페인 상호 작용*

아웃바운드 상호 작용은 연락처 목록에서 상호 작용 엔진에 대한 호출입니다(이메일, DM 등을 게재하는 데 사용됨). 각 연락처에 대해 동일한 규칙과 프로세스가 적용됩니다. 이러한 유형의 상호 작용은 일반적으로 배치 모드에서 처리됩니다.

자세히 알아보기 [아웃바운드 상호 작용](../../interaction/using/about-outbound-channels.md).
+++

+++**패키지 내보내기/가져오기**

패키지 내보내기는 객체 정의가 포함된 XML 파일 생성에서 이루어지는 작업입니다. 패키지는 기능 및 정의를 한 인스턴스에서 다른 인스턴스로 마이그레이션하는 데 사용됩니다. 또한 백업 및 소스 제어 시스템에 중요한 제품 정의를 추가하는 데에도 사용됩니다.

자세히 알아보기 [패키지 내보내기/가져오기](../../platform/using/working-with-data-packages.md).
+++

+++**팔레트**

워크플로우 팔레트에는 워크플로우에 추가할 수 있는 사용 가능한 활동이 표시됩니다. 이 구성 요소는 사용에 따라 논리적으로 그룹화된 워크플로우 활동과 함께 탭 형식으로 표시됩니다. 팔레트에서 사용할 수 있는 활동은 Campaign 인스턴스에 설치된 추가 기능과 워크플로를 표시하는 컨텍스트에 따라 결정됩니다.

자세히 알아보기 [팔레트](../../workflow/using/building-a-workflow.md#adding-and-linking-activities).
+++

+++**성능 모니터링**

성능 모니터링 정보가 모니터링 탭에 표시됩니다. 메모리 및 CPU 사용량, SMTP 서버 통계, 서버 프로세스 및 기타 관련 정보와 같은 기본 시스템에 대한 지표를 표시합니다.

자세히 알아보기 [성능 모니터링](../../production/using/monitoring-processes.md).
+++

+++**개인화 블록**

Adobe Campaign은 게재에 삽입할 수 있는 기본 제공 개인화 블록을 제공합니다. 동적, 개인화된 기능이며 특정 렌더링을 포함합니다. 예를 들어 미러 페이지에 로고, 인사말 메시지 또는 링크를 추가할 수 있습니다. 기본적으로 여러 개인화 블록을 사용할 수 있습니다. 게재 개인화를 최적화할 수 있는 사용자 지정 개인화 블록을 정의할 수도 있습니다. 실제 데이터는 게재의 분석 단계 동안 생성된 각 메시지에 삽입됩니다.

자세히 알아보기 [개인화 블록](../../delivery/using/personalization-blocks.md).
+++

+++**개인화 필드**

개인화 필드는 특정 수신자에 대한 게재를 개인화할 때 사용되는 단일 데이터 필드 참조입니다. 게재 분석 단계 중에 실제 데이터 값이 삽입됩니다.

자세히 알아보기 [개인화 필드](../../delivery/using/personalization-fields.md).
+++

+++**개인화 변수**

개인화 변수는 수신자의 정보를 기반으로 다양한 수신자에게 다양한 텍스트를 표시할 수 있는 게재의 코드 조각입니다. 이러한 필드는 개인화 필드 또는 블록으로 구현할 수 있습니다.

자세히 알아보기 [개인화 변수](../../delivery/using/about-personalization.md).
+++

+++**플랜**

플랜은 달력을 기준으로 마케팅 활동을 구성하는 데 사용되는 폴더 유형입니다. 탐색기 보기의 계획 폴더는 연도, 분기 또는 월과 같은 시간 기반 단위를 정의합니다. 계획 폴더는 중첩될 수 있으며 다른 계획 폴더, 프로그램 폴더 또는 캠페인을 포함할 수 있습니다.

자세히 알아보기 [플랜](../../campaign/using/setting-up-marketing-campaigns.md).
+++

+++**사전 정의된 필터**

사전 정의된 필터는 다시 사용하기 위해 저장된 쿼리입니다. 사전 정의된 필터를 사용하면 생산성을 높이고(한 번만 만들어지기 때문에), 일관성을 구축하는 데 도움을 주고(모든 마케터가 사용할 수 있기 때문에), 자신을 만들지 못할 수 있는 코드나 논리를 사용할 수 있기 때문에 마케터에게 필요한 기술을 낮출 수 있습니다.

자세히 알아보기 [사전 정의된 필터](../../platform/using/creating-filters.md#filtering-recipients).
+++

<!--
----DEPRECATED----
+++**Predictive Engagement Scoring**

Predictive engagement scoring predicts the probability of a recipient engaging with a message and the probability of opting out (unsubscribing) within the next seven days after the next email send. The probabilities are further divided into buckets according to the specific risk of disengagement, medium, or low. The model also provides the risk percentile rank for the customers to understand where the rank of a certain customer in relation to others. 

Learn more about [Predictive Engagement Scoring](../../platform/using/creating-filters.md).
+++
-->

+++**기본 키**

기본 키는 데이터베이스 테이블의 각 레코드에 대한 고유 식별자입니다. 테이블에는 하나 이상의 키가 있어야 합니다. 일반적으로 키는 스키마의 기본 요소와 인덱스 뒤에 선언됩니다. 기본 키는 합성 키가 될 수 없습니다(여러 필드를 포함).

자세히 알아보기 [기본 키](../../configuration/using/schema/key.md).
+++

+++**프로필**

프로필은 최종 고객, 잠재 고객 또는 잠재 고객을 나타내는 정보 레코드입니다. 각 프로필은 쿠키 ID, 고객 ID, 모바일 식별자 또는 특정 채널과 관련된 기타 정보가 포함된 외부 테이블 또는 nmsRecipient 테이블의 레코드에 해당합니다.

자세히 알아보기 [프로필](../../platform/using/about-profiles.md).
+++

+++**프로그램**

프로그램 및 하위 프로그램 폴더는 충성도, 획득 또는 크로스셀과 같은 비즈니스 목표에 대한 마케팅 활동을 구성합니다. 또한 회계 기간 또는 캠페인 전술(예: 이벤트 또는 뉴스레터)을 나타낼 수 있습니다. 각 프로그램에는 전체 보기를 제공하는 달력에 연결된 캠페인이 포함되어 있습니다.

자세히 알아보기 [프로그램](../../campaign/using/setting-up-marketing-campaigns.md).
+++

+++**퍼블릭 리소스**

Adobe Campaign의 공개 리소스 폴더에는 애플리케이션 서버가 호스팅하는 이미지가 들어 있습니다. 게재의 이미지는 이메일과 같은 게재에 표시되려면 애플리케이션 서버(또는 Campaign이 이렇게 구성된 경우 이미지 호스팅 서버)에 게시되어야 합니다.

자세히 알아보기 [공개 리소스](../../installation/using/deploying-an-instance.md#managing-public-resources).
+++

+++**푸시**

*컨텍스트: 모바일 앱 채널*

푸시 알림은 모바일 애플리케이션에서 수신하는 메시지입니다. 푸시 알림은 모바일 애플리케이션에 Experience Platform SDK 코드를 포함하여 Adobe Campaign에서 작동하도록 구성됩니다. 푸시의 경우 iOS 및 Android의 두 가지 게재 채널을 사용할 수 있습니다.

자세히 알아보기 [푸시](../../delivery/using/about-mobile-app-channel.md).
+++

## Q - T {#sec-5}

+++**수신자**

Adobe Campaign에서 수신자는 게재(이메일, SMS 등)를 전송할 타겟팅된 기본 프로필입니다 고객에게 전달합니다. 데이터베이스에 저장된 수신자 데이터를 사용하면 타겟을 필터링하고 개인화 데이터를 추가할 수 있습니다. 일반적으로 개인, 연락처, 인구 통계학적 및 트랜잭션 정보이지만, 마케팅 및 분석을 지원하는 모든 유형의 정보일 수 있습니다.

자세히 알아보기 [수신자](../../configuration/using/about-data-model.md).
+++

+++**렌더링 기능**

*컨텍스트: 캠페인 상호 작용*

렌더링 함수는 오퍼 공간에서 정의됩니다. 오퍼에 정의된 속성을 기반으로 오퍼 표현을 구성하는 데 사용됩니다. 렌더링 함수 모드에는 HTML, XML 및 텍스트의 세 가지가 있습니다.

자세히 알아보기 [렌더링 기능](../../interaction/using/creating-offer-spaces.md).
+++

<!--
-----DID NOT FIND IN ACC DOCS, ACS?----
+++**Retargeting campaigns**

Campaigns that re-target the recipients of a previous delivery or deliveries.
+++
-->

+++**스키마**

스키마는 데이터베이스 테이블과 연관된 XML 문서입니다. 데이터 구조를 정의하고 테이블의 SQL 정의를 설명합니다. 연산자가 Campaign에서 스키마를 조작하면 제품이 작업을 필요한 SQL로 변환한 다음 데이터베이스에 대해 실행됩니다.

자세히 알아보기 [스키마](../../configuration/using/about-schema-reference.md).
+++

+++**스키마 확장**

스키마 확장을 사용하면 비즈니스 사용 사례에 가장 적합하게 기본 제공 스키마를 사용자 지정할 수 있습니다. 예를 들어 &quot;충성도&quot; 필드를 수신자 표에 추가할 수 있습니다.

자세히 알아보기 [스키마 확장](../../configuration/using/extending-a-schema.md).
+++

+++**시드 주소**

시드 주소는 정의된 대상 기준과 일치하지 않는 수신자를 타겟팅 하는 데 사용됩니다. 이렇게 하면 게재 범위를 벗어난 수신자는 다른 대상 수신자와 마찬가지로 게재를 받을 수 있습니다. 수신자 데이터베이스의 부정 사용을 감지하거나 게재를 보장하기 위해 메시지 대상자에 추가됩니다.

자세히 알아보기 [시드 주소](../../delivery/using/about-seed-addresses.md).
+++

<!--
-------ACS?-----
+++**Send-time optimization**

To improve the open rate of your messages, you can manually define a sending time per recipient. Each profile will receive the message at the specified date and time, whenever possible. Defining a sending time can be done at the delivery level or using a workflow.

Learn more about [Send-time optimization](../../delivery/using/about-seed-addresses.md:).
+++
-->

+++**서비스**

Adobe Campaign을 사용하면 뉴스레터 또는 제품 업데이트와 같은 정보 서비스를 만들고 관리하고 이러한 서비스에 대한 구독을 관리할 수 있습니다. 여러 서비스를 동시에 정의할 수 있습니다.

자세히 알아보기 [서비스](../../delivery/using/about-services-and-subscriptions.md).
+++

+++**SFTP 관리**

컨트롤 패널에서 액세스 권한이 있는 Campaign 인스턴스에 연결된 모든 SFTP 서버와 상호 작용할 수 있습니다. 컨트롤 패널에서는 스토리지 용량 모니터링, IP 주소 관리 허용 목록 및 공개 SSH 키 관리와 같은 작업을 SFTP 서버에 수행할 수 있습니다.

자세히 알아보기 [SFTP 관리](https://experienceleague.adobe.com/docs/control-panel/using/sftp-management/about-sftp-management.html).
+++

+++**구독 서비스 활동**

구독 서비스 워크플로우 활동을 사용하면 전환에 지정된 모집단에 대한 정보 서비스 구독을 만들거나 삭제할 수 있습니다.

자세히 알아보기 [구독 서비스 활동](../../workflow/using/subscription-services.md).
+++

+++**대상 승인**

*컨텍스트: Campaign 분산 마케팅*

Target 승인은 게재를 보내기 전에 (분석 단계에서 타겟이 생성된 후) 별도의 운영자 또는 운영자 그룹이 게재의 최종 타겟을 승인하도록 하는 프로세스입니다.

자세히 알아보기 [Target 승인](../../workflow/using/local-approval.md).
+++

+++**타겟 데이터**

Target 데이터는 워크플로우의 작업 테이블(전환)에 저장된 데이터입니다. 이 데이터는 게재 콘텐츠를 개인화하거나 게재의 동적 요소 논리를 정의하는 데 게재 내에서 사용할 수 있습니다.

자세히 알아보기 [Target 데이터](../../workflow/using/data-life-cycle.md#target-data).
+++

+++**대상 매핑**

Target 매핑은 게재 채널을 특정 데이터 유형에 매핑하는 것입니다. Target 매핑은 서로 다른 게재 채널이 스키마의 데이터 필드에 연결되는 방식을 정의합니다. Campaign에서 특정 필드 또는 표현식을 사용하여 해당 데이터 유형으로 보내는 방법을 정의합니다.

자세히 알아보기 [대상 매핑](../../delivery/using/selecting-a-target-mapping.md).
+++

+++**타겟팅 활동**

타겟팅 활동은 타겟팅, 모집단 데이터 조작 및 필터링 활동과 관련된 워크플로우 활동입니다. 이를 통해 연산자는 세트를 정의하고 교차, 결합 또는 제외 작업을 사용하여 이러한 세트를 분할 또는 결합하여 하나 이상의 대상을 작성할 수 있습니다.

자세히 알아보기 [타겟팅 활동](../../workflow/using/about-targeting-activities.md).
+++

+++**대상 차원**

타겟팅 차원은 쿼리 또는 기타 워크플로우 활동에 의해 생성(반환)되는 데이터 유형입니다. Adobe Campaign은 데이터베이스 행을 가져오는 데 사용된 쿼리에 관계없이 응답자 데이터베이스 행의 기본 키만 반환합니다.

자세히 알아보기 [타겟팅 차원](../../workflow/using/targeting-data.md).
+++

+++**작업 활동**

*컨텍스트: 마케팅 리소스 관리(MRM)*

작업 워크플로우 활동은 사람 작업을 워크플로우의 논리에 통합합니다. 작업이 완료되면 첫 번째 시나리오와 작업이 완료되지 않으면 두 번째 시나리오를 지정할 수 있습니다. 일반적인 사용 사례는 오프라인 작업을 캠페인에 통합하거나 승인과 같은 사용자 지정 작업에 사용됩니다.

자세히 알아보기 [작업 활동](../../workflow/using/task.md).
+++

<!--
-----NOT USEFUL, detail-----
+++**Task**

One iteration of the defined functionality of a workflow activity. Each execution of a task has a unique task identifier.   

Learn more about [Tasks](../../workflow/using/about-workflows.md).
+++
-->

+++**템플릿**

템플릿은 개체를 만드는 데 사용되는 디자인 요소입니다. 여기에는 개체 설정과 개체 내용(선택 사항)이 포함됩니다. 템플릿 시스템은 게재, 캠페인, 워크플로우 및 Adobe Campaign의 다양한 기타 요소를 만드는 데 사용됩니다. 사용 가능한 공장 템플릿은 설치된 패키지에 의해 정의됩니다. 그런 다음 캠페인 운영자가 필요에 따라 템플릿을 복제하고 사용자 정의할 수 있습니다.
+++

<!--
-----ACS -> SEEDS IN ACC-----
+++**Test profiles**

Allows targeting of additional recipients who do not match the defined targeting criteria. They are added to a message’s audience to detect any fraudulent use of your recipient database or to ensure delivery. Seen as the Seed type in the Campaign interface.

Learn more about [Test profiles](../../workflow/using/about-workflows.md).
+++
-->

<!--
-----NOT FOR DOCS?-----
+++**Total database storage**

The aggregate size of the production and non-production instance(s) database storage managed by Adobe. 

Learn more about [Total database storage](../../workflow/using/about-workflows.md).
+++
-->

+++**추적 로그**

추적 기술 워크플로우는 게재가 전송되고 추적이 활성화되면 추적 데이터를 검색합니다. 이 데이터는 게재의 추적 탭에서 찾을 수 있습니다. 이메일의 열람 및 클릭 또는 수신자가 받은 메시지와의 기타 상호 작용에 대한 정보를 찾을 수 있습니다.

자세히 알아보기 [추적 로그](../../delivery/using/accessing-the-tracking-logs.md).
+++

+++**트랜잭션 메시지**

트랜잭션 메시지는 외부 정보 시스템에서 보낸 이벤트에서 생성된 사용자 지정 트리거 알림을 관리하기 위해 설계된 Campaign 모듈입니다. 트랜잭션 메시지는 웹 사이트와 같은 공급자가 실시간으로 전송하는 개별적이고 고유한 통신입니다. 수신자가 확인하거나 확정하려는 중요한 정보가 포함되어 있기 때문에 특히 기대됩니다.

자세히 알아보기 [트랜잭션 메시지](../../message-center/using/about-transactional-messaging.md).
+++

&lt;!-------은 ??----->
+++**트리거된 캠페인**

트리거된 캠페인은 워크플로우에서 API 요청을 받을 때 실행되는 캠페인입니다. API 호출은 워크플로우 실행을 시작하는 워크플로우의 신호 활동에서 사용됩니다.

자세히 알아보기 [트리거된 캠페인](../../workflow/using/external-signal.md).
+++

<!--
-----NOT USEFUL-----
+++**Triggers**

Signals that initiate execution of a workflow, delivery or other action. Typically an API call. 

Learn more about [Triggers](../../workflow/using/about-workflows.md).
+++
-->

+++**유형화**

*컨텍스트: 캠페인 최적화*

유형화는 게재의 분석 단계에 적용되는 유형화 규칙의 그룹입니다. 캠페인 유형화에는 여러 유형화 규칙이 포함될 수 있지만, 게재는 하나의 유형화만 참조할 수 있습니다.

자세히 알아보기 [유형화](../../campaign-opt/using/about-campaign-typologies.md#typologies).
+++

+++**유형화 규칙**

*컨텍스트: 캠페인 최적화*

유형화 규칙은 게재 분석 단계의 일부로 구현되는 비즈니스 규칙입니다. 유형화 규칙은 게재 내용(제어 규칙) 또는 게재 대상(필터링 규칙) 또는 비즈니스 요구 사항을 적용하는 기타 논리(압력 규칙)를 확인하는 것입니다. 규칙은 하나 이상의 유형화에 포함할 수 있는 세분화된 요소입니다.

자세히 알아보기 [유형화 규칙](../../campaign-opt/using/about-campaign-typologies.md#typology-rules).
+++

## U - Z {#sec-6}

+++**단일 모드**

*컨텍스트: 캠페인 상호 작용, 트랜잭션 메시지*

단일 모드에서 단일 연락처는 런타임 시 오퍼 엔진에 의해 처리됩니다. 이 모드는 일반적으로 인바운드 상호 작용 및 트랜잭션 메시지에 사용됩니다.

자세히 알아보기 [단일 모드](../../interaction/using/about-inbound-channels.md).
+++

<!--
-----NO OCCURRENCE IN ACC, OLD v6 CONCEPT?
+++**Universes**

Application pages hosted by the Campaign instance. Used for approval forms, landing pages, opt-out forms, preference pages or to implement other business requirements.  

Learn more about [Universes](../../workflow/using/about-workflows.md).
+++
------>

+++**웹 애플리케이션**

웹 애플리케이션은 Campaign 인스턴스가 호스팅하는 동적 및 대화형 애플리케이션 페이지입니다. 여기에는 데이터베이스의 데이터와 연결된 사용자의 권한에 맞는 콘텐츠가 포함되어 있습니다. 예를 들어 엑스트라넷에 대한 편집 양식 또는 테이블, 차트, 입력 양식 등이 있는 데이터베이스의 데이터를 포함하는 알림 양식을 만들 수 있습니다. 이 기능을 사용하면 사용자가 정보를 조회하거나 입력할 수 있는 웹 페이지를 디자인하고 게시할 수 있습니다.

자세히 알아보기 [웹 애플리케이션](../../web/using/about-web-applications.md).
+++

+++**워크플로우**

워크플로우는 캠페인 실행 흐름을 시각적으로 표현한 것입니다. 애플리케이션 서버의 여러 모듈에 걸쳐 전체 프로세스 및 작업을 오케스트레이션할 수 있습니다. 이 포괄적인 그래픽 환경을 사용하면 세분화, 캠페인 실행, 파일 처리, 인력 참여 등의 프로세스를 디자인할 수 있습니다. 워크플로우 엔진은 이러한 프로세스를 실행하고 추적합니다.

자세히 알아보기 [워크플로](../../workflow/using/about-workflows.md).
+++

+++**워크플로우 저널**

워크플로우 저널은 워크플로우의 단계별 실행 로그입니다. 여기에는 워크플로우의 모든 내역 또는 감사 추적이 포함됩니다. 개발, 문제 해결 또는 디버그 목적으로 사용됩니다.

자세히 알아보기 [워크플로우 저널](../../workflow/using/monitoring-workflow-execution.md).
+++

+++**작업대**

작업 테이블에는 워크플로우 전환으로 전달되는 모든 정보가 들어 있습니다. 각 워크플로는 여러 작업 테이블을 사용합니다. 작업 테이블은 원래 활동의 결과를 보관하며, 해당 콘텐츠는 워크플로우의 다음 (연결된) 활동에 대한 입력으로 사용됩니다.  작업 테이블의 조작(확장, 사용자 지정)은 Adobe Campaign 연산자의 주요 기술 중 하나입니다.

자세히 알아보기 [작업대](../../workflow/using/about-workflows.md).
+++
