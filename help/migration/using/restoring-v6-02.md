---
title: v6.02 복원
seo-title: v6.02 복원
description: v6.02 복원
seo-description: null
page-status-flag: never-activated
uuid: df21209b-4825-42fa-a303-f383f872abb5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: rollback
discoiquuid: 4f65ba19-e9f0-4425-b640-f27c61394859
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 9%

---


# v6.02 복원{#restoring-v}

v7에서 v6.02를 복원하는 절차입니다.

1. 데이터베이스의 백업을 복구하고 복원합니다.
1. Neolane v6.back **폴더(Linux의** nl6.back **)를 복구한 후** Neolane v6 **(Linux의****** nl6)로 이름을 변경하고 원래 위치로 복원합니다.
1. 수신 포트를 다시 할당하여 IIS 웹 사이트 수준에서 Adobe Campaign v6.02의 통합을 다시 설정하여 IIS를 다시 구성합니다.
1. Adobe Campaign v6.1 서비스를 중지합니다.
1. IIS를 다시 시작합니다.
1. Adobe Campaign v6.02 서비스를 다시 시작합니다.

