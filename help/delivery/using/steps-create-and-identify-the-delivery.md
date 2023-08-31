---
product: campaign
title: 게재 만들기 및 식별
description: 게재 만들기 및 식별
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Channel Configuration
role: User
exl-id: 6e37bc14-b1a9-42af-8c28-ae4b5bcaa055
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 7%

---

# 게재 만들기 및 식별 {#create-and-identify-the-delivery}

## 게재 만들기 {#creating-the-delivery}

개요 또는 를 통해 게재를 만들 수 있습니다. **[!UICONTROL Create > Delivery]** 메뉴 아래의 제품에서 사용할 수 있습니다.


게재를 만들려면 **[!UICONTROL Create]** 게재 목록 위에 새 게재를 만들 때 사용된 게재 채널을 표시해야 합니다. 이렇게 하려면 의 드롭다운 목록에서 적절한 게재 템플릿을 선택합니다 **[!UICONTROL Delivery template]** 필드.

![](assets/s_ncs_user_wizard_email01_1.png)

기본 템플릿은 설치한 각 채널에 대해 제공됩니다(DM, 이메일, 팩스, 전화, 모바일 채널(SMS), Facebook, Twitter 등).

>[!NOTE]
>
>목록에 제공되는 채널은 라이선스 계약에 따라 다릅니다.

필요에 따라 특정 매개 변수를 사전 구성하기 위해 새 게재 템플릿을 만들 수 있습니다. 템플릿에 대한 자세한 내용은 다음을 참조하십시오. [이 섹션](about-templates.md).

## 게재 식별 {#identifying-the-delivery}

게재를 식별하려면 매개 변수를 완료해야 합니다. 방법은 다음과 같습니다.

1. 에 게재 이름을 입력합니다. **[!UICONTROL Label]** 필드.

   게재 코드를 게재에 지정할 수도 있습니다. 게재 이름 및 해당 코드는 게재 목록에 표시되지만 수신자는 볼 수 없습니다.

1. 에 설명 추가 **[!UICONTROL Description]** 필드.
1. 관련 필드에서 게재 특성을 선택합니다. 이 정보는 게재 추적에 유용합니다. 게재 목록에서 이 기준을 기반으로 필터링하거나 이 선택 기준을 사용하여 쿼리를 작성할 수 있습니다.

   ![](assets/s_ncs_user_email_del_nature.png)

1. 클릭 **[!UICONTROL Continue]** 이 정보를 확인하고 메시지 구성 창을 표시합니다.

게재 콘텐츠를 구성할 준비가 되었습니다. 게재 콘텐츠 정의는 각 채널에 따라 다릅니다. 자세한 내용은 전용 섹션 을 참조하십시오.

* [이메일 콘텐츠 정의](defining-the-email-content.md)
* [SMS 콘텐츠를 정의합니다](sms-create.md#defining-the-sms-content)
* [DM 콘텐츠 정의](defining-the-direct-mail-content.md)
* [푸시 알림](about-mobile-app-channel.md)
