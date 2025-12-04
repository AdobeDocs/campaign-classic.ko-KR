---
product: campaign
title: 이모티콘 목록 사용자 정의
description: Adobe Campaign 사용 시 이모티콘 목록을 사용자 지정하는 방법 알아보기
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Email, Push
role: User, Developer
hide: true
hidefromtoc: true
exl-id: b8642df3-1960-4f2c-8273-c3988a3e85f0
source-git-commit: 17ac1e0d68d2945b01aecc7c45fc5be7e6bd38af
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 3%

---

# 이모티콘 목록 사용자 정의 {#customize-emoticons}

팝업에 표시되는 이모티콘 목록은 열거형에 의해 제어되며, 열거형을 통해 목록에 값을 표시하여 사용자가 지정된 필드에 대해 선택할 수 있는 사항을 제한할 수 있습니다.
이모티콘 목록 순서는 사용자 지정할 수 있으며, 목록에 다른 이모티콘을 추가할 수도 있습니다.

이모티콘은 이메일 및 푸시에만 사용할 수 있습니다. 자세한 내용은 [Campaign v8 설명서](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-the-email-content.html#inserting-emoticons){target="_blank"}를 참조하세요.


## 새 이모티콘 추가 {#add-new-emoticon}

>[!CAUTION]
>
>이모티콘 목록은 81개를 초과하는 항목을 표시할 수 없습니다.

1. 이 [페이지](https://unicode.org/emoji/charts/full-emoji-list.html)에서 추가할 새 이모티콘을 선택하세요. 브라우저 및 OS와 같은 다양한 플랫폼과 호환되어야 합니다.

1. **[!UICONTROL Explorer]**&#x200B;에서 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Enumerations]**&#x200B;을(를) 선택하고 **[!UICONTROL Emoticon list]** 기본 열거형을 클릭합니다.

   >[!NOTE]
   >
   >기본 열거형은 Adobe Campaign Classic 콘솔의 관리자만 관리할 수 있습니다.

   ![](assets/emoticon_1.png)

1. **[!UICONTROL Add]**&#x200B;을(를) 클릭합니다.

1. 다음 필드를 채웁니다.

   * **[!UICONTROL U+]**: 새 이모티콘 코드. 이 [페이지](https://unicode.org/emoji/charts/full-emoji-list.html)에서 이모티콘 코드 목록을 찾을 수 있습니다.
호환성 문제를 방지하기 위해 브라우저 및 모든 운영 체제에서 지원되는 이모티콘을 선택하는 것이 좋습니다.

   * **[!UICONTROL Label]**: 새 이모티콘 레이블.

   ![](assets/emoticon_5.png)

1. 구성이 완료되면 **[!UICONTROL Ok]**&#x200B;을(를) 클릭한 다음 **[!UICONTROL Save]**&#x200B;을(를) 클릭합니다.
새 이모티콘이 스토어에 자동으로 삽입됩니다.

1. 게재의 **[!UICONTROL Insert emoticon]** 창에 표시하려면 새로 만든 이모티콘을 두 번 클릭하여 선택합니다.

1. **[!UICONTROL Display order]** 드롭다운에서 새 이모티콘이 표시되는 순서를 선택하십시오. 이미 할당된 표시 순서를 선택하면 기존 이모티콘이 자동으로 스토어로 이동됩니다.

   <br>이 예제에서 표시 순서 번호 61을 선택했습니다. 즉, 항목에 이미 이 순서가 있는 경우 자동으로 저장소로 이동되고 새 항목이 열거형 목록에 배치됩니다.

   ![](assets/emoticon_2.png)

1. 이제 새 이모티콘이 **[!UICONTROL Insert emoticon list]** 기본 제공 열거형에 추가되었습니다. 언제든지 **[!UICONTROL Display order]**&#x200B;을(를) 변경하거나 더 이상 필요하지 않은 경우 스토어로 이동할 수 있습니다.

1. 변경 사항을 고려하려면 연결을 끊고 Adobe Campaign Classic에서 다시 연결합니다. 새 이모티콘이 **[!UICONTROL Insert emoticon]** 팝업 창에 계속 나타나지 않으면 캐시를 지워야 할 수도 있습니다. 자세한 정보는 이 [섹션](../../platform/using/faq-campaign-classic-v7.md#how-do-i-clear-console-cache)을 참조하십시오.

1. 이제 이전 단계에서 구성한 대로 61번째 위치의 **[!UICONTROL Insert emoticon]** 팝업 창에서 게재에서 새 이모티콘을 찾을 수 있습니다. 게재에서 이모티콘을 사용하는 방법에 대한 자세한 내용은 [Campaign v8 설명서](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-the-email-content.html#inserting-emoticons){target="_blank"}를 참조하세요.

   ![](assets/emoticon_4.png)

1. **[!UICONTROL Insert emoticon]** 팝업 창에 다음 이모티콘이 나타나면 해당 이모티콘이 올바르게 구성되지 않은 것입니다. **[!UICONTROL U+]**&#x200B;에서 **[!UICONTROL Display order]** 코드 또는 **[!UICONTROL Emoticon list]**&#x200B;이(가) 올바른지 확인하십시오.

   ![](assets/emoticon_6.png)
