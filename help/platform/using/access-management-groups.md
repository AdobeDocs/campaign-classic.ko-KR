---
product: campaign
title: 운영자 그룹 만들기 및 관리
description: 운영자 그룹에 대한 액세스 권한을 부여하는 방법 알아보기
feature: Access Management
role: User, Admin
level: Beginner
exl-id: d5833d3d-e8ef-4f2b-8084-4ba825c79525
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# 운영자 그룹 만들기 및 관리 {#operator-groups}

![](../../assets/common.svg)

운영자 그룹은 **[!UICONTROL Administration > Access management > Operator groups]** 노드 아래에 있어야 합니다.

## 새 연산자 그룹 만들기 {#creating-a-new-operator-group}

새 운영자 그룹을 생성하려면 다음 단계를 수행합니다.

1. 을(를) 클릭합니다. **[!UICONTROL New]** 그룹 목록 오른쪽에 있는 버튼을 클릭하거나 목록을 마우스 오른쪽 버튼으로 클릭하고 **[!UICONTROL New]**.
1. 섹션 아래 창의 **[!UICONTROL General]** 탭에서 해당 필드에 이 그룹의 이름과 설명을 입력합니다.

   ![](assets/s_ncs_user_create_operator_gp.png)

1. 을(를) 클릭합니다. **[!UICONTROL Content]** 탭하여 이 그룹에 대한 권한을 정의합니다.
1. 을(를) 클릭합니다. **[!UICONTROL Add]** 버튼을 클릭하여 지정된 권한 또는 그룹에 연결할 연산자를 선택합니다.
1. 드롭다운 목록 또는 폴더 오른쪽의 **[!UICONTROL Folder]** 이 그룹에 연결할 지정된 권한 또는 연산자를 찾는 필드입니다.
1. 추가할 권한 또는 연산자를 선택하고 를 클릭합니다 **[!UICONTROL OK]** 유효성을 검사하려면 다음을 수행하십시오.

   ![](assets/s_ncs_user_create_operator_gp03.png)

   다른 권한 또는 연산자를 추가하려면 이 작업을 반복합니다.

1. 을(를) 클릭합니다. **[!UICONTROL Save]** 목록에 그룹을 추가하는 단추.

## 기본 그룹 {#default-groups}

기본 연산자 그룹은 다음과 같습니다.

1. **[!UICONTROL Administrator]**

   이 그룹의 연산자는 인스턴스에 대한 전체 액세스 권한을 갖습니다. 관리자는 인터페이스의 가장 기술적인 부분에 액세스할 수 있는 사용자입니다. 그들은 **[!UICONTROL Administration]** 역할 을 수행하고 플랫폼이 모두 설정되어 있는지 확인합니다.

   이 그룹에는 이름이 지정된 다음 권한이 포함되어 있습니다.

   * **[!UICONTROL ADMINISTRATION]**: 워크플로우, 게재, 스크립트 등과 같은 모든 객체를 실행/생성/편집/삭제할 수 있는 권한.

1. **[!UICONTROL Delivery operators]**

   이 그룹의 연산자는 게재 관리를 담당합니다. 게재를 만들고 준비하는 데 필요한 기본 리소스(캠페인 유형화, 게재 매핑, 기본 템플릿, 개인화 블록 등)에 액세스할 수 있습니다.

   이 그룹에는 다음과 같은 명명된 권한이 포함되어 있습니다.

   * **[!UICONTROL PREPARE DELIVERIES]**: 게재 분석을 만들고, 편집하고, 시작할 수 있는 권한
   * **[!UICONTROL START DELIVERIES]**: 이전에 분석한 게재를 승인할 수 있는 권한.

1. **[!UICONTROL Campaign managers]**

   이 그룹의 운영자는 마케팅 캠페인을 관리할 수 있습니다. 캠페인(계획, 프로그램, 워크플로우, 예산 등)에 연결된 객체에 액세스할 수 있습니다. 의 프레임워크 내에서 **[!UICONTROL Campaign]** (선택적 Adobe Campaign 모듈).

   이 그룹에는 다음과 같은 명명된 권한이 포함되어 있습니다.

   * **[!UICONTROL INSERT FOLDERS]**: Adobe Campaign 트리에 폴더를 삽입할 수 있는 권한(관련 분기에 대한 편집 권한이 있는 경우),
   * **[!UICONTROL WORKFLOW]**: 워크플로우를 사용할 수 있는 권한.
   >[!NOTE]
   >
   >이 그룹에서는 연산자가 게재를 시작할 수 없습니다.

1. **[!UICONTROL Content contributors]**

   이 그룹의 연산자는 **[!UICONTROL Content management]** (선택적 Adobe Campaign 모듈). 이 그룹은 추가 권한을 부여하지 않습니다.

1. **[!UICONTROL Access to reports]**

   이 그룹은 웹 액세스를 통해 게재 보고서에 액세스하기 위해 외부 운영자를 위해 예약되어 있습니다.

1. **[!UICONTROL Workflow execution]**

   이 그룹을 사용하면 운영자에게 캠페인과 관련이 없는 워크플로우를 관리할 권한을 할당할 수 있습니다.

1. **[!UICONTROL Workflow supervisors]**

   이 그룹의 운영자는 캠페인 워크플로우와 관련된 경고의 경우 이메일 알림을 받습니다.

1. 로컬 / 중앙 관리

   이러한 그룹을 사용하면 **[!UICONTROL Distributed marketing]** (선택적 Adobe Campaign 모듈).

1. **[!UICONTROL Offer managers]**

   이 그룹의 연산자는 오퍼를 만들고 유지 관리할 수 있습니다. 자세한 내용은 다음을 참조하십시오 [페이지](../../interaction/using/operator-profiles.md).
이 그룹에는 다음과 같은 명명된 권한이 포함되어 있습니다.

   * **[!UICONTROL INSERT FOLDERS]**: Adobe Campaign 트리에 폴더를 삽입할 수 있는 권한(관련 분기에 대한 편집 권한이 있는 경우),
   * **[!UICONTROL EDIT FOLDERS]**: 내부 이름, 레이블, 연결된 이미지, 하위 폴더 순서 등과 같은 폴더 속성을 변경할 수 있는 권한.
