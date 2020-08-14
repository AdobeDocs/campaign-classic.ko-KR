---
title: Campaign 설정 FAQ
seo-title: Campaign 구성 방법
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
translation-type: ht
source-git-commit: 928c2d944bb9709b54a41b07e8828646f2601cb9
workflow-type: ht
source-wordcount: '759'
ht-degree: 100%

---


# Campaign 설정 FAQ {#settings-faq}

요구 사항에 맞게 Campaign 인스턴스를 설정하는 주요 구성을 배웁니다.

## Campaign 인터페이스의 언어를 변경할 수 있습니까? {#can-i-change-the-language-of-campaign-interface-}

인스턴스를 만들 때 Campaign 언어가 선택됩니다. 나중에 변경할 수 없습니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../installation/using/creating-an-instance-and-logging-on.md)을 참조하십시오.

Adobe Campaign 사용자 인터페이스는 영어, 프랑스어, 독일어 및 일본어 4개 언어로 제공됩니다. 클라이언트 콘솔과 서버는 동일한 언어로 설정되어야 합니다. 각 Campaign 인스턴스는 하나의 언어로만 실행할 수 있습니다.

Campaign을 설치할 때 미국 영어 또는 영국 영어 중 하나를 선택할 수 있습니다. 날짜 및 시간 형식이 다릅니다. 차이점에 대한 자세한 정보는 [이 섹션](../../platform/using/adobe-campaign-workspace.md#date-and-time)을 참조하십시오.

## 다른 Adobe 솔루션과 함께 Campaign Classic을 사용할 수 있습니까? {#can-i-use-campaign-classic-with-other-adobe-solutions-}

Adobe Campaign의 게재 기능 및 고급 캠페인 관리 기능과 사용자 경험을 개인화할 수 있도록 만들어진 솔루션 세트를 결합할 수 있습니다.

[다른 Adobe 솔루션과 함께 사용하는 방법](../../integrations/using/about-campaign-integrations.md) 및 [Campaign에서 IMS를 설정하는 방법](../../integrations/using/about-adobe-id.md)을 배우려면 여기를 클릭하십시오.

## Campaign 인스턴스에 추적 기능을 설정하려면 어떻게 해야 합니까? {#how-can-i-set-up-tracking-capabilities-on-my-campaign-instance-}

전문가 사용자로서 Campaign 인스턴스에서 추적 기능을 구성할 수 있습니다.

[자세한 내용을 보려면 여기를 클릭하십시오](../../installation/using/deploying-an-instance.md#tracking-configuration).

## 전자 메일 게재 기능을 구성하는 방법 {#how-to-configure-email-deliverability-}

[게재 기능 구성](../../delivery/using/about-deliverability.md#configuration) 섹션 외에 게재 기능 권장 사항을 참조하여 Campaign 게재 기능을 최대화하기 위해 인스턴스를 구성하는 방법을 이해합니다.

[자세한 내용을 보려면 여기를 클릭하십시오](../../delivery/using/technical-recommendations.md).

## 콘텐츠 승인을 구현하려면 어떻게 해야 합니까? {#how-can-i-implement-content-approval-}

Campaign을 사용하면 마케팅 캠페인의 주요 단계에 대한 승인 프로세스를 공동 작업 모드로 설정할 수 있습니다. 각 캠페인에 대해 게재 대상, 콘텐츠 및 비용을 승인할 수 있습니다. 승인이 필요한 Adobe Campaign 운영자는 전자 메일로 통보를 받을 수 있으며 콘솔 또는 웹 연결을 통해 승인을 수락하거나 거부할 수 있습니다.

[여기를 클릭하여 자세한 내용을 살펴보고](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries) Campaign에서 게재 콘텐츠 승인을 구현하는 단계를 알아봅니다.

## 외부 데이터베이스에 저장된 데이터에 액세스하려면 어떻게 해야 합니까? {#how-can-i-access-data-stored-in-an-external-database-}

Adobe Campaign은 하나 이상의 외부 데이터베이스에 저장된 정보를 처리하기 위해 Adobe Campaign 데이터 구조를 변경하지 않고 외부 데이터에 액세스할 수 있는 FDA(Federated Data Access) 옵션을 제공합니다.

[자세한 내용을 보려면 여기를 클릭하십시오](../../platform/using/connecting-to-database.md).

## Campaign을 연결할 수 있는 외부 데이터베이스는 무엇입니까? {#which-external-databases-can-i-connect-campaign-to-}

FDA(Federated Data Access)를 통해 Campaign과 호환되는 외부 데이터베이스는 [호환성 매트릭스](https://helpx.adobe.com/kr/campaign/kb/compatibility-matrix.html)에 나열되어 있습니다.

## Adobe Campaign을 LDAP와 통합할 수 있습니까? {#can-adobe-campaign-integrate-with-ldap-}

온-프레미스/하이브리드 고객은 Campaign Classic을 LDAP 디렉토리와 통합할 수 있습니다.

[방법을 배우려면 여기를 클릭하십시오](../../installation/using/connecting-through-ldap.md).

## Campaign에서 CRM 커넥터를 설정하려면 어떻게 해야 합니까? {#how-can-i-set-up-crm-connectors-in-campaign-}

Adobe Campaign은 Adobe Campaign 플랫폼을 타사 시스템에 연결하는 다양한 CRM 커넥터를 제공합니다. 이러한 CRM 커넥터를 사용하면 연락처, 계정, 구매 등을 동기화할 수 있습니다. 또한 다양한 타사 및 비즈니스 애플리케이션과 사용자의 애플리케이션을 손쉽게 통합할 수 있습니다.

이러한 커넥터를 사용하면 빠르고 손쉽게 데이터를 통합할 수 있습니다. Adobe Campaign은 CRM에서 사용할 수 있는 테이블을 수집하고 선택하는 전용 마법사를 제공합니다. 이렇게 하면 시스템 전체에서 항상 데이터가 최신 상태로 유지되도록 양방향 동기화를 보장합니다.

CRM 도구를 Adobe Campaign과 동기화하는 방법을 배우려면 [CRM 커넥터 구성](../../platform/using/crm-connectors.md)을 참조하십시오. [Adobe Campaign 및 Microsoft Dynamics 365 통합](https://helpx.adobe.com/campaign/kt/acc/using/acc-integrate-dynamics365-with-acc-feature-video-set-up.html)에 대한 이 사용 사례 비디오를 시청하십시오.

## 컴퓨터에 특정하거나 사용자에 특정한 문제인 경우 소프트 캐시 지우기를 수행하는 방법 {#perform-soft-cache-clear}

새 로고가 올바로 반영되고 시스템별/사용자별 데이터를 성공적으로 내보낼 수 있는 등의 문제가 있는 경우 Windows(Windows 7, Windows XP, Windows 10)에서 소프트 캐시 지우기를 수행해야 할 수 있습니다.

로그인하고 나면 **[!UICONTROL File]** > **[!UICONTROL Clear the local cache]**(으)로 이동합니다. 그런 다음 로그아웃한 후 다시 로그인합니다.

![](assets/faq_soft_cache.png)

그래도 도움이 되지 않는 경우 아래 단계를 수행하여 하드 캐시를 지우십시오.

## 컴퓨터에 특정하거나 사용자에 특정한 문제인 경우 하드 캐시 지우기를 수행하는 방법 {#perform-hard-cache-clear}

새 로고가 올바로 반영되고 시스템별/사용자별 데이터를 성공적으로 내보낼 수 있는 등의 문제가 있는 경우 Windows(Windows 7, Windows XP, Windows 10)에서 하드 캐시 지우기를 수행해야 할 수 있습니다.

1. 클라이언트 콘솔에서 **[!UICONTROL File]** > **[!UICONTROL Clear the local cache]**&#x200B;을(를) 선택합니다 .

1. 클라이언트 콘솔(리치 클라이언트)을 로그아웃하고 닫습니다.

1. 운영 체제 버전을 기준으로 다음 위치로 이동합니다.

   * Windows 7: C:\Users\&lt; 사용자 이름 >\AppData\Roaming\Neolane\NL_5\
   * Windows XP: C:\Documents and Settings\&lt; 사용자 이름 >\Application Data\Neolane\NL_5
   여기서는 nlclient-config-&lt; 영숫자 값 >.xml이라는 많은 xml 파일을 볼 수 있습니다.

1. 이러한 xml 파일 및 관련 폴더를 삭제합니다.

   >[!IMPORTANT]
   >
   >nlclient_cnx.xml 파일을 삭제하지 마십시오.

1. 클라이언트 콘솔에 로그인합니다.