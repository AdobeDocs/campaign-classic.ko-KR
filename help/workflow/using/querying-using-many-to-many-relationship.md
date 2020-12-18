---
solution: Campaign Classic
product: campaign
title: 다대다 관계를 사용하여 쿼리
description: 다대다 관계를 사용하여 쿼리를 수행하는 방법 알아보기
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---


# 다대다 관계 {#querying-using-a-many-to-many-relationship} 쿼리

이 예에서는 지난 7일 동안 연락하지 않은 수신자를 복구하려고 합니다. 이 쿼리는 모든 게재와 관련이 있습니다.

이 예는 컬렉션 요소(또는 주황색 노드)의 선택과 관련된 필터를 구성하는 방법도 보여줍니다. 컬렉션 요소는 **[!UICONTROL Field to select]** 창에서 사용할 수 있습니다.

* 어떤 표를 선택해야 합니까?

   받는 사람 테이블(**nms:recipient**)

* 출력 열에 대해 선택할 필드

   기본 키, 성, 이름 및 이메일

* 필터링된 정보가 있는 기준

   오늘 7일 전에 다시 돌아오는 수신자의 배달 로그 기준

다음 단계를 적용합니다.

1. 범용 쿼리 편집기를 열고 수신자 테이블 **[!UICONTROL (nms:recipient)]**&#x200B;을 선택합니다.
1. **[!UICONTROL Data to extract]** 창에서 **[!UICONTROL Primary key]**, **[!UICONTROL First name]**, **[!UICONTROL Last name]** 및 **[!UICONTROL Email]**&#x200B;를 선택합니다.

   ![](assets/query_editor_nveau_33.png)

1. 정렬 창에서 이름을 알파벳순으로 정렬합니다.

   ![](assets/query_editor_nveau_34.png)

1. **[!UICONTROL Data filtering]** 창에서 **[!UICONTROL Filtering conditions]**&#x200B;을 선택합니다.
1. **[!UICONTROL Target element]** 창에서 지난 7일 동안 추적 로그가 없는 프로파일을 추출하기 위한 필터링 조건에 2단계가 포함됩니다. 선택해야 하는 요소는 다대다 링크입니다.

   * 첫 번째 **[!UICONTROL Value]** 열에 대해 **[!UICONTROL Recipient delivery logs (broadlog)]** 컬렉션 요소(주황색 노드)를 선택하여 시작합니다.

      ![](assets/query_editor_nveau_67.png)

      **[!UICONTROL do not exist as]** 연산자를 선택합니다. 이 행에서 두 번째 값을 선택할 필요가 없습니다.

   * 두 번째 필터링 조건의 내용은 첫 번째 필터링 조건에 따라 다릅니다. 여기에서 **[!UICONTROL Event date]** 필드는 이 테이블에 대한 링크가 있으므로 **[!UICONTROL Recipient delivery logs]** 테이블에서 직접 제공됩니다.

      ![](assets/query_editor_nveau_36.png)

      **[!UICONTROL greater than or equal to]** 연산자가 있는 **[!UICONTROL Event date]**&#x200B;을 선택합니다. **[!UICONTROL DaysAgo (7)]** 값을 선택합니다. 이렇게 하려면 **[!UICONTROL Value]** 필드에서 **[!UICONTROL Edit expression]**&#x200B;을 클릭합니다. **[!UICONTROL Formula type]** 창에서 **[!UICONTROL Process on dates]** 및 **[!UICONTROL Current date minus n days]**&#x200B;를 선택하고 &quot;7&quot;을 값으로 지정합니다.

      ![](assets/query_editor_nveau_37.png)

      필터 조건이 구성됩니다.

      ![](assets/query_editor_nveau_38.png)

1. **[!UICONTROL Data formatting]** 창에서 마지막 이름을 대문자로 전환합니다. **[!UICONTROL Transformation]** 열에서 **[!UICONTROL Last name]** 행을 클릭하고 드롭다운 메뉴에서 **[!UICONTROL Switch to upper case]**&#x200B;를 선택합니다.

   ![](assets/query_editor_nveau_39.png)

1. **[!UICONTROL Add a calculated field]** 함수를 사용하여 데이터 미리 보기 창에 열을 삽입합니다.

   이 예에서 단일 열에 받는 사람의 이름과 성을 가진 계산된 필드를 추가합니다. **[!UICONTROL Add a calculated field]** 함수를 클릭합니다. **[!UICONTROL Export calculated field definition]** 창에서 레이블과 내부 이름을 입력하고 **[!UICONTROL JavaScript Expression]** 유형을 선택합니다. 그런 다음 다음 다음 표현식을 입력합니다.

   ```
   var rep = source._firstName+" - "+source._lastName
   return rep
   ```

   ![](assets/query_editor_nveau_40.png)

   **[!UICONTROL OK]**&#x200B;을(를) 클릭합니다. **[!UICONTROL Data formatting]** 창이 구성되었습니다.

   계산된 필드 추가에 대한 자세한 내용은 이 섹션을 참조하십시오.

1. 결과는 **[!UICONTROL Data preview]** 창에 표시됩니다. 지난 7일 동안 연락하지 않은 수신자는 알파벳순으로 표시됩니다. 이름은 대문자로 표시되며 이름과 성을 가진 열이 만들어집니다.

   ![](assets/query_editor_nveau_41.png)
