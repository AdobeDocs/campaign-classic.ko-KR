---
product: campaign
title: 생일 이메일 보내기
description: 워크플로우로 생일 이메일을 보내는 방법 알아보기
feature: Workflows
exl-id: 38006cca-e945-4b9d-8e2d-ed537b8541d9
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '878'
ht-degree: 2%

---

# 생일 이메일 보내기{#sending-a-birthday-email}



## 소개 {#introduction}

이 사용 사례에서는 생일 당일 수신자 목록에 반복 이메일 전송을 계획하는 방법을 제공합니다.

이 사용 사례를 설정하기 위해 다음과 같은 타겟팅 워크플로우를 만들었습니다.

![](assets/birthday-workflow_usecase_1.png)

이 (일일 실행) 워크플로우는 현재 날짜에 생일이 있는 모든 수신자를 선택합니다.

![](assets/do-not-localize/how-to-video.png) 이 사용 사례는 비디오 형식에서도 찾을 수 있습니다. 자세한 내용은 [워크플로 만들기](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/automating-with-workflows/creating-a-workflow.html) 비디오를 참조하십시오.

이렇게 하려면 캠페인을 만들고 **[!UICONTROL Targeting and workflows]** 탭을 클릭하십시오. 자세한 내용은 [워크플로우에서 기본 대상 만들기](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow) 섹션을 참조하십시오.

그런 다음 다음 다음 단계를 수행합니다.

## 전송 예약 {#configuring-the-scheduler}

1. 먼저 매일 게재 전송을 트리거할 **스케줄러**&#x200B;를 추가하십시오. 아래 예에서는 게재가 매일 오전 6시에 생성됩니다.

   ![](assets/recur_delivery2.png)


## 생일이 다음과 같은 수신자 식별 {#identifying-recipients-whose-birthday-it-is}

워크플로우가 매일 시작되도록 **[!UICONTROL Scheduler]** 활동을 구성한 후 생년월일이 현재 날짜와 동일한 모든 수신자를 식별합니다.

그렇게 하려면 다음 단계를 적용합니다.

1. **[!UICONTROL Query]** 활동을 워크플로우에 끌어다 놓고 두 번 클릭합니다.
1. **쿼리 편집** 링크를 클릭하고 **[!UICONTROL Filtering conditions]**&#x200B;을(를) 선택합니다.

   ![](assets/s_ncs_user_create_exp_exple00.png)

1. **[!UICONTROL Expression]** 열의 첫 번째 셀을 클릭하고 **[!UICONTROL Edit expression]**&#x200B;을(를) 클릭하여 표현식 편집기를 엽니다.

   ![](assets/s_ncs_user_create_exp_exple.png)

1. 필터링 모드를 선택하려면 **[!UICONTROL Advanced selection]**&#x200B;을(를) 클릭하십시오.

   ![](assets/s_ncs_user_create_exp_exple_a.png)

1. 표현식 편집기를 표시하려면 **[!UICONTROL Edit the formula using an expression]**&#x200B;을(를) 선택하고 **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다.
1. 함수 목록에서 **[!UICONTROL Date]** 노드를 통해 액세스할 수 있는 **[!UICONTROL Day]**&#x200B;을(를) 두 번 클릭합니다. 이 함수는 매개 변수로 전달된 날짜에 해당하는 일을 나타내는 숫자를 반환합니다.

   ![](assets/s_ncs_user_create_exp_exple01.png)

1. 사용 가능한 필드 목록에서 **[!UICONTROL Birth date]**&#x200B;을(를) 두 번 클릭합니다. 그런 다음 편집기의 상단 섹션에 다음 수식이 표시됩니다.

   ```
   Day(@birthDate)
   ```

   **[!UICONTROL Finish]**&#x200B;을(를) 클릭하여 확인합니다.

1. 쿼리 편집기의 **[!UICONTROL Operator]** 열의 첫 번째 셀에서 **[!UICONTROL equal to]**&#x200B;을(를) 선택합니다.

   ![](assets/s_ncs_user_create_exp_exple02.png)

1. 그런 다음 두 번째 열(**[!UICONTROL Value]**)의 첫 번째 셀을 클릭하고 **[!UICONTROL Edit expression]**&#x200B;을 클릭하여 식 편집기를 엽니다.
1. 함수 목록에서 **[!UICONTROL Date]** 노드를 통해 액세스할 수 있는 **[!UICONTROL Day]**&#x200B;을(를) 두 번 클릭합니다.
1. 현재 날짜를 검색하려면 **[!UICONTROL GetDate]** 함수를 두 번 클릭하십시오.

   ![](assets/s_ncs_user_create_exp_exple04.png)

   편집기의 상단 섹션에는 다음 수식이 표시됩니다.

   ```
   Day(GetDate())
   ```

   **[!UICONTROL Finish]**&#x200B;을(를) 클릭하여 확인합니다.

1. 이 절차를 반복하여 현재 달에 해당하는 출생월을 검색합니다. 이렇게 하려면 **[!UICONTROL Add]** 단추를 클릭하고 3단계부터 10단계까지 반복하여 **[!UICONTROL Day]**&#x200B;을(를) **[!UICONTROL Month]**(으)로 바꿉니다.

   전체 쿼리는 다음과 같습니다.

   ![](assets/s_ncs_user_create_exp_exple03.png)

**[!UICONTROL Query]** 활동 결과를 **[!UICONTROL Email delivery]** 활동에 연결하여 생일에 받는 사람 목록으로 전자 메일을 보냅니다.

## 2월 29일에 태어난 수신자 포함(선택 사항) {#including-recipients-born-on-february-29th--optional-}

2월 29일에 태어난 모든 수신자를 포함하려는 경우 이 사용 사례에서는 윤년이든 아니든 생일에 대한 수신자 목록에 반복 이메일을 보내는 방법을 제시합니다.

이 사용 사례의 주요 구현 단계는 다음과 같습니다.

* 수신자 선택
* 윤년인지 여부 선택
* 2월 29일에 태어난 수신자 선택

이 사용 사례를 설정하기 위해 다음과 같은 타겟팅 워크플로우를 만들었습니다.



현재 연도 **이(가) 윤년이 아님**&#x200B;이고 워크플로우가 3월 1일에 실행되는 경우 어제(2월 29일) 생일이 있었던 모든 수신자를 선택하고 수신자 목록에 추가해야 합니다. 다른 경우에는 추가 작업이 필요하지 않습니다.

### 1단계: 수신자 선택 {#step-1--selecting-the-recipients}

워크플로우가 매일 시작되도록 **[!UICONTROL Scheduler]** 활동을 구성한 후에는 기념일이 현재 일인 모든 수신자를 식별합니다.

>[!NOTE]
>
>당해 연도가 윤년이면 2월 29일에 출생한 수급자 전원이 자동 포함된다.

![](assets/birthday-workflow_usecase_2.png)

생일이 현재 날짜에 해당하는 수신자를 선택하면 [생일이 현재 날짜인 수신자 식별](#identifying-recipients-whose-birthday-it-is) 섹션에 표시됩니다.

### 2단계: 윤년인지 여부 선택 {#step-2--select-whether-or-not-it-is-a-leap-year}

**[!UICONTROL Test]** 활동을 통해 윤년인지 여부와 현재 날짜가 3월 1일인지를 확인할 수 있습니다.

테스트가 확인되면(연도가 윤년이 아니고 - 2월 29일이 없으며 - 현재 날짜가 실제로 3월 1일) **[!UICONTROL True]** 전환이 활성화되고 2월 29일에 태어난 수신자가 3월 1일 게재에 추가됩니다. 그렇지 않으면 **[!UICONTROL False]** 전환이 활성화되며 현재 날짜에 태어난 받는 사람만 게재를 받습니다.

아래 코드를 복사하여 **[!UICONTROL Advanced]** 탭의 **[!UICONTROL Initialization script]** 섹션에 붙여넣습니다.

```
function isLeapYear(iYear)
{
    if(iYear/4 == Math.floor(iYear/4))
    {
        if(iYear/100 != Math.floor(iYear/100))
        {
            // Divisible by 4 only -> Leap Year
            return 1;
        }
        else
        {
            if(iYear/400 == Math.floor(iYear/400))
            {
                // Divisible by 4, 100 and 400 -> Leap year
                return 1;
            }
        }
    }
    // all others: no leap year
    return 0;
}

// Return today's date and time
var currentTime = new Date()
// returns the month (from 0 to 11)
var month = currentTime.getMonth() + 1
// returns the day of the month (from 1 to 31)
var day = currentTime.getDate()
// returns the year (four digits)
var year = currentTime.getFullYear()

// is current year a leap year?
vars.currentIsALeapYear = isLeapYear(year);

// is current date the first of march?
if(month == 3 && day == 1) {
  // today is 1st of march
vars.firstOfMarch = 1;
}
```

![](assets/birthday-workflow_usecase_3.png)

**[!UICONTROL Conditional forks]** 섹션에 다음 조건을 추가하십시오.

```
vars.currentIsALeapYear == 0 && vars.firstOfMarch == 1
```

![](assets/birthday-workflow_usecase_4.png)

### 3단계: 2월 29일에 태어난 수신자 선택 {#step-3--select-any-recipients-born-on-february-29th}

**[!UICONTROL Fork]** 활동을 만들고 아웃바운드 전환 중 하나를 **[!UICONTROL Query]** 활동에 연결합니다.

이 질의에서는 생년월일이 2월 29일인 모든 수신자를 선택합니다.

![](assets/birthday-workflow_usecase_5.png)

결과를 **[!UICONTROL Union]** 활동과 결합합니다.

두 **[!UICONTROL Test]** 활동 분기의 결과를 **[!UICONTROL Email delivery]** 활동에 연결하여 윤년이 아닌 해 동안 2월 29일에 태어난 모든 받는 사람(생일 기준)에게 전자 메일을 보냅니다.

## 반복 게재 만들기 {#creating-a-recurring-delivery-in-a-targeting-workflow}

보내려는 생일 전자 메일 템플릿을 기반으로 **반복 게재** 활동을 추가합니다.

>[!CAUTION]
>
>워크플로우를 실행하려면 Campaign 패키지와 관련된 기술 워크플로우를 시작해야 합니다. 자세한 내용은 [기술 워크플로우 목록](about-technical-workflows.md) 섹션을 참조하십시오.
>
>캠페인에 대해 승인 단계를 활성화한 경우 이러한 단계를 확인한 후에만 게재가 전송됩니다. 자세한 내용은 [승인할 프로세스 선택](../../campaign/using/marketing-campaign-approval.md#choosing-the-processes-to-be-approved) 섹션을 참조하세요.

![](assets/birthday-workflow_usecase_1.png)
