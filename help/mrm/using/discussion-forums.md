---
product: campaign
title: 토론 포럼
description: Campaign 토론 포럼 사용 방법 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: campaign
content-type: reference
topic-tags: tasks--resources-and-budgets
exl-id: 222853c5-c754-4c0b-8ee4-a64b2f8677a4
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 0%

---

# 토론 포럼{#discussion-forums}



Adobe Campaign 운영자는 토론 포럼을 사용하여 정보를 공유할 수 있습니다. 계획, 프로그램, 캠페인, 리소스, 시뮬레이션, 재고 요소에는 각각 고유한 포럼이 있습니다. 각 연산자에는 개인 포럼도 있습니다. 모든 토론은 개인적인 토론회에서도 공개적입니다.

운영자는 포럼에 가입하여 메시지가 게시될 때마다 알림 이메일을 받을 수 있습니다.

## 포럼 액세스 {#accessing-a-forum}

캠페인, 운영자 등의 포럼을 방문하려면 대시보드로 이동하여 **[!UICONTROL Forum]** 오른쪽 상단 모서리에 있는 링크 이 링크는 포럼에 있는 총 메시지 수도 제공합니다.

![](assets/mrm_forum_access_link.png)

## 포럼 사용 {#using-a-forum}

메시지와 해당 응답은 시간 순서대로 표시됩니다(최신 항목부터 오래된 항목까지).

메시지의 내용을 표시하려면 해당 헤더를 클릭합니다.

![](assets/mrm_forum_expand_msg.png)

**새 토론 시작**

새 토론을 시작하려면 **[!UICONTROL Add a discussion]** 단추를 클릭합니다. 다음 **[!UICONTROL Discussion forum]** 상자가 표시됩니다(아래 참조).

![](assets/mrm_forum_new_thread.png)

**기존 토론에 메시지 게시**

기존 토론에 메시지를 게시하려면 답변할 메시지를 연 다음 **[!UICONTROL Reply]** 왼쪽 상단 모서리에 있는 링크. 다음 **[!UICONTROL Discussion forum]** 상자가 표시됩니다(아래 참조).

![](assets/mrm_forum_answer_msg.png)

메시지에 회신하면 원래 메시지를 게시한 사람에게 알림이 전송됩니다.

**메시지 작성**

다음에서 **[!UICONTROL Discussion forum]** 상자:

1. 에 텍스트를 입력하십시오. **[!UICONTROL Message]** 필드 및 토론 제목 **[!UICONTROL Subject]** 필드.

   ![](assets/mrm_forum_edit_msg.png)

1. 필요한 경우:

   * 포럼을 구독하지 않은 사람이 토론에 참여하도록 하려면 **[!UICONTROL Operator to notify]** 필드. 운영자는 이 특정 메시지에 대한 알림 이메일을 수신하게 됩니다(포럼 가입이 아님). 여러 연산자에게 알리려면 연산자 그룹을 선택합니다.
   * 메시지에 첨부 파일을 추가하려면 **[!UICONTROL Browse]**. 첨부 파일도 알림 이메일에 포함됩니다. 첨부 파일은 개별적으로 보낼 수만 있습니다. 여러 파일을 보내려면 압축해야 합니다.

1. 클릭 **[!UICONTROL Create the message]** 포럼에 게시합니다.

>[!NOTE]
>
>메시지가 포럼에 게시되면 더 이상 변경하거나 삭제할 수 없습니다.

## 운영자의 개인 포럼에 게시 {#posting-to-the-personal-forum-of-an-operator}

예를 들어 메시지가 특정 캠페인과 관련이 없지만 Adobe Campaign에서 대화를 추적하려는 경우 운영자의 포럼에 메시지를 게시할 수 있습니다. 개인 포럼은 공개되며 모든 운영자가 귀하의 메시지를 볼 수 있습니다. 운영자는 누군가 개인 포럼에 게시할 때마다 메시지를 수신합니다.

운영자의 포럼에 액세스하려면:

* 에 액세스하는 데 필요한 권한이 있는 경우 **[!UICONTROL Administration > Access management > Operators]** 탐색기의 노드에서 원하는 연산자의 대시보드를 열고 **[!UICONTROL Forum]** 오른쪽 상단 모서리에 있는 링크
* 그렇지 않은 경우 Adobe Campaign에서 연산자 이름을 찾고(이 운영자가 포럼에 게시한 메시지, 할당 중인 작업) 이를 클릭하여 대시보드에 액세스합니다. 관리자에게 연산자 폴더 보기를 만들도록 요청할 수도 있습니다.

## 포럼 구독 {#subscribing-to-a-forum}

포럼에 가입하면 토론을 따를 수 있습니다. 포럼에 메시지가 게시될 때마다 이메일 알림을 받게 됩니다. 이 이메일에는 메시지 본문과 첨부 파일이 포함됩니다. 메시지에 응답하려면 이메일 본문을 클릭한 다음 Adobe Campaign 웹 인터페이스에 로그인합니다. 포럼에 가입하면 모든 사용자가 이 정보를 볼 수 있습니다.

* 포럼에 가입하려면 **[!UICONTROL Follow discussions]** 메시지 목록 위에 있는 오른쪽 상단 섹션의 단추입니다.

   ![](assets/mrm_forum_subscribe.png)

   섹션이 파란색으로 바뀌고 포럼에 가입했음을 보여 줍니다.

* 포럼에서 가입을 해지하려면 **[!UICONTROL Unsubscribe]** 단추를 클릭합니다.

   ![](assets/mrm_forum_unsubscribe.png)

* 개인 대시보드에는 구독 중인 포럼이 나열됩니다. 다음을 클릭합니다. **[!UICONTROL Subscription to discussion forums]** 링크를 클릭하여 목록을 표시한 다음, 원하는 항목을 클릭하여 해당 포럼에 액세스합니다.

   ![](assets/platform_dashboard_operator_subscr_forums.png)

   개인 대시보드에 대한 자세한 내용은 [이 섹션](../../platform/using/access-management-operators.md).

* 포럼을 구독하는 사용자를 보려면 **[!UICONTROL List of subscribers to this discussion forum]** 메시지 목록 위에 연결합니다.

   ![](assets/mrm_forum_subscribers.png)

## 알림 게재 확인 {#checking-notification-delivery}

포럼을 구독한 운영자가 예상대로 알림을 받지 못하는 경우:

* 운영자의 프로필에 이메일 주소를 입력했는지 확인합니다.
* 로 이동 **[!UICONTROL Administration > Production > Technical workflows > Campaign processes]** 노드 및 다음을 확인합니다. **[!UICONTROL Jobs in discussion forums]** 워크플로가 시작되었으며 오류가 없습니다.
* 게재 로그 보기:

   * Adobe Campaign 홈페이지에서 **[!UICONTROL Campaigns > Navigation > Deliveries]**&#x200B;을(를) 열고 **[!UICONTROL Discussion forum notification]** 게재.
   * 탐색기에서 **[!UICONTROL Administration > Production > Objects created automatically > Technical deliveries > Workflow notifications]**&#x200B;을 클릭한 다음 을 클릭합니다 **[!UICONTROL Discussion forum notifications]**.
   다음에서 **[!UICONTROL Discussion forum notifications]** 상자에서 게재 로그는 **[!UICONTROL Edit > Delivery]** 탭. 다음을 볼 수도 있습니다. **[!UICONTROL Tracking > Log]** 및 **[!UICONTROL Exclusion causes]** 탭.
