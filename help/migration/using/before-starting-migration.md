---
solution: Campaign Classic
product: campaign
title: 마이그레이션을 시작하기 전
description: 마이그레이션을 시작하기 전
audience: migration
content-type: reference
topic-tags: migration-procedure
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 1%

---


# 마이그레이션을 시작하기 전{#before-starting-migration}

>[!NOTE]
>
>이 문서에서는 데이터베이스에 연결된 명령이 예로 제공됩니다. 구성에 따라 달라질 수 있습니다. 데이터베이스 관리자에게 문의하십시오.

## 경고 {#warnings}

* 마이그레이션 프로세스는 전문가 사용자만 수행해야 합니다. Adobe Campaign의 데이터베이스 전문가, 시스템 관리자 및 애플리케이션 개발자의 도움을 받아야 합니다.
* 마이그레이션을 시작하기 전에 사용하는 시스템 및 시스템 구성 요소가 실제로 v7과 호환되는지 확인하십시오. [호환성 매트릭스](../../rn/using/compatibility-matrix.md)를 참조하십시오.
* Adobe Campaign 클라우드 메시지(중간 소싱)를 사용하는 경우 전체 마이그레이션 절차를 시작하기 전에 Adobe에 문의하십시오.
* 마이그레이션 프로세스를 시작하기 전에 **반드시**&#x200B;데이터를 백업해야 합니다.
* 마이그레이션 프로세스를 완료하는 데 며칠이 걸릴 수 있습니다.
* Adobe Campaign v7은 구성 측면에서 5.11 및 6.02 버전보다 엄격합니다. 데이터 손상 등의 문제를 방지하고 데이터베이스의 데이터 무결성을 유지하는 것이 주 목적입니다. 따라서 v5.11 및 v6.02에서 제공되는 특정 기능은 v7에서 더 이상 작동하지 않을 수 있으므로 마이그레이션 후 수정해야 할 수 있습니다. 제작 작업을 시작하기 전에 모든 구성, 특히 Adobe Campaign 사용에 필요한 워크플로우를 체계적으로 테스트하는 것이 좋습니다.

### 설치된 버전 {#installed-version}

마이그레이션하기 전에 사용 중인 현재 버전의 최신 빌드를 설치해야 합니다.

**nlserver pdump** 명령을 사용하여 클라이언트 콘솔의 **[!UICONTROL Help> About]** 메뉴로 이동하여 서버의 버전을 확인합니다.

### 데이터 백업 {#data-backup}

마이그레이션 프로세스를 시작하기 전에 **반드시**&#x200B;데이터를 백업해야 합니다.

### 환경 {#environment}

* 데이터베이스 엔진 유형(DBMS)은 변경할 수 없습니다. 예를 들어 PostgreSQL 엔진에서 Oracle 엔진으로 전환할 수 없습니다. 그러나 Oracle 8 엔진에서 Oracle 10 엔진으로 전환할 수 있습니다.
* 유니코드가 아닌 데이터베이스에서 유니코드 데이터베이스로 이동할 수 없습니다.

### 권장 사항 {#recommendation}

마이그레이션 절차는 민감하므로 절차를 시작하기 전에 이 문서를 철저히 읽는 것이 좋습니다.

## 마이그레이션 단계 {#migration-steps}

마이그레이션 절차는 **모든** 서버 및 특정 순서로 수행되어야 합니다.

* **독립 실행형 플랫폼**(단일 컴퓨터 모드)의 경우 응용 프로그램이 완전히 마이그레이션됩니다.
* **표준 플랫폼**(기업)의 경우 마이그레이션 단계는 다음과 같습니다.

   1. 마케팅 서버를 마이그레이션합니다.
   1. 메일 서버(mta)를 마이그레이션합니다.
   1. 리디렉션 및 추적 서버(Apache / IIS)를 마이그레이션합니다.

* **클라우드 메시지 플랫폼**&#x200B;의 경우 실행 서버는 Adobe Campaign에서 호스팅됩니다. 다른 서버 간 마이그레이션을 조정하려면 Adobe Campaign에 문의하십시오.
* **Power Booter 또는 Power Cluster 플랫폼**&#x200B;의 경우 마이그레이션 단계는 다음과 같습니다.

   1. 리디렉션 및 추적 서버(Apache / IIS)를 마이그레이션합니다.
   1. Power Boxer/Cluster 서버를 마이그레이션합니다.
   1. 마케팅 서버를 마이그레이션합니다.

## 사용자 암호 {#user-passwords}

v7에서 **내부** 및 **admin** 연산자 연결은 암호로 보호해야 합니다. 마이그레이션&#x200B;**전에 이 계정과 모든 연산자 계정인**&#x200B;에 암호를 할당하는 것이 좋습니다. **내부**&#x200B;에 대한 암호를 지정하지 않은 경우 연결할 수 없습니다. **internal**&#x200B;에 암호를 할당하려면 다음 명령을 입력합니다.

```
nlserver config -internalpassword
```

>[!IMPORTANT]
>
>**내부** 암호는 모든 추적 서버에 대해 동일해야 합니다. 자세한 내용은 [내부 식별자](../../installation/using/campaign-server-configuration.md#internal-identifier) 및 [권한 ](../../platform/using/access-management.md#about-permissions) 섹션을 참조하십시오.

