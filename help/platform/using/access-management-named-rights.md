---
product: campaign
title: 명명된 권한을 사용하여 사용 권한 설정
description: 명명된 권한을 사용하여 권한을 설정하는 방법 알아보기
badge: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용"
feature: Access Management, Permissions
role: User, Admin
level: Beginner
exl-id: 07470a91-d8d2-4c41-9555-05522c8068f0
source-git-commit: 8aceafa362b80f6e34edfd91a71551a58501a3d0
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 5%

---

# 명명된 권한을 사용하여 사용 권한 설정{#named-rights}

>[!NOTE]
>
>이 페이지는 기본 인증을 사용하여 Campaign에 연결하는 운영자에만 적용됩니다. Adobe IMS 인증의 경우 [이 설명서](https://helpx.adobe.com/kr/enterprise/using/manage-permissions-and-roles.html)를 참조하세요.

기본적으로 Adobe Campaign에서는 연산자 및 연산자 그룹에 할당된 권한을 정의할 수 있는 명명된 권한 집합을 제안합니다. 이러한 권한은 트리의 **[!UICONTROL Administration > Access management > Named rights]** 노드에서 편집할 수 있습니다.

![](assets/s_ncs_admin_named_rights.png)

이러한 권한은 다음과 같습니다.

* **[!UICONTROL ADMINISTRATION]**: **[!UICONTROL ADMINISTRATION]** 권한이 있는 연산자는 인스턴스에 대한 전체 액세스 권한을 갖습니다. 관리자는 워크플로우, 게재, 스크립트 등과 같은 개체를 실행/생성/편집/삭제할 수 있습니다.

* **[!UICONTROL APPROVAL ADMINISTRATION]**: 워크플로 및 게재 내에서 여러 승인 단계를 설정하여 현재 상태가 할당된 운영자 또는 그룹에 의해 승인되었는지 확인할 수 있습니다. **[!UICONTROL APPROVAL ADMINISTRATION]** 권한이 있는 사용자는 승인 단계를 설정하고 해당 단계를 승인해야 하는 운영자 또는 운영자 그룹을 할당할 수 있습니다.

* **[!UICONTROL CENTRAL]**: 중앙 관리(분산 마케팅)에 적합합니다.

* **[!UICONTROL DELETE FOLDER]**: 폴더를 삭제할 권한. 이 권한을 사용하면 사용자가 탐색기 보기에서 폴더를 삭제할 수 있습니다.

* **[!UICONTROL EDIT FOLDERS]**: 내부 이름, 레이블, 연결된 이미지, 하위 폴더 순서 등과 같은 폴더 속성을 변경할 수 있는 권한.

* **[!UICONTROL EXPORT]**: 사용자는 **[!UICONTROL EXPORT]** 워크플로우 활동을 사용하여 Adobe Campaign 인스턴스의 데이터를 서버나 로컬 컴퓨터의 파일로 내보낼 수 있습니다.

* **[!UICONTROL FILES ACCESS]**: 서버에서 파일을 읽고 쓸 수 있도록 **[!UICONTROL JavaScript]** 워크플로우 활동에 쓸 수 있는 스크립트를 통해 파일에 대한 읽기 및 쓰기 액세스 권한을 갖습니다.

* **[!UICONTROL IMPORT]**: 일반 데이터 가져오기에 적합합니다. **[!UICONTROL IMPORT]**&#x200B;에서는 데이터를 다른 테이블로 가져올 수 있지만 **[!UICONTROL RECIPIENT IMPORT]** 권한에서는 수신자 테이블로만 가져올 수 있습니다.

* **[!UICONTROL INSERT FOLDERS]**: 폴더를 삽입할 수 있는 권한 **[!UICONTROL INSERT FOLDERS]** 권한이 있는 사용자는 탐색기 보기의 폴더 트리에 새 폴더를 만들 수 있습니다.

* **[!UICONTROL LOCAL]**: 로컬 관리(Distributed Marketing)에 적합합니다.

* **[!UICONTROL MERGE]**: 선택한 레코드를 하나로 병합할 수 있는 권한입니다. 수신자가 중복 항목으로 존재하는 경우 **[!UICONTROL MERGE]** 권한을 통해 사용자는 중복 항목을 선택하고 기본 수신자에게 병합할 수 있습니다.

* **[!UICONTROL PREPARE DELIVERIES]**: 게재를 만들고 편집하고 저장할 수 있는 권한. **[!UICONTROL PREPARE DELIVERIES]** 권한이 있는 사용자는 게재 분석 프로세스를 시작할 수도 있습니다.

* **[!UICONTROL PRIVACY DATA RIGHT]**: 개인 정보 데이터를 수집 및 삭제할 권한. 자세한 정보는 이 [페이지](https://helpx.adobe.com/kr/campaign/kb/acc-privacy.html)를 참조하십시오.

* **[!UICONTROL PROGRAM EXECUTION]**: 다양한 프로그래밍 언어로 명령을 실행할 수 있는 권한.

* **[!UICONTROL RECIPIENT IMPORT]**: 수신자를 가져올 수 있는 권한. **[!UICONTROL RECIPIENT IMPORT]** 권한이 있는 사용자는 로컬 파일을 받는 사람 테이블로 가져올 수 있습니다.

* **[!UICONTROL SQL SCRIPT EXECUTION]** 데이터베이스에서 직접 SQL 명령을 실행할 수 있는 권한.

* **[!UICONTROL START DELIVERIES]**: 이전에 분석된 게재를 승인할 수 있는 권한. 게재 분석 후 게재는 다양한 승인 단계에서 일시 중지되며 재개하려면 승인을 받아야 합니다. **[!UICONTROL START DELIVERIES]** 권한이 있는 사용자는 게재를 승인할 수 있습니다.

* **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY]**: 작업 테이블을 만들고 채우기 위해 SQL 데이터 관리 활동을 사용하여 고유한 SQL 스크립트를 작성할 권한([이 섹션](../../workflow/using/sql-data-management.md) 참조).

* **[!UICONTROL WORKFLOW]**: 워크플로우를 실행할 수 있는 권한. 이 권한이 없으면 사용자는 워크플로우를 시작, 중지 또는 다시 시작할 수 없습니다.

* **[!UICONTROL WEBAPP]**: 웹 응용 프로그램을 사용할 수 있는 권한.

>[!NOTE]
>
>이 목록은 플랫폼에 설치된 추가 기능에 따라 다를 수 있습니다.

## 액세스 권한 지표 {#access-rights-matrix}

기본 그룹 및 명명된 권한을 사용하여 운영자는 탐색 계층의 특정 폴더에 액세스하고 읽기, 쓰기 및 삭제 권한을 부여할 수 있습니다.

Adobe Campaign 액세스 권한 매트릭스는 [여기](/help/platform/using/assets/access-rights-matrix.pdf)에서 사용할 수 있습니다.

[![이미지](assets/do-not-localize/user_management.png)](https://experienceleague.adobe.com/docs/campaign-classic/assets/access-rights-matrix.pdf?lang=ko)
