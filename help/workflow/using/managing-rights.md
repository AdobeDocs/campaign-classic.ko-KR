---
product: campaign
title: 워크플로우 권한 관리
description: 워크플로우 권한을 관리하는 방법 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: 88995fb3-d336-4355-acd4-33118dd0e2b0
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 1%

---

# 워크플로우 권한 관리{#managing-rights}



관리자가 아닌 경우 Adobe Campaign 운영자는 워크플로우를 작성, 실행 또는 수정하기 위한 액세스 권한이 필요합니다.

일반적으로 워크플로를 수행하는 운영자는 다양한 활동(수신자, 수신자 목록, 구독, 게재 등) 중에 사용되는 데이터가 포함된 파일 및 하위 파일에 액세스해야 합니다.

또한 영향을 줄 워크플로에서 수행한 작업(수신자 가져오기, 파일 액세스, Fusion, SQL 스크립트 실행 등)과 일치하는 명명된 권한에도 매핑해야 합니다.

운영자 및 권한 관리에 대한 자세한 내용은 다음을 참조하십시오. [섹션](../../platform/using/access-management.md).

## 운영자 그룹 {#operator-groups-wf}

다음 연산자 그룹은 워크플로우에 연결됩니다.

* 다음 **[!UICONTROL Workflow execution]** 그룹을 사용하면 타겟팅 워크플로우의 실행 및 승인을 제어할 수 있습니다. 권한이 명명된 워크플로우가 이 그룹의 연산자에 매핑됩니다. 데이터 파일에 대한 액세스 권한 외에 워크플로우의 모든 작업에 필요합니다. 기본적으로 **[!UICONTROL Workflow execution]** 그룹은 표준 타겟팅 워크플로우 파일 및 워크플로우 템플릿에 대한 읽기 전용 액세스 권한을 가집니다. 이 그룹의 운영자는 보류 중인 승인 파일에 대한 읽기 및 쓰기 액세스 권한도 갖습니다.
* 다음 **[!UICONTROL Workflow supervisors]** 그룹을 사용하면 운영자가 워크플로 승인을 관리할 수 있습니다.
* 다음 **[!UICONTROL Operation Managers]** 그룹 을 클릭하여 캠페인 워크플로우에 액세스합니다.

## 명명된 권한 {#named-rights}

right라는 WORKFLOW만 워크플로에 따라 고유합니다. 이 워크플로를 사용하면 워크플로를 만들고, 시작하고, 중지할 수 있습니다. 지정된 권한을 적용하려면 워크플로우 파일에 대한 읽기 권한이 필요합니다. 타겟팅 워크플로우의 경우 **[!UICONTROL Profiles and Targets]** 파일이 필요합니다.

## 워크플로우 실행 계정 {#workflow-execution-account}

워크플로우 템플릿 수준에서 사용할 실행 계정을 구성할 수 있습니다. 실행 계정을 사용하면 Adobe Campaign 연산자의 실행 시작에 관계없이 권한을 워크플로우에 직접 매핑할 수 있습니다. 기본적으로 모든 워크플로우는 이를 시작한 연산자의 권한으로 실행됩니다.

실행 계정을 워크플로우에 매핑하려면 워크플로우 템플릿 목록으로 이동한 후 워크플로우에 연결된 템플릿을 마우스 오른쪽 버튼으로 클릭합니다. 선택 **[!UICONTROL Action > Change execution account...]** 그런 다음 사용할 계정을 선택합니다.
