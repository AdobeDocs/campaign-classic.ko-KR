---
solution: Campaign Classic
product: campaign
title: 일반 가져오기 샘플
description: 가져오기 작업을 사용하여 수행할 수 있는 일반 가져오기에 대해 자세히 알아보십시오.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: 37cc6cd8b71ec82cd4e6a910d6664a51ed5c091e
workflow-type: tm+mt
source-wordcount: '995'
ht-degree: 0%

---


# 일반 가져오기 샘플 {#import-operations-samples}

## 받는 사람 목록에서 가져오기 {#example--import-from-a-list-of-recipients}

목록 개요에서 받는 사람 목록을 만들고 제공하려면 다음 단계를 적용합니다.

1. 목록 만들기

   * Adobe Campaign 홈 페이지의 **[!UICONTROL Profiles and targets]** 메뉴에서 **[!UICONTROL Lists]** 링크를 클릭합니다.
   * **[!UICONTROL Create]**&#x200B;을 클릭한 다음 **[!UICONTROL Import a list]** 단추를 클릭합니다.

1. 가져올 파일 선택

   **[!UICONTROL Local file]** 필드 오른쪽에 있는 폴더를 클릭하고 가져올 목록이 포함된 파일을 선택합니다.

   ![](assets/s_ncs_user_import_example00_01.png)

1. 목록 이름 및 저장소

   목록 이름을 입력하고 저장할 디렉토리를 선택합니다.

   ![](assets/s_ncs_user_import_example00_02.png)

1. 가져오기 시작

   **[!UICONTROL Next]**&#x200B;을 클릭한 다음 **[!UICONTROL Start]**&#x200B;을 클릭하여 목록 가져오기를 시작합니다.

   ![](assets/s_ncs_user_import_example00_03.png)

## 텍스트 파일 {#example--import-new-records-from-a-text-file-}에서 새 레코드 가져오기

텍스트 파일에 저장된 새 수신자 프로필을 Adobe Campaign 데이터베이스로 가져오려면 다음 단계를 적용합니다.

1. 템플릿 선택

   * Adobe Campaign 홈 페이지에서 **[!UICONTROL Profiles and targets]** 링크를 클릭한 다음 **[!UICONTROL Jobs]** 작업 목록 위에서 **[!UICONTROL New import]**&#x200B;을 클릭합니다.
   * 기본적으로 **[!UICONTROL New text import]** 템플릿을 선택된 상태로 유지합니다.
   * 레이블 및 설명을 변경합니다.
   * **[!UICONTROL Simple import]**&#x200B;을(를) 선택합니다.
   * 기본 작업 폴더를 유지합니다.
   * **[!UICONTROL Advanced parameters]**&#x200B;을 클릭하고 **[!UICONTROL Tracking mode]** 옵션을 선택하여 실행 중 가져오기에 대한 세부 정보를 봅니다.

1. 가져올 파일 선택

   **[!UICONTROL Local file]** 필드 오른쪽에 있는 폴더를 클릭하고 가져올 파일을 선택합니다.

   ![](assets/s_ncs_user_import_example01_01.png)

1. 필드 연결

   소스 및 대상 스키마를 자동으로 매핑하려면 **[!UICONTROL Guess the destination fields]** 아이콘을 클릭합니다. **[!UICONTROL Next]**&#x200B;을(를) 클릭하기 전에 이 창의 정보를 확인하십시오.

   ![](assets/s_ncs_user_import_example03_01.png)

1. 조정

   * **수신자(nms:recipient)** 테이블로 이동합니다.
   * **[!UICONTROL Insertion]** 작업을 선택하고 다른 필드에 기본값을 그대로 둡니다.

      ![](assets/s_ncs_user_import_example04_01.png)

1. 받는 사람 가져오기

   * 필요한 경우 레코드를 가져올 폴더를 지정합니다.

      ![](assets/s_ncs_user_import_example05_01.png)

1. 가져오기 시작

   * **[!UICONTROL Start]**&#x200B;을(를) 클릭합니다.

      편집기의 중앙 영역에서 가져오기 작업이 성공했는지 확인하고 처리된 레코드 수를 볼 수 있습니다.

      ![](assets/s_ncs_user_import_example06_01.png)

      **[!UICONTROL Tracking]** 모드에서는 소스 파일의 각 레코드에 대한 가져오기 세부 사항을 추적할 수 있습니다. 이렇게 하려면 홈 페이지에서 **[!UICONTROL Profiles and Targets]**, **[!UICONTROL Processes]**&#x200B;을 클릭한 다음 관련 가져오기를 선택하고 **[!UICONTROL General]**, **[!UICONTROL Journal]** 및 **[!UICONTROL Rejects]** 탭을 찾습니다.

      * 가져오기 진행 상태 확인

         ![](assets/s_ncs_user_import_example07_01.png)

      * 각 레코드에 대한 프로세스 보기

         ![](assets/s_ncs_user_import_example07_02.png)

## 받는 사람 {#example--update-and-insert-recipients} 업데이트 및 삽입

데이터베이스의 기존 레코드를 업데이트하고 텍스트 파일에서 새 레코드를 만들고 싶습니다. 다음은 절차의 예입니다.

1. 템플릿 선택

   위의 예 2에 설명된 단계를 반복합니다.

1. 가져올 파일

   가져올 파일을 선택합니다.

   이 예제에서 파일 첫 번째 줄의 개요는 파일이 3개의 레코드에 대한 업데이트와 레코드 생성에 대한 업데이트를 포함하고 있음을 보여줍니다.

   ![](assets/s_ncs_user_import_example02_02.png)

1. 필드 연결

   위의 예 2에서 절차를 적용합니다.

1. 조정

   * 기본적으로 **[!UICONTROL Update or insert]**&#x200B;을(를) 선택된 상태로 두십시오.
   * 데이터베이스의 기존 레코드가 텍스트 파일의 데이터로 수정되도록 **[!UICONTROL Management of duplicates]** 옵션을 **[!UICONTROL Update]** 모드로 유지합니다.
   * **[!UICONTROL Birth date]**, **[!UICONTROL Name]** 및 **[!UICONTROL Company]** 필드를 선택하고 필드에 조정 키를 할당합니다.

      ![](assets/s_ncs_user_import_example04_02.png)

1. 가져오기 시작

   * **[!UICONTROL Start]**&#x200B;을(를) 클릭합니다.

      추적 창에서 가져오기에 성공했는지 확인하고 처리된 레코드 수를 볼 수 있습니다.

      ![](assets/s_ncs_user_import_example06_02.png)

   * 받는 사람 테이블을 확인하여 이 작업으로 레코드가 수정되었는지 확인합니다.

      ![](assets/s_ncs_user_import_example06_03.png)

## 외부 파일 {#example--enrich-the-values-with-those-of-an-external-file}의 값을 채웁니다.

데이터베이스 테이블의 특정 필드를 텍스트 파일에서 수정하여 데이터베이스에 포함된 값에 우선 순위를 지정합니다.

이 예제에서는 텍스트 파일의 특정 필드에 값이 있는 반면 데이터베이스의 해당 필드는 비어 있는 것을 확인할 수 있습니다. 다른 필드에는 데이터베이스에 포함된 필드와 다른 값이 포함되어 있습니다.

* 가져올 텍스트 파일의 내용입니다.

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

   파일의 첫 번째 줄의 미리 보기에서는 파일에 특정 레코드에 대한 업데이트가 포함되어 있음을 확인할 수 있습니다.

1. 조정

   * 테이블로 이동하여 **[!UICONTROL Update]** 작업을 선택합니다.
   * **[!UICONTROL Management of doubles]** 필드에 **[!UICONTROL Reject entity]** 옵션을 선택합니다.
   * 데이터베이스의 기존 레코드가 텍스트 파일의 데이터로 수정되도록 **[!UICONTROL Management of duplicates]** 옵션을 **[!UICONTROL Update]** 모드로 유지합니다.
   * 커서를 **[!UICONTROL Last name (@lastName)]** 노드에 놓고 **[!UICONTROL Update only if destination is empty]** 옵션을 선택합니다.
   * **[!UICONTROL Company (@company)]** 노드에 대해 이 작업을 반복합니다.
   * **[!UICONTROL Birth date]**, **[!UICONTROL E-mail]** 및 **[!UICONTROL First name]** 필드에 조정 키를 할당합니다.

      ![](assets/s_ncs_user_import_example04_03.png)

1. 가져오기 시작

   **[!UICONTROL Start]**&#x200B;을(를) 클릭합니다.

   받는 사람 테이블을 확인하여 가져오기에 의해 레코드가 수정되었는지 확인합니다.

   ![](assets/s_ncs_user_import_example06_05.png)

   비어 있던 값만 텍스트 파일의 값으로 대체되었지만 데이터베이스의 기존 값을 가져오기 파일의 값으로 덮어쓰지 않았습니다.

## 외부 파일 {#example--update-and-enrich-the-values-from-those-in-an-external-file}에 있는 값을 업데이트하고 채웁니다.

텍스트 파일에서 데이터베이스 테이블의 특정 필드를 수정하여 텍스트 파일에 포함된 값을 우선 순위를 지정합니다.

이 예제에서는 텍스트 파일의 특정 필드에 빈 값이 있는 반면 데이터베이스의 해당 필드는 비어 있지 않습니다. 다른 필드에는 데이터베이스의 값과 다른 값이 포함되어 있습니다.

* 가져올 텍스트 파일의 내용입니다.

   ![](assets/s_ncs_user_import_example02_04.png)

* 가져오기 전 데이터베이스 상태

   ![](assets/s_ncs_user_import_example06_07.png)

1. 템플릿 선택

   위의 예 2에서 절차를 적용합니다.

1. 가져올 파일

   가져올 파일을 선택합니다.

   파일의 첫 번째 줄의 미리 보기에서는 파일에 특정 레코드에 대한 빈 필드와 업데이트가 포함되어 있음을 확인할 수 있습니다.

1. 필드 연결

   위의 예 2에서 절차를 적용합니다.

1. 조정

   * 테이블로 이동하여 **[!UICONTROL Update]**&#x200B;을 선택합니다.
   * **[!UICONTROL Management of doubles]** 필드에 **[!UICONTROL Reject entity]** 옵션을 선택합니다.
   * 데이터베이스의 기존 레코드가 텍스트 파일의 데이터로 수정되도록 하려면 **[!UICONTROL Update]** 모드에서 **[!UICONTROL Management of duplicates]** 옵션을 두십시오.
   * 커서를 **[!UICONTROL Account number (@account)]** 노드에 놓고 **[!UICONTROL Take empty values into account]** 옵션을 선택합니다.
   * **[!UICONTROL Birth date]**, **[!UICONTROL E-mail]** 및 **[!UICONTROL First name]** 필드를 선택하고 필드에 조정 키를 할당합니다.

      ![](assets/s_ncs_user_import_example04_04.png)

1. 가져오기 시작

   * **[!UICONTROL Start]**&#x200B;을(를) 클릭합니다.
   * 받는 사람 테이블을 확인하여 작업이 레코드를 수정했는지 확인합니다.

      ![](assets/s_ncs_user_import_example06_06.png)

      비어 있던 텍스트 파일의 값이 데이터베이스의 값을 덮어씁니다. 4단계에서 중복으로 선택된 **[!UICONTROL Update]** 옵션과 함께 데이터베이스의 기존 값이 가져오기 파일의 값으로 업데이트되었습니다.
