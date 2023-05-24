---
product: campaign
title: 액세스 관리
description: 액세스 관리 모범 사례에 대해 자세히 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Access Management, Permissions
exl-id: af88e4e7-0ee3-48b4-9db4-7dd390d9d46a
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 8%

---

# 액세스 관리 {#access-management}



## Webapp 연산자

기본적으로 webApp 연산자는 관리자입니다. 보안을 향상하려면 다음 지침을 따르십시오.

* 이 연산자의 right라는 책임자를 새 책임자로 바꿉니다(&#39;webapp&#39; 이라고도 함). 자세한 정보는 [이 페이지](../../platform/using/access-management.md)를 참조하십시오.

* 폴더(주로 수신자 폴더)에 webApp 연산자를 추가하여 수신자에게 읽기/쓰기 액세스 권한을 부여합니다. 자세한 정보는 이 [페이지](../../platform/using/access-management.md)를 참조하십시오.

* 다중 브랜드(또는 다중 지역) 인스턴스를 사용하는 경우 웹 애플리케이션 액세스를 다른 수신자 폴더로 분할할 수 있습니다. 방법은 다음과 같습니다.

   1. webApp 연산자 복제

   1. 각 복제에 대한 이름을 입력합니다. 예: webapp_brand, webapp_brand2 등

   1. 웹 애플리케이션 템플릿을 복제하여 브랜드당 하나의 템플릿을 갖게 하고 속성을 편집하여 특정 계정 사용을 선택하여 연산자를 변경합니다.  [이 페이지](../../web/using/defining-web-forms-properties.md)에서 자세히 알아보십시오.

## 보안 그룹 및 관리자

운영자가 필요한 작업을 수행하도록 하면서도 그 이상은 허용하지 않을 수 있는 충분한 권한을 운영자에게 부여할 수 있는 충분한 보안 그룹을 만듭니다.

관리 연산자를 사용하지 마십시오 (또는 공유하지 마십시오). 실제 사용자당 한 명의 연산자를 만듭니다(정확한 감사/로깅을 위해). 새로 명명된 관리자를 관리 그룹에 추가합니다. admin 연산자를 사용하지 않는 경우 삭제하지 않고 비활성화하지 마십시오. 이 연산자는 처리를 실행하는 데 내부적으로 사용됩니다. 하지만 금지할 수 있습니다 [클라이언트 콘솔에 액세스](../../platform/using/access-management.md) 및 해당 보안 영역을 제한(localhost로)합니다.

관리자 그룹(또는 관리자 지정 권한이 있는 운영자)에 연산자를 너무 많이 추가하지 마십시오. 매우 강력한 연산자입니다(모든 SQL 문을 수행하고 서버에서 명령을 실행하는 등의 작업을 수행할 수 있음).

Adobe Campaign은 다음을 통해 세 가지 높은 수준의 권한을 제공합니다. [명명된 권한](../../platform/using/access-management.md#named-rights):

* **관리** (관리자): 모든 항목에 액세스할 수 있고 명명된 모든 권한 검사를 우회하여 모든 작업을 수행할 수 있으므로 PROGRAM EXECUTION(createProcess) 및 SQL 명명된 권한이 포함됩니다

* **프로그램 실행** (createProcess): 서버에서 외부 프로그램 실행을 허용합니다.

* **SQL**: 데이터베이스에서 SQL 스크립트를 실행할 수 있도록 허용하므로 보안 모델을 건너뛸 수 있습니다. 허용 목록에 추가하다 주: 복잡한 계산 필터링(예: 필터링)을 수행해야 하는 경우, 데이터베이스 관리자에게 SQL 함수를 생성하고 이를 SQL 함수에 추가하도록 요청할 수 있습니다. [이 페이지](../../installation/using/scripting-coding-guidelines.md)에서 자세히 알아보십시오.

* **매우 적은 수의(및 신뢰할 수 있는) 운영자에게 허용**
