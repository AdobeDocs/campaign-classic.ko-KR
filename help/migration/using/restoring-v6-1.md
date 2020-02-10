---
title: v6.1 복원
seo-title: v6.1 복원
description: v6.1 복원
seo-description: null
page-status-flag: never-activated
uuid: 3fb71b6f-4d70-4814-a885-4d414a542eca
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: rollback
discoiquuid: e510482c-a56d-4254-90f8-19bd5c545e30
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9482a99c3be164651b3428179388cb0a8a75783f

---


# v6.1 복원{#restoring-v}

v7에서 v6.1을 복원하는 절차입니다.

1. 데이터베이스의 백업을 복구하고 복원합니다.
1. Adobe Campaign **v6.back** 폴더(Linux의&#x200B;**nl6.back** )를 복구한 다음 Adobe Campaign v6 **(Linux의** nl6 **** )로 이름을 변경하고 원래 위치로 복원합니다.
1. 수신 포트를 다시 할당하여 IIS 웹 사이트 수준에서 Adobe Campaign v6.1의 통합을 다시 설정하여 IIS를 다시 구성합니다.
1. Adobe Campaign v7 서비스를 중지합니다.
1. IIS를 다시 시작합니다.
1. Adobe Campaign v6.1 서비스를 다시 시작합니다.

