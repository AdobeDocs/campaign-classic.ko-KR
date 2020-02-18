---
title: 캠페인 설정 FAQ
seo-title: 캠페인을 구성하는 방법
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
source-git-commit: 7aa381654805798fcdd24f588160bed15e037a2b

---


# 캠페인 설정 FAQ {#settings-faq}

요구 사항에 맞게 Campaign 인스턴스를 설정하는 주요 구성을 알아봅니다.

## 캠페인 인터페이스의 언어를 변경할 수 있습니까? {#can-i-change-the-language-of-campaign-interface-}

인스턴스를 만들 때 캠페인 언어가 선택됩니다. 나중에 변경할 수 없습니다. For more on this, refer to [this section](../../installation/using/creating-an-instance-and-logging-on.md).

Adobe Campaign 사용자 인터페이스는 다음 4개 언어로 제공됩니다.영어, 프랑스어, 독일어 및 일본어 클라이언트 콘솔과 서버는 동일한 언어로 설정되어야 합니다. 각 Campaign 인스턴스는 하나의 언어로만 실행할 수 있습니다.

영어 버전의 경우 Campaign을 설치할 때 영어 또는 영국 영어를 선택할 수 있습니다.날짜 및 시간 형식이 다릅니다. For more on these differences refer to [this section](../../platform/using/adobe-campaign-workspace.md#date-and-time).

## 다른 Adobe 솔루션과 함께 Campaign Classic을 사용할 수 있습니까? {#can-i-use-campaign-classic-with-other-adobe-solutions-}

Adobe Campaign의 전달 기능 및 고급 캠페인 관리 기능과 사용자 경험을 개인화할 수 있도록 만들어진 솔루션 세트를 결합할 수 있습니다.

다른 Adobe 솔루션을 [사용하여 작업하는](../../integrations/using/about-campaign-integrations.md) 방법과 Campaign에서 IMS를 설정하는 [방법을 알려면 여기를 클릭하십시오](../../integrations/using/about-adobe-id.md).

## Campaign 인스턴스에 추적 기능을 설정하려면 어떻게 해야 합니까? {#how-can-i-set-up-tracking-capabilities-on-my-campaign-instance-}

전문가 사용자는 캠페인 인스턴스에서 추적 기능을 구성할 수 있습니다.

[자세한](../../installation/using/deploying-an-instance.md#tracking-configuration)내용을 보려면 여기를 클릭하십시오.

## 이메일 전달 기능을 구성하는 방법 {#how-to-configure-email-deliverability-}

전달 [시작 안내서](http://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html)외에도 이메일 전달 기능 구성에 대한 섹션을 참조하여 Campaign 제공 기능을 최대화하도록 인스턴스를 구성하는 방법을 알아보십시오.

[자세한](../../installation/using/email-deliverability.md)내용을 보려면 여기를 클릭하십시오.

## 콘텐츠 승인을 구현하려면 어떻게 해야 합니까? {#how-can-i-implement-content-approval-}

Campaign을 사용하면 마케팅 캠페인의 기본 단계에 대한 승인 프로세스를 협업 모드로 설정할 수 있습니다. 각 캠페인에 대해 게재 타겟, 컨텐츠 및 비용을 승인할 수 있습니다. 승인 담당 Adobe Campaign 운영자에게는 이메일로 통보를 할 수 있으며 콘솔 또는 웹 연결을 통해 승인을 수락하거나 거부할 수 있습니다.

[여기를 클릭하여 자세한](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries) 내용을 살펴보고 Campaign에서 게재 컨텐츠 승인을 구현하는 단계를 살펴보십시오.

## 외부 데이터베이스에 저장된 데이터에 액세스하려면 어떻게 합니까? {#how-can-i-access-data-stored-in-an-external-database-}

Adobe Campaign은 하나 이상의 외부 데이터베이스에 저장된 정보를 처리하기 위해 FDA(Federated Data Access) 옵션을 제공합니다.adobe Campaign 데이터 구조를 변경하지 않고 외부 데이터에 액세스할 수 있습니다.

[자세한](../../platform/using/connecting-to-database.md)내용을 보려면 여기를 클릭하십시오.

## Campaign을 연결할 수 있는 외부 데이터베이스는 무엇입니까? {#which-external-databases-can-i-connect-campaign-to-}

Federated Data Access(FDA)를 통해 Campaign과 호환되는 외부 데이터베이스는 호환성 [매트릭스에](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)나열되어 있습니다.

## Adobe Campaign을 LDAP와 통합할 수 있습니까? {#can-adobe-campaign-integrate-with-ldap-}

온-프레미스/하이브리드 고객은 Campaign Classic을 LDAP 디렉토리와 통합할 수 있습니다.

[방법을](../../installation/using/connecting-through-ldap.md)살펴보려면 여기를 클릭하십시오.

## Campaign에서 CRM 커넥터를 설정하려면 어떻게 해야 합니까? {#how-can-i-set-up-crm-connectors-in-campaign-}

Adobe Campaign은 Adobe Campaign 플랫폼을 타사 시스템에 연결하는 다양한 CRM 커넥터를 제공합니다. 이러한 CRM 커넥터를 사용하면 연락처, 계정, 구매 등을 동기화할 수 있습니다. 또한 다양한 타사 및 비즈니스 애플리케이션과 애플리케이션을 손쉽게 통합할 수 있습니다.

이러한 커넥터를 사용하면 빠르고 손쉽게 데이터를 통합할 수 있습니다.Adobe Campaign은 CRM에서 사용할 수 있는 표를 수집하고 선택하는 전용 마법사를 제공합니다. 이렇게 하면 두 가지 방향 동기화를 통해 데이터가 시스템 전체에서 항상 최신 상태로 유지되는지 확인할 수 있습니다.

CRM [도구를 Adobe Campaign과 동기화하는 방법을 알아보려면 CRM 커넥터](../../platform/using/crm-connectors.md) 구성을 참조하십시오. Adobe Campaign 및 Microsoft Dynamics [365 통합에](https://helpx.adobe.com/campaign/kt/acc/using/acc-integrate-dynamics365-with-acc-feature-video-set-up.html)대한 이 활용 사례 비디오를 시청하십시오.
