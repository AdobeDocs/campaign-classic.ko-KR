---
solution: Campaign Classic
product: campaign
title: 이모티콘 목록 사용자 정의
description: Adobe Campaign Classic 사용 시 이모티콘 목록을 사용자 지정하는 방법을 알아봅니다.
audience: delivery
content-type: reference
topic-tags: sending-emails
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 3%

---


# 이모티콘 목록 사용자 정의 {#customize-emoticons}

팝업에 표시되는 이모티콘 목록은 지정된 필드에 대한 사용자의 선택을 제한하기 위해 목록에 값을 표시할 수 있는 열거형으로 결정됩니다.
이모티콘 목록 순서를 사용자 정의할 수 있고 다른 이모티콘을 목록에 추가할 수도 있습니다.
이메일에 이모티콘을 사용할 수 있으며 이 페이지에 대한 자세한 내용은 이 [페이지를 참조하십시오](../../delivery/using/defining-the-email-content.md#inserting-emoticons).

## 새 이모티콘 추가 {#add-new-emoticon}

>[!CAUTION]
>
>이모티콘 목록은 81개 이상의 항목을 표시할 수 없습니다.

1. 이 [페이지에서 추가할 새 이모티콘을 선택합니다](https://unicode.org/emoji/charts/full-emoji-list.html). 브라우저 및 OS와 같은 다양한 플랫폼과 호환되어야 합니다.

1. 에서 **[!UICONTROL Explorer]**> **[!UICONTROL Administration]** **[!UICONTROL Platform]** > **[!UICONTROL Enumerations]** 을 선택하고 기본 **[!UICONTROL Emoticon list]** 열거형을 클릭합니다.

   >[!NOTE]
   >
   >기본 열거형은 Adobe Campaign Classic 콘솔의 관리자만 관리할 수 있습니다.

   ![](assets/emoticon_1.png)

1. **[!UICONTROL Add]**&#x200B;을(를) 클릭합니다.

1. 필드를 채웁니다.

   * **[!UICONTROL U+]**:새로운 이모티콘 코드 이 [페이지에서 이모티콘 코드 목록을 찾을 수 있습니다](https://unicode.org/emoji/charts/full-emoji-list.html).
호환성 문제를 방지하려면 브라우저와 모든 운영 체제에서 지원되는 이모티콘을 선택하는 것이 좋습니다.

   * **[!UICONTROL Label]**:새 이모티콘 레이블

   ![](assets/emoticon_5.png)

1. 구성 **[!UICONTROL Ok]** 이 완료되면 을 **[!UICONTROL Save]** 클릭합니다.
새 이모티콘이 스토어에 자동으로 배치됩니다.

1. 게재 창에 표시하려면 새로 만든 이모티콘을 두 번 클릭하여 선택합니다. **[!UICONTROL Insert emoticon]**

1. 새 이모티콘 **[!UICONTROL Display order]** 이 표시되는 순서를 드롭다운 메뉴에서 선택합니다. 이미 할당된 표시 순서를 선택하면 기존 이모티콘이 스토어로 자동으로 이동됩니다.

   <br>이 예에서는 항목이 이미 이 주문을 받은 경우 스토어로 자동 이동되고 새로운 항목이 열거형 목록에 포함될 것임을 의미하는 표시 순서 번호 61을 선택했습니다.

   ![](assets/emoticon_2.png)

1. 이제 새로운 이모티콘이 기본 열거에 **[!UICONTROL Insert emoticon list]** 추가되었습니다. 더 이상 필요하지 않은 경우 언제든지 **[!UICONTROL Display order]** 변경하거나 스토어로 옮길 수 있습니다.

1. 변경 사항을 고려하려면, 연결을 끊고 Adobe Campaign Classic에서 다시 연결하십시오. 새 이모티콘이 **[!UICONTROL Insert emoticon]** 팝업 창에 표시되지 않으면 캐시를 지워야 할 수 있습니다. 자세한 정보는 이 [섹션](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear)을 참조하십시오.

1. 이제 이전 단계에 구성된 대로 61번째 위치의 **[!UICONTROL Insert emoticon]** 팝업 창의 배달에서 새 이모티콘을 찾을 수 있습니다. 배달에서 이모티콘을 사용하는 방법에 대한 자세한 내용은 이 [페이지를 참조하십시오](../../delivery/using/defining-the-email-content.md#inserting-emoticons).

   ![](assets/emoticon_4.png)

1. 다음 이모티콘이 **[!UICONTROL Insert emoticon]** 팝업 창에 나타나는 경우 이 이모티콘이 올바르게 구성되지 않았음을 의미합니다. 코드가 **[!UICONTROL U+]** 올바른지 또는 **[!UICONTROL Display order]** 에서 **[!UICONTROL Emoticon list]**&#x200B;확인하십시오.

   ![](assets/emoticon_6.png)
