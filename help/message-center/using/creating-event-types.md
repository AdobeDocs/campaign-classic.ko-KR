---
product: campaign
title: 이벤트 유형 만들기
description: Adobe Campaign Classic에서 전송하려는 트랜잭션 메시지와 일치하는 이벤트 유형을 만드는 방법을 알아봅니다.
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 98b7c827-f31d-46a6-a28d-40a78a4b4248
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 3%

---

# 이벤트 유형 만들기 {#creating-event-types}

각 이벤트를 개인화된 메시지로 변경하려면 먼저 **이벤트 유형**&#x200B;을 만들어야 합니다.

[메시지 템플릿을 만들 때](../../message-center/using/creating-the-message-template.md)전송할 메시지와 일치하는 이벤트 유형을 선택합니다.

>[!IMPORTANT]
>
>이벤트 유형을 메시지 템플릿에서 사용하기 전에 만들어야 합니다.

Adobe Campaign에서 처리할 이벤트 유형을 만들려면 아래 단계를 수행하십시오.

1. **컨트롤 인스턴스**&#x200B;에 로그온합니다.

1. 트리의 **[!UICONTROL Administration > Platform > Enumerations]** 폴더로 이동합니다.

1. 목록에서 **[!UICONTROL Event type]** 을 선택합니다.

1. **[!UICONTROL Add]** 을 클릭하여 열거형 값을 만듭니다. 주문 확인, 암호 변경, 주문 전달 변경 등이 가능합니다.

   ![](assets/messagecenter_eventtype_enum_001.png)

   >[!IMPORTANT]
   >
   >각 이벤트 유형은 **[!UICONTROL Event type]** 열거형의 값과 일치해야 합니다.

1. 항목별 목록 값이 만들어지면 작성이 유효하도록 인스턴스에 로그오프했다가 다시 로그온합니다.

>[!NOTE]
>
>[열거형 관리](../../platform/using/managing-enumerations.md)의 항목별 목록에 대해 자세히 알아보십시오.


