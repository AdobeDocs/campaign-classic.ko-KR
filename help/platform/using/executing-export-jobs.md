---
product: campaign
title: 내보내기 작업 구성
description: Campaign에서 내보내기 작업을 구성하고 실행하는 방법 알아보기
feature: Overview
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 94fc473a-dc49-41e8-b572-51c162b09996
source-git-commit: 9df46ed923831ffdfb28acddfbc371cecafb251c
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 2%

---

# 내보내기 작업 구성 {#executing-export-jobs}



내보내기 작업을 사용하면 연락처, 클라이언트, 목록, 세그먼트 등 데이터베이스에서 데이터를 액세스하고 추출할 수 있습니다.

예를 들어 스프레드시트에서 캠페인 추적 데이터(추적 내역 등)를 사용하는 것이 유용할 수 있습니다. 출력 데이터는 txt, CSV, TAB 또는 XML 형식일 수 있습니다.

내보내기 도우미를 사용하여 내보내기를 구성하고, 해당 옵션을 정의하고, 실행을 시작할 수 있습니다. 수출의 유형(단순 또는 복수)과 운영자의 권리에 따라 그 내용이 달라지는 일련의 화면이다.

내보내기 도우미는 새 내보내기 작업을 만든 후에 표시됩니다([가져오기 및 내보내기 작업 만들기](../../platform/using/creating-import-export-jobs.md) 참조).

## 1단계 - 내보내기 템플릿 선택 {#step-1---choosing-the-export-template}

내보내기 도우미를 시작할 때 먼저 템플릿을 선택해야 합니다. 예를 들어 최근에 등록한 수신자의 내보내기를 구성하려면 아래 단계를 수행합니다.

1. **[!UICONTROL Profiles and Targets > Job > Generic imports and exports]** 폴더를 선택하십시오.
1. **새로 만들기**&#x200B;를 클릭한 다음 **내보내기**&#x200B;를 클릭하여 내보내기 템플릿을 만듭니다.

   ![](assets/s_ncs_user_export_wizard01.png)

1. **[!UICONTROL Export template]** 필드 오른쪽에 있는 화살표를 클릭하여 템플릿을 선택하거나 **[!UICONTROL Select link]**&#x200B;을(를) 클릭하여 트리를 찾습니다.

   기본 서식 파일은 **[!UICONTROL New text export]**&#x200B;입니다. 이 템플릿은 수정해서는 안 되지만, 복제하여 새 템플릿을 구성할 수 있습니다. 기본적으로 내보내기 템플릿은 **[!UICONTROL Resources > Templates > Job templates]** 노드에 저장됩니다.

1. **[!UICONTROL Label]** 필드에 내보낼 이름을 입력합니다. 설명을 추가할 수 있습니다.
1. 내보내기 유형을 선택합니다. 내보내기 유형에는 두 가지가 있습니다. 하나 이상의 원본 문서 유형에서 한 개의 파일만 내보내는 **[!UICONTROL Simple export]**&#x200B;과(와) 한 번의 실행으로 여러 개의 파일을 내보내는 **[!UICONTROL Multiple export]**&#x200B;이(가) 있습니다.

## 2단계 - 내보낼 파일 유형 {#step-2---type-of-file-to-export}

내보낼 문서 유형(예: 내보낼 데이터의 스키마)을 선택합니다.

기본적으로 **[!UICONTROL Jobs]** 노드에서 내보내기가 시작되면 데이터가 받는 사람 테이블에서 가져옵니다. **[!UICONTROL right click > Export]** 메뉴의 데이터 목록에서 내보내기를 시작하면 데이터가 속한 테이블이 **[!UICONTROL Document type]** 필드에 자동으로 채워집니다.

![](assets/s_ncs_user_export_wizard02.png)

* 기본적으로 **[!UICONTROL Download the file generated on the server after the export]** 옵션이 선택되어 있습니다. **[!UICONTROL Local file]** 필드에서 만들 파일의 이름과 경로를 입력하거나 필드 오른쪽의 폴더를 클릭하여 로컬 디스크를 찾습니다. 이 옵션을 선택 해제하여 서버 출력 파일의 액세스 경로와 이름을 입력할 수 있습니다.

  >[!NOTE]
  >
  >자동 가져오기 및 내보내기 작업은 항상 서버에서 수행됩니다.
  >
  >일부 데이터만 내보내려면 **[!UICONTROL Advanced parameters]**&#x200B;을(를) 클릭하고 적절한 필드에 내보낼 줄 수를 입력합니다.

* 차등 내보내기를 만들어 마지막 실행 이후 수정된 레코드만 내보낼 수 있습니다. 이렇게 하려면 **[!UICONTROL Advanced parameters]** 링크를 클릭한 다음 **[!UICONTROL Differential export]** 탭을 클릭하고 **[!UICONTROL Activate differential export]**&#x200B;을(를) 선택합니다.

  ![](assets/s_ncs_user_export_wizard02_b.png)

  마지막으로 수정한 날짜를 입력해야 합니다. 필드 또는 계산에서 검색할 수 있습니다.

## 3단계 - 출력 형식 정의 {#step-3---defining-the-output-format}

내보내기 파일의 출력 형식을 선택합니다. 텍스트, 고정 열 텍스트, CSV 및 XML 형식을 사용할 수 있습니다.

![](assets/s_ncs_user_export_wizard03.png)

* **[!UICONTROL Text]** 형식의 경우 구분 기호를 선택하여 열(탭, 쉼표, 세미콜론 또는 사용자 지정)과 문자열(작은 따옴표 또는 큰따옴표 또는 없음)을 구분합니다.
* **[!UICONTROL text]** 및 **[!UICONTROL CSV]**&#x200B;의 경우 **[!UICONTROL Use first lines as column titles]** 옵션을 선택할 수 있습니다.
* 날짜 형식과 숫자 형식을 나타냅니다. 이렇게 하려면 관련 필드의 **[!UICONTROL Edit]** 단추를 클릭하고 편집기를 사용합니다.
* 열거형 값이 포함된 필드의 경우 **[!UICONTROL Export labels instead of internal values of enumerations]**&#x200B;을(를) 선택할 수 있습니다. 예를 들어 제목은 **1=Mr 형식으로 저장할 수 있습니다.**, **2=Miss**, **3=Mrs.**. 이 옵션을 선택하면 **Mr**, **Miss** 및 **Mrs**&#x200B;을(를) 내보냅니다.

## 4단계 - 데이터 선택 {#step-4---data-selection}

내보낼 필드를 선택합니다. 방법은 다음과 같습니다.

1. **[!UICONTROL Available fields]** 목록에서 원하는 필드를 두 번 클릭하여 **[!UICONTROL Output columns]** 섹션에 추가합니다.
1. 목록 오른쪽에 있는 화살표를 사용하여 출력 파일의 필드 순서를 정의합니다.

   ![](assets/s_ncs_user_export_wizard04.png)

1. 함수를 호출하려면 **[!UICONTROL Add]** 단추를 클릭하십시오. 자세한 내용은 [함수 목록](../../platform/using/about-queries-in-campaign.md)을 참조하세요.

## 5단계 - 열 정렬 {#step-5---sorting-columns}

열의 정렬 순서를 선택합니다.

![](assets/s_ncs_user_export_wizard05.png)

## 6단계 - 조건 필터링 {#step-6---filter-conditions-}

모든 데이터를 내보내지 않도록 필터 조건을 추가할 수 있습니다. 이 필터링의 구성은 게재 도우미에서 수신자 타겟팅과 동일합니다. [이 페이지](../../delivery/using/steps-defining-the-target-population.md)를 참조하십시오.

![](assets/s_ncs_user_export_wizard05_b.png)

## 7단계 - 데이터 서식 {#step-7---data-formatting}

출력 파일에 대한 필드의 순서와 레이블을 수정하고 소스 데이터에 변환을 적용할 수 있습니다.

* 내보낼 열의 순서를 변경하려면 관련 열을 선택하고 테이블 오른쪽에 있는 파란색 화살표를 사용합니다.
* 필드의 레이블을 변경하려면 수정할 필드와 일치하는 **[!UICONTROL Label]** 열의 셀을 클릭하고 새 레이블을 입력합니다. 확인하려면 키보드에서 Enter 키를 누릅니다.
* 필드의 내용에 대/소문자 변환을 적용하려면 **[!UICONTROL Transformation]** 열에서 선택합니다. 다음을 선택할 수 있습니다.

   * 소문자로 전환
   * 대문자로 전환
   * 첫 글자를 대문자로

  ![](assets/s_ncs_user_export_wizard06.png)

* 새 계산 필드(예: 성 + 이름이 포함된 열)를 만들려면 **[!UICONTROL Add a calculated field]**&#x200B;을(를) 클릭합니다. 자세한 내용은 [계산된 필드](../../platform/using/executing-import-jobs.md#calculated-fields)를 참조하세요.

요소 컬렉션(예: 수신자의 구독, 요소가 속한 목록 등)을 내보내는 경우 내보낼 컬렉션의 요소 수를 지정해야 합니다.

![](assets/s_ncs_user_export_wizard06_c.png)

## 8단계 - 데이터 미리보기 {#step-8---data-preview}

내보내기 결과를 미리 보려면 **[!UICONTROL Start the preview of the data]**&#x200B;을(를) 클릭합니다. 기본적으로 처음 200개의 줄이 표시됩니다. 이 값을 변경하려면 **[!UICONTROL Lines to display]** 필드 오른쪽에 있는 화살표를 클릭합니다.

![](assets/s_ncs_user_export_wizard07.png)

열 결과 미리 보기에서 XML로 전환하려면 길잡이 아래쪽에 있는 탭을 클릭합니다. 생성된 SQL 쿼리를 볼 수도 있습니다.

## 9단계 - 내보내기 시작 {#step-9---launching-the-export}

데이터 내보내기를 시작하려면 **[!UICONTROL Start]**&#x200B;을(를) 클릭하십시오.

![](assets/s_ncs_user_export_wizard08.png)

그런 다음 가져오기 작업의 실행을 모니터링할 수 있습니다([작업 실행 모니터링](../../platform/using/monitoring-jobs-execution.md) 참조).
