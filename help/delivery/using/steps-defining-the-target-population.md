---
title: 대상 모집단 정의
seo-title: 대상 모집단 정의
description: 대상 모집단 정의
seo-description: null
page-status-flag: never-activated
uuid: 8bf70ea4-5f28-4d85-b5ce-0bd3ed3eea55
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: df29492f-ed73-4ab8-b075-e76b3b9ebce3
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1578'
ht-degree: 2%

---


# 대상 모집단 정의 {#defining-the-target-population}

## 대상 모집단 정보 {#about-target-populations}

각 게재에 대해 몇 가지 유형의 타겟 모집단을 정의할 수 있습니다. 아래 섹션에서는 선택 방법에 대한 자세한 정보를 제공합니다.

* 배달을 받는 사람. [자세한 내용](../../delivery/using/steps-defining-the-target-population.md#selecting-the-main-target)
* 유효성 검사 주기를 설정하기 위해 증명 메시지의 받는 사람. [자세한 내용](../../delivery/using/steps-defining-the-target-population.md#defining-a-specific-proof-target)

또한 게재가 마케팅 캠페인에 포함된 경우 [시드 주소](../../delivery/using/about-seed-addresses.md)및 [제어 그룹을 정의할 수도 있습니다](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

## 게재의 기본 받는 사람 선택 {#selecting-the-main-target}

대부분의 경우 기본 대상은 Adobe Campaign 데이터베이스에서 추출됩니다(기본 모드). 그러나 수신자는 외부 파일에 저장할 수도 있습니다. 자세한 내용은 [이 섹션을 참조하십시오](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients).

게재의 수신자를 선택하려면 아래 절차를 따르십시오.

1. 배달 편집기에서 을 선택합니다 **[!UICONTROL To]**.
1. 받는 사람이 데이터베이스에 저장된 경우 첫 번째 옵션을 선택합니다.

   ![](assets/s_ncs_user_wizard_email02a.png)

1. 드롭다운 목록에서 대상 매핑을 **[!UICONTROL Target mapping]** 선택합니다. Adobe Campaign 기본 대상 매핑은 **[!UICONTROL Recipients]** nms:recipient **** 스키마를 기반으로 합니다.

   다른 대상 매핑을 사용할 수 있으며, 일부 대상 매핑은 특정 구성과 관련될 수 있습니다. 대상 매핑에 대한 자세한 내용은 대상 매핑 [선택을 참조하십시오](../../delivery/using/selecting-a-target-mapping.md).

1. 단추를 **[!UICONTROL Add]** 클릭하여 제한 필터를 정의합니다.

   그런 다음 적용할 필터링 유형을 선택할 수 있습니다.

   ![](assets/s_ncs_user_wizard_email02b.png)

   데이터베이스에 정의된 타깃팅 유형을 사용하여 수신자를 선택할 수 있습니다. 대상 유형을 사용하려면 해당 유형을 선택하고 을 클릭합니다 **[!UICONTROL Next]**. 각 대상에 대해 탭을 클릭하여 관련 받는 사람을 표시할 수 **[!UICONTROL Preview]** 있습니다. 특정 유형의 타겟에 대해 이 **[!UICONTROL Refine target]** 단추를 사용하면 여러 타깃팅 기준을 결합할 수 있습니다.

   기본적으로 다음 대상 유형이 제공됩니다.

   * **[!UICONTROL Filtering conditions]** :이 옵션을 사용하면 쿼리를 정의하고 결과를 표시할 수 있습니다. 쿼리 정의 방법은 [이 섹션에 나와 있습니다](../../platform/using/creating-filters.md#creating-an-advanced-filter).
   * **[!UICONTROL Subscribers of an information service]** :이 옵션을 사용하면 받는 사람이 가입해야 하는 뉴스레터를 선택하는 데 사용할 수 있습니다.

      ![](assets/s_ncs_user_wizard_email02c.png)

   * **[!UICONTROL Recipients of a delivery]** :이 옵션을 사용하면 기존 게재의 수신자를 타깃팅 기준으로 정의할 수 있습니다. 그런 다음 목록에서 배달을 선택해야 합니다.

      ![](assets/s_ncs_user_wizard_email02d.png)

   * **[!UICONTROL Delivery recipients belonging to a folder]** :이 옵션을 사용하면 배달 폴더를 선택하고 해당 폴더에서 배달 수신자를 타깃팅할 수 있습니다.

      ![](assets/s_ncs_user_wizard_email02e.png)

      드롭다운 목록에서 선택하여 수신자의 동작을 필터링할 수 있습니다.

      ![](assets/s_ncs_user_wizard_email02f.png)

      >[!NOTE]
      >
      >이 **[!UICONTROL Include sub-folders]** 옵션을 사용하면 선택한 노드 아래의 트리 구조에 있는 폴더에 포함된 배달을 타깃팅할 수도 있습니다.

   * **[!UICONTROL Recipients included in a folder]** :이 옵션을 사용하면 트리의 특정 폴더에 포함된 프로필을 타깃팅할 수 있습니다.
   * **[!UICONTROL A recipient]** :이 옵션을 사용하면 데이터베이스의 프로필에서 특정 수신자를 선택할 수 있습니다.
   * **[!UICONTROL A list of recipients]** :이 옵션을 사용하면 수신자 목록을 타깃팅할 수 있습니다. 목록은 [이 섹션에 나와 있습니다](../../platform/using/creating-and-managing-lists.md).
   * **[!UICONTROL User filters]** :이 옵션을 사용하면 미리 구성된 필터에 액세스하여 데이터베이스의 프로필에 대한 필터링 기준으로 사용할 수 있습니다. 사전 구성된 필터가 [이 섹션에 표시됩니다](../../platform/using/creating-filters.md#saving-a-filter).
   * 이 옵션을 **[!UICONTROL Exclude recipients corresponding to this segment]** 사용하면 정의된 대상 기준을 충족하지 않는 수신자를 타깃팅할 수 있습니다. 이 옵션을 사용하려면 적절한 상자를 선택한 다음, 앞에서 정의된 대로 타깃팅을 적용하여 결과 프로필을 제외합니다.

      ![](assets/s_ncs_user_wizard_email02g.png)

1. 필드에 이 타깃팅의 이름을 **[!UICONTROL Label]** 입력합니다. 기본적으로 레이블은 첫 번째 타깃팅 기준의 레이블이 됩니다. 조합의 경우 명시적인 이름을 사용하는 것이 좋습니다.
1. 구성된 타깃팅 **[!UICONTROL Finish]** 의 유효성을 확인하려면 을(를) 클릭합니다.

   정의된 타깃팅 기준은 기본 대상 구성 탭의 중앙 섹션에 요약됩니다. 콘텐트를 보려면 기준을 클릭합니다(구성 및 미리 보기). 기준을 삭제하려면 해당 레이블 옆에 있는 십자 기호를 클릭합니다.

   ![](assets/s_ncs_user_wizard_email02h.png)

### 외부 받는 사람 선택 {#selecting-external-recipients}

데이터베이스에 저장되지는 않았지만 외부 파일에 저장된 수신자에 대한 배달을 시작할 수 있습니다. 예를 들어 텍스트 파일에서 가져온 수신자에게 배달을 보냅니다.

방법은 다음과 같습니다.

1. 배달 받는 사람을 선택하려면 **[!UICONTROL To]** 링크를 클릭합니다.
1. 옵션을 **[!UICONTROL Defined in an external file]** 선택합니다.

   ![](assets/s_ncs_user_wizard_external_recipients.png)

1. 기본적으로 수신자는 데이터베이스에 가져옵니다. 를 선택해야 합니다 **[!UICONTROL Target mapping]**. 대상 매핑에 대한 자세한 내용은 대상 매핑 [선택을 참조하십시오.](../../delivery/using/selecting-a-target-mapping.md)

   선택할 수도 있습니다 **[!UICONTROL Do not import the recipients into the database]**.

1. 수신자를 가져올 때 링크를 클릭하여 외부 파일을 선택하고 구성합니다. **[!UICONTROL File format definition...]**

   For more information on data import, refer to [this section](../../platform/using/importing-data.md#step-2---source-file-selection).

1. 을 클릭하고 배달 **[!UICONTROL Finish]** 을 표준 배달로 구성합니다.

>[!CAUTION]
>
>이메일 전달을 위한 메시지 내용을 정의할 때는 미러 페이지에 대한 링크를 포함하지 마십시오.이 배달 모드에서 생성할 수 없습니다.

### 제외 설정 설정 {#customizing-exclusion-settings}

주소 오류 및 품질 등급은 IAP(서비스 제공업체)에서 제공합니다. 이 정보는 배달 작업 후 수신자 프로필에서 자동으로 업데이트되며 서비스 제공업체에서 반환하는 파일이 포함됩니다. 프로필에서 읽기 전용으로 볼 수 있습니다.

일정한 수의 연속적인 오류에 도달했거나 품질 등급이 이 창에 지정된 임계값 미만인 주소를 제외하도록 선택할 수 있습니다. 데이터가 반환되지 않은 비적격 주소를 승인할지 여부를 선택할 수도 있습니다.

>[!NOTE]
>
>두 받는 사람의 이름과 성, 우편 번호, 구/군/시 이름이 같은 경우 두 번 오류가 발생하고 중복되지 않습니다.

이 **[!UICONTROL Exclusions]** 탭은 메시지 수를 제한하는 데 사용됩니다.

>[!NOTE]
>
>기본 매개 변수는 권장되지만 필요에 따라 설정을 조정할 수 있습니다. 그러나 이러한 옵션은 사용 및 오류가 발생하지 않도록 전문가 사용자만이 변경할 수 있습니다.

기본 구성을 수정하려면 **[!UICONTROL Edit...]** 링크를 클릭합니다.

![](assets/s_ncs_user_wizard_email02i.png)

다음 옵션을 사용할 수 있습니다.

* **[!UICONTROL Exclude duplicate addresses during delivery]**. 이 옵션은 기본적으로 활성화되어 있습니다.이를 통해 배달 중 중복된 이메일 주소를 제거할 수 있습니다. 적용된 전략은 Adobe Campaign 사용 방식과 데이터베이스의 데이터 유형에 따라 다를 수 있습니다.

   옵션의 기본값은 각 배달 템플릿에 대해 구성할 수 있습니다.

   예제:

   * 뉴스레터 또는 전자 문서 전달 데이터에 기본 중복 항목이 없는 경우도 있습니다. 동일한 이메일 주소를 사용하는 커플에게 개인화된 두 가지 이메일 메시지를 받게 됩니다.한 사람의 이름은 개개인으로 지정됩니다. 이 경우 이 옵션을 선택 취소할 수 있습니다.
   * 마케팅 캠페인 전달:동일한 수신자에게 너무 많은 메시지를 보내지 않으려면 중복 제외가 필요합니다. 이 경우 이 옵션을 선택할 수 있습니다.

      이 옵션을 선택 해제하면 추가 옵션에 액세스할 수 있습니다. **[!UICONTROL Keep duplicate records (same identifier)]**. 여러 타깃팅 기준을 충족하는 수신자에게 여러 전달을 승인할 수 있도록 해줍니다.

      ![](assets/s_ncs_user_wizard_email02j.png)

* **[!UICONTROL Exclude recipients who no longer want to be contacted]** , 즉 이메일 주소가 차단 목록에 있는 받는 사람(&#39;수신 거부&#39;) 전자 마케팅의 전문 윤리 및 전자 상거래 관련 법을 준수하기 위해 이 옵션을 선택해야 합니다.
* **[!UICONTROL Exclude quarantined recipients]**. 이 옵션을 사용하면 응답이 없는 주소가 있는 모든 프로필을 대상에서 제외할 수 있습니다. 이 옵션을 계속 선택하는 것이 좋습니다.

   >[!NOTE]
   >
   >검역 관리에 대한 자세한 내용은 검역 관리 [이해를 참조하십시오](../../delivery/using/understanding-quarantine-management.md).

* **[!UICONTROL Limit delivery]** 지정된 개수의 메시지로 전송합니다. 이 옵션을 사용하면 보낼 최대 메시지 수를 입력할 수 있습니다. 대상의 컨텐츠가 표시된 메시지 수를 초과하는 경우 임의 선택이 대상에 적용됩니다.

### 대상 모집단 크기 줄이기 {#reducing-the-size-of-the-target-population}

대상 인구의 크기를 줄일 수 있습니다. 이렇게 하려면 **[!UICONTROL Requested quantity]** 필드에서 내보낼 받는 사람 수를 지정합니다.

![](assets/s_ncs_user_edit_del_exe_tab.png)

## 증명 메시지 받는 사람 선택 {#selecting-the-proof-target}

증명은 기본 타겟으로 보내기 전에 배달을 테스트할 수 있는 특수 메시지입니다. 메시지의 양식과 내용을 모두 승인하는 사람은 입증 책임입니다.

![](assets/do-not-localize/how-to-video.png) [비디오에서 이 기능 살펴보기](#seeds-and-proofs-video)


교정본 대상을 선택하려면 아래 단계를 따르십시오.

1. 링크를 **[!UICONTROL To]** 클릭합니다.
1. 탭을 **[!UICONTROL Target of the proofs]** 클릭합니다.
1. 적용할 방법을 선택하려면 **[!UICONTROL Targeting mode]** 필드를 클릭합니다. **[!UICONTROL Definition of a specific proof target]** , **[!UICONTROL Substitution of the address]** , **[!UICONTROL Seed addresses]** 또는 **[!UICONTROL Specific target and seed addresses]**&#x200B;를 선택합니다.

>[!NOTE]
>
>일반적으로 증명 대상을 주 대상에 추가할 수 있습니다. 이렇게 하려면 **[!UICONTROL Main target]** 탭의 하단 섹션에서 해당 옵션을 선택합니다.

## 특정 증명 대상 정의 {#defining-a-specific-proof-target}

증명 대상을 선택할 때 이 **[!UICONTROL Definition of a specific proof target]** 옵션을 사용하면 데이터베이스의 프로필에서 증명 수신자를 선택할 수 있습니다.

기본 대상을 정의하는 경우와 마찬가지로 **[!UICONTROL Add]** 단추를 사용하여 수신자를 선택하려면 이 옵션을 선택합니다. 주 [대상 선택을 참조하십시오](../../delivery/using/steps-defining-the-target-population.md#selecting-the-main-target).

![](assets/s_ncs_user_wizard_email01_143.png)

For more on proof sending, refer to [this section](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### 증명 시 주소 대체 사용 {#using-address-substitution-in-proof}

데이터베이스에서 전용 수신자를 선택하는 대신 이 **[!UICONTROL Substitution of the address]** 옵션을 사용할 수 있습니다.

이 옵션을 사용하면 배달을 받는 사람 프로필을 사용하고 해당 이메일 주소를 증빙 자료를 수신할 하나 이상의 다른 주소로 바꿀 수 있습니다.

이 옵션을 선택하면 대체 내용을 구성할 수 있는 특수 편집기를 통해 증명 주소가 채워집니다.

![](assets/s_ncs_user_wizard_email_bat_substitute.png)

구성은 다음과 같이 수행됩니다.

1. 대체 **[!UICONTROL Add]** 를 정의하려면 아이콘을 클릭합니다.
1. 사용할 수신자 주소를 입력하거나 목록에서 선택합니다.
1. 증표에 사용할 프로파일을 선택합니다.데이터 **[!UICONTROL Random]** 에 있는 대상의 프로파일 데이터를 **[!UICONTROL Profile to use]** 사용할 수 있도록 열에 값을 저장합니다.

   ![](assets/s_ncs_user_wizard_email_bat_substitute_choose.png)

1. 다음 예제와 같이 기본 대상에서 프로필을 선택하려면 아이콘을 **[!UICONTROL Detail]** 클릭합니다.

   ![](assets/s_ncs_user_wizard_email_bat_substitute_select.png)

   필요한 만큼 대체 주소를 정의할 수 있습니다.

## 시드 주소를 증명으로 사용 {#using-seed-addresses-as-proof}

교정본 **[!UICONTROL Seed addresses]** 의 대상으로 사용할 수 있습니다.이 옵션을 사용하면 기존 시드 주소 목록을 사용하거나 가져올 수 있습니다.

![](assets/s_ncs_user_wizard_email_bat_control_address.png)

>[!NOTE]
>
>시드 주소는 [시드 주소에 표시됩니다](../../delivery/using/about-seed-addresses.md).

이 옵션을 사용하여 특정 증명 대상의 정의와 시드 주소의 사용을 결합할 수 **[!UICONTROL Specific target and Seed addresses]** 있습니다. 그런 다음 관련 구성은 두 개의 개별 하위 탭에서 정의됩니다.

## How to manage seed and proofs in an email {#seeds-and-proofs-video}

이 비디오에서는 기존 이메일에 씨드(sed) 및 교정을 추가하는 방법과 보내는 방법을 살펴봅니다.

>[!VIDEO](https://video.tv.adobe.com/v/25606?quality=12)

다음을 참조하십시오.
* [증명 대상 선택](#selecting-the-proof-target)

* [시드 주소 정보](../../delivery/using/about-seed-addresses.md)

* [사용 사례: 기준 시드 주소 선택](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md)
