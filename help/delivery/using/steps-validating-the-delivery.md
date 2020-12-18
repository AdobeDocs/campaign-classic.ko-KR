---
solution: Campaign Classic
product: campaign
title: 게재 유효성 검사
description: 게재 유효성 검사
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
translation-type: tm+mt
source-git-commit: 6d5dbc16ed6c6e5a2e62ceb522e2ccd64b142825
workflow-type: tm+mt
source-wordcount: '1667'
ht-degree: 5%

---


# 게재 유효성 검사 {#validating-the-delivery}

배달을 만들고 구성한 경우 기본 타겟으로 전송하기 전에 해당 배달의 유효성을 확인해야 합니다.

방법은 다음과 같습니다.

1. **배달 분석**:이 단계에서는 전달할 메시지를 준비할 수 있습니다. [배달 분석](#analyzing-the-delivery)을 참조하십시오.

   분석 중에 적용된 규칙은 [이 섹션](#validation-process-with-typologies)에 있습니다. 사용 가능한 유효성 검사 모드는 [승인 모드 변경](#changing-the-approval-mode) 섹션에 자세히 설명되어 있습니다.

1. **증거 자료 보내기**:이 단계에서는 컨텐츠, URL, 개인화 필드 등을 승인할 수 있습니다. [증명 보내기](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof) 및 [특정 증명 대상 정의](../../delivery/using/steps-defining-the-target-population.md#defining-a-specific-proof-target)를 참조하십시오.

>[!IMPORTANT]
>
>이 두 단계는 메시지 내용을 수정한 후 모두 수행해야 합니다.

## 배달 {#analyzing-the-delivery} 분석 중

분석은 대상 인구를 계산하여 게재 컨텐츠가 준비되는 단계입니다. 완료되면 배송을 보낼 준비가 됩니다.

### 분석 시작 중 {#launching-the-analysis}

1. 배달 분석을 시작하려면 **[!UICONTROL Send]**&#x200B;을 클릭합니다.
1. **[!UICONTROL Deliver as soon as possible]**&#x200B;을(를) 선택합니다.

   ![](assets/s_ncs_user_email_del_send.png)

1. 분석을 수동으로 시작하려면 **[!UICONTROL Analyze]**&#x200B;을 클릭합니다.

   진행률 표시줄에는 분석 진행 상태가 표시됩니다.

   ![](assets/s_ncs_user_email_del_analyze_progress.png)

   >[!NOTE]
   >
   >분석 중에 사용되는 유효성 검사 규칙은 [유형 유형](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies) 섹션이 있는 유효성 검사 프로세스에 설명되어 있습니다.

1. **[!UICONTROL Stop]**&#x200B;을 클릭하여 분석을 언제든지 중지할 수 있습니다.

   ![](assets/s_ncs_user_wizard_email01_16.png)

   준비 단계 중에는 메시지가 전송되지 않습니다. 따라서 위험 없이 분석을 시작하거나 취소할 수 있습니다.

   >[!IMPORTANT]
   >
   >분석이 실행되면 게재(또는 증명)가 중지됩니다. 게재(또는 증명)에 대한 변경 사항은 적용되기 전에 다른 분석이 뒤따라야 합니다.

1. 분석이 완료될 때까지 기다립니다.

   분석이 완료되면 창의 위쪽 섹션은 배달 준비가 완료되었는지 또는 오류가 발생했는지 여부를 나타냅니다. 모든 유효성 검사 단계, 경고 및 오류가 표시됩니다. 컬러 아이콘은 메시지 유형을 보여줍니다.
   * 파란색 아이콘은 유용한 메시지를 나타냅니다.
   * 노란색 아이콘은 중요하지 않은 처리 오류를 나타냅니다.
   * 빨간색 아이콘은 배달 전송을 방해하는 중요한 오류를 나타냅니다.

   ![](assets/s_ncs_user_email_del_analyze_error.png)

1. 오류가 있는 경우 **[!UICONTROL Close]**&#x200B;을 클릭하여 오류를 수정합니다.

1. 변경한 후 **[!UICONTROL Analyze]**&#x200B;을(를) 클릭하여 분석을 다시 시작합니다.

분석 결과를 확인한 후 **[!UICONTROL Confirm delivery]**&#x200B;을 클릭하여 지정된 타겟으로 메시지를 보낼 수 있습니다. 확인 메시지를 사용하여 배달을 시작할 수 있습니다.

![](assets/s_ncs_user_email_del_analyze_ok.png)

>[!NOTE]
>
>보낼 메시지 수가 구성과 일치하지 않으면 **[!UICONTROL Change the main delivery target]** 링크를 클릭합니다. 이를 통해 대상 모집단 정의를 변경하고 분석을 다시 시작할 수 있습니다.

### 분석 매개 변수 {#analysis-parameters}

배달 속성의 **[!UICONTROL Analysis]** 탭에서는 분석 단계 중 메시지 준비에 대한 정보 집합을 정의할 수 있습니다.

![](assets/s_ncs_user_email_del_analyze_adv_param.png)

이 탭에서는 다음 옵션에 액세스할 수 있습니다.

* **[!UICONTROL Label and code of the delivery]** :이 섹션의 옵션은 배달 분석 단계 중 이러한 필드의 값을 계산하는 데 사용됩니다. **[!UICONTROL Compute the execution folder during the delivery analysis]** 필드는 분석 단계 동안 이 배달 작업을 포함할 폴더의 이름을 계산합니다.
* **[!UICONTROL Approval mode]** :이 필드를 사용하면 분석이 완료되면 수동 또는 자동 배달을 정의할 수 있습니다. 유효성 검사 모드는 [승인 모드 변경](#changing-the-approval-mode) 섹션에 표시됩니다.
* **[!UICONTROL Prepare the delivery parts in the database]** :이 옵션을 사용하면 배달 분석 성능을 개선할 수 있습니다. 자세한 내용은 [이 섹션](#improving-delivery-analysis)을 참조하십시오.
* **[!UICONTROL Prepare the personalization data with a workflow]** :이 옵션을 사용하면 자동 워크플로우에서 전달에 포함된 개인화 데이터를 준비할 수 있으므로 개인화 실행을 위한 성능을 크게 향상시킬 수 있습니다. 자세한 내용은 [개인화 최적화](../../delivery/using/personalization-fields.md#optimizing-personalization)를 참조하십시오.
* **[!UICONTROL Start job in a detached process]** :이 옵션을 사용하면 별도의 프로세스에서 배달 분석을 시작할 수 있습니다. 분석 함수는 기본적으로 Adobe Campaign 응용 프로그램 서버 프로세스(웹 클라이언트 서버)를 사용합니다. 이 옵션을 선택하면 응용 프로그램 서버가 실패한 경우에도 분석이 완료되도록 합니다.
* **[!UICONTROL Log SQL queries generated during the analysis in the journal]** :이 옵션은 분석 단계 동안 배달 저널에 SQL 쿼리 로그를 추가합니다.
* **[!UICONTROL Ignore personalization scripts during sending]** :이 옵션을 사용하면 HTML 컨텐츠에 있는 JavaScript 지시문의 해석을 우회할 수 있습니다. 배달된 컨텐츠에 그대로 표시됩니다. 이러한 지시문은 **&lt;%=** 태그와 함께 도입됩니다.

### 배달 분석 성능 개선 {#improving-delivery-analysis}

배달 준비 속도를 높이기 위해 분석을 시작하기 전에 **[!UICONTROL Prepare the delivery parts in the database]** 옵션을 확인할 수 있습니다.

이 옵션을 활성화하면 배달 준비 작업이 데이터베이스 내에서 직접 수행되므로 분석을 크게 가속화할 수 있습니다.

현재 이 옵션은 다음 조건을 충족하는 경우에만 사용할 수 있습니다.
* 배달은 이메일이어야 합니다. 다른 채널은 현재 지원되지 않습니다.
* 중간 소싱 또는 외부 공정순서를 사용해서는 안 되며, 일괄 납품 공정순서 유형만 사용해야 합니다. **[!UICONTROL Delivery properties]**&#x200B;의 **[!UICONTROL General]** 탭에서 사용되는 라우팅을 확인할 수 있습니다.
* 외부 파일에서 들어오는 모집단은 대상으로 지정할 수 없습니다. 단일 전달의 경우 **[!UICONTROL Email parameters]**&#x200B;에서 **[!UICONTROL To]** 링크를 클릭하고 **[!UICONTROL Defined in the database]** 옵션이 선택되어 있는지 확인합니다. 워크플로우에 사용된 배달을 보려면 받는 사람이 **[!UICONTROL Delivery]** 탭에서 **[!UICONTROL Specified by the inbound event(s)]**&#x200B;인지 확인하십시오.
* PostgreSQL 데이터베이스를 사용하고 있어야 합니다.

### 분석 우선 순위 구성 {#analysis-priority-}

배달이 캠페인에 포함된 경우 **[!UICONTROL Advanced]** 탭에서는 추가 옵션을 제공합니다. 이렇게 하면 동일한 캠페인에서 배달을 위한 처리 순서를 구성할 수 있습니다.

보내기 전에 각 배달이 분석됩니다. 분석 기간은 배달 추출 파일에 따라 다릅니다. 파일 크기가 클수록 분석이 더 오래 걸리고 다음 배달이 대기합니다.

**[!UICONTROL Message preparation by the scheduler]**&#x200B;에 대한 옵션을 사용하여 캠페인 워크플로우에서 배달 분석의 우선 순위를 지정할 수 있습니다.

![](assets/delivery_analysis_priority.png)

배달이 너무 크면 다른 워크플로우 전달에 대한 분석이 느려지지 않도록 낮은 우선 순위를 할당해야 합니다.

>[!NOTE]
>
>전달 분석이 워크플로우의 진행 속도를 저하시키지 않도록 **[!UICONTROL Schedule execution for a time of low activity]**&#x200B;을(를) 똑딱거리며 실행을 예약할 수 있습니다.

## 증명 보내기 {#sending-a-proof}

메시지 구성에서 발생할 수 있는 오류를 탐지하기 위해 Adobe에서는 게재 유효성 검사 주기를 설정할 것을 강력히 권장합니다. 필요한 만큼 자주 테스트 내용을 수신자에게 보내서 콘텐츠가 승인되었는지 확인합니다. 콘텐츠를 승인하려면 변경 사항이 있을 때마다 증명을 보내야 합니다.

>[!NOTE]
>
>* 사용 가능한 유효성 검사 모드는 [승인 모드 변경](../../delivery/using/steps-validating-the-delivery.md#changing-the-approval-mode)에 자세히 설명되어 있습니다.
>* 증명 대상의 구성은 [특정 증명 대상 정의](../../delivery/using/steps-defining-the-target-population.md#defining-a-specific-proof-target)에서 설명합니다.

>



증명을 보내려면 아래 단계를 따르십시오.

1. 증명 대상이 [특정 증명 대상 정의](../../delivery/using/steps-defining-the-target-population.md#defining-a-specific-proof-target)에 설명된 대로 구성되었는지 확인합니다.
1. 배달 마법사의 상단 막대에서 **[!UICONTROL Send a proof]**&#x200B;을 클릭합니다.

   ![](assets/s_ncs_user_email_del_send_proof.png)

1. 메시지 분석을 시작합니다. [배달 분석](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery)을 참조하십시오.
1. 이제 배달을 보낼 수 있습니다([배달](../../delivery/using/steps-sending-the-delivery.md) 전송 참조).

   배달이 전송되면 증명 자료가 배달 목록에 표시되고 자동으로 생성되고 번호가 지정됩니다. 컨텐츠와 속성에 액세스하려면 편집할 수 있습니다. 자세한 정보는 이 [페이지](../../delivery/using/about-delivery-monitoring.md)를 참조하십시오.

   ![](assets/s_ncs_user_delivery_validation_cycle_03a.png)

   >[!NOTE]
   >
   >전달을 위해 여러 형식(HTML 및 텍스트)을 만든 경우 창의 아래쪽 섹션에서 자격 증명 받는 사람에게 보낼 메시지의 형식을 선택할 수 있습니다.

   ![](assets/s_ncs_user_email_del_send_proof_formats.png)

증명을 받는 검증 그룹에 의해 작성된 주석 결과로 전달 내용을 수정할 수 있습니다. 변경 작업을 수행한 후 분석을 다시 실행한 다음 다른 증거를 전송해야 합니다. 각 새로운 증명 자료는 번호가 매겨져 배달 저널에 기록됩니다.

배달을 분석하면 로그의 **[!UICONTROL Proofs]** 하위 탭(**[!UICONTROL Audit]** 탭)을 통해 보낸 다양한 교정본을 볼 수 있습니다.

![](assets/s_ncs_user_delivery_validation_cycle_03.png)

전달 내용이 완료될 때까지 필요한 만큼 교정본을 보내야 합니다. 그런 다음 배달을 기본 타겟으로 보내고 유효성 검사 주기를 닫을 수 있습니다.

배달 속성의 **[!UICONTROL Advanced]** 탭에서는 증명 자료의 속성을 정의할 수 있습니다. 필요한 경우 수신자 제외 규칙을 재정의할 수 있습니다.

![](assets/s_ncs_user_wizard_email01_145.png)

다음 옵션을 사용할 수 있습니다.

* 첫 번째 옵션을 사용하면 교정 인쇄본을 두 배로 유지할 수 있습니다.
* 다음 옵션 모두에 있는 받는 사람차단 목록과 주소를 격리 상태로 유지할 수 있습니다. [제외 설정 사용자 지정](../../delivery/using/steps-defining-the-target-population.md#customizing-exclusion-settings)에서 기본 대상에 대한 이러한 옵션에 대한 설명을 참조하십시오. 이러한 주소가 기본적으로 제외되는 배달 대상과 달리 증명 대상에 대해서는 기본적으로 보관됩니다.
* **[!UICONTROL Keep the delivery code for the proof]** 옵션을 사용하면 전달 내용과 관련된 배달에 대해 정의된 것과 동일한 배달 코드를 증표에 제공할 수 있습니다. 이 코드는 배달 마법사의 첫 번째 단계에서 지정됩니다.
* 기본적으로 증빙 문서의 제목에는 &#39;Proof #&#39;라는 접두사가 붙으며 여기서 #은 증명 번호의 번호입니다. **[!UICONTROL Label prefix]** 필드에서 이 접두어를 변경할 수 있습니다.

## {#validation-process-with-typologies} 유형 유형이 있는 유효성 검사 프로세스

메시지를 보내기 전에 캠페인을 분석하여 내용과 구성을 승인해야 합니다. 분석 단계 동안 적용된 확인 규칙은 **분류 항목**&#x200B;에 정의됩니다. 기본적으로 이메일의 경우 분석은 다음 사항을 다룹니다.

* 객체 승인
* URL 및 이미지 승인
* URL 레이블 승인
* 구독 취소 링크 승인
* 교정본 크기 확인
* 유효성 기간 확인
* 파도 예약 확인

각 전달에 적용할 유형이 전달 매개 변수의 **[!UICONTROL Typologies]** 탭에서 선택됩니다.

**[!UICONTROL Administration > Campaign execution > Typology management > Typology rules]** 노드를 통해 승인 규칙, 해당 컨텐트, 실행 순서 및 전체 설명을 보고 편집할 수 있습니다.

이 노드에서 새 규칙을 만들고 새 유형을 정의할 수 있습니다. 이러한 작업은 JavaScript를 알고 있는 전문가 사용자용으로 예약되어 있습니다.

유형 규칙 유형에 대한 자세한 내용은 [캠페인 유형 지정 정보](../../campaign/using/about-campaign-typologies.md)를 참조하십시오.

현재 유형을 편집하려면 **[!UICONTROL Typology]** 필드 오른쪽에 있는 **[!UICONTROL Edit link]** 아이콘을 클릭합니다.

![](assets/s_ncs_user_email_del_typo_tab.png)

**[!UICONTROL Rule]** 탭에는 적용할 유형 규칙 목록이 있습니다. 규칙을 선택하고 **[!UICONTROL Detail...]** 아이콘을 클릭하여 해당 구성을 봅니다.

![](assets/s_ncs_user_email_del_typo_rules_edit.png)

>[!NOTE]
>
>**[!UICONTROL Arbitration]** 유형 유형 유형은 판매 압력 관리의 프레임워크에서 사용됩니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../campaign/using/about-marketing-resource-management.md)을 참조하십시오.

## 승인 모드 {#changing-the-approval-mode} 변경

배달 속성에 대한 **[!UICONTROL Analysis]** 탭에서는 유효성 검사 모드를 선택할 수 있습니다. 분석 중에 경고가 생성되는 경우(예: 특정 문자가 전달 주제의 제목에 삽입되는 경우 등) 게재를 구성하여 여전히 실행되어야 하는지 여부를 정의할 수 있습니다. 기본적으로 사용자는 분석 단계가 끝날 때 메시지 전송을 확인해야 합니다.이것은 **manual** 유효성 검사입니다.

해당 필드의 드롭다운 목록에서 다른 승인 모드를 선택합니다.

![](assets/s_ncs_user_email_del_validation_mode.png)

다음 승인 모드를 사용할 수 있습니다.

* **[!UICONTROL Manual]**:분석 단계가 끝나면 전송을 시작하려면 사용자가 배달을 확인해야 합니다. 이렇게 하려면 **[!UICONTROL Start]** 단추를 클릭하여 배달을 시작합니다.
* **[!UICONTROL Semi-automatic]**:분석 단계가 경고 메시지를 생성하지 않는 경우 전송이 자동으로 시작됩니다.
* **[!UICONTROL Automatic]**:전송은 결과와 관계없이 분석 단계가 끝날 때 자동으로 시작됩니다.
