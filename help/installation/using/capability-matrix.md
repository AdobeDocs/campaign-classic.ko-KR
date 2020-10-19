---
title: 캠페인 온프레미스, 하이브리드 및 호스팅 기능 매트릭스
description: 호스팅 및 온-프레미스 배포 간의 주요 차이점
page-status-flag: never-activated
uuid: d1c786a1-2691-4966-9108-059004050464
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
discoiquuid: 582f7ac6-cebe-4b47-8730-bbc16fd6b1bd
translation-type: tm+mt
source-git-commit: c2e1b4cf7051b7f1b9d5f2db0d9f51a733ca2abc
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 10%

---


# 호스팅 모델당 기능 매트릭스 {#capability-matrix-per-model}

Adobe Campaign Classic에는 모듈 및 옵션 세트가 포함되어 있습니다. 이러한 모듈 및 모듈의 사용 가능 여부는 설치 배포 유형에 따라 달라질 수 있습니다. 이 문서에서는 완전히 호스팅된(Managed Services)과 온-프레미스 배포 간의 특정 기능에 대한 주요 차이점에 대해 자세히 설명합니다.

이 페이지에서는 호스팅(Managed Services)과 온-프레미스 배포 간의 주요 차이점을 보여줍니다. 하이브리드 배포 지정은 Adobe에서 호스팅하고 사내 환경에 호스팅되는 요소에 따라 다릅니다.

다양한 호스팅 모델이 이 섹션 [에 도입되었습니다](../../installation/using/hosting-models.md).

## 기능 매트릭스{#capability-matrix}

| 기능 | 호스팅 | 하이브리드 | 온-프레미스 | 세부 정보 |
|-----------------------------------------------|------------------|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 캠페인 서버 구성 | On-Demand | 사용 가능 | 사용 가능 | 호스팅된 고객의 경우[서버 구성](../../installation/using/the-server-configuration-file.md)파일은 Adobe에서만 수정할 수 있습니다. |
| 이메일 숨은 참조 | On-Demand | On-Demand | 사용 가능 | 호스팅 및 하이브리드 아키텍처의 경우 계정 담당자에게 연락하여 이메일 BCC를 활성화합니다. 온프레미스 설치의 경우 설명서의 지침을 따르십시오. [자세히 알아보기](../../installation/using/email-archiving.md) |
| 메시지 센터 실행 인스턴스 관리 | On-Demand | On-Demand | 사용 가능 | 호스팅 배포의 경우 실행 인스턴스에서 사용자를 만드는 등의 특정 설정은 Adobe에서만 수행할 수 있습니다. [자세히 알아보기](../../message-center/using/about-transactional-messaging.md) |
| 중간 소싱 플랫폼 관리 | On-Demand | On-Demand | 사용 가능 | Adobe에서 호스팅하는 중간 소싱 플랫폼은 Adobe에서만 구성할 수 있습니다. |
| 리트머스 를 통한 받은 편지함 렌더링 | On-Demand | On-Demand | 사용 가능 | 리트머스 계정이 필요합니다. 필요한 세부 사항을 얻거나 받은 편지함 렌더링 구성을 수행하려면 Adobe으로 이동해야 합니다. [자세히 알아보기](../../delivery/using/inbox-rendering.md) |
| IMS와 통합(Adobe ID) | On-Demand | On-Demand | On-Demand | IMS 프로비저닝은 Adobe에 의해 수행됩니다. 이 통합은 Adobe Experience Cloud 통합의 전제 조건입니다. [자세히 알아보기](../../integrations/using/about-adobe-id.md) |
| 파일 전송을 위한 데이터 암호화/암호 해독 | On-Demand | 사용 가능 | 사용 가능 | 파일 사전 또는 사후 처리를 사용하려면 Adobe Campaign 서버에 필요한 유틸리티를 설치해야 합니다. 호스팅된 고객은 캠페인 Campaign 컨트롤 패널을 사용할 수 있습니다. [자세히 알아보기](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing) |
| 파일 지핑/압축 해제 | 온디맨드 사용 가능 | 사용 가능 | 파일 사전 또는 사후 처리를 사용하려면 Adobe Campaign 서버에 필요한 유틸리티를 설치해야 합니다. 호스팅된 고객은 캠페인 Campaign 컨트롤 패널을 사용할 수 있습니다. [자세히 알아보기](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing) |
| 도메인 이름 위임 | On-Demand | On-Demand | 사용할 수 없음 | [자세히 알아보기](https://helpx.adobe.com/kr/campaign/kb/domain-name-delegation.html) |
| SpamCharacter 설치 | On-Demand | 사용 가능 | 사용 가능 | SpamCharacter를 설치하려면 서버 구성 파일을 편집해야 합니다. [자세히 알아보기](../../delivery/using/spamassassin.md) |
| 배달 기능 보고서 액세스 | 사용 가능 | On-Demand | 사용 가능 | 특정 하이브리드 배포에서는 마케팅 인스턴스에서 전달 가능성 보고서에 액세스할 수 없습니다. |
| LDAP 인증 구성 | 사용할 수 없음 | 사용 가능 | 사용 가능 | LDAP 구성은 온-프레미스 또는 하이브리드 설치에서만 가능합니다. [자세히 알아보기](../../installation/using/connecting-through-ldap.md) |


## Federated Data Access{#fda}

Adobe Campaign provides the **Federated Data Access** (FDA) option in order to process information stored in one or more external databases: you can access external data without changing the structure of Adobe Campaign data. [자세히 알아보기](../../platform/using/about-fda.md)

>[!CAUTION]
>
>FDA를 통해 외부 데이터베이스에 액세스하는 것은 [Snowflake 커넥터를 제외한 온-프레미스 또는 하이브리드 설치에서만 가능합니다](../../platform/using/specific-configuration-database.md#configure-access-to-snowflake).


**자세한 내용은**

* [호환성 매트릭스](../../rn/using/compatibility-matrix.md)
* [릴리스 정보](../../rn/using/latest-release.md)
* [Campaign Classic 업그레이드](../../rn/using/rn-overview.md)
* [사용이 중단되거나 제거된 기능](../../rn/using/deprecated-features.md)
* [Gold Standard 릴리스](../../rn/using/gold-standard.md)
* [Gold Standard 프로그램](https://helpx.adobe.com/kr/campaign/kb/gold-standard.html).
