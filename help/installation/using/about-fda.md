---
product: campaign
title: Federated Data Access 시작
description: 외부 데이터베이스의 데이터에 액세스하고 처리하는 방법에 대해 알아봅니다
feature: Installation, Federated Data Access
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---

# Federated Data Access 시작 {#about-federated-data-access}



Adobe Campaign은 하나 이상의 외부 데이터베이스에 저장된 정보를 처리하기 위해 **FDA(Federated Data Access**) 옵션을 제공합니다. Adobe Campaign 데이터의 구조를 변경하지 않고 외부 데이터에 액세스할 수 있습니다.

## 필수 구성 요소 {#operating-principle}

FDA 옵션을 사용하면 타사 데이터베이스에서 데이터 모델을 확장할 수 있습니다. 대상 테이블의 구조를 자동으로 감지하고 SQL 소스의 데이터를 사용합니다.

이 기능을 사용하기 위한 사전 요구 사항은 다음과 같습니다.

* **구성**: 호환되는 외부 데이터베이스 목록은 [호스팅 모델](../../installation/using/hosting-models.md)에 따라 다릅니다.
* **외부 데이터베이스 버전**: Adobe Campaign FDA 모듈과 호환되는 외부 데이터베이스가 있어야 합니다.

  호스팅 모델별 데이터베이스 시스템 및 호환 버전 목록은 Campaign [호환성 매트릭스](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA)에 자세히 설명되어 있습니다.

* **권한**: 사용자는 Adobe Campaign 및 외부 데이터베이스에도 [필요한 권한](../../installation/using/remote-database-access-rights.md)이 있어야 합니다.

