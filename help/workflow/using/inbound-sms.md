---
product: campaign
title: 인바운드 SMS
description: 인바운드 SMS 워크플로우 활동에 대해 자세히 알아보십시오
audience: workflow
content-type: reference
topic-tags: event-activities
exl-id: 94a9d50b-4ead-4815-8d12-942fa78b4e8a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 4%

---

# 인바운드 SMS{#inbound-sms}

![](../../assets/common.svg)

**인바운드 SMS** 활동을 사용하면 외부 계정에서 텍스트 메시지를 다운로드하고 처리할 수 있습니다.

## 속성 {#properties}

![](assets/sms_rec_edit.png)

**인바운드 SMS** 활동의 첫 번째 탭에서는 SMS 메시지의 라우팅 매개 변수를 입력하고 각 메시지를 받을 때 실행할 스크립트를 입력할 수 있습니다. 두 번째 탭에서는 활동에 예약을 할당할 수 있으며, 세 번째 탭에서는 활동의 만료 조건을 정의합니다.

1. **[!UICONTROL SMS routing]**: SMS 복구에 사용할 외부 계정을 선택합니다. 외부 계정은 트리의 **[!UICONTROL Administration > Platform > External accounts]** 노드를 통해 구성됩니다.
1. **[!UICONTROL Script]**
1. **[!UICONTROL Schedule]**

   ![](assets/sms_rec_edit_2.png)

1. **[!UICONTROL Expiration]**

**[!UICONTROL Script]**, **[!UICONTROL Schedule]** 및 **[!UICONTROL Expiry]** 탭은 [인바운드 전자 메일](inbound-emails.md)에 자세히 설명되어 있습니다.
