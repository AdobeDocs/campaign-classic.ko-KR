---
product: campaign
title: 일반 가져오기 샘플
description: 가져오기 작업을 사용하여 수행할 수 있는 일반 가져오기에 대해 자세히 알아보십시오.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 4582b524-2b6d-484c-bace-29d2e69f60e9
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '995'
ht-degree: 1%

---

# 일반 가져오기 샘플 {#import-operations-samples}

## 수신자 목록 {#example--import-from-a-list-of-recipients}에서 가져오기

목록 개요에서 수신자 목록을 만들고 제공하려면 다음 단계를 수행합니다.

1. 목록 만들기

   * Adobe Campaign 홈 페이지의 **[!UICONTROL Profiles and targets]** 메뉴에서 **[!UICONTROL Lists]** 링크를 클릭합니다.
   * **[!UICONTROL Create]** 을 클릭한 다음 **[!UICONTROL Import a list]** 버튼을 클릭합니다.

1. 가져올 파일 선택

   **[!UICONTROL Local file]** 필드 오른쪽의 폴더를 클릭하고 가져올 목록이 포함된 파일을 선택합니다.

   ![](assets/s_ncs_user_import_example00_01.png)

1. 목록 이름 및 저장소

   목록의 이름을 입력하고 저장할 디렉토리를 선택합니다.

   ![](assets/s_ncs_user_import_example00_02.png)

1. 가져오기 시작

   **[!UICONTROL Next]** 을 클릭한 다음 **[!UICONTROL Start]** 을 클릭하여 목록 가져오기를 시작합니다.

   ![](assets/s_ncs_user_import_example00_03.png)

## 텍스트 파일 {#example--import-new-records-from-a-text-file-}에서 새 레코드 가져오기

텍스트 파일에 저장된 새 수신자 프로필을 Adobe Campaign 데이터베이스로 가져오려면 다음 단계를 수행하십시오.

1. 템플릿 선택

   * Adobe Campaign 홈 페이지에서 **[!UICONTROL Profiles and targets]** 링크를 클릭한 다음 **[!UICONTROL Jobs]** 을 클릭합니다. 작업 목록 위에서 **[!UICONTROL New import]** 을 클릭합니다.
   * 기본적으로 선택한 **[!UICONTROL New text import]** 템플릿을 유지합니다.
   * 레이블 및 설명을 변경합니다.
   * **[!UICONTROL Simple import]**&#x200B;을(를) 선택합니다.
   * 기본 작업 폴더를 유지합니다.
   * **[!UICONTROL Advanced parameters]** 을 클릭하고 **[!UICONTROL Tracking mode]** 옵션을 선택하여 실행 중에 가져오기의 세부 정보를 확인합니다.

1. 가져올 파일 선택

   **[!UICONTROL Local file]** 필드 오른쪽의 폴더를 클릭하고 가져올 파일을 선택합니다.

   ![](assets/s_ncs_user_import_example01_01.png)

1. 필드 연결

   소스 및 대상 스키마를 자동으로 매핑하려면 **[!UICONTROL Guess the destination fields]** 아이콘을 클릭하십시오. **[!UICONTROL Next]**&#x200B;을 클릭하기 전에 이 창의 정보를 확인하십시오.

   ![](assets/s_ncs_user_import_example03_01.png)

1. 조정

   * **수신자(nms:recipient)** 테이블로 이동합니다.
   * **[!UICONTROL Insertion]** 작업을 선택하고 다른 필드에 기본값을 둡니다.

      ![](assets/s_ncs_user_import_example04_01.png)

1. 수신자 가져오기

   * 필요한 경우 가져올 레코드의 폴더를 지정합니다.

      ![](assets/s_ncs_user_import_example05_01.png)

1. 가져오기 시작

   * **[!UICONTROL Start]**&#x200B;을(를) 클릭합니다.

      편집기의 중앙 영역에서 가져오기 작업이 성공했는지 확인하고 처리된 레코드 수를 볼 수 있습니다.

      ![](assets/s_ncs_user_import_example06_01.png)

      **[!UICONTROL Tracking]** 모드에서는 소스 파일의 각 레코드에 대한 가져오기 세부 정보를 추적할 수 있습니다. 이렇게 하려면 홈 페이지에서 **[!UICONTROL Profiles and Targets]** 을 클릭하고 **[!UICONTROL Processes]** 를 클릭한 다음 관련 가져오기를 선택하고 **[!UICONTROL General]**, **[!UICONTROL Journal]** 및 **[!UICONTROL Rejects]** 탭을 찾습니다.

      * 가져오기 진행 상태 확인

         ![](assets/s_ncs_user_import_example07_01.png)

      * 각 레코드에 대한 프로세스 보기

         ![](assets/s_ncs_user_import_example07_02.png)

## 수신자 업데이트 및 삽입 {#example--update-and-insert-recipients}

데이터베이스의 기존 레코드를 업데이트하고 텍스트 파일에서 새 레코드를 만들려고 합니다. 다음은 절차의 예입니다.

1. 템플릿 선택

   위의 예제 2에 설명된 단계를 반복합니다.

1. 가져올 파일

   가져올 파일을 선택합니다.

   이 예제에서 파일의 첫 번째 행에 대한 개요는 파일에 세 개의 레코드 및 레코드 작성에 대한 업데이트가 포함되어 있음을 보여줍니다.

   ![](assets/s_ncs_user_import_example02_02.png)

1. 필드 연결

   위의 예 2에서 절차를 적용합니다.

1. 조정

   * 기본적으로 **[!UICONTROL Update or insert]** 을(를) 선택한 상태로 유지합니다.
   * 데이터베이스의 기존 레코드가 텍스트 파일의 데이터로 수정되도록 **[!UICONTROL Update]** 모드에서 **[!UICONTROL Management of duplicates]** 옵션을 유지합니다.
   * 필드 **[!UICONTROL Birth date]**, **[!UICONTROL Name]** 및 **[!UICONTROL Company]**&#x200B;를 선택하고 필드에 조정 키를 할당합니다.

      ![](assets/s_ncs_user_import_example04_02.png)

1. 가져오기 시작

   * **[!UICONTROL Start]**&#x200B;을(를) 클릭합니다.

      추적 창에서 가져오기에 성공했는지 확인하고 처리된 레코드 수를 볼 수 있습니다.

      ![](assets/s_ncs_user_import_example06_02.png)

   * 받는 사람 테이블을 검색하여 이 작업에서 레코드가 수정되었는지 확인합니다.

      ![](assets/s_ncs_user_import_example06_03.png)

## 외부 파일 {#example--enrich-the-values-with-those-of-an-external-file}의 값으로 값을 보강합니다.

데이터베이스 테이블의 특정 필드를 텍스트 파일에서 수정하여 데이터베이스에 포함된 값에 우선 순위를 두려고 합니다.

이 예제에서는 텍스트 파일의 특정 필드에 값이 있는 반면 데이터베이스의 해당 필드는 비어 있는 것을 확인할 수 있습니다. 다른 필드에는 데이터베이스에 포함된 필드와 다른 값이 포함되어 있습니다.

* 가져올 텍스트 파일의 컨텐츠입니다.

   ![](assets/s_ncs_user_import_example02_03.png)

* 가져오기 전 데이터베이스 상태

   ![](assets/s_ncs_user_import_example06_04.png)

다음 단계를 적용합니다.

1. 템플릿 선택

   위의 예 2에서 절차를 적용합니다.

1. 가져올 파일

   가져올 파일을 선택합니다.

1. 필드 연결

   위의 예 2에서 절차를 적용합니다.

   파일의 첫 번째 줄 미리 보기에서 파일에 특정 레코드에 대한 업데이트가 포함되어 있음을 확인할 수 있습니다.

1. 조정

   * 테이블로 이동하여 **[!UICONTROL Update]** 작업을 선택합니다.
   * **[!UICONTROL Management of doubles]** 필드에 대해 **[!UICONTROL Reject entity]** 옵션을 선택합니다.
   * 데이터베이스의 기존 레코드가 텍스트 파일의 데이터로 수정되도록 **[!UICONTROL Update]** 모드에서 **[!UICONTROL Management of duplicates]** 옵션을 유지합니다.
   * **[!UICONTROL Last name (@lastName)]** 노드에 커서를 놓고 **[!UICONTROL Update only if destination is empty]** 옵션을 선택합니다.
   * **[!UICONTROL Company (@company)]** 노드에 대해 이 작업을 반복합니다.
   * **[!UICONTROL Birth date]**, **[!UICONTROL E-mail]** 및 **[!UICONTROL First name]** 필드에 조정 키를 할당합니다.

      ![](assets/s_ncs_user_import_example04_03.png)

1. 가져오기 시작

   **[!UICONTROL Start]**&#x200B;을(를) 클릭합니다.

   받는 사람 테이블을 검색하여 가져오기로 레코드가 수정되었는지 확인합니다.

   ![](assets/s_ncs_user_import_example06_05.png)

   비어 있는 값만 텍스트 파일의 값으로 대체되었지만 데이터베이스의 기존 값을 가져오기 파일의 값으로 덮어쓰지 않았습니다.

## 외부 파일 {#example--update-and-enrich-the-values-from-those-in-an-external-file}의 값을 업데이트하고 보강합니다.

텍스트 파일에서 데이터베이스 테이블의 특정 필드를 수정하여 텍스트 파일에 포함된 값에 우선 순위를 두려고 합니다.

이 예제에서는 텍스트 파일의 특정 필드에 빈 값이 있는 반면 데이터베이스의 해당 필드는 비어 있지 않습니다. 다른 필드에는 데이터베이스의 값과 다른 값이 포함됩니다.

* 가져올 텍스트 파일의 컨텐츠입니다.

   ![](assets/s_ncs_user_import_example02_04.png)

* 가져오기 전 데이터베이스 상태

   ![](assets/s_ncs_user_import_example06_07.png)

1. 템플릿 선택

   위의 예 2에서 절차를 적용합니다.

1. 가져올 파일

   가져올 파일을 선택합니다.

   파일의 첫 번째 줄 미리 보기에서 파일에 특정 레코드에 대한 빈 필드와 업데이트가 포함되어 있음을 알 수 있습니다.

1. 필드 연결

   위의 예 2에서 절차를 적용합니다.

1. 조정

   * 테이블로 이동하고 **[!UICONTROL Update]** 을 선택합니다.
   * **[!UICONTROL Management of doubles]** 필드에 대해 **[!UICONTROL Reject entity]** 옵션을 선택합니다.
   * 데이터베이스의 기존 레코드가 텍스트 파일의 데이터로 수정되도록 하려면 **[!UICONTROL Update]** 모드에서 **[!UICONTROL Management of duplicates]** 옵션을 둡니다.
   * **[!UICONTROL Account number (@account)]** 노드에 커서를 놓고 **[!UICONTROL Take empty values into account]** 옵션을 선택합니다.
   * 필드 **[!UICONTROL Birth date]**, **[!UICONTROL E-mail]** 및 **[!UICONTROL First name]**&#x200B;를 선택하고 필드에 조정 키를 할당합니다.

      ![](assets/s_ncs_user_import_example04_04.png)

1. 가져오기 시작

   * **[!UICONTROL Start]**&#x200B;을(를) 클릭합니다.
   * 받는 사람 테이블을 검색하여 작업이 레코드를 수정했는지 확인합니다.

      ![](assets/s_ncs_user_import_example06_06.png)

      비어 있는 텍스트 파일의 값이 데이터베이스의 값을 덮어씁니다. 데이터베이스의 기존 값이 4단계에서 중복에 대해 선택한 **[!UICONTROL Update]** 옵션을 사용하여 가져오기 파일의 값으로 업데이트되었습니다.
