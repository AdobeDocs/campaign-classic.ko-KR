---
solution: Campaign Classic
product: campaign
title: 액세스 관리
description: 액세스 관리 우수 사례에 대해 자세히 알아보십시오.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: f03554302c77a39a3ad68d47417ed930f43302b7
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 5%

---


# 액세스 관리 {#access-management}

## 웹 앱 운영자

기본적으로 webApp 연산자는 관리자입니다. 보안을 강화하려면 다음 지침을 따르십시오.

* 이 연산자에서 바로 명명된 관리자를 새 관리자로 바꿉니다(이름이 &#39;웹 앱&#39;일 수 있음). 자세한 정보는 [이 페이지](../../platform/using/access-management.md)를 참조하십시오.

* 받는 사람에게 읽기/쓰기 액세스 권한을 부여하려면 폴더(주로 받는 사람 폴더)에 webApp 연산자를 추가합니다. 자세한 정보는 이 [페이지](../../platform/using/access-management.md)를 참조하십시오.

* 다중 브랜드(또는 다중 지역) 인스턴스를 사용하는 경우 웹 응용 프로그램 액세스를 다른 받는 사람 폴더에 분할할 수 있습니다. 방법은 다음과 같습니다.

   1. webApp 연산자 복제

   1. 각 복제의 이름을 입력합니다. 예:webapp_brand, webapp_brand2 등

   1. 웹 응용 프로그램 템플릿을 복제하여 브랜드당 하나의 템플릿을 사용하고 특정 계정 사용을 선택하여 속성을 편집하여 연산자를 변경합니다.  [이 페이지](../../web/using/defining-web-forms-properties.md)에서 자세히 알아보십시오.

## 보안 그룹 및 관리 연산자

운영자가 필요한 작업을 할 수 있도록 충분한 권한을 주고 그 이상의 권한을 부여할 수 있는 충분한 보안 그룹을 만들 수 있습니다.

관리자 연산자를 사용하지 마십시오(또는 공유하지 않음). 실제 사용자당 한 개의 연산자를 만듭니다(정확한 감사/기록을 위해). 새로 지명된 관리자를 관리 그룹에 추가합니다. 관리 연산자를 사용하지 않는 경우, 삭제하지 말고, 비활성화하지 마십시오.이 연산자는 처리를 실행하는 데 내부적으로 사용됩니다. 그러나 클라이언트 콘솔](../../platform/using/access-management.md)에 대한 [의 액세스를 금지하고 해당 보안 영역(localhost)을 제한할 수 있습니다.

관리 그룹에 너무 많은 연산자를 추가하지 마십시오(또는 관리자 이름 지정 권한이 있는 경우). 매우 강력한 연산자입니다(모든 SQL 문을 수행하고 서버에서 명령을 실행하는 등).

Adobe Campaign은 [명명된 rights](../../platform/using/access-management.md#named-rights)를 통해 세 개의 고급 권한을 제공합니다.

* **관리** (관리자):모든 항목에 대한 액세스 권한을 부여하고 명명된 권한 검사를 무시하고 모든 작업을 수행할 수 있도록 허용하여 PROGRAM EXECUTION(createProcess) 및 SQL 명명된 권한을 포함합니다

* **프로그램 실행** (createProcess):서버에서 외부 프로그램 실행을 허용합니다.

* **SQL**:데이터베이스에서 SQL 스크립트를 실행할 수 있습니다(보안 모델을 건너뛸 수 있음). 참고:복잡한 계산을 수행해야 하는 경우(예: 필터링) 데이터베이스 관리자에게 SQL 함수를 만들고 허용 목록에 추가하도록 요청할 수 있습니다. [이 페이지](../../installation/using/scripting-coding-guidelines.md)에서 자세히 알아보십시오.

* **매우 적은 수의(및 신뢰할 수 있는) 연산자에게 해당 연산자를 부여합니다.**
