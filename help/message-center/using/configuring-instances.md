---
product: campaign
title: 인스턴스 구성
description: Adobe Campaign Classic에서 트랜잭션 메시지 제어 및 실행 인스턴스를 구성하는 방법에 대해 알아봅니다
feature: Transactional Messaging, Message Center
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용됩니다."
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 23a384d1-27ce-46c2-98c3-0fb60a5c50ee
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '1229'
ht-degree: 1%

---


# 인스턴스 구성 {#creating-a-shared-connection}



트랜잭션 메시지 기능을 사용하려면 컨트롤 및 실행 인스턴스를 구성해야 합니다. 다음 중 하나를 사용할 수 있습니다.
* [컨트롤 인스턴스 1개](#control-instance) 하나 또는 여러 개의 실행 인스턴스와 연결됨
* [여러 컨트롤 인스턴스](#using-several-control-instances) 여러 실행 인스턴스와 연결됨

>[!IMPORTANT]
>
>스키마 확장은 다음에 의해 사용된 리소스에 영향을 주었습니다. [메시지 센터 기술 워크플로우](../../message-center/using/additional-configurations.md#technical-workflows) 제어 또는 실행 인스턴스 중 하나에서 트랜잭션 메시지 모듈에서 사용하는 다른 인스턴스에 복제해야 합니다.

실행 인스턴스를 지정하여 제어 인스턴스에 연결해야 합니다.

이 단원에서는 제어 및 실행 인스턴스를 구성하고 연결하는 데 필요한 모든 단계에 대해 설명합니다.

>[!IMPORTANT]
>
>제어 인스턴스와 실행 인스턴스를 다른 컴퓨터에 설치해야 합니다. 동일한 Campaign 인스턴스를 공유할 수 없습니다.

## 컨트롤 인스턴스 구성 {#control-instance}

제어 인스턴스와 실행 인스턴스를 연결하려면 먼저 **[!UICONTROL Execution instance]** 외부 계정 입력 **컨트롤 인스턴스에서**. 따라서 한 번 [게시됨](../../message-center/using/publishing-message-templates.md#template-publication), 트랜잭션 메시지 템플릿을 실행 인스턴스에 배포할 수 있습니다.

실행 인스턴스를 여러 개 사용하는 경우 실행 인스턴스가 있는 만큼의 외부 계정을 만들어야 합니다.

>[!NOTE]
>
>실행 인스턴스를 여러 제어 인스턴스에서 사용하는 경우 데이터를 폴더 및 연산자로 나눌 수 있습니다. 자세한 내용은 [여러 컨트롤 인스턴스 사용](#using-several-control-instances).

### 외부 계정 만들기

>[!NOTE]
>
>아래 단계를 수행해야 합니다. **컨트롤 인스턴스에서**.

을(를) 만들려면 **[!UICONTROL Execution instance]** 외부 계정을 입력한 후 다음을 적용합니다.

1. 로 이동 **[!UICONTROL Administration > Platform > External accounts]** 폴더를 삭제합니다.
1. 실행 인스턴스 유형 Adobe Campaign에서 즉시 사용할 수 있도록 제공되는 외부 계정 중 하나를 선택하고 마우스 오른쪽 버튼으로 클릭한 다음 를 선택합니다 **[!UICONTROL Duplicate]** .

   ![](assets/messagecenter_create_extaccount_001.png)

1. 필요에 따라 레이블을 변경합니다.

   ![](assets/messagecenter_create_extaccount_002.png)

1. 다음 항목 선택 **[!UICONTROL Enabled]** 외부 계정을 작동하는 옵션입니다.

   ![](assets/messagecenter_create_extaccount_003.png)

1. 실행 인스턴스가 설치된 서버 주소를 지정합니다.

   ![](assets/messagecenter_create_extaccount_004.png)

1. 계정은 연산자 폴더에 정의된 메시지 센터 에이전트와 일치해야 합니다. 기본적으로 Adobe Campaign에서 제공하는 기본 계정은 입니다. **[!UICONTROL mc]** .

   ![](assets/messagecenter_create_extaccount_005.png)

1. 연산자 폴더에 정의된 계정 암호를 입력합니다.

   >[!NOTE]
   >
   >인스턴스에 로그온할 때마다 암호를 입력하지 않도록 하려면 실행 인스턴스에 제어 인스턴스의 IP 주소를 지정할 수 있습니다. 자세한 내용은 [실행 인스턴스 구성](#execution-instance).

1. 실행 인스턴스에서 사용할 복구 방법을 지정합니다. 복구할 데이터는 실행 인스턴스에 의해 제어 인스턴스로 전달되어 트랜잭션 메시지 및 이벤트 아카이브에 추가됩니다.

   ![](assets/messagecenter_create_extaccount_007.png)

   데이터 수집은 HTTP/HTTPS 액세스를 사용하는 웹 서비스 또는 FDA(Federated Data Access) 모듈을 통해 발생합니다.

   >[!NOTE]
   >
   >HTTP를 통해 FDA를 사용하는 경우 PostgreSQL 데이터베이스를 사용하는 실행 인스턴스만 지원됩니다. MSSQL 또는 Oracle 데이터베이스는 지원되지 않습니다.

   제어 인스턴스가 실행 인스턴스의 데이터베이스에 직접 액세스할 수 있는 경우에는 두 번째 방법(FDA)이 권장됩니다. 그렇지 않으면 웹 서비스 액세스를 선택합니다. 지정하는 FDA 계정은 제어 인스턴스에서 생성된 다양한 실행 인스턴스의 데이터베이스에 대한 연결과 일치합니다.

   ![](assets/messagecenter_create_extaccount_008.png)

   FDA(Federated Data Access)에 대한 자세한 내용은 [이 섹션](../../installation/using/about-fda.md).

1. 클릭 **[!UICONTROL Test the connection]** 컨트롤 인스턴스와 실행 인스턴스가 연결되어 있는지 확인합니다.

   ![](assets/messagecenter_create_extaccount_006.png)

여러 실행 인스턴스를 사용할 때 이 단계를 반복하여 실행 인스턴스가 있는 만큼의 외부 계정을 만듭니다.

### 실행 인스턴스 식별 {#identifying-execution-instances}

각 실행 인스턴스를 제어 인스턴스에서 볼 때 각 실행 인스턴스의 내역을 구분하려면 각 실행 인스턴스를 고유 식별자와 연결해야 합니다.

이 식별자는 각 실행 인스턴스에 할당할 수 있습니다. **수동**. 이 경우 이 단계를 수행해야 합니다 **각 실행 인스턴스에서**. 이렇게 하려면 아래에 설명된 대로 배포 마법사를 사용합니다.

1. 실행 인스턴스에서 배포 마법사를 엽니다.
1. 로 이동 **[!UICONTROL Message Center]** 창.
1. 선택한 식별자를 인스턴스에 할당합니다.

   ![](assets/messagecenter_id_execinstance_001.png)

1. 각 실행 인스턴스에 대해 위의 단계를 반복합니다.

식별자는 다음과 같을 수도 있습니다. **자동으로** 속성. 이렇게 하려면 **컨트롤 인스턴스**&#x200B;을(를) 클릭하고 **[!UICONTROL Initialize connection]** 단추를 클릭합니다.

![](assets/messagecenter_create_extaccount_006bis.png)

## 실행 인스턴스 구성 {#execution-instance}

>[!NOTE]
>
>아래 단계를 수행해야 합니다. **실행 인스턴스**.

실행 인스턴스를 제어 인스턴스에 연결하려면 아래 단계를 따르십시오.

컨트롤 인스턴스가 암호를 지정하지 않고도 실행 인스턴스에 연결할 수 있으려면 **메시지 센터** 액세스 권한 섹션에 자세히 설명되어 있습니다. 그러나 빈 암호는 기본적으로 사용할 수 없습니다.

빈 암호를 사용하려면 실행 인스턴스로 이동하여 이벤트를 제공하는 정보 시스템의 IP 주소로 제한된 보안 영역을 정의하십시오. 이 보안 영역에서는 빈 암호를 허용하고 허용해야 합니다. `<identifier> / <password>` 연결을 입력합니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../installation/using/security-zones.md)을 참조하십시오.

>[!NOTE]
>
>실행 인스턴스를 여러 제어 인스턴스에서 사용하는 경우 데이터를 폴더 및 연산자로 나눌 수 있습니다. 자세한 내용은 [여러 컨트롤 인스턴스 사용](#using-several-control-instances).

1. 실행 인스턴스에서 연산자 폴더( **[!UICONTROL Administration > Access management > Operators]** ).
1. 다음 항목 선택 **메시지 센터** 요원님

   ![](assets/messagecenter_operator_001.png)

1. 다음 항목 선택 **[!UICONTROL Edit]** 탭을 클릭하고 **[!UICONTROL Access rights]** 을(를) 클릭하고 **[!UICONTROL Edit the access parameters...]** 링크를 클릭합니다.

   ![](assets/messagecenter_operator_002.png)

1. 다음에서 **[!UICONTROL Access settings]** 창에서 **[!UICONTROL Add a trusted IP mask]** 를 연결하고 컨트롤 인스턴스의 IP 주소를 추가합니다.

   ![](assets/messagecenter_operator_003.png)

여러 실행 인스턴스를 사용할 때 각 실행 인스턴스에 대해 이 단계를 반복합니다.

## 여러 컨트롤 인스턴스 사용 {#using-several-control-instances}

실행 클러스터를 다양한 제어 인스턴스와 공유할 수 있습니다. 이러한 유형의 아키텍처에는 다음과 같은 구성이 필요합니다.

예를 들어, 회사에서 각각 고유한 제어 인스턴스를 사용하여 두 개의 브랜드를 관리한다고 가정해 보겠습니다. **컨트롤 1** 및 **컨트롤 2**. 두 개의 실행 인스턴스도 사용됩니다. 각 제어 인스턴스에 대해 다른 메시지 센터 연산자를 입력해야 합니다. **mc1** 연산자 **컨트롤 1** 인스턴스 및 **mc2** 연산자 **컨트롤 2** 인스턴스.

모든 실행 인스턴스의 트리에서 연산자당 하나의 폴더를 만듭니다(**폴더 1** 및 **폴더 2**)을 설정하고, 각 운영자의 해당 폴더에 대한 데이터 액세스를 제한합니다.

### 컨트롤 인스턴스 구성 {#configuring-control-instances}

>[!NOTE]
>
>아래 단계를 수행해야 합니다. **컨트롤 인스턴스**.

1. 다음에서 **컨트롤 1** 인스턴스를 제어하고 실행 인스턴스당 하나의 외부 계정을 만든 다음 **mc1** 각 외부 계정의 연산자입니다. 다음 **mc1** 연산자가 모든 실행 인스턴스에 생성됩니다( 참조). [실행 인스턴스 구성](#configuring-execution-instances)).

   ![](assets/messagecenter_multi_control_1.png)

1. 다음에서 **컨트롤 2** 인스턴스를 제어하고 실행 인스턴스당 하나의 외부 계정을 만든 다음 **mc2** 각 외부 계정의 연산자입니다. 다음 **mc2** 연산자가 모든 실행 인스턴스에 생성됩니다( 참조). [실행 인스턴스 구성](#configuring-execution-instances)).

   ![](assets/messagecenter_multi_control_2.png)

   >[!NOTE]
   >
   >컨트롤 인스턴스 구성에 대한 자세한 내용은 [이 섹션](#control-instance).

### 실행 인스턴스 구성 {#configuring-execution-instances}

>[!NOTE]
>
>아래 단계를 수행해야 합니다. **실행 인스턴스**.

여러 제어 인스턴스를 사용하려면 모든 실행 인스턴스에서 이 구성을 수행해야 합니다.

1. 에서 연산자당 하나의 폴더를 만듭니다. **[!UICONTROL Administration > Production > Message Center]** 노드: **폴더 1** 및 **폴더 2**. 폴더 및 보기 만들기에 대한 자세한 내용은 [이 페이지](../../platform/using/access-management-folders.md).

   ![](assets/messagecenter_multi_control_3.png)

1. 만들기 **mc1** 및 **mc2** 기본적으로 제공되는 메시지 센터 연산자를 복제하여 연산자(**mc**). 연산자 만들기에 대한 자세한 내용은 [이 섹션](../../platform/using/access-management-operators.md).

   ![](assets/messagecenter_multi_control_4.png)

   >[!NOTE]
   >
   >**mc1** 및 **mc2** 연산자에 다음이 있어야 합니다. **[!UICONTROL Message Center execution]** 권한이 있고 Adobe Campaign 클라이언트 콘솔에 액세스할 수 없습니다. 연산자는 항상 보안 영역에 연결되어 있어야 합니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../installation/using/security-zones.md)을 참조하십시오.

1. 각 연산자에 대해 **[!UICONTROL Restrict to information found in sub-folders of]** 상자를 열고 관련 폴더(**폴더 1** 대상: **mc1** 연산자 and **폴더 2** 대상: **mc2** 연산자).

   ![](assets/messagecenter_multi_control_5.png)

1. 각 운영자에게 해당 폴더에 대한 읽기 및 쓰기 권한을 부여합니다. 이렇게 하려면 폴더를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Properties]** . 그런 다음 를 선택합니다. **[!UICONTROL Security]** 를 탭하고 관련 연산자(**mc1** 대상 **폴더 1** 및 **mc2** 대상 **폴더 2**). 다음을 확인하십시오. **[!UICONTROL Read/Write data]** 상자가 선택되어 있습니다.

   ![](assets/messagecenter_multi_control_6.png)
