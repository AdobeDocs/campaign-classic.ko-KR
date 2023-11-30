---
product: campaign
title: 게재 유효성 검사
description: 게재 유효성 검사 방법 알아보기
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Deliverability, Email Rendering, Proofs
role: User
exl-id: c2f4d8d0-f0fe-4d1a-92fd-91edaf9729f3
source-git-commit: 198921813ff097db0d4ba0a8203fef65bb591af7
workflow-type: tm+mt
source-wordcount: '1677'
ht-degree: 8%

---

# 게재 유효성 검사 {#validating-the-delivery}

게재를 만들고 구성한 경우 기본 타겟에게 보내기 전에 먼저 게재의 유효성을 검사해야 합니다.

방법은 다음과 같습니다.

1. **게재 분석**: 이 단계에서는 전달할 메시지를 준비할 수 있습니다. [자세히 알아보기](#analyzing-the-delivery)

   분석 시 적용되는 규칙은에 나와 있습니다. [이 섹션](#validation-process-with-typologies). 사용 가능한 유효성 검사 모드는 [승인 모드 변경](#changing-the-approval-mode) 섹션.

1. **증명 보내기**: 이 단계에서는 콘텐츠, URL, 개인화 등을 제어할 수 있습니다. 다음에서 자세히 알아보기 [증명 보내기](steps-validating-the-delivery.md#sending-a-proof) 및 [특정 증명 대상 정의](steps-defining-the-target-population.md#defining-a-specific-proof-target).

>[!IMPORTANT]
>
>위의 두 단계는 메시지 콘텐츠를 수정할 때마다 실행해야 합니다.

## 게재 분석 {#analyzing-the-delivery}

분석은 대상 모집단을 계산하고 게재 콘텐츠가 준비되는 단계입니다. 완료되면 게재를 보낼 수 있습니다.

### 분석 시작 {#launching-the-analysis}

1. 게재 분석을 시작하려면 다음을 클릭: **[!UICONTROL Send]**.
1. **[!UICONTROL Deliver as soon as possible]**&#x200B;을(를) 선택합니다.

   ![](assets/s_ncs_user_email_del_send.png)

1. 클릭 **[!UICONTROL Analyze]** 를 클릭하여 분석을 수동으로 시작합니다.

   진행률 표시줄에는 분석 진행률이 표시됩니다.

   ![](assets/s_ncs_user_email_del_analyze_progress.png)

   >[!NOTE]
   >
   >분석 시 사용되는 유효성 검사 규칙은에 설명되어 있습니다. [유형화를 사용한 유효성 검사 프로세스](steps-validating-the-delivery.md#validation-process-with-typologies) 섹션.

1. 언제든지 을 클릭하여 분석을 중지할 수 있습니다. **[!UICONTROL Stop]**.

   ![](assets/s_ncs_user_wizard_email01_16.png)

   준비 단계 동안 메시지가 전송되지 않습니다. 따라서 위험 없이 분석을 시작하거나 취소할 수 있습니다.

   >[!IMPORTANT]
   >
   >실행 시 분석이 게재(또는 증명)를 중지합니다. 게재(또는 증명)에 대한 모든 변경 후에는 적용되기 전에 다른 분석이 뒤따라야 합니다.

1. 분석이 완료될 때까지 기다립니다.

   분석이 완료되면 창의 위쪽 섹션에 게재 준비가 완료되었는지 또는 오류가 발생했는지 여부가 표시됩니다. 모든 유효성 검사 단계, 경고 및 오류가 나열됩니다. 색상이 지정된 아이콘은 메시지 유형을 나타냅니다.
   * 파란색 아이콘은 정보 메시지를 나타냅니다.
   * 노란색 아이콘은 중요하지 않은 처리 오류를 나타냅니다.
   * 빨간색 아이콘은 게재 전송을 방해하는 심각한 오류를 나타냅니다.

   ![](assets/s_ncs_user_email_del_analyze_error.png)

1. 클릭 **[!UICONTROL Close]** 오류를 수정하려면 다음을 수행합니다.

1. 변경한 후 분석을 다시 시작합니다. **[!UICONTROL Analyze]**.

분석 결과를 확인한 후 다음을 클릭할 수 있습니다 **[!UICONTROL Confirm delivery]** 지정된 대상에 메시지를 보냅니다. 확인 메시지를 통해 게재를 시작할 수 있습니다.

![](assets/s_ncs_user_email_del_analyze_ok.png)

>[!NOTE]
>
>다음을 클릭합니다. **[!UICONTROL Change the main delivery target]** 전송할 메시지 수가 구성과 일치하지 않으면 연결합니다. 이렇게 하면 대상 모집단의 정의를 변경하고 분석을 다시 시작할 수 있습니다.

### 분석 설정 {#analysis-parameters}

다음 **[!UICONTROL Analysis]** 게재 속성의 탭을 사용하여 분석 단계 동안 메시지 준비에 대한 정보 세트를 정의할 수 있습니다.

![](assets/s_ncs_user_email_del_analyze_adv_param.png)

이 탭에서는 다음 옵션에 액세스할 수 있습니다.

* **[!UICONTROL Label and code of the delivery]** : 이 섹션의 옵션은 게재 분석 단계 동안 이러한 필드의 값을 계산하는 데 사용됩니다. 다음 **[!UICONTROL Compute the execution folder during the delivery analysis]** 필드는 분석 단계 중에 이 게재 작업이 포함될 폴더의 이름을 계산합니다.
* **[!UICONTROL Approval mode]** : 이 필드에서는 분석이 완료되면 수동 또는 자동 배달을 정의할 수 있습니다. 유효성 검사 모드는 [승인 모드 변경](#changing-the-approval-mode) 섹션.
* **[!UICONTROL Prepare the delivery parts in the database]** : 이 옵션을 사용하면 게재 분석 성능을 향상시킬 수 있습니다. 자세한 내용은 [이 섹션](#improving-delivery-analysis)을 참조하십시오.
* **[!UICONTROL Prepare the personalization data with a workflow]** : 이 옵션을 사용하면 게재에 포함된 개인화 데이터를 자동 워크플로우로 준비할 수 있으므로 개인화 실행을 위한 성능을 크게 향상시킬 수 있습니다. 자세한 내용은 [개인화 최적화](personalization-fields.md#optimizing-personalization).
* **[!UICONTROL Start job in a detached process]** : 이 옵션을 사용하면 별도의 프로세스에서 게재 분석을 시작할 수 있습니다. 분석 함수는 기본적으로 Adobe Campaign 애플리케이션 서버 프로세스(web nlserver)를 사용합니다. 이 옵션을 선택하면 애플리케이션 서버에 장애가 발생하더라도 분석이 완료됩니다.
* **[!UICONTROL Log SQL queries generated during the analysis in the journal]** : 이 옵션은 분석 단계 중에 SQL 쿼리 로그를 게재 저널에 추가합니다.
* **[!UICONTROL Ignore personalization scripts during sending]** : 이 옵션을 사용하면 HTML 컨텐츠에 있는 JavaScript 지시문을 해석하지 않을 수 있습니다. 전달된 콘텐츠에 있는 그대로 표시됩니다. 이러한 지시문은 **&lt;%=** 태그).

### 게재 분석 성능 개선 {#improving-delivery-analysis}

게재 준비 속도를 높이기 위해 다음을 확인할 수 있습니다. **[!UICONTROL Prepare the delivery parts in the database]** 분석을 시작하기 전에 옵션을 선택합니다.

이 옵션을 활성화하면 게재 준비가 데이터베이스 내에서 직접 수행되므로 분석을 상당히 가속화할 수 있습니다.

현재 이 옵션은 다음 조건이 충족될 때만 사용할 수 있습니다.

* 게재는 이메일이어야 합니다. 다른 채널은 현재 지원되지 않습니다.
* 중간 소싱 또는 외부 공정순서를 사용하지 말고 일괄 게재 공정순서 유형만 사용해야 합니다. 에서 사용되는 라우팅을 확인할 수 있습니다. **[!UICONTROL General]** 의 탭 **[!UICONTROL Delivery properties]**.
* 외부 파일에서 가져온 모집단을 타깃팅할 수 없습니다. 단일 게재의 경우 **[!UICONTROL To]** 다음에서 링크: **[!UICONTROL Email parameters]** 다음을 확인하십시오. **[!UICONTROL Defined in the database]** 옵션이 선택되어 있습니다. 워크플로우에서 사용되는 게재의 경우 수신자가 **[!UICONTROL Specified by the inbound event(s)]** 다음에서 **[!UICONTROL Delivery]** 탭.
* PostgreSQL 데이터베이스를 사용하고 있어야 합니다.

### 분석 우선 순위 구성 {#analysis-priority-}

게재가 캠페인의 일부인 경우 **[!UICONTROL Advanced]** 탭은 추가 옵션을 제공합니다. 이렇게 하면 동일한 캠페인의 게재에 대한 처리 순서를 구성할 수 있습니다.

보내기 전에 각 게재를 분석합니다. 분석 기간은 게재 추출 파일에 따라 다릅니다. 파일 크기가 클수록 분석에 더 오래 걸려서 다음 게재가 대기하게 됩니다.

에 대한 옵션 **[!UICONTROL Message preparation by the scheduler]** 캠페인 워크플로우에서 게재 분석의 우선 순위를 지정할 수 있습니다.

![](assets/delivery_analysis_priority.png)

게재가 너무 큰 경우 다른 워크플로우 게재 분석이 느려지지 않도록 우선 순위를 낮게 할당하는 것이 좋습니다.

>[!NOTE]
>
>큰 게재 분석으로 워크플로우의 진행 속도가 느려지지 않도록 다음을 클릭하여 실행 일정을 잡을 수 있습니다. **[!UICONTROL Schedule execution for a time of low activity]**.

## 증명 보내기 {#sending-a-proof}

메시지 구성에서 발생할 수 있는 오류를 탐지하기 위해 Adobe에서는 게재 유효성 검사 주기를 설정할 것을 강력히 권장합니다. 필요한 만큼 자주 테스트 내용을 수신자에게 보내서 콘텐츠가 승인되었는지 확인합니다. 콘텐츠를 승인하려면 변경 사항이 있을 때마다 증명을 보내야 합니다.

>[!NOTE]
>
>사용 가능한 유효성 검사 모드는에 자세히 설명되어 있습니다. [승인 모드 변경](steps-validating-the-delivery.md#changing-the-approval-mode).

증명을 보내려면 아래 단계를 따르십시오.

1. 에 설명된 대로 증명 대상이 구성되었는지 확인합니다. [특정 증명 대상 정의](steps-defining-the-target-population.md#defining-a-specific-proof-target).

   >[!CAUTION]
   >
   >[반복 게재](../../workflow/using/recurring-delivery.md) 다음을 포함한 증명 보내기를 지원하지 않음 [대상 데이터](../../workflow/using/data-life-cycle.md#target-data) 개인화 요소.

1. 클릭 **[!UICONTROL Send a proof]** 게재 마법사의 상단 표시줄에서 을 클릭합니다.

   ![](assets/s_ncs_user_email_del_send_proof.png)

1. 메시지 분석을 시작합니다. 다음을 참조하십시오 [게재 분석](steps-validating-the-delivery.md#analyzing-the-delivery).
1. 이제 게재를 보낼 수 있습니다( 참조) [게재 보내기](steps-sending-the-delivery.md)).

   게재를 전송하면 게재 목록에 증명이 표시되고 자동으로 생성되고 번호가 매겨집니다. 콘텐츠 및 속성에 액세스하려는 경우 편집할 수 있습니다. 자세한 정보는 이 [페이지](about-delivery-monitoring.md)를 참조하십시오.

   ![](assets/s_ncs_user_delivery_validation_cycle_03a.png)

   >[!NOTE]
   >
   >게재에 대해 여러 형식(HTML 및 텍스트)을 만든 경우 창의 하단에서 증명 수신자에게 보낼 메시지 형식을 선택할 수 있습니다.

   ![](assets/s_ncs_user_email_del_send_proof_formats.png)

증명을 받는 유효성 검사 그룹에서 작성한 댓글로 게재 콘텐츠를 수정할 수 있습니다. 변경한 후 분석을 다시 시작한 다음 다른 증명을 보내야 합니다. 각 새 증명에는 번호가 매겨져 있으며 게재 저널에 기록됩니다.

게재를 분석하면 를 통해 전송된 다양한 증명을 볼 수 있습니다. **[!UICONTROL Proofs]** 로그의 하위 탭(**[!UICONTROL Audit]** 탭).

![](assets/s_ncs_user_delivery_validation_cycle_03.png)

게재 콘텐츠가 완료될 때까지 필요한 만큼 증명을 보내야 합니다. 그런 다음 게재를 기본 타겟으로 보내고 유효성 검사 주기를 닫을 수 있습니다.

다음 **[!UICONTROL Advanced]** 게재 속성 탭에서는 증명의 속성을 정의할 수 있습니다. 필요한 경우 수신자 제외 규칙을 재정의할 수 있습니다.

![](assets/s_ncs_user_wizard_email01_145.png)

다음 옵션을 사용할 수 있습니다.

* 첫 번째 옵션을 사용하면 증명이 두 번 표시되도록 할 수 있습니다.
* 다음 두 옵션 모두 수신자의 차단 목록 및 주소를 격리할 수 있도록 해줍니다. 의 기본 대상에 대한 이러한 옵션 설명을 참조하십시오. [제외 설정 사용자 지정](steps-defining-the-target-population.md#customizing-exclusion-settings). 기본적으로 이러한 주소가 제외되는 게재 대상과 달리, 게재 대상은 기본적으로 증명 대상으로 유지됩니다.
* 다음 **[!UICONTROL Keep the delivery code for the proof]** 옵션을 사용하면 증명에 관련된 게재에 대해 정의된 것과 동일한 게재 코드를 제공할 수 있습니다. 이 코드는 게재 마법사의 첫 번째 단계에서 지정됩니다.
* 기본적으로 증명 제목에는 &#39;Proof #&#39;가 붙습니다. 여기서 #은 증명 번호입니다. 에서 이 접두사를 변경할 수 있습니다. **[!UICONTROL Label prefix]** 필드.

## 유형화를 사용한 유효성 검사 프로세스 {#validation-process-with-typologies}

메시지를 보내기 전에 캠페인을 분석하여 콘텐츠와 구성을 승인해야 합니다. 분석 단계 동안 적용된 확인 규칙은 **유형화**. 기본적으로 이메일의 경우, 분석은 다음 사항을 다룹니다.

* 객체 승인
* URL 및 이미지 승인
* URL 레이블 승인
* 구독 취소 링크 승인
* 증명 크기 확인
* 유효 기간 확인
* 예약된 예약된 예약된 일괄 처리 확인

각 게재에 적용할 유형화는에서 선택합니다. **[!UICONTROL Typologies]** 게재 매개 변수의 탭

을(를) 통해 승인 규칙, 콘텐츠, 실행 순서 및 전체 설명을 보고 편집할 수 있습니다. **[!UICONTROL Administration > Campaign execution > Typology management > Typology rules]** 노드.

이 노드에서 새 규칙을 만들고 새 유형화를 정의할 수 있습니다. 그러나 이러한 작업은 JavaScript를 알고 있는 전문가 사용자용으로 예약되어 있습니다.

유형화 규칙에 대한 자세한 내용은 [이 페이지](../../campaign-opt/using/about-campaign-typologies.md).

현재 유형화를 편집하려면 **[!UICONTROL Edit link]** 아이콘 의 오른쪽 **[!UICONTROL Typology]** 필드.

![](assets/s_ncs_user_email_del_typo_tab.png)

다음 **[!UICONTROL Rule]** 탭은 적용할 유형화 규칙 목록을 제공합니다. 규칙을 선택하고 **[!UICONTROL Detail...]** 구성 보기 아이콘:

![](assets/s_ncs_user_email_del_typo_rules_edit.png)

>[!NOTE]
>
>**[!UICONTROL Arbitration]** 영업 압력 관리의 틀 안에서 유형 유형화를 사용한다. 이 작업에 대한 자세한 정보는 [이 섹션](../../mrm/using/about-marketing-resource-management.md)을 참조하십시오.

## 승인 모드 변경 {#changing-the-approval-mode}

다음 **[!UICONTROL Analysis]** 게재 속성 탭에서는 유효성 검사 모드를 선택할 수 있습니다. 분석 중에 경고가 생성되는 경우(예: 특정 문자가 게재 주제에 강조 표시되는 경우 등) 게재를 구성하여 계속 실행할지 여부를 정의할 수 있습니다. 사용자는 기본적으로 분석 단계가 끝나면 메시지 전송을 확인해야 합니다. 이를 **수동** 유효성 검사라고 합니다.

해당 필드의 드롭다운 목록에서 다른 승인 모드를 선택합니다.

![](assets/s_ncs_user_email_del_validation_mode.png)

다음 승인 모드를 사용할 수 있습니다.

* **[!UICONTROL Manual]**: 분석 단계가 끝날 때 사용자는 전송을 확인하려면 게재를 확인해야 합니다. 이렇게 하려면 **[!UICONTROL Start]** 버튼을 클릭하여 게재를 시작합니다.
* **[!UICONTROL Semi-automatic]**: 분석 단계에서 경고 메시지가 생성되지 않는 경우 전송이 자동으로 시작됩니다.
* **[!UICONTROL Automatic]**: 결과에 관계없이 분석 단계가 끝날 때 전송이 자동으로 시작됩니다.
