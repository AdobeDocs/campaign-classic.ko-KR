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
source-git-commit: 620724e283215df1fb3f10bd0211652b36284b57

---


# 데이터 모델 모범 사례{#data-model-best-practices}

다음은 큰 테이블과 복잡한 조인을 사용하여 데이터 모델을 디자인할 때 따라야 하는 몇 가지 우수 사례입니다.

* 추가 사용자 지정 수신자 테이블을 사용할 때는 각 배달 매핑에 대한 전용 로그 테이블이 있어야 합니다.
* 특히 사용하지 않은 열을 식별하여 열 수를 줄입니다.
* 여러 조건 및/또는 여러 열에 연결된 경우와 같이 복잡한 조인을 방지하여 데이터 모델 관계를 최적화합니다.
* 조인 키의 경우 항상 문자 문자열이 아닌 숫자 데이터를 사용합니다.
* 로그 보존 깊이를 최대한 줄일 수 있습니다. 더 깊은 작업 내역이 필요한 경우 계산 및/또는 사용자 정의 로그 테이블을 처리하여 더 큰 내역을 저장할 수 있습니다.

대용량의 데이터베이스 디자인을 최적화하는 방법에 대한 자세한 우수 사례는 Campaign Classic [데이터 모델 우수 사례를 참조하십시오](https://helpx.adobe.com/campaign/kb/acc-data-model-best-practices.html).
