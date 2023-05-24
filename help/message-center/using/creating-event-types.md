---
product: campaign
title: 이벤트 유형 만들기
description: Adobe Campaign Classic에서 보낼 트랜잭션 메시지와 일치하는 이벤트 유형을 만드는 방법을 알아봅니다
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 98b7c827-f31d-46a6-a28d-40a78a4b4248
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 3%

---

# 이벤트 유형 만들기 {#creating-event-types}



각 이벤트를 개인화된 메시지로 변경하려면 먼저 다음을 만들어야 합니다 **이벤트 유형**.

날짜 [메시지 템플릿 만들기](../../message-center/using/creating-the-message-template.md)를 클릭하고, 보낼 메시지와 일치하는 이벤트 유형을 선택합니다.

>[!IMPORTANT]
>
>메시지 템플릿에서 이벤트 유형을 사용하려면 먼저 이벤트 유형을 만들어야 합니다.

Adobe Campaign에서 처리할 이벤트 유형을 만들려면 아래 단계를 수행합니다.

1. 에 로그온 **컨트롤 인스턴스**.

1. 로 이동 **[!UICONTROL Administration > Platform > Enumerations]** 트리의 폴더입니다.

1. 선택 **[!UICONTROL Event type]** 목록에서 삭제할 수 있습니다.

1. 클릭 **[!UICONTROL Add]** 열거형 값을 만듭니다. 주문 확인, 암호 변경, 주문 게재 변경 등이 될 수 있습니다.

   ![](assets/messagecenter_eventtype_enum_001.png)

   >[!IMPORTANT]
   >
   >각 이벤트 유형은 **[!UICONTROL Event type]** 열거형입니다.

1. 항목별 목록 값이 생성되면 로그오프한 후 인스턴스에 다시 로그온하여 생성을 유효화합니다.

>[!NOTE]
>
>의 항목별 목록에 대해 자세히 알아보기 [열거형 관리](../../platform/using/managing-enumerations.md).


