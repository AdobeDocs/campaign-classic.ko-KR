---
solution: Campaign Classic
product: campaign
title: 중복 수신자 필터링
description: 복제된 받는 사람을 필터링하는 방법 살펴보기
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 4%

---


# 중복 수신자 필터링 {#filtering-duplicated-recipients}

이 예에서는 중복되는 프로파일을 복구하기 위해 게재에 두 번 이상 나타나는 수신자를 필터링하려고 합니다.

이 예제를 만들려면 다음 단계를 수행하십시오.

1. 워크플로우에서 **[!UICONTROL Query]** 활동을 드래그하여 놓고 활동을 엽니다.
1. 타겟 및 필터링 차원 **[!UICONTROL Edit query]** 을 클릭하고 설정합니다 **[!UICONTROL Recipients]**.

   ![](assets/query_recipients_1.png)

1. 다음 필터 조건을 정의하여 배달 로그에 있는 수신자를 타깃팅합니다. 표현식 **열에서** 수신자 배달 로그(브로드로그) **를** 선택하고 OperatorTownl 열과 같이 **** 존재함을 **** 선택합니다.

   ![](assets/query_recipients_2.png)

1. 다음 필터 조건을 정의하여 배달을 타게팅합니다. 표현식 열 **[!UICONTROL Internal name]** 과 연산자 열에서 **[!UICONTROL equal to]** 선택합니다.
1. 값 열에서 타깃팅된 게재의 내부 이름을 추가합니다.

   ![](assets/query_recipients_3.png)

1. 연산자가 있는 경우 동일한 작업을 반복하여 다른 배달을 타깃팅합니다. **[!UICONTROL AND]**

   ![](assets/query_recipients_4.png)

아웃바운드 전환에는 배달에서 타깃팅된 중복 받는 사람이 포함됩니다.
