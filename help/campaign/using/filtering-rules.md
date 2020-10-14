---
title: 필터링 규칙
seo-title: 필터링 규칙
description: 필터링 규칙
seo-description: null
page-status-flag: never-activated
uuid: 24238a99-1f0f-4d04-9807-557ec2a5ba16
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: campaign-optimization
discoiquuid: 0d50826e-2211-4c3b-8413-ca1453bba6c4
translation-type: tm+mt
source-git-commit: 75cbb8d697a95f4cc07768e6cf3585e4e079e171
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 3%

---


# 필터링 규칙{#filtering-rules}

필터링 규칙을 사용하면 쿼리에 정의된 기준을 기반으로 제외할 메시지를 정의할 수 있습니다. 이러한 규칙은 타깃팅 차원에 연결됩니다.

필터링 규칙은 다른 유형의 규칙(제어, 압력 등)에 연결할 수 있습니다. 를 선택하거나 전용 필터링 유형 **으로 그룹화합니다** . 이에 대한 자세한 내용은 필터링 유형 [만들기 및 사용을 참조하십시오](#creating-and-using-a-filtering-typology).

## Creating a filtering rule {#creating-a-filtering-rule}

예를 들어 뉴스레터 가입자를 필터링하여 미성년자인 수신자에게 통신이 전송되지 않도록 할 수 있습니다.

이 필터를 정의하려면 다음 단계를 적용합니다.

1. 모든 통신 채널에 적용할 수 있는 **[!UICONTROL Filtering]** 유형 규칙을 만듭니다.

   ![](assets/campaign_opt_create_filter_01.png)

1. 기본 타깃팅 차원을 변경하고 가입(**nms:subscription**)을 선택합니다.

   ![](assets/campaign_opt_create_filter_02.png)

1. 링크를 사용하여 필터를 **[!UICONTROL Edit the query from the targeting dimension...]** 만듭니다.

   ![](assets/campaign_opt_create_filter_03.png)

1. 이 규칙을 캠페인 유형에 연결하고 저장합니다.

   ![](assets/campaign_opt_create_filter_04.png)

이 규칙이 배달에서 사용될 때, 미성년 가입자는 자동으로 제외됩니다. 특정 메시지는 규칙 응용 프로그램을 나타냅니다.

![](assets/campaign_opt_create_filter_05.png)

## 필터링 규칙 설정 {#conditioning-a-filtering-rule}

연결된 배달 또는 배달 개요를 기준으로 필터링 규칙의 응용 프로그램 필드를 제한할 수 있습니다.

이렇게 하려면, 분류 규칙의 **[!UICONTROL General]** 탭으로 이동하여 적용할 제한 유형을 선택하고 필터를 만듭니다.

![](assets/campaign_opt_create_filter_06.png)

이 경우, 규칙이 모든 게재에 연결되어 있어도 정의된 필터의 기준과 일치하는 것에만 적용됩니다.

>[!NOTE]
>
>작업 과정의 워크플로우에서 유형 지정 및 필터링 규칙을 사용할 수 **[!UICONTROL Delivery outline]** 있습니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../workflow/using/delivery-outline.md)을 참조하십시오.

## 필터링 유형 만들기 및 사용 {#creating-and-using-a-filtering-typology}

다음과 같은 유형을 만들 수 **[!UICONTROL Filtering]** 있습니다.필터링 규칙만 포함합니다.

![](assets/campaign_opt_create_typo_filtering.png)

대상을 선택할 때 이러한 특정 유형을 게재에 연결할 수 있습니다.배달 마법사에서 **[!UICONTROL To]** 링크를 클릭한 다음 **[!UICONTROL Exclusions]** 탭을 클릭합니다.

![](assets/campaign_opt_apply_typo_filtering.png)

그런 다음 배달에 적용할 필터링 유형을 선택합니다. 이렇게 하려면 **[!UICONTROL Add]** 단추를 클릭하고 적용할 유형을 선택합니다.

또한 유형별로 그룹화하지 않고 이 탭을 통해 필터링 규칙을 직접 연결할 수도 있습니다. 이렇게 하려면 창의 아래 섹션을 사용하십시오.

![](assets/campaign_opt_select_typo_filtering.png)

>[!NOTE]
>
>선택 창에서는 분류 및 필터링 규칙만 사용할 수 있습니다.
>
>이러한 구성은 배달 템플릿에서 템플릿을 사용하여 만든 모든 새 게재에 자동으로 적용되도록 정의할 수 있습니다.


## 기본 제공 기능 제외 규칙 {#default-deliverability-exclusion-rules}

기본적으로 두 개의 필터링 규칙을 사용할 수 있습니다. **[!UICONTROL Exclude addresses]** ( **[!UICONTROL addressExclusions]** ) 및 **[!UICONTROL Exclude domains]** ( **[!UICONTROL domainExclusions]** ). 이메일 분석 중에 이러한 규칙은 받는 사람 이메일 주소와 배달 가능 인스턴스에서 관리되는 암호화된 전역 제외 목록에 포함된 금지된 주소 또는 도메인 이름과 비교합니다. 일치하는 메시지가 있으면 해당 받는 사람에게 메시지가 전송되지 않습니다.

악성 활동, 특히 차단 목록 Spamtrap 사용으로 인해에 추가되지 않도록 하는 것입니다. 예를 들어 웹 양식 중 하나를 통해 구독하는 데 Spamtrap을 사용하는 경우 확인 이메일이 자동으로 해당 Spamtrap에 전송되고 그러면 해당 주소가에 자동으로 차단 목록 추가됩니다.

>[!NOTE]
>
>글로벌 제외 목록에 포함된 주소 및 도메인 이름은 숨겨집니다. 배달 분석 로그에는 제외된 받는 사람 수만 표시됩니다.

