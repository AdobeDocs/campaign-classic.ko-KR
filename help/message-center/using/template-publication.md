---
solution: Campaign Classic
product: campaign
title: 템플릿 게시
description: 트랜잭션 메시지 템플릿 게시
audience: message-center
content-type: reference
topic-tags: message-templates
translation-type: tm+mt
source-git-commit: 02dee9c4cc03784ccc20f147f816798248bd10f2
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 2%

---


# 템플릿 게시{#template-publication}

제어 인스턴스에서 만든 메시지 템플릿이 완료되면 게시할 수 있습니다. 이 프로세스에서는 모든 실행 인스턴스에도 게시됩니다.

[게시]를 사용하면 실행 인스턴스에 두 개의 메시지 템플릿을 자동으로 만들 수 있으며, 이를 통해 실시간 및 일괄 처리 이벤트에 연결된 메시지를 보낼 수 있습니다.

>[!NOTE]
>
>트랜잭션 메시지 템플릿을 게시할 때 유형 규칙도 실행 인스턴스에도 자동으로 게시됩니다.

>[!IMPORTANT]
>
>템플릿을 변경할 때마다 트랜잭션 메시지 배달 중에 이러한 변경 사항이 적용되도록 템플릿을 다시 게시해야 합니다.

1. 제어 인스턴스에서 트리의 **[!UICONTROL Message Center > Transactional message templates]** 폴더로 이동합니다.
1. 실행 인스턴스에 게시할 템플릿을 선택합니다.
1. **[!UICONTROL Publish]**&#x200B;을(를) 클릭합니다.

   ![](assets/messagecenter_publish_model_008.png)

게시를 완료하면 일괄 처리에 적용할 메시지 템플릿과 실시간 유형 이벤트가 모두 **[!UICONTROL Administration > Production > Message Center Execution> Default > Transactional message templates]** 폴더의 프로덕션 인스턴스 트리에 생성됩니다.

![](assets/messagecenter_deployed_model_001.png)

템플릿이 게시되면 해당 이벤트가 트리거되면 실행 인스턴스가 이벤트를 수신하고 이를 거래 템플릿에 연결하여 각 수신자에게 해당 트랜잭션 메시지를 전송합니다.

>[!NOTE]
>
>보낸 사람 주소와 같은 트랜잭션 메시지 템플릿의 기존 필드를 빈 값으로 바꾸면 트랜잭션 메시지가 다시 게시되면 실행 인스턴스의 해당 필드가 업데이트되지 않습니다. 이전 값이 여전히 포함됩니다.
>
>그러나 비어 있지 않은 값을 추가하는 경우 다음 게시 후 해당 필드가 평소대로 업데이트됩니다.
