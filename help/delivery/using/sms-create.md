---
product: campaign
title: Campaign으로 SMS 만들기
description: Campaign을 사용하여 SMS를 만드는 방법을 알아봅니다
feature: SMS
exl-id: 94aa4628-d973-433d-b963-b078e2d6672b
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 3%

---

# SMS 게재 만들기 {#creating-a-sms-delivery}

![](../../assets/common.svg)

## 게재 채널 선택 {#selecting-the-delivery-channel}

새 SMS 게재를 만들려면 아래 단계를 수행하십시오.

>[!NOTE]
>
>게재 만들기에 대한 글로벌 개념은 [이 섹션](steps-about-delivery-creation-steps.md).

1. 게재 대시보드와 같은 새 게재를 만듭니다.
1. 게재 템플릿을 선택합니다 **모바일로 전송(SMPP)** 이전에 만든 URL 섹션을 참조하십시오. 자세한 내용은 [게재 템플릿 변경](sms-set-up.md#changing-the-delivery-template) 섹션을 참조하십시오.

   ![](assets/s_user_mobile_wizard.png)

1. 레이블, 코드 및 설명을 사용하여 게재를 식별합니다. 이 작업에 대한 자세한 정보는 [이 섹션](steps-create-and-identify-the-delivery.md#identifying-the-delivery)을 참조하십시오.
1. 클릭 **[!UICONTROL Continue]** 이 정보를 확인하고 메시지 구성 창을 표시하려면 다음을 수행하십시오.

## SMS 콘텐츠를 정의합니다 {#defining-the-sms-content}

SMS 콘텐츠를 만들려면 아래 단계를 수행하십시오.

1. 메시지의 내용을 **[!UICONTROL Text content]** 섹션에 나열된 상태로 남아 있습니다. 도구 모음 단추를 사용하여 내용을 가져오거나 저장하거나 검색할 수 있습니다. 마지막 단추는 개인화 필드를 삽입하는 데 사용됩니다.

   ![](assets/s_ncs_user_wizard_sms01_138.png)

   개인화 필드 사용은 [개인화 기본 정보](about-personalization.md) 섹션을 참조하십시오.

1. 클릭 **[!UICONTROL Preview]** 개인화를 사용하여 메시지 렌더링을 볼 수 있도록 페이지 하단에 있습니다. 미리 보기를 시작하려면 **[!UICONTROL Test personalization]** 단추를 누릅니다. 정의된 대상에서 수신자를 선택하거나 다른 수신자를 선택할 수 있습니다.

   ![](assets/s_ncs_user_wizard_sms01_139.png)

   SMS 메시지를 승인할 수 있습니다. 콘텐츠 편집기 오른쪽에 표시되는 휴대폰 화면에서 SMS 콘텐츠를 볼 수도 있습니다. 화면을 클릭하고 마우스를 사용하여 컨텐츠를 스크롤합니다.

   ![](assets/s_ncs_user_wizard_sms01_140.png)

1. 을(를) 클릭합니다. **[!UICONTROL Data loaded]** 링크를 클릭하여 수신자와 관련된 정보를 확인합니다.

   ![](assets/s_user_mobile_wizard_sms_02.png)

   >[!NOTE]
   >
   >Latin-1(ISO-8859-1) 코드 페이지가 사용되는 경우 SMS 메시지는 160자의 길이로 제한됩니다. 유니코드로 메시지를 쓰는 경우 70자를 초과할 수 없습니다. 특정 특수 문자는 메시지 길이에 영향을 줄 수 있습니다. 메시지 길이에 대한 자세한 내용은 [SMS 문자 변환](#about-character-transliteration) 섹션을 참조하십시오.
   >
   >개인화 필드 또는 조건부 콘텐츠 필드가 있으면 메시지 크기가 수신자마다 다릅니다. 개인화가 수행되면 메시지 길이를 평가해야 합니다.
   >
   >분석을 실행하면 메시지 길이가 확인되고 오버플로가 발생할 경우 경고가 표시됩니다.

1. NetSize 커넥터 또는 SMPP 커넥터를 사용하는 경우 게재 발신자의 이름을 개인화할 수 있습니다. 자세한 내용은 [고급 매개 변수](#advanced-parameters) 섹션을 참조하십시오.

## 대상 모집단 선택 {#selecting-the-target-population}

게재의 대상 모집단을 선택할 때의 자세한 프로세스가에 표시됩니다. [이 섹션](steps-defining-the-target-population.md).

개인화 필드 사용에 대한 자세한 내용은 [이 섹션](about-personalization.md).

시드 목록 포함에 대한 자세한 내용은 [이 페이지](about-seed-addresses.md).
