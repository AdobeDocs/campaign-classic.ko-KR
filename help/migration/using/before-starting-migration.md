---
title: 마이그레이션을 시작하기 전에
seo-title: 마이그레이션을 시작하기 전에
description: 마이그레이션을 시작하기 전에
seo-description: null
page-status-flag: never-activated
uuid: b9325510-2fa5-4be4-9cf0-f37232bbbd8c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migration-procedure
discoiquuid: d8877378-fb43-4f32-91c6-60f2f788f916
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f460c79a763c6a207656c54351a4c685f2a78a03

---


# 마이그레이션을 시작하기 전에{#before-starting-migration}

>[!NOTE]
>
>이 문서에서는 데이터베이스에 연결된 명령이 예로 제공됩니다. 구성에 따라 달라질 수 있습니다. 데이터베이스 관리자에게 문의하십시오.

## 경고 {#warnings}

### 설치된 버전 {#installed-version}

마이그레이션하기 전에 사용 중인 현재 버전의 최신 빌드를 설치해야 합니다.

nlserver pdump 명령을 사용하여 클라이언트 콘솔의 **[!UICONTROL Help> About]** 메뉴로 이동하여 서버의 버전을 **확인합니다** .

### 데이터 백업 {#data-backup}

마이그레이션 프로세스를 시작하기 전에 데이터를 백업해야 **합니다** .

### 환경 {#environment}

* 데이터베이스 엔진 유형(DBMS)을 변경할 수 없습니다. 예를 들어 PostgreSQL 엔진에서 Oracle 엔진으로 전환할 수 없습니다. 그러나 Oracle 8 엔진에서 Oracle 10 엔진으로 전환할 수 있습니다.
* 유니코드가 아닌 데이터베이스에서 유니코드 데이터베이스로 이동할 수 없습니다.

### 권장 사항 {#recommendation}

마이그레이션 절차가 특히 민감하므로 절차를 시작하기 전에 이 문서를 철저히 읽는 것이 좋습니다.

## 마이그레이션 단계 {#migration-steps}

마이그레이션 절차는 **모든** 서버와 특정 순서로 수행되어야 합니다.

* 독립 **실행형 플랫폼** (단일 시스템 모드)의 경우 애플리케이션이 완전히 마이그레이션됩니다.
* 표준 플랫폼 **** (기업)의 경우 마이그레이션 단계는 다음과 같습니다.

   1. 마케팅 서버를 마이그레이션합니다.
   1. 메일 서버(mta)를 마이그레이션합니다.
   1. 리디렉션 및 추적 서버(Apache / IIS)를 마이그레이션합니다.

* 클라우드 메시지 **플랫폼의**&#x200B;경우 실행 서버는 Adobe Campaign에서 호스팅됩니다. 다른 서버 간 마이그레이션을 조정하려면 Adobe Campaign에 문의하십시오.
* Power Booter 또는 **Power Cluster 플랫폼의**&#x200B;경우 마이그레이션 단계는 다음과 같습니다.

   1. 리디렉션 및 추적 서버(Apache / IIS)를 마이그레이션합니다.
   1. Power Boxer/Cluster 서버를 마이그레이션합니다.
   1. 마케팅 서버를 마이그레이션합니다.

>[!NOTE]
>
>v6.02 마케팅 서버와 v7 클라우드 메시징 또는 Power Boxer/Cluster 서버 간의 통신이 가능합니다. 그러나 v6.02 마케팅 서버를 유지하려는 경우 클라우드 메시지 전달 또는 Power Boxer/클러스터로 마이그레이션하기 전에 최신 v6.02 빌드로 업데이트해야 합니다.

## 사용자 암호 {#user-passwords}

v7에서 **내부** 및 **관리자** 연산자 연결은 암호로 보호되어야 합니다. 마이그레이션 **전에 이러한 계정 및 모든 연산자 계정에 암호를 지정하는 것이 좋습니다**. **내부**&#x200B;암호를 지정하지 않은 경우 연결할 수 없습니다. 암호를 **내부**&#x200B;계정에 할당하려면 다음 명령을 입력합니다.

```
nlserver config -internalpassword
```

>[!CAUTION]
>
>모든 추적 서버에 대해 **내부** 암호가 동일해야 합니다. 자세한 내용은 내부 식별자 [및](../../installation/using/campaign-server-configuration.md#internal-identifier) 권한 [섹션을](../../platform/using/access-management.md#about-permissions) 참조하십시오.

