---
product: campaign
title: 워크플로우 권한 관리
description: 워크플로우 권한 관리 방법 알아보기
feature: Workflows
exl-id: 88995fb3-d336-4355-acd4-33118dd0e2b0
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# 워크플로우 권한 관리{#managing-rights}

![](../../assets/common.svg)

관리자가 아닌 경우 Adobe Campaign 운영자가 워크플로우를 작성, 실행 또는 수정하기 위한 액세스 권한이 필요합니다.

일반적으로 워크플로우를 수행하는 운영자는 다양한 활동(수신자, 수신자 목록, 구독, 게재 등)에서 사용되는 데이터 및 하위 파일일 수 있는 데이터가 포함된 파일에 액세스해야 합니다.

또한 워크플로우에서 수행하는 작업(수신자 가져오기, 파일 액세스, 퓨전, SQL 스크립트 실행 등)과 일치하는 명명된 권한에 매핑해야 합니다.

운영자 및 권한 관리에 대한 자세한 내용은 다음을 참조하십시오 [섹션](../../platform/using/access-management.md).

## 운영자 그룹 {#operator-groups-wf}

다음 운영자 그룹은 워크플로우와 연관되어 있습니다.

* 다음 **[!UICONTROL Workflow execution]** 그룹 을 사용하면 타깃팅 워크플로우의 실행 및 승인을 제어할 수 있습니다. 오른쪽 워크플로우가 이 그룹의 연산자에 매핑됩니다. 데이터 파일에 대한 액세스 권한 외에 워크플로우의 모든 작업에 필요합니다. 기본적으로 **[!UICONTROL Workflow execution]** 그룹에는 표준 타겟팅 워크플로우 파일 및 워크플로우 템플릿에 대한 읽기 전용 액세스 권한이 있습니다. 이 그룹의 연산자도 보류 중인 승인 파일에 대한 읽기 및 쓰기 액세스 권한도 갖습니다.
* 다음 **[!UICONTROL Workflow supervisors]** 그룹 을 사용하면 운영자가 워크플로우 승인을 관리할 수 있습니다.
* 다음 **[!UICONTROL Operation Managers]** 그룹 을 사용하여 캠페인 워크플로우에 액세스합니다.

## 명명된 권한 {#named-rights}

워크플로우에는 오른쪽(오른쪽)이라는 워크플로우 만 있습니다. 워크플로우를 만들고, 시작하고, 중지할 수 있습니다. 명명된 권한을 적용할 수 있으려면 워크플로우 파일에 대한 읽기 권한이 필요합니다. 워크플로우 타겟팅의 경우 **[!UICONTROL Profiles and Targets]** 파일이 필요합니다.

## 워크플로우 실행 계정 {#workflow-execution-account}

워크플로우 템플릿 수준에서 사용할 실행 계정을 구성할 수 있습니다. 실행 계정을 사용하면 실행을 시작하는 Adobe Campaign 운영자와 관계없이 승인을 워크플로우에 직접 매핑할 수 있습니다. 기본적으로 모든 워크플로우는 시작한 연산자의 권한으로 실행됩니다.

실행 계정을 워크플로우에 매핑하려면 워크플로우 템플릿 목록으로 이동한 다음 워크플로우에 연결된 템플릿을 마우스 오른쪽 단추로 클릭합니다. 선택 **[!UICONTROL Action > Change execution account...]** 그런 다음 사용할 계정을 선택합니다.
