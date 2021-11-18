---
product: campaign
title: 마케팅 리소스 관리
description: 마케팅 리소스 관리 방법 알아보기
audience: campaign
content-type: reference
topic-tags: tasks--resources-and-budgets
exl-id: f661e1d1-de2f-4c6a-bbff-e3ffcd1831f0
source-git-commit: f000cb8bae164c22d1ede15db4e763cf50530674
workflow-type: tm+mt
source-wordcount: '1386'
ht-degree: 0%

---

# 마케팅 리소스 관리{#managing-marketing-resources}

![](../../assets/v7-only.svg)

Adobe Campaign을 사용하면 캠페인 수명 주기에 포함된 마케팅 리소스를 관리하고 추적할 수 있습니다. 이러한 마케팅 리소스는 브로셔, 시각적 지원 또는 여러 운영자와 관련된 기타 커뮤니케이션 매체가 될 수 있습니다.

Adobe Campaign을 통해 관리되는 각 마케팅 리소스에 대해 언제든지 상태 및 내역을 추적하고 현재 버전을 볼 수 있습니다.

## 마케팅 리소스 추가 {#adding-a-marketing-resource}

마케팅 리소스는 **[!UICONTROL Campaigns]** 탭.

리소스를 추가하려면 **[!UICONTROL Create]** 버튼을 클릭합니다.

![](assets/s_ncs_user_mkg_resource_add.png)

Adobe Campaign 서버에서 리소스를 사용할 수 있도록 하려면 편집기 중간 영역에 리소스를 드래그하여 놓아 원하는 리소스를 추가해야 합니다. 또한 **[!UICONTROL Upload file to server...]** 링크를 클릭합니다.

![](assets/s_ncs_user_mkg_resource_file.png)

확인 메시지를 통해 업로드를 시작할 수 있습니다.

업로드가 완료되면 리소스가 사용 가능한 리소스 목록에 추가됩니다. Adobe Campaign 운영자가 액세스할 수 있습니다. QA 팀은 **[!UICONTROL Preview]** 탭), 복사본을 만들어 수정하거나 서버에서 파일을 업데이트합니다( **[!UICONTROL Edit]** 탭).

![](assets/s_ncs_user_mkg_resource_extract.png)

을(를) 클릭합니다. **[!UICONTROL General]** 탭하여 이 리소스를 모니터링, 추적 및 승인하는 운영자 또는 운영자 그룹을 선택합니다. 검토자 선택은 **[!UICONTROL Advanced parameters]** 링크를 클릭합니다.

* 리소스가 할당된 연산자는 리소스를 추적할 책임이 있습니다.
* 승인 운영자는 마케팅 리소스를 승인해야 합니다. 리소스 유효성 검사 프로세스가 시작되면 알림을 받게 됩니다.

   검토자를 선택하지 않으면 리소스는 **[!UICONTROL cannot be]** 승인을 받습니다.

* 필요한 경우 교정을 지정할 수도 있습니다.

리소스에 대한 (지시) 가용성 날짜를 지정할 수 있습니다. 이 날짜 이후에는 **[!UICONTROL Late]** 상태.

## 리소스에 대한 공동 작업 {#collaborative-work-on-resources}

마케팅 리소스를 수정 및 업데이트할 수 있으며, 필요한 경우 다른 Adobe Campaign 운영자에게 알립니다. 다음을 수행할 수 있습니다.

* 리소스를 수정하려면 로컬에서 리소스를 다운로드하십시오.
* 서버의 파일을 업데이트하고 다른 연산자가 액세스할 수 있도록 합니다.
* 다른 연산자의 수정을 금지하려면 리소스를 잠급니다.

>[!NOTE]
>
>다음 **[!UICONTROL History]** 탭에는 리소스에 대한 다운로드 및 업데이트 로그가 포함되어 있습니다. 다음 **[!UICONTROL Details]** 버튼을 사용하면 선택한 버전을 볼 수 있습니다.

### 리소스 잠금/잠금 해제 {#locking-unlocking-a-resource}

리소스가 만들어지면 마케팅 리소스 대시보드에서 리소스를 사용할 수 있으며 운영자가 리소스를 편집하고 수정할 수 있습니다.

연산자가 리소스에 대해 작업하려는 경우 다른 연산자가 동시에 리소스를 수정하지 못하도록 작업을 시작하기 전에 잠그는 것이 좋습니다. 그런 다음 리소스가 예약됩니다. 액세스할 수 있는 상태로 유지되지만 다른 연산자가 서버에 게시하거나 업데이트할 수 없습니다.

특수 메시지는 액세스를 시도하는 모든 운영자에게 알립니다:

![](assets/s_ncs_user_mkg_resource_locked.png)

다음 **[!UICONTROL Tracking]** 탭에는 리소스를 잠근 연산자의 이름과 계획된 갱신 날짜가 표시됩니다.

![](assets/s_ncs_user_mkg_resource_locked_date.png)

리소스를 잠그려면 리소스 다음에 **[!UICONTROL Lock]** 리소스 대시보드의 버튼.

![](assets/s_ncs_user_mkg_resource_lock.png)

에서 계획된 반품 일자를 표시할 수 있습니다 **[!UICONTROL Tracking]** 리소스의 탭입니다.

![](assets/s_ncs_user_mkg_resource_lock_date.png)

이 정보를 사용하면 다른 Adobe Campaign 운영자에게 리소스 잠금이 해제되는 날짜를 알려줍니다.

리소스가 업데이트되면 자동으로 잠금 해제되고 모든 연산자가 다시 사용할 수 있게 됩니다.

필요한 경우 대시보드에서 수동으로 잠금을 해제할 수도 있습니다.

>[!NOTE]
>
>리소스를 잠근 연산자와 관리자 권한이 있는 연산자만 리소스의 잠금을 해제할 수 있습니다.

### 토론 포럼 {#discussion-forums}

각 리소스에 대해 **[!UICONTROL Forum]** 탭에서 참가자가 정보를 교환할 수 있습니다.

[토론 포럼](../../mrm/using/discussion-forums.md) Adobe Campaign에서 토론 포럼이 작동하는 방식을 설명합니다.

## 마케팅 리소스의 수명 주기 {#life-cycle-of-a-marketing-resource}

리소스가 만들어지면 Adobe Campaign 연산자가 리소스를 디자인, 교정, 승인 및 게시하도록 지정됩니다. 이러한 캠페인에 대해 기간을 결정할 수 있습니다.

다음 **[!UICONTROL Tracking]** 탭에서 리소스에 대해 수행된 작업을 모니터링할 수 있습니다. 승인, 승인 참조, 관련 주석 또는 게시

다음 **[!UICONTROL History]** 탭에는 이 리소스에 대해 수행된 파일 전송이 표시됩니다.

### 승인 프로세스 {#approval-process}

예상 가용 일자가 리소스 세부 정보에 지정된 경우 **[!UICONTROL Tracking]** 탭. 이 날짜에 도달하면 다음을 사용하여 승인 프로세스를 실행할 수 있습니다 **[!UICONTROL Submit for approval]** 리소스 대시보드의 버튼. 그런 다음 리소스 상태가 **[!UICONTROL Approval in progress]**.

를 통해 리소스를 승인할 수 있습니다 **[!UICONTROL Approve resource]** 버튼을 클릭합니다.

![](assets/s_ncs_user_task_valid_date.png)

그러면 승인된 운영자는 승인을 수락하거나 거부할 수 있습니다. 이 작업은 다음 중 한 방법으로 수행할 수 있습니다. (알림 메시지에서 링크를 클릭하여) 또는 콘솔을 통해(를) 전송된 이메일 메시지를 통해 **[!UICONTROL Approve]** ) 단추를 클릭합니다.

승인 창에서 댓글을 입력할 수 있습니다.

![](assets/s_ncs_user_mkg_resource_valid_ok.png)

다음 **[!UICONTROL Tracking]** 탭에서는 모든 연산자가 승인 프로세스의 다양한 단계를 추적할 수 있습니다.

![](assets/s_ncs_user_mkg_resource_log.png)

>[!NOTE]
>
>각 마케팅 리소스에 대해 지정된 검토자 외에도 관리자 권한이 있는 운영자와 리소스 관리자가 마케팅 리소스를 승인할 수 있습니다.

### 리소스 게시 {#publishing-a-resource}

승인되면 마케팅 리소스를 게시해야 합니다. 게시 프로세스는 회사 요구 사항에 따라 특정 구현이 적용되어야 합니다. 즉, 엑스트라넷 또는 다른 서버에 리소스를 게시할 수 있으며 특정 정보를 외부 서비스 공급자 등으로 보낼 수 있습니다.

리소스를 게시하려면 **[!UICONTROL Publish]** 마케팅 리소스 대시보드의 편집 영역에 있는 단추.

![](assets/s_ncs_user_mkg_resource_available.png)

워크플로우를 통해 리소스 게시를 자동화할 수도 있습니다.

리소스를 게시하면 다른 작업에서 리소스를 사용할 수 있게 됩니다(예: ). 게시와 같은 게시는 리소스의 특성에 따라 다릅니다. 전단지의 경우, 게시란 파일을 프린터에 보내는 것을 의미하며 웹 에이전시의 경우 웹 사이트에 게시하는 등을 의미합니다.

Adobe Campaign을 게시하려면 적절한 워크플로우를 만들어 리소스에 연결해야 합니다. 이렇게 하려면 **[!UICONTROL Advanced settings]** 리소스의 상자를 선택한 다음, **[!UICONTROL Post-processing]** 필드.

![](assets/mrm_asset_postprocessing_workflow.png)

워크플로우가 실행됩니다.

* 검토자가 **[!UICONTROL Publish resource]** 링크(또는 검토자가 정의되지 않은 경우 리소스를 담당하는 사람)입니다.
* 마케팅 리소스 만들기 작업을 통해 리소스를 관리하는 경우 작업이 **[!UICONTROL Finished]**- **[!UICONTROL Publish the marketing resource]** 작업이 체크 인된 경우 [마케팅 리소스 만들기 작업](../../mrm/using/creating-and-managing-tasks.md#marketing-resource-creation-task))

워크플로우가 즉시 시작되지 않는 경우(예를 들어 워크플로우가 중지된 경우) 리소스의 상태가 (으)로 변경됩니다 **[!UICONTROL Pending publication]**. 워크플로우가 시작되면 리소스의 상태가 (으)로 변경됩니다 **[!UICONTROL Published]**. 이 상태는 게시 프로세스에서 발생할 수 있는 오류를 고려하지 않습니다. 워크플로우의 상태를 확인하여 제대로 실행되었는지 확인합니다.

## 캠페인에 리소스 연결 {#linking-a-resource-to-a-campaign}

### 마케팅 리소스 참조 {#referencing-a-marketing-resource}

캠페인 템플릿에서 이 기능을 선택한 경우 마케팅 리소스를 캠페인과 연결할 수 있습니다.

>[!NOTE]
>
>캠페인 템플릿을 만들고 구성하는 방법에 대한 자세한 내용은 [캠페인 템플릿](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

을(를) 클릭합니다. **[!UICONTROL Documents > Resources]** campaign 대시보드의 탭을 클릭한 다음 **[!UICONTROL Add]** 을 눌러 관련 리소스를 선택합니다.

![](assets/s_ncs_user_mkg_resource_ref.png)

상태, 특성 또는 유형별로 리소스를 필터링하거나 개인화된 필터를 적용할 수 있습니다.

![](assets/s_ncs_user_mkg_resource_ref_filter.png)

클릭 **[!UICONTROL OK]** 를 추가하여 이 캠페인에 대해 참조된 마케팅 리소스 목록에 리소스를 추가합니다.

다음 **[!UICONTROL Details]** 버튼을 사용하면 편집하고 볼 수 있습니다.

추가된 리소스는 대시보드에 표시됩니다. 그곳에서 편집할 수도 있습니다.

### 게재 아웃라인에 마케팅 리소스 추가 {#adding-a-marketing-resource-to-a-delivery-outline}

게재 개요를 통해 마케팅 리소스를 게재와 연결할 수 있습니다.

![](assets/s_ncs_user_mkg_resource_in_compo.png)

>[!NOTE]
>
>게재 아웃라인에 대한 자세한 내용은 [게재 아웃라인을 통해 연결된 리소스 연결 및 구조화](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

## 주식 관리 {#stock-management}

공급을 관리하고 재고가 부족한 경우 대시보드에 경고를 표시하기 위해 마케팅 리소스를 하나 이상의 주식과 연관시킬 수 있습니다.

>[!NOTE]
>
>Adobe Campaign의 주식 관리에 대한 자세한 내용은 [주식 관리](../../campaign/using/providers--stocks-and-budgets.md#stock-management).

마케팅 리소스를 스톡 리소스와 연결하려면 스톡 맵을 편집하고 스톡을 편집하거나 만듭니다. 재고 라인을 추가하고 해당 마케팅 리소스를 선택합니다.

![](assets/s_ncs_user_task_in_a_stock.png)

필요한 경우 를 통해 선택한 리소스를 편집할 수 있습니다. **[!UICONTROL Edit the link]** 리소스를 선택한 후 리소스의 오른쪽에 있는 아이콘(확대경)입니다.

초기 스톡과 경고 스톡을 지정한 다음 저장합니다.

재고가 리소스 세부 정보에 표시됩니다.

![](assets/s_ncs_user_task_with_a_stock.png)

재고가 부족하면 관련 운영자에게 경고가 전송됩니다.

## 고급 함수 {#advanced-functions}

마케팅 리소스 대시보드를 사용하여 일반적인 작업 유형을 수행할 수 있습니다. 추가, 편집, 잠금/잠금 해제, 승인, 게시. Adobe Campaign 트리를 통해 다른 유형의 마케팅 리소스를 만들고 고급 기능에 액세스할 수 있습니다. 이렇게 하려면 **[!UICONTROL Explorer]** Adobe Campaign 홈 페이지에서 을 참조하십시오.

기본적으로 마케팅 리소스는 **[!UICONTROL MRM > Marketing resources]** 노드 아래에 있어야 합니다.

![](assets/s_ncs_user_mkg_resource_create_from_list.png)

이 보기에서 다음 리소스를 추가할 수 있습니다.

* 파일
* HTML
* 텍스트
* URL
