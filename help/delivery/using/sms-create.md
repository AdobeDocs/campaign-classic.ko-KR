---
product: campaign
title: Campaign으로 SMS 만들기
description: Campaign으로 SMS를 만드는 방법 알아보기
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: SMS
exl-id: 94aa4628-d973-433d-b963-b078e2d6672b
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 3%

---

# SMS 게재 만들기  {#creating-a-sms-delivery}



## 게재 채널 선택 {#selecting-the-delivery-channel}

새 SMS 게재를 만들려면 아래 단계를 수행합니다.

>[!NOTE]
>
>게재 만들기에 대한 전체적인 개념은에 나와 있습니다. [이 섹션](steps-about-delivery-creation-steps.md).

1. 게재 대시보드 등에서 새 게재를 만듭니다.
1. 게재 템플릿 선택 **모바일(SMPP)에 전송됨** 이전에 생성한 것입니다. 자세한 내용은 [게재 템플릿 변경](sms-set-up.md#changing-the-delivery-template) 섹션.

   ![](assets/s_user_mobile_wizard.png)

1. 레이블, 코드 및 설명을 사용하여 게재를 식별합니다. 이 작업에 대한 자세한 정보는 [이 섹션](steps-create-and-identify-the-delivery.md#identifying-the-delivery)을 참조하십시오.
1. 클릭 **[!UICONTROL Continue]** 이 정보를 확인하고 메시지 구성 창을 표시합니다.

## SMS 콘텐츠를 정의합니다 {#defining-the-sms-content}

SMS의 콘텐츠를 만들려면 아래 단계를 수행합니다.

1. 에 메시지 내용 입력 **[!UICONTROL Text content]** 섹션에 있는 마지막 항목이 될 필요가 없습니다. 도구 모음 단추를 사용하여 콘텐츠를 가져오거나 저장하거나 검색할 수 있습니다. 마지막 버튼은 개인화 필드를 삽입하는 데 사용됩니다.

   ![](assets/s_ncs_user_wizard_sms01_138.png)

   개인화 필드의 사용은에 나와 있습니다. [개인화 기본 정보](about-personalization.md) 섹션.

1. 클릭 **[!UICONTROL Preview]** 페이지 하단에서 개인화와 함께 메시지 렌더링을 볼 수 있습니다. 미리보기를 시작하려면 다음을 사용하여 수신자를 선택합니다. **[!UICONTROL Test personalization]** 단추를 클릭합니다. 정의된 대상에서 수신자를 선택하거나 다른 수신자를 선택할 수 있습니다.

   ![](assets/s_ncs_user_wizard_sms01_139.png)

   SMS 메시지를 승인할 수 있습니다. 콘텐츠 편집기 오른쪽에 표시된 휴대폰 화면에서 SMS의 콘텐츠를 볼 수도 있습니다. 화면을 클릭하고 마우스를 사용하여 컨텐츠를 스크롤합니다.

   ![](assets/s_ncs_user_wizard_sms01_140.png)

1. 다음을 클릭합니다. **[!UICONTROL Data loaded]** 수신자와 관련된 정보를 볼 수 있는 링크입니다.

   ![](assets/s_user_mobile_wizard_sms_02.png)

   >[!NOTE]
   >
   >SMS 메시지는 Latin-1(ISO-8859-1) 코드 페이지를 사용하는 경우 160자로 제한됩니다. 메시지가 유니코드로 작성되면 70자를 초과할 수 없습니다. 특정 특수 문자는 메시지 길이에 영향을 줄 수 있습니다. 메시지 길이에 대한 자세한 내용은 [SMS 문자 변환](#about-character-transliteration) 섹션.
   >
   >개인화 필드 또는 조건부 콘텐츠 필드가 있으면 메시지 크기가 받는 사람마다 다릅니다. 개인화가 수행되면 메시지 길이를 평가해야 합니다.
   >
   >분석을 시작할 때 메시지 길이를 확인하고 오버플로 시 경고가 표시됩니다.

1. NetSize 커넥터 또는 SMPP 커넥터를 사용하는 경우 게재 발신자의 이름을 개인화할 수 있습니다. 자세한 내용은 [고급 매개 변수](#advanced-parameters) 섹션.

## 대상 모집단 선택 {#selecting-the-target-population}

게재의 대상 모집단을 선택할 때의 자세한 프로세스는에 나와 있습니다. [이 섹션](steps-defining-the-target-population.md).

개인화 필드 사용에 대한 자세한 내용은 을 참조하십시오. [이 섹션](about-personalization.md).

시드 목록 포함에 대한 자세한 내용은 을 참조하십시오. [이 페이지](about-seed-addresses.md).
