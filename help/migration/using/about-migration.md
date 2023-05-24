---
product: campaign
title: Campaign Classic으로 마이그레이션
description: 이전 Campaign 버전에서 Campaign Classic으로 마이그레이션하는 방법에 대해 알아봅니다.
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: migration
content-type: reference
topic-tags: migration-overview
hide: true
hidefromtoc: true
exl-id: 3050238d-6f77-4ffa-9aef-677ab8009388
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 3%

---

# 마이그레이션 시작{#about-migration}



이 문서에서는 마이그레이션에 대한 사전 요구 사항 및 Adobe Campaign Classic v7으로 마이그레이션하는 단계에 대해 자세히 설명합니다. 단계 및 옵션 설정은 구성에 따라 다릅니다.

이주 과정은 신중하게 수행되어야 하며, 그 영향은 사전에 충분히 고려되어야 하고 절차는 엄격하게 수행되어야 한다. 전문가 사용자만 수행해야 합니다. 다음으로 연락하는 것이 좋습니다. [Adobe 고객 지원 센터](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 마이그레이션 절차를 시작하기 전에

마이그레이션이 오류 없이 원활하게 실행되는지 확인하기 위해 테스트/스테이징 환경에서 미리 테스트해야 합니다. 프로덕션 환경 마이그레이션은 마이그레이션된 테스트 환경의 유효성을 완전히 검사한 후에만 수행해야 합니다.

>[!NOTE]
>
>Adobe Campaign v7의 새로운 기능 및 향상된 기능은 [릴리스 정보](../../rn/using/latest-release.md).


## 전제 조건

* 마이그레이션 프로세스는 전문가 사용자가 수행해야 합니다. Adobe Campaign에서 적어도 데이터베이스 전문가, 시스템 관리자 및 애플리케이션 개발자의 도움을 받아야 합니다.
* 마이그레이션을 시작하기 전에 사용하는 시스템 및 시스템 구성 요소가 v7과 호환되는지 확인하십시오. [자세히 알아보기](../../rn/using/compatibility-matrix.md)
* Adobe Campaign 클라우드 메시징(중간 소싱 배포)을 사용하는 경우 시작하기 전에 Adobe 고객 지원 센터에 문의하십시오.
* 마이그레이션 프로세스를 시작하기 전에 **필수** 데이터를 백업합니다.
* 마이그레이션 프로세스를 완료하는 데 며칠이 걸릴 수 있습니다.
* Adobe Campaign v7은 이전 버전보다 안전한 버전입니다. 이는 데이터 손상과 같은 문제를 방지하고 데이터베이스의 데이터 무결성을 유지하기 위한 구성 지침에 영향을 줍니다. 고객은 워크플로우를 포함한 모든 구성을 테스트할 책임이 있습니다.

에서 추가 전제 조건을 사용할 수 있습니다. [이 페이지](../../migration/using/before-starting-migration.md).


## 현대화 된 환경 {#modernizing-your-environment}

마이그레이션을 수행하면 환경(데이터베이스 엔진, 운영 체제)을 업데이트할 수 있습니다. Adobe Campaign은 프로덕션 환경을 최신 버전으로 업그레이드할 것을 강력히 권장합니다.

>[!CAUTION]
>
>Adobe Campaign v7에서 지원하는 버전에 대한 자세한 내용은 [호환성 매트릭스](../../rn/using/compatibility-matrix.md).

## 주요 마이그레이션 단계 {#key-migration-steps}

Adobe Campaign v7으로 마이그레이션하는 일반 절차는에 자세히 설명되어 있습니다. [이 페이지](../../migration/using/before-starting-migration.md).


## 특정 구성 {#specific-configurations}

Adobe Campaign v7에서 수행한 변경 사항은 이전 버전에서 개발된 특정 구성을 조정해야 함을 의미할 수도 있습니다. 따라서 마이그레이션 전에 모든 구성에 대한 감사를 수행해야 할 수 있습니다. 도움이 필요하면 Adobe Campaign에 문의하십시오.

예를 들어 웹 응용 프로그램, SQLdata를 사용한 스키마 확장 또는 기본 스키마 복제에 대한 특정 설정에 특히 주의해야 합니다. 자세한 정보는 [이 페이지](../../migration/using/configuring-your-platform.md)를 참조하십시오.

마찬가지로, Adobe Campaign 내의 강화된 보안에 대응하기 위해 일부 내부 메커니즘이 수정되었습니다. 이러한 구성을 그에 따라 조정해야 합니다.

