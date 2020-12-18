---
solution: Campaign Classic
product: campaign
title: 호스팅 모델
description: Discover 캠페인 호스팅 모델
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 1%

---


# 호스팅 모델{#hosting-models}

Adobe Campaign은 3가지 호스팅 모델 중에서 선택할 수 있는 유연성과 자유로운 방식으로 최고의 모델 또는 비즈니스 요구에 맞는 모델을 선택할 수 있습니다.

>[!NOTE]
>
>Adobe 호스팅 환경의 경우 서버 구성 및 인스턴스 구성 파일 사용자 지정과 같은 Adobe에서만 기본 설치 및 구성 단계를 수행할 수 있습니다. 배포 모드 간의 주요 차이점에 대한 자세한 내용은 [이 페이지](../../installation/using/capability-matrix.md)를 참조하십시오.

* **Managed Services(호스팅)**

   Adobe Campaign은 관리 서비스로 배포할 수 있습니다.사용자 인터페이스, 실행 관리 엔진 및 고객의 캠페인 데이터베이스를 비롯한 Adobe Campaign의 모든 구성 요소는 이메일 실행, 미러 페이지, 추적 서버 및 가입 해지 페이지/기본 설정 센터 및 랜딩 페이지와 같은 외부적으로 대면하는 웹 구성 요소를 포함하여 Adobe에 의해 완벽하게 호스팅됩니다. Adobe은 Cloud에 개발, 테스트/스테이지 및 프로덕션에 최대 3개의 인스턴스를 할당합니다. 이 호스팅 모델에 대한 설치 및 구성 단계는 이 섹션](../../installation/using/hosted-model.md)에 [표시됩니다.

   ![](assets/deployment_hosted.png)

* **온-프레미스**

   Adobe Campaign은 사내에서 배포할 수 있습니다.사용자 인터페이스, 실행 관리 엔진 및 데이터베이스를 포함한 Adobe Campaign의 모든 구성 요소는 고객 데이터 센터에 있는 사이트에 있습니다. 이 배포 모델에서 고객은 모든 소프트웨어 및 하드웨어 업데이트 및 업그레이드를 관리하며, 전용 데이터베이스 관리자는 캠페인 인스턴스 관리를 위해 유지 관리 및 최적화 작업을 수행해야 합니다. 온-프레미스 고객을 위한 배포 지침은 이 섹션](../../installation/using/before-starting.md)에 [표시됩니다.

   ![](assets/deployment_onpremise.png)

* **하이브리드**

   하이브리드 모델로 배포할 때 Adobe Campaign 솔루션 소프트웨어는 고객 사이트에 사내에 있으며 실행 관리는 Adobe을 통해 클라우드 서비스로 제공됩니다. Adobe Campaign 마케팅 인스턴스는 고객의 방화벽 내에 설치되므로 PII(개인 식별 정보)는 내부에 유지되며 이메일을 개인화하는 데 필요한 데이터만 Cloud로 전송됩니다. 클라우드에 호스팅된 실행 인스턴스는 온-프레미스 인스턴스에서 이메일을 배달할 요청을 받습니다. 이 인스턴스는 모든 이메일을 개인화하여 전송합니다. 모든 유형의 데이터는 클라우드에 영구적으로 저장되지 않습니다. 이 호스팅 모델에 대한 설치 및 구성 단계는 이 섹션](../../installation/using/hybrid-model.md)에 [표시됩니다.

   ![](assets/deployment_hybrid.png)

