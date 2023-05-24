---
product: campaign
title: 마이그레이션을 시작하기 전
description: 마이그레이션을 시작하기 전
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: migration
content-type: reference
topic-tags: migration-procedure
hide: true
hidefromtoc: true
exl-id: d666bc0b-596a-4908-9364-7df5bb8d68d0
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 2%

---

# 전제 조건{#before-starting-migration}



이 페이지에는 마이그레이션 프로세스를 시작하기 전에 수행할 특정 단계가 나열되어 있습니다. 또한 다음을 참조해야 합니다 [이 페이지](about-migration.md) 추가 지침을 참조하십시오.

>[!NOTE]
>
>이 문서에서는 명령이 샘플로 제공됩니다. 구성에 따라 달라질 수 있습니다.

1. Adobe Campaign 버전 확인: 마이그레이션하기 전에 사용 중인 현재 버전의 최신 빌드를 설치하십시오.
1. 데이터를 백업합니다.
1. 환경을 확인합니다. DBMS(데이터베이스 엔진 시스템)는 변경할 수 없습니다. 예를 들어 PostgreSQL 엔진에서 Oracle 엔진으로 전환할 수 없습니다. 그러나 데이터베이스 엔진의 최신 버전으로 전환할 수 있습니다. 유니코드가 아닌 데이터베이스에서 유니코드 데이터베이스로 이동할 수 없습니다.

## 마이그레이션 단계 {#migration-steps}

마이그레이션 절차는 다음 일자에 수행되어야 합니다. **모두** 서버 및 특정 순서로.

* 의 경우 **독립 실행형 플랫폼** (단일 시스템 모드), 애플리케이션은 완전히 마이그레이션됩니다.
* 의 경우 **표준 플랫폼** (enterprise) 마이그레이션 단계는 다음과 같습니다.

   1. 마케팅 서버 마이그레이션.
   1. 메일 서버(mta)를 마이그레이션합니다.
   1. 리디렉션 및 추적 서버(Apache/IIS)를 마이그레이션합니다.

* 의 경우 **클라우드 메시징 플랫폼**, 실행 서버는 Adobe Campaign에서 호스팅됩니다. 다른 서버 간의 마이그레이션을 조정하려면 Adobe Campaign에 문의하십시오.
* 의 경우 **전원 부스터 또는 전원 클러스터 플랫폼**, 마이그레이션 단계는 다음과 같습니다.

   1. 리디렉션 및 추적 서버(Apache/IIS)를 마이그레이션합니다.
   1. 전원 부스터/클러스터 서버를 마이그레이션합니다.
   1. 마케팅 서버 마이그레이션.

## 사용자 암호 {#user-passwords}

v7에서, **내부** 및 **admin** 운영자 연결은 암호로 보호되어야 합니다. 이러한 계정 및 모든 운영자 계정에 암호를 할당하는 것이 좋습니다. **마이그레이션 전**. 에 대한 암호를 지정하지 않은 경우 **내부**&#x200B;을 클릭하여 연결할 수 없습니다. 암호를 할당하려면 **내부**&#x200B;를 클릭하고 다음 명령을 입력합니다.

```
nlserver config -internalpassword
```

>[!CAUTION]
>
>다음 **내부** 모든 추적 서버에 대해 암호가 동일해야 합니다. 자세한 내용은 [내부 식별자](../../installation/using/configuring-campaign-server.md#internal-identifier) 및 [권한](../../platform/using/access-management.md) 섹션.
