---
product: campaign
title: 게재 유효성 검사
description: 게재 유효성 검사
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
exl-id: c2f4d8d0-f0fe-4d1a-92fd-91edaf9729f3
source-git-commit: 690f7c4e62203127da7a7055afa0ee8ad4a2bce4
workflow-type: tm+mt
source-wordcount: '1663'
ht-degree: 5%

---

# 게재 유효성 검사 {#validating-the-delivery}

게재를 만들고 구성한 경우 기본 타겟으로 보내기 전에 유효성 검사를 해야 합니다.

방법은 다음과 같습니다.

1. **게재를 분석합니다**.이 단계에서는 전달할 메시지를 준비할 수 있습니다. [자세히 알아보기](#analyzing-the-delivery)

   분석 중에 적용된 규칙은 [이 섹션](#validation-process-with-typologies)에 나와 있습니다. 사용 가능한 유효성 검사 모드는 [승인 모드 변경](#changing-the-approval-mode) 섹션에 자세히 설명되어 있습니다.

1. **증명 보내기**:이 단계에서는 컨텐츠, URL, 개인화 등을 제어할 수 있습니다. [증명 보내기](steps-validating-the-delivery.md#sending-a-proof) 및 [특정 증명 대상 정의](steps-defining-the-target-population.md#defining-a-specific-proof-target)에서 자세히 알아보십시오.

>[!IMPORTANT]
>
>메시지 콘텐츠를 수정한 후 위의 두 단계를 실행해야 합니다.

## 게재 분석 {#analyzing-the-delivery}

분석은 대상 모집단을 계산하고 게재 콘텐츠가 준비되는 단계입니다. 완료되면 게재를 보낼 수 있습니다.

### 분석 시작 {#launching-the-analysis}

1. 게재 분석을 시작하려면 **[!UICONTROL Send]** 을 클릭합니다.
1. **[!UICONTROL Deliver as soon as possible]**&#x200B;을(를) 선택합니다.

   ![](assets/s_ncs_user_email_del_send.png)

1. 분석을 수동으로 시작하려면 **[!UICONTROL Analyze]** 을 클릭하십시오.

   진행률 표시줄에는 분석 진행률이 표시됩니다.

   ![](assets/s_ncs_user_email_del_analyze_progress.png)

   >[!NOTE]
   >
   >분석 중에 사용된 유효성 검사 규칙은 [유형화가 포함된 유효성 검사 프로세스에 설명되어 있습니다](steps-validating-the-delivery.md#validation-process-with-typologies).

1. 언제든지 **[!UICONTROL Stop]** 을 클릭하여 분석을 중지할 수 있습니다.

   ![](assets/s_ncs_user_wizard_email01_16.png)

   준비 단계 동안 메시지가 전송되지 않습니다. 따라서 위험 없이 분석을 시작하거나 취소할 수 있습니다.

   >[!IMPORTANT]
   >
   >실행 시 분석에서 게재(또는 증명)를 중지합니다. 게재(또는 증명)에 대한 모든 변경 사항 뒤에 적용할 수 있으려면 먼저 다른 분석이 뒤따라야 합니다.

1. 분석이 완료될 때까지 기다립니다.

   분석이 완료되면 창의 위쪽 섹션에는 게재 준비가 완료되었는지 또는 오류가 발생했는지 여부가 표시됩니다. 모든 유효성 검사 단계, 경고 및 오류가 나열됩니다. 색상 아이콘은 메시지 유형을 보여줍니다.
   * 파란색 아이콘은 유용한 메시지를 나타냅니다.
   * 노란색 아이콘은 중요하지 않은 처리 오류를 나타냅니다.
   * 빨간색 아이콘은 게재를 보낼 수 없는 중요한 오류를 나타냅니다.

   ![](assets/s_ncs_user_email_del_analyze_error.png)

1. 오류가 있는 경우 **[!UICONTROL Close]** 을 클릭하여 오류를 수정합니다.

1. 변경 작업을 수행한 후 **[!UICONTROL Analyze]** 을 클릭하여 분석을 다시 시작합니다.

분석 결과를 확인한 후 **[!UICONTROL Confirm delivery]** 을 클릭하여 지정된 타겟으로 메시지를 보낼 수 있습니다. 확인 메시지를 통해 게재를 시작할 수 있습니다.

![](assets/s_ncs_user_email_del_analyze_ok.png)

>[!NOTE]
>
>전송할 메시지 수가 구성과 일치하지 않는 경우 **[!UICONTROL Change the main delivery target]** 링크를 클릭합니다. 이를 통해 대상 모집단의 정의를 변경하고 분석을 다시 시작할 수 있습니다.

### 분석 설정 {#analysis-parameters}

게재 속성의 **[!UICONTROL Analysis]** 탭에서는 분석 단계 동안 메시지 준비에 대한 정보 세트를 정의할 수 있습니다.

![](assets/s_ncs_user_email_del_analyze_adv_param.png)

이 탭에서는 다음 옵션에 액세스할 수 있습니다.

* **[!UICONTROL Label and code of the delivery]** :이 섹션의 옵션은 게재 분석 단계 동안 이러한 필드의 값을 계산하는 데 사용됩니다. **[!UICONTROL Compute the execution folder during the delivery analysis]** 필드는 분석 단계 동안 이 게재 작업을 포함할 폴더의 이름을 계산합니다.
* **[!UICONTROL Approval mode]** :이 필드를 사용하면 분석이 완료되면 수동 또는 자동 배달을 정의할 수 있습니다. 검증 모드는 [승인 모드 변경](#changing-the-approval-mode) 섹션에 나와 있습니다.
* **[!UICONTROL Prepare the delivery parts in the database]** :이 옵션을 사용하면 게재 분석 성능을 향상시킬 수 있습니다. 자세한 내용은 [이 섹션](#improving-delivery-analysis)을 참조하십시오.
* **[!UICONTROL Prepare the personalization data with a workflow]** :이 옵션을 사용하면 자동 워크플로우에서 게재에 포함된 개인화 데이터를 준비할 수 있으므로 개인화 실행을 위한 상당한 성능 향상을 달성할 수 있습니다. 자세한 내용은 [개인화 최적화](personalization-fields.md#optimizing-personalization)를 참조하십시오.
* **[!UICONTROL Start job in a detached process]** :이 옵션을 사용하면 별도의 프로세스에서 게재 분석을 시작할 수 있습니다. 분석 함수는 기본적으로 Adobe Campaign 애플리케이션 서버 프로세스(웹 nlserver)를 사용합니다. 이 옵션을 선택하면 애플리케이션 서버 장애 시에도 분석이 완료됩니다.
* **[!UICONTROL Log SQL queries generated during the analysis in the journal]** :이 옵션은 분석 단계 동안 게재 저널에 SQL 쿼리 로그를 추가합니다.
* **[!UICONTROL Ignore personalization scripts during sending]** :이 옵션을 사용하면 HTML 컨텐츠에 있는 JavaScript 지시문의 해석을 무시할 수 있습니다. 전달된 컨텐츠에 그대로 표시됩니다. 이러한 지시문은 **&lt;%=** 태그와 함께 도입됩니다.

### 게재 분석 성능 개선 {#improving-delivery-analysis}

게재 준비 속도를 높이기 위해 분석을 시작하기 전에 **[!UICONTROL Prepare the delivery parts in the database]** 옵션을 선택할 수 있습니다.

이 옵션을 활성화하면 데이터베이스 내에서 직접 게재 준비를 수행하므로 분석 시간을 크게 단축할 수 있습니다.

현재 이 옵션은 다음 조건이 충족되는 경우에만 사용할 수 있습니다.
* 게재는 이메일이어야 합니다. 다른 채널은 지금은 지원되지 않습니다.
* 중간 소싱 또는 외부 공정순서를 사용해서는 안 되며 대량 납품 공정순서 유형만 사용할 수 있습니다. **[!UICONTROL Delivery properties]** 의 **[!UICONTROL General]** 탭에서 사용되는 라우팅을 확인할 수 있습니다.
* 외부 파일에서 만든 모집단은 타겟팅할 수 없습니다. 단일 게재의 경우 **[!UICONTROL Email parameters]**&#x200B;에서 **[!UICONTROL To]** 링크를 클릭하고 **[!UICONTROL Defined in the database]** 옵션이 선택되어 있는지 확인합니다. 워크플로우에 사용되는 게재의 경우 수신자가 **[!UICONTROL Delivery]** 탭에서 **[!UICONTROL Specified by the inbound event(s)]**&#x200B;인지 확인합니다.
* PostgreSQL 데이터베이스를 사용하고 있어야 합니다.

### 분석 우선 순위 구성 {#analysis-priority-}

게재가 캠페인의 일부인 경우 **[!UICONTROL Advanced]** 탭에서는 추가 옵션을 제공합니다. 이렇게 하면 동일한 캠페인에서 게재에 대한 처리 순서를 구성할 수 있습니다.

전송하기 전에 각 게재가 분석됩니다. 분석 기간은 게재 추출 파일에 따라 다릅니다. 파일 크기가 클수록 분석 시간이 길어져 다음 게재가 대기합니다.

**[!UICONTROL Message preparation by the scheduler]** 옵션을 사용하면 캠페인 워크플로우에서 게재 분석에 우선 순위를 지정할 수 있습니다.

![](assets/delivery_analysis_priority.png)

게재가 너무 큰 경우 다른 워크플로우 게재의 분석을 느리게 하지 않도록 낮은 우선 순위를 할당하는 것이 더 좋습니다.

>[!NOTE]
>
>더 큰 게재 분석으로 워크플로우의 진행 속도가 느려지지 않도록 하려면 **[!UICONTROL Schedule execution for a time of low activity]** 을(를) 똑딱거리며 실행을 예약할 수 있습니다.

## 증명 보내기 {#sending-a-proof}

메시지 구성에서 발생할 수 있는 오류를 탐지하기 위해 Adobe에서는 게재 유효성 검사 주기를 설정할 것을 강력히 권장합니다. 필요한 만큼 자주 테스트 내용을 수신자에게 보내서 콘텐츠가 승인되었는지 확인합니다. 콘텐츠를 승인하려면 변경 사항이 있을 때마다 증명을 보내야 합니다.

>[!NOTE]
>
>* 사용 가능한 유효성 검사 모드는 [승인 모드 변경](steps-validating-the-delivery.md#changing-the-approval-mode)에 자세히 설명되어 있습니다.
>* 증명 타겟의 구성은 [특정 증명 대상을 정의합니다](steps-defining-the-target-population.md#defining-a-specific-proof-target)에 설명되어 있습니다.

>



증명을 보내려면 아래 단계를 따르십시오.

1. 증명 대상이 [특정 증명 대상 정의](steps-defining-the-target-population.md#defining-a-specific-proof-target)에 설명된 대로 구성되었는지 확인합니다.
1. 게재 마법사의 맨 위 막대에서 **[!UICONTROL Send a proof]** 을 클릭합니다.

   ![](assets/s_ncs_user_email_del_send_proof.png)

1. 메시지 분석을 시작합니다. [게재 분석](steps-validating-the-delivery.md#analyzing-the-delivery)을 참조하십시오.
1. 이제 게재를 보낼 수 있습니다([게재 보내기](steps-sending-the-delivery.md) 참조).

   게재가 전송되면 증명이 게재 목록에 표시되고 자동으로 만들어지고 번호가 매겨집니다. 콘텐츠 및 속성에 액세스하려는 경우 편집할 수 있습니다. 자세한 정보는 이 [페이지](about-delivery-monitoring.md)를 참조하십시오.

   ![](assets/s_ncs_user_delivery_validation_cycle_03a.png)

   >[!NOTE]
   >
   >게재하기 위해 여러 형식(HTML 및 텍스트)을 만든 경우 창의 아래 섹션에서 증명 수신자에게 보낼 메시지 형식을 선택할 수 있습니다.

   ![](assets/s_ncs_user_email_del_send_proof_formats.png)

증명을 받는 유효성 검사 그룹에서 만든 모든 주석의 결과로 게재 콘텐츠를 수정할 수 있습니다. 변경 작업을 수행한 후 분석을 다시 실행한 다음 다른 증명을 보내야 합니다. 새로운 증명 각각에는 번호가 매겨져 게재 저널에 기록됩니다.

게재를 분석하면 로그의 **[!UICONTROL Proofs]** 하위 탭(**[!UICONTROL Audit]** 탭)을 통해 전송된 다양한 증명을 볼 수 있습니다.

![](assets/s_ncs_user_delivery_validation_cycle_03.png)

게재의 컨텐츠가 완료될 때까지 필요한 만큼 증명을 보내야 합니다. 그런 다음 게재를 기본 타겟으로 보내고 유효성 검사 주기를 닫을 수 있습니다.

게재 속성의 **[!UICONTROL Advanced]** 탭에서는 증명의 속성을 정의할 수 있습니다. 필요한 경우 수신자 제외 규칙을 무시할 수 있습니다.

![](assets/s_ncs_user_wizard_email01_145.png)

다음 옵션을 사용할 수 있습니다.

* 첫 번째 옵션을 사용하면 증명 double을 유지할 수 있습니다.
* 다음 두 옵션을 모두 사용하면 중인 수신자와 주소를 격리할 차단 목록 수 있습니다. [제외 설정 사용자 지정](steps-defining-the-target-population.md#customizing-exclusion-settings)에서 기본 대상에 대해 이러한 옵션에 대한 설명을 참조하십시오. 이러한 주소는 기본적으로 제외되는 게재 타겟과 달리, 증명 대상에 대해서는 기본적으로 유지됩니다.
* **[!UICONTROL Keep the delivery code for the proof]** 옵션을 사용하면 증표에 게재에 대해 정의된 배달 코드와 동일한 배달 코드를 제공할 수 있습니다. 이 코드는 게재 마법사의 첫 번째 단계에서 지정됩니다.
* 기본적으로 증명의 제목에는 &#39;Proof #&#39; 접두사가 붙습니다. 여기서 #은 증명의 번호입니다. **[!UICONTROL Label prefix]** 필드에서 이 접두사를 변경할 수 있습니다.

## 유형화를 사용한 유효성 검사 프로세스 {#validation-process-with-typologies}

메시지를 보내기 전에 캠페인을 분석하여 해당 콘텐츠와 구성을 승인해야 합니다. 분석 단계 동안 적용된 확인 규칙은 **유형화**&#x200B;에 정의됩니다. 기본적으로 이메일의 경우 분석은 다음 사항을 다룹니다.

* 개체 승인
* URL 및 이미지 승인
* URL 레이블 승인
* 구독 취소 링크 승인
* 증명 크기 확인
* 유효 기간 확인
* 웨이브 일정 확인

각 게재에 적용할 유형화는 게재 매개 변수의 **[!UICONTROL Typologies]** 탭에서 선택됩니다.

**[!UICONTROL Administration > Campaign execution > Typology management > Typology rules]** 노드를 통해 승인 규칙, 내용, 실행 순서 및 전체 설명을 보고 편집할 수 있습니다.

이 노드에서 새 규칙을 만들고 새 유형화를 정의할 수 있습니다. 하지만 이러한 작업은 JavaScript를 알고 있는 전문가 사용자를 위해 예약되어 있습니다.

유형화 규칙에 대한 자세한 정보는 [이 페이지](../../campaign/using/about-campaign-typologies.md)를 참조하십시오.

현재 유형화를 편집하려면 **[!UICONTROL Typology]** 필드 오른쪽에 있는 **[!UICONTROL Edit link]** 아이콘을 클릭합니다.

![](assets/s_ncs_user_email_del_typo_tab.png)

**[!UICONTROL Rule]** 탭에서는 적용할 유형화 규칙 목록을 제공합니다. 규칙을 선택하고 **[!UICONTROL Detail...]** 아이콘을 클릭하여 해당 구성을 확인합니다.

![](assets/s_ncs_user_email_del_typo_rules_edit.png)

>[!NOTE]
>
>**[!UICONTROL Arbitration]** 유형 유형화는 판매 압력 관리 프레임워크에서 사용됩니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../mrm/using/about-marketing-resource-management.md)을 참조하십시오.

## 승인 모드 변경 {#changing-the-approval-mode}

게재 속성의 **[!UICONTROL Analysis]** 탭에서는 유효성 검사 모드를 선택할 수 있습니다. 분석 중에 경고가 생성된 경우(예: 특정 문자가 게재의 주체에 입력되는 경우 등) 게재를 구성하여 여전히 실행해야 하는지 여부를 정의할 수 있습니다. 기본적으로 사용자는 분석 단계가 끝날 때 메시지 전송을 확인해야 합니다.**수동** 유효성 검사입니다.

해당 필드의 드롭다운 목록에서 다른 승인 모드를 선택합니다.

![](assets/s_ncs_user_email_del_validation_mode.png)

다음 승인 모드를 사용할 수 있습니다.

* **[!UICONTROL Manual]**:분석 단계가 끝날 때 사용자는 게재를 확인하여 전송을 시작해야 합니다. 이렇게 하려면 **[!UICONTROL Start]** 버튼을 클릭하여 게재를 시작합니다.
* **[!UICONTROL Semi-automatic]**:분석 단계에서 경고 메시지가 생성되지 않으면 전송이 자동으로 시작됩니다.
* **[!UICONTROL Automatic]**:전송은 결과와 관계없이 분석 단계가 끝날 때 자동으로 시작됩니다.
