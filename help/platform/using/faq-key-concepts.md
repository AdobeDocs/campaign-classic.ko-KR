---
title: 주요 개념
description: Campaign Classic FAQ
page-status-flag: never-activated
uuid: 3f719ac2-cc26-4fb0-adda-84666c8c38e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 16dbe423-018f-4666-9901-2120a8dc609a
translation-type: ht
source-git-commit: cb96a238f4c8e413377ce6102b065b91badfe6db
workflow-type: ht
source-wordcount: '887'
ht-degree: 100%

---


# 주요 개념 {#key-concepts}

Adobe Campaign으로 시작하는 주요 단계를 배웁니다.

## Adobe Id로 Campaign Classic에 연결할 수 있습니까? {#can-i-connect-to-campaign-classic-with-an-adobe-id-}

IMS(Adobe Identity Management 시스템)와의 통합 덕분에 사용자는 Adobe ID을 사용하여 Adobe Campaign 콘솔에 연결할 수 있습니다. 이 통합은 다음과 같은 이점을 제공합니다.

*  모든 Experience Cloud 솔루션에 동일한 ID를 사용할 수 있습니다.
* 서로 다른 통합으로 Adobe Campaign을 사용하는 경우 연결이 기억됩니다.
* 보안 암호 관리 정책.
* 페더레이션 ID 계정 사용(외부 ID 공급자).

Adobe ID을 사용하여 Campaign Classic에 액세스하는 방법에 대한 [자세한 내용을 보려면 여기를 클릭하십시오](../../integrations/using/about-adobe-id.md).

## Campaign의 버전은 무엇입니까? {#what-is-my-version-of-campaign-}

Campaign 클라이언트 콘솔의 **도움말 > 정보...[ 메뉴에서 버전 및 빌드 번호](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)를** 확인합니다.

## 온프레미스 및 호스팅 환경에서 작업하는 경우의 차이점은 무엇입니까? {#what-are-the-differences-when-working-on-premise-vs--in-a-hosted-environment-}

Adobe Campaign Classic에는 모듈 및 옵션 세트가 포함되어 있습니다. 이러한 모듈 및 구성 가용성은 설치 [배포 유형](../../installation/using/hosting-models.md)이 호스팅(Managed Services), hybrid 또는 온프레미스인지에 따라 달라질 수 있습니다.

[자세한 내용을 보려면 여기를 클릭하십시오](../../installation/using/capability-matrix.md).

## 사용자 권한을 설정하려면 어떻게 해야 합니까? {#how-can-i-set-up-user-permissions-}

Campaign 관리자는 조직의 사용자에 대한 권한을 설정할 수 있습니다.

다음은 권한을 부여하거나 거부한 권한 및 제한 세트입니다.

* 특정 기능에 액세스하고
* 특정 데이터에 액세스하며
* 데이터 만들기, 수정 및/또는 삭제합니다.

사용자 권한에 대한 [자세한 내용을 보려면 여기를 클릭하십시오](../../platform/using/access-management.md).

## Campaign을 통한 개인 정보 보호 규정 준수 방법 {#how-to-be-gdpr-compliant-with-campaign-}

Adobe Campaign은 GDPR 및 CCPA에 대한 개인 정보 보호 규정을 준수하는 데 도움이 되는 도구를 제공합니다.

Adobe 서비스를 사용할 때 GDPR 준수를 위해 Adobe Campaign이 제공하는 도구와 기능 및 모범 사례를 살펴보려면 [이 문서를](https://helpx.adobe.com/kr/campaign/kb/campaign-privacy-overview.html) 참조하십시오. Campaign Classic에 대한 구현 단계는 [이 문서](https://helpx.adobe.com/kr/campaign/kb/acc-privacy.html)에 설명되어 있습니다.

## 알아야 하는 Campaign 사용자 인터페이스 개념은 무엇입니까? {#what-are-campaign-user-interface-concepts-i-should-know-}

Adobe Campaign 작업 영역의 기본 사항에 대한 자세한 내용은 [이 섹션을](../../platform/using/adobe-campaign-workspace.md) 참조하십시오.

![](assets/do-not-localize/how-to-video.png) [비디오에서 캠페인 작업 영역 살펴보기](https://docs.adobe.com/content/help/ko-KR/campaign-classic-learn/tutorials/getting-started/exploring-the-adobe-campaign-classic-user-interface.html)

## 메시지 대상자를 선택하려면 어떻게 해야 합니까? {#how-can-i-select-the-target-population-of-my-messages-}

Adobe Campaign을 사용하면 다양한 전략을 사용하여 대상을 만들고 대상 수신자를 선택할 수 있습니다.

[자세한 내용을 보려면 여기를 클릭하십시오](../../delivery/using/steps-defining-the-target-population.md).

## 워크플로우란 무엇입니까? {#what-is-a-workflow-}

Adobe Campaign에는 애플리케이션 서버의 여러 모듈에 걸쳐 전체 프로세스 및 작업을 오케스트레이션하는 워크플로우가 포함되어 있습니다. 이 포괄적인 그래픽 환경을 사용하면 세분화, 캠페인 실행, 파일 처리, 인력 참여 등의 프로세스를 디자인할 수 있습니다. 워크플로우 엔진은 이러한 프로세스를 실행하고 추적합니다.

예를 들어 워크플로우에서 서버에서 파일을 다운로드하고 압축을 해제한 다음 Adobe Campaign 데이터베이스에 포함된 레코드를 가져올 수 있습니다.

워크플로우에는 알림을 받거나 프로세스를 선택하고 승인할 수 있는 운영자가 한 명 이상 포함될 수도 있습니다. 이러한 방식으로 게재 작업을 만들고, 콘텐츠를 사용하여 작업하도록 한 명 이상의 운영자에게 작업을 할당하고, 대상을 지정하고, 게재를 시작하기 전에 증명을 승인할 수 있습니다.

워크플로우에 대한 [자세한 내용을 살펴보려면 여기를 클릭하십시오](../../workflow/using/about-workflows.md). 또한 [워크플로우 모범 사례](../../workflow/using/building-a-workflow.md)를 참조할 수 있습니다.

## 첫 번째 전자 메일을 만들고 보내는 방법 {#how-to-create-and-send-a-first-email-}

[자세한 내용을 보려면 여기를 클릭하십시오](../../delivery/using/about-email-channel.md).

![](assets/do-not-localize/how-to-video.png) [비디오에서 이 방법 살펴보기](https://docs.adobe.com/content/help/ko-KR/campaign-classic-learn/tutorials/getting-started/creating-a-campaign-and-an-email.html)

## SMS 메시지를 보내는 방법 {#how-to-send-sms-messages-}

[이 섹션](../../delivery/using/sms-channel.md)에서 플랫폼을 구성하고 SMS 메시지를 전송하는 방법을 살펴보십시오.

## 푸시 알림을 전송하는 방법 {#how-to-send-push-notifications-}

Adobe Campaign을 사용하여 앱을 통해 iOS 및 Android 디바이스에 [개인화된 푸시 알림 보내기](../../delivery/using/creating-notifications.md) 방법을 살펴볼 수 있습니다.

## 온라인 설문 조사를 디자인하고 공유하는 방법 {#how-to-design-and-share-an-online-survey-}

Campaign Classic을 사용하여 [온라인 설문 조사를 만들기](../../web/using/getting-started-with-surveys.md)위해 디자인하고 게재하는 주요 단계를 배웁니다.

## 랜딩 페이지를 만드는 방법 {#how-to-create-landing-page-}

Adobe Campaign 디지털 콘텐츠 편집기를 사용하여 랜딩 페이지를 디자인하고 데이터베이스 필드가 있는 매핑을 정의할 수 있습니다.

[자세한 내용을 보려면 여기를 클릭하십시오](../../web/using/creating-a-landing-page.md).

## 게재를 추적하려면 어떻게 해야 합니까? {#how-can-i-track-deliveries-}

전용 [게재 보고서](../../reporting/using/delivery-reports.md)를 통해 Campaign Classic으로 전송된 게재를 추적한 다음 게재를 모니터링할 수 있습니다.

[이 페이지](https://helpx.adobe.com/kr/campaign/kb/acc-tracking.html)에서 Campaign의 추적 관리에 대해 자세히 알아보십시오.

## 보안 모범 사례 (온-프레미스)란 무엇입니까? {#what-are-security-best-practices--on-premise--}

[보안 구성 체크리스트를](https://helpx.adobe.com/kr/campaign/kb/acc-security.html) 참조하여 보안 구성 및 온-프레미스 배포에 대한 보안 구성 및 강화 위한 주요 요소를 탐색합니다.

## 오류 메시지를 번역하는 방법 {#how-to-translate-an-error-message-}

외국어로 오류 메시지가 표시됩니까? 모든 오류 메시지와 해당 번역이 [이 페이지](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/error_messages/error_codes.html)에 나열됩니다.

## 웹 양식을 만들고 Campaign에서 답변을 수집할 수 있습니까? {#can-i-create-a-webform-and-collect-answers-in-campaign-}

디자인, 테스트, 게시 및 답변 수집과 같은 [웹 양식을 만드는](../../web/using/about-web-forms.md) 방법을 알아봅니다. 

## 더 이상 사용되지 않는 기능 및 버전 목록이 있습니까? {#is-there-a-list-of-deprecated-features-and-versions-}

Adobe는 제품 및 시간의 경과에 따라 기능을 보다 강력한 버전으로 대체하기 위한 계획을 지속적으로 평가하고 향후 기대치 또는 확장에 보다 적합한 부품을 재구현하기로 합니다. Campaign은 타사 도구와 연동되므로, 지원되는 버전만 구현하기 위해 호환성이 정기적으로 업데이트됩니다.

[자세한 내용을 보려면 여기를 클릭하십시오](https://helpx.adobe.com/kr/campaign/kb/deprecated-and-removed-features.html).

## 새로운 설명서 업데이트 및 도움말 자료가 출시됩니까? {#are-there-new-documentation-updates-and-help-materials-released-}

최신 Campaign Classic 설명서 업데이트가 [이 페이지](https://docs.adobe.com/content/help/ko-KR/campaign-classic/using/documentation-updates.html)에 나열됩니다.

[이 페이지](https://helpx.adobe.com/kr/campaign/kb/article-list.html)에 나열된 최신 기술 노트를 참조할 수도 있습니다.
