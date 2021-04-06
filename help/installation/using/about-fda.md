---
solution: Campaign Classic
product: campaign
title: 외부 데이터베이스 액세스
description: 외부 데이터베이스에서 데이터에 액세스하고 데이터를 처리하는 방법 학습
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
translation-type: tm+mt
source-git-commit: 37802e52f1d1d38d9c3d59c439f23114a594bfef
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 4%

---

# 통합 데이터 액세스 시작 {#about-federated-data-access}

Adobe Campaign은 하나 이상의 외부 데이터베이스에 저장된 정보를 처리하기 위해 **Federated Data Access**(FDA) 옵션을 제공합니다.Adobe Campaign 데이터 구조를 변경하지 않고 외부 데이터에 액세스할 수 있습니다.

## 사전 요구 사항 {#operating-principle}

FDA 옵션을 사용하면 데이터 모델을 제3자 데이터베이스로 확장할 수 있습니다. 타깃팅된 테이블의 구조를 자동으로 감지하고 SQL 소스의 데이터를 사용합니다.

이 기능을 사용하려면 사전 요구 사항이 아래에 나열되어 있습니다.

* **구성**:Snowflake을 제외하고, 통합 데이터 액세스 **를** 설정하려면 온프레미스 또  **** 하이브리드 호스팅 모델이 필요합니다. [자세히 알아보기](../../installation/using/hosting-models.md)
* **외부 데이터베이스 버전**:Adobe Campaign FDA 모듈과 호환되는 외부 데이터베이스가 필요합니다. 데이터베이스 시스템 및 호환 버전 목록은 캠페인 [호환성 매트릭스](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA)에 자세히 설명되어 있습니다.
* **권한**:또한 사용자는 Adobe Campaign 및 외부  [데이터베이스에서 ](../../installation/using/remote-database-access-rights.md) 필요한권한을 가져야 합니다.

