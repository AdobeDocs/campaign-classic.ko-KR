---
product: campaign
title: 중복 수신자 필터링
description: 중복 수신자를 필터링하는 방법 알아보기
feature: Workflows
exl-id: 7cbabbae-375f-4336-9afa-6356f37a79d0
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 4%

---

# 중복 수신자 필터링 {#filtering-duplicated-recipients}



이 예제에서는 중복 프로필을 복구하기 위해 게재에 두 번 이상 나타나는 수신자를 필터링하려고 합니다.

이 예제를 만들려면 다음 단계를 적용합니다.

1. 드래그 앤 드롭 **[!UICONTROL Query]** 워크플로우의 활동을 열고 활동을 엽니다.
1. 클릭 **[!UICONTROL Edit query]** 및 target 및 필터링 차원을 다음으로 설정 **[!UICONTROL Recipients]**.

   ![](assets/query_recipients_1.png)

1. 게재 로그에 존재하는 수신자를 타겟팅하려면 다음 필터 조건을 정의하십시오. 선택 **수신자 게재 로그(broadlog)** 다음에서 **표현식** 열, 선택 **다음과 같이 존재합니다.** 다음에서 **연산자** 열.

   ![](assets/query_recipients_2.png)

1. 게재를 타겟팅할 다음 필터 조건을 정의합니다. 선택 **[!UICONTROL Internal name]** 표현식 열 및 **[!UICONTROL equal to]** 연산자 열에서
1. 값 열에서 타겟팅된 게재의 내부 이름을 추가합니다.

   ![](assets/query_recipients_3.png)

1. 포함 **[!UICONTROL AND]** 연산자. 동일한 작업을 반복하여 다른 게재를 타깃팅합니다.

   ![](assets/query_recipients_4.png)

아웃바운드 전환에는 게재에서 타겟팅한 중복 수신자가 포함됩니다.
