---
solution: Campaign Classic
product: campaign
title: 반복 가져오기 설정
description: 반복 가져오기에 대한 워크플로 템플릿을 구성하는 방법을 알아봅니다.
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: bb7e3ce726e2c589c033686cf3ab2960de140d91
workflow-type: tm+mt
source-wordcount: '1023'
ht-degree: 0%

---


# 반복 가져오기 작업 과정 설정 {#setting-up-a-recurring-import}

동일한 구조의 파일을 정기적으로 가져와야 하는 경우 워크플로우 템플릿을 사용하는 것이 가장 좋습니다.

이 예에서는 Adobe Campaign 데이터베이스의 CRM에서 가져온 프로파일을 가져오는 데 다시 사용할 수 있는 워크플로우를 사전 설정하는 방법을 보여줍니다. 각 활동에 대한 가능한 모든 설정에 대한 자세한 내용은 이 [섹션](../../workflow/using/about-activities.md)을 참조하십시오.

1. **[!UICONTROL Resources > Templates > Workflow templates]**&#x200B;에서 새 워크플로 템플릿을 만듭니다.
1. 다음 활동을 추가합니다.

   * **[!UICONTROL Data loading (file)]**:가져올 데이터가 포함된 파일의 예상 구조를 정의합니다.
   * **[!UICONTROL Enrichment]**:가져온 데이터를 데이터베이스 데이터와 조정합니다.
   * **[!UICONTROL Split]**:조정 가능 여부에 따라 필터를 만들어 레코드를 다르게 처리합니다.
   * **[!UICONTROL Deduplication]**:데이터베이스에 삽입하기 전에 들어오는 파일에서 데이터를 중복 제거합니다.
   * **[!UICONTROL Update data]**:가져온 프로필로 데이터베이스를 업데이트합니다.

   ![](assets/import_template_example0.png)

1. **[!UICONTROL Data Loading (file)]** 활동을 구성합니다.

   * 샘플 파일을 업로드하여 예상 구조를 정의합니다. 샘플 파일은 가져올 수 있는 열을 모두 제외하고 몇 줄만 포함해야 합니다. 파일 형식을 확인하고 편집하여 각 열의 유형이 올바르게 설정되어 있는지 확인합니다.텍스트, 날짜, 정수 등 예제:

      ```
      lastname;firstname;birthdate;email;crmID
      Smith;Hayden;23/05/1989;hayden.smith@mailtest.com;123456
      ```

   * **[!UICONTROL Name of the file to load]** 섹션에서 **[!UICONTROL Upload a file from the local machine]**&#x200B;을 선택하고 필드를 비워 둡니다. 이 템플릿에서 새 워크플로우를 만들 때마다 정의된 구조에 해당하는 한 원하는 파일을 여기에서 지정할 수 있습니다.

      옵션을 사용할 수 있지만 이에 따라 템플릿을 수정해야 합니다. 예를 들어 **[!UICONTROL Specified in the transition]**&#x200B;을 선택하면 FTP/SFTP 서버에서 가져올 파일을 검색하기 전에 **[!UICONTROL File Transfer]** 활동을 추가할 수 있습니다. S3 또는 SFTP 연결을 사용하면 Adobe 실시간 고객 데이터 플랫폼을 통해 세그먼트 데이터를 Adobe Campaign으로 가져올 수도 있습니다. 자세한 내용은 이 [설명서](https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html)를 참조하십시오.

      ![](assets/import_template_example1.png)

1. **[!UICONTROL Enrichment]** 활동을 구성합니다. 이 컨텍스트에서 이 활동의 목적은 들어오는 데이터를 식별하기 위한 것입니다.

   * **[!UICONTROL Enrichment]** 탭에서 **[!UICONTROL Add data]**&#x200B;을 선택하고 가져온 데이터와 수신자의 타깃팅 차원 사이의 링크를 정의합니다. 이 예에서 **CRM ID** 사용자 정의 필드를 사용하여 조인 조건을 만듭니다. 고유한 레코드를 식별할 수 있는 동안 필요한 필드 또는 필드 조합을 사용합니다.
   * **[!UICONTROL Reconciliation]** 탭에서 **[!UICONTROL Identify the document from the working data]** 옵션을 선택 해제한 상태로 두십시오.

   ![](assets/import_template_example2.png)

1. 한 전환에서 대사된 받는 사람과 조정할 수 없지만 두 번째 전환에서는 충분한 데이터가 있는 받는 사람을 검색하려면 **[!UICONTROL Split]** 활동을 구성합니다.

   조정된 받는 사람과의 전환을 사용하여 데이터베이스를 업데이트할 수 있습니다. 파일에서 최소 정보 세트를 사용할 수 있는 경우 알 수 없는 수신자가 있는 전환을 사용하여 데이터베이스에 새 받는 사람 항목을 만들 수 있습니다.

   조정할 수 없고 데이터가 충분하지 않은 수신자는 보정을 통해 아웃바운드 전환으로 선택되며 별도의 파일로 내보내거나 무시하면 됩니다.

   * 활동의 **[!UICONTROL General]** 탭에서 필터링 설정으로 **[!UICONTROL Use the additional data only]**&#x200B;을 선택하고 **[!UICONTROL Targeting dimension]**&#x200B;이(가) 자동으로 **[!UICONTROL Enrichment]**&#x200B;으로 설정되어 있는지 확인합니다.

      데이터베이스에 레코드를 삽입할 수 없는 레코드를 확인하려면 **[!UICONTROL Generate complement]** 옵션을 선택합니다. 필요한 경우 보완 데이터에 추가 처리를 적용할 수 있습니다.파일 내보내기, 목록 업데이트 등

   * **[!UICONTROL Subsets]** 탭의 첫 번째 하위 집합에서 받는 사람 기본 키가 0이 아닌 레코드만 선택하려면 인바운드 모집단에 필터링 조건을 추가합니다. 이렇게 하면 데이터베이스에서 받는 사람과 대사된 파일의 데이터가 해당 하위 집합에서 선택됩니다.

      ![](assets/import_template_example3.png)

   * 데이터베이스에 삽입할 데이터를 충분히 가진 대사되지 않은 레코드를 선택하는 두 번째 하위 집합을 추가합니다. 예:이메일 주소, 이름 및 성.

      하위 세트는 생성 순서로 처리됩니다. 즉, 이 두 번째 하위 세트가 처리되면 데이터베이스에 이미 존재하는 모든 레코드가 첫 번째 하위 세트에 선택되어 있습니다.

      ![](assets/import_template_example3_2.png)

   * 처음 두 하위 세트에서 선택되지 않은 모든 레코드는 **[!UICONTROL Complement]**&#x200B;에서 선택됩니다.

1. 이전에 구성한 **[!UICONTROL Split]** 활동의 첫 번째 아웃바운드 전환 뒤에 있는 **[!UICONTROL Update data]** 활동을 구성합니다.

   * 인바운드 전환에는 데이터베이스에 이미 있는 받는 사람만 포함되므로 **[!UICONTROL Update]**&#x200B;을 **[!UICONTROL Operation type]**&#x200B;으로 선택합니다.
   * **[!UICONTROL Record identification]** 섹션에서 **[!UICONTROL Using reconciliation keys]**&#x200B;을 선택하고 타깃팅 차원과 **[!UICONTROL Enrichment]**&#x200B;에서 만든 링크 사이에 키를 정의합니다. 이 예에서 **CRM ID** 사용자 정의 필드가 사용됩니다.
   * **[!UICONTROL Fields to update]** 섹션에서 파일의 해당 열 값으로 업데이트할 수신자 차원의 필드를 지정합니다. 파일 열 이름이 받는 사람 차원 필드의 이름과 동일하거나 거의 동일한 경우 자동 선택 단추를 사용하여 다른 필드를 자동으로 일치시킬 수 있습니다.

      ![](assets/import_template_example6.png)

1. 대사되지 않은 수신자가 포함된 전환 다음에 있는 **[!UICONTROL Deduplication]** 활동을 구성합니다.

   * **[!UICONTROL Edit configuration]**&#x200B;을 선택하고 타깃팅 차원을 워크플로의 **[!UICONTROL Enrichment]** 활동에서 생성된 임시 스키마로 설정합니다.

      ![](assets/import_template_example4.png)

   * 이 예에서는 이메일 필드를 사용하여 고유한 프로필을 찾습니다. 반드시 채워야 하는 필드와 고유한 조합의 일부를 사용할 수 있습니다.
   * **[!UICONTROL Deduplication method]** 화면에서 **[!UICONTROL Advanced parameters]**&#x200B;을 선택하고 **[!UICONTROL Disable automatic filtering of 0 ID records]** 옵션을 선택하여 기본 키가 0(이 전환의 모든 레코드여야 함)인 레코드가 제외되지 않도록 확인합니다.

   ![](assets/import_template_example7.png)

1. 이전에 구성한 **[!UICONTROL Deduplication]** 활동 뒤에 있는 **[!UICONTROL Update data]** 활동을 구성합니다.

   * 인바운드 전환에는 데이터베이스에 없는 수신자만 포함되므로 **[!UICONTROL Insert]**&#x200B;을 **[!UICONTROL Operation type]**&#x200B;으로 선택합니다.
   * **[!UICONTROL Record identification]** 섹션에서 **[!UICONTROL Directly using the targeting dimension]**&#x200B;을 선택하고 **[!UICONTROL Recipients]** 차원을 선택합니다.
   * **[!UICONTROL Fields to update]** 섹션에서 파일의 해당 열 값으로 업데이트할 수신자 차원의 필드를 지정합니다. 파일 열 이름이 받는 사람 차원 필드의 이름과 동일하거나 거의 동일한 경우 자동 선택 단추를 사용하여 다른 필드를 자동으로 일치시킬 수 있습니다.

      ![](assets/import_template_example8.png)

1. 데이터베이스에 삽입되지 않은 데이터를 추적하려면 **[!UICONTROL Split]** 활동의 세 번째 전환 후 **[!UICONTROL Data extraction (file)]** 활동 및 **[!UICONTROL File transfer]** 활동을 추가합니다. 필요한 열을 내보내고 가져올 수 있는 FTP 또는 SFTP 서버에 파일을 전송하도록 해당 활동을 구성합니다.
1. **[!UICONTROL End]** 활동을 추가하고 워크플로우 템플릿을 저장합니다.

이제 템플릿을 사용할 수 있으며 모든 새 워크플로우에 사용할 수 있습니다. 그런 다음 **[!UICONTROL Data loading (file)]** 활동에서 가져올 데이터가 포함된 파일을 모두 지정해야 합니다.

![](assets/import_template_example9.png)
