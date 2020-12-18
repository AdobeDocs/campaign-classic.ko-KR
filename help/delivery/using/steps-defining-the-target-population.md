---
solution: Campaign Classic
product: campaign
title: 대상 모집단 정의
description: 대상 모집단 정의
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
translation-type: tm+mt
source-git-commit: cea4a26935312b1cb119a3fa671af7bf00788fe9
workflow-type: tm+mt
source-wordcount: '1579'
ht-degree: 2%

---


# 대상 모집단 정의 {#defining-the-target-population}

## 대상 모집단 {#about-target-populations} 정보

각 게재에 대해 몇 가지 유형의 타겟 모집단을 정의할 수 있습니다. 아래 섹션에서는 선택 방법에 대한 자세한 정보를 제공합니다.

* 배달의 기본 받는 사람. [자세한 내용](../../delivery/using/steps-defining-the-target-population.md#selecting-the-main-target)
* 유효성 검사 주기를 설정하기 위해 증명 메시지의 받는 사람. [자세한 내용](../../delivery/using/steps-defining-the-target-population.md#defining-a-specific-proof-target)

또한 배달을 마케팅 캠페인에 포함하는 경우 [시드 주소](../../delivery/using/about-seed-addresses.md) 및 [제어 그룹](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)을 정의할 수도 있습니다.

## 배달 {#selecting-the-main-target}의 기본 받는 사람 선택

대부분의 경우 기본 대상은 Adobe Campaign 데이터베이스에서 추출됩니다(기본 모드). 그러나 수신자는 외부 파일에도 저장할 수 있습니다. [이 섹션](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients)에서 자세히 알아보십시오.

게재의 수신자를 선택하려면 아래 단계를 수행합니다.

1. 배달 편집기에서 **[!UICONTROL To]**&#x200B;을 선택합니다.
1. 받는 사람이 데이터베이스에 저장된 경우 첫 번째 옵션을 선택합니다.

   ![](assets/s_ncs_user_wizard_email02a.png)

1. **[!UICONTROL Target mapping]** 드롭다운 목록에서 대상 매핑을 선택합니다. Adobe Campaign 기본 대상 매핑은 **nms:recipient** 스키마를 기반으로 **[!UICONTROL Recipients]**&#x200B;입니다.

   다른 대상 매핑을 사용할 수 있으며, 일부는 특정 구성과 관련될 수 있습니다. 대상 매핑에 대한 자세한 내용은 [대상 매핑 선택](../../delivery/using/selecting-a-target-mapping.md)을 참조하십시오.

1. **[!UICONTROL Add]** 단추를 클릭하여 제한 필터를 정의합니다.

   그런 다음 적용할 필터링 유형을 선택할 수 있습니다.

   ![](assets/s_ncs_user_wizard_email02b.png)

   데이터베이스에 정의된 타깃팅 유형을 사용하여 수신자를 선택할 수 있습니다. 대상 유형을 사용하려면 해당 유형을 선택하고 **[!UICONTROL Next]**&#x200B;을 클릭합니다. 각 대상에 대해 **[!UICONTROL Preview]** 탭을 클릭하여 관련 받는 사람을 표시할 수 있습니다. 특정 유형의 타겟에 대해 **[!UICONTROL Refine target]** 단추를 사용하면 여러 타깃팅 기준을 결합할 수 있습니다.

   기본적으로 다음 타겟 유형이 제공됩니다.

   * **[!UICONTROL Filtering conditions]** :이 옵션을 사용하면 쿼리를 정의하고 결과를 표시할 수 있습니다. 쿼리를 정의하는 방법은 [이 섹션](../../platform/using/creating-filters.md#creating-an-advanced-filter)에 있습니다.
   * **[!UICONTROL Subscribers of an information service]** :이 옵션을 사용하면 작성되는 배달을 타깃팅하기 위해 수신자에게 가입해야 하는 뉴스레터를 선택할 수 있습니다.

      ![](assets/s_ncs_user_wizard_email02c.png)

   * **[!UICONTROL Recipients of a delivery]** :이 옵션을 사용하면 기존 배달을 타깃팅 기준으로 받는 사람을 정의할 수 있습니다. 그런 다음 목록에서 배달을 선택해야 합니다.

      ![](assets/s_ncs_user_wizard_email02d.png)

   * **[!UICONTROL Delivery recipients belonging to a folder]** :이 옵션을 사용하면 배달 폴더를 선택하고 해당 폴더에서 배달된 수신자를 타깃팅할 수 있습니다.

      ![](assets/s_ncs_user_wizard_email02e.png)

      드롭다운 목록에서 수신자의 동작을 선택하여 필터링할 수 있습니다.

      ![](assets/s_ncs_user_wizard_email02f.png)

      >[!NOTE]
      >
      >**[!UICONTROL Include sub-folders]** 옵션을 사용하면 선택한 노드 아래의 트리 구조에 있는 폴더에 포함된 배달을 타깃팅할 수도 있습니다.

   * **[!UICONTROL Recipients included in a folder]** :이 옵션을 사용하면 트리의 특정 폴더에 포함된 프로파일을 타깃팅할 수 있습니다.
   * **[!UICONTROL A recipient]** :이 옵션을 사용하면 데이터베이스의 프로필에서 특정 수신자를 선택할 수 있습니다.
   * **[!UICONTROL A list of recipients]** :이 옵션을 사용하면 받는 사람 목록을 타깃팅할 수 있습니다. 목록은 [이 섹션](../../platform/using/creating-and-managing-lists.md)에 있습니다.
   * **[!UICONTROL User filters]** :이 옵션을 사용하면 미리 구성된 필터에 액세스하여 데이터베이스의 프로파일에 대한 필터링 기준으로 사용할 수 있습니다. 미리 구성된 필터는 [이 섹션](../../platform/using/creating-filters.md#saving-a-filter)에 표시됩니다.
   * **[!UICONTROL Exclude recipients corresponding to this segment]** 옵션을 사용하면 정의된 대상 기준을 충족하지 않는 수신자를 타깃팅할 수 있습니다. 이 옵션을 사용하려면 적절한 상자를 선택한 다음, 정의된 대로 타깃팅을 적용하여 결과 프로필을 제외합니다.

      ![](assets/s_ncs_user_wizard_email02g.png)

1. **[!UICONTROL Label]** 필드에 이 타깃팅의 이름을 입력합니다. 기본적으로 레이블은 첫 번째 타깃팅 기준의 레이블이 됩니다. 조합의 경우 명시적인 이름을 사용하는 것이 좋습니다.
1. 구성된 타깃팅을 확인하려면 **[!UICONTROL Finish]**&#x200B;을 클릭합니다.

   정의된 타깃팅 기준은 기본 대상 구성 탭의 중앙 섹션에 요약됩니다. 내용을 보려면 기준을 클릭합니다(구성 및 미리 보기). 기준을 삭제하려면 레이블 다음에 있는 십자가를 클릭합니다.

   ![](assets/s_ncs_user_wizard_email02h.png)

### 외부 받는 사람 선택 {#selecting-external-recipients}

데이터베이스에 저장되지는 않았지만 외부 파일에 저장된 수신자에 대한 배달을 시작할 수 있습니다. 예를 들어 텍스트 파일에서 가져온 수신자에게 배달을 보냅니다.

방법은 다음과 같습니다.

1. **[!UICONTROL To]** 링크를 클릭하여 배달 받는 사람을 선택합니다.
1. **[!UICONTROL Defined in an external file]** 옵션을 선택합니다.

   ![](assets/s_ncs_user_wizard_external_recipients.png)

1. 기본적으로 수신자는 데이터베이스에 가져옵니다. **[!UICONTROL Target mapping]**&#x200B;을 선택해야 합니다. 대상 매핑에 대한 자세한 내용은 [대상 매핑 선택](../../delivery/using/selecting-a-target-mapping.md)을 참조하십시오.

   **[!UICONTROL Do not import the recipients into the database]**&#x200B;을 선택할 수도 있습니다.

1. 받는 사람을 가져올 때 **[!UICONTROL File format definition...]** 링크를 클릭하여 외부 파일을 선택하고 구성합니다.

   데이터 가져오기에 대한 자세한 내용은 [이 섹션](../../platform/using/importing-data.md#step-2---source-file-selection)을 참조하십시오.

1. **[!UICONTROL Finish]**&#x200B;을 클릭하고 배달을 표준 배달로 구성합니다.

>[!CAUTION]
>
>이메일 전달을 위한 메시지 내용을 정의할 때 미러 페이지에 대한 링크를 포함하지 마십시오.이 배달 모드에서 생성할 수 없습니다.

### 제외 설정 {#customizing-exclusion-settings} 설정

주소 오류 및 품질 등급은 IAP(서비스 제공업체)에서 제공합니다. 이 정보는 배달 작업 후 수신자 프로필에서 자동으로 업데이트되며 서비스 제공업체에서 반환된 파일이 있습니다. 프로필에서는 읽기 전용으로 볼 수 있습니다.

연속적인 특정 오류 수에 도달했거나 품질 등급이 이 창에 지정된 임계값 미만인 주소를 제외하도록 선택할 수 있습니다. 데이터가 반환되지 않은 미자격 주소를 승인할지 여부를 선택할 수도 있습니다.

>[!NOTE]
>
>DM(Direct Mail) 제공에서 두 받는 사람의 이름, 성, 우편 번호 및 구/군/시 이름이 동일한 경우 이중 오류가 발생하고 중복 항목이 고려되지 않습니다.

**[!UICONTROL Exclusions]** 탭은 메시지 수를 제한하는 데 사용됩니다.

>[!NOTE]
>
>기본 매개 변수는 권장되지만 필요에 따라 설정을 조정할 수 있습니다. 하지만 이러한 옵션은 사용 및 오류가 발생하지 않도록 전문가 사용자에게만 변경해야 합니다.

기본 구성을 수정하려면 **[!UICONTROL Edit...]** 링크를 클릭합니다.

![](assets/s_ncs_user_wizard_email02i.png)

다음 옵션을 사용할 수 있습니다.

* **[!UICONTROL Exclude duplicate addresses during delivery]**. 이 옵션은 기본적으로 활성화되어 있습니다.배달 중에 중복된 이메일 주소를 제거할 수 있습니다. 적용된 전략은 Adobe Campaign 사용 방법 및 데이터베이스의 데이터 유형에 따라 다를 수 있습니다.

   옵션의 기본값은 각 배달 템플릿에 대해 구성할 수 있습니다.

   예제:

   * 뉴스레터 또는 전자 문서 전달. 데이터에 네이티브 중복 항목이 없는 경우 일부 경우에는 중복의 제외가 없습니다. 동일한 이메일 주소를 사용하는 커플의 경우 2개의 특정 개인화된 이메일 메시지를 받게 됩니다.한 명은 이름별로 각 개인에게 지정됩니다. 이 경우 이 옵션을 선택 취소할 수 있습니다.
   * 마케팅 캠페인 전달:중복 제외는 동일한 수신자에게 너무 많은 메시지를 전송하지 않도록 하는 데 중요합니다. 이 경우 이 옵션을 선택할 수 있습니다.

      이 옵션을 선택 취소하면 추가 옵션에 액세스할 수 있습니다.**[!UICONTROL Keep duplicate records (same identifier)]**. 여러 타깃팅 기준을 충족하는 수신자에게 여러 게재를 승인할 수 있도록 해줍니다.

      ![](assets/s_ncs_user_wizard_email02j.png)

* **[!UICONTROL Exclude recipients who no longer want to be contacted]** , 즉 이메일 주소가에 있는 받는 사람차단 목록(&#39;수신 거부&#39;). 전자 마케팅의 전문 윤리 및 전자 상거래에 적용되는 법을 준수하기 위해 이 옵션을 계속 선택해야 한다.
* **[!UICONTROL Exclude quarantined recipients]**. 이 옵션을 사용하면 응답하지 않는 주소가 있는 모든 프로파일을 대상에서 제외할 수 있습니다. 이 옵션을 선택된 상태로 유지하는 것이 좋습니다.

   >[!NOTE]
   >
   >격리 관리에 대한 자세한 내용은 [격리 관리 이해](../../delivery/using/understanding-quarantine-management.md)를 참조하십시오.

* **[!UICONTROL Limit delivery]** 지정된 개수의 메시지로 전송하십시오. 이 옵션을 사용하면 보낼 최대 메시지 수를 입력할 수 있습니다. 대상의 컨텐트가 표시된 메시지 수를 초과하는 경우 임의 선택 사항이 대상에 적용됩니다.

### 대상 모집단 {#reducing-the-size-of-the-target-population} 크기 줄이기

대상 인구의 크기를 줄일 수 있습니다. 이렇게 하려면 **[!UICONTROL Requested quantity]** 필드에 내보낼 받는 사람 수를 지정합니다.

![](assets/s_ncs_user_edit_del_exe_tab.png)

## 증명 메시지 받는 사람 선택 {#selecting-the-proof-target}

증명은 기본 타겟으로 보내기 전에 배달을 테스트할 수 있는 특수 메시지입니다. 메시지 양식 및 내용을 모두 승인하는 책임은 입증해야 합니다.

![](assets/do-not-localize/how-to-video.png) [비디오에서 이 기능 살펴보기](#seeds-and-proofs-video)


교정본 대상을 선택하려면 아래 단계를 따르십시오.

1. **[!UICONTROL To]** 링크를 클릭합니다.
1. **[!UICONTROL Target of the proofs]** 탭을 클릭합니다.
1. 적용할 방법을 선택하려면 **[!UICONTROL Targeting mode]** 필드를 클릭합니다.**[!UICONTROL Definition of a specific proof target]** , **[!UICONTROL Substitution of the address]** , **[!UICONTROL Seed addresses]** 또는 **[!UICONTROL Specific target and seed addresses]**.

>[!NOTE]
>
>일반적으로 증명 대상을 주 대상에 추가할 수 있습니다. 이렇게 하려면 **[!UICONTROL Main target]** 탭의 아래 섹션에서 해당 옵션을 선택합니다.

## 특정 증명 대상 정의 {#defining-a-specific-proof-target}

증명 대상을 선택할 때 **[!UICONTROL Definition of a specific proof target]** 옵션을 사용하면 데이터베이스의 프로필에서 증명 받는 사람을 선택할 수 있습니다.

기본 대상을 정의하는 경우와 같이 **[!UICONTROL Add]** 단추를 사용하여 수신자를 선택하려면 이 옵션을 선택합니다. [기본 대상 선택](../../delivery/using/steps-defining-the-target-population.md#selecting-the-main-target)을 참조하십시오.

![](assets/s_ncs_user_wizard_email01_143.png)

증명 보내기에 대한 자세한 내용은 [이 섹션](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)을 참조하십시오.

### 증명 {#using-address-substitution-in-proof}에 주소 대체 사용

데이터베이스에서 전용 수신자를 선택하는 대신 **[!UICONTROL Substitution of the address]** 옵션을 사용할 수 있습니다.

이 옵션을 사용하면 배달을 받는 사람 프로필을 사용하고 해당 이메일 주소를 증명 자료를 받을 다른 하나 이상의 주소로 바꿀 수 있습니다.

이 옵션을 선택하면 대체를 구성할 수 있는 특수 편집기를 통해 증명 주소가 채워집니다.

![](assets/s_ncs_user_wizard_email_bat_substitute.png)

구성은 다음과 같이 수행됩니다.

1. **[!UICONTROL Add]** 아이콘을 클릭하여 대체를 정의합니다.
1. 사용할 수신자 주소를 입력하거나 목록에서 선택합니다.
1. 증표에 사용할 프로파일을 선택합니다.**[!UICONTROL Profile to use]** 열에 **[!UICONTROL Random]** 값을 저장하여 대상의 프로필의 데이터를 증표에 사용합니다.

   ![](assets/s_ncs_user_wizard_email_bat_substitute_choose.png)

1. 다음 예제와 같이 기본 대상에서 프로파일을 선택하려면 **[!UICONTROL Detail]** 아이콘을 클릭합니다.

   ![](assets/s_ncs_user_wizard_email_bat_substitute_select.png)

   필요한 만큼 대체 주소를 정의할 수 있습니다.

## 시드 주소를 증명 {#using-seed-addresses-as-proof}으로 사용

교정쇄의 대상으로 **[!UICONTROL Seed addresses]**&#x200B;을 사용할 수 있습니다.이 옵션을 사용하면 기존 시드 주소 목록을 사용하거나 가져올 수 있습니다.

![](assets/s_ncs_user_wizard_email_bat_control_address.png)

>[!NOTE]
>
>시드 주소는 [시드 주소 정보](../../delivery/using/about-seed-addresses.md)에 표시됩니다.

**[!UICONTROL Specific target and Seed addresses]** 옵션을 사용하여 특정 증명 대상의 정의와 시드 주소의 사용을 결합할 수 있습니다. 관련 구성은 두 개의 개별 하위 탭에 정의됩니다.

참조 항목:

* [증명 대상 선택](#selecting-the-proof-target)
* [시드 주소 기본 정보](../../delivery/using/about-seed-addresses.md)
* [사용 사례: 기준 시드 주소 선택](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md)

## 자습서 비디오 {#seeds-and-proofs-video}

이 비디오에서는 기존 이메일에 씨드 및 교정본을 추가하는 방법과 보내는 방법을 살펴봅니다.

>[!VIDEO](https://video.tv.adobe.com/v/25606?quality=12)

추가 Campaign Classic 방법 비디오는 [여기](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=ko)에서 사용할 수 있습니다.
