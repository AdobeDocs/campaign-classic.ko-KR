---
title: 백업
seo-title: 백업
description: 백업
seo-description: null
page-status-flag: never-activated
uuid: 50134154-a671-4534-b48d-a9e2c42e8f1a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: data-processing
discoiquuid: 870ab0f2-1bd7-42e7-8d83-a08a520b6587
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 2%

---


# 백업{#backup}

시스템 상의 문제(물리적 또는 시스템 관련 문제)가 발생하는 경우 데이터가 손실되지 않도록 백업하려면 반드시 필요합니다.

데이터는 두 개의 서로 다른 위치에 저장됩니다.

* 물리적 파일은 Adobe Campaign 디렉토리에 저장됩니다.
* 다른 데이터는 데이터베이스에 저장됩니다.

대부분의 데이터가 데이터베이스에 있습니다. 백업할 정보의 99%를 나타냅니다.

## 물리적 파일 {#physical-files}

파일은 다음과 같은 여러 범주로 구분됩니다.

* 구성 파일( **nl6/conf에 위치)**

   Adobe Campaign을 신속하게 재구성할 수 있습니다.

* 리디렉션 파일 ** nl6/var/`<instancename>`/redir**

   추적 서버(일명 &#39;전두엽&#39;)에 있으며 모든 이전 캠페인 리디렉션을 포함합니다. 이전 캠페인에서 여전히 사용됩니다.

* 로그 파일: **nl6/var/`<instancename>`/log**

   이것들은 문제를 추적하는 데 사용될 수 있다.

백업할 디렉토리는 다음과 같습니다.

* nl6/conf

* nl6/var/`<instanceName>`/redir(각 인스턴스에 대해)

* nl6/var/`<instanceName>`/log(선택 사항)

* nl6/var/`<instanceName>`/relay(선택 사항)

>[!CAUTION]
>
>데이터베이스를 백업하는 것이 중요합니다.

## 데이터베이스 {#database}

데이터베이스에는 모든 비즈니스 라인 데이터는 물론 Adobe Campaign 리치 클라이언트 콘솔에 표시되는 모든 정보가 포함되어 있습니다.

호스팅 회사와 특히 데이터베이스 관리자는 이 작업을 담당합니다.
