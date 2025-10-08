---
product: campaign
title: 이벤트 유형 만들기
description: Adobe Campaign Classic에서 보낼 트랜잭션 메시지와 일치하는 이벤트 유형을 만드는 방법을 알아봅니다
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 98b7c827-f31d-46a6-a28d-40a78a4b4248
source-git-commit: 28279c6ec0eab7f914cf6107cd1ec1cebd05113d
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 3%

---

# 이벤트 유형 만들기 {#creating-event-types}



각 이벤트를 개인화된 메시지로 변경하려면 먼저 **이벤트 유형**&#x200B;을 만들어야 합니다.

[메시지 템플릿을 만들](../../message-center/using/creating-the-message-template.md) 때 보낼 메시지와 일치하는 이벤트 유형을 선택합니다.

>[!IMPORTANT]
>
>메시지 템플릿에서 이벤트 유형을 사용하려면 먼저 이벤트 유형을 만들어야 합니다.

Adobe Campaign에서 처리할 이벤트 유형을 만들려면 아래 단계를 수행합니다.

1. **컨트롤 인스턴스**&#x200B;에 로그온합니다.

1. 트리의 **[!UICONTROL Administration > Platform > Enumerations]** 폴더로 이동합니다.

1. 목록에서 **[!UICONTROL Event type]**&#x200B;을(를) 선택합니다.

1. 열거형 값을 만들려면 **[!UICONTROL Add]**&#x200B;을(를) 클릭합니다. 주문 확인, 암호 변경, 주문 게재 변경 등이 될 수 있습니다.

   ![](assets/messagecenter_eventtype_enum_001.png)

   >[!IMPORTANT]
   >
   >각 이벤트 형식은 **[!UICONTROL Event type]** 열거형의 값과 일치해야 합니다.

1. 항목별 목록 값이 생성되면 로그오프한 후 인스턴스에 다시 로그온하여 생성을 유효화합니다.

>[!NOTE]
>
>**Adobe Campaign v8(콘솔) 설명서**&#x200B;에서 [열거형으로 작업](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/config/settings/enumerations){target=_blank}하는 방법에 대해 자세히 알아보세요.



