---
product: campaign
title: 호스팅 모델
description: 캠페인 호스팅 모델 살펴보기
feature: 개요
role: Architect
level: Beginner
exl-id: a06b1365-d487-4df1-8f4a-7268b871a427
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 2%

---

# 호스팅 모델{#hosting-models}

Adobe Campaign은 3가지 호스팅 모델 중에서 선택하여 비즈니스 요구에 맞는 최상의 모델 또는 모델을 선택할 수 있는 유연성과 자유를 제공합니다.

>[!NOTE]
>
>Adobe 호스팅 환경의 경우 서버 구성 및 인스턴스 구성 파일 사용자 지정과 같이, 기본 설치 및 구성 단계는 Adobe이 수행해야 합니다. 배포 모드 간의 주요 차이점에 대한 자세한 내용은 [이 페이지](../../installation/using/capability-matrix.md)를 참조하십시오.

## Managed Services / 호스팅

Adobe Campaign을 Managed Service으로 배포할 수 있습니다.사용자 인터페이스, 실행 관리 엔진 및 고객의 Campaign 데이터베이스를 포함한 Adobe Campaign의 모든 구성 요소는 이메일 실행, 미러 페이지, 추적 서버 및 구독 취소 페이지/기본 설정 센터 및 랜딩 페이지와 같은 외부에서 보는 웹 구성 요소를 포함하여 Adobe에 의해 완전히 호스팅됩니다.

![](assets/deployment_hosted.png)

호스팅된 고객의 경우 대부분의 설치 및 구성 단계는 Adobe에 의해 수행됩니다. 다음 섹션에 액세스하여 구현을 사용자 지정할 수 있습니다.

* 브랜드당 추적 및 미러 페이지 URL을 구성합니다. 트랜잭션 메시지는 [이 섹션](../../message-center/using/additional-configurations.md#configuring-multibranding)을 참조하십시오.
* 클라이언트 콘솔 설치:[을 참조하여 이 섹션](../../installation/using/installing-the-client-console.md)을 참조하십시오.
* 게재 기능 도구 및 모범 사례에 대해 자세히 알아보려면 [자세한 설명서](../../delivery/using/about-deliverability.md)를 참조하십시오.
* 캠페인 옵션 구성:[을 참조하여 이 섹션](../../installation/using/configuring-campaign-options.md)을 참조하십시오.
* CRM 커넥터 구성:[을 참조하여 이 섹션](../../platform/using/crm-connectors.md)을 참조하십시오.

## On-premise

Adobe Campaign은 온-프레미스에서 배포할 수 있습니다.사용자 인터페이스, 실행 관리 엔진 및 데이터베이스를 포함한 Adobe Campaign의 모든 구성 요소는 고객 데이터 센터에 있는 사이트에 있습니다. 이 배포 모델에서 고객은 모든 소프트웨어 및 하드웨어 업데이트 및 업그레이드를 관리하며, 전용 데이터베이스 관리자는 Campaign 인스턴스를 관리하기 위해 유지 관리 및 최적화 작업을 수행해야 합니다.

![](assets/deployment_onpremise.png)

Campaign Classic 배포를 시작하기 전에 온-프레미스 고객으로서 다음 사전 요구 사항 및 권장 사항을 확인하십시오.

* Adobe Campaign에 대해 지원되는 모든 시스템 및 구성 요소 버전을 나열하는 [호환성 매트릭스](../../rn/using/compatibility-matrix.md)를 참조하십시오.
* 사용자 환경에 따라 Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) 및 [Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md)용 사전 요구 사항을 참조하십시오.[
* 이 섹션](../../installation/using/database.md)에서 데이터베이스 엔진 [과 관련된 권장 사항을 알아봅니다.
* 필요한 데이터베이스 액세스 레이어가 서버에 설치되어 있고 Adobe Campaign 계정에서 액세스할 수 있는지 확인합니다. [자세히 알아보기](../../installation/using/application-server.md)
* 일부 프로세스가 다른 사용자와 통신하거나 LAN 및 인터넷에 액세스하는 데 필요한 네트워크 구성 즉, 이러한 프로세스에 대해 일부 TCP 포트를 열어야 합니다. [네트워크 ](../../installation/using/network-configuration.md) 구성 요구 사항에 대해 자세히 알아보십시오.
* [Campaign 보안 및 개인 정보 보호 체크리스트](https://helpx.adobe.com/kr/campaign/kb/acc-security.html)를 참조하십시오.
* 이 문서](https://helpx.adobe.com/kr/campaign/kb/hardware-sizing-guide.html)에서 온-프레미스 배포에 대한 하드웨어 요구 사항을 추정하는 일반 지침을 확인하십시오. [.

## 하이브리드

하이브리드 모델로 배포될 때 Adobe Campaign 솔루션 소프트웨어는 고객 사이트에 온프레미스이며 실행 관리는 Adobe에 의해 클라우드 서비스로 제공됩니다. Adobe Campaign 마케팅 인스턴스는 고객 방화벽 내에 설치되므로 개인 식별 정보(PII)는 내부에 유지되며 이메일을 개인화하는 데 필요한 데이터만 이메일 실행을 위해 Cloud에 전송됩니다. 클라우드에 호스팅된 실행 인스턴스는 온-프레미스 인스턴스에서 전자 메일을 전달하도록 요청을 받습니다. 이 인스턴스는 모든 이메일을 개인화하고 전달합니다. 어떤 종류의 데이터도 클라우드에 영구적으로 저장되지 않습니다.

![](assets/deployment_hybrid.png)

하이브리드 고객으로서, 대부분의 설치 및 구성 단계는 Adobe에 의해 수행됩니다. 다음 섹션에 액세스하여 구현을 사용자 지정할 수 있습니다.

* 트랜잭션 메시지 구성:[을 참조하여 이 섹션](../../message-center/using/transactional-messaging-architecture.md)을 참조하십시오.
* 브랜드당 추적 및 미러 페이지 URL을 구성합니다. 트랜잭션 메시지는 [이 섹션](../../message-center/using/additional-configurations.md#configuring-multibranding)을 참조하십시오.
* 클라이언트 콘솔 설치:[을 참조하여 이 섹션](../../installation/using/installing-the-client-console.md)을 참조하십시오.
* 기본 제공 패키지 설치:[을 참조하여 이 섹션](../../installation/using/installing-campaign-standard-packages.md)을 참조하십시오.
* 게재 기능:[MX 규칙](../../installation/using/email-deliverability.md#mx-configuration) 및 [전자 메일 형식](../../installation/using/email-deliverability.md#managing-email-formats)을 구성합니다. 게재 기능 도구 및 모범 사례에 대해 자세히 알아보려면 [자세한 설명서](../../delivery/using/about-deliverability.md)를 참조하십시오.
* 캠페인 옵션 구성:[을 참조하여 이 섹션](../../installation/using/configuring-campaign-options.md)을 참조하십시오.
* 외부 데이터베이스 구성(Federated Data Access):[을 참조하여 이 섹션](../../installation/using/about-fda.md)을 참조하십시오.
* CRM 커넥터 구성:[을 참조하여 이 섹션](../../platform/using/crm-connectors.md)을 참조하십시오.
* 중간 소싱 배포 원칙에 대한 자세한 내용은 [에서 이 섹션](../../installation/using/mid-sourcing-deployment.md)을 참조하십시오.
