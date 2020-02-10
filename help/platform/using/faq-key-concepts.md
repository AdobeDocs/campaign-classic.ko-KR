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
source-git-commit: 994ec35e37a1c26e83a8dd2ae31f6594cadd4c45

---


# 주요 개념 {#key-concepts}

Adobe Campaign으로 시작하는 주요 단계를 살펴보십시오.

## Adobe ID 파섹 {#can-i-connect-to-campaign-classic-with-an-adobe-id-}

IMS(Adobe Identity Management System)와의 통합 덕분에 사용자는 Adobe ID를 사용하여 Adobe Campaign 콘솔에 연결할 수 있습니다. 이 통합은 다음과 같은 이점을 제공합니다.

* 모든 Experience Cloud 솔루션에 동일한 ID를 사용할 수 있습니다.
* 서로 다른 통합으로 Adobe Campaign을 사용하면 연결이 기억됩니다.
* 보안 암호 관리 정책.
* Federated ID 계정 사용(외부 ID 공급자).

[Adobe ID를 사용하여 Campaign Classic에 액세스하는 방법에 대한 자세한](../../integrations/using/about-adobe-id.md) 내용을 보려면 여기를 클릭하십시오.

## 내 버전의 Campaign은 무엇입니까? {#what-is-my-version-of-campaign-}

[ 도움말 > 정보...에서 ](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)버전 및 빌드 번호를&#x200B;****&#x200B;확인합니다.캠페인 클라이언트 콘솔의 메뉴.

## 사내 작업과 호스팅 환경에서 작업할 때의 차이점은 무엇입니까? {#what-are-the-differences-when-working-on-premise-vs--in-a-hosted-environment-}

Adobe Campaign Classic에는 모듈 및 옵션 세트가 포함되어 있습니다. 이러한 모듈 및 구성 사용 가능 여부는 설치 배포 [유형에](../../installation/using/hosting-models.md) 따라 다릅니다.호스팅(Managed Services) 또는 온프레미스.

[자세한](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html)내용을 보려면 여기를 클릭하십시오.

## 사용자 권한을 설정하려면 어떻게 해야 합니까? {#how-can-i-set-up-user-permissions-}

캠페인 관리자는 조직 사용자에 대한 권한을 설정할 수 있습니다.

다음은 다음을 승인하거나 거부하는 권한 및 제한 세트입니다.

* 특정 기능 이용,
* 특정 데이터에 대한 액세스,
* 데이터 만들기, 수정 및/또는 삭제

[사용자 권한에 대한 자세한](../../platform/using/access-management.md) 내용을 보려면 여기를 클릭하십시오.

## Adobe Campaign을 통한 개인 정보 보호 규정 준수 {#how-to-be-gdpr-compliant-with-campaign-}

Adobe Campaign은 GDPR 및 CCPA에 대한 개인 정보 보호 규정 준수를 지원하는 다양한 툴을 제공합니다.

Adobe Campaign에서 제공하는 툴과 기능 및 모범 사례를 통해 Adobe 서비스를 사용할 때 GDPR 준수를 지원하는 방법을 살펴보려면 [이 문서를](https://helpx.adobe.com/campaign/kb/campaign-privacy-overview.html) 참조하십시오. Campaign Classic의 구현 단계는 [이 문서에](https://helpx.adobe.com/campaign/kb/acc-privacy.html)설명되어 있습니다.

## 알아야 하는 Campaign 사용자 인터페이스 개념은 무엇입니까? {#what-are-campaign-user-interface-concepts-i-should-know-}

Adobe Campaign 작업 영역의 기본 사항에 대한 자세한 내용은 [이 섹션을](../../platform/using/adobe-campaign-workspace.md) 참조하십시오. 또한 [이 비디오를](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/getting-started/interface-overview.html)볼 수 있습니다.

## 메시지 대상자를 선택하려면 어떻게 해야 합니까? {#how-can-i-select-the-target-population-of-my-messages-}

Adobe Campaign을 사용하면 서로 다른 전략을 사용하여 대상을 만들고 타겟 수신자를 선택할 수 있습니다.

[자세한](../../delivery/using/steps-defining-the-target-population.md)내용을 보려면 여기를 클릭하십시오.

## 워크플로우란? {#what-is-a-workflow-}

Adobe Campaign에는 애플리케이션 서버의 여러 모듈에 걸쳐 전체 프로세스 및 작업을 조정하는 워크플로우가 포함되어 있습니다. 이 포괄적인 그래픽 환경을 사용하면 세그멘테이션, 캠페인 실행, 파일 처리, 인력 참여 등을 비롯한 프로세스를 디자인할 수 있습니다. 워크플로우 엔진은 이러한 프로세스를 실행하고 추적합니다.

예를 들어 워크플로우에서 서버에서 파일을 다운로드하고 압축을 해제한 다음 Adobe Campaign 데이터베이스에 포함된 레코드를 가져올 수 있습니다.

또한 워크플로우에는 알림을 받을 하나 이상의 연산자나 프로세스를 선택하여 승인할 수 있는 연산자가 포함될 수 있습니다. 이렇게 하면 게재 작업을 만들고, 컨텐츠에서 작업하고, 대상을 지정하고, 교정을 시작하기 전에 교정본을 승인할 하나 이상의 연산자에 작업을 할당할 수 있습니다.

[워크플로우에 대한 자세한](../../workflow/using/about-workflows.md) 내용을 살펴보려면 여기를 클릭하십시오. 또한 [워크플로우 모범 사례를](../../workflow/using/building-a-workflow.md)읽을 수 있습니다.

## 첫 번째 이메일을 만들고 보내는 방법 {#how-to-create-and-send-a-first-email-}

[자세한 내용을](../../delivery/using/about-email-channel.md) 살펴보거나 이 비디오를 [시청하여](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/getting-started/creating-a-campaign-and-an-email.html) 캠페인에서 이메일을 만듭니다.

## SMS 메시지를 보내는 방법 {#how-to-send-sms-messages-}

이 [섹션에서](../../delivery/using/sms-channel.md)플랫폼을 구성하고 SMS 메시지를 전송하는 방법을 알아봅니다.

## 푸시 알림을 전송하는 방법 {#how-to-send-push-notifications-}

Adobe Campaign을 사용하여 앱을 통해 개인화된 푸시 알림을 [](../../delivery/using/creating-notifications.md) iOS 및 Android 디바이스에 전송하는 방법을 살펴볼 수 있습니다.

## 온라인 설문 조사를 디자인하고 공유하는 방법 {#how-to-design-and-share-an-online-survey-}

Campaign Classic을 사용하여 온라인 설문 조사를 [디자인하고 퍼블리싱하는 주요 단계를 통해 온라인 설문 조사를](../../web/using/getting-started-with-surveys.md)만드는 방법을 살펴볼 수 있습니다.

## 랜딩 페이지를 만드는 방법 {#how-to-create-landing-page-}

Adobe Campaign 디지털 콘텐츠 편집기를 사용하여 랜딩 페이지를 디자인하고 데이터베이스 필드를 사용하여 매핑을 정의할 수 있습니다.

[자세한](../../web/using/creating-a-landing-page.md)내용을 보려면 여기를 클릭하십시오.

## 배송을 추적하려면 어떻게 해야 합니까? {#how-can-i-track-deliveries-}

전용 [배달 보고서를](../../reporting/using/reports-on-deliveries.md#delivery-reports) 통해 Campaign Classic으로 전송된 배달을 추적한 다음 배달을 모니터링할 수 있습니다.

이 [페이지에서](https://helpx.adobe.com/campaign/kb/acc-tracking.html)Campaign의 추적 관리에 대해 자세히 알아보십시오.

## 보안 모범 사례(온프레미스)란 무엇입니까? {#what-are-security-best-practices--on-premise--}

보안 [구성 체크리스트를](https://helpx.adobe.com/campaign/kb/acc-security.html) 참조하여 보안 구성과 사내 배포의 보안 강화를 확인할 수 있습니다.

## 오류 메시지를 변환하는 방법 {#how-to-translate-an-error-message-}

외국어로 오류 메시지가 표시됩니까? 모든 오류 메시지와 해당 번역이 [이 페이지에](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)나열됩니다.

## 웹 양식을 만들고 Campaign에서 답변을 수집할 수 있습니까? {#can-i-create-a-webform-and-collect-answers-in-campaign-}

웹 양식을 [만드는 방법을 알아봅니다](../../web/using/about-web-forms.md).웹 양식을 디자인, 테스트, 퍼블리싱하고 답변을 수집할 수 있습니다.

## 더 이상 사용되지 않는 기능 및 버전 목록이 있습니까? {#is-there-a-list-of-deprecated-features-and-versions-}

Adobe는 제품의 기능을 지속적으로 평가하고 시간이 지남에 따라 더 강력한 버전으로 기능을 대체하려는 계획을 지속적으로 평가하거나, 향후 기대치 또는 확장에 보다 효과적으로 대비하기 위해 선택된 부품을 재구현하기로 결정했습니다. Campaign은 타사 도구와 연동되므로 지원되는 버전만 구현하기 위해 정기적으로 호환성이 업데이트됩니다.

[자세한](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)내용을 보려면 여기를 클릭하십시오.

## 새로운 설명서 업데이트 및 도움말 자료가 제공됩니까? {#are-there-new-documentation-updates-and-help-materials-released-}

최신 Campaign Classic 설명서 업데이트가 이 [페이지에](https://docs.adobe.com/content/help/en/campaign-classic/using/documentation-updates.html)나열됩니다.

이 [페이지에](https://helpx.adobe.com/campaign/kb/article-list.html)나열된 최신 기술 노트를 참조할 수도 있습니다.
