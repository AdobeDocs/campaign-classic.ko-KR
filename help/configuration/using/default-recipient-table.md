---
title: Adobe Campaign Classic 수신자 테이블 사용
description: 데이터 모델을 디자인할 때 Adobe Campaign Classic에서 즉시 사용 가능한 수신자 테이블을 사용하는 방법을 알아봅니다.
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 65affa58a66090c3bffc837fdbd85aa46338bd3e

---


# 기본 수신자 테이블 사용{#default-recipient-table}

Adobe Campaign의 바로 사용 가능한 수신자 테이블은 데이터 모델을 구축하기 위한 좋은 시작점을 제공합니다. 미리 정의된 필드 및 표 링크가 많이 있으며, 이를 손쉽게 확장할 수 있습니다. 이 기능은 간단한 수신자 중심의 데이터 모델에 적합하므로 주로 수신자를 타깃팅하는 경우에 특히 유용합니다.

표준 수신자 테이블을 사용하면 다음과 같은 이점이 있습니다.

* 구독, 시드 목록, 설문 조사, 소셜 등과 같은 기능을 즉시 사용할 수 있습니다.
* 마케팅 데이터베이스에 수신자 중심의 데이터 모델 제공
* 더욱 빨라진 구현
* 지원 및 파트너의 간편한 유지 관리

하지만 수신자 테이블을 확장할 수는 있지만 표의 필드 또는 링크 수를 줄일 수는 없습니다.

>[!IMPORTANT]
>
>기본 제공 모듈에 오류가 발생할 수 있으므로 수신자 테이블에서 필드를 삭제하지 않는 것이 좋습니다(쓸모 없는 경우에도).

또한 수신자 테이블이 제품의 일부이므로 제품이 변경될 때 테이블과 관련 양식이 모두 진화합니다. 따라서 추가 유지 관리가 필요하여 모든 익스텐션이 업그레이드 시 여전히 유효한지 확인해야 합니다.
