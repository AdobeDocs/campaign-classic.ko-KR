---
product: campaign
title: 소개
description: 소개
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 3e39a0d2-ff7e-4233-82bb-2b360f696a33
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 1%

---

# 소개{#introduction}

![](../../assets/v7-only.svg)

이 섹션에서는 Adobe Campaign, 클라이언트측 및 서버측 업그레이드에 적용할 절차에 대해 설명하고 기존 인스턴스의 유니코드로 전환하는 방법에 대해 설명합니다.

>[!NOTE]
>
>호스팅된 인스턴스의 경우 Adobe 관리자와 함께 조정해야 합니다.\
>온-프레미스 인스턴스의 경우 Adobe 컨설턴트의 지원을 받을 수 있습니다.

Adobe Campaign이 설치된 모든 서버에 업그레이드를 적용해야 합니다.

1. 리디렉션 및 추적 서버 마이그레이션(Apache/IIS).
1. 전원 부스터/클러스터 서버를 마이그레이션합니다.
1. 마케팅 서버를 마이그레이션합니다.

Adobe Campaign은 업데이트 중에 조작해야 하는 서버 측에서 실행되는 여러 프로세스, 특히 다음과 같은 사항을 기반으로 합니다.

* 응용 프로그램 서버(nlserver 웹)
* 배달 서버(nlserver mta)
* 리디렉션 서버(webmdl)

>[!CAUTION]
>
>클라이언트 콘솔은 서버 인스턴스와 동일한 빌드에 있어야 합니다.

>[!NOTE]
>
>다양한 Adobe Campaign 프로세스에 대한 자세한 내용은 [이 섹션](../../installation/using/general-architecture.md#logical-application-layer).\
>전원 부스터 또는 전원 클러스터 유형 아키텍처를 사용하는 경우 이 프로세스를 모든 전원 부스터/클러스터 서버에 적용해야 합니다.

새 버전에 데이터베이스 구조가 변경되는 경우 다음 순서로 서버를 다시 시작하는 것이 좋습니다.

1. 애플리케이션 서버(nlserver 웹),
1. 리디렉션 서버(웹 mdl),
1. 배달 서버(nlserver mta).
