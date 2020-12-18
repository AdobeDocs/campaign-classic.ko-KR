---
solution: Campaign Classic
product: campaign
title: 열거형 유형 계산 필드 추가
description: 열거형 유형 계산 필드를 추가하는 방법에 대해 알아봅니다.
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---


# 열거형 유형 계산 필드 {#adding-an-enumeration-type-calculated-field} 추가

여기에서 **[!UICONTROL Enumerations]** 유형의 계산된 필드를 사용하여 쿼리를 만듭니다. 이 필드는 데이터 미리 보기 창에 추가 열을 생성합니다. 이 열은 각 수신자에 대한 결과로 반환된 숫자 값을 지정합니다(0, 1 및 2). 새 열의 각 값에 성이 할당됩니다.값이 &quot;0&quot;인 경우 &quot;1&quot;의 경우 &quot;Male&quot;, &quot;2&quot;의 경우 &quot;Female&quot; 또는 &quot;Not indicated&quot;의 경우

* 어떤 표를 선택해야 합니까?

   받는 사람 테이블(nms:recipient)

* 출력 열에서 선택할 필드를 선택하십시오.

   성, 이름, 성별

* 정보를 기준으로 필터링할 기준

   받는 사람 언어

다음 단계를 적용합니다.

1. 범용 쿼리 편집기를 열고 수신자 테이블(**[!UICONTROL nms:recipient]**)을 선택합니다.
1. **[!UICONTROL Data to extract]** 창에서 **[!UICONTROL Last name]**, **[!UICONTROL First name]** 및 **[!UICONTROL Gender]**&#x200B;을 선택합니다.

   ![](assets/query_editor_nveau_73.png)

1. **[!UICONTROL Sorting]** 창에서 **[!UICONTROL Next]**:이 예에는 정렬 작업이 필요하지 않습니다.
1. **[!UICONTROL Data filtering]**&#x200B;에서 **[!UICONTROL Filtering conditions]**&#x200B;을(를) 선택합니다.
1. **[!UICONTROL Target element]** 창에서 영어를 말하는 수신자를 수집하도록 필터 조건을 설정합니다.

   ![](assets/query_editor_nveau_74.png)

1. **[!UICONTROL Data formatting]** 창에서 **[!UICONTROL Add a calculated field]**&#x200B;을 클릭합니다.

   ![](assets/query_editor_nveau_75.png)

1. **[!UICONTROL Export calculated field definition]** 창의 **[!UICONTROL Type]** 창으로 이동하여 **[!UICONTROL Enumerations]**&#x200B;를 선택합니다.

   새 계산된 필드가 참조하는 열을 정의합니다. 이렇게 하려면 **[!UICONTROL Source column]** 필드의 드롭다운 메뉴에서 **[!UICONTROL Gender]** 열을 선택합니다.대상 값은 **[!UICONTROL Gender]** 열과 일치합니다.

   ![](assets/query_editor_nveau_76.png)

   **소스** 및 **대상** 값을 정의합니다.대상 값을 사용하면 쿼리 결과를 읽기 쉽게 만들 수 있습니다. 이 쿼리는 받는 사람 성별을 반환해야 하며 결과는 0, 1 또는 2입니다.

   입력할 각 &quot;source-destination&quot; 줄의 경우 **[!UICONTROL List of enumeration values]**&#x200B;에서 **[!UICONTROL Add]**&#x200B;을 클릭합니다.

   * **[!UICONTROL Source]** 열에서 새 줄에 각 성별(0,1,2)의 소스 값을 입력합니다.
   * **[!UICONTROL Destination]** 열에 값을 입력합니다.라인 &quot;0&quot;에 대해 &quot;Not indicated&quot;, 라인 &quot;1&quot;에 대해 &quot;Male&quot;, 라인 &quot;2&quot;에 대해 &quot;Female&quot;.

   **[!UICONTROL Keep the source value]** 함수를 선택합니다.

   **[!UICONTROL OK]**&#x200B;을 클릭하여 계산된 필드를 승인합니다.

   ![](assets/query_editor_nveau_77.png)

1. **[!UICONTROL Data formatting]** 창에서 **[!UICONTROL Next]**&#x200B;을 클릭합니다.
1. 미리 보기 창에서 **[!UICONTROL start the preview of the data]**.

   추가 열은 0, 1 및 2의 성별을 정의합니다.

   * 0을 &quot;지정되지 않음&quot;
   * &quot;남성&quot;의 경우 1
   * &quot;여성&quot;의 경우 2

   ![](assets/query_editor_nveau_78.png)

   예를 들어 **[!UICONTROL List of enumeration values]**&#x200B;에 성별 &quot;2&quot;를 입력하지 않고 **[!UICONTROL In other cases]** 필드의 **[!UICONTROL Generate a warning and continue]** 함수를 선택한 경우 경고 로그가 표시됩니다. 이 로그는 성별 &quot;2&quot;(여성)을 입력하지 않았음을 나타냅니다. 데이터 미리 보기 창의 **[!UICONTROL Logs generated during export]** 필드에 표시됩니다.

   ![](assets/query_editor_nveau_79.png)

   다른 예를 들어 &quot;2&quot; 열거형 값이 입력되지 않았다고 가정해 보겠습니다. **[!UICONTROL Generate an error and reject the line]** 함수를 선택합니다.모든 성별 &quot;2&quot; 수신자는 예외 항목 및 기타 라인(이름 및 성 등)의 정보를 발생시킵니다. 내보낼 수 없습니다. 데이터 미리 보기 창의 **[!UICONTROL Logs generated during export]** 필드에 오류 로그가 표시됩니다. 이 로그는 열거형 값 &quot;2&quot;를 입력하지 않았음을 나타냅니다.

   ![](assets/query_editor_nveau_80.png)
