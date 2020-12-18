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

팝업에 표시되는 이모티콘 목록은 지정된 필드에 대한 사용자의 선택을 제한하기 위해 목록에 값을 표시할 수 있는 열거형에 의해 결정됩니다.
이모티콘 목록 순서를 사용자 정의할 수 있고 다른 이모티콘을 목록에 추가할 수도 있습니다.
이모티콘은 이메일에 대해 사용할 수 있으며 푸시에 대한 자세한 내용은 이 [page](../../delivery/using/defining-the-email-content.md#inserting-emoticons)을 참조하십시오.

## 새 이모티콘 {#add-new-emoticon} 추가

>[!CAUTION]
>
>이모티콘 목록은 81개 이상의 항목을 표시할 수 없습니다.

1. 이 [페이지](https://unicode.org/emoji/charts/full-emoji-list.html)에서 추가할 새 이모티콘을 선택합니다. 브라우저 및 OS와 같은 다양한 플랫폼과 호환되어야 합니다.

1. **[!UICONTROL Explorer]**&#x200B;에서 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Enumerations]**&#x200B;을 선택하고 **[!UICONTROL Emoticon list]** 바로 사용 가능한 열거형을 클릭합니다.

   >[!NOTE]
   >
   >기본 열거형은 Adobe Campaign Classic 콘솔의 관리자만 관리할 수 있습니다.

   ![](assets/emoticon_1.png)

1. **[!UICONTROL Add]**&#x200B;을(를) 클릭합니다.

1. 필드를 채웁니다.

   * **[!UICONTROL U+]**:새로운 이모티콘 코드. 이 [페이지](https://unicode.org/emoji/charts/full-emoji-list.html)에서 이모티콘 코드 목록을 찾을 수 있습니다.
호환성 문제를 방지하기 위해 브라우저와 모든 운영 체제에서 지원되는 이모티콘을 선택할 것을 권장합니다.

   * **[!UICONTROL Label]**:새 이모티콘의 레이블.

   ![](assets/emoticon_5.png)

1. 구성이 완료되면 **[!UICONTROL Ok]**&#x200B;을 클릭한 다음 **[!UICONTROL Save]** 를 클릭합니다.
새 이모티콘이 스토어에 자동으로 배치됩니다.

1. 게재의 **[!UICONTROL Insert emoticon]** 창에 표시하려면 새로 만든 이모티콘을 두 번 클릭하여 선택합니다.

1. **[!UICONTROL Display order]** 드롭다운에서 새 이모티콘이 표시되는 순서를 선택합니다. 이미 할당된 표시 순서를 선택하면 기존 이모티콘이 스토어로 자동으로 이동됩니다.

   <br>이 예제에서는 표시 순서 번호 61을 선택했습니다. 즉, 이 순서가 있는 항목이 이미 스토어로 이동되면 새 항목이 열거형 목록에 나타납니다.

   ![](assets/emoticon_2.png)

1. 이제 새 이모티콘이 **[!UICONTROL Insert emoticon list]** 바로 사용 가능한 열거에 추가되었습니다. 언제든지 **[!UICONTROL Display order]**&#x200B;을 변경하거나 더 이상 필요하지 않은 경우 스토어로 이동할 수 있습니다.

1. 변경 사항을 고려하려면, 연결을 해제한 다음 Adobe Campaign Classic에서 다시 연결하십시오. 새 이모티콘이 여전히 **[!UICONTROL Insert emoticon]** 팝업 창에 표시되지 않으면 캐시를 지워야 할 수 있습니다. 자세한 정보는 이 [섹션](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear)을 참조하십시오.

1. 이제 새 이모티콘은 이전 단계에 구성된 것처럼 61번째 위치의 **[!UICONTROL Insert emoticon]** 팝업 창의 배달에서 찾을 수 있습니다. 배달에서 이모티콘을 사용하는 방법에 대한 자세한 내용은 이 [페이지](../../delivery/using/defining-the-email-content.md#inserting-emoticons)를 참조하십시오.

   ![](assets/emoticon_4.png)

1. 다음 이모티콘이 **[!UICONTROL Insert emoticon]** 팝업 창에 표시되는 경우 이 이모티콘이 올바르게 구성되지 않았음을 의미합니다. **[!UICONTROL U+]** 코드나 **[!UICONTROL Display order]** 코드가 **[!UICONTROL Emoticon list]**&#x200B;에서 올바른지 확인하십시오.

   ![](assets/emoticon_6.png)
