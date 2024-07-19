---
product: campaign
title: 마이그레이션을 시작하기 전
description: 마이그레이션을 시작하기 전
feature: Upgrade
audience: migration
content-type: reference
topic-tags: migration-procedure
hide: true
hidefromtoc: true
exl-id: d666bc0b-596a-4908-9364-7df5bb8d68d0
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 2%

---

# 필수 구성 요소{#before-starting-migration}



이 페이지에는 마이그레이션 프로세스를 시작하기 전에 수행할 특정 단계가 나열되어 있습니다. 또한 자세한 지침은 [이 페이지](about-migration.md)를 참조해야 합니다.

>[!NOTE]
>
>이 문서에서는 명령이 샘플로 제공됩니다. 구성에 따라 달라질 수 있습니다.

1. Adobe Campaign 버전 확인: 마이그레이션하기 전에 사용 중인 현재 버전의 최신 빌드를 설치하십시오.
1. 데이터를 백업합니다.
1. 환경을 확인합니다. DBMS(데이터베이스 엔진 시스템)는 변경할 수 없습니다. 예를 들어 PostgreSQL 엔진에서 Oracle 엔진으로 전환할 수 없습니다. 그러나 데이터베이스 엔진의 최신 버전으로 전환할 수 있습니다. 유니코드가 아닌 데이터베이스에서 유니코드 데이터베이스로 이동할 수 없습니다.

## 마이그레이션 단계 {#migration-steps}

마이그레이션 절차는 **모든** 서버에서 특정 순서로 수행해야 합니다.

* **독립 실행형 플랫폼**(단일 컴퓨터 모드)의 경우 응용 프로그램이 완전히 마이그레이션됩니다.
* **표준 플랫폼**(엔터프라이즈)의 경우 마이그레이션 단계는 다음과 같습니다.

   1. 마케팅 서버 마이그레이션.
   1. 메일 서버(mta)를 마이그레이션합니다.
   1. 리디렉션 및 추적 서버(Apache/IIS)를 마이그레이션합니다.

* **클라우드 메시징 플랫폼**&#x200B;의 경우 실행 서버는 Adobe Campaign에서 호스팅됩니다. 다른 서버 간의 마이그레이션을 조정하려면 Adobe Campaign에 문의하십시오.
* **전원 부스터 또는 전원 클러스터 플랫폼**&#x200B;의 경우 마이그레이션 단계는 다음과 같습니다.

   1. 리디렉션 및 추적 서버(Apache/IIS)를 마이그레이션합니다.
   1. 전원 부스터/클러스터 서버를 마이그레이션합니다.
   1. 마케팅 서버 마이그레이션.

## 사용자 암호 {#user-passwords}

v7에서 **internal** 및 **admin** 연산자 연결은 암호로 보호되어야 합니다. 이러한 계정 및 모든 연산자 계정(**마이그레이션 전**)에 암호를 할당하는 것이 좋습니다. **internal**&#x200B;에 대한 암호를 지정하지 않은 경우 연결할 수 없습니다. **internal**&#x200B;에 암호를 할당하려면 다음 명령을 입력하십시오.

```
nlserver config -internalpassword
```

>[!CAUTION]
>
>**internal** 암호는 모든 추적 서버에 대해 동일해야 합니다. 자세한 내용은 [내부 식별자](../../installation/using/configuring-campaign-server.md#internal-identifier) 및 [권한](../../platform/using/access-management.md) 섹션을 참조하십시오.
