---
title: v5.11 복원
seo-title: v5.11 복원
description: v5.11 복원
seo-description: null
page-status-flag: never-activated
uuid: 4480c97c-5845-483c-a17b-644f05783b4e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: rollback
discoiquuid: ef778333-8e50-402b-9a69-78ac94497c67
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9482a99c3be164651b3428179388cb0a8a75783f

---


# v5.11 복원{#restoring-v}

v7에서 v5.11을 복원하는 절차는 다음과 같습니다.

1. 데이터베이스의 백업을 복구하고 복원합니다.
1. Neolane v5.back **폴더(Linux의** nl5.back **)를** 복구한 다음 Neolane v5 **(Linux의****** nl5)로 이름을 변경한 다음 원래 위치로 복원합니다.
1. IIS 웹 사이트 수준에서 Neolane v5의 통합을 다시 설정하기 위해 수신 포트를 다시 할당하여 IIS를 다시 구성합니다.
1. Adobe Campaign v7 서비스를 중지합니다.
1. IIS를 다시 시작합니다.
1. Adobe Campaign v5 서비스를 다시 시작합니다.

