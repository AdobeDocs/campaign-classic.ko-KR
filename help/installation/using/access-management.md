---
product: campaign
title: 액세스 관리
description: 액세스 관리 모범 사례에 대해 자세히 알아보십시오
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Access Management, Permissions
exl-id: af88e4e7-0ee3-48b4-9db4-7dd390d9d46a
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 8%

---

# 액세스 관리 {#access-management}



## 웹 앱 운영자

기본적으로 webApp 연산자는 관리자입니다. 보안을 향상하려면 다음 지침을 따르십시오.

* 이 연산자에서 바로 명명된 관리자를 새 관리자(이름이 &#39;webapp&#39;일 수 있음)로 바꿉니다. 자세한 정보는 [이 페이지](../../platform/using/access-management.md)를 참조하십시오.

* 수신자에게 읽기/쓰기 권한을 부여하려면 폴더(주로 수신자 폴더)에 webApp 연산자를 추가합니다. 자세한 정보는 이 [페이지](../../platform/using/access-management.md)를 참조하십시오.

* 다중 브랜드(또는 다중 지역) 인스턴스를 사용하는 경우 웹 애플리케이션 액세스를 다른 수신자 폴더에 분할할 수 있습니다. 방법은 다음과 같습니다.

   1. webApp 연산자를 복제합니다

   1. 각 복제의 이름을 입력합니다. 예: webapp_brand, webapp_brand2 등

   1. 웹 애플리케이션 템플릿을 복제하여 브랜드당 하나의 템플릿을 갖도록 하고, 특정 계정 사용을 선택하여 연산자를 변경할 속성을 편집합니다.  [이 페이지](../../web/using/defining-web-forms-properties.md)에서 자세히 알아보십시오.

## 보안 그룹 및 관리자 연산자

운영자가 필요한 작업을 수행할 수 있도록 충분한 권한을 부여할 수 있는 충분한 보안 그룹을 만듭니다.

관리자 연산자를 사용하지 않거나, 공유하지 마십시오. 실제 사용자당 한 개의 연산자를 만듭니다(정확한 감사/로깅을 위해). 새로 명명된 관리자를 관리 그룹에 추가합니다. 관리자 연산자를 사용하지 않는 경우, 삭제하지 말고, 사용하지 마십시오. 이 연산자는 내부적으로 사용하여 처리를 실행합니다. 하지만 당신은 그것을 금지할 수 있어요 [클라이언트 콘솔에 대한 액세스](../../platform/using/access-management.md) 보안 영역을 localhost로 제한합니다.

관리자 그룹에 너무 많은 연산자를 추가하지 마십시오(또는 관리자 이름이 지정된 권한이 있음). 매우 강력한 연산자입니다(모든 SQL 문을 수행하거나 서버에서 명령을 실행할 수 있음).

Adobe Campaign은 [명명된 권한](../../platform/using/access-management.md#named-rights):

* **관리** (관리자): 는 모든 항목에 액세스할 수 있도록 하며, 명명된 모든 오른쪽 검사를 건너뛰고 모든 작업을 수행할 수 있도록 하므로 PROGRAM EXECUTION(createProcess) 및 SQL에서 명명된 권한이 포함됩니다

* **프로그램 실행** (createProcess): 서버에서 외부 프로그램 실행 허용

* **SQL**: 에서는 데이터베이스에서 SQL 스크립트를 실행할 수 있습니다. 보안 모델을 무시할 수 있습니다. 참고: 복잡한 계산을 수행해야 하는 경우(예: 필터링) 데이터베이스 관리자에게 SQL 함수를 생성하여에 추가하도록 요청할 수 허용 목록에 추가하다 있습니다. [이 페이지](../../installation/using/scripting-coding-guidelines.md)에서 자세히 알아보십시오.

* **매우 적은 수의(및 신뢰할 수 있는) 연산자에게 이러한 권한을 부여합니다**
