---
solution: Campaign Classic
product: campaign
title: 캠페인 온-프레미스, 하이브리드 및 호스팅 기능 매트릭스
description: 호스팅 및 온-프레미스 배포 간의 주요 차이점 확인
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 18%

---


# 기능 매트릭스 {#capability-matrix-per-model}

Adobe Campaign Classic에는 모듈 및 옵션 세트가 포함되어 있습니다. 이러한 모듈 및 모듈의 사용 가능 여부는 설치 배포 유형에 따라 다릅니다. 이 문서에서는 완전히 호스팅된(Managed Services)과 온-프레미스 배포 간의 특정 기능에 대한 주요 차이점에 대해 자세히 설명합니다.

이 페이지에는 호스팅(Managed Services)과 온-프레미스 배포 간의 주요 차이점이 표시됩니다. 하이브리드 배포 지정은 Adobe에서 호스팅하고 사내 시스템에 호스팅되는 요소에 따라 다릅니다.

다른 호스팅 모델은 이 섹션](../../installation/using/hosting-models.md)에 [이 도입되었습니다.

## 배포 모델당 가용성 {#capability-matrix}

| 기능 | 호스팅 | 하이브리드 | 온-프레미스 | 세부 정보 |
|-----------------------------------------------|------------------|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 캠페인 서버 구성 | On-Demand | 사용 가능 | 사용 가능 | [자세히 알아보기](../../installation/using/the-server-configuration-file.md) |
| 이메일 숨은 참조 | On-Demand | On-Demand | 사용 가능 | [자세히 알아보기](../../installation/using/email-archiving.md) |
| 메시지 센터 실행 인스턴스 관리 | On-Demand | On-Demand | 사용 가능 | [자세히 알아보기](../../message-center/using/about-transactional-messaging.md) |
| 중간 소싱 플랫폼 관리 | On-Demand | On-Demand | 사용 가능 | [자세히 알아보기](../../installation/using/mid-sourcing-server.md) |
| 리트머스 를 통한 받은 편지함 렌더링 | On-Demand | On-Demand | 사용 가능 | [자세히 알아보기](../../delivery/using/inbox-rendering.md) |
| IMS와 통합(Adobe ID) | On-Demand | On-Demand | On-Demand | [자세히 알아보기](../../integrations/using/about-adobe-id.md) |
| 파일 전송에 대한 데이터 암호화/암호 해독 | On-Demand | 사용 가능 | 사용 가능 | [자세히 알아보기](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing) |
| 파일 지핑/압축 해제 | On-Demand | 사용 가능 | 사용 가능 | [자세히 알아보기](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing) |
| 도메인 이름 위임 | On-Demand | On-Demand | 사용할 수 없음 | [자세히 알아보기](https://helpx.adobe.com/kr/campaign/kb/domain-name-delegation.html) |
| SpamCharacter 설치 | On-Demand | 사용 가능 | 사용 가능 | [자세히 알아보기](../../delivery/using/spamassassin.md) |
| 배달 가능 보고서 액세스 | 사용 가능 | On-Demand | 사용 가능 | [자세히 알아보기](../../delivery/using/monitoring-deliverability.md) |
| LDAP 인증 구성 | 사용할 수 없음 | 사용 가능 | 사용 가능 | [자세히 알아보기](../../installation/using/connecting-through-ldap.md) |


## 통합 데이터 액세스{#fda}

Adobe Campaign은 하나 이상의 외부 데이터베이스에 저장된 정보를 처리하기 위해 **Federated Data Access**(FDA) 옵션을 제공합니다.adobe campaign 데이터 구조를 변경하지 않고 외부 데이터에 액세스할 수 있습니다. [자세히 알아보기](../../installation/using/about-fda.md)

>[!CAUTION]
>
>FDA를 통해 외부 데이터베이스에 액세스하는 것은 [Snowflake 커넥터](../../installation/using/configure-fda-snowflake.md)를 제외하고 온-프레미스 또는 하이브리드 설치에서만 가능합니다.


**참조 항목**

* [호환성 매트릭스](../../rn/using/compatibility-matrix.md)
* [릴리스 정보](../../rn/using/latest-release.md)
* [Campaign Classic 업그레이드](../../rn/using/rn-overview.md)
* [사용이 중단되거나 제거된 기능](../../rn/using/deprecated-features.md)
* [Gold Standard 릴리스](../../rn/using/gold-standard.md)
* [Gold Standard 프로그램](https://helpx.adobe.com/kr/campaign/kb/gold-standard.html)
