---
title: 소개
seo-title: 소개
description: 소개
seo-description: null
page-status-flag: never-activated
uuid: 4192a74e-1d4f-4784-80e3-53aaefa9141e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
discoiquuid: 772992bf-588f-42bd-a72a-986a88815264
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 소개{#introduction}

이 섹션에서는 Adobe Campaign, 클라이언트측 및 서버측 업그레이드에 적용할 절차를 소개하고 기존 인스턴스의 유니코드로 전환하는 방법에 대해 설명합니다.

>[!NOTE]
>
>호스팅된 인스턴스의 경우 Adobe 관리자와 협력해야 합니다.\
>온-프레미스 인스턴스의 경우 Adobe 컨설턴트의 지원을 받을 수 있습니다.

업그레이드는 Adobe Campaign이 설치된 모든 서버에 적용되어야 합니다.

1. 리디렉션 및 추적 서버(Apache/IIS)를 마이그레이션합니다.
1. Power Boxer/Cluster 서버를 마이그레이션합니다.
1. 마케팅 서버를 마이그레이션합니다.

Adobe Campaign은 업데이트 중에 조작해야 하는 서버 측에서 실행되는 여러 프로세스를 기반으로 합니다. 특히

* 응용 프로그램 서버(nlserver 웹)
* 배달 서버(nlserver mta)
* 리디렉션 서버(웹 mdl)

>[!NOTE]
>
>다양한 Adobe Campaign 프로세스에 대한 자세한 내용은 [이 섹션을](../../installation/using/general-architecture.md#logical-application-layer)참조하십시오.\
>Power Boxer 또는 Power Cluster 유형 아키텍처를 사용하는 경우 이 프로세스를 모든 Power Boxer/Cluster 서버에 적용해야 합니다.

새 버전에 데이터베이스 구조 변경이 포함된 경우 다음 순서로 서버를 다시 시작하는 것이 좋습니다.

1. 응용 프로그램 서버(nlserver 웹),
1. 리디렉션 서버(웹 mdl),
1. 배달 서버(nlserver mta).

