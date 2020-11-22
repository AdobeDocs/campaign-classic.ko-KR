---
solution: Campaign Classic
product: campaign
title: 공유 연결 만들기
description: 공유 연결 만들기
audience: message-center
content-type: reference
topic-tags: instance-configuration
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '998'
ht-degree: 2%

---


# 공유 연결 만들기{#creating-a-shared-connection}

>[!IMPORTANT]
>
>* 제어 또는 실행 인스턴스의 [메시지 센터 기술 워크플로에서](../../message-center/using/technical-workflows.md) 사용하는 스키마에서 만들어진 스키마 확장은 Adobe Campaign 트랜잭션 메시징 모듈에서 사용하는 다른 인스턴스에 복제되어야 합니다.
>* 제어 인스턴스와 실행 인스턴스를 다른 컴퓨터에 설치해야 합니다. 동일한 캠페인 인스턴스를 공유할 수 없습니다.

>



## 컨트롤 인스턴스 {#control-instance}

상세 분류 아키텍처가 있는 경우 제어 인스턴스에 연결된 실행 인스턴스를 지정하고 연결해야 합니다. 트랜잭션 메시지 템플릿은 실행 인스턴스에 배포됩니다. 외부 계정 유형을 구성하여 제어 인스턴스와 실행 인스턴스 간의 연결이 **[!UICONTROL Execution instance]** 만들어집니다. 실행 인스턴스만큼 외부 계정을 만들어야 합니다.

>[!NOTE]
>
>실행 인스턴스를 여러 제어 인스턴스에서 사용하면 데이터를 폴더 및 연산자로 나눌 수 있습니다. 자세한 내용은 여러 컨트롤 인스턴스 [사용을 참조하십시오](#using-several-control-instances).

실행 인스턴스 유형 외부 계정을 만들려면 다음 단계를 적용합니다.

1. Go to the **[!UICONTROL Administration > Platform > External accounts]** folder.
1. 실행 인스턴스 유형 외부 계정 중 하나를 Adobe Campaign과 함께 바로 사용할 수 있도록 선택하고 마우스 오른쪽 버튼을 클릭한 다음 을 선택합니다 **[!UICONTROL Duplicate]** .

   ![](assets/messagecenter_create_extaccount_001.png)

1. 필요에 따라 레이블을 변경합니다.

   ![](assets/messagecenter_create_extaccount_002.png)

1. 외부 계정 **[!UICONTROL Enabled]** 을 작동시키려면 옵션을 선택합니다.

   ![](assets/messagecenter_create_extaccount_003.png)

1. 실행 인스턴스가 설치된 서버의 주소를 지정합니다.

   ![](assets/messagecenter_create_extaccount_004.png)

1. 계정은 연산자 폴더에 정의된 메시지 센터 에이전트와 일치해야 합니다. 기본적으로 Adobe Campaign에서 제공하는 기본 계정은 입니다 **[!UICONTROL mc]** .

   ![](assets/messagecenter_create_extaccount_005.png)

1. 연산자 폴더에 정의된 계정의 암호를 입력합니다.

   >[!NOTE]
   >
   >인스턴스에 로그온할 때마다 암호를 입력하지 않으려면 실행 인스턴스에서 제어 인스턴스의 IP 주소를 지정할 수 있습니다. For more on this, refer to [Execution instance](#execution-instance).

1. 실행 인스턴스에서 사용할 복구 방법을 지정합니다.

   복구할 데이터는 트랜잭션 메시지 및 이벤트 보관에 추가하기 위해 실행 인스턴스별로 제어 인스턴스로 전달됩니다.

   ![](assets/messagecenter_create_extaccount_007.png)

   데이터 수집은 HTTP/HTTPS 액세스를 사용하는 웹 서비스 또는 FDA(Federated Data Access) 모듈을 통해 이루어집니다.

   >[!NOTE]
   >
   >HTTP를 통해 FDA를 사용하는 경우 PostgreSQL 데이터베이스를 사용하는 실행 인스턴스만 지원됩니다. MSSQL 또는 Oracle 데이터베이스가 지원되지 않습니다.

   두 번째 방법은 제어 인스턴스가 실행 인스턴스의 데이터베이스에 직접 액세스하는 경우 권장됩니다. 그렇지 않은 경우 웹 서비스 액세스를 선택합니다. 지정할 FDA 계정은 제어 인스턴스에서 만들어진 다양한 실행 인스턴스의 데이터베이스에 대한 연결과 일치합니다.

   ![](assets/messagecenter_create_extaccount_008.png)

   연합 데이터 액세스(FDA)에 대한 자세한 내용은 외부 데이터베이스 [액세스를 참조하십시오](../../installation/using/about-fda.md).

1. 을 **[!UICONTROL Test the connection]** 클릭하여 제어 인스턴스와 실행 인스턴스가 연결되어 있는지 확인합니다.

   ![](assets/messagecenter_create_extaccount_006.png)

1. 각 실행 인스턴스는 식별자와 연결해야 합니다. 이 식별자는 배포 마법사를 사용하거나(실행 인스턴스 [식별 참조](../../message-center/using/identifying-execution-instances.md)), 제어 인스턴스에서 연결 **** 초기화 버튼을 클릭하여 자동으로 각 실행 인스턴스에 적용될 수 있습니다.

   ![](assets/messagecenter_create_extaccount_006bis.png)

## 실행 인스턴스 {#execution-instance}

제어 인스턴스가 암호를 부여하지 않고도 실행 인스턴스에 연결할 수 있게 하려면 **메시지 센터** 액세스 권한 섹션에 제어 인스턴스의 IP 주소를 입력하면 됩니다. 그러나 기본적으로 빈 암호는 사용할 수 없습니다.

빈 암호를 사용하려면 실행 인스턴스로 이동하고 이벤트를 전달하는 정보 시스템의 IP 주소로 제한된 보안 영역을 정의합니다. 이 보안 영역은 빈 암호를 허용하고 `<identifier> / <password>` 문자 연결을 허용해야 합니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../installation/using/configuring-campaign-server.md#defining-security-zones)을 참조하십시오.

>[!NOTE]
>
>실행 인스턴스를 여러 제어 인스턴스에서 사용하면 데이터를 폴더 및 연산자로 나눌 수 있습니다. 자세한 내용은 여러 컨트롤 인스턴스 [사용을 참조하십시오](#using-several-control-instances).

1. 실행 인스턴스( )의 연산자 폴더로 **[!UICONTROL Administration > Access management > Operators]** 이동합니다.
1. 메시지 **센터** 에이전트를 선택합니다.

   ![](assets/messagecenter_operator_001.png)

1. 탭을 **[!UICONTROL Edit]** 선택하고 **[!UICONTROL Access rights]** 을 클릭한 다음 **[!UICONTROL Edit the access parameters...]** 링크를 클릭합니다.

   ![](assets/messagecenter_operator_002.png)

1. 창에서 **[!UICONTROL Access settings]** **[!UICONTROL Add a trusted IP mask]** 링크를 클릭하고 제어 인스턴스의 IP 주소를 추가합니다.

   ![](assets/messagecenter_operator_003.png)

## 여러 컨트롤 인스턴스 사용 {#using-several-control-instances}

실행 클러스터를 다양한 제어 인스턴스와 공유할 수 있습니다. 이러한 유형의 아키텍처는 다음과 같은 구성이 필요합니다.

예를 들어 회사에서 각각 자체 제어 인스턴스를 사용하여 두 개의 브랜드를 관리하는 경우, **컨트롤 1** 및 **컨트롤 2**. 두 개의 실행 인스턴스도 사용됩니다. 각 제어 인스턴스에 대해 다른 메시지 센터 연산자를 입력해야 합니다.Control 1 **인스턴스의** 연산자 **와** mc2 ******연산자** 는인스턴스의 연산자입니다.

모든 실행 인스턴스의 트리에서 연산자당 하나의 폴더(**폴더 1** 및 **폴더 2**)를 만들고 각 연산자의 데이터 액세스 권한을 해당 폴더에 제한합니다.

### 제어 인스턴스 구성 {#configuring-control-instances}

1. Control **1** 컨트롤 인스턴스에서 실행 인스턴스당 외부 계정 하나를 만들고 각 외부 계정에 **mc1** 연산자를 입력합니다. 그 후 **mc1** 연산자는 모든 실행 인스턴스에 생성됩니다(실행 인스턴스 [구성 참조](#configuring-execution-instances)).

   ![](assets/messagecenter_multi_control_1.png)

1. Control **2** 컨트롤 인스턴스에서 실행 인스턴스당 외부 계정 하나를 만들고 각 외부 계정에 **mc2** 연산자를 입력합니다. 그 후 **mc2** 연산자는 모든 실행 인스턴스에 생성됩니다(실행 인스턴스 [구성 참조](#configuring-execution-instances)).

   ![](assets/messagecenter_multi_control_2.png)

   >[!NOTE]
   >
   >제어 인스턴스 구성에 대한 자세한 내용은 제어 인스턴스 [를 참조하십시오](#control-instance).

### 실행 인스턴스 구성 {#configuring-execution-instances}

여러 제어 인스턴스를 사용하려면 ALL 실행 인스턴스에 대해 이 구성을 수행해야 합니다.

1. 노드에서 연산자당 하나의 폴더를 **[!UICONTROL Administration > Production > Message Center]** 만듭니다. **폴더 1** 및 **폴더 2**. 폴더 및 보기 만들기에 대한 자세한 내용은 [플랫폼을 참조하십시오](../../platform/using/access-management.md#folders-and-views).

   ![](assets/messagecenter_multi_control_3.png)

1. 기본적으로 제공되는 메시지 센터 연산자( **mc** )를 복제하여 **mc1** 및&#x200B;**mc2**&#x200B;연산자를만듭니다. For more on creating operators, refer to [this section](../../platform/using/access-management.md#operators).

   ![](assets/messagecenter_multi_control_4.png)

   >[!NOTE]
   >
   >**mc1** 및 **mc2** 연산자는 **[!UICONTROL Message Center execution]** 권한이 있어야 하며 Adobe Campaign 클라이언트 콘솔에 액세스할 수 없습니다. 연산자는 항상 보안 영역에 연결되어 있어야 합니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../installation/using/configuring-campaign-server.md#defining-security-zones)을 참조하십시오.

1. 각 연산자에 대해 **[!UICONTROL Restrict to information found in sub-folders of]** 확인란을 선택하고 관련 폴더(**mc1** 연산자의 **폴더 1** 과mc2 연산자의 **폴더 2****** 폴더)를 선택합니다.

   ![](assets/messagecenter_multi_control_5.png)

1. 각 운영자에게 해당 폴더에 대한 읽기 및 쓰기 권한을 부여합니다. 이렇게 하려면 폴더를 마우스 오른쪽 단추로 클릭하고 을 선택합니다 **[!UICONTROL Properties]** . 그런 다음 **[!UICONTROL Security]** 탭을 선택하고 관련 연산자(**폴더 1** 의 경우 **mc1** ,폴더 2 **의 경우** mc2 ****)를 추가합니다. 상자가 **[!UICONTROL Read/Write data]** 선택되어 있는지 확인합니다.

   ![](assets/messagecenter_multi_control_6.png)

