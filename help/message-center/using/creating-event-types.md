---
product: campaign
title: 이벤트 유형 만들기
description: Adobe Campaign Classic에서 전송하려는 트랜잭션 메시지와 일치하는 이벤트 유형을 만드는 방법을 알아봅니다.
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 98b7c827-f31d-46a6-a28d-40a78a4b4248
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 3%

---

# 이벤트 유형 만들기 {#creating-event-types}

![](../../assets/v7-only.svg)

각 이벤트를 개인화된 메시지로 변경할 수 있도록 먼저 다음을 만들어야 합니다 **이벤트 유형**.

When [메시지 템플릿 만들기](../../message-center/using/creating-the-message-template.md)을 지정하면 전송할 메시지와 일치하는 이벤트 유형을 선택합니다.

>[!IMPORTANT]
>
>이벤트 유형을 메시지 템플릿에서 사용하기 전에 만들어야 합니다.

Adobe Campaign에서 처리할 이벤트 유형을 만들려면 아래 단계를 수행하십시오.

1. 에 로그인합니다. **제어 인스턴스**.

1. 로 이동합니다. **[!UICONTROL Administration > Platform > Enumerations]** 트리의 폴더.

1. 선택 **[!UICONTROL Event type]** 참조하십시오.

1. 클릭 **[!UICONTROL Add]** 열거형 값을 만들려면 주문 확인, 암호 변경, 주문 전달 변경 등이 가능합니다.

   ![](assets/messagecenter_eventtype_enum_001.png)

   >[!IMPORTANT]
   >
   >각 이벤트 유형은 **[!UICONTROL Event type]** 열거형.

1. 항목별 목록 값이 만들어지면 작성이 유효하도록 인스턴스에 로그오프했다가 다시 로그온합니다.

>[!NOTE]
>
>의 항목별 목록에 대해 자세히 알아보십시오 [열거형 관리](../../platform/using/managing-enumerations.md).


