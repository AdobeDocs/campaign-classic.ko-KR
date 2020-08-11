---
title: 주요 개념
seo-title: 캠페인 기능 FAQ
description: Campaign Classic FAQ
page-status-flag: never-activated
uuid: 3f719ac2-cc26-4fb0-adda-84666c8c38e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 16dbe423-018f-4666-9901-2120a8dc609a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: bc54cef4c44be4c694e062f56685dbb09d2fcf8e
workflow-type: tm+mt
source-wordcount: '902'
ht-degree: 1%

---


# 주요 개념 {#key-concepts}

Adobe Campaign으로 시작하는 주요 단계를 살펴보십시오.

## Adobe ID과 Campaign Classic에 연결할 수 있습니까? {#can-i-connect-to-campaign-classic-with-an-adobe-id-}

IMS(Adobe Identity Management 시스템)와의 통합 덕분에 Adobe ID을 사용하여 Adobe Campaign 콘솔에 연결할 수 있습니다. 이 통합은 다음과 같은 이점을 제공합니다.

* 모든 Experience Cloud 솔루션에 동일한 ID를 사용할 수 있습니다.
* 서로 다른 통합으로 Adobe Campaign을 사용하는 경우 연결이 기억됩니다.
* 보안 암호 관리 정책.
* Federated ID 계정 사용(외부 ID 공급자).

[Adobe ID으로 Campaign Classic에 액세스하는 방법에 대해 자세히](../../integrations/using/about-adobe-id.md) 알아보려면 여기를 클릭하십시오.

## 내 Campaign 버전이란? {#what-is-my-version-of-campaign-}

Campaign 클라이언트 콘솔의 [도움말 > 정보...](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) 메뉴에서 **버전 및 빌드 번호를** 확인합니다.

## 온프레미스 및 호스팅 환경에서 작업하는 경우의 차이점은 무엇입니까? {#what-are-the-differences-when-working-on-premise-vs--in-a-hosted-environment-}

Adobe Campaign Classic은 다양한 모듈 및 옵션을 제공합니다. 이러한 모듈 및 구성 가용성은 설치 배포 [유형에 따라](../../installation/using/hosting-models.md) 달라질 수 있습니다.호스팅(Managed Services) 또는 온프레미스

[자세한 내용을 보려면 여기를 클릭하십시오](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html).

## 사용자 권한을 설정하려면 어떻게 해야 합니까? {#how-can-i-set-up-user-permissions-}

캠페인 관리자는 조직의 사용자에 대한 권한을 설정할 수 있습니다.

다음은 권한을 부여하거나 거부한 권한 및 제한 세트입니다.

* 특정 기능에 대한 액세스,
* 특정 데이터에 액세스하고
* 데이터 만들기, 수정 및/또는 삭제

[사용자 권한에 대해 자세히](../../platform/using/access-management.md) 알려면 여기를 클릭하십시오.

## Adobe Campaign을 통한 개인 정보 보호 규정 준수 {#how-to-be-gdpr-compliant-with-campaign-}

Adobe Campaign은 GDPR 및 CPA에 대한 개인 정보 보호 규정을 준수하는 데 도움이 되는 툴을 제공합니다.

Adobe 서비스를 사용할 때 GDPR 준수를 위해 Adobe Campaign이 제공하는 툴과 기능, 모범 사례 등을 자세히 알아보려면 [이 문서를](https://helpx.adobe.com/campaign/kb/campaign-privacy-overview.html) 참조하십시오. Campaign Classic에 대한 구현 단계는 [이 문서에 설명되어 있습니다](https://helpx.adobe.com/campaign/kb/acc-privacy.html).

## 알아야 하는 Campaign 사용자 인터페이스 개념이란 무엇입니까? {#what-are-campaign-user-interface-concepts-i-should-know-}

Adobe Campaign 작업 영역의 기본 사항에 대한 자세한 내용은 [이 섹션을](../../platform/using/adobe-campaign-workspace.md) 참조하십시오. 또한 [이 비디오를 볼 수 있습니다](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/getting-started/interface-overview.html).

## 메시지 대상자를 선택하려면 어떻게 해야 합니까? {#how-can-i-select-the-target-population-of-my-messages-}

Adobe Campaign을 사용하면 다양한 전략을 통해 고객을 만들고 타겟 수신자를 선택할 수 있습니다.

[자세한 내용을 보려면 여기를 클릭하십시오](../../delivery/using/steps-defining-the-target-population.md).

## 워크플로우란? {#what-is-a-workflow-}

Adobe Campaign에는 애플리케이션 서버의 다양한 모듈에서 전체 프로세스 및 작업을 조정하는 워크플로우가 포함되어 있습니다. 이 포괄적인 그래픽 환경을 사용하면 세그먼테이션, 캠페인 실행, 파일 처리, 인력 참여 등의 프로세스를 디자인할 수 있습니다. 워크플로우 엔진은 이러한 프로세스를 실행하고 추적합니다.

예를 들어 워크플로우에서 서버에서 파일을 다운로드하고 압축을 해제한 다음 Adobe Campaign 데이터베이스에 포함된 레코드를 가져올 수 있습니다.

워크플로우에는 알림을 받거나 프로세스를 선택하여 승인할 수 있는 연산자가 하나 이상 포함될 수도 있습니다. 이러한 방식으로 배달 작업을 만들고, 컨텐츠를 사용하여 작업하도록 하나 이상의 연산자에 작업을 할당하고, 대상을 지정하고, 교정을 시작하기 전에 교정본을 승인할 수 있습니다.

[워크플로우에 대한 자세한](../../workflow/using/about-workflows.md) 내용을 살펴보려면 여기를 클릭하십시오. 또한 워크플로우 [모범 사례를 읽을 수 있습니다](../../workflow/using/building-a-workflow.md).

## 첫 번째 이메일을 만들고 보내는 방법? {#how-to-create-and-send-a-first-email-}

[자세한](../../delivery/using/about-email-channel.md) 내용을 [확인하거나 이 비디오를](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/getting-started/creating-a-campaign-and-an-email.html) 시청하여캠페인에서 이메일을 만듭니다.

## SMS 메시지를 보내는 방법 {#how-to-send-sms-messages-}

이 섹션에서 플랫폼을 구성하고 SMS 메시지를 전송하는 방법 [을 살펴보십시오](../../delivery/using/sms-channel.md).

## 푸시 알림을 전송하는 방법 {#how-to-send-push-notifications-}

Adobe Campaign을 사용하여 앱을 통해 iOS 및 Android 디바이스에 개인화된 푸시 알림 [](../../delivery/using/creating-notifications.md) 전송 방법을 살펴볼 수 있습니다.

## 온라인 설문 조사를 디자인하고 공유하는 방법 {#how-to-design-and-share-an-online-survey-}

Campaign Classic을 사용하여 온라인 설문 조사 [를 디자인하고 퍼블리싱하는](../../web/using/getting-started-with-surveys.md)방법을 살펴볼 수 있습니다.

## 랜딩 페이지를 만드는 방법 {#how-to-create-landing-page-}

Adobe Campaign 디지털 컨텐츠 편집기를 사용하여 랜딩 페이지를 디자인하고 데이터베이스 필드가 있는 매핑을 정의할 수 있습니다.

[자세한 내용을 보려면 여기를 클릭하십시오](../../web/using/creating-a-landing-page.md).

## 배송을 추적하려면 어떻게 해야 합니까? {#how-can-i-track-deliveries-}

전용 [배달 보고서를 통해 Campaign Classic으로 전송된 배달을 추적한](../../reporting/using/delivery-reports.md) 다음 배달을 모니터링할 수 있습니다.

이 페이지에서 Campaign의 추적 관리에 대해 자세히 [알아보십시오](https://helpx.adobe.com/campaign/kb/acc-tracking.html).

## 보안 모범 사례란? {#what-are-security-best-practices--on-premise--}

보안 [구성 체크리스트를](https://helpx.adobe.com/campaign/kb/acc-security.html) 참조하여 보안 구성 및 온-프레미스 배포에 대한 보안 강화를 확인할 수 있습니다.

## 오류 메시지를 변환하는 방법 {#how-to-translate-an-error-message-}

외국어로 오류 메시지가 표시됩니까? 모든 오류 메시지와 해당 번역이 [이 페이지에 나열됩니다](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/error_messages/error_codes.html).

## 웹 양식을 만들고 Campaign에서 답변을 수집할 수 있습니까? {#can-i-create-a-webform-and-collect-answers-in-campaign-}

웹 양식 [을 만드는 방법을 알아봅니다](../../web/using/about-web-forms.md).웹 양식을 디자인, 테스트, 퍼블리싱하고 답변을 수집할 수 있습니다.

## 더 이상 사용되지 않는 기능 및 버전 목록이 있습니까? {#is-there-a-list-of-deprecated-features-and-versions-}

Adobe은 제품 및 시간의 경과에 따라 기능을 보다 강력한 버전으로 대체하려는 기능을 지속적으로 평가하거나, 향후 기대치 또는 익스텐션에 보다 적합한 부품을 재구현하기로 결정했습니다. Campaign은 타사 도구와 연동되므로, 지원되는 버전만 구현하기 위해 호환성이 정기적으로 업데이트됩니다.

[자세한 내용을 보려면 여기를 클릭하십시오](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html).

## 새로운 설명서 업데이트 및 도움말 자료가 출시됩니까? {#are-there-new-documentation-updates-and-help-materials-released-}

최신 Campaign Classic 설명서 업데이트가 이 페이지 [에 나와 있습니다](https://docs.adobe.com/content/help/en/campaign-classic/using/documentation-updates.html).

이 페이지에 나열된 최신 기술 노트를 참조할 수도 [있습니다](https://helpx.adobe.com/campaign/kb/article-list.html).
