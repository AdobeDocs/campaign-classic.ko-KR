---
product: campaign
title: 소개
description: 소개
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 3e39a0d2-ff7e-4233-82bb-2b360f696a33
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 1%

---

# 소개{#introduction}



이 섹션에서는 Adobe Campaign, 클라이언트측 및 서버측을 업그레이드하는 데 적용할 절차를 설명하고 기존 인스턴스의 유니코드로 전환하는 방법에 대해 설명합니다.

>[!NOTE]
>
>호스팅/Managed Services 인스턴스의 경우 Adobe 관리자와 상의해야 합니다.\
>온프레미스 인스턴스의 경우 Adobe 컨설턴트의 지원을 받을 수 있습니다.

업그레이드는 Adobe Campaign이 설치된 모든 서버에 적용되어야 합니다.

1. 리디렉션 및 추적 서버(Apache/IIS)를 마이그레이션합니다.
1. 전원 부스터/클러스터 서버를 마이그레이션합니다.
1. 마케팅 서버 마이그레이션.

Adobe Campaign은 업데이트 중에 조작해야 하는 서버측에서 실행되는 여러 프로세스를 기반으로 합니다. 특히 다음과 같습니다.

* 애플리케이션 서버(nlserver 웹)
* 게재 서버(nlserver mta)
* 리디렉션 서버(webmdl)

>[!CAUTION]
>
>클라이언트 콘솔은 서버 인스턴스와 동일한 빌드에 있어야 합니다.

>[!NOTE]
>
>다양한 Adobe Campaign 프로세스에 대한 자세한 내용은 [이 섹션](../../installation/using/general-architecture.md#logical-application-layer).\
>Power Booster 또는 Power Cluster 유형 아키텍처를 사용하는 경우 모든 Power Booster/Cluster 서버에 이 프로세스를 적용해야 합니다.

새 버전에 데이터베이스 구조 변경이 포함된 경우 다음 순서로 서버를 다시 시작하는 것이 좋습니다.

1. 애플리케이션 서버(nlserver 웹),
1. 리디렉션 서버(webmdl),
1. 게재 서버(nlserver mta).
