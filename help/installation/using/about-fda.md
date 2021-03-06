---
product: campaign
title: 페더레이션 데이터 액세스 시작
description: 외부 데이터베이스에서 데이터에 액세스하고 처리하는 방법을 알아봅니다
feature: Federated Data Access
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---

# 페더레이션 데이터 액세스 시작 {#about-federated-data-access}

![](../../assets/v7-only.svg)

Adobe Campaign은 다음을 제공합니다 **페더레이션 데이터 액세스** (FDA) 옵션을 사용하여 하나 이상의 외부 데이터베이스에 저장된 정보를 처리할 수 있습니다. Adobe Campaign 데이터의 구조를 변경하지 않고 외부 데이터에 액세스할 수 있습니다.

## 전제 조건 {#operating-principle}

FDA 옵션을 사용하면 데이터 모델을 타사 데이터베이스로 확장할 수 있습니다. 대상 테이블의 구조를 자동으로 감지하고 SQL 소스의 데이터를 사용합니다.

이 기능을 사용하려면 사전 요구 사항이 아래에 나열되어 있습니다.

* **구성**: 호환되는 외부 데이터베이스 목록은 [호스팅 모델](../../installation/using/hosting-models.md).
* **외부 데이터베이스 버전**: Adobe Campaign FDA 모듈과 호환되는 외부 데이터베이스가 있어야 합니다.

   Campaign에서는 호스팅 모델당 데이터베이스 시스템 및 호환 버전 목록을 자세히 설명합니다 [호환성 매트릭스](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).

* **권한**: 사용자도 [필요한 권한](../../installation/using/remote-database-access-rights.md) Adobe Campaign 및 외부 데이터베이스에 있을 때 사용됩니다.

