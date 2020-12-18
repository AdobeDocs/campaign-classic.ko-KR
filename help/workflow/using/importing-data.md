---
solution: Campaign Classic
product: campaign
title: 데이터 가져오기
description: Adobe Campaign에서 데이터를 가져오는 방법 살펴보기
audience: workflow
content-type: reference
topic-tags: -general-operation
translation-type: tm+mt
source-git-commit: 49f3c123cb8e91b3a2a2a1eb6bd593a242b8bbfe
workflow-type: tm+mt
source-wordcount: '2476'
ht-degree: 1%

---


# 데이터 가져오기{#importing-data}

>[!CAUTION]
>
>데이터를 가져오는 동안 Adobe Campaign 계약에 따라 SFTP 저장소, 데이터베이스 저장소 및 활성 프로필 제한에 주의하십시오.

## 데이터 수집 방법 {#how-to-collect-data}

### 목록의 데이터 사용:목록 읽기 {#using-data-from-a-list--read-list}

워크플로우에서 전송된 데이터는 데이터가 미리 준비하고 구조화된 목록에서 가져올 수 있습니다.

이 목록은 Adobe Campaign에서 직접 만들거나 **[!UICONTROL Import a list]** 옵션으로 가져올 수 있습니다. 이 옵션에 대한 자세한 내용은 이 [페이지](../../platform/using/generic-imports-and-exports.md)를 참조하십시오.

워크플로우에서 목록 읽기 활동 사용에 대한 자세한 내용은 [목록 읽기](../../workflow/using/read-list.md)를 참조하십시오.

### {#loading-data-from-a-file} 파일에서 데이터 로드

워크플로우에서 처리된 데이터를 구조화된 파일에서 추출하여 Adobe Campaign으로 가져올 수 있습니다.

로드 데이터 활동에 대한 설명은 [데이터 로드(파일)](../../workflow/using/data-loading--file-.md) 섹션에서 찾을 수 있습니다.

가져올 구조화된 파일의 예:

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

## 데이터 {#best-practices-when-importing-data} 가져오기 시 모범 사례

아래 설명된 몇 가지 간단한 규칙을 주의하고 준수하면 데이터베이스 내에서 데이터 일관성을 유지하고 데이터베이스 업데이트나 데이터 내보내기 중에 발생하는 일반적인 오류를 방지하는 데 많은 도움이 됩니다.

### 가져오기 템플릿 사용 {#using-import-templates}

대부분의 가져오기 워크플로우는 다음 활동을 포함해야 합니다.**[!UICONTROL Data loading (file)]**, **[!UICONTROL Enrichment]**, **[!UICONTROL Split]**, **[!UICONTROL Deduplication]**, **[!UICONTROL Update data]**.

가져오기 템플릿을 사용하면 유사한 가져오기 작업을 손쉽게 준비하고 데이터베이스 내에서 데이터 일관성을 유지할 수 있습니다. [워크플로우 템플릿](../../workflow/using/building-a-workflow.md#workflow-templates) 섹션에서 워크플로우 템플릿을 작성하는 방법을 알아봅니다.

많은 프로젝트에서 가져오기는 프로젝트에 사용된 파일에 중복이 없으므로 **[!UICONTROL Deduplication]** 작업 없이 빌드됩니다. 다른 파일을 가져올 때 중복이 나타나는 경우가 있습니다. 데이터 중복 제거는 매우 어렵습니다. 따라서 모든 가져오기 워크플로우에서 데이터 중복 제거 단계를 수행하는 것이 매우 좋습니다.

수신 데이터가 일관되고 올바르거나 IT 부서 또는 Adobe Campaign 관리자가 처리하도록 하는 것을 고려해 두지 마십시오. 프로젝트 중에 데이터 정리를 염두에 두십시오. 데이터를 가져올 때 중복 제거, 조정 및 일관성을 유지할 수 있습니다.

가져오기 템플릿 예는 [반복 가져오기 설정](#setting-up-a-recurring-import) 섹션에서 사용할 수 있습니다.

### 플랫 파일 형식 사용 {#using-flat-file-formats}

가장 효율적인 가져오기 형식은 플랫 파일입니다. 데이터베이스 수준에서 플랫 파일을 벌크 모드로 가져올 수 있습니다.

예제:

* 구분 기호:탭 또는 세미콜론
* 머리글이 있는 첫 줄
* 문자열 구분 기호 없음
* 날짜 형식:YYYY/MM/DD HH:mm:SS

Adobe Campaign은 표준 파일 가져오기 작업을 사용하여 XML 파일을 가져올 수 없습니다. JavaScript를 사용하여 XML 파일을 가져올 수 있지만 적은 볼륨만 가져올 수 있습니다.파일당 10K 미만의 레코드

### 압축 및 암호화 사용 {#using-compression-and-encryption}

가능하면 파일을 압축 파일로 가져오고 내보냅니다.

Linux에서는 명령줄을 사용하여 파일의 압축을 풀고 동시에 가져올 수 있습니다. 예제:

```
zcat nl6/var/vp/import/filename.gz
```

또한 안전하지 않을 경우 네트워크를 통해 전송되는 파일을 암호화하는 것이 좋습니다. GPG는 여기에 사용할 수 있습니다.

### {#loading-data-in-batch-from-files} 파일에서 데이터를 일괄 로드

파일에서 데이터를 일괄적으로 로드하는 것은 한 번에 한 줄씩 실시간으로(예: 웹 서비스를 통해) 로드하는 것보다 더 효과적입니다.

웹 서비스를 사용하여 가져오는 것은 효율적이지 않습니다. 가능하면 파일을 사용하는 것이 가장 좋습니다.

또한 라인 수준에서 작동하기 때문에 외부 웹 서비스를 통해 실시간으로 프로파일을 강화하도록 하면 성능 문제와 메모리 누수가 발생할 수 있습니다.

데이터를 가져와야 하는 경우에는 웹 응용 프로그램 또는 웹 서비스를 사용하는 것보다 작업 과정을 사용하여 데이터를 일괄적으로 가져오는 것이 더 좋습니다.

### 데이터 관리 사용 {#using-data-management}

JavaScript를 사용하여 반복 모드(행)로 로드하는 것은 작은 볼륨으로 제한되어야 합니다.

효율성을 높이기 위해 데이터 관리 워크플로우에서 항상 **[!UICONTROL Data Loading (File)]** 활동을 사용하십시오.

### 델타 모드 {#importing-in-delta-mode}에서 가져오기

일반 가져오기는 델타 모드에서 수행해야 합니다. 즉, 수정되거나 새 데이터만 항상 전체 테이블이 아니라 Adobe Campaign으로 전송됩니다.

전체 가져오기는 초기 로드에만 사용해야 합니다.

JavaScript가 아니라 데이터 관리를 사용하여 데이터를 가져옵니다.

### 일관성 유지{#maintaining-consistency}

Adobe Campaign 데이터베이스에서 데이터 일관성을 유지하려면 아래 원칙을 따르십시오.

* 가져온 데이터가 Adobe Campaign의 참조 테이블과 일치하면 워크플로우의 해당 테이블과 대사되어야 합니다. 일치하지 않는 레코드는 거부해야 합니다.
* 가져온 데이터가 항상 **&quot;정규화된&quot;**(이메일, 전화 번호, DM 주소) 이고 이 표준화가 안정적이며 수년 동안 변경되지 않는지 확인합니다. 이 경우 데이터베이스에 일부 중복 항목이 표시될 가능성이 있으며 Adobe Campaign은 &quot;퍼지&quot; 일치를 수행하는 도구를 제공하지 않으므로 이러한 항목을 관리하고 제거하는 것은 매우 어렵습니다.
* 트랜잭션 데이터에는 조정 키가 있어야 하며, 중복을 만들지 않도록 기존 데이터와 대사해야 합니다.
* **관련 파일을 순서대로** 가져옵니다.

   가져오기가 서로 의존하는 여러 파일로 구성된 경우 작업 과정에서는 파일을 올바른 순서로 가져왔는지 확인해야 합니다. 파일이 실패하면 다른 파일은 가져오지 않습니다.

* **데이터를 가져올** 때 중복 제거, 조정 및 일관성을 유지할 수 있습니다.

## 사용 사례:반복 가져오기 {#setting-up-a-recurring-import} 설정

가져오기 템플릿을 사용하는 것은 구조가 동일한 파일을 정기적으로 가져와야 하는 경우에 가장 좋습니다.

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

## {#unzipping-or-decrypting-a-file-before-processing}을(를) 처리하기 전에 파일의 압축을 풀거나 해독하는 중

### 사전 처리 단계 정보 {#about-pre-processing-stages}

Adobe Campaign을 사용하면 압축 또는 암호화된 파일을 가져올 수 있습니다. [데이터 로드(파일)](../../workflow/using/data-loading--file-.md) 활동에서 읽으려면 먼저 사전 처리를 정의하여 파일을 압축 해제하거나 해독할 수 있습니다.

그렇게 하려면 다음을 수행하십시오.

1. 공개/비공개 키 쌍을 생성하려면 [Campaign 컨트롤 패널](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#decrypting-data)을 사용합니다.

   >[!NOTE]
   >
   >Campaign 컨트롤 패널은 AWS를 통해 호스팅되는 모든 고객에게 제공됩니다(마케팅 인스턴스를 사내에 호스트하는 고객 제외).

1. Adobe Campaign 설치가 Adobe을 통해 호스팅되는 경우 Adobe 고객 지원 센터에 문의하여 서버에 필요한 유틸리티를 설치하도록 하십시오.
1. Adobe Campaign의 설치를 온-프레미스 경우 사용할 유틸리티를 설치합니다(예:GPG, GZIP) 및 응용 프로그램 서버에 필요한 키(암호화 키)가 있습니다.

그런 다음 원하는 사전 처리 명령을 워크플로우에 사용할 수 있습니다.

1. 워크플로우에서 **[!UICONTROL File transfer]** 활동을 추가하고 구성합니다.
1. **[!UICONTROL Data loading (file)]** 활동을 추가하고 파일 형식을 정의합니다.
1. **[!UICONTROL Pre-process the file]** 옵션을 선택합니다.
1. 적용할 사전 처리 명령을 지정합니다.
1. 다른 활동을 추가하여 파일에서 가져오는 데이터를 관리합니다.
1. 워크플로우를 저장하고 실행합니다.

아래의 사용 사례에는 예가 나와 있습니다.

**관련 항목:**

* [데이터 로드(파일) 활동](../../workflow/using/data-loading--file-.md).
* [파일](../../workflow/using/how-to-use-workflow-data.md#zipping-or-encrypting-a-file) 압축 또는 암호화

### 사용 사례:Campaign 컨트롤 패널 {#use-case-gpg-decrypt}에서 생성된 키를 사용하여 암호화된 데이터 가져오기

이 경우 Campaign 컨트롤 패널에서 생성된 키를 사용하여 외부 시스템에서 암호화된 데이터를 가져오기 위한 워크플로우를 구축합니다.

![](assets/do-not-localize/how-to-video.png) [비디오에서 이 기능 살펴보기](#video)

이 사용 사례를 수행하는 단계는 다음과 같습니다.

1. Campaign 컨트롤 패널을 사용하여 키 쌍(공개/비공개)을 생성합니다. 자세한 단계는 [Campaign 컨트롤 패널 설명서](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#decrypting-data)에서 확인할 수 있습니다.

   * 공개 키는 Campaign으로 전송할 데이터를 암호화하는 데 사용하는 외부 시스템과 공유됩니다.
   * 개인 키는 Campaign Classic에서 들어오는 암호화된 데이터를 해독하는 데 사용됩니다.

   ![](assets/gpg_generate.png)

1. 외부 시스템에서는 Campaign 컨트롤 패널에서 다운로드한 공개 키를 사용하여 Campaign Classic으로 가져올 데이터를 암호화합니다.

1. Campaign Classic에서 Campaign 컨트롤 패널을 통해 설치된 개인 키를 사용하여 암호화된 데이터를 가져오고 이를 해독하는 작업 과정을 만듭니다. 이렇게 하려면 다음과 같이 워크플로우를 구성합니다.

   ![](assets/gpg_import_workflow.png)

   * **[!UICONTROL File transfer]** 활동:외부 소스에서 Campaign Classic으로 파일을 전송합니다. 이 예에서는 SFTP 서버에서 파일을 전송하려고 합니다.
   * **[!UICONTROL Data loading (file)]** 활동:파일의 데이터를 데이터베이스에 로드하고 Campaign 컨트롤 패널에 생성된 개인 키를 사용하여 이를 해독합니다.

1. **[!UICONTROL File transfer]** 활동을 연 다음 암호화된 .gpg 파일을 가져올 외부 계정을 지정합니다.

   ![](assets/gpg_key_transfer.png)

   활동을 구성하는 방법에 대한 글로벌 개념은 [이 섹션](../../workflow/using/file-transfer.md)에서 사용할 수 있습니다.

1. **[!UICONTROL Data loading (file)]** 활동을 연 다음 필요에 따라 구성합니다. 활동을 구성하는 방법에 대한 글로벌 개념은 [이 섹션](../../workflow/using/data-loading--file-.md)에서 사용할 수 있습니다.

   들어오는 데이터의 암호를 해독하려면 사전 처리 단계를 활동에 추가합니다. 이렇게 하려면 **[!UICONTROL Pre-process the file]** 옵션을 선택한 다음 **[!UICONTROL Command]** 필드에 이 암호 해독 명령을 복사하여 붙여 넣습니다.

   `gpg --batch --passphrase passphrase --decrypt <%=vars.filename%>`

   ![](assets/gpg_load.png)

   >[!CAUTION]
   >
   >이 예에서는 기본적으로 &quot;암호 문구&quot;인 Campaign 컨트롤 패널에서 사용하는 암호를 사용합니다.
   >
   >이전에 고객 지원 요청을 통해 인스턴스에 이미 GPG 키가 설치되어 있는 경우 암호가 변경되었으며 기본적으로 다른 형태일 수 있습니다.

1. **[!UICONTROL OK]**&#x200B;을 클릭하여 활동 구성을 확인합니다.

1. 이제 워크플로우를 실행할 수 있습니다. 이 파일이 실행되면 워크플로우 로그에서 암호 해독이 실행되었고 파일의 데이터를 가져올 수 있습니다.

   ![](assets/gpg_run.png)

### 자습서 비디오 {#video}

이 비디오에서는 GPG 키를 사용하여 데이터를 해독하는 방법을 보여 줍니다.

>[!VIDEO](https://video.tv.adobe.com/v/36482?quality=12)

추가 Campaign Classic 방법 비디오는 [여기](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=ko)에서 사용할 수 있습니다.
