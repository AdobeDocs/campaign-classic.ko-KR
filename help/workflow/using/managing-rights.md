---
title: 권한 관리
seo-title: 권한 관리
description: 권한 관리
seo-description: null
page-status-flag: never-activated
uuid: 07039fec-c957-4548-acc7-22dc7827a54b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: advanced-management
discoiquuid: f78603e9-f6ff-4ebe-941b-b3fbd1924b71
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 권한 관리{#managing-rights}

관리자가 아닌 경우 Adobe Campaign 운영자는 워크플로우를 생성, 실행 또는 수정하는 데 대한 액세스 권한이 필요합니다.

일반적으로 워크플로우에서 작동하는 연산자는 다양한 활동(수신자, 수신자 목록, 구독, 배달 등) 중에 사용된 데이터가 포함된 파일과 하위 파일일 수 있습니다.

또한 이러한 권한은 워크플로우가 수행하는 작업(수신자 가져오기, 파일 액세스, 퓨전, SQL 스크립트 실행 등)과 일치하는 명명된 권한에 매핑되어야 합니다.

연산자 및 권한 관리에 대한 자세한 내용은 이 [섹션을](../../platform/using/access-management.md)참조하십시오.

## 연산자 그룹 {#operator-groups}

다음 연산자 그룹은 워크플로우에 연결됩니다.

* 이 **[!UICONTROL Workflow execution]** 그룹을 사용하면 타깃팅 워크플로우의 실행 및 승인을 제어할 수 있습니다.right라는 워크플로우는 이 그룹의 연산자에 매핑됩니다. 데이터 파일에 대한 액세스 권한 외에도 워크플로우의 모든 작업에 필요합니다. 기본적으로 이 **[!UICONTROL Workflow execution]** 그룹은 표준 타깃팅 워크플로우 파일 및 워크플로우 템플릿에 대한 읽기 전용 액세스 권한을 갖습니다. 이 그룹의 운영자도 대기 중인 승인 파일에 대한 읽기 및 쓰기 액세스 권한을 가집니다.
* 이 **[!UICONTROL Workflow supervisors]** 그룹을 사용하면 운영자가 워크플로우 승인을 관리할 수 있습니다.
* 캠페인 워크플로우에 액세스할 **[!UICONTROL Operation Managers]** 그룹입니다.

## 명명된 권한 {#named-rights}

right라는 WORKFLOW만 워크플로우에 따라 다릅니다.워크플로우를 생성, 시작 및 중지할 수 있습니다. 지정된 권한을 적용하려면 워크플로 파일에 대한 읽기 권한이 필요합니다. 타깃팅 워크플로우의 경우 **[!UICONTROL Profiles and Targets]** 파일에서 바로 읽을 수 있어야 합니다.

## 워크플로우 실행 계정 {#workflow-execution-account}

워크플로우 템플릿 수준에서 사용할 실행 계정을 구성할 수 있습니다. 실행 계정을 사용하면 실행을 시작하는 Adobe Campaign 운영자에 관계없이 승인을 워크플로우에 직접 매핑할 수 있습니다. 기본적으로 모든 워크플로우는 시작한 운영자의 권한으로 실행됩니다.

실행 계정을 워크플로우에 매핑하려면 워크플로우 템플릿 목록으로 이동하여 워크플로우에 연결된 템플릿을 마우스 오른쪽 버튼으로 클릭합니다. 그런 다음 사용할 계정을 **[!UICONTROL Action > Change execution account...]** 선택합니다.
