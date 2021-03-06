---
product: campaign
title: 이전 버전으로 롤백
description: 이전 버전으로 롤백하는 방법을 알아봅니다.
audience: migration
content-type: reference
topic-tags: rollback
exl-id: 5120a7c4-3760-48d9-94da-d587d333e8d8
source-git-commit: 8610d29a3df1080f1622a2cb3685c0961fb40092
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# 이전 버전으로 롤백{#about-rollback}

![](../../assets/v7-only.svg)

마이그레이션 후 문제가 발생하면 이전 버전의 Campaign으로 롤백해야 할 수 있습니다.

롤백 절차는 Campaign의 초기 버전에 따라 다릅니다.

## Campaign v6.1로 복원

v7에서 v6.1을 복원하는 절차는 다음과 같습니다.

1. 데이터베이스의 백업을 복구하여 복원합니다.
1. 복구 **Adobe Campaign v6.back** 폴더 (**nl6.back** Linux에서 (으)로 이름을 변경합니다. **Adobe Campaign v6** (**nl6** Linux에서)를 사용하여 원래 위치로 복원합니다.
1. 수신 포트를 다시 할당하여 IIS 웹 사이트 수준에서 Adobe Campaign v6.1의 통합을 다시 설정하여 IIS를 다시 구성합니다.
1. Adobe Campaign v7 서비스를 중지합니다.
1. IIS를 다시 시작합니다.
1. Adobe Campaign v6.1 서비스를 다시 시작합니다.

## Campaign v6.02로 복원

v7에서 v6.02를 복원하는 절차는 다음과 같습니다.

1. 데이터베이스의 백업을 복구하여 복원합니다.
1. 복구 **Neolane v6.back** 폴더 (**nl6.back** Linux에서 (으)로 이름을 변경합니다. **Neolane v6** (**nl6** Linux에서)를 사용하여 원래 위치로 복원합니다.
1. 수신 포트를 다시 할당하여 IIS 웹 사이트 수준에서 Adobe Campaign v6.02의 통합을 다시 설정하여 IIS를 다시 구성합니다.
1. Adobe Campaign v6.1 서비스를 중지합니다.
1. IIS를 다시 시작합니다.
1. Adobe Campaign v6.02 서비스를 다시 시작합니다.

## Campaign v5.11로 복원

v7에서 v5.11을 복원하는 절차는 다음과 같습니다.

1. 데이터베이스의 백업을 복구하여 복원합니다.
1. 복구 **Neolane v5.back** 폴더 (**nl5.back** Linux에서 (으)로 이름을 변경합니다. **Neolane v5** (**nl5** Linux에서)를 사용하여 원래 위치로 복원합니다.
1. 수신 포트를 다시 할당하여 IIS 웹 사이트 수준에서 Neolane v5 통합을 다시 설정하여 IIS를 다시 구성합니다.
1. Adobe Campaign v7 서비스를 중지합니다.
1. IIS를 다시 시작합니다.
1. Adobe Campaign v5 서비스를 다시 시작합니다.
