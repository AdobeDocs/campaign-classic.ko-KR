---
solution: Campaign Classic
product: campaign
title: 다대다 관계를 사용하여 쿼리
description: 다대다 관계를 사용하여 쿼리를 수행하는 방법 살펴보기
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---


# 다대다 관계를 사용하여 쿼리 {#querying-using-a-many-to-many-relationship}

이 예에서는 지난 7일 동안 연락하지 않은 수신자를 복구하려고 합니다. 이 쿼리는 모든 배달과 관련이 있습니다.

이 예에서는 컬렉션 요소(또는 주황색 노드)의 선택과 관련된 필터를 구성하는 방법도 보여 줍니다. 컬렉션 요소는 **[!UICONTROL Field to select]** 창에서 사용할 수 있습니다.

* 어떤 표를 선택해야 합니까?

   받는 사람 테이블(**nms:recipient**)

* 출력 열에 대해 선택할 필드

   기본 키, 성, 이름 및 이메일

* 필터링된 정보의 기준

   수신자의 배달 로그 기준(오늘 7일 전)

다음 단계를 적용합니다.

1. 일반 쿼리 편집기를 열고 수신자 테이블을 선택합니다 **[!UICONTROL (nms:recipient)]**.
1. 창 **[!UICONTROL Data to extract]** 에서 **[!UICONTROL Primary key]**, **[!UICONTROL First name]**&#x200B;및 **[!UICONTROL Last name]** 을 선택합니다 **[!UICONTROL Email]**.

   ![](assets/query_editor_nveau_33.png)

1. 정렬 창에서 이름을 알파벳순으로 정렬합니다.

   ![](assets/query_editor_nveau_34.png)

1. In the **[!UICONTROL Data filtering]** window, select **[!UICONTROL Filtering conditions]**.
1. 지난 7일 동안 추적 로그가 없는 프로파일을 추출하기 위한 필터링 조건에는 두 단계가 포함됩니다. **[!UICONTROL Target element]** 선택해야 하는 요소는 다대다 링크입니다.

   * 첫 번째 열에 대한 **[!UICONTROL Recipient delivery logs (broadlog)]** 컬렉션 요소(주황색 노드)를 선택하여 **[!UICONTROL Value]** 시작합니다.

      ![](assets/query_editor_nveau_67.png)

      연산자를 **[!UICONTROL do not exist as]** 선택합니다. 이 줄에서 두 번째 값을 선택할 필요가 없습니다.

   * 두 번째 필터링 조건의 내용은 첫 번째 필터링 조건에 따라 다릅니다. 이 **[!UICONTROL Event date]** 테이블에 대한 링크가 있기 때문에 이 필드는 **[!UICONTROL Recipient delivery logs]** 테이블에서 직접 제공됩니다.

      ![](assets/query_editor_nveau_36.png)

      연산자 **[!UICONTROL Event date]** 로 **[!UICONTROL greater than or equal to]** 선택합니다. 값을 **[!UICONTROL DaysAgo (7)]** 선택합니다. 이렇게 하려면 필드 **[!UICONTROL Edit expression]** 에서 을 **[!UICONTROL Value]** 클릭합니다. 창에서 **[!UICONTROL Formula type]** 값을 &quot;7&quot; **[!UICONTROL Process on dates]** 으로 지정하고 선택합니다 **[!UICONTROL Current date minus n days]**.

      ![](assets/query_editor_nveau_37.png)

      필터 조건이 구성됩니다.

      ![](assets/query_editor_nveau_38.png)

1. 창에서 **[!UICONTROL Data formatting]** 마지막 이름을 대문자로 전환합니다. 열의 **[!UICONTROL Last name]** 선을 **[!UICONTROL Transformation]** 클릭하고 드롭다운 메뉴 **[!UICONTROL Switch to upper case]** 에서 선택합니다.

   ![](assets/query_editor_nveau_39.png)

1. 이 **[!UICONTROL Add a calculated field]** 함수를 사용하여 데이터 미리 보기 창에 열을 삽입합니다.

   이 예에서 단일 열에 받는 사람의 이름과 성을 포함하는 계산된 필드를 추가합니다. 함수를 **[!UICONTROL Add a calculated field]** 클릭합니다. 창에서 **[!UICONTROL Export calculated field definition]** 레이블과 내부 이름을 입력하고 **[!UICONTROL JavaScript Expression]** 유형을 선택합니다. 그런 다음 다음 다음 표현식을 입력합니다.

   ```
   var rep = source._firstName+" - "+source._lastName
   return rep
   ```

   ![](assets/query_editor_nveau_40.png)

   **[!UICONTROL OK]**&#x200B;을(를) 클릭합니다. 창이 **[!UICONTROL Data formatting]** 구성됩니다.

   계산된 필드 추가에 대한 자세한 내용은 이 섹션을 참조하십시오.

1. 결과가 창에 **[!UICONTROL Data preview]** 표시됩니다. 지난 7일 동안 연락하지 않은 수신자는 사전순으로 표시됩니다. 이름은 대소문자를 구분하고 이름과 이름이 같은 열이 만들어집니다.

   ![](assets/query_editor_nveau_41.png)
