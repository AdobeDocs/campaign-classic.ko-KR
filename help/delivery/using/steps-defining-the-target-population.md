---
product: campaign
title: 대상 모집단 정의
description: 대상 모집단을 정의하는 방법 알아보기
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Audiences, Proofs
role: User
exl-id: d0ed7be7-3147-4cb8-9ce7-ea51602e9048
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '1602'
ht-degree: 2%

---

# 대상 모집단 정의 {#defining-the-target-population}

각 게재에 대해 여러 유형의 대상 모집단을 정의할 수 있습니다.

* **주 대상자**: 메시지를 받을 프로필. [자세히 알아보기](steps-defining-the-target-population.md#selecting-the-main-target)
* **증명**: 유효성 검사 주기와 관련된 증명 메시지를 받는 사람입니다. [자세히 알아보기](steps-defining-the-target-population.md#defining-a-specific-proof-target)
* **시드 주소**: 게재 대상에서 제외되었지만 게재를 받을 수신자(마케팅 캠페인의 컨텍스트에서만). [자세히 알아보기](about-seed-addresses.md)
* **컨트롤 그룹**: 게재를 받지 못하는 모집단으로, 동작 및 캠페인 영향을 추적하는 데 사용됩니다(마케팅 캠페인의 컨텍스트에서만). [자세히 알아보기](../../campaign/using/marketing-campaign-target.md#defining-a-control-group).

## 게재의 기본 수신자 선택 {#selecting-the-main-target}

대부분의 경우 기본 대상은 Adobe Campaign 데이터베이스(기본 모드)에서 추출됩니다. 그러나 수신자는 외부 파일에도 저장할 수 있습니다. [이 섹션](steps-defining-the-target-population.md#selecting-external-recipients)에서 자세히 알아보십시오.

게재 수신자를 선택하려면 아래 단계를 따르십시오.

1. 게재 편집기에서 **[!UICONTROL To]**&#x200B;을(를) 선택합니다.
1. 수신자가 데이터베이스에 저장되어 있는 경우 첫 번째 옵션을 선택합니다.

   ![](assets/s_ncs_user_wizard_email02a.png)

1. **[!UICONTROL Target mapping]** 드롭다운 목록에서 대상 매핑을 선택합니다. Adobe Campaign 기본 대상 매핑은 **nms:recipient** 스키마를 기반으로 하는 **[!UICONTROL Recipients]**&#x200B;입니다.

   다른 대상 매핑을 사용할 수 있으며, 일부는 특정 구성과 관련될 수 있습니다. 대상 매핑에 대한 자세한 내용은 [대상 매핑 선택](selecting-a-target-mapping.md)을 참조하세요.

1. 제한 필터를 정의하려면 **[!UICONTROL Add]** 단추를 클릭하십시오.

   그런 다음 적용할 필터링 유형을 선택할 수 있습니다.

   ![](assets/s_ncs_user_wizard_email02b.png)

   데이터베이스에 정의된 타겟팅 유형을 사용하여 수신자를 선택할 수 있습니다. 대상 유형을 사용하려면 해당 유형을 선택하고 **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다. 각 대상에 대해 **[!UICONTROL Preview]** 탭을 클릭하여 관련 받는 사람을 표시할 수 있습니다. 특정 유형의 대상에 대해 **[!UICONTROL Refine target]** 버튼을 사용하면 여러 타깃팅 기준을 결합할 수 있습니다.

   기본적으로 제공되는 타겟 유형은 다음과 같습니다.

   * **[!UICONTROL Filtering conditions]** : 이 옵션을 사용하면 쿼리를 정의하고 결과를 표시할 수 있습니다. 쿼리를 정의하는 방법은 [이 섹션](../../platform/using/creating-filters.md#creating-an-advanced-filter)에 나와 있습니다.
   * **[!UICONTROL Subscribers of an information service]** : 이 옵션을 사용하면 만들어지는 게재에서 수신자를 타겟팅해야 하는 뉴스레터를 선택할 수 있습니다.

     ![](assets/s_ncs_user_wizard_email02c.png)

   * **[!UICONTROL Recipients of a delivery]** : 이 옵션을 사용하면 기존 게재의 수신자를 타깃팅 기준으로 정의할 수 있습니다. 그런 다음 목록에서 게재를 선택해야 합니다.

     ![](assets/s_ncs_user_wizard_email02d.png)

   * **[!UICONTROL Delivery recipients belonging to a folder]** : 이 옵션을 사용하면 게재 폴더를 선택하고 해당 폴더에서 게재 수신자를 타겟팅할 수 있습니다.

     ![](assets/s_ncs_user_wizard_email02e.png)

     드롭다운 목록에서 선택하여 수신자의 동작을 필터링할 수 있습니다.

     ![](assets/s_ncs_user_wizard_email02f.png)

     >[!NOTE]
     >
     >**[!UICONTROL Include sub-folders]** 옵션을 사용하면 선택한 노드 아래의 트리 구조에 있는 폴더에 포함된 게재를 타겟팅할 수도 있습니다.

   * **[!UICONTROL Recipients included in a folder]** : 이 옵션을 사용하면 트리의 특정 폴더에 포함된 프로필을 타겟팅할 수 있습니다.
   * **[!UICONTROL A recipient]** : 이 옵션을 사용하면 데이터베이스의 프로필에서 특정 받는 사람을 선택할 수 있습니다.
   * **[!UICONTROL A list of recipients]** : 이 옵션을 사용하면 받는 사람 목록을 타깃팅할 수 있습니다. 목록은 [이 섹션](../../platform/using/creating-and-managing-lists.md)에 표시됩니다.
   * **[!UICONTROL User filters]** : 이 옵션을 사용하면 사전 구성된 필터에 액세스하여 데이터베이스의 프로필에 대한 필터링 기준으로 사용할 수 있습니다. 미리 구성된 필터는 [이 섹션](../../platform/using/creating-filters.md#saving-a-filter)에 있습니다.
   * **[!UICONTROL Exclude recipients corresponding to this segment]** 옵션을 사용하면 정의된 대상 기준을 충족하지 않는 수신자를 타깃팅할 수 있습니다. 이 옵션을 사용하려면 적절한 상자를 선택한 다음 앞에서 정의한 대로 타겟팅을 적용하여 결과 프로필을 제외합니다.

     ![](assets/s_ncs_user_wizard_email02g.png)

1. **[!UICONTROL Label]** 필드에 이 타깃팅의 이름을 입력하십시오. 기본적으로 레이블은 첫 번째 타겟팅 기준의 레이블이 됩니다. 조합의 경우 명시적인 이름을 사용하는 것이 좋습니다.
1. 구성된 타깃팅의 유효성을 검사하려면 **[!UICONTROL Finish]**&#x200B;을(를) 클릭하십시오.

   정의된 타겟팅 기준은 기본 타겟 구성 탭의 중앙 섹션에 요약되어 있습니다. 조건을 클릭하여 해당 콘텐츠를 봅니다(구성 및 미리 보기). 기준을 삭제하려면 레이블 뒤에 있는 십자선을 클릭합니다.

   ![](assets/s_ncs_user_wizard_email02h.png)

### 외부 수신자 선택 {#selecting-external-recipients}

데이터베이스에 저장되지 않았지만 외부 파일에 저장된 수신자에 대해 게재를 시작할 수 있습니다. 예를 들어 텍스트 파일에서 가져온 수신자에게 게재를 보내겠습니다.

방법은 다음과 같습니다.

1. **[!UICONTROL To]** 링크를 클릭하여 게재 수신자를 선택합니다.
1. **[!UICONTROL Defined in an external file]** 옵션을 선택하십시오.

   ![](assets/s_ncs_user_wizard_external_recipients.png)

1. 기본적으로 수신자는 데이터베이스에서 가져옵니다. **[!UICONTROL Target mapping]**&#x200B;을(를) 선택해야 합니다. 대상 매핑에 대한 자세한 내용은 [대상 매핑 선택](selecting-a-target-mapping.md)을 참조하세요.

   **[!UICONTROL Do not import the recipients into the database]**&#x200B;을(를) 선택할 수도 있습니다.

1. 받는 사람을 가져올 때 **[!UICONTROL File format definition...]** 링크를 클릭하여 외부 파일을 선택하고 구성합니다.

   데이터 가져오기에 대한 자세한 내용은 [이 섹션](../../platform/using/executing-import-jobs.md#step-2---source-file-selection)을 참조하세요.

1. **[!UICONTROL Finish]**&#x200B;을(를) 클릭하고 게재를 표준 게재로 구성합니다.

>[!CAUTION]
>
>이메일 게재를 위한 메시지의 콘텐츠를 정의할 때 미러 페이지에 대한 링크를 포함하지 마십시오. 이 게재 모드에서는 생성할 수 없습니다.

### 제외 설정 정의 {#define-exclusion-settings}

주소 오류 및 품질 평가는 서비스 공급자(IAP)가 제공합니다. 이 정보는 게재 작업 후 수신자 프로필에 자동으로 업데이트되고, 서비스 공급자가 반환한 파일로 업데이트됩니다. 프로필에서 읽기 전용으로 볼 수 있습니다.

특정 수의 연속 오류에 도달했거나 품질 등급이 이 창에 지정된 임계값 미만인 주소는 제외하도록 선택할 수 있습니다. 데이터가 반환되지 않은 비적격 주소를 승인할지 여부도 선택할 수 있습니다.

>[!NOTE]
>
>DM 게재에서 두 수신자의 이름, 성, 우편 번호 및 도시가 동일한 경우 이중 오류가 발생하고 중복은 고려되지 않습니다.

**[!UICONTROL Exclusions]** 탭은 메시지 수를 제한하는 데 사용됩니다.

>[!NOTE]
>
>기본 매개 변수를 사용하는 것이 좋지만 필요에 따라 설정을 조정할 수 있습니다. 그러나 이러한 옵션은 오용과 오류를 방지하기 위해 전문가 사용자만 변경해야 합니다.

기본 구성을 수정하려면 **[!UICONTROL Edit...]** 링크를 클릭하십시오.

![](assets/s_ncs_user_wizard_email02i.png)

다음 옵션을 사용할 수 있습니다.

* **[!UICONTROL Exclude duplicate addresses during delivery]**. 이 옵션은 기본적으로 활성화되어 있습니다. 게재 중에 중복 이메일 주소를 제거할 수 있습니다. 적용되는 전략은 Adobe Campaign 사용 방법과 데이터베이스의 데이터 유형에 따라 달라질 수 있습니다.

  각 게재 템플릿에 대해 옵션의 기본값을 구성할 수 있습니다.

  예제:

   * 뉴스레터 또는 전자 문서 게재. 데이터에 기본 중복 항목이 없는 경우에 따라 중복 항목을 제외하지 않습니다. 동일한 이메일 주소를 구독하는 커플은 두 개의 특정 개인화된 이메일 메시지를 받을 수 있습니다. 한 개는 이름별로 각 개인에게 주소가 지정됩니다. 이 경우 이 옵션을 선택 취소할 수 있습니다.
   * 마케팅 캠페인 게재: 동일한 수신자에게 너무 많은 메시지를 보내지 않으려면 중복 제외가 필요합니다. 이 경우 이 옵션을 선택할 수 있습니다.

     이 옵션을 선택 취소하면 추가 옵션 **[!UICONTROL Keep duplicate records (same identifier)]**&#x200B;에 액세스할 수 있습니다. 이를 통해 여러 타겟팅 기준을 충족하는 수신자에게 여러 게재를 승인할 수 있습니다.

     ![](assets/s_ncs_user_wizard_email02j.png)

* **[!UICONTROL Exclude recipients who no longer want to be contacted]**(즉, 이메일 주소가 차단 목록에 추가하다에 있는 수신자(&#39;옵트아웃&#39;)). 이 옵션은 e-마케팅의 직업 윤리와 전자 상거래에 관한 법률을 준수하기 위해 선택된 상태로 유지되어야 합니다.
* **[!UICONTROL Exclude quarantined recipients]**. 이 옵션을 사용하면 주소가 응답하지 않는 프로필을 타겟에서 제외할 수 있습니다. 이 옵션은 계속 선택하는 것이 좋습니다.

  >[!NOTE]
  >
  >격리 관리에 대한 자세한 내용은 [격리 관리 이해](understanding-quarantine-management.md)를 참조하십시오.

* **[!UICONTROL Limit delivery]**&#x200B;을(를) 지정한 메시지 수만큼 보냅니다. 이 옵션을 사용하면 전송할 최대 메시지 수를 입력할 수 있습니다. 타겟의 콘텐츠가 표시된 메시지의 수를 초과하는 경우, 타겟에 무작위 선택이 적용된다.

### 대상 모집단의 크기 축소 {#reducing-the-size-of-the-target-population}

대상 모집단의 크기를 줄일 수 있습니다. 이렇게 하려면 **[!UICONTROL Requested quantity]** 필드에 내보낼 받는 사람 수를 지정합니다.

![](assets/s_ncs_user_edit_del_exe_tab.png)

## 증명 메시지 수신자 선택 {#selecting-the-proof-target}

증명은 게재를 기본 타겟에게 보내기 전에 테스트할 수 있는 특수 메시지입니다. 증명 수신자는 메시지의 양식과 콘텐츠를 모두 승인해야 합니다.

![](assets/do-not-localize/how-to-video.png) [비디오에서 이 기능 살펴보기](#seeds-and-proofs-video)


증명 대상을 선택하려면 아래 단계를 따르십시오.

1. **[!UICONTROL To]** 링크를 클릭합니다.
1. **[!UICONTROL Target of the proofs]** 탭을 클릭합니다.
1. 적용할 방법을 선택하려면 **[!UICONTROL Targeting mode]** 필드를 클릭하십시오. **[!UICONTROL Definition of a specific proof target]** , **[!UICONTROL Substitution of the address]** , **[!UICONTROL Seed addresses]** 또는 **[!UICONTROL Specific target and seed addresses]**.

>[!NOTE]
>
>일반적으로 증명의 대상을 기본 대상에 추가할 수 있습니다. 이렇게 하려면 **[!UICONTROL Main target]** 탭의 아래 섹션에서 적절한 옵션을 선택합니다.

## 특정 증명 대상 정의 {#defining-a-specific-proof-target}

증명 대상을 선택할 때 **[!UICONTROL Definition of a specific proof target]** 옵션을 사용하면 데이터베이스의 프로필에서 증명 수신자를 선택할 수 있습니다.

기본 대상을 정의하는 경우와 같이 **[!UICONTROL Add]** 단추를 사용하여 수신자를 선택하려면 이 옵션을 선택하십시오. [주 대상 선택](steps-defining-the-target-population.md#selecting-the-main-target)을 참조하세요.

![](assets/s_ncs_user_wizard_email01_143.png)

증명 전송에 대한 자세한 정보는 [이 섹션](steps-validating-the-delivery.md#sending-a-proof)을 참조하세요.

### 증명에서 주소 대체 사용 {#using-address-substitution-in-proof}

데이터베이스에서 전용 수신자를 선택하는 대신 **[!UICONTROL Substitution of the address]** 옵션을 사용할 수 있습니다.

이 옵션을 사용하면 게재의 수신자 프로필을 사용하고 이메일 주소를 증명을 받을 하나 이상의 다른 주소로 바꿀 수 있습니다.

이 옵션을 선택하면 대체를 구성할 수 있는 특수 편집기를 통해 증명 주소가 채워집니다.

![](assets/s_ncs_user_wizard_email_bat_substitute.png)

구성은 다음과 같이 수행됩니다.

1. **[!UICONTROL Add]** 아이콘을 클릭하여 대체를 정의합니다.
1. 사용할 수신자 주소를 입력하거나 목록에서 선택하십시오.
1. 증명에서 사용할 프로필 선택: 증명에서 대상 프로필의 데이터를 사용하려면 **[!UICONTROL Profile to use]** 열에 **[!UICONTROL Random]** 값을 저장하십시오.

   ![](assets/s_ncs_user_wizard_email_bat_substitute_choose.png)

1. 다음 예제와 같이 **[!UICONTROL Detail]** 아이콘을 클릭하여 기본 대상에서 프로필을 선택합니다.

   ![](assets/s_ncs_user_wizard_email_bat_substitute_select.png)

   필요한 만큼 대체 주소를 정의할 수 있습니다.

## 시드 주소를 증명으로 사용 {#using-seed-addresses-as-proof}

증명 대상으로 **[!UICONTROL Seed addresses]**&#x200B;을(를) 사용할 수 있습니다. 이 옵션을 사용하면 기존 시드 주소 목록을 사용하거나 가져올 수 있습니다.

![](assets/s_ncs_user_wizard_email_bat_control_address.png)

>[!NOTE]
>
>시드 주소는 [시드 주소 정보](about-seed-addresses.md)에 표시됩니다.

**[!UICONTROL Specific target and Seed addresses]** 옵션을 사용하여 특정 증명 대상의 정의와 시드 주소의 사용을 결합할 수 있습니다. 그런 다음 관련 구성이 두 개의 개별 하위 탭에서 정의됩니다.

다음도 참조하십시오.

* [증명 대상 선택](#selecting-the-proof-target)
* [시드 주소 정보](about-seed-addresses.md)
* [활용 사례: 기준 시드 주소 선택](use-case-selecting-seed-addresses-on-criteria.md)

## 튜토리얼 비디오 {#seeds-and-proofs-video}

이 비디오에서는 기존 이메일에 시드 및 증명을 추가하는 방법과 이를 보내는 방법을 알아봅니다.

>[!VIDEO](https://video.tv.adobe.com/v/25606?quality=12)

추가 Campaign Classic 방법 비디오를 [여기](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=ko)에서 사용할 수 있습니다.
