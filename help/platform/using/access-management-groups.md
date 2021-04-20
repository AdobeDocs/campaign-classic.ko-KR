---
solution: Campaign Classic
product: campaign
title: 연산자 그룹 만들기 및 관리
description: 연산자 그룹에 액세스 권한을 부여하는 방법에 대해 알아봅니다.
feature: Access Management
role: Business Practitioner, Administrator
level: Beginner
translation-type: tm+mt
source-git-commit: f2bd093d3a010e079b7f5adf3371e21d07a4f3ae
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 0%

---


# 연산자 그룹 {#operator-groups} 만들기 및 관리

연산자 그룹은 트리의 **[!UICONTROL Administration > Access management > Operator groups]** 노드를 통해 만들어집니다.

## 새 연산자 그룹 {#creating-a-new-operator-group} 만들기

새 연산자 그룹을 만들려면 다음 단계를 적용합니다.

1. 그룹 목록 오른쪽에 있는 **[!UICONTROL New]** 단추를 클릭하거나 목록을 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL New]** 을 선택합니다.
1. 아래 섹션의 **[!UICONTROL General]** 탭에서 해당 필드에 이 그룹의 이름과 설명을 입력합니다.

   ![](assets/s_ncs_user_create_operator_gp.png)

1. **[!UICONTROL Content]** 탭을 클릭하여 이 그룹의 승인을 정의합니다.
1. **[!UICONTROL Add]** 단추를 클릭하여 지정된 권한을 선택하거나 그룹에 연결할 연산자를 선택합니다.
1. 드롭다운 목록 또는 **[!UICONTROL Folder]** 필드 오른쪽의 폴더를 클릭하여 이 그룹에 연결할 지정된 권한이나 연산자를 찾습니다.
1. 추가할 권한 또는 연산자를 선택하고 유효성을 검사하려면 **[!UICONTROL OK]**&#x200B;을 클릭합니다.

   ![](assets/s_ncs_user_create_operator_gp03.png)

   다른 권한 또는 연산자를 추가하려면 이 작업을 반복합니다.

1. **[!UICONTROL Save]** 단추를 클릭하여 그룹에 추가합니다.

## 기본 그룹 {#default-groups}

기본 연산자 그룹은 다음과 같습니다.

1. **[!UICONTROL Administrator]**

   이 그룹의 연산자는 인스턴스에 대한 전체 액세스 권한을 가집니다. 관리자는 인터페이스에서 가장 기술적인 부분에 액세스할 수 있는 사용자입니다. **[!UICONTROL Administration]** 역할을 유지하고 플랫폼이 모두 설정되어 있는지 확인합니다.

   이 그룹에는 오른쪽이라는 이름의 다음 항목이 포함됩니다.

   * **[!UICONTROL ADMINISTRATION]**:워크플로우, 전달, 스크립트 등 모든 객체를 실행/생성/편집/삭제할 권리

1. **[!UICONTROL Delivery operators]**

   이 그룹의 연산자는 납품 관리를 담당합니다.이러한 구성 요소는 제공을 만들고 준비하는 데 필요한 기본 리소스(캠페인 유형, 배달 매핑, 기본 템플릿, 개인화 블록 등)에 대한 액세스를 가능하게 합니다.

   이 그룹에는 다음과 같은 명명된 권한이 포함됩니다.

   * **[!UICONTROL PREPARE DELIVERIES]**:전달 분석을 작성, 편집 및 시작할 수 있는 권한
   * **[!UICONTROL START DELIVERIES]**:이전에 분석한 전달을 승인할 수 있는 권리.

1. **[!UICONTROL Campaign managers]**

   이 그룹의 연산자는 마케팅 캠페인을 관리할 수 있습니다.캠페인(계획, 프로그램, 워크플로우, 예산 등)에 연결된 개체에 액세스할 수 있습니다. **[!UICONTROL Campaign]** 프레임워크 내에서(선택적 Adobe Campaign 모듈).

   이 그룹에는 다음과 같은 명명된 권한이 포함됩니다.

   * **[!UICONTROL INSERT FOLDERS]**:Adobe Campaign 트리에 폴더를 삽입할 권리(관련 분기에 대한 편집 권한이 있는 경우),
   * **[!UICONTROL WORKFLOW]**:워크플로우 사용 권한
   >[!NOTE]
   >
   >이 그룹에서는 연산자가 배달을 시작할 수 없습니다.

1. **[!UICONTROL Content contributors]**

   이 그룹의 연산자는 **[!UICONTROL Content management]**(선택적 Adobe Campaign 모듈) 프레임워크 내에서 콘텐트 폴더에 액세스할 수 있습니다. 이 그룹은 추가 권한을 부여하지 않습니다.

1. **[!UICONTROL Access to reports]**

   이 그룹은 웹 액세스를 통해 배달 보고서에 액세스하기 위해 외부 운영자를 위해 예약됩니다.

1. **[!UICONTROL Workflow execution]**

   이 그룹을 사용하면 캠페인과 관련이 없는 워크플로우를 관리할 수 있는 권한을 운영자에게 할당할 수 있습니다.

1. **[!UICONTROL Workflow supervisors]**

   이 그룹의 연산자는 캠페인 워크플로우에 대한 경고가 표시되는 경우 이메일 알림을 수신합니다.

1. 로컬 / 중앙 관리

   이러한 그룹을 사용하면 **[!UICONTROL Distributed marketing]**(선택적 Adobe Campaign 모듈)을 사용할 수 있습니다.

1. **[!UICONTROL Offer managers]**

   이 그룹의 연산자는 오퍼를 만들고 유지 관리할 수 있습니다. 이에 대한 자세한 내용은 이 [페이지](../../interaction/using/operator-profiles.md)를 참조하십시오.
이 그룹에는 다음과 같은 명명된 권한이 포함됩니다.

   * **[!UICONTROL INSERT FOLDERS]**:Adobe Campaign 트리에 폴더를 삽입할 권리(관련 분기에 대한 편집 권한이 있는 경우),
   * **[!UICONTROL EDIT FOLDERS]**:내부 이름, 레이블, 연결된 이미지, 하위 폴더 순서 등과 같은 폴더 속성을 변경할 수 있는 권한입니다.
