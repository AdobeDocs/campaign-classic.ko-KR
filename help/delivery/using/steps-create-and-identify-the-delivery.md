---
title: 배달 만들기 및 식별
seo-title: 배달 만들기 및 식별
description: 배달 만들기 및 식별
seo-description: null
page-status-flag: never-activated
uuid: 8bf70ea4-5f28-4d85-b5ce-0bd3ed3eea55
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: df29492f-ed73-4ab8-b075-e76b3b9ebce3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 62e6537ba306956cac3bf6e1dd18567bc1414917

---


# 배달 만들기 및 식별 {#create-and-identify-the-delivery}

## 배달 만들기 {#creating-the-delivery}

개요 또는 **[!UICONTROL Create > Delivery]** 메뉴를 통해 배달을 만들 수 있습니다.


배달을 만들려면 배달 목록 **[!UICONTROL Create]** 위의 을 클릭합니다. 새 배달을 만들 때 사용된 배달 채널을 표시해야 합니다. 이렇게 하려면 **[!UICONTROL Delivery template]** 필드의 드롭다운 목록에서 적절한 배달 템플릿을 선택합니다.

![](assets/s_ncs_user_wizard_email01_1.png)

설치한 각 채널에 대해 기본 템플릿이 제공됩니다.다이렉트 메일, 이메일, 팩스, 전화, 모바일 채널(SMS), Facebook, Twitter 등

>[!NOTE]
>
>목록에 제공되는 채널은 라이선스 계약에 따라 다릅니다.

필요에 맞게 특정 매개 변수를 미리 구성하려면 새 배달 템플릿을 만들 수 있습니다. 템플릿에 대한 자세한 내용은 [이 섹션을](../../delivery/using/about-templates.md)참조하십시오.

## 배달 식별 {#identifying-the-delivery}

배달을 식별하려면 매개 변수를 완료해야 합니다. 이렇게 하려면:

1. 필드에 납품할 이름을 **[!UICONTROL Label]** 입력합니다.

   배달 코드도 배달에 할당할 수 있습니다. 배달 이름 및 해당 코드는 배달 목록에 표시되지만 받는 사람은 볼 수 없습니다.

1. 필드에 설명을 **[!UICONTROL Description]** 추가합니다.
1. 관련 필드에서 배달 특성을 선택합니다. 이 정보는 배달 추적에 유용합니다.이 선택 기준을 사용하여 배달 목록에서 이 기준을 기반으로 필터링하거나 쿼리를 빌드할 수 있습니다.

   ![](assets/s_ncs_user_email_del_nature.png)

1. 을 **[!UICONTROL Continue]** 클릭하여 이 정보를 확인하고 메시지 구성 창을 표시합니다.

배달 콘텐츠를 구성할 준비가 되었습니다. 전달 컨텐츠 정의는 각 채널에 따라 다릅니다. 자세한 내용은 전용 섹션을 참조하십시오.

* [이메일 컨텐츠 정의](../../delivery/using/defining-the-email-content.md)
* [SMS 컨텐츠 정의](../../delivery/using/sms-channel.md#defining-the-sms-content)
* [DM 콘텐츠 정의](../../delivery/using/defining-the-direct-mail-content.md)
* [푸시 알림](../../delivery/using/about-mobile-app-channel.md)

