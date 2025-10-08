---
product: campaign
title: 가져오기 작업 구성
description: Campaign에서 가져오기 작업을 구성하고 실행하는 방법 알아보기
feature: Overview
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 05909ea6-2c93-42ff-9142-1dd14fa6fdec
source-git-commit: 28279c6ec0eab7f914cf6107cd1ec1cebd05113d
workflow-type: tm+mt
source-wordcount: '2983'
ht-degree: 1%

---

# 가져오기 작업 구성 {#executing-import-jobs}



Adobe Campaign을 사용하면 하나 이상의 파일에서 텍스트, CSV, TAB 또는 XML 형식으로 데이터를 데이터베이스로 가져올 수 있습니다. 이러한 파일은 테이블(기본 파일 또는 연결된 파일)과 연결되고 소스 파일의 각 필드는 데이터베이스의 필드와 연결됩니다.

>[!NOTE]
>
>**[!UICONTROL Import a list]** 함수를 사용하여 데이터베이스 데이터와 매핑하지 않고 데이터를 가져올 수 있습니다. 그런 다음 **[!UICONTROL Read list]** 개체를 통해 워크플로우에서만 데이터를 사용할 수 있습니다. 자세한 정보는 이 [페이지](../../workflow/using/read-list.md)를 참조하십시오.

가져오기 도우미에서 가져오기를 구성하고, 해당 옵션(예: 데이터 변환)을 정의하고, 실행을 시작할 수 있습니다. 가져오기 유형(단순 또는 다중)과 운영자의 권한에 따라 콘텐츠가 달라지는 일련의 화면입니다.

가져오기 도우미는 새 가져오기 작업을 만든 후에 표시됩니다([가져오기 및 내보내기 작업 만들기](../../platform/using/creating-import-export-jobs.md) 참조).

>[!NOTE]
>
>IIS 웹 서버를 사용하는 경우 대용량 파일(28MB 초과) 업로드를 승인하려면 구성이 필요할 수 있습니다. 자세한 정보는 [이 섹션](../../installation/using/integration-into-a-web-server-for-windows.md#changing-the-upload-file-size-limit)을 참조하십시오.

## 소스 파일 {#source-file}

소스 파일에서 각 행은 레코드와 일치합니다. 레코드의 데이터는 구분 기호(공백, 탭, 문자 등)로 구분됩니다. 즉, 데이터는 열 형태로 검색되며 각 열은 데이터베이스의 필드와 연결됩니다.

## 1단계 - 가져오기 템플릿 선택 {#step-1---choosing-the-import-template}

가져오기 도우미를 시작할 때 먼저 템플릿을 선택해야 합니다. 예를 들어 뉴스레터를 수신한 수신자의 가져오기를 구성하려면 아래 단계를 따르십시오.

1. **[!UICONTROL Profiles and Targets > Job > Generic imports and exports]** 폴더를 선택하십시오.
1. **새로 만들기**&#x200B;를 클릭한 다음 **가져오기**&#x200B;를 클릭하여 가져오기 템플릿을 만듭니다.

   ![](assets/s_ncs_user_import_wizard01_1.png)

1. **[!UICONTROL Import template]** 필드 오른쪽에 있는 화살표를 클릭하여 템플릿을 선택하거나 **[!UICONTROL Select link]**&#x200B;을(를) 클릭하여 트리를 찾습니다.

   기본 서식 파일은 **[!UICONTROL New text import]**&#x200B;입니다. 이 템플릿은 수정해서는 안 되지만, 필요에 따라 복제하여 새 템플릿을 구성할 수도 있습니다. 기본적으로 가져오기 템플릿은 **[!UICONTROL Profiles and targets > Templates > Job templates]** 노드에 저장됩니다.

1. **[!UICONTROL Label]** 필드에 이 가져오기의 이름을 입력하십시오. 설명을 추가할 수 있습니다.
1. 해당 필드에서 가져오기 유형을 선택합니다. 가져올 수 있는 유형에는 두 가지가 있습니다. **[!UICONTROL Simple import]**&#x200B;은(는) 한 개의 파일만 가져오고 **[!UICONTROL Multiple import]**&#x200B;은(는) 여러 개의 파일을 한 번에 가져옵니다.

   여러 번 가져오려면 가져오기 도우미의 첫 번째 화면에 있는 **[!UICONTROL Multiple import]** 드롭다운 목록에서 **[!UICONTROL Import type]**&#x200B;을(를) 선택하십시오.

   ![](assets/s_ncs_user_import_wizard01_2.png)

1. **[!UICONTROL Add]**&#x200B;을(를) 클릭하여 가져올 필드를 지정합니다.

   ![](assets/s_ncs_user_import_wizard01_3.png)

   파일을 추가할 때마다 **[!UICONTROL File to import]** 길잡이의 화면이 표시됩니다. [2단계 - Source 파일 선택](#step-2---source-file-selection) 섹션을 보고 도우미의 단계에 따라 가져오기 옵션을 간단히 정의하십시오.

   >[!NOTE]
   >
   >여러 가져오기는 특정 요구 사항만 충족해야 하며 권장되지 않습니다.

### 고급 매개 변수 {#advanced-parameters}

**[!UICONTROL Advanced parameters]** 링크를 사용하여 다음 옵션에 액세스할 수 있습니다.

* **[!UICONTROL General]** 탭

   * **[!UICONTROL Stop execution if there are too many rejects]**

     이 옵션은 기본적으로 선택되어 있습니다. 거부 수에 관계없이 가져오기를 계속 실행하려면 가져오기를 선택 해제할 수 있습니다. 기본적으로 처음 100개 행이 거부되면 실행이 중지됩니다.

   * **[!UICONTROL Trace mode]**

     각 라인에 대한 가져오기 실행을 추적하려면 이 옵션을 선택합니다.

   * **[!UICONTROL Start the job in a detached process]**

     이 옵션은 기본적으로 선택되어 있습니다. 가져오기 실행을 분리하여 데이터베이스에서 진행 중인 다른 작업에 영향을 주지 않도록 할 수 있습니다.

   * **[!UICONTROL Do not update enumerations]**

     데이터베이스에 열거형 값 목록이 보강되지 않도록 하려면 이 옵션을 선택합니다. **Adobe Campaign v8(콘솔) 설명서**&#x200B;에서 [열거형으로 작업](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/config/settings/enumerations){target=_blank}하는 방법에 대해 자세히 알아보세요.


* **[!UICONTROL Variables]** 탭

  쿼리 편집기 및 계산된 필드에서 액세스할 수 있는 작업과 관련된 변수를 정의할 수 있습니다. 변수를 만들려면 **[!UICONTROL Add]**&#x200B;을(를) 클릭하고 변수 편집기를 사용하십시오.

  >[!IMPORTANT]
  >
  >**[!UICONTROL Variables]** 탭은 워크플로 형식 프로그래밍 전용이며 전문가 사용자만 구성해야 합니다.

## 2단계 - Source 파일 선택 {#step-2---source-file-selection}

소스 파일은 텍스트 형식(txt, csv, tab, 고정 열) 또는 xml일 수 있습니다.

기본적으로 **[!UICONTROL Upload file on the server]**&#x200B;이(가) 선택되어 있습니다. **[!UICONTROL Local file]** 필드 오른쪽에 있는 폴더를 클릭하여 로컬 디스크를 찾은 다음 가져올 파일을 선택하십시오. 서버에 있는 경우 가져올 파일의 액세스 경로와 이름을 입력하려면 이 옵션을 선택 취소할 수 있습니다.

![](assets/s_ncs_user_import_wizard02_1.png)

파일이 지정되면 **[!UICONTROL Auto-detect format]**&#x200B;을(를) 클릭하여 창의 아래 섹션에서 해당 데이터를 볼 수 있습니다. 이 미리 보기에는 소스 파일의 처음 200개 행이 표시됩니다.

![](assets/s_ncs_user_import_wizard02_2.png)

이 보기 위에 제공되는 옵션을 사용하여 가져오기를 구성합니다. 이러한 옵션을 통해 정의된 매개 변수가 미리보기에 전송됩니다. 다음 옵션을 사용할 수 있습니다.

* **[!UICONTROL Click here to change the file format...]**&#x200B;을(를) 사용하면 파일 형식을 확인하고 구성을 세밀하게 조정할 수 있습니다.
* **[!UICONTROL Update on server...]**&#x200B;을(를) 사용하면 로컬 파일을 서버로 전송할 수 있습니다. 이 옵션은 **[!UICONTROL Upload file on the server]**&#x200B;을(를) 선택한 경우에만 사용할 수 있습니다.
* **[!UICONTROL Download]**&#x200B;은(는) 파일을 서버에 업로드한 경우에만 사용할 수 있습니다.
* **[!UICONTROL Auto-detect format]**&#x200B;은(는) 데이터 원본의 형식을 다시 초기화하는 데 사용됩니다. 이 옵션을 사용하면 **[!UICONTROL Click here to change the file format...]** 옵션을 통해 형식이 지정된 데이터에 원래 형식을 다시 적용할 수 있습니다.
* **[!UICONTROL Advanced parameters]** 링크를 사용하면 원본 데이터를 필터링하고 고급 옵션에 액세스할 수 있습니다. 이 화면에서 파일의 일부만 가져오도록 선택할 수 있습니다. 필터를 정의하여 해당 라인의 값에 따라 &#39;잠재 고객&#39; 또는 &#39;고객&#39; 유형 사용자만 가져올 수도 있습니다. 이러한 옵션은 전문가 JavaScript 사용자만 사용해야 합니다.

### 파일 형식 변경 {#changing-the-file-format}

**[!UICONTROL Click here to change the file format...]** 옵션을 사용하면 원본 파일의 데이터 형식을 지정할 수 있습니다. 특히 열 구분 기호 및 각 필드의 데이터 형식을 지정할 수 있습니다. 이 구성은 다음 창을 통해 수행됩니다.

![](assets/s_ncs_user_import_wizard02_3.png)

이 단계에서는 파일 필드의 값을 읽는 방법을 설명할 수 있습니다. 예를 들어, 날짜의 경우 날짜 또는 날짜 + 시간 데이터를 형식(dd/mm/yyyy, mm/dd/yy 등)과 연결할 수 있습니다. 입력 데이터가 예상 포맷과 일치하지 않으면 가져오는 동안 거부됩니다.

창의 아래쪽에 있는 미리보기 영역에서 구성 결과를 볼 수 있습니다.

**[!UICONTROL OK]**&#x200B;을(를) 클릭하여 서식을 저장한 다음 **[!UICONTROL Next]**&#x200B;을(를) 클릭하여 다음 단계를 표시합니다.

## 3단계 - 필드 매핑 {#step-3---field-mapping}

그런 다음 대상 스키마를 선택하고 각 열의 데이터를 데이터베이스의 필드에 매핑해야 합니다.

![](assets/s_ncs_user_import_wizard03_1.png)

* **[!UICONTROL Destination schema]** 필드를 사용하면 데이터를 가져올 스키마를 선택할 수 있습니다. 이 정보는 필수입니다. 기존 스키마 중 하나를 선택하려면 **[!UICONTROL Select link]** 아이콘을 클릭하십시오. **[!UICONTROL Edit link]**&#x200B;을(를) 클릭하여 선택한 테이블의 내용을 표시합니다.
* 중앙 테이블에는 소스 파일에 정의된 모든 필드가 표시됩니다. 대상 파일을 연결하려면 가져올 필드를 선택하십시오. 이러한 필드는 수동 또는 자동으로 매핑할 수 있습니다.

  필드를 수동으로 매핑하려면 확인란을 클릭하여 소스 필드를 선택하고 두 번째 열을 클릭하여 선택한 필드에 해당하는 셀을 활성화합니다. 그런 다음 **[!UICONTROL Edit expression]** 아이콘을 클릭하여 현재 테이블의 모든 필드를 표시합니다. 대상 필드를 선택하고 **[!UICONTROL OK]**&#x200B;을(를) 클릭하여 매핑의 유효성을 검사합니다.

  소스 필드와 대상 필드를 자동으로 연결하려면 필드 목록 오른쪽에 있는 **[!UICONTROL Guess the destination fields]** 아이콘을 클릭합니다. 필요한 경우 제안된 필드를 수정할 수 있습니다.

  >[!IMPORTANT]
  >
  >다음 단계로 진행하기 전에 이 작업의 결과를 항상 확인해야 합니다.

* 가져온 필드에 변형을 적용할 수 있습니다. 이렇게 하려면 해당 필드와 관련된 **[!UICONTROL Transformation]** 열의 셀을 클릭하고 적용할 변형을 선택합니다.

  ![](assets/s_ncs_user_import_wizard03_2.png)

  >[!IMPORTANT]
  >
  >가져오기를 수행할 때 변환이 적용됩니다. 그러나 대상 필드에 대한 제약 조건이 정의된 경우(위의 예에서 @lastname 필드에서) 이러한 제약 조건이 우선합니다.

* 중앙 테이블의 오른쪽에 있는 적절한 아이콘을 사용하여 계산된 필드를 추가할 수 있습니다. 계산된 필드를 사용하면 복잡한 변환을 수행하거나 가상 열을 추가하거나 여러 열의 데이터를 병합할 수 있습니다. 다양한 가능성에 대한 자세한 내용은 다음 섹션을 참조하십시오.

### 계산된 필드 {#calculated-fields}

계산된 필드는 소스 파일에 추가된 새 열이며 다른 열에서 계산됩니다. 그런 다음 계산된 필드를 Adobe Campaign 데이터베이스의 필드와 연결할 수 있습니다. 그러나 계산된 필드에서는 조정 작업을 수행할 수 없습니다.

계산된 필드에는 네 가지 유형이 있습니다.

* **[!UICONTROL Fixed string]**: 계산된 필드의 값이 원본 파일의 모든 줄에 대해 동일합니다. 삽입되거나 업데이트된 레코드의 필드 값을 설정할 수 있습니다. 예를 들어 가져온 모든 레코드에 대해 마커를 &quot;yes&quot;로 설정할 수 있습니다.
* **[!UICONTROL String with JavaScript tags]**: 계산된 필드의 값이 JavaScript 명령을 포함하는 문자열입니다.
* **[!UICONTROL JavaScript expression]**: 계산된 필드의 값은 JavaScript 함수를 평가한 결과입니다. 반환되는 값은 숫자, 날짜 등이 될 수 있습니다.
* **[!UICONTROL Enumeration]**: 필드의 값은 원본 파일에 포함된 값에 따라 달라집니다. 편집기를 사용하면 다음 예제와 같이 소스 열을 지정하고 열거형 값 목록을 입력할 수 있습니다.

  ![](assets/s_ncs_user_import_wizard03_3.png)

  **[!UICONTROL Preview]** 탭에서는 정의된 구성의 결과를 볼 수 있습니다. 여기에 **[!UICONTROL Subscription]** 열이 추가되었습니다. **상태** 필드에서 값을 계산합니다.

  ![](assets/s_ncs_user_import_wizard03_4.png)

## 4단계 - 조정 {#step-4---reconciliation}

가져오기 도우미의 조정 단계에서는 파일의 데이터를 데이터베이스의 기존 데이터와 조정하는 모드를 정의하고 파일 데이터와 데이터베이스 데이터 간의 우선순위 규칙을 설정할 수 있습니다. 구성 창은 다음과 같습니다.

![](assets/s_ncs_user_import_wizard04_1.png)

화면의 중앙 섹션에는 데이터를 가져올 Adobe Campaign 데이터베이스의 필드 및 테이블이 있는 트리가 포함되어 있습니다.

각 노드(테이블 또는 필드)에 대해 특수 옵션을 사용할 수 있습니다. 목록에서 관련 노드를 클릭하면 해당 매개 변수와 간단한 설명이 아래에 표시됩니다. 각 요소에 대해 정의된 동작이 해당 **[!UICONTROL Behavior]** 열에 표시됩니다.

![](assets/s_ncs_user_import_wizard04_2.png)

### 작업 유형 {#types-of-operation}

가져오기와 관련된 각 테이블에 대해 작업 유형을 정의해야 합니다. 데이터베이스의 기본 요소에 사용할 수 있는 작업은 다음과 같습니다.

* **[!UICONTROL Update or insertion]**: 데이터베이스에 있는 경우 레코드를 업데이트하고 없는 경우 만듭니다.
* **[!UICONTROL Insertion]**: 데이터베이스에 레코드를 삽입합니다.
* **[!UICONTROL Update]**: 기존 레코드만 업데이트합니다(다른 레코드는 무시함).
* **[!UICONTROL Reconciliation only]**: 데이터베이스에서 레코드를 검색하지만 업데이트를 수행하지 않습니다. 예를 들어 폴더의 데이터를 업데이트하지 않고 파일의 열에 따라 가져올 수신자 폴더를 연결할 수 있습니다.
* **[!UICONTROL Deletion]**: 데이터베이스의 레코드를 제거할 수 있습니다.

가져오기와 관련된 테이블의 각 필드에 대해 다음 옵션을 사용할 수 있습니다.

* **[!UICONTROL Update (empty) if source value is empty]**: 업데이트 시 원본 파일의 필드가 비어 있으면 필드의 값이 데이터베이스 값을 제거합니다. 그렇지 않으면 데이터베이스 필드가 유지됩니다.
* **[!UICONTROL Update only if destination is empty]**: 데이터베이스 필드가 비어 있지 않으면 원본 파일의 값이 데이터베이스 필드의 값을 덮어쓰지 않습니다. 이 경우 소스 파일의 값을 가져옵니다.
* **[!UICONTROL Update the field only when the record is inserted]**: 업데이트 또는 삽입 작업 중에 새로운 원본 파일 레코드만 가져옵니다.

>[!NOTE]
>
>조정 키의 정의는 중복 제거가 없는 삽입의 경우를 제외하고 항상 **필수**&#x200B;입니다.

### 조정 키 {#reconciliation-keys}

중복 제거를 관리하려면 하나 이상의 조정 키를 입력해야 합니다.

조정 키는 레코드를 식별하는 데 사용되는 필드 세트입니다. 예를 들어 수신자를 가져오려면 조정 키는 계정 번호, &quot;이메일&quot; 필드 또는 &quot;성, 이름, 회사&quot; 필드 등이 될 수 있습니다.

이 경우 파일 행이 데이터베이스의 기존 수신자와 일치하는지 확인하기 위해 가져오기 엔진은 키의 모든 필드에 대해 파일 값을 데이터베이스의 값과 비교합니다. 필드가 레코드에 고유한 경우 소스 데이터와 대상 데이터 간의 정확한 비교를 수행하여 가져오기 후 데이터의 무결성을 보장할 수 있습니다. 두 번째 조정 키는 동일한 테이블에 대해 채울 수 있습니다. 첫 번째 키가 비어 있는 라인에 사용됩니다.

가져오는 동안 수정할 수 있는 필드를 선택하지 마십시오. 이 경우 엔진이 추가 레코드를 만들 수 있습니다.

![](assets/s_ncs_user_import_wizard04_3.png)

>[!NOTE]
>
>수신자 가져오기의 경우 선택한 폴더의 식별자가 키에 암시적으로 추가됩니다.
>
>따라서 폴더를 선택하지 않은 경우에만 이 폴더에 대해 조정이 수행됩니다.

### 중복 제거 {#deduplication}

>[!NOTE]
>
>&#39;double&#39;은 가져올 파일에 두 번 이상 존재하는 항목입니다.
>
>&#39;복제&#39;는 가져올 파일과 데이터베이스에 모두 있는 항목입니다.

**[!UICONTROL Management of doubles]** 필드를 사용하면 데이터 중복 제거를 구성할 수 있습니다. 중복 제거는 소스 파일&#x200B;**(또는 여러 파일을 가져오는 경우 소스 파일)에**&#x200B;번 나타나는 레코드, 즉 조정 키의 필드가 동일한 행과 관련이 있습니다.

* **[!UICONTROL Update]** 모드(기본 모드)의 중복 관리는 중복 제거를 수행하지 않습니다. 따라서 마지막 레코드에는 우선 순위가 있습니다(이전 레코드의 데이터를 업데이트하기 때문). 이 모드에서는 중복 항목 계산이 수행되지 않습니다.
* **[!UICONTROL Ignore]** 모드 또는 **[!UICONTROL Reject entity]**&#x200B;의 중복 관리는 가져오기에서 중복을 제외합니다. 이 경우 레코드를 가져오지 않습니다.
* **[!UICONTROL Reject entity]** 모드에서 요소를 가져오지 않았으며 가져오기 로그에 오류가 생성됩니다.
* **[!UICONTROL Ignore]** 모드에서는 요소를 가져오지 않지만 오류 추적은 유지되지 않습니다. 이 모드를 사용하면 성능을 최적화할 수 있습니다.

>[!IMPORTANT]
>
>중복 제거는 메모리에서만 수행됩니다. 따라서 중복 제거가 포함된 가져오기의 크기는 제한됩니다. 제한은 여러 매개 변수(애플리케이션 서버의 용량, 활동, 키의 필드 수 등)에 따라 다릅니다. 중복 제거의 최대 크기는 1,000,000줄 정도입니다.

데이터 중복 제거는 소스 파일과 데이터베이스에 모두 존재하는 레코드와 관련이 있습니다. 업데이트만 포함된 작업(예: **[!UICONTROL Update and insertion]** 또는 **[!UICONTROL Update]**)과 관련된 것입니다. **[!UICONTROL Duplicate management]** 옵션을 사용하면 원본 파일과 데이터베이스 모두에 있는 레코드를 업데이트하거나 무시할 수 있습니다. **[!UICONTROL Update or insert based on origin]** 옵션은 선택적 모듈에 속하며 표준 컨텍스트에서 사용할 수 없습니다.

**[!UICONTROL Reject]** 및 **[!UICONTROL Ignore]** 옵션은 위에 표시된 대로 작동합니다.

### 오류가 있는 경우 {#behavior-in-the-event-of-an-error}

대부분의 데이터 전송 작업은 다양한 유형의 오류(비간섭적 라인 형식, 잘못된 이메일 주소 등)를 생성합니다. 가져오기 엔진에서 생성된 모든 오류 및 모든 경고가 저장되고 가져오기 인스턴스에 연결됩니다.

![](assets/s_ncs_user_import_general_tab.png)

이러한 거부에 대한 자세한 내용은 **[!UICONTROL Rejects]** 탭을 통해 볼 수 있습니다.

![](assets/s_ncs_user_import_rejets_tab.png)

두 가지 유형의 거부가 있습니다(**[!UICONTROL Connector]** 열에 유형이 표시됨).

* 텍스트 커넥터 거부는 파일 라인을 처리하는 동안 발생하는 오류(계산된 필드, 데이터 분석 등)와 관련이 있습니다. 이 경우 오류가 발생하면 전체 줄을 항상 거부합니다.
* 데이터베이스 커넥터가 거부하면 데이터 조정 또는 데이터베이스에 쓰는 동안 오류가 발생합니다. 여러 테이블로 가져오는 경우 거부는 레코드의 일부에만 영향을 줄 수 있습니다(예: 수신자 및 관련 이벤트 가져오기의 경우 오류가 발생하면 수신자를 거부하지 않고 이벤트가 업데이트되지 않음).

데이터 조정 페이지에서 필드별로 원하는 오류 관리 유형 필드를 정의하고 테이블별로 테이블을 정의할 수 있습니다.

* **[!UICONTROL Ignore and log a warning]**: 오류가 발생한 필드를 제외한 모든 필드를 데이터베이스로 가져옵니다.
* **[!UICONTROL Reject parent element]**: 오류가 발생한 필드뿐만 아니라 레코드의 전체 줄이 거부됩니다.
* **[!UICONTROL Reject all elements]**: 가져오기가 중지되고 레코드의 모든 요소가 거부되었습니다.

  ![](assets/s_ncs_user_import_wizard04_4.png)

가져오기 인스턴스의 거부 화면에 있는 트리는 거부된 필드와 오류가 발생한 위치를 나타냅니다.

**[!UICONTROL Export rejects]** 아이콘을 통해 다음 레코드가 포함된 파일을 생성할 수 있습니다.

![](assets/s_ncs_user_import_errors_export.png)

## 5단계 - 수신자를 가져올 때 추가 단계 {#step-5---additional-step-when-importing-recipients}

가져오기 도우미의 다음 단계에서는 데이터를 가져올 폴더를 선택하거나 만들고, 가져온 수신자를 (신규 또는 기존) 목록에 자동으로 매핑하고, 수신자를 서비스에 가입할 수 있습니다.

![](assets/s_ncs_user_import_wizard05_1.png)

>[!NOTE]
>
>이 단계는 수신자만 가져올 때와 기본 Adobe Campaign 수신자 테이블(**nms:recipient**)을 사용할 때 나타납니다.

* **[!UICONTROL Edit]** 링크를 클릭하여 수신자를 연결하거나 구독할 폴더, 목록 또는 서비스를 선택합니다.

   1. 폴더로 가져오기

      **[!UICONTROL Edit...]** 섹션의 **[!UICONTROL Import into a folder]** 링크를 사용하여 수신자를 가져올 폴더를 선택하거나 만들 수 있습니다. 기본적으로 정의된 파티션이 없으면 데이터를 연산자의 기본 폴더로 가져옵니다.

      >[!NOTE]
      >
      >연산자의 기본 폴더는 연산자가 쓰기 액세스 권한을 갖는 첫 번째 폴더입니다. [폴더 액세스 관리](../../platform/using/access-management-folders.md)에서 자세히 알아보세요.

      가져오기 폴더를 선택하려면 **[!UICONTROL Folder]** 필드 오른쪽에 있는 화살표를 클릭하고 관련 폴더를 선택합니다. **[!UICONTROL Select link]** 아이콘을 사용하여 새 창에 트리를 표시하거나 새 폴더를 만들 수도 있습니다.

      ![](assets/s_ncs_user_import_wizard05_2.png)

      새 폴더를 만들려면 폴더를 추가할 노드를 선택하고 마우스 오른쪽 단추를 클릭합니다. **[!UICONTROL Create a new 'Recipients' folder]**&#x200B;을(를) 선택합니다.

      ![](assets/s_ncs_user_import_wizard05_3.png)

      폴더가 현재 노드 아래에 추가됩니다. 새 폴더 이름을 입력하고 Enter 키를 눌러 확인한 다음 **[!UICONTROL OK]**&#x200B;을(를) 클릭합니다.

      ![](assets/s_ncs_user_import_wizard05_4.png)

   1. 목록과 연결

      **[!UICONTROL Edit...]** 섹션의 **[!UICONTROL Add recipients to a list]** 링크를 사용하여 수신자를 가져올 목록을 선택하거나 만들 수 있습니다.

      ![](assets/s_ncs_user_import_wizard05_5.png)

      **[!UICONTROL Select link]**&#x200B;을(를) 클릭한 다음 **[!UICONTROL Create]**&#x200B;을(를) 클릭하여 이러한 받는 사람에 대한 새 목록을 만들 수 있습니다. 목록 만들기 및 관리는 [이 섹션](../../platform/using/creating-and-managing-lists.md)에 표시됩니다.

      ![](assets/s_ncs_user_import_wizard05_6.png)

      목록에 이미 있는 수신자에 수신자를 추가하거나 새 수신자가 있는 목록을 다시 만들도록 결정할 수 있습니다. 이 경우 목록에 수신자가 이미 포함되어 있으면 삭제되고 가져온 수신자로 바뀝니다.

   1. 서비스 구독

      가져온 모든 수신자를 정보 서비스에 가입하려면 **[!UICONTROL Edit...]** 섹션의 **[!UICONTROL Subscribe recipients to a service]** 링크를 클릭하여 수신자가 가입할 정보 서비스를 선택하거나 만드십시오. **[!UICONTROL Send a confirmation message]** 옵션을 선택할 수 있습니다. 이 메시지의 내용은 구독 서비스와 연결된 게재 템플릿에 정의되어 있습니다.

      ![](assets/s_ncs_user_import_wizard05_7.png)

      **[!UICONTROL Select link]**&#x200B;을(를) 클릭한 다음 **[!UICONTROL Create]** 아이콘을 클릭하여 이러한 수신자에 대한 새 서비스를 만들 수 있습니다. 정보 서비스 관리는 [이 섹션](../../delivery/using/managing-subscriptions.md)에 나와 있습니다.

* **[!UICONTROL Origin]** 필드를 사용하여 받는 사람의 원본 정보를 프로필에 추가하십시오. 이 정보는 다중 가져오기의 프레임워크 내에서 특히 유용합니다.

**[!UICONTROL Next]**&#x200B;을(를) 클릭하여 이 단계의 유효성을 검사하고 다음 단계를 표시합니다.

## 6단계 - 가져오기 시작 {#step-6---launching-the-import}

도우미의 마지막 단계에서는 데이터 가져오기를 시작할 수 있습니다. 이렇게 하려면 **[!UICONTROL Start]** 단추를 클릭하십시오.

![](assets/s_ncs_user_import_wizard06_1.png)

그런 다음 가져오기 작업의 실행을 모니터링할 수 있습니다([작업 실행 모니터링](../../platform/using/monitoring-jobs-execution.md) 참조).
