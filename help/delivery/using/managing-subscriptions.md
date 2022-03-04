---
product: campaign
title: 구독 관리
description: 구독 관리
feature: Subscriptions
exl-id: 16dddd4a-2e1a-4c78-8168-f656657bb9b8
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '1098'
ht-degree: 2%

---

# 구독 관리{#managing-subscriptions}

![](../../assets/common.svg)

## 정보 서비스 정보 {#about-information-services}

정보 서비스는 다음과 같이 구성됩니다.

* 등록 및 구독(옵트인),
* 등록 취소, 구독 취소(옵트아웃) 또는 자동 구독 취소(평가판 오퍼와 같은 제한 시간 서비스),
* 구독 및 구독 취소 확인 메커니즘(확인, 이중 옵트인 등이 있는 간단한 메커니즘),
* 가입자 기록 추적.

표준 기능으로서, 이러한 서비스에는 특정 통계 보고서가 포함됩니다. 가입자 추적, 충성도 수준, 구독 취소 트렌드 등

이메일의 경우, 필수 구독 취소 링크가 자동으로 생성되며 전체 옵트인/옵트아웃은 Adobe를 완전히 자동화하여 기록 추적을 통해 시행 중인 규정을 완전히 준수하도록 보장합니다.

서비스 구독/구독 취소 모드가 세 가지 있습니다.

1. 수동
1. 가져오기(구독만),
1. 웹 양식을 통해

>[!NOTE]
>
>이중 옵트인이 있는 구독 양식을 만드는 샘플은 [이 섹션](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in).

## 정보 서비스 만들기 {#creating-an-information-service}

가입자에게 관련 확인 메시지나 자동 게재와 함께 정보 서비스 구독을 만들고 관리할 수 있습니다.

정보 서비스 맵에 액세스하려면 **[!UICONTROL Profiles and Targets]** 탭을 클릭하고 **[!UICONTROL Services and Subscriptions]** 링크를 클릭합니다.

![](assets/s_ncs_user_services_new.png)

기존 서비스를 편집하려면 해당 이름을 클릭합니다. 서비스를 만들려면 **[!UICONTROL Create]** 목록 위에 있는 단추입니다.

![](assets/s_ncs_user_services_add.png)

* 에 서비스 이름을 입력합니다. **[!UICONTROL Label]** 필드를 작성하고 게재 채널을 선택합니다. 이메일, 모바일, Facebook, Twitter 또는 모바일 애플리케이션.

   >[!NOTE]
   >
   >Facebook 및 Twitter 가입은 [이 섹션](../../social/using/about-social-marketing.md). 모바일 애플리케이션 구독은 [모바일 앱 채널 기본 정보](about-mobile-app-channel.md).

* 이메일 유형 서비스의 경우 **게재 모드**. 가능한 모드는 다음과 같습니다. **[!UICONTROL Newsletter]** 또는 **[!UICONTROL Viral]**.
* 보낼 수 있습니다 **확인 메시지** 구독 또는 구독 취소용. 이렇게 하려면 에서 해당 게재를 만드는 데 사용할 게재 템플릿을 선택합니다 **[!UICONTROL Subscription]** 및 **[!UICONTROL Unsubscription]** 필드. 이러한 템플릿은 **[!UICONTROL Subscription]** 정의된 대상 없이 대상 매핑을 입력합니다. 섹션을 참조하십시오. [이메일 채널 기본 정보](about-email-channel.md).
* 기본적으로 구독은 무제한 제공됩니다. 을 선택 취소할 수 있습니다 **[!UICONTROL Unlimited]** 서비스의 유효 기간을 정의하는 옵션입니다. 기간은 일 단위로 지정할 수 있습니다(**[!UICONTROL d]** ) 또는 개월(**[!UICONTROL m]** ).

서비스가 저장되면 서비스 및 구독 목록에 추가됩니다. 해당 이름을 클릭하여 편집합니다. 몇 개의 탭을 사용할 수 있습니다. 다음 **[!UICONTROL Subscriptions]** 탭에서는 정보 서비스의 구독자 목록을 볼 수 있습니다(**[!UICONTROL Active subscriptions]** 탭) 또는 구독/구독 취소 내역(**[!UICONTROL History]** 탭). 이 탭에서 구독자를 추가 및 삭제할 수도 있습니다. 자세한 내용은 [구독자 추가 및 삭제](#adding-and-deleting-subscribers).

![](assets/s_ncs_user_services_subscriptions.png)

다음 **[!UICONTROL Detail...]** 버튼을 사용하면 선택한 수신자에 대한 구독 속성을 볼 수 있습니다.

수신자에 대한 구독 속성을 수정할 수 있습니다.

![](assets/s_ncs_user_services_modify.png)

대시보드에서 **[!UICONTROL Reports]** 구독을 추적하려면 탭을 클릭하십시오. 구독 수준, 총 구독자 수 등의 변경 사항 이 탭에서 보고서를 보관하고 히스토리를 볼 수 있습니다.

## 구독자 추가 및 삭제 {#adding-and-deleting-subscribers}

에서 **[!UICONTROL Subscriptions]** 정보 서비스 탭 클릭 **[!UICONTROL Add]** 가입자를 추가하려면 구독자 목록을 마우스 오른쪽 단추로 클릭하고 를 선택할 수도 있습니다 **[!UICONTROL Add]**. 구독할 프로필이 저장되는 폴더를 선택한 다음 구독할 프로필을 선택하고 을(를) 클릭합니다 **[!UICONTROL OK]** 유효성을 검사하려면 다음을 수행하십시오.

구독자를 삭제하려면 구독자를 선택하고 **[!UICONTROL Delete]**. 가입자 목록을 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Delete]**.

두 경우 모두 구독 취소에 대한 게재 템플릿이 서비스에 첨부된 경우 관련 사용자에게 확인 메시지를 보낼 수 있습니다( 참조) [정보 서비스 만들기](#creating-an-information-service)). 경고를 사용하면 이 게재의 유효성을 검사하거나 유효성을 검사할 수 있습니다.

![](assets/s_ncs_user_services_update.png)

자세한 내용은 [구독 및 구독 취소 메커니즘](#subscription-and-unsubscription-mechanisms).

## 서비스 가입자에게 제공 {#delivering-to-the-subscribers-of-a-service}

정보 서비스 가입자에게 게재하기 위해 다음 예와 같이 관련 정보 서비스의 구독자를 타깃팅할 수 있습니다.

![](assets/s_ncs_user_wizard_target_is_a_service01.png)

>[!CAUTION]
>
>대상 매핑은 **[!UICONTROL Subscriptions]**.

**[!UICONTROL Subscribers of an information service]**&#x200B;을(를) 선택하고 **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다 .

![](assets/s_ncs_user_wizard_target_is_a_service02.png)

타겟팅된 정보 서비스를 선택하고 **[!UICONTROL Finish]**.

![](assets/s_ncs_user_wizard_target_is_a_service03.png)

다음 **[!UICONTROL Preview]** 탭에서는 선택한 정보 서비스의 구독자 목록을 볼 수 있습니다.

## 구독 및 구독 취소 메커니즘 {#subscription-and-unsubscription-mechanisms}

구독 및 구독 취소 메커니즘을 설정하여 프로세스 및 가입자 관리를 자동화할 수 있습니다.

>[!NOTE]
>
>새 구독자에게 확인 메시지를 보낼 수 있습니다.\
>이 메시지의 콘텐츠는 **[!UICONTROL Subscription]** 또는 **[!UICONTROL Unsubscription]** 필드.
>
>확인 메시지는 이러한 필드에 지정된 게재 템플릿을 통해 만들어집니다. 이러한 대상 매핑은 **[!UICONTROL Subscriptions]**.

![](assets/s_ncs_user_subscribe_confirmation.png)

### 서비스에 수신자 가입 {#subscribing-a-recipient-to-a-service}

정보 서비스에 수신자를 등록하려면 다음 작업을 수행할 수 있습니다.

* 서비스를 수동으로 추가합니다. 다음을 수행합니다. **[!UICONTROL Subscriptions]** 해당 프로필의 탭을 클릭합니다. **[!UICONTROL Add]** 관련 정보 서비스를 선택합니다.

   자세한 내용은 [이 섹션](../../platform/using/editing-a-profile.md).

* 이 서비스에 수신자 집합을 자동으로 구독합니다. 수신자 목록은 필터링 작업, 그룹, 폴더, 가져오기 또는 마우스를 사용한 직접 선택에서 가져올 수 있습니다. 이러한 수신자를 구독하려면 프로필을 선택하고 마우스 오른쪽 단추를 클릭합니다. 선택 **[!UICONTROL Actions > Subscribe selection to a service...]**&#x200B;을(를) 선택한 후 작업을 시작합니다.
* 수신자를 가져와 정보 서비스에 자동으로 구독합니다. 이렇게 하려면 가져오기 마법사의 마지막 단계에서 관련 서비스를 선택합니다.

   이 작업에 대한 자세한 정보는 [이 섹션](../../platform/using/executing-import-jobs.md)을 참조하십시오.

* 수신자가 서비스에 가입할 수 있도록 웹 양식을 사용하십시오.

   이 작업에 대한 자세한 정보는 [이 섹션](../../web/using/about-web-applications.md)을 참조하십시오.

* 타겟팅 워크플로우 만들기 및 **[!UICONTROL Subscription service]** 상자.

   ![](assets/s_ncs_user_subscribe_from_wf.png)

   워크플로우와 워크플로우 사용 방법에 대해서는 [이 섹션](../../workflow/using/about-workflows.md).

### 서비스에서 수신자 가입 해지 {#unsubscribing-a-recipient-from-a-service}

#### 수동 구독 취소 {#manual-unsubscribing}

이메일 게재에는 법에 따라 구독 취소 링크가 포함되어야 합니다. 수신자는 이 링크를 클릭하여 프로필을 업데이트하며 향후 게재 타겟에서 제외할 수 있습니다.

기본 구독 취소 링크는 게재 마법사에 제공된 컨텐츠 편집기의 도구 모음에 있는 마지막 단추를 통해 삽입됩니다(참조 [개인화 기본 정보](about-personalization.md)). 수신자가 이 링크를 클릭하면 프로필이차단 목록(옵트아웃)에 추가됩니다. 즉, 이 수신자를 더 이상 게재 작업의 타깃팅이 되지 않습니다.

그러나 수신자는 모든 서비스의 구독을 취소하지 않고 서비스 구독을 취소하도록 선택할 수 있습니다. 이를 허용하려면 웹 양식을 사용할 수 있습니다( [이 섹션](../../web/using/adding-fields-to-a-web-form.md#subscription-checkboxes)) 또는 개인화된 구독 취소 링크를 삽입합니다( 참조). [개인화 블록](personalization-blocks.md)).

수신자 프로필에서 수신자의 구독을 수동으로 취소할 수도 있습니다. 이렇게 하려면 **[!UICONTROL Subscriptions]** 관련 받는 사람의 탭에서 관련 정보 서비스를 선택하고 **[!UICONTROL Delete]**.

관련 정보 서비스를 통해 한 명 이상의 수신자의 구독을 취소할 수 있습니다. 이렇게 하려면 **[!UICONTROL Subscriptions]** 서비스의 탭에서 관련 수신자를 선택하고 **[!UICONTROL Delete]**.

#### 자동 구독 취소 {#automatic-unsubscription}

정보 서비스는 제한된 기간을 가질 수 있습니다. 유효 기간이 만료되면 수신자는 자동으로 구독 취소됩니다. 이 기간은 **[!UICONTROL Edit]** 서비스 속성의 탭입니다. 그것은 일 단위로 표시된다.

![](assets/s_ncs_user_services_delay.png)

모집단에 대한 구독 취소 워크플로우를 설정할 수도 있습니다. 이렇게 하려면 구독 워크플로우와 동일한 절차를 따르지만 **[!UICONTROL Unsubscription]** 선택 사항입니다. 자세한 내용은 [서비스에 수신자 가입](#subscribing-a-recipient-to-a-service).

### 가입자 추적 {#subscriber-tracking}

를 사용하여 정보 서비스 구독의 변경 사항을 추적할 수 있습니다 **[!UICONTROL Reports]** 링크를 클릭합니다.

![](assets/s_ncs_user_services_report.png)
