---
product: campaign
title: 명명된 권한을 사용하여 사용 권한 설정
description: 명명된 권한을 사용하여 권한을 설정하는 방법을 알아봅니다
feature: Access Management
role: User, Admin
level: Beginner
exl-id: 07470a91-d8d2-4c41-9555-05522c8068f0
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 7%

---

# 명명된 권한을 사용하여 사용 권한 설정{#named-rights}

![](../../assets/common.svg)

기본적으로 Adobe Campaign에서는 운영자 및 운영자 그룹에 할당된 승인을 정의할 수 있는 명명된 권한 집합을 제안합니다. 이러한 권한은 **[!UICONTROL Administration > Access management > Named rights]** 노드 아래에 있어야 합니다.

![](assets/s_ncs_admin_named_rights.png)

권한은 다음과 같습니다.

* **[!UICONTROL ADMINISTRATION]**: 연산자가 **[!UICONTROL ADMINISTRATION]** 인스턴스에 대한 전체 액세스 권한이 있습니다. 관리자 사용자는 워크플로우, 전달, 스크립트 등과 같은 개체를 실행/생성/편집/삭제할 수 있습니다.

* **[!UICONTROL APPROVAL ADMINISTRATION]**: 워크플로우 및 게재 내에서 여러 승인 단계를 설정하여 현재 상태가 지정된 운영자 또는 그룹에 의해 승인되었는지 확인할 수 있습니다. 을 사용하는 사용자 **[!UICONTROL APPROVAL ADMINISTRATION]** 권한 은 승인 단계를 설정하고 해당 단계를 승인해야 하는 운영자 또는 운영자 그룹을 지정할 수도 있습니다.

* **[!UICONTROL CENTRAL]**: 중앙 관리 권한(분산 마케팅).

* **[!UICONTROL DELETE FOLDER]**: 폴더를 삭제할 수 있는 권한. 이 권한을 사용하면 사용자가 탐색기 보기에서 폴더를 삭제할 수 있습니다.

* **[!UICONTROL EDIT FOLDERS]**: 내부 이름, 레이블, 연결된 이미지, 하위 폴더 순서 등과 같은 폴더 속성을 변경할 수 있는 권한.

* **[!UICONTROL EXPORT]**: 사용자는 Adobe Campaign 인스턴스의 데이터를 **[!UICONTROL EXPORT]** 워크플로우 활동.

* **[!UICONTROL FILES ACCESS]**: 에서 작성할 수 있는 스크립트를 통해 파일에 대한 읽기 및 쓰기 액세스 권한 **[!UICONTROL JavaScript]** 서버에서 파일을 읽기/쓰기 위한 워크플로우 활동.

* **[!UICONTROL IMPORT]**: 일반 데이터 가져오기에 대한 권한. **[!UICONTROL IMPORT]** 데이터를 다른 테이블로 가져올 수 있지만 **[!UICONTROL RECIPIENT IMPORT]** 오른쪽에서는 수신자 테이블로만 가져올 수 있습니다.

* **[!UICONTROL INSERT FOLDERS]**: 폴더를 삽입할 수 있는 권한. 을 사용하는 사용자 **[!UICONTROL INSERT FOLDERS]** 탐색기 보기의 폴더 트리에서 새 폴더를 만들 수 있습니다.

* **[!UICONTROL LOCAL]**: 로컬 관리 권한(분산 마케팅).

* **[!UICONTROL MERGE]**: 선택한 레코드를 하나로 병합할 수 있는 권한. 수신자가 중복으로 존재하는 경우 **[!UICONTROL MERGE]** 마우스 오른쪽 단추를 사용하면 사용자가 중복을 선택하고 기본 수신자로 병합할 수 있습니다.

* **[!UICONTROL PREPARE DELIVERIES]**: 게재 생성, 편집 및 저장 권한. 을 사용하는 사용자 **[!UICONTROL PREPARE DELIVERIES]** 게재 분석 프로세스를 시작할 수도 있습니다.

* **[!UICONTROL PRIVACY DATA RIGHT]**: 개인 정보 데이터를 수집 및 삭제할 권한. 자세한 정보는 이 [페이지](https://helpx.adobe.com/kr/campaign/kb/acc-privacy.html)를 참조하십시오.

* **[!UICONTROL PROGRAM EXECUTION]**: 다양한 프로그래밍 언어로 명령을 실행할 수 있는 권한.

* **[!UICONTROL RECIPIENT IMPORT]**: 수신자를 가져올 수 있는 권한. 을 사용하는 사용자 **[!UICONTROL RECIPIENT IMPORT]** 로컬 파일을 수신자 테이블로 가져올 수 있는 권한이 있습니다.

* **[!UICONTROL SQL SCRIPT EXECUTION]** 데이터베이스에서 직접 SQL 명령을 실행할 수 있는 권한.

* **[!UICONTROL START DELIVERIES]**: 이전에 분석한 게재를 승인할 수 있는 권한. 게재 분석 후, 게재는 다양한 승인 단계에서 일시 중지되며 재개하려면 승인을 받아야 합니다. 을 사용하는 사용자 **[!UICONTROL START DELIVERIES]** 게재 승인 권한이 허용됩니다.

* **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY]**: 작업 테이블을 만들고 채우기 위해 SQL 데이터 관리 활동을 사용하여 고유한 SQL 스크립트를 작성할 수 있는 권한( 참조) [이 섹션](../../workflow/using/sql-data-management.md)).

* **[!UICONTROL WORKFLOW]**: 워크플로우를 실행할 수 있는 권한. 이 권한이 없으면 사용자가 워크플로우를 시작, 중지 또는 다시 시작할 수 없습니다.

* **[!UICONTROL WEBAPP]**: 웹 응용 프로그램을 사용할 수 있는 권한.

>[!NOTE]
>
>이 목록은 플랫폼에 설치된 추가 기능에 따라 다를 수 있습니다.

## 액세스 권한 매트릭스 {#access-rights-matrix}

기본 그룹 및 명명된 권한을 통해 연산자는 탐색 계층 구조에서 특정 폴더에 액세스하고 읽기, 쓰기 및 삭제 권한을 부여할 수 있습니다.

Adobe Campaign 액세스 권한 표를 사용할 수 있습니다 [여기](/help/platform/using/assets/access-rights-matrix.pdf).

[![이미지](assets/do-not-localize/user_management.png)](https://experienceleague.adobe.com/docs/campaign-classic/assets/access-rights-matrix.pdf?lang=en)
