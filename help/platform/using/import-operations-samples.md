---
product: campaign
title: 일반 가져오기 샘플
description: 가져오기 작업을 사용하여 수행할 수 있는 일반 가져오기에 대해 자세히 알아봅니다.
feature: Data Management
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 4582b524-2b6d-484c-bace-29d2e69f60e9
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '1011'
ht-degree: 1%

---

# 일반 가져오기 샘플 {#import-operations-samples}



## 수신자 목록에서 가져오기 {#example--import-from-a-list-of-recipients}

목록 개요에서 수신자 목록을 만들고 제공하려면 다음 단계를 적용합니다.

1. 목록 만들기

   * Adobe Campaign 홈 페이지의 **[!UICONTROL Profiles and targets]** 메뉴에서 **[!UICONTROL Lists]** 링크를 클릭합니다.
   * **[!UICONTROL Create]**&#x200B;을(를) 클릭한 다음 **[!UICONTROL Import a list]** 단추를 클릭합니다.

1. 가져올 파일 선택

   **[!UICONTROL Local file]** 필드 오른쪽에 있는 폴더를 클릭하고 가져올 목록이 포함된 파일을 선택합니다.

   ![](assets/s_ncs_user_import_example00_01.png)

1. 목록 이름 및 저장소

   목록의 이름을 입력하고 저장해야 하는 디렉터리를 선택합니다.

   ![](assets/s_ncs_user_import_example00_02.png)

1. 가져오기 실행

   목록을 가져오려면 **[!UICONTROL Next]**&#x200B;을(를) 클릭한 다음 **[!UICONTROL Start]**&#x200B;을(를) 클릭합니다.

   ![](assets/s_ncs_user_import_example00_03.png)

## 텍스트 파일에서 새 레코드 가져오기 {#example--import-new-records-from-a-text-file-}

텍스트 파일에 저장된 새 수신자 프로필을 Adobe Campaign 데이터베이스로 가져오려면 다음 단계를 적용합니다.

1. 템플릿 선택

   * Adobe Campaign 홈페이지에서 **[!UICONTROL Profiles and targets]** 링크를 클릭한 다음 **[!UICONTROL Jobs]**&#x200B;을(를) 클릭합니다. 작업 목록 위에서 **[!UICONTROL New import]**&#x200B;을(를) 클릭합니다.
   * 기본적으로 선택된 **[!UICONTROL New text import]** 템플릿을 유지합니다.
   * 레이블과 설명을 변경합니다.
   * **[!UICONTROL Simple import]**&#x200B;을(를) 선택합니다.
   * 기본 작업 폴더를 유지합니다.
   * 실행 중 가져오기 세부 정보를 보려면 **[!UICONTROL Advanced parameters]**&#x200B;을(를) 클릭하고 **[!UICONTROL Tracking mode]** 옵션을 선택하십시오.

1. 가져올 파일 선택

   **[!UICONTROL Local file]** 필드 오른쪽에 있는 폴더를 클릭하고 가져올 파일을 선택합니다.

   ![](assets/s_ncs_user_import_example01_01.png)

1. 필드 연결

   원본 및 대상 스키마를 자동으로 매핑하려면 **[!UICONTROL Guess the destination fields]** 아이콘을 클릭하십시오. **[!UICONTROL Next]**&#x200B;을(를) 클릭하기 전에 이 창에서 정보를 확인하십시오.

   ![](assets/s_ncs_user_import_example03_01.png)

1. 조정

   * **수신자(nms:recipient)** 테이블로 이동합니다.
   * **[!UICONTROL Insertion]** 작업을 선택하고 다른 필드에 기본값을 둡니다.

     ![](assets/s_ncs_user_import_example04_01.png)

1. 수신자 가져오기

   * 필요한 경우 레코드를 가져올 폴더를 지정합니다.

     ![](assets/s_ncs_user_import_example05_01.png)

1. 가져오기 실행

   * **[!UICONTROL Start]**&#x200B;를 클릭합니다.

     편집기의 중앙 영역에서 가져오기 작업이 성공했는지 확인하고 처리된 레코드 수를 볼 수 있습니다.

     ![](assets/s_ncs_user_import_example06_01.png)

     **[!UICONTROL Tracking]** 모드를 사용하면 원본 파일의 각 레코드에 대한 가져오기 세부 정보를 추적할 수 있습니다. 이렇게 하려면 홈 페이지에서 **[!UICONTROL Profiles and Targets]**&#x200B;을(를) 클릭한 다음 **[!UICONTROL Processes]**&#x200B;을(를) 클릭하고 관련 가져오기를 선택한 다음 **[!UICONTROL General]**, **[!UICONTROL Journal]** 및 **[!UICONTROL Rejects]** 탭을 조회합니다.

      * 가져오기 진행률 확인

        ![](assets/s_ncs_user_import_example07_01.png)

      * 각 레코드에 대한 프로세스 보기

        ![](assets/s_ncs_user_import_example07_02.png)

## 수신자 업데이트 및 삽입 {#example--update-and-insert-recipients}

데이터베이스의 기존 레코드를 업데이트하고 텍스트 파일에서 새 레코드를 만들려고 합니다. 다음은 절차의 예입니다.

1. 템플릿 선택

   위의 예 2에 설명된 단계를 반복합니다.

1. 가져올 파일

   가져올 파일을 선택합니다.

   이 예제에서 파일의 첫 번째 줄에 대한 개요는 파일에 3개의 레코드와 레코드 만들기에 대한 업데이트가 포함되어 있음을 보여 줍니다.

   ![](assets/s_ncs_user_import_example02_02.png)

1. 필드 연결

   위의 예 2에 있는 절차를 적용합니다.

1. 조정

   * 기본적으로 **[!UICONTROL Update or insert]**&#x200B;을(를) 선택한 상태로 유지합니다.
   * 데이터베이스의 기존 레코드가 텍스트 파일의 데이터로 수정되도록 **[!UICONTROL Management of duplicates]** 옵션을 **[!UICONTROL Update]** 모드로 유지합니다.
   * **[!UICONTROL Birth date]**, **[!UICONTROL Name]** 및 **[!UICONTROL Company]** 필드를 선택하고 조정 키를 할당하십시오.

     ![](assets/s_ncs_user_import_example04_02.png)

1. 가져오기 실행

   * **[!UICONTROL Start]**&#x200B;를 클릭합니다.

     추적 창에서 가져오기가 성공했는지 확인하고 처리된 레코드 수를 볼 수 있습니다.

     ![](assets/s_ncs_user_import_example06_02.png)

   * 수신자 테이블에서 레코드가 이 작업에 의해 수정되었는지 확인합니다.

     ![](assets/s_ncs_user_import_example06_03.png)

## 외부 파일의 값으로 값 보강 {#example--enrich-the-values-with-those-of-an-external-file}

텍스트 파일에서 데이터베이스 테이블의 특정 필드를 수정하여 데이터베이스에 포함된 값에 우선 순위를 두려고 합니다.

이 예제에서 텍스트 파일의 특정 필드는 값을 가지지만 데이터베이스의 해당 필드는 비어 있는 것을 볼 수 있습니다. 다른 필드에는 데이터베이스에 포함된 값과 다른 값이 포함됩니다.

* 가져올 텍스트 파일의 컨텐츠입니다.

  ![](assets/s_ncs_user_import_example02_03.png)

* 가져오기 전 데이터베이스 상태

  ![](assets/s_ncs_user_import_example06_04.png)

다음 단계를 적용합니다.

1. 템플릿 선택

   위의 예 2에 있는 절차를 적용합니다.

1. 가져올 파일

   가져올 파일을 선택합니다.

1. 필드 연결

   위의 예 2에 있는 절차를 적용합니다.

   파일의 첫 번째 줄 미리 보기에서 파일에 특정 레코드에 대한 업데이트가 포함되어 있음을 확인할 수 있습니다.

1. 조정

   * 테이블로 이동하여 **[!UICONTROL Update]** 작업을 선택하십시오.
   * **[!UICONTROL Management of doubles]** 필드에 대해 **[!UICONTROL Reject entity]** 옵션을 선택합니다.
   * 데이터베이스의 기존 레코드가 텍스트 파일의 데이터로 수정되도록 **[!UICONTROL Management of duplicates]** 옵션을 **[!UICONTROL Update]** 모드로 유지합니다.
   * **[!UICONTROL Last name (@lastName)]** 노드에 커서를 놓고 **[!UICONTROL Update only if destination is empty]** 옵션을 선택합니다.
   * **[!UICONTROL Company (@company)]** 노드에 대해 이 작업을 반복합니다.
   * 필드 **[!UICONTROL Birth date]**, **[!UICONTROL Email]** 및 **[!UICONTROL First name]**&#x200B;에 조정 키를 할당하십시오.

     ![](assets/s_ncs_user_import_example04_03.png)

1. 가져오기 실행

   **[!UICONTROL Start]**&#x200B;를 클릭합니다.

   수신자 테이블에서 가져오기로 레코드가 수정되었는지 확인합니다.

   ![](assets/s_ncs_user_import_example06_05.png)

   비어 있는 값만 텍스트 파일의 값으로 대체되었지만 데이터베이스의 기존 값은 가져오기 파일의 값으로 덮어써지지 않았습니다.

## 외부 파일의 값을 업데이트하고 보강합니다. {#example--update-and-enrich-the-values-from-those-in-an-external-file}

텍스트 파일에 포함된 값에 우선 순위를 부여하여 데이터베이스 테이블의 특정 필드를 수정하려고 합니다.

이 예제에서 텍스트 파일의 특정 필드는 비어 있는 값을 가지지만 데이터베이스의 해당 필드는 비어 있지 않다는 것을 알 수 있습니다. 다른 필드에는 데이터베이스의 값과 다른 값이 포함됩니다.

* 가져올 텍스트 파일의 컨텐츠입니다.

  ![](assets/s_ncs_user_import_example02_04.png)

* 가져오기 전 데이터베이스 상태

  ![](assets/s_ncs_user_import_example06_07.png)

1. 템플릿 선택

   위의 예 2에 있는 절차를 적용합니다.

1. 가져올 파일

   가져올 파일을 선택합니다.

   파일의 첫 번째 줄 미리 보기에서 파일에 특정 레코드에 대한 빈 필드 및 업데이트가 포함되어 있음을 확인할 수 있습니다.

1. 필드 연결

   위의 예 2에 있는 절차를 적용합니다.

1. 조정

   * 테이블로 이동하여 **[!UICONTROL Update]**&#x200B;을(를) 선택하십시오.
   * **[!UICONTROL Management of doubles]** 필드에 대해 **[!UICONTROL Reject entity]** 옵션을 선택합니다.
   * 데이터베이스의 기존 레코드를 텍스트 파일의 데이터로 수정할 수 있도록 **[!UICONTROL Update]** 모드의 **[!UICONTROL Management of duplicates]** 옵션을 그대로 둡니다.
   * **[!UICONTROL Account number (@account)]** 노드에 커서를 놓고 **[!UICONTROL Take empty values into account]** 옵션을 선택합니다.
   * **[!UICONTROL Birth date]**, **[!UICONTROL Email]** 및 **[!UICONTROL First name]** 필드를 선택하고 조정 키를 할당하십시오.

     ![](assets/s_ncs_user_import_example04_04.png)

1. 가져오기 실행

   * **[!UICONTROL Start]**&#x200B;를 클릭합니다.
   * 수신자 테이블에서 작업에 의해 레코드가 수정되었는지 확인합니다.

     ![](assets/s_ncs_user_import_example06_06.png)

     비어 있는 텍스트 파일의 값이 데이터베이스의 값을 덮어썼습니다. 데이터베이스의 기존 값이 4단계에서 중복을 위해 선택한 **[!UICONTROL Update]** 옵션과 함께 가져오기 파일의 값으로 업데이트되었습니다.
