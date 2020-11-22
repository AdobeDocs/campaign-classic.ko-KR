---
solution: Campaign Classic
product: campaign
title: 수신자 테이블 쿼리
description: 받는 사람 테이블을 쿼리하는 방법 알아보기
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 3%

---


# 수신자 테이블 쿼리 {#querying-recipient-table}

이 예에서는 이메일 도메인이 &quot;orange.co.uk&quot;이고 런던에 살지 않는 수신자의 이름과 이메일을 복구하려고 합니다.

* 어떤 테이블을 선택해야 합니까?

   받는 사람 테이블(nms:recipient)

* 출력 열로 선택할 필드

   이메일, 이름, 구/군/시 및 계정 번호

* 받는 사람의 필터링 조건은 무엇입니까?

   도시 및 이메일 도메인

* 정렬이 구성되어 있습니까?

   예, **[!UICONTROL Account number]** 및 **[!UICONTROL Last name]**

이 예제를 만들려면 다음 단계를 수행하십시오.

1. 을 **[!UICONTROL Tools > Generic query editor...]** 클릭하고 **수신자** (nms:recipient **) 테이블을**&#x200B;선택합니다. 그 다음 **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다.
1. 선택: **[!UICONTROL Last name]**, **[!UICONTROL First name]**, **[!UICONTROL Email]**, **[!UICONTROL City]** and **[!UICONTROL Account number]**&#x200B;를 참조하십시오. 이러한 필드는 에 추가됩니다 **[!UICONTROL Output columns]**. 그 다음 **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다.

   ![](assets/query_editor_03.png)

1. 열을 정렬하여 올바른 순서로 표시합니다. 여기서 계정 번호를 내림차순 및 이름의 알파벳 순서로 정렬하려고 합니다. 그 다음 **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다.

   ![](assets/query_editor_04.png)

1. 창에서 **[!UICONTROL Data filtering]** 검색을 세분화합니다.을 선택하고 **[!UICONTROL Filtering conditions]** 클릭합니다 **[!UICONTROL Next]**.
1. 이 **[!UICONTROL Target element]** 창을 통해 필터 설정을 입력할 수 있습니다.

   다음 필터 조건을 정의합니다.받는 사람: &quot;orange.co.uk&quot;과 같은 이메일 도메인을 가진 사람. 이렇게 하려면 **열에서** 이메일 도메인(@email) **[!UICONTROL Expression]** 을 **선택하고** 열에서 **[!UICONTROL Operator]** 같음을 **[!UICONTROL Value]** 선택하고열에 &quot;orange.co.uk&quot;을 입력합니다.

   ![](assets/query_editor_05.png)

1. 필요한 경우 이 **[!UICONTROL Distribution of values]** 단추를 클릭하여 잠재 고객의 이메일 도메인을 기준으로 배포를 확인합니다. 데이터베이스의 각 이메일 도메인에 대해 백분율을 사용할 수 있습니다. 필터를 적용할 때까지 &quot;orange.co.uk&quot;이 아닌 도메인이 표시됩니다.

   질의 요약이 창 하단에 표시됩니다. **전자 메일 도메인이 &#39;orange.co.uk&#39;과 같습니다**.

1. 쿼리 결과 **[!UICONTROL Preview]** 에 대한 아이디어를 얻으려면 다음을 클릭합니다.&quot;orange.co.uk&quot; 이메일 도메인만 표시됩니다.

   ![](assets/query_editor_nveau_17.png)

1. 우리는 이제 런던에 살고 있지 않은 연락처를 찾기 위해 질문을 바꿀 것이다.

   열 **[!UICONTROL City (location/@city)]** 에서 **[!UICONTROL Expression]** 연산자로 **[!UICONTROL different from]** 선택하고 열 **[!UICONTROL London]** 에 **[!UICONTROL Value]** 입력합니다.

   ![](assets/query_editor_08.png)

1. 그러면 **[!UICONTROL Data formatting]** 창가쪽으로 가시면 됩니다 열 순서를 확인하십시오. &quot;계정 번호&quot; 열 아래에서 &quot;구/군/시&quot; 열을 위로 이동합니다.

   목록에서 제거하려면 &quot;이름&quot; 열의 선택을 취소합니다.

   ![](assets/query_editor_nveau_15.png)

1. In the **[!UICONTROL Data preview]** window, click **[!UICONTROL Start the preview of the data]**. 이 함수는 쿼리 결과를 계산합니다.

   이 **[!UICONTROL Column results]** 탭에는 쿼리 결과가 열에 표시됩니다.

   그 결과 런던에 살지 않는 &quot;orange.co.uk&quot; 이메일 도메인이 있는 모든 수신자가 표시됩니다. 이전 단계에서 선택 취소되었기 때문에 &quot;이름&quot; 열은 표시되지 않습니다. 계정 번호는 내림차순으로 정렬됩니다.

   ![](assets/query_editor_nveau_12.png)

   이 **[!UICONTROL XML result]** 탭에는 XML 형식의 결과가 표시됩니다.

   ![](assets/query_editor_nveau_13.png)

   이 **[!UICONTROL Generated QSL queries]** 탭에는 SQL 형식의 쿼리 결과가 표시됩니다.

   ![](assets/query_editor_nveau_14.png)
