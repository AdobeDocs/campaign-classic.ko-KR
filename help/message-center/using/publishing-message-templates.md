---
product: campaign
title: 메시지 템플릿 게시
description: Adobe Campaign Classic에서의 트랜잭션 메시지 템플릿 게시 및 게시 취소에 대해 알아봅니다.
feature: Transactional Messaging, Message Center, Templates
audience: message-center
content-type: reference
topic-tags: message-templates
exl-id: 1d55f42b-64bf-4b1f-a317-c1f7456aa5b3
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 2%

---

# 메시지 템플릿 게시 {#publishing-template-messages}



## 템플릿 게시 {#template-publication}

컨트롤 인스턴스에서 만든 [메시지 템플릿](../../message-center/using/creating-the-message-template.md)이(가) 완료되고 [테스트](../../message-center/using/testing-message-templates.md)를 마치면 게시할 수 있습니다. 이 프로세스는 모든 실행 인스턴스에도 게시합니다.

게시를 사용하면 실행 인스턴스에 **두 개의 메시지 템플릿**&#x200B;을 자동으로 만들 수 있으므로 **실시간 이벤트** 및 **일괄 처리 이벤트**&#x200B;에 연결된 메시지를 보낼 수 있습니다.

>[!NOTE]
>
>트랜잭션 메시지 템플릿을 게시할 때 유형화 규칙도 실행 인스턴스에 자동으로 게시됩니다.

>[!IMPORTANT]
>
>템플릿을 변경할 때마다 다시 게시하여 트랜잭션 메시지 게재 중에 이러한 변경 사항을 적용해야 합니다.

1. 컨트롤 인스턴스에서 트리의 **[!UICONTROL Message Center > Transactional message templates]** 폴더로 이동합니다.
1. 실행 인스턴스에 게시할 템플릿을 선택합니다.
1. **[!UICONTROL Publish]**&#x200B;를 클릭합니다.

   ![](assets/messagecenter_publish_model_008.png)

게시가 완료되면 일괄 처리에 적용할 메시지 템플릿과 실시간 유형 이벤트가 모두 **[!UICONTROL Administration > Production > Message Center Execution> Default > Transactional message templates]** 폴더의 프로덕션 인스턴스 트리에 만들어집니다.

![](assets/messagecenter_deployed_model_001.png)

템플릿이 게시되면 해당 이벤트가 트리거되면 실행 인스턴스가 이벤트를 수신하고 이를 트랜잭션 템플릿에 링크하며 각 수신자에게 해당 트랜잭션 메시지를 보냅니다. 자세한 내용은 [이벤트 처리](../../message-center/using/about-event-processing.md)를 참조하세요.

>[!NOTE]
>
>보낸 사람 주소와 같은 트랜잭션 메시지 템플릿의 기존 필드를 빈 값으로 바꾸는 경우 트랜잭션 메시지가 다시 게시되면 실행 인스턴스의 해당 필드가 업데이트되지 않습니다. 여전히 이전 값이 포함됩니다.
>
>그러나 비어 있지 않은 값을 추가하면 해당 필드는 다음 게시 이후에 평소대로 업데이트됩니다.

## 템플릿 게시 취소 {#template-unpublication}

메시지 템플릿이 실행 인스턴스에 게시되면 게시를 취소할 수 있습니다. 템플릿 게시 프로세스에 대한 자세한 내용은 [이 섹션](#template-publication)을(를) 참조하십시오.

* 실제로 해당 이벤트가 트리거된 경우에도 게시된 템플릿을 호출할 수 있습니다. 메시지 템플릿을 더 이상 사용하지 않는 경우에는 게시를 취소하는 것이 좋습니다. 이는 실수로 원치 않는 트랜잭션 메시지를 보내는 것을 방지하기 위해서입니다.

  예를 들어 크리스마스 캠페인에만 사용하는 메시지 템플릿을 게시했습니다. 크리스마스 기간이 끝난 후에 게시 취소하고 내년에 다시 게시할 수도 있습니다.

* 또한 **[!UICONTROL Published]** 상태의 트랜잭션 메시지 템플릿은 삭제할 수 없습니다. 먼저 게시를 취소해야 합니다.

>[!NOTE]
>
>이 기능은 Campaign 20.2 릴리스부터 사용할 수 있습니다.

트랜잭션 메시지 템플릿의 게시를 취소하려면 아래 단계를 따르십시오.

1. 컨트롤 인스턴스에서 트리의 **[!UICONTROL Message Center > Transactional message templates]** 폴더로 이동합니다.
1. 게시를 취소할 템플릿을 선택합니다.
1. **[!UICONTROL Unpublish]**&#x200B;를 클릭합니다.

   <!--1. Fill in the **[!UICONTROL Log of the process]** field.-->

1. **[!UICONTROL Start]**&#x200B;를 클릭합니다.

![](assets/message-center-unpublish.png)

트랜잭션 메시지 템플릿 상태가 **[!UICONTROL Published]**&#x200B;에서 **[!UICONTROL Being edited]**(으)로 다시 변경됩니다.

게시 취소가 완료되면:

* 두 메시지 템플릿(일괄 처리 및 실시간 유형 이벤트에 적용됨)이 모두 각 실행 인스턴스에서 삭제됩니다.

  이 ID는 **[!UICONTROL Administration > Production > Message Center Execution > Default > Transactional message templates]** 폴더에 더 이상 표시되지 않습니다([이 섹션](#template-publication) 참조).

* 템플릿이 게시 취소되면 컨트롤 인스턴스에서 삭제할 수 있습니다.

  이렇게 하려면 목록에서 선택한 다음 화면 오른쪽 상단의 **[!UICONTROL Delete]** 단추를 클릭합니다.
