---
title: 다대다 관계를 사용하여 쿼리
description: 다대다 관계를 사용하여 쿼리를 수행하는 방법 살펴보기
page-status-flag: never-activated
uuid: 0556d53e-0fdf-47b3-b1e0-b52e85e0c662
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 7e5605c8-78f2-4011-b317-96a59c699848
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cf7c90f0ea9fbce3a4fd53f24189617cbd33fc40

---


# 다대다 관계를 사용하여 쿼리 {#querying-using-a-many-to-many-relationship}

이 예에서는 지난 7일 동안 연결되지 않은 수신자를 복구하려고 합니다. 이 쿼리는 모든 게재와 관련이 있습니다.

이 예에서는 컬렉션 요소(또는 주황색 노드)의 선택과 관련된 필터를 구성하는 방법도 보여줍니다. 컬렉션 요소는 **[!UICONTROL Field to select]** 창에서 사용할 수 있습니다.

* 어떤 표를 선택해야 합니까?

   받는 사람 테이블(**nms:recipient**)

* 출력 열에 대해 선택할 필드

   기본 키, 성, 이름 및 이메일

* 필터링된 정보를 기준으로

   오늘 7일 전에 다시 돌아오는 수신자의 배달 로그 기준

다음 단계를 적용합니다.

1. 일반 쿼리 편집기를 열고 수신자 테이블을 선택합니다 **[!UICONTROL (nms:recipient)]**.
1. 창에서 **[!UICONTROL Data to extract]** , **[!UICONTROL Primary key]****[!UICONTROL First name]**&#x200B;및 **[!UICONTROL Last name]** **[!UICONTROL Email]**&#x200B;를 선택합니다.

   ![](assets/query_editor_nveau_33.png)

1. 정렬 창에서 이름을 알파벳순으로 정렬합니다.

   ![](assets/query_editor_nveau_34.png)

1. 창에서 **[!UICONTROL Data filtering]** 을 선택합니다 **[!UICONTROL Filtering conditions]**.
1. 창에서 지난 7일 동안 추적 로그가 없는 프로파일 추출을 위한 필터링 조건에는 두 단계가 포함됩니다. **[!UICONTROL Target element]** 선택해야 하는 요소는 다대다 링크입니다.

   * 첫 번째 **[!UICONTROL Recipient delivery logs (broadlog)]** 열에 대한 **[!UICONTROL Value]** 컬렉션 요소(주황색 노드)를 선택하여 시작합니다.

      ![](assets/query_editor_nveau_67.png)

      연산자를 **[!UICONTROL do not exist as]** 선택합니다. 이 줄에서 두 번째 값을 선택할 필요가 없습니다.

   * 두 번째 필터링 조건의 내용은 첫 번째 필터링 조건에 따라 달라집니다. 이 **[!UICONTROL Event date]** 테이블에 대한 링크가 있으므로 이 **[!UICONTROL Recipient delivery logs]** 필드는 테이블에서 직접 제공됩니다.

      ![](assets/query_editor_nveau_36.png)

      연산자로 **[!UICONTROL Event date]** 선택합니다 **[!UICONTROL greater than or equal to]** . 값을 **[!UICONTROL DaysAgo (7)]** 선택합니다. 이렇게 하려면 **[!UICONTROL Edit expression]** 필드를 클릭합니다 **[!UICONTROL Value]** . 창에서 **[!UICONTROL Formula type]** 을 선택하고 **[!UICONTROL Process on dates]** **[!UICONTROL Current date minus n days]**&#x200B;값으로 &quot;7&quot;을 지정합니다.

      ![](assets/query_editor_nveau_37.png)

      필터 조건이 구성됩니다.

      ![](assets/query_editor_nveau_38.png)

1. 창에서 **[!UICONTROL Data formatting]** 성을 대문자로 전환합니다. 열의 **[!UICONTROL Last name]** 행을 클릭하고 **[!UICONTROL Transformation]** 드롭다운 **[!UICONTROL Switch to upper case]** 메뉴에서 선택합니다.

   ![](assets/query_editor_nveau_39.png)

1. 이 **[!UICONTROL Add a calculated field]** 함수를 사용하여 데이터 미리 보기 창에 열을 삽입합니다.

   이 예에서는 단일 열에 수신자의 이름과 성이 있는 계산된 필드를 추가합니다. 함수를 **[!UICONTROL Add a calculated field]** 클릭합니다. 창에서 **[!UICONTROL Export calculated field definition]** 레이블과 내부 이름을 입력하고 **[!UICONTROL JavaScript Expression]** 유형을 선택합니다. 그런 다음 다음 표현식을 입력합니다.

   ```
   var rep = source._firstName+" - "+source._lastName
   return rep
   ```

   ![](assets/query_editor_nveau_40.png)

   클릭 **[!UICONTROL OK]**. 창이 **[!UICONTROL Data formatting]** 구성됩니다.

   계산된 필드 추가에 대한 자세한 내용은 이 섹션을 참조하십시오.

1. 결과가 **[!UICONTROL Data preview]** 창에 표시됩니다. 지난 7일 동안 연락하지 않은 수신자는 알파벳 순으로 표시됩니다. 이름은 대문자로 표시되며 이름과 성을 가진 열이 만들어집니다.

   ![](assets/query_editor_nveau_41.png)
