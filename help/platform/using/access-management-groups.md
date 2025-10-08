---
product: campaign
title: 운영자 그룹 만들기 및 관리
description: 운영자 그룹에 대한 액세스 권한을 부여하는 방법 알아보기
badge: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용"
feature: Access Management, Permissions
role: User, Admin
level: Beginner
exl-id: d5833d3d-e8ef-4f2b-8084-4ba825c79525
source-git-commit: a5bbd2e6c102a8afa4cd5931b77b0c83705a7bfa
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 1%

---

# 운영자 그룹 만들기 및 관리 {#operator-groups}

>[!NOTE]
>
>이 절차는 **기존 기본 인증**&#x200B;을 사용하여 Campaign에 연결하는 연산자에만 적용됩니다. Campaign Classic v7.3.1부터 모든 연산자는 [Adobe IMS(Identity Management System)](https://helpx.adobe.com/kr/enterprise/using/identity.html){target="_blank"}를 사용하여 Campaign에 연결해야 합니다. [자세히 알아보기](../../technotes/using/migrate-users-to-ims.md)
>
>Adobe ID을 사용하여 Campaign에 연결할 때 다음 섹션이 더 이상 적용되지 않습니다. [Campaign v8 설명서](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html?lang=ko){target="_blank"}에서 Adobe IMS를 사용하여 권한을 설정하는 방법에 대해 알아봅니다.

연산자 그룹은 트리의 **[!UICONTROL Administration > Access management > Operator groups]** 노드를 통해 만들어집니다.

## 새 연산자 그룹 만들기 {#creating-a-new-operator-group}

새 연산자 그룹을 생성하려면 다음 단계를 적용합니다.

1. 그룹 목록의 오른쪽에 있는 **[!UICONTROL New]** 단추를 클릭하거나 목록을 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL New]**&#x200B;을(를) 선택합니다.
1. 아래 섹션의 **[!UICONTROL General]** 탭에서 해당 필드에 이 그룹의 이름과 설명을 입력합니다.

   ![](assets/s_ncs_user_create_operator_gp.png)

1. 이 그룹에 대한 권한을 정의하려면 **[!UICONTROL Content]** 탭을 클릭하십시오.
1. **[!UICONTROL Add]** 단추를 클릭하여 지정한 권한 또는 그룹에 연결할 연산자를 선택하십시오.
1. 드롭다운 목록 또는 **[!UICONTROL Folder]** 필드 오른쪽에 있는 폴더를 클릭하여 이 그룹에 연결할 지정된 권한 또는 연산자를 찾습니다.
1. 추가할 권한 또는 연산자를 선택하고 **[!UICONTROL OK]**&#x200B;을(를) 클릭하여 유효성을 검사하십시오.

   ![](assets/s_ncs_user_create_operator_gp03.png)

   다른 권한 또는 연산자를 추가하려면 이 작업을 반복하십시오.

1. 목록에 그룹을 추가하려면 **[!UICONTROL Save]** 단추를 클릭하십시오.

## 기본 그룹 {#default-groups}

기본 연산자 그룹은 다음과 같습니다.

1. **[!UICONTROL Administrator]**

   이 그룹의 운영자는 인스턴스에 대한 전체 액세스 권한을 갖습니다. 관리자는 인터페이스의 가장 기술적인 부분에 액세스할 수 있는 사용자입니다. **[!UICONTROL Administration]** 역할을 보유하고 있으며 플랫폼이 모두 설정되어 있는지 확인합니다.

   이 그룹에는 다음과 같은 명명된 권한이 포함되어 있습니다.

   * **[!UICONTROL ADMINISTRATION]**: 워크플로우, 게재, 스크립트 등과 같은 개체를 실행/만들기/편집/삭제할 수 있는 권한.

1. **[!UICONTROL Delivery operators]**

   이 그룹의 운영자는 게재 관리를 담당합니다. 이를 통해 게재를 만들고 준비하는 데 필요한 기본 리소스(캠페인 유형화, 게재 매핑, 기본 템플릿, 개인화 블록 등)에 액세스할 수 있습니다.

   이 그룹에는 다음과 같은 명명된 권한이 포함되어 있습니다.

   * **[!UICONTROL PREPARE DELIVERIES]**: 게재 분석을 만들고 편집하고 시작할 수 있는 권한,
   * **[!UICONTROL START DELIVERIES]**: 이전에 분석된 게재를 승인할 수 있는 권한.

1. **[!UICONTROL Campaign managers]**

   이 그룹의 운영자는 마케팅 캠페인을 관리할 수 있습니다. **[!UICONTROL Campaign]**(선택 사항 Adobe Campaign 모듈) 프레임워크 내에서 캠페인에 연결된 개체(계획, 프로그램, 워크플로, 예산 등)에 액세스할 수 있습니다.

   이 그룹에는 다음과 같은 명명된 권한이 포함되어 있습니다.

   * **[!UICONTROL INSERT FOLDERS]**: 관련 분기에 대한 편집 권한이 있는 경우 폴더를 Adobe Campaign 트리에 삽입할 수 있는 권한
   * **[!UICONTROL WORKFLOW]**: 워크플로우를 사용할 수 있는 권한.

   >[!NOTE]
   >
   >이 그룹에서는 운영자가 게재를 시작할 수 없습니다.

1. **[!UICONTROL Content contributors]**

   이 그룹의 연산자는 **[!UICONTROL Content management]**&#x200B;의 프레임워크(선택 사항 Adobe Campaign 모듈) 내에서 콘텐츠 폴더에 액세스할 수 있습니다. 이 그룹은 추가 권한을 부여하지 않습니다.

1. **[!UICONTROL Access to reports]**

   이 그룹은 특정 연산자에 대해 Campaign 대시보드의 보고서, 예약 및 포럼 아이콘을 활성화하기 위해 외부 연산자용으로 예약되어 있습니다.

1. **[!UICONTROL Workflow execution]**

   이 그룹을 사용하면 운영자에게 캠페인과 관련 없는 워크플로우를 관리할 권한을 할당할 수 있습니다.

1. **[!UICONTROL Workflow supervisors]**

   이 그룹의 운영자는 캠페인 워크플로우에 대한 경고의 경우 이메일 알림을 받습니다.

1. 로컬 / 중앙 관리

   이러한 그룹을 사용하면 **[!UICONTROL Distributed marketing]**(선택적 Adobe Campaign 모듈)을 사용할 수 있습니다.

1. **[!UICONTROL Offer managers]**

   이 그룹의 운영자는 오퍼를 만들고 유지 관리할 수 있습니다. 자세한 내용은 이 [페이지](../../interaction/using/operator-profiles.md)를 참조하세요.
이 그룹에는 다음과 같은 명명된 권한이 포함되어 있습니다.

   * **[!UICONTROL INSERT FOLDERS]**: 관련 분기에 대한 편집 권한이 있는 경우 폴더를 Adobe Campaign 트리에 삽입할 수 있는 권한,
   * **[!UICONTROL EDIT FOLDERS]**: 내부 이름, 레이블, 연결된 이미지, 하위 폴더 순서 등과 같은 폴더 속성을 변경할 수 있는 권한.
