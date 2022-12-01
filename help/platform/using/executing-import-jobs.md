---
product: campaign
title: 가져오기 작업 구성
description: Campaign Classic에서 가져오기 작업을 구성하고 실행하는 방법을 알아봅니다.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 05909ea6-2c93-42ff-9142-1dd14fa6fdec
source-git-commit: f000cb8bae164c22d1ede15db4e763cf50530674
workflow-type: tm+mt
source-wordcount: '2955'
ht-degree: 1%

---

# 가져오기 작업 구성 {#executing-import-jobs}

![](../../assets/common.svg)

Adobe Campaign을 사용하면 하나 이상의 파일에서 텍스트, CSV, TAB 또는 XML 형식으로 데이터를 데이터베이스로 가져올 수 있습니다. 이러한 파일은 테이블(주 파일 또는 연결된)과 연결되며 소스 파일의 각 필드는 데이터베이스의 필드와 연결됩니다.

>[!NOTE]
>
>를 사용하여 데이터를 데이터베이스 데이터와 매핑하지 않고 가져올 수 있습니다 **[!UICONTROL Import a list]** 함수 위에 있어야 합니다. 그런 다음 를 통해 워크플로우에서만 데이터를 사용할 수 있습니다 **[!UICONTROL Read list]** 개체. 자세한 정보는 이 [페이지](../../workflow/using/read-list.md)를 참조하십시오.

가져오기 마법사를 사용하여 가져오기를 구성하고 해당 옵션(예: 데이터 변형)을 정의하고 실행을 시작할 수 있습니다. 가져오기 유형(단순 또는 다중)과 연산자의 권한에 따라 컨텐츠가 달라집니다.

새 가져오기 작업을 만들면 가져오기 마법사가 표시됩니다( [가져오기 및 내보내기 작업 만들기](../../platform/using/creating-import-export-jobs.md).

>[!NOTE]
>
>IIS 웹 서버를 사용하는 경우 대용량 파일(28MB)을 업로드하는 데 구성이 필요할 수 있습니다. 자세한 정보는 [이 섹션](../../installation/using/integration-into-a-web-server-for-windows.md#changing-the-upload-file-size-limit)을 참조하십시오.

## 소스 파일 {#source-file}

소스 파일에서 각 행은 레코드와 일치합니다. 레코드의 데이터는 구분 기호(공백, 탭, 문자 등)로 구분됩니다. 즉, 데이터가 열 형태로 검색되고 각 열이 데이터베이스의 필드와 연결됩니다.

## 1단계 - 가져오기 템플릿 선택 {#step-1---choosing-the-import-template}

가져오기 마법사를 시작할 때 먼저 템플릿을 선택해야 합니다. 예를 들어 뉴스레터를 받은 수신자의 가져오기를 구성하려면 아래 단계를 따르십시오.

1. 을(를) 선택합니다 **[!UICONTROL Profiles and Targets > Job > Generic imports and exports]** 폴더를 입력합니다.
1. 클릭 **새로 만들기** 을 클릭한 다음 **가져오기** 가져오기 템플릿을 만들려면

   ![](assets/s_ncs_user_import_wizard01_1.png)

1. 오른쪽 화살표 클릭 **[!UICONTROL Import template]** 필드를 클릭하여 템플릿을 선택하거나 **[!UICONTROL Select link]** 트리를 찾아보려면

   기본 템플릿은 다음과 같습니다 **[!UICONTROL New text import]**. 이 템플릿은 수정할 수 없지만 요구 사항에 따라 새 템플릿을 구성하기 위해 복제할 수 있습니다. 기본적으로 가져오기 템플릿은 **[!UICONTROL Profiles and targets > Templates > Job templates]** 노드 아래에 있어야 합니다.

1. 에 이 가져오기의 이름을 입력합니다. **[!UICONTROL Label]** 필드. 설명을 추가할 수 있습니다.
1. 해당 필드에서 가져오기 유형을 선택합니다. 가져올 수 있는 가져오기 유형은 다음 두 가지가 있습니다. **[!UICONTROL Simple import]** 한 파일만 가져오려면 **[!UICONTROL Multiple import]** 여러 파일을 한 번에 가져올 수 있습니다.

   여러 가져오기의 경우 **[!UICONTROL Multiple import]** 에서 **[!UICONTROL Import type]** 가져오기 마법사의 첫 번째 화면에 있는 드롭다운 목록입니다.

   ![](assets/s_ncs_user_import_wizard01_2.png)

1. 을 클릭하여 가져올 필드를 지정합니다 **[!UICONTROL Add]**.

   ![](assets/s_ncs_user_import_wizard01_3.png)

   파일을 추가할 때마다 **[!UICONTROL File to import]** 마법사가 표시됩니다. 섹션을 참조하십시오. [2단계 - 소스 파일 선택](#step-2---source-file-selection) 및 마법사의 단계에 따라 간단한 가져오기에 대한 가져오기 옵션을 정의합니다.

   >[!NOTE]
   >
   >여러 가져오기는 특정 요구 사항만 처리되어야 하며 권장되지 않습니다.

### 고급 매개 변수 {#advanced-parameters}

다음 **[!UICONTROL Advanced parameters]** 링크를 통해 다음 옵션에 액세스할 수 있습니다.

* **[!UICONTROL General]** 탭

   * **[!UICONTROL Stop execution if there are too many rejects]**

      이 옵션은 기본적으로 선택되어 있습니다. 거부 수에 관계없이 가져오기를 계속 실행하려는 경우 이 옵션을 선택 취소할 수 있습니다. 기본적으로 처음 100개 줄이 거부되면 실행이 중지됩니다.

   * **[!UICONTROL Trace mode]**

      각 라인에 대한 가져오기 실행을 추적하려면 이 옵션을 선택합니다.

   * **[!UICONTROL Start the job in a detached process]**

      이 옵션은 기본적으로 선택되어 있습니다. 이 옵션을 통해 데이터베이스에서 진행 중인 다른 작업에 영향을 주지 않도록 가져오기 실행을 분리할 수 있습니다.

   * **[!UICONTROL Do not update enumerations]**

      데이터베이스의 열거된 값 목록을 보강하지 않으려면 이 옵션을 선택합니다. 자세한 내용은 [열거형 관리](../../platform/using/managing-enumerations.md).

* **[!UICONTROL Variables]** 탭

   쿼리 편집기 및 계산된 필드에서 액세스할 작업과 연결된 변수를 정의할 수 있습니다. 변수를 만들려면 **[!UICONTROL Add]** 변수 편집기를 사용합니다.

   >[!IMPORTANT]
   >
   >다음 **[!UICONTROL Variables]** 탭은 워크플로우 유형 프로그래밍 용도로만 사용되며 전문가 사용자만 구성해야 합니다.

## 2단계 - 소스 파일 선택 {#step-2---source-file-selection}

소스 파일은 텍스트 형식(텍스트, csv, 탭, 고정 열)이나 xml일 수 있습니다.

기본적으로 **[!UICONTROL Upload file on the server]** 이 선택되어 있습니다. 오른쪽의 폴더를 클릭합니다 **[!UICONTROL Local file]** 필드를 선택하여 로컬 디스크를 찾고 가져올 파일을 선택합니다. 서버에 있는 경우 가져올 파일의 이름과 액세스 경로를 입력하려면 이 옵션을 선택 취소할 수 있습니다.

![](assets/s_ncs_user_import_wizard02_1.png)

파일이 지정된 경우 창의 아래 섹션에서 해당 데이터를 볼 수 있습니다 **[!UICONTROL Auto-detect format]**. 이 미리 보기는 소스 파일의 처음 200개 줄을 표시합니다.

![](assets/s_ncs_user_import_wizard02_2.png)

이 보기에서 위에 제공된 옵션을 사용하여 가져오기를 구성합니다. 이러한 옵션을 통해 정의된 매개 변수가 미리 보기로 전송됩니다. 다음 옵션을 사용할 수 있습니다.

* **[!UICONTROL Click here to change the file format...]** 파일 형식을 확인하고 구성을 세밀하게 조정할 수 있습니다.
* **[!UICONTROL Update on server...]** 로컬 파일을 서버에 전송할 수 있습니다. 이 옵션은 **[!UICONTROL Upload file on the server]** 이 선택되어 있습니다.
* **[!UICONTROL Download]** 는 파일이 서버에 업로드된 경우에만 사용할 수 있습니다.
* **[!UICONTROL Auto-detect format]** 는 데이터 소스의 형식을 다시 초기화하는 데 사용됩니다. 이 옵션을 사용하면 를 통해 형식이 지정된 데이터에 원래 형식을 다시 적용할 수 있습니다 **[!UICONTROL Click here to change the file format...]** 선택 사항입니다.
* 다음 **[!UICONTROL Advanced parameters]** 링크를 사용하면 소스 데이터를 필터링하고 고급 옵션에 액세스할 수 있습니다. 이 화면에서 파일의 일부만 가져오도록 선택할 수 있습니다. 필터를 정의하여 예를 들어 해당 라인의 값에 따라 &#39;Prospect&#39; 또는 &#39;Customer&#39; 유형 사용자만 가져올 수도 있습니다. 이러한 옵션은 전문 JavaScript 사용자만 사용해야 합니다.

### 파일 형식 변경 {#changing-the-file-format}

다음 **[!UICONTROL Click here to change the file format...]** 옵션을 사용하면 소스 파일의 데이터 형식을 지정할 수 있으며, 특히 각 필드에 대한 열 구분자와 데이터 유형을 지정할 수 있습니다. 이 구성은 다음 창을 통해 수행됩니다.

![](assets/s_ncs_user_import_wizard02_3.png)

이 단계에서는 파일 필드의 값을 읽는 방법을 설명합니다. 예를 들어, 날짜의 경우 날짜 또는 날짜 + 시간 데이터를 형식(dd/mm/yyyy, mm/dd/yy 등)과 연결할 수 있습니다. 입력 데이터가 예상 형식과 일치하지 않으면 가져오기 중에 거부가 발생합니다.

창 하단의 미리 보기 영역에서 구성 결과를 볼 수 있습니다.

클릭 **[!UICONTROL OK]** 서식을 저장하려면 **[!UICONTROL Next]** 을 눌러 다음 단계를 표시합니다.

## 3단계 - 필드 매핑 {#step-3---field-mapping}

그런 다음 대상 스키마를 선택하고 각 열의 데이터를 데이터베이스의 필드에 매핑해야 합니다.

![](assets/s_ncs_user_import_wizard03_1.png)

* 다음 **[!UICONTROL Destination schema]** 필드를 사용하면 데이터를 가져올 스키마를 선택할 수 있습니다. 이 정보는 필수입니다. 을(를) 클릭합니다. **[!UICONTROL Select link]** 기존 스키마 중 하나를 선택하는 아이콘. 클릭 **[!UICONTROL Edit link]** 을 눌러 선택한 테이블의 컨텐트를 표시합니다.
* 중앙 테이블에는 소스 파일에 정의된 모든 필드가 표시됩니다. 대상 파일을 가져오기 위해 가져올 필드를 선택합니다. 이러한 필드는 수동으로 또는 자동으로 매핑할 수 있습니다.

   필드를 수동으로 매핑하려면 확인란을 클릭하여 소스 필드를 선택하고 두 번째 열을 클릭하여 선택한 필드에 해당하는 셀을 활성화합니다. 그런 다음 **[!UICONTROL Edit expression]** 아이콘을 클릭하여 현재 테이블의 모든 필드를 표시합니다. 대상 필드를 선택하고 을(를) 클릭합니다 **[!UICONTROL OK]** 매핑의 유효성을 검사하려면

   소스 필드와 대상 필드를 자동으로 연결하려면 **[!UICONTROL Guess the destination fields]** 필드 목록 오른쪽에 있는 아이콘을 클릭합니다. 필요한 경우 제안된 필드를 수정할 수 있습니다.

   >[!IMPORTANT]
   >
   >다음 단계로 진행하기 전에 이 작업의 결과를 항상 검증해야 합니다.

* 가져온 필드에 변형을 적용할 수 있습니다. 이렇게 하려면 의 셀을 클릭합니다 **[!UICONTROL Transformation]** 해당 필드와 관련된 열에서 적용할 변형을 선택합니다.

   ![](assets/s_ncs_user_import_wizard03_2.png)

   >[!IMPORTANT]
   >
   >가져오기가 수행될 때 변환이 적용됩니다. 대상 필드에 대한 제한이 정의되어 있지만, 위의 예에서 @lastname 필드에서 이러한 제한 사항이 우선합니다.

* 중앙 테이블의 오른쪽에 있는 적절한 아이콘을 사용하여 계산된 필드를 추가할 수 있습니다. 계산된 필드를 사용하면 복잡한 변환을 수행하거나, 가상 열을 추가하거나, 여러 열의 데이터를 병합할 수 있습니다. 다양한 가능성에 대한 자세한 내용은 다음 섹션을 참조하십시오.

### 계산된 필드 {#calculated-fields}

계산된 필드는 소스 파일에 추가되고 다른 열에서 계산된 새 열입니다. 그런 다음 계산된 필드를 Adobe Campaign 데이터베이스의 필드와 연결할 수 있습니다. 그러나 계산된 필드에서는 조정 작업을 수행할 수 없습니다.

다음 네 가지 유형의 계산된 필드가 있습니다.

* **[!UICONTROL Fixed string]**: 계산된 필드의 값은 소스 파일의 모든 행에 대해 동일합니다. 삽입되거나 업데이트된 레코드의 필드 값을 설정할 수 있도록 해줍니다. 예를 들어 가져온 모든 레코드에 대해 마커를 &quot;예&quot;로 설정할 수 있습니다.
* **[!UICONTROL String with JavaScript tags]**: 계산된 필드의 값은 JavaScript 명령을 포함하는 문자열에서 사용할 수 있습니다.
* **[!UICONTROL JavaScript expression]**: 계산된 필드의 값은 JavaScript 함수를 평가한 결과입니다. 반환된 값은 숫자, 날짜 등이 될 수 있습니다.
* **[!UICONTROL Enumeration]**: 필드의 값은 소스 파일에 포함된 값에 따라 달라집니다. 편집기에서 소스 열을 지정하고 다음 예와 같이 열거형 값 목록을 입력할 수 있습니다.

   ![](assets/s_ncs_user_import_wizard03_3.png)

   다음 **[!UICONTROL Preview]** 탭에서는 정의된 구성의 결과를 볼 수 있습니다. 여기, **[!UICONTROL Subscription]** 열이 추가되었습니다. 값은 **상태** 필드.

   ![](assets/s_ncs_user_import_wizard03_4.png)

## 4단계 - 조정 {#step-4---reconciliation}

가져오기 마법사의 조정 단계에서는 파일의 데이터를 데이터베이스의 기존 데이터로 조정하는 모드를 정의하고 파일 데이터와 데이터베이스 데이터 간의 우선순위 규칙을 설정할 수 있습니다. 구성 창은 다음과 같습니다.

![](assets/s_ncs_user_import_wizard04_1.png)

화면의 중앙 섹션에는 데이터를 가져올 Adobe Campaign 데이터베이스의 테이블과 필드가 있는 트리가 포함되어 있습니다.

각 노드(테이블 또는 필드)에 대해 특수 옵션을 사용할 수 있습니다. 목록에서 관련 노드를 클릭하면 해당 매개 변수와 간단한 설명이 아래에 표시됩니다. 각 요소에 대해 정의된 동작이 해당 요소에 표시됩니다 **[!UICONTROL Behavior]** 열.

![](assets/s_ncs_user_import_wizard04_2.png)

### 작업 유형 {#types-of-operation}

가져오기에 관련된 각 테이블에 대해 작업 유형을 정의해야 합니다. 데이터베이스의 기본 요소에 사용할 수 있는 작업은 다음과 같습니다.

* **[!UICONTROL Update or insertion]**: 데이터베이스에 있는 경우 레코드를 업데이트하고 없는 경우 만듭니다.
* **[!UICONTROL Insertion]**: 데이터베이스에 레코드를 삽입합니다.
* **[!UICONTROL Update]**: 기존 레코드만 업데이트합니다(다른 레코드는 무시).
* **[!UICONTROL Reconciliation only]**: 데이터베이스에서 레코드를 찾지만 업데이트를 수행하지 않습니다. 예를 들어, 폴더의 데이터를 업데이트하지 않고 파일의 열에 따라 가져올 수신자 폴더를 연결할 수 있습니다.
* **[!UICONTROL Deletion]**: 데이터베이스의 레코드를 제거할 수 있습니다.

가져오기에 관련된 테이블의 각 필드에 대해 다음 옵션을 사용할 수 있습니다.

* **[!UICONTROL Update (empty) if source value is empty]**: 업데이트 시 소스 파일에서 필드가 비어 있으면 필드의 값이 데이터베이스 값을 제거합니다. 그렇지 않으면 데이터베이스 필드가 유지됩니다.
* **[!UICONTROL Update only if destination is empty]**: 데이터베이스 필드가 비어 있지 않으면 소스 파일의 값이 데이터베이스 필드의 값을 덮어쓰지 않습니다. 이 경우 소스 파일의 값을 사용합니다.
* **[!UICONTROL Update the field only when the record is inserted]**: 업데이트 또는 삽입 작업 중에는 새 소스 파일 레코드만 가져옵니다.

>[!NOTE]
>
>조정 키의 정의는 항상 다음과 같습니다 **필수**&#x200B;중복 제거 없이 삽입되는 경우를 제외하고 .

### 조정 키 {#reconciliation-keys}

중복 제거를 관리하려면 하나 이상의 조정 키를 채워야 합니다.

조정 키는 레코드를 식별하는 데 사용되는 필드 세트입니다. 예를 들어 수신자를 가져오기 위해 조정 키는 계정 번호, &quot;이메일&quot; 필드 또는 &quot;성, 이름, 회사&quot; 필드 등이 될 수 있습니다.

이 경우 파일의 줄이 데이터베이스의 기존 수신자와 일치하는지 확인하기 위해 가져오기 엔진은 파일의 값과 키의 모든 필드에 대한 데이터베이스 값을 비교합니다. 레코드에 대한 필드인 경우 소스 데이터와 대상 데이터 간의 미세 비교를 수행할 수 있으므로 가져오기 후 데이터의 무결성을 보장합니다. 동일한 테이블에 대해 두 번째 조정 키를 입력할 수 있습니다. 첫 번째 키가 비어 있는 행에 사용됩니다.

가져오는 동안 수정할 수 있는 필드를 선택하지 마십시오. 이 경우 엔진은 추가 레코드를 만들 수 있습니다.

![](assets/s_ncs_user_import_wizard04_3.png)

>[!NOTE]
>
>수신자 가져오기의 경우 선택한 폴더의 식별자가 키에 암묵적으로 추가됩니다.
>
>따라서 이 폴더에서만 조정이 수행됩니다(폴더를 선택하지 않은 경우).

### 중복 제거 {#deduplication}

>[!NOTE]
>
>double은 가져올 파일에 두 번 이상 존재하는 항목입니다.
>
>&#39;duplicate&#39;는 가져올 파일과 데이터베이스에 모두 있는 항목입니다.

다음 **[!UICONTROL Management of doubles]** 필드에서는 데이터 중복 제거를 구성할 수 있습니다. 중복 제거는 여러 번 나타나는 기록 **소스 파일에서** (또는 여러 파일 가져오기의 경우 소스 파일), 즉 조정 키의 필드가 동일한 줄.

* 의 중복 관리 **[!UICONTROL Update]** 모드(기본 모드)에서는 중복 제거를 수행하지 않습니다. 따라서 마지막 레코드에는 우선 순위가 있습니다(이전 레코드의 데이터를 업데이트하므로). 이 모드에서는 중복 카운트가 수행되지 않습니다.
* 의 중복 관리 **[!UICONTROL Ignore]** 모드 또는 **[!UICONTROL Reject entity]** 가져오기에서 중복을 제외합니다. 이 경우 레코드를 가져오지 않습니다.
* in **[!UICONTROL Reject entity]** 모드에서는 요소를 가져오지 않고 가져오기 로그에 오류가 생성됩니다.
* in **[!UICONTROL Ignore]** 모드에서는 요소를 가져올 수 없지만 오류 추적은 유지되지 않습니다. 이 모드에서는 성능을 최적화할 수 있습니다.

>[!IMPORTANT]
>
>중복 제거는 메모리에서만 수행됩니다. 따라서 중복 제거가 포함된 가져오기의 크기가 제한됩니다. 제한은 몇 가지 매개 변수(애플리케이션 서버의 용량, 활동, 키의 필드 수 등)에 따라 다릅니다. 중복 제거의 최대 크기는 1,000,000개 라인의 수입니다.

데이터 중복 제거는 소스 파일과 데이터베이스에 모두 있는 레코드입니다. 업데이트 전용(즉, **[!UICONTROL Update and insertion]** 또는 **[!UICONTROL Update]**). 다음 **[!UICONTROL Duplicate management]** 옵션을 사용하면 소스 파일과 데이터베이스에 있는 레코드를 업데이트하거나 무시할 수 있습니다. 다음 **[!UICONTROL Update or insert based on origin]** 옵션은 선택적 모듈에 속하며 표준 컨텍스트에서 사용할 수 없습니다.

옵션 **[!UICONTROL Reject]** 및 **[!UICONTROL Ignore]** 위에서 설명한 대로 작동합니다.

### 오류가 있는 경우 {#behavior-in-the-event-of-an-error}

대부분의 데이터 전송 작업은 다양한 유형의 오류(일관성 없는 라인 형식, 잘못된 이메일 주소 등)를 생성합니다. 가져오기 엔진에서 생성된 모든 오류와 경고는 저장되고 가져오기 인스턴스에 연결됩니다.

![](assets/s_ncs_user_import_general_tab.png)

이러한 거부에 대한 세부 사항은 **[!UICONTROL Rejects]** 탭.

![](assets/s_ncs_user_import_rejets_tab.png)

거부의 유형은 다음 두 가지 유형이 있습니다. **[!UICONTROL Connector]** column):

* 텍스트 커넥터의 거부는 파일 줄을 처리하는 동안 발생하는 오류(계산된 필드, 데이터 분석 등)와 관련되어 있습니다. 이 경우 오류가 발생하면 전체 줄이 항상 거부됩니다.
* 데이터베이스 커넥터 거부는 데이터 조정 또는 데이터베이스에 쓰는 동안 발생하는 오류를 처리합니다. 여러 테이블로 가져오는 경우, 거부에는 레코드의 일부만 걱정될 수 있습니다(예: 수신자 및 관련 이벤트 가져오기의 경우, 수신자를 거부하지 않고 이벤트 업데이트를 방지할 수 있음).

데이터 조정 페이지에서 원하는 오류 관리 유형 필드를 필드 및 테이블별로 정의할 수 있습니다.

* **[!UICONTROL Ignore and log a warning]**: 오류를 생성한 필드를 제외한 모든 필드를 데이터베이스로 가져옵니다.
* **[!UICONTROL Reject parent element]**: 오류가 발생한 필드뿐만 아니라 레코드의 전체 줄을 거부합니다.
* **[!UICONTROL Reject all elements]**: 가져오기가 중지되고 레코드의 모든 요소가 거부됩니다.

   ![](assets/s_ncs_user_import_wizard04_4.png)

가져오기 인스턴스의 거부 화면에 있는 트리는 거부된 필드와 오류가 발생한 위치를 나타냅니다.

를 통해 이러한 레코드가 포함된 파일을 생성할 수 있습니다. **[!UICONTROL Export rejects]** 아이콘:

![](assets/s_ncs_user_import_errors_export.png)

## 5단계 - 수신자를 가져올 때의 추가 단계 {#step-5---additional-step-when-importing-recipients}

가져오기 마법사의 다음 단계에서는 데이터를 가져올 폴더를 선택하거나 만들고 가져온 수신자를 (신규 또는 기존) 목록으로 자동 매핑하고 수신자를 서비스에 가입할 수 있습니다.

![](assets/s_ncs_user_import_wizard05_1.png)

>[!NOTE]
>
>이 단계는 수신자를 가져올 때만 그리고 기본 Adobe Campaign 수신자 테이블(**nms:recipient**).

* 을(를) 클릭합니다. **[!UICONTROL Edit]** 수신자를 연결하거나 구독할 폴더, 목록 또는 서비스를 선택하는 링크입니다.

   1. 폴더로 가져오기

      다음 **[!UICONTROL Edit...]** 링크 **[!UICONTROL Import into a folder]** 섹션에서 수신자를 가져올 폴더를 선택하거나 만들 수 있습니다. 기본적으로 정의된 파티션이 없으면 데이터를 연산자의 기본 폴더로 가져옵니다.

      >[!NOTE]
      >
      >연산자의 기본 폴더는 연산자가 쓰기 액세스 권한을 갖는 첫 번째 폴더입니다. 추가 정보 [폴더 액세스 관리](../../platform/using/access-management-folders.md).

      가져오기 폴더를 선택하려면 오른쪽 화살표를 클릭합니다 **[!UICONTROL Folder]** 필드를 입력하고 관련 폴더를 선택합니다. 를 사용할 수도 있습니다 **[!UICONTROL Select link]** 아이콘을 클릭하여 새 창에 트리를 표시하거나 새 폴더를 만듭니다.

      ![](assets/s_ncs_user_import_wizard05_2.png)

      새 폴더를 만들려면 폴더를 추가할 노드를 선택하고 마우스 오른쪽 버튼을 클릭합니다. **[!UICONTROL Create a new 'Recipients' folder]**&#x200B;을(를) 선택합니다.

      ![](assets/s_ncs_user_import_wizard05_3.png)

      폴더는 현재 노드 아래에 추가됩니다. 새 폴더의 이름을 입력하고 Enter 키를 눌러 확인한 다음 를 클릭합니다 **[!UICONTROL OK]**.

      ![](assets/s_ncs_user_import_wizard05_4.png)

   1. 목록과 연결

      다음 **[!UICONTROL Edit...]** 링크 위치 **[!UICONTROL Add recipients to a list]** 섹션에서 수신자를 가져올 목록을 선택하거나 만들 수 있습니다.

      ![](assets/s_ncs_user_import_wizard05_5.png)

      을(를) 클릭하여 이러한 수신자에 대한 새 목록을 만들 수 있습니다 **[!UICONTROL Select link]**, 그런 다음 **[!UICONTROL Create]**. 목록 작성 및 관리는 [이 섹션](../../platform/using/creating-and-managing-lists.md).

      ![](assets/s_ncs_user_import_wizard05_6.png)

      목록에 이미 있는 수신자에 수신자를 추가하거나 새 수신자와 함께 목록을 다시 작성하도록 결정할 수 있습니다. 이 경우 목록에 이미 수신자가 포함되어 있으면 해당 수신자는 삭제되고 가져온 수신자로 대체됩니다.

   1. 서비스 가입

      가져온 모든 수신자를 정보 서비스에 가입하려면 **[!UICONTROL Edit...]** 링크 **[!UICONTROL Subscribe recipients to a service]** 섹션을 추가하여 수신자를 구독할 정보 서비스를 선택하거나 만듭니다. 을(를) 선택할 수 있습니다 **[!UICONTROL Send a confirmation message]** 옵션: 이 메시지의 콘텐츠는 구독 서비스와 연결된 게재 템플릿에서 정의됩니다.

      ![](assets/s_ncs_user_import_wizard05_7.png)

      을(를) 클릭하여 이러한 수신자를 위한 새 서비스를 만들 수 있습니다 **[!UICONTROL Select link]** 그리고 **[!UICONTROL Create]** 아이콘. 정보 서비스 관리는 [이 섹션](../../delivery/using/managing-subscriptions.md).

* 를 사용하십시오 **[!UICONTROL Origin]** 필드를 사용하여 수신자의 위치에 대한 정보를 프로필에 추가합니다. 이 정보는 여러 가져오기의 프레임워크 내에서 특히 유용합니다.

클릭 **[!UICONTROL Next]** 이 단계의 유효성을 확인하고 다음 단계를 표시합니다.

## 6단계 - 가져오기 시작 {#step-6---launching-the-import}

마법사의 마지막 단계에서 데이터 가져오기를 시작할 수 있습니다. 이렇게 하려면 **[!UICONTROL Start]** 버튼을 클릭합니다.

![](assets/s_ncs_user_import_wizard06_1.png)

그런 다음 가져오기 작업의 실행을 모니터링할 수 있습니다( [작업 실행 모니터링](../../platform/using/monitoring-jobs-execution.md).
