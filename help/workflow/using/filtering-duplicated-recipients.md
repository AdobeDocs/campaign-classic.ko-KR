---
product: campaign
title: 중복 수신자 필터링
description: 중복 수신자를 필터링하는 방법을 알아봅니다
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: 7cbabbae-375f-4336-9afa-6356f37a79d0
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 4%

---

# 중복 수신자 필터링 {#filtering-duplicated-recipients}

![](../../assets/common.svg)

이 예제에서는 중복 프로필을 복구하기 위해 게재에 두 번 이상 표시되는 수신자를 필터링하려고 합니다.

이 예제를 만들려면 다음 단계를 적용합니다.

1. 워크플로우에 **[!UICONTROL Query]** 활동을 끌어다 놓고 활동을 엽니다.
1. **[!UICONTROL Edit query]** 을 클릭하고 대상 및 필터링 차원을 **[!UICONTROL Recipients]** 로 설정합니다.

   ![](assets/query_recipients_1.png)

1. 게재 로그에 있는 수신자를 타겟팅하려면 다음 필터 조건을 정의합니다. **수신자 배달 로그(broadlog)**&#x200B;를 **표현식** 열에서 **존재(예:**&#x200B;연산자&#x200B;**열)를 선택합니다.**

   ![](assets/query_recipients_2.png)

1. 게재를 타깃팅할 다음 필터 조건을 정의합니다. 표현식 열에서 **[!UICONTROL Internal name]** 을 선택하고 연산자 열에서 **[!UICONTROL equal to]** 를 선택합니다.
1. 값 열에서 타깃팅된 게재의 내부 이름을 추가합니다.

   ![](assets/query_recipients_3.png)

1. **[!UICONTROL AND]** 연산자로 동일한 작업을 반복하여 다른 게재를 타깃팅합니다.

   ![](assets/query_recipients_4.png)

아웃바운드 전환에는 게재에서 타겟팅한 중복 수신자가 포함되어 있습니다.
