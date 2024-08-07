---
product: campaign
title: 외부 데이터베이스에 연결
description: 외부 데이터베이스에 연결하는 방법 알아보기
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 240d7e11-da3a-4d64-8986-1f1c8ebcea3c
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '645'
ht-degree: 0%

---

# 데이터베이스에 연결 {#connecting-to-the-database}



외부 데이터베이스에 대한 연결을 활성화하려면 연결 매개 변수(예: 타겟팅된 데이터 소스 및 로드해야 하는 데이터가 있는 테이블의 이름)를 지정해야 합니다.

>[!CAUTION]
>
>Adobe Campaign 사용자는 외부 데이터베이스의 데이터를 처리할 외부 데이터베이스 및 Adobe Campaign 애플리케이션 서버에 대한 특정 권한이 필요합니다. 자세한 내용은 [원격 데이터베이스 액세스 권한](../../installation/using/remote-database-access-rights.md) 섹션을 참조하십시오.
>
>오작동을 방지하려면 원격 공유 데이터에 액세스하는 운영자가 별도의 공간에서 작업해야 합니다.

## 공유 연결 만들기 {#creating-a-shared-connection}

공유 외부 데이터베이스에 대한 연결을 활성화하려면 이 연결이 활성화되어 있는 한 Adobe Campaign을 통해 데이터베이스에 액세스할 수 있습니다.

1. **[!UICONTROL Administration > Platform > External accounts]** 노드를 통해 미리 구성을 정의해야 합니다.
1. **[!UICONTROL New]** 단추를 클릭하고 **[!UICONTROL External database]** 유형을 선택합니다.
1. 외부 데이터베이스의 **[!UICONTROL Connection]** 매개 변수를 정의합니다.

   **ODBC** 형식 데이터베이스에 연결하려면 **[!UICONTROL Server]** 필드에 서버 이름이 아닌 ODBC 데이터 원본 이름이 포함되어야 합니다. 더욱이, 특정 추가 구성은 사용되는 데이터베이스에 따라 필요할 수 있다. [데이터베이스 유형별 특정 구성](../../installation/using/configure-fda.md) 섹션을 참조하십시오.

1. 매개 변수를 입력한 후 **[!UICONTROL Test the connection]** 단추를 클릭하여 승인합니다.

   ![](assets/wf-external-account-create.png)

1. 필요한 경우 구성을 삭제하지 않고 이 데이터베이스에 대한 액세스를 비활성화하려면 **[!UICONTROL Enabled]** 옵션을 선택 취소하십시오.
1. Adobe Campaign에서 이 데이터베이스에 액세스할 수 있도록 하려면 SQL 함수를 배포해야 합니다. **[!UICONTROL Parameters]** 탭을 클릭한 다음 **[!UICONTROL Deploy functions]** 단추를 클릭합니다.

   ![](assets/wf-external-account-functions.png)

**[!UICONTROL Parameters]** 탭에서 테이블 및 인덱스에 대한 특정 작업 테이블스페이스를 정의할 수 있습니다.

## 임시 연결 만들기 {#creating-a-temporary-connection}

워크플로우 활동에서 외부 데이터베이스에 대한 연결을 직접 정의할 수 있습니다. 이 경우 로컬 외부 데이터베이스에 저장되며 현재 워크플로우 내에서 사용하도록 예약됩니다. 외부 계정에는 저장되지 않습니다. 이 유형의 정시 연결은 워크플로우의 다른 활동(특히 **[!UICONTROL Query]**, **[!UICONTROL Data loading (RDBMS)]**, **[!UICONTROL Enrichment]** 활동 또는 **[!UICONTROL Split]** 활동)에서 만들 수 있습니다.

>[!CAUTION]
>
>이러한 구성은 권장되지 않지만 정기적으로 데이터를 수집하는 데 사용할 수 있습니다. 그러나 [공유 연결 만들기](#creating-a-shared-connection) 섹션에 나와 있는 대로 외부 계정을 만들어야 합니다.

예를 들어 쿼리 활동에서 외부 데이터베이스에 대한 주기적 연결을 만드는 단계는 다음과 같습니다.

1. **[!UICONTROL Add data...]**&#x200B;을(를) 클릭하고 **[!UICONTROL External data]** 옵션을 선택합니다.
1. **[!UICONTROL Locally defining the data source]** 옵션을 선택하십시오.

   ![](assets/wf_add_data_local_external_data.png)

1. 드롭다운 목록에서 대상 데이터베이스 엔진을 선택합니다. 서버 이름을 입력하고 인증 매개 변수를 제공합니다.

   외부 데이터베이스의 이름도 지정합니다.

   ![](assets/wf_add_data_local_external_data_param.png)

   **[!UICONTROL Next]** 버튼을 클릭합니다.

1. 데이터가 저장된 테이블을 선택합니다.

   해당 필드에 직접 테이블 이름을 입력하거나 편집 아이콘을 눌러 데이터베이스 테이블 목록에 액세스할 수 있습니다.

   ![](assets/wf_add_data_local_external_data_select_table.png)

1. 외부 데이터베이스 데이터와 Adobe Campaign 데이터베이스의 데이터 사이에 하나 또는 여러 조정 필드를 정의하려면 **[!UICONTROL Add]** 단추를 클릭하십시오. **[!UICONTROL Remote field]** 및 **[!UICONTROL Local field]**&#x200B;의 **[!UICONTROL Edit expression]** 아이콘을 사용하면 각 테이블의 필드 목록에 액세스할 수 있습니다.

   ![](assets/wf_add_data_local_external_data_join.png)

1. 필요한 경우 필터링 조건 및 데이터 정렬 모드를 지정합니다.
1. 외부 데이터베이스에서 수집할 추가 데이터를 선택합니다. 이렇게 하려면 추가할 필드를 두 번 클릭하여 **[!UICONTROL Output columns]**&#x200B;에 표시합니다.

   ![](assets/wf_add_data_local_external_data_select.png)

   이 구성을 확인하려면 **[!UICONTROL Finish]**&#x200B;을(를) 클릭하십시오.

## 보안 연결 {#secure-connection}

>[!NOTE]
>
>보안 연결은 PostgreSQL에만 사용할 수 있습니다.

외부 FDA 계정을 구성할 때 외부 데이터베이스에 대한 액세스 보안을 설정할 수 있습니다.

이렇게 하려면 사용된 포트의 서버 주소와 주소 뒤에 &quot;**:ssl**&quot;을(를) 추가합니다. 예: **192.168.0.52:4501:ssl**.

그런 다음 데이터는 보안 SSL 프로토콜을 통해 전송됩니다.

## 추가 구성 {#additional-configurations}

필요한 경우 외부 데이터베이스에서 데이터를 처리하는 스키마를 만들 수 있습니다. 마찬가지로, Adobe Campaign을 사용하여 외부 테이블의 데이터에 대한 매핑을 정의할 수 있습니다. 이러한 구성은 일반적이며 워크플로우에만 적용되지 않습니다.

>[!NOTE]
>
>Adobe Campaign에서 스키마를 만들고 새 데이터 매핑을 정의하는 방법에 대한 자세한 내용은 [이 페이지](../../configuration/using/about-schema-edition.md)를 참조하십시오.
