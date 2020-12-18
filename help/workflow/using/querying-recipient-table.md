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

이 예에서는 이메일 도메인이 &quot;orange.co.uk&quot;이고 런던에 살고 있지 않은 수신자의 이름과 이메일을 복구하려고 합니다.

* 어떤 테이블을 선택해야 합니까?

   받는 사람 테이블(nms:recipient)

* 출력 열로 선택할 필드

   이메일, 이름, 구/군/시 및 계정 번호

* 받는 사람의 필터링 조건은 무엇입니까?

   도시 및 이메일 도메인

* 정렬이 구성되어 있습니까?

   예, **[!UICONTROL Account number]** 및 **[!UICONTROL Last name]** 기준

이 예제를 만들려면 다음 단계를 수행하십시오.

1. **[!UICONTROL Tools > Generic query editor...]**&#x200B;을 클릭하고 **수신자**(**nms:recipient**) 테이블을 선택합니다. 그 다음 **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다.
1. 선택:**[!UICONTROL Last name]**, **[!UICONTROL First name]**, **[!UICONTROL Email]**, **[!UICONTROL City]** 및 **[!UICONTROL Account number]**. 이러한 필드는 **[!UICONTROL Output columns]**&#x200B;에 추가됩니다. 그 다음 **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다.

   ![](assets/query_editor_03.png)

1. 열을 정렬하여 올바른 순서로 표시합니다. 여기서는 계정 번호를 내림차순으로 정렬하고 이름을 알파벳순으로 정렬하려고 합니다. 그 다음 **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다.

   ![](assets/query_editor_04.png)

1. **[!UICONTROL Data filtering]** 창에서 검색을 세분화합니다.**[!UICONTROL Filtering conditions]**&#x200B;을 선택하고 **[!UICONTROL Next]**&#x200B;를 클릭합니다.
1. **[!UICONTROL Target element]** 창에서 필터 설정을 입력할 수 있습니다.

   다음 필터 조건을 정의합니다.받는 사람: &quot;orange.co.uk&quot;과 같은 이메일 도메인을 가진 사람. 이렇게 하려면 **[!UICONTROL Expression]** 열에서 **이메일 도메인(@email)**&#x200B;을 선택하고 **[!UICONTROL Operator]** 열에서 **equal to**&#x200B;를 선택하고 **[!UICONTROL Value]** 열에 &quot;orange.co.uk&quot;을 입력합니다.

   ![](assets/query_editor_05.png)

1. 필요한 경우 **[!UICONTROL Distribution of values]** 단추를 클릭하여 잠재 고객의 이메일 도메인을 기반으로 배포를 봅니다. 데이터베이스의 각 이메일 도메인에 백분율을 사용할 수 있습니다. &quot;orange.co.uk&quot; 이외의 도메인은 필터가 적용될 때까지 표시됩니다.

   질의 요약이 창 하단에 표시됩니다.**이메일 도메인은 &#39;orange.co.uk&#39;**&#x200B;과(와) 같습니다.

1. 쿼리 결과에 대한 아이디어를 얻으려면 **[!UICONTROL Preview]**&#x200B;을 클릭합니다.&quot;orange.co.uk&quot; 이메일 도메인만 표시됩니다.

   ![](assets/query_editor_nveau_17.png)

1. 우리는 이제 런던에 거주하지 않는 연락처를 찾기 위해 질문을 바꿀 것이다.

   **[!UICONTROL Expression]** 열에서 **[!UICONTROL City (location/@city)]**&#x200B;을 선택하고 **[!UICONTROL different from]** 열에 **[!UICONTROL London]**&#x200B;을 입력합니다.**[!UICONTROL Value]**

   ![](assets/query_editor_08.png)

1. 그러면 **[!UICONTROL Data formatting]** 창으로 이동합니다. 열 순서를 확인합니다. &quot;City&quot; 열을 &quot;Account number&quot; 열 아래로 이동합니다.

   목록에서 제거하려면 &quot;이름&quot; 열의 선택을 취소합니다.

   ![](assets/query_editor_nveau_15.png)

1. **[!UICONTROL Data preview]** 창에서 **[!UICONTROL Start the preview of the data]**&#x200B;을 클릭합니다. 이 함수는 쿼리 결과를 계산합니다.

   **[!UICONTROL Column results]** 탭에는 쿼리 결과가 열에 표시됩니다.

   그 결과 런던에 거주하지 않는 &quot;orange.co.uk&quot; 이메일 도메인이 있는 모든 수신자가 표시됩니다. 이전 단계에서 선택 취소되어 &quot;이름&quot; 열이 표시되지 않습니다. 계정 번호는 내림차순으로 정렬됩니다.

   ![](assets/query_editor_nveau_12.png)

   **[!UICONTROL XML result]** 탭에는 XML 형식의 결과가 표시됩니다.

   ![](assets/query_editor_nveau_13.png)

   **[!UICONTROL Generated QSL queries]** 탭에는 SQL 형식의 쿼리 결과가 표시됩니다.

   ![](assets/query_editor_nveau_14.png)
