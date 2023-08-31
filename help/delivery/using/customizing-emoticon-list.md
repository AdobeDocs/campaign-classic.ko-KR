---
product: campaign
title: 이모티콘 목록 사용자 정의
description: Adobe Campaign 사용 시 이모티콘 목록을 사용자 지정하는 방법 알아보기
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Email, Push
role: User, Data Engineer
exl-id: b8642df3-1960-4f2c-8273-c3988a3e85f0
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 4%

---

# 이모티콘 목록 사용자 정의 {#customize-emoticons}

팝업에 표시되는 이모티콘 목록은 열거형에 의해 제어되며, 열거형을 통해 목록에 값을 표시하여 사용자가 지정된 필드에 대해 선택할 수 있는 사항을 제한할 수 있습니다.
이모티콘 목록 순서는 사용자 지정할 수 있으며, 목록에 다른 이모티콘을 추가할 수도 있습니다.
이메일에 이모티콘이 제공되고 이에 대한 자세한 내용을 푸시하려면 다음을 참조하세요. [페이지](defining-the-email-content.md#inserting-emoticons).

## 새 이모티콘 추가 {#add-new-emoticon}

>[!CAUTION]
>
>이모티콘 목록은 81개를 초과하는 항목을 표시할 수 없습니다.

1. 이 목록에서 추가할 새 이모티콘을 선택하십시오. [페이지](https://unicode.org/emoji/charts/full-emoji-list.html). 브라우저 및 OS와 같은 다양한 플랫폼과 호환되어야 합니다.

1. 다음에서 **[!UICONTROL Explorer]**, 선택 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Enumerations]** 을(를) 클릭하고 **[!UICONTROL Emoticon list]** 기본 열거형입니다.

   >[!NOTE]
   >
   >기본 열거형은 Adobe Campaign Classic 콘솔의 관리자만 관리할 수 있습니다.

   ![](assets/emoticon_1.png)

1. **[!UICONTROL Add]**&#x200B;를 클릭합니다.

1. 다음 필드를 채웁니다.

   * **[!UICONTROL U+]**: 새 이모티콘 코드. 이모티콘 코드 목록은 여기에서 찾을 수 있습니다 [페이지](https://unicode.org/emoji/charts/full-emoji-list.html).
호환성 문제를 방지하기 위해 브라우저 및 모든 운영 체제에서 지원되는 이모티콘을 선택하는 것이 좋습니다.

   * **[!UICONTROL Label]**: 새 이모티콘의 레이블입니다.

   ![](assets/emoticon_5.png)

1. 클릭 **[!UICONTROL Ok]** 그러면 **[!UICONTROL Save]** 구성이 완료되면.
새 이모티콘이 스토어에 자동으로 삽입됩니다.

1. 에 표시하려면 다음을 수행하십시오. **[!UICONTROL Insert emoticon]** 게재 창에서 새로 만든 이모티콘을 두 번 클릭하여 선택합니다.

1. 다음에서 선택: **[!UICONTROL Display order]** 드롭다운을 통해 새 이모티콘을 표시할 순서를 지정합니다. 이미 할당된 표시 순서를 선택하면 기존 이모티콘이 자동으로 스토어로 이동됩니다.

   <br>이 예에서는 표시 순서 번호 61을 선택했습니다. 즉, 항목에 이미 이 순서가 있는 경우 자동으로 저장소로 이동되고 새 항목이 열거 목록에 배치됩니다.

   ![](assets/emoticon_2.png)

1. 이제 새 이모티콘이 **[!UICONTROL Insert emoticon list]** 기본 열거형입니다. 변경할 수 있습니다. **[!UICONTROL Display order]** 언제든 필요하시거나 필요 없으시면 매장으로 옮기세요.

1. 변경 사항을 고려하려면 연결을 끊고 Adobe Campaign Classic에서 다시 연결합니다. 새 이모티콘이 여전히 **[!UICONTROL Insert emoticon]** 팝업 창에서 캐시를 지워야 할 수도 있습니다. 자세한 정보는 이 [섹션](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear)을 참조하십시오.

1. 이제 게재의 새 이모티콘을 찾을 수 있습니다. **[!UICONTROL Insert emoticon]** 이전 단계에서 구성한 대로 61번째 위치의 팝업 창. 게재에서 이모티콘을 사용하는 방법에 대한 자세한 내용은 다음을 참조하십시오. [페이지](defining-the-email-content.md#inserting-emoticons).

   ![](assets/emoticon_4.png)

1. 에 다음 이모티콘이 표시되는 경우 **[!UICONTROL Insert emoticon]** 팝업 창, 즉 제대로 구성되지 않았음을 의미합니다. 다음을 확인함: **[!UICONTROL U+]** 코드 또는 **[!UICONTROL Display order]** 이(가) 다음에서 올바릅니다. **[!UICONTROL Emoticon list]**.

   ![](assets/emoticon_6.png)
