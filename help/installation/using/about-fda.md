---
product: campaign
title: Federated Data Access 시작
description: 외부 데이터베이스의 데이터에 액세스하고 처리하는 방법에 대해 알아봅니다
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Federated Data Access
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---

# Federated Data Access 시작 {#about-federated-data-access}



Adobe Campaign은 **페더레이션 데이터 액세스** (FDA) 하나 이상의 외부 데이터베이스에 저장된 정보를 처리하기 위한 옵션: Adobe Campaign 데이터의 구조를 변경하지 않고 외부 데이터에 액세스할 수 있습니다.

## 전제 조건 {#operating-principle}

FDA 옵션을 사용하면 타사 데이터베이스에서 데이터 모델을 확장할 수 있습니다. 대상 테이블의 구조를 자동으로 감지하고 SQL 소스의 데이터를 사용합니다.

이 기능을 사용하기 위한 사전 요구 사항은 다음과 같습니다.

* **구성**: 호환되는 외부 데이터베이스 목록은 다음에 따라 다릅니다. [호스팅 모델](../../installation/using/hosting-models.md).
* **외부 데이터베이스 버전**: Adobe Campaign FDA 모듈과 호환되는 외부 데이터베이스가 있어야 합니다.

   호스팅 모델별 데이터베이스 시스템 및 호환 버전 목록은 Campaign에 자세히 설명되어 있습니다 [호환성 매트릭스](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).

* **권한**: 사용자에게 다음도 있어야 합니다. [필요한 권한](../../installation/using/remote-database-access-rights.md) Adobe Campaign 및 외부 데이터베이스에 있습니다.

