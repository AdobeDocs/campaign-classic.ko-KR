---
product: campaign
title: 마이그레이션을 시작하기 전
description: 마이그레이션을 시작하기 전
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: d666bc0b-596a-4908-9364-7df5bb8d68d0
source-git-commit: 8610d29a3df1080f1622a2cb3685c0961fb40092
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 2%

---

# 필수 구성 요소{#before-starting-migration}

![](../../assets/v7-only.svg)

이 페이지에는 마이그레이션 프로세스를 시작하기 전에 수행할 특정 단계가 나열됩니다. 또한 [이 페이지](about-migration.md) 추가 지침

>[!NOTE]
>
>이 문서에서 명령은 샘플로 제공됩니다. 구성에 따라 달라질 수 있습니다.

1. Adobe Campaign 버전을 확인합니다. 마이그레이션하기 전에 사용 중인 현재 버전의 최신 빌드를 설치하십시오.
1. 데이터를 백업합니다.
1. 환경을 확인합니다. 데이터베이스 엔진 시스템(DBMS)은 변경할 수 없습니다. 예를 들어 PostgreSQL 엔진에서 Oracle 엔진으로 전환할 수 없습니다. 그러나 데이터베이스 엔진의 최신 버전으로 전환할 수 있습니다. 유니코드가 아닌 데이터베이스에서 유니코드 데이터베이스로 이동할 수 없습니다.

## 마이그레이션 단계 {#migration-steps}

마이그레이션 절차는 계속 수행되어야 합니다 **모두** 특정 순서로 서버와

* 의 경우 **독립형 플랫폼** (단일 시스템 모드) 애플리케이션을 완전히 마이그레이션합니다.
* 의 경우 **표준 플랫폼** (enterprise) 마이그레이션 단계는 다음과 같습니다.

   1. 마케팅 서버를 마이그레이션합니다.
   1. 메일 서버(mta)를 마이그레이션합니다.
   1. 리디렉션 및 추적 서버(Apache/IIS)를 마이그레이션합니다.

* 의 경우 **클라우드 메시징 플랫폼**&#x200B;로 지정하는 경우 실행 서버는 Adobe Campaign에서 호스팅됩니다. 다른 서버 간의 마이그레이션을 조정하려면 Adobe Campaign에 문의하십시오.
* 의 경우 **전원 부스터 또는 전원 클러스터 플랫폼**, 마이그레이션 단계는 다음과 같습니다.

   1. 리디렉션 및 추적 서버(Apache/IIS)를 마이그레이션합니다.
   1. 전원 부스터/클러스터 서버를 마이그레이션합니다.
   1. 마케팅 서버를 마이그레이션합니다.

## 사용자 암호 {#user-passwords}

v7에서, **내부** 및 **관리** 연산자 연결은 암호로 보호해야 합니다. 이러한 계정 및 모든 운영자 계정에 암호를 지정하는 것이 좋습니다. **마이그레이션 전**. 암호를 지정하지 않은 경우 **내부**&#x200B;연결할 수 없습니다. 암호를 **내부**&#x200B;를 입력하여 다음 명령을 입력합니다.

```
nlserver config -internalpassword
```

>[!CAUTION]
>
>다음 **내부** 암호는 모든 추적 서버에 대해 동일해야 합니다. 자세한 내용은 [내부 식별자](../../installation/using/configuring-campaign-server.md#internal-identifier) 및 [권한](../../platform/using/access-management.md) 섹션에 자세히 설명되어 있습니다.
