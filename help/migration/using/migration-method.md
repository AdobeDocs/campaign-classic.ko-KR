---
title: 마이그레이션 방법
seo-title: 마이그레이션 방법
description: 마이그레이션 방법
seo-description: null
page-status-flag: never-activated
uuid: 6b954d5b-cfa3-43c6-ac3d-da9185e9e9d1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migration-overview
discoiquuid: 3ac779a7-1f91-4c1c-a439-10d01697326a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9f7cf3d530f141a661df5fcc8cbcf0bb4c8d3e89

---


# 마이그레이션 방법{#migration-method}

## 환경 현대화 {#modernizing-your-environment}

마이그레이션을 수행하는 것은 환경을 업데이트하는 기회가 될 수 있습니다(데이터베이스 엔진, 운영 체제). Adobe Campaign에서는 프로덕션 환경을 최신 버전으로 업그레이드할 것을 적극 권장합니다.

32비트 버전 데이터베이스 및 운영 체제는 여전히 v7에서 지원되지만 Adobe Campaign의 향후 버전에서는 더 이상 지원되지 않습니다. 최대한 빨리 64비트로 업그레이드할 것을 적극 권장합니다.

v6.02에서 &quot;multi timezone&quot; 모드는 PostgreSQL 데이터베이스 엔진에만 사용할 수 있었습니다. 이제 데이터베이스 엔진 유형에 상관없이 제공됩니다. 기본 시간대를 &quot;다중 시간대&quot; 기준으로 변경하는 것이 좋습니다. 자세한 내용은 시간대 [섹션을](../../migration/using/general-configurations.md#time-zones) 참조하십시오.

>[!IMPORTANT]
>
>Adobe Campaign 5.11 및 6.02에서 지원되는 일부 소프트웨어 버전은 더 이상 Adobe Campaign v7에서 지원되지 않습니다.
>
>Adobe Campaign에서 지원하는 버전에 대한 자세한 내용은 [호환성 매트릭스를](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)참조하십시오.

## 주요 마이그레이션 단계 {#key-migration-steps}

Adobe Campaign v7으로 마이그레이션하는 일반적인 절차는 마이그레이션 시작 [전](../../migration/using/before-starting-migration.md) 섹션에 자세히 설명되어 있습니다.

Adobe Campaign v7로의 마이그레이션에 대한 구현 단계는 Adobe Campaign 7 [로 마이그레이션하기 위한 사전 요구 사항 섹션에 자세히 설명되어](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) 있습니다.

필요한 구성은 기존 구성과 플랫폼의 초기 버전에 따라 다릅니다. 이러한 내용은 일반 [구성](../../migration/using/general-configurations.md) 섹션에 요약되어 있습니다.

## 특정 구성 {#specific-configurations}

Adobe Campaign v7에서 발생한 변경 사항은 이전 버전에서 개발된 특정 구성을 수정해야 함을 의미할 수도 있습니다. 따라서 마이그레이션 전에 모든 구성에 대한 감사를 수행해야 할 수 있습니다.자세한 내용은 Adobe Campaign에 문의하십시오.

예를 들어 웹 응용 프로그램에 대한 특정 설정, SQLdata를 사용한 스키마 확장 또는 기본 스키마 복제에 대한 특정 주의가 필요합니다. 자세한 내용은 플랫폼 [구성](../../migration/using/configuring-your-platform.md) 섹션을 참조하십시오.

마찬가지로, Adobe Campaign에서 강화된 보안에 응답하기 위해 일부 내부 메커니즘이 수정되었습니다.이러한 구성을 적용해야 합니다.
