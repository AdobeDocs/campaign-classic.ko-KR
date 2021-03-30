---
solution: Campaign Classic
product: campaign
title: Campaign을 사용하여 SMS 만들기
description: Campaign을 사용하여 SMS를 만드는 방법 살펴보기
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
translation-type: tm+mt
source-git-commit: 5a084ebe5295d19de24cf92c721d4692f0f5deb8
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 3%

---


# SMS 게재 만들기 {#creating-a-sms-delivery}

## 배달 채널 {#selecting-the-delivery-channel} 선택

새 SMS 배달을 만들려면 아래 절차를 따르십시오.

>[!NOTE]
>
>배달 생성에 대한 글로벌 개념은 [이 섹션](../../delivery/using/steps-about-delivery-creation-steps.md)에 있습니다.

1. 배달 대시보드와 같은 새 배달을 만듭니다.
1. 이전에 만든 배달 템플릿 **모바일로 전송(SMPP)**&#x200B;을 선택합니다. 자세한 내용은 [배달 템플릿 변경](sms-set-up.md#changing-the-delivery-template) 섹션을 참조하십시오.

   ![](assets/s_user_mobile_wizard.png)

1. 레이블, 코드 및 설명을 사용하여 배달을 식별합니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../delivery/using/steps-create-and-identify-the-delivery.md#identifying-the-delivery)을 참조하십시오.
1. 이 정보를 확인하고 메시지 구성 창을 표시하려면 **[!UICONTROL Continue]**&#x200B;을 클릭합니다.

## SMS 콘텐츠를 정의합니다 {#defining-the-sms-content}

SMS의 컨텐츠를 만들려면 아래 단계를 따르십시오.

1. 마법사의 **[!UICONTROL Text content]** 섹션에 메시지 내용을 입력합니다. 도구 모음 단추를 사용하여 내용을 가져오거나 저장 또는 검색할 수 있습니다. 마지막 단추는 개인화 필드를 삽입하는 데 사용됩니다.

   ![](assets/s_ncs_user_wizard_sms01_138.png)

   개인화 필드는 [개인화 정보](../../delivery/using/about-personalization.md) 섹션에 표시됩니다.

1. 페이지 하단에 있는 **[!UICONTROL Preview]**&#x200B;을 클릭하여 개인화로 메시지 렌더링을 표시합니다. 미리 보기를 시작하려면 도구 모음에서 **[!UICONTROL Test personalization]** 단추를 사용하여 수신자를 선택합니다. 정의된 타겟에서 수신자를 선택하거나 다른 수신자를 선택할 수 있습니다.

   ![](assets/s_ncs_user_wizard_sms01_139.png)

   SMS 메시지를 승인할 수 있습니다. 컨텐츠 편집기의 오른쪽에 표시되는 휴대폰 화면에서 SMS 컨텐츠를 볼 수도 있습니다. 화면을 클릭하고 마우스를 사용하여 내용을 스크롤합니다.

   ![](assets/s_ncs_user_wizard_sms01_140.png)

1. 수신자에 대한 정보를 보려면 **[!UICONTROL Data loaded]** 링크를 클릭합니다.

   ![](assets/s_user_mobile_wizard_sms_02.png)

   >[!NOTE]
   >
   >Latin-1(ISO-8859-1) 코드 페이지가 사용되는 경우 SMS 메시지 길이는 160자로 제한됩니다. 유니코드로 작성된 메시지는 70자를 초과할 수 없습니다. 특정 특수 문자는 메시지 길이에 영향을 줄 수 있습니다. 메시지 길이에 대한 자세한 내용은 [SMS 문자 변환](#about-character-transliteration) 섹션을 참조하십시오.
   >
   >개인화 필드 또는 조건부 컨텐츠 필드가 있는 경우 메시지 크기는 받는 사람마다 다릅니다. 개인화가 수행되면 메시지의 길이를 평가해야 합니다.
   >
   >분석을 실행하면 메시지 길이가 확인되고 오버플로가 발생한 경우 경고가 표시됩니다.

1. NetSize 커넥터 또는 SMPP 커넥터를 사용하는 경우 배달 보낸 사람의 이름을 개인화할 수 있습니다. 자세한 내용은 [고급 매개 변수](#advanced-parameters) 섹션을 참조하십시오.

## 대상 모집단 {#selecting-the-target-population} 선택

게재의 대상 모집단을 선택할 때의 자세한 프로세스는 [이 섹션](../../delivery/using/steps-defining-the-target-population.md)에 표시됩니다.

개인화 필드 사용에 대한 자세한 내용은 [이 섹션](../../delivery/using/about-personalization.md)을 참조하십시오.

시드 목록 포함에 대한 자세한 내용은 [이 페이지](../../delivery/using/about-seed-addresses.md)를 참조하십시오.

