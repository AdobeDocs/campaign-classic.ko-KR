---
title: 호스팅 모델
description: 호스팅 모델
page-status-flag: never-activated
uuid: a9e035d9-326b-4e14-8f05-a22fe38d172b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
discoiquuid: 3175b9ab-e305-4f19-8267-d6172fa07a2a
translation-type: tm+mt
source-git-commit: c03e90b2e2f57606749c86cda343ce5756fec122
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 3%

---


# 호스팅 모델{#hosting-models}

Adobe Campaign은 3가지 호스팅 모델 중에서 선택할 수 있는 유연성과 자유를 제공하여 비즈니스 요구 사항에 맞는 모델 또는 모델을 선택할 수 있습니다.

>[!NOTE]
>
>Adobe 호스팅 환경의 경우 서버 구성 및 인스턴스 구성 파일 사용자 지정과 같은 Adobe에서만 기본 설치 및 구성 단계를 수행할 수 있습니다. 배포 모드 간의 주요 차이점에 대한 자세한 내용은 [이 문서를 참조하십시오](https://helpx.adobe.com/kr/campaign/kb/acc-on-prem-vs-hosted.html).

* **Managed Services(호스팅)**

   Managed Service로 Adobe Campaign을 배포할 수 있습니다.사용자 인터페이스, 실행 관리 엔진 및 고객의 캠페인 데이터베이스를 비롯한 Adobe Campaign의 모든 구성 요소는 이메일 실행, 미러 페이지, 추적 서버, 구독 취소 페이지/기본 설정 센터 및 랜딩 페이지와 같은 외부적으로 볼 수 있는 웹 구성 요소를 포함하여 Adobe에 의해 완전히 호스팅됩니다. Adobe은 Cloud에 개발, 테스트/단계 및 프로덕션에 최대 3개의 인스턴스를 할당합니다. 이 호스팅 모델에 대한 설치 및 구성 단계는 이 섹션 [에 나와 있습니다](../../installation/using/hosted-model.md).

   ![](assets/deployment_hosted.png)

* **온-프레미스**

   Adobe Campaign은 사내 배포 가능:사용자 인터페이스, 실행 관리 엔진 및 데이터베이스를 포함한 Adobe Campaign의 모든 구성 요소는 고객 데이터 센터에 있습니다. 이 배포 모델에서 고객은 모든 소프트웨어 및 하드웨어 업데이트 및 업그레이드를 관리하고, 전용 데이터베이스 관리자는 캠페인 인스턴스 관리를 위해 유지 관리 및 최적화 작업을 수행해야 합니다. 온-프레미스 고객을 위한 배포 지침은 이 섹션 [에 나와 있습니다](../../installation/using/before-starting.md).

   ![](assets/deployment_onpremise.png)

* **하이브리드**

   하이브리드 모델로 배포할 경우 Adobe Campaign 솔루션 소프트웨어는 고객 사이트에 사내에 있으며 실행 관리는 Adobe의 클라우드 서비스로 제공됩니다. Adobe Campaign 마케팅 인스턴스는 고객의 방화벽 내에 설치되므로 PII(개인 식별 정보)는 내부에 유지되며 이메일을 개인화하는 데 필요한 데이터만 클라우드로 전송하여 이메일 실행을 지원합니다. 클라우드에서 호스팅되는 실행 인스턴스는 온-프레미스 인스턴스에서 이메일을 배달하라는 요청을 받습니다. 이 인스턴스는 모든 이메일을 개인화하고 배달합니다. 어떤 종류의 데이터도 클라우드에 영구적으로 저장되지 않습니다. 이 호스팅 모델에 대한 설치 및 구성 단계는 이 섹션 [에 나와 있습니다](../../installation/using/hybrid-model.md).

   ![](assets/deployment_hybrid.png)

