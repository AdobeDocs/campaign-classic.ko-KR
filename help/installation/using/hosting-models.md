---
product: campaign
title: 호스팅 모델
description: Campaign 호스팅 모델 살펴보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Overview
role: Architect
level: Beginner
exl-id: a06b1365-d487-4df1-8f4a-7268b871a427
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 2%

---

# 호스팅 모델{#hosting-models}



Adobe Campaign은 세 가지 호스팅 모델을 선택할 수 있으며, 이를 통해 비즈니스 요구 사항에 맞는 최적의 모델 또는 모델을 유연하게 선택할 수 있습니다.

>[!NOTE]
>
>Adobe 호스팅 환경의 경우, 주 설치 및 구성 단계는 서버 구성 및 Adobe 구성 파일 사용자 지정과 같은 인스턴스에서만 수행할 수 있습니다. 배포 모드 간의 주요 차이점에 대해 자세히 알아보려면 를 참조하십시오. [이 페이지](../../installation/using/capability-matrix.md).

## Managed Services / 호스트됨

Adobe Campaign을 as a Managed Service으로 배포할 수 있습니다. 사용자 인터페이스, 실행 관리 엔진 및 고객의 Campaign 데이터베이스를 포함한 Adobe Campaign의 모든 구성 요소는 이메일 실행, 미러 페이지, 추적 서버 및 구독 취소 페이지/기본 설정 센터 및 랜딩 페이지와 같은 외부 웹 구성 요소를 포함한 Adobe에 의해 완전히 호스팅됩니다.

![](assets/deployment_hosted.png)

호스팅된 고객은 대부분의 설치 및 구성 단계를 Adobe이 수행합니다. 다음 섹션에 액세스하여 구현을 사용자 정의할 수 있습니다.

* 브랜드별 추적 및 미러 페이지 URL을 구성합니다. 트랜잭션 메시지의 경우 다음을 참조하십시오. [이 섹션으로](../../message-center/using/additional-configurations.md#configuring-multibranding).
* 클라이언트 콘솔 설치: 다음을 참조하십시오. [이 섹션으로](../../installation/using/installing-the-client-console.md).
* 게재 기능 도구 및 모범 사례에 대한 자세한 내용은 [자세한 설명서](../../delivery/using/about-deliverability.md).
* Campaign 옵션 구성: 다음을 참조하십시오. [이 섹션으로](../../installation/using/configuring-campaign-options.md).
* CRM 커넥터 구성: 다음을 참조하십시오. [이 섹션으로](../../platform/using/crm-connectors.md).

## 온프레미스

Adobe Campaign을 온-프레미스로 배포할 수 있습니다. 사용자 인터페이스, 실행 관리 엔진 및 데이터베이스를 포함한 Adobe Campaign의 모든 구성 요소가 고객의 데이터 센터에 상주합니다. 이 배포 모델에서 고객은 모든 소프트웨어 및 하드웨어 업데이트 및 업그레이드를 관리하며, 전담 데이터베이스 관리자는 Campaign 인스턴스 관리를 위해 유지 관리 및 최적화 작업을 수행해야 합니다.

![](assets/deployment_onpremise.png)

온-프레미스 고객인 경우 Campaign Classic 배포를 시작하기 전에 다음 사전 요구 사항과 권장 사항을 고려합니다.

* 다음을 읽어 보십시오. [호환성 매트릭스](../../rn/using/compatibility-matrix.md) Adobe Campaign에 대해 지원되는 시스템 및 구성 요소의 모든 버전이 나열됩니다.
* 환경에 따라 다음을 참조하십시오. [windows용 사전 요구 사항](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) 및 [linux 사전 요구 사항](../../installation/using/prerequisites-of-campaign-installation-in-linux.md).
* 데이터베이스 엔진 관련 권장 사항 알아보기 [이 섹션에서](../../installation/using/database.md).
* 필요한 데이터베이스 액세스 레이어가 서버에 설치되어 있고 Adobe Campaign 계정에서 액세스할 수 있는지 확인하십시오. [자세히 알아보기](../../installation/using/application-server.md)
* 일부 프로세스가 다른 프로세스와 통신하거나 LAN 및 인터넷에 액세스해야 하므로 네트워크를 구성합니다. 즉, 이러한 프로세스를 위해 일부 TCP 포트를 열어야 합니다. [자세히 알아보기](../../installation/using/network-configuration.md) 네트워크 구성 요구 사항 정보.
* 읽기 [Campaign 보안 및 개인 정보 확인 목록](https://helpx.adobe.com/kr/campaign/kb/acc-security.html).
* 온프레미스 배포에 대한 하드웨어 요구 사항 추정에 대한 일반 지침 확인 [이 문서에서](https://helpx.adobe.com/kr/campaign/kb/hardware-sizing-guide.html).

## 하이브리드

하이브리드 모델로 배포되는 경우 Adobe Campaign 솔루션 소프트웨어는 고객 사이트에 온프레미스로 상주하며 실행 관리는 Adobe에서 클라우드 서비스로 제공됩니다. Adobe Campaign 마케팅 인스턴스는 고객의 방화벽 내에 설치되므로 PII(개인 식별 정보)는 사내에 유지되고 이메일을 개인화하는 데 필요한 데이터만 이메일 실행을 위해 클라우드로 전송됩니다. 클라우드에서 호스팅되는 실행 인스턴스는 온-프레미스 인스턴스에서 이메일을 배달하라는 요청을 수신합니다. 이 인스턴스는 모든 이메일을 개인화하고 전달합니다. 어떤 종류의 데이터도 클라우드에 영구적으로 저장되지 않습니다.

![](assets/deployment_hybrid.png)

하이브리드 고객은 대부분의 설치 및 구성 단계를 Adobe에서 수행합니다. 다음 섹션에 액세스하여 구현을 사용자 정의할 수 있습니다.

* 트랜잭션 메시지 구성: 참조 [이 섹션으로](../../message-center/using/transactional-messaging-architecture.md).
* 브랜드별 추적 및 미러 페이지 URL을 구성합니다. 트랜잭션 메시지의 경우 다음을 참조하십시오. [이 섹션으로](../../message-center/using/additional-configurations.md#configuring-multibranding).
* 클라이언트 콘솔 설치: 다음을 참조하십시오. [이 섹션으로](../../installation/using/installing-the-client-console.md).
* 기본 제공 패키지 설치: 참조 [이 섹션으로](../../installation/using/installing-campaign-standard-packages.md).
* 전달성: 구성 [MX 규칙](../../installation/using/email-deliverability.md#mx-configuration) 및 [이메일 형식](../../installation/using/email-deliverability.md#managing-email-formats). 게재 기능 도구 및 모범 사례에 대한 자세한 내용은 [자세한 설명서](../../delivery/using/about-deliverability.md).
* Campaign 옵션 구성: 다음을 참조하십시오. [이 섹션으로](../../installation/using/configuring-campaign-options.md).
* 외부 데이터베이스 구성(Federated Data Access): 을 참조하십시오. [이 섹션으로](../../installation/using/about-fda.md).
* CRM 커넥터 구성: 다음을 참조하십시오. [이 섹션으로](../../platform/using/crm-connectors.md).
* 중간 소싱 배포 원칙에 대한 자세한 내용은 다음을 참조하십시오. [이 섹션으로](../../installation/using/mid-sourcing-deployment.md).
