---
solution: Campaign Classic
product: campaign
title: 권한 관리
description: 권한 관리
audience: workflow
content-type: reference
topic-tags: advanced-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 1%

---


# 권한 관리{#managing-rights}

관리자가 아닌 경우 Adobe Campaign 연산자는 워크플로우를 생성, 실행 또는 수정하는 데 대한 액세스 권한이 필요합니다.

일반적으로 워크플로우를 수행하는 운영자는 다양한 활동(받는 사람, 수신자 목록, 구독, 배달 등)에 사용되는 데이터가 포함된 파일과 하위 파일일 수 있는 파일을 액세스해야 합니다.

또한 받는 사람 가져오기, 파일 액세스, fusion, SQL 스크립트 실행 등 워크플로우에 영향을 미치는 워크플로우에 의해 수행되는 작업과 일치하는 명명된 권한에 매핑해야 합니다.

연산자 및 권한 관리에 대한 자세한 내용은 이 [섹션](../../platform/using/access-management.md)을 참조하십시오.

## 연산자 그룹 {#operator-groups}

다음 연산자 그룹이 워크플로우에 연결됩니다.

* **[!UICONTROL Workflow execution]** 그룹을 사용하여 타깃팅 워크플로의 실행 및 승인을 제어할 수 있습니다.오른쪽이라는 WORKFLOW가 이 그룹의 연산자에 매핑됩니다. 데이터 파일에 대한 액세스 권한 외에 워크플로우의 모든 작업에 필요합니다. 기본적으로 **[!UICONTROL Workflow execution]** 그룹은 표준 타깃팅 워크플로우 파일 및 워크플로우 템플릿에 대한 읽기 전용 액세스 권한을 갖습니다. 이 그룹의 연산자도 보류 중인 승인 파일에 대한 읽기 및 쓰기 액세스 권한을 가집니다.
* **[!UICONTROL Workflow supervisors]** 그룹을 사용하여 운영자가 워크플로우 승인을 관리할 수 있습니다.
* 캠페인 워크플로우에 액세스하기 위한 **[!UICONTROL Operation Managers]** 그룹.

## 명명된 권한 {#named-rights}

워크플로우에 따라 오른쪽으로 지정된 WORKFLOW만 다릅니다.워크플로우를 생성, 시작 및 중지할 수 있습니다. 지정된 권한을 적용할 수 있으려면 워크플로우 파일에 대한 읽기 권한이 필요합니다. 타깃팅 워크플로의 경우 **[!UICONTROL Profiles and Targets]** 파일의 읽기 권한이 필요합니다.

## 워크플로 실행 계정 {#workflow-execution-account}

워크플로우 템플릿 수준에서 사용할 실행 계정을 구성할 수 있습니다. 실행 계정을 사용하면 실행을 시작하는 Adobe Campaign 운영자와 상관없이 승인을 워크플로우에 직접 매핑할 수 있습니다. 기본적으로 모든 워크플로우는 시작한 연산자의 권한으로 실행됩니다.

실행 계정을 워크플로우에 매핑하려면 워크플로우 템플릿 목록으로 이동하여 워크플로우에 연결된 템플릿을 마우스 오른쪽 버튼으로 클릭합니다. **[!UICONTROL Action > Change execution account...]**&#x200B;을 선택한 다음 사용할 계정을 선택합니다.
