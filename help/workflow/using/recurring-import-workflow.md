---
product: campaign
title: 반복 가져오기 설정
description: 반복 가져오기에 대한 워크플로우 템플릿을 구성하는 방법을 알아봅니다
feature: Workflows, Data Management
hide: true
hidefromtoc: true
exl-id: e6e140cb-8de0-4ab9-bddc-95abe04124c6
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '1015'
ht-degree: 0%

---

# 가져오기 반복 워크플로 설정 {#setting-up-a-recurring-import}



구조가 같은 파일을 정기적으로 가져오려면 워크플로우 템플릿을 사용하는 것이 좋습니다.

이 예에서는 Adobe Campaign 데이터베이스의 CRM에서 가져온 프로필을 가져오는 데 다시 사용할 수 있는 워크플로우를 사전 설정하는 방법을 보여 줍니다. 각 활동에 대해 가능한 모든 설정에 대한 자세한 내용은 이 [섹션](about-activities.md)을 참조하세요.

1. **[!UICONTROL Resources > Templates > Workflow templates]**&#x200B;에서 새 워크플로 템플릿을 만듭니다.
1. 다음 활동을 추가합니다.

   * **[!UICONTROL Data loading (file)]**: 가져올 데이터가 포함된 파일의 예상 구조를 정의합니다.
   * **[!UICONTROL Enrichment]**: 가져온 데이터를 데이터베이스 데이터와 조정합니다.
   * **[!UICONTROL Split]**: 조정할 수 있는지 여부에 따라 레코드를 다르게 처리하는 필터를 만듭니다.
   * **[!UICONTROL Deduplication]**: 데이터베이스에 삽입하기 전에 들어오는 파일에서 데이터를 중복 제거합니다.
   * **[!UICONTROL Update data]**: 가져온 프로필로 데이터베이스를 업데이트합니다.

   ![](assets/import_template_example0.png)

1. **[!UICONTROL Data Loading (file)]** 활동을 구성합니다.

   * 샘플 파일을 업로드하여 예상 구조를 정의합니다. 샘플 파일에는 가져오기에 필요한 열을 제외한 몇 줄만 포함되어야 합니다. 파일 형식을 확인 및 편집하여 각 열의 유형(텍스트, 날짜, 정수 등)이 올바르게 설정되었는지 확인합니다. 예제:

     ```
     lastname;firstname;birthdate;email;crmID
     Smith;Hayden;23/05/1989;hayden.smith@mailtest.com;123456
     ```

   * **[!UICONTROL Name of the file to load]** 섹션에서 **[!UICONTROL Upload a file from the local machine]**&#x200B;을(를) 선택하고 필드를 비워 둡니다. 이 템플릿에서 새 워크플로우를 만들 때마다 정의된 구조에 해당하는 한 원하는 파일을 여기에서 지정할 수 있습니다.

     옵션을 사용할 수 있지만 그에 따라 템플릿을 수정해야 합니다. 예를 들어 **[!UICONTROL Specified in the transition]**&#x200B;을(를) 선택하는 경우 FTP/SFTP 서버에서 가져올 파일을 검색하기 전에 **[!UICONTROL File Transfer]** 활동을 추가할 수 있습니다. S3 또는 SFTP 연결을 통해 Adobe Real-time Customer Data Platform을 사용하여 세그먼트 데이터를 Adobe Campaign으로 가져올 수도 있습니다. 자세한 정보는 이 [설명서](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html)를 참조하세요.

     ![](assets/import_template_example1.png)

1. **[!UICONTROL Enrichment]** 활동을 구성합니다. 이 컨텍스트에서 이 활동의 목적은 들어오는 데이터를 식별하는 것입니다.

   * **[!UICONTROL Enrichment]** 탭에서 **[!UICONTROL Add data]**&#x200B;을(를) 선택하고 가져온 데이터와 수신자 타겟팅 차원 간의 링크를 정의합니다. 이 예제에서는 **CRM ID** 사용자 지정 필드를 사용하여 조인 조건을 만듭니다. 고유한 레코드를 식별할 수 있는 한 필요한 필드 또는 필드 조합을 사용하십시오.
   * **[!UICONTROL Reconciliation]** 탭에서 **[!UICONTROL Identify the document from the working data]** 옵션을 선택하지 않은 상태로 둡니다.

   ![](assets/import_template_example2.png)

1. **[!UICONTROL Split]** 활동을 구성하여 한 전환에서 조정된 받는 사람과 조정할 수 없지만 두 번째 전환에서 충분한 데이터가 있는 받는 사람을 검색합니다.

   조정된 수신자와의 전환을 사용하여 데이터베이스를 업데이트할 수 있습니다. 파일에서 최소 정보 집합을 사용할 수 있는 경우 알 수 없는 수신자가 있는 전환을 사용하여 데이터베이스에서 새 수신자 항목을 만들 수 있습니다.

   조정할 수 없고 데이터가 충분하지 않은 수신자는 보충 아웃바운드 전환에서 선택되고 별도의 파일로 내보내거나 간단히 무시할 수 있습니다.

   * 활동의 **[!UICONTROL General]** 탭에서 **[!UICONTROL Use the additional data only]**&#x200B;을(를) 필터링 설정으로 선택하고 **[!UICONTROL Targeting dimension]**&#x200B;이(가) 자동으로 **[!UICONTROL Enrichment]**(으)로 설정되었는지 확인하십시오.

     데이터베이스에 삽입할 수 없는 레코드가 있는지 확인하려면 **[!UICONTROL Generate complement]** 옵션을 선택하십시오. 그런 다음 필요한 경우 파일 내보내기, 목록 업데이트 등의 추가 처리를 보조 데이터에 적용할 수 있습니다.

   * **[!UICONTROL Subsets]** 탭의 첫 번째 하위 집합에서 인바운드 모집단에 필터링 조건을 추가하여 받는 사람 기본 키가 0이 아닌 레코드만 선택합니다. 이렇게 하면 데이터베이스의 수신자와 조정된 파일의 데이터가 해당 하위 집합에서 선택됩니다.

     ![](assets/import_template_example3.png)

   * 데이터베이스에 삽입할 데이터가 충분한 조정되지 않은 레코드를 선택하는 두 번째 하위 집합을 추가합니다. 이메일 주소, 이름 및 성 등을 예로 들 수 있습니다.

     하위 집합은 생성 순서로 처리됩니다. 즉, 이 두 번째 하위 집합이 처리될 때 데이터베이스에 이미 존재하는 모든 레코드가 첫 번째 하위 집합에서 이미 선택됩니다.

     ![](assets/import_template_example3_2.png)

   * 처음 두 하위 집합에서 선택되지 않은 모든 레코드가 **[!UICONTROL Complement]**&#x200B;에서 선택됩니다.

1. 이전에 구성한 **[!UICONTROL Split]** 활동의 첫 번째 아웃바운드 전환 뒤에 있는 **[!UICONTROL Update data]** 활동을 구성합니다.

   * 인바운드 전환에 데이터베이스에 이미 있는 수신자만 포함되므로 **[!UICONTROL Update]**&#x200B;을(를) **[!UICONTROL Operation type]**(으)로 선택합니다.
   * **[!UICONTROL Record identification]** 섹션에서 **[!UICONTROL Using reconciliation keys]**&#x200B;을(를) 선택하고 타겟팅 차원과 **[!UICONTROL Enrichment]**&#x200B;에서 만들어진 링크 사이에 키를 정의합니다. 이 예제에서는 **CRM ID** 사용자 지정 필드가 사용됩니다.
   * **[!UICONTROL Fields to update]** 섹션에서 파일의 해당 열 값으로 업데이트할 수신자 차원의 필드를 나타냅니다. 파일 열의 이름이 수신자 차원 필드의 이름과 동일하거나 거의 동일한 경우 자동 선택 버튼을 사용하여 다른 필드를 자동으로 일치시킬 수 있습니다.

     ![](assets/import_template_example6.png)

1. 조정되지 않은 수신자가 포함된 전환 뒤에 있는 **[!UICONTROL Deduplication]** 활동을 구성합니다.

   * **[!UICONTROL Edit configuration]**&#x200B;을(를) 선택하고 타겟팅 차원을 워크플로의 **[!UICONTROL Enrichment]** 활동에서 생성된 임시 스키마로 설정합니다.

     ![](assets/import_template_example4.png)

   * 이 예제에서는 이메일 필드를 사용하여 고유한 프로필을 찾습니다. 가 채워져 있고 고유한 조합의 일부인 모든 필드를 사용할 수 있습니다.
   * **[!UICONTROL Deduplication method]** 화면에서 **[!UICONTROL Advanced parameters]**&#x200B;을(를) 선택하고 **[!UICONTROL Disable automatic filtering of 0 ID records]** 옵션을 선택하여 기본 키가 0인 레코드(이 전환의 모든 레코드여야 함)가 제외되지 않았는지 확인합니다.

   ![](assets/import_template_example7.png)

1. 이전에 구성한 **[!UICONTROL Deduplication]** 활동 뒤에 있는 **[!UICONTROL Update data]** 활동을 구성하십시오.

   * 인바운드 전환에 데이터베이스에 없는 수신자만 포함되므로 **[!UICONTROL Insert]**&#x200B;을(를) **[!UICONTROL Operation type]**(으)로 선택합니다.
   * **[!UICONTROL Record identification]** 섹션에서 **[!UICONTROL Directly using the targeting dimension]**&#x200B;을(를) 선택하고 **[!UICONTROL Recipients]** 차원을 선택합니다.
   * **[!UICONTROL Fields to update]** 섹션에서 파일의 해당 열 값으로 업데이트할 수신자 차원의 필드를 나타냅니다. 파일 열의 이름이 수신자 차원 필드의 이름과 동일하거나 거의 동일한 경우 자동 선택 버튼을 사용하여 다른 필드를 자동으로 일치시킬 수 있습니다.

     ![](assets/import_template_example8.png)

1. **[!UICONTROL Split]** 활동의 세 번째 전환 후에 데이터베이스에 삽입되지 않은 데이터를 추적하려면 **[!UICONTROL Data extraction (file)]** 활동 및 **[!UICONTROL File transfer]** 활동을 추가합니다. 필요한 열을 내보내고 파일을 검색할 수 있는 FTP 또는 SFTP 서버에 전송하도록 이러한 활동을 구성합니다.
1. **[!UICONTROL End]** 활동을 추가하고 워크플로 템플릿을 저장합니다.

이제 템플릿을 사용할 수 있으며, 모든 새 워크플로우에서 사용할 수 있습니다. 그런 다음 **[!UICONTROL Data loading (file)]** 활동에서 가져올 데이터가 포함된 파일을 지정하는 데 모두 필요합니다.

![](assets/import_template_example9.png)
