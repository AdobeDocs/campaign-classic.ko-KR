---
title: 호스팅 모델
seo-title: 호스팅 모델
description: 호스팅 모델
seo-description: null
page-status-flag: never-activated
uuid: a9e035d9-326b-4e14-8f05-a22fe38d172b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
discoiquuid: 3175b9ab-e305-4f19-8267-d6172fa07a2a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# 호스팅 모델{#hosting-models}

Adobe Campaign은 세 가지 호스팅 모델 중에서 선택할 수 있는 유연성과 자유자재로 비즈니스 요구에 맞는 최상의 모델 또는 모델을 선택할 수 있는 기능을 제공합니다.

>[!NOTE]
>
>Adobe가 호스팅하는 배포에 대해서만 기본 설치 및 구성 단계를 수행할 수 있습니다. 예를 들어 서버 및 인스턴스 구성 파일을 구성합니다. 배포 모드 간의 주요 차이점에 대한 자세한 내용은 [이 문서를](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html)참조하십시오. 호스팅 또는 하이브리드 모델이 있는 경우 이 [섹션을](../../installation/using/about-hybrid-and-hosted-models.md)참조하십시오.

* **관리 서비스(호스팅)**

   Adobe Campaign을 관리 서비스로 배포할 수 있습니다.사용자 인터페이스, 실행 관리 엔진 및 고객의 캠페인 데이터베이스를 비롯한 Adobe Campaign의 모든 구성 요소는 이메일 실행, 미러 페이지, 추적 서버, 구독 취소 페이지/기본 설정 센터 및 랜딩 페이지와 같은 외부적으로 대면하는 웹 구성 요소를 포함하여 Adobe에서 완벽하게 호스팅됩니다. Adobe는 개발, 테스트/스테이지 및 프로덕션에 최대 3개의 인스턴스를 클라우드에 할당합니다. 이 호스팅 모델에 대한 설치 및 구성 단계는 이 [섹션에](../../installation/using/hosted-model.md)설명되어 있습니다.

   ![](assets/deployment_hosted.png)

* **온-프레미스**

   Adobe Campaign은 사내 배포 가능:사용자 인터페이스, 실행 관리 엔진 및 데이터베이스를 비롯한 Adobe Campaign의 모든 구성 요소가 고객 데이터 센터에 사이트에 있습니다. 이 배포 모델에서 고객은 모든 소프트웨어 및 하드웨어 업데이트 및 업그레이드를 관리하며, 전용 데이터베이스 관리자는 Campaign 인스턴스 관리를 위해 유지 관리 및 최적화 작업을 수행해야 합니다.

   ![](assets/deployment_onpremise.png)

* **하이브리드**

   하이브리드 모델로 배포할 때 Adobe Campaign 솔루션 소프트웨어는 고객 사이트에 사내에 있으며 실행 관리는 Adobe에서 클라우드 서비스로 제공합니다. Adobe Campaign 마케팅 인스턴스는 고객의 방화벽 내에 설치되므로 PII(개인 식별 정보)는 내부에 유지되며 이메일을 개인화하는 데 필요한 데이터만 Cloud로 전송하여 이메일을 실행할 수 있습니다. 클라우드에서 호스팅되는 실행 인스턴스는 온-프레미스 인스턴스에서 이메일을 배달할 요청을 받습니다. 이 인스턴스는 모든 이메일을 개인화하여 전달합니다. 어떤 종류의 데이터도 클라우드에 영구적으로 저장되지 않습니다. 이 호스팅 모델에 대한 설치 및 구성 단계는 이 [섹션에](../../installation/using/hybrid-model.md)설명되어 있습니다.

   ![](assets/deployment_hybrid.png)

