---
product: campaign
title: 초기 구성 정보
description: 초기 구성 정보
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: f77ba178-0dfb-4a2e-b33b-971765d42298
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 8%

---

# 인스턴스 구성 및 배포의 주요 단계{#about-initial-configuration}



Adobe Campaign 설치가 완료되면 제한 사항 및 기술 아키텍처로 효율적으로 작동하도록 구성해야 합니다. Adobe Campaign 인스턴스를 구성하는 단계는 이 장의 다음 순서에 따라 자세히 설명되어 있습니다.

1. 인스턴스 및 관련 연결을 만듭니다. 다음을 참조하십시오. [인스턴스 만들기 및 로그온](../../installation/using/creating-an-instance-and-logging-on.md).
1. 데이터베이스를 만들고 구성합니다. 다음을 참조하십시오. [데이터베이스 만들기 및 구성](../../installation/using/creating-and-configuring-the-database.md).
1. Adobe Campaign 서버 구성. 다음을 참조하십시오. [Campaign 서버 구성](../../installation/using/configuring-campaign-server.md).
1. 인스턴스를 배포하려면 다음을 참조하십시오. [인스턴스 배포](../../installation/using/deploying-an-instance.md).

인스턴스를 구성한다는 것은 활성화 프로세스(웹, mta, wfserver 등)를 의미합니다 서버에서 시작하여 이메일 전송, 추적 등을 위한 모듈을 구성합니다. 각 인스턴스에 대해 Adobe Campaign 프로세스가 서버에서 활성화됩니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../installation/using/configuring-campaign-server.md#enabling-processes)을 참조하십시오.

사용된 모듈, 아키텍처 및 요구 사항에 따라 각 인스턴스에 대해 Adobe Campaign 작업을 최적화하기 위해 추가 구성이 필요할 수 있습니다.
