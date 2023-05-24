---
product: campaign
title: 마케팅 캠페인 게재
description: 마케팅 캠페인 게재에 대해 자세히 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Campaigns, Resource Management, Cross Channel Orchestration
exl-id: 1dd3c080-444d-45f8-9562-d2d01a9d2860
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1487'
ht-degree: 2%

---

# 마케팅 캠페인 게재 {#marketing-campaign-deliveries}

게재는 캠페인 대시보드, 캠페인 워크플로우 또는 게재 개요를 통해 직접 만들 수 있습니다.

캠페인에서 생성되면 게재는 이 캠페인에 연결되고 캠페인 수준에서 통합됩니다.

![](assets/do-not-localize/how-to-video.png)[ 비디오에서 이 기능 살펴보기](#create-email-video)

## 게재 만들기 {#creating-deliveries}

캠페인에 연결된 게재를 만들려면 **[!UICONTROL Add a delivery]** 캠페인 대시보드에 링크.

![](assets/campaign_op_add_delivery.png)

제안된 구성은 DM, 이메일, 모바일 채널 등 다양한 유형의 게재에 적합합니다. [자세히 알아보기](../../delivery/using/steps-about-delivery-creation-steps.md)

## 게재를 시작합니다 {#starting-a-delivery}

모든 승인이 승인되면 게재를 시작할 수 있습니다. 게재 절차는 게재 유형에 따라 다릅니다. 이메일 또는 모바일 채널 게재에 대해서는 다음을 참조하십시오. [온라인 게재 시작](#starting-an-online-delivery)및 DM 게재에 대해서는 다음을 참조하십시오. [오프라인 게재 시작](#starting-an-offline-delivery).

### 온라인 게재 시작 {#starting-an-online-delivery}

모든 승인 요청이 승인되면 게재 상태가 (으)로 변경됩니다. **[!UICONTROL Pending confirmation]** 연산자로 시작할 수 있습니다. 해당되는 경우 게재를 시작할 검토자로 지정된 Adobe Campaign 운영자(또는 운영자 그룹)에게 게재를 시작할 준비가 되었다는 알림이 전송됩니다.

>[!NOTE]
>
>게재 속성에서 게재를 시작하기 위해 특정 연산자 또는 연산자 그룹을 지정한 경우 게재를 담당하는 연산자가 전송을 확인하도록 할 수도 있습니다. 이렇게 하려면 를 활성화합니다. **NMS_ActivateOwnerConfirmation** 다음을 입력하여 옵션 제공 **1** 을 값으로 추가합니다. 옵션은 다음 위치에서 관리됩니다. **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** Adobe Campaign 탐색기의 노드
>  
>이 옵션을 비활성화하려면 다음을 입력합니다. **0** 을 값으로 추가합니다. 그러면 전송 확인 프로세스가 기본값으로 작동합니다. 게재 속성에서 전송을 위해 지정된 운영자 또는 운영자 그룹(또는 관리자)만 전송을 확인하고 수행할 수 있습니다.

![](assets/s_ncs_user_edit_del_to_start_from_del.png)

이 정보는 캠페인 대시보드에도 표시됩니다. 다음 **[!UICONTROL Confirm delivery]** 링크를 통해 게재를 시작할 수 있습니다.

![](assets/s_ncs_user_edit_del_to_start.png)

확인 메시지를 사용하면 이 작업의 보안을 유지할 수 있습니다.

### 오프라인 게재 시작 {#starting-an-offline-delivery}

모든 승인이 승인되면 게재 상태가 다음으로 변경됩니다. **[!UICONTROL Pending extraction]**. 추출 파일은 DM 게재가 추출 보류 중일 때 기본 구성에서 자동으로 시작되는 특수 워크플로우를 통해 만들어집니다. 프로세스가 진행 중이면 대시보드에 표시되고 해당 링크를 통해 편집할 수 있습니다.

>[!NOTE]
>
>Campaign 패키지와 관련된 기술 워크플로는에 나와 있습니다. [기술 워크플로우 목록](../../workflow/using/about-technical-workflows.md).

**1단계 - 파일 승인**

추출 워크플로우가 성공적으로 실행되면 추출 파일을 승인해야 합니다(게재 설정에서 추출 파일 승인을 선택한 경우).

자세한 내용은 다음을 참조하십시오. [추출 파일 승인](../../campaign/using/marketing-campaign-approval.md#approving-an-extraction-file).

**2단계 - 서비스 공급자에 대한 메시지 승인**

* 추출 파일이 승인되면 라우터 알림 이메일의 증명을 생성할 수 있습니다. 이 이메일 메시지는 게재 템플릿을 기반으로 구축됩니다. 승인을 받아야 합니다.

   >[!NOTE]
   >
   >이 단계는 승인 창에서 증명 전송 및 승인이 활성화된 경우에만 사용할 수 있습니다.

![](assets/s_ncs_user_file_valid_select_BAT.png)


* 다음을 클릭합니다. **[!UICONTROL Send a proof]** 버튼을 클릭하여 증명을 만듭니다.

   증명 대상을 미리 정의해야 합니다.

   필요한 만큼 증명을 만들 수 있습니다. 다음을 통해 액세스됩니다. **[!UICONTROL Direct mail...]** 게재 세부 정보 링크.

   ![](assets/s_ncs_user_file_notif_submit_proof.png)

* 게재 상태가 다음으로 변경됨 **[!UICONTROL To submit]**. 다음을 클릭합니다. **[!UICONTROL Submit proofs]** 버튼을 클릭하여 승인 프로세스를 시작합니다.

   ![](assets/s_ncs_user_file_notif_submit_proof_validation.png)

* 게재 상태가 다음으로 변경됨 **[!UICONTROL Proof to validate]** 버튼을 사용하면 승인을 수락하거나 거부할 수 있습니다.

   ![](assets/s_ncs_user_file_notif_supplier_link.png)

   이 승인을 수락 또는 거부하거나 추출 단계로 돌아갈 수 있습니다.

   ![](assets/s_ncs_user_file_notif_supplier_link_confirm.png)

* 추출 파일이 라우터로 전송되고 게재가 완료됩니다.

### 비용 및 재고 계산 {#calculation-of-costs-and-stocks}

파일 추출에서는 예산 계산과 재고 계산이라는 두 가지 작업을 실행합니다. 예산 항목이 갱신됩니다.

* 다음 **[!UICONTROL Budget]** 탭에서는 캠페인에 대한 예산을 관리할 수 있습니다. 비용 항목의 합계는 다음에 표시됩니다. **[!UICONTROL Calculates cost]** 캠페인의 메인 탭 및 해당 캠페인이 속한 프로그램의 필드. 금액은 캠페인 예산에도 반영됩니다.

   실제 비용은 결국 라우터가 제공한 정보로부터 산출될 것이다. 실제로 전송된 메시지만 송장이 발행됩니다.

* 주식은 다음에 정의됩니다. **[!UICONTROL Administration > Campaign management > Stocks]** 트리의 노드 및 의 비용 구조 **[!UICONTROL Administration > Campaign management > Service providers]** 노드.

   재고 라인이 재고 섹션에 표시됩니다. 초기 재고를 정의하려면 재고 라인을 엽니다. 게재가 발생할 때마다 재고가 감소합니다. 경고 수준 및 알림을 정의할 수 있습니다.

>[!NOTE]
>
>원가 계산 및 재고 관리에 대한 자세한 내용은 [공급자, 재고 및 예산](../../campaign/using/providers--stocks-and-budgets.md).

## 관련 문서 관리 {#managing-associated-documents}

보고서, 사진, 웹 페이지, 다이어그램 등 다양한 문서를 캠페인에 연결할 수 있습니다. 이러한 문서는 모든 형식(Microsoft Word, PowerPoint, PNG, JPG, Acrobat PDF 등)으로 제공됩니다. 문서를 캠페인과 연결하는 방법 알아보기 [이 섹션에서](../../campaign/using/marketing-campaign-assets.md).

>[!IMPORTANT]
>
>이 모드는 작은 문서용으로 예약되어 있습니다.

캠페인에서 프로모션 쿠폰, 특정 지점 또는 상점과 관련된 특별 오퍼 등과 같은 다른 항목을 참조할 수도 있습니다. 이러한 요소를 아웃라인에 포함하면 DM 게재와 연결할 수 있습니다. [자세히 알아보기](#associating-and-structuring-resources-linked-via-a-delivery-outline)

>[!NOTE]
>
>MRM을 사용하는 경우 여러 참가자가 공동 작업을 위해 사용할 수 있는 마케팅 리소스 라이브러리를 관리할 수도 있습니다. 다음을 참조하십시오 [마케팅 리소스 관리](../../mrm/using/managing-marketing-resources.md).

### 문서 추가 {#adding-documents}

캠페인 수준(컨텍스트 문서) 또는 프로그램 수준(일반 문서)에서 문서를 연결할 수 있습니다.

다음 **[!UICONTROL Documents]** 탭에는 다음이 포함되어 있습니다.

* 콘텐츠에 필요한 모든 문서 목록(템플릿, 이미지 등) 적절한 권한이 있는 Adobe Campaign 운영자가 로컬로 다운로드할 수 있습니다.
* 라우터에 대한 정보가 포함된 문서(있는 경우).

문서는 를 통해 프로그램 또는 캠페인에 연결됩니다. **[!UICONTROL Edit > Documents]** 탭.

![](assets/s_ncs_user_op_add_document.png)

대시보드에 제공된 링크를 통해 캠페인에 문서를 추가할 수도 있습니다.

![](assets/add_a_document_in_op.png)

다음을 클릭합니다. **[!UICONTROL Details]** 아이콘을 클릭하여 파일의 내용을 보고 정보를 추가할 수 있습니다.

![](assets/s_ncs_user_op_add_document_details.png)

대시보드에서 캠페인과 관련된 문서는 **[!UICONTROL Document(s)]** 섹션에 있는 마지막 항목이 될 필요가 없습니다.

![](assets/s_ncs_user_op_edit_document.png)

이 보기에서 편집하고 수정할 수도 있습니다.

### 게재 개요를 통해 연결된 리소스 연결 및 구조 {#associating-and-structuring-resources-linked-via-a-delivery-outline}

>[!NOTE]
>
>게재 개요는 DM 캠페인 컨텍스트에서만 사용됩니다.

게재 개요는 구조화된 요소 세트(문서, 지점/스토어, 프로모션 쿠폰 등)를 나타냅니다. 회사 및 특정 캠페인을 위해 만들어졌습니다.

이러한 요소는 게재 개요로 그룹화되고 특정 게재 개요가 게재와 연결됩니다. 이 요소는 로 보내진 추출 파일에서 참조됩니다. **서비스 공급자** 게재에 첨부하기 위해. 예를 들어 분기와 분기가 사용하는 마케팅 브로셔를 참조하는 게재 개요를 만들 수 있습니다.

캠페인의 경우 게재 개요를 사용하면 관련 분기, 승인된 프로모션 오퍼, 로컬 이벤트 초대 등의 특정 기준에 따라 게재와 연결할 외부 요소를 구성할 수 있습니다.

#### 개요 만들기 {#creating-an-outline}

아웃라인을 생성하려면 다음을 누릅니다. **[!UICONTROL Delivery outlines]** 의 하위 탭 **[!UICONTROL Edit > Documents]** 관련 캠페인의 탭입니다.

>[!NOTE]
>
>이 탭이 없으면 이 캠페인에서 이 기능을 사용할 수 없습니다. 캠페인 템플릿 구성을 참조하십시오.
>   
>자세한 내용은 다음을 참조하십시오. [캠페인 템플릿](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

![](assets/s_ncs_user_op_composition_link.png)

그런 다음 을 클릭합니다. **[!UICONTROL Add a delivery outline]** 그리고 campaign에 대한 아웃라인의 계층 구조를 만듭니다.

1. 트리의 루트를 마우스 오른쪽 버튼으로 클릭하고 를 선택합니다. **[!UICONTROL New > Delivery outlines]**.
1. 방금 생성한 아웃라인을 마우스 오른쪽 버튼으로 클릭하고 다음을 선택합니다. **[!UICONTROL New > Item]** 또는 **[!UICONTROL New > Personalization fields]**.

![](assets/s_ncs_user_op_add_composition.png)

아웃라인에는 항목 및 개인화 필드, 리소스 및 오퍼가 포함될 수 있습니다.

* 예를 들어, 여기에서 참조되고 설명되며 게재에 첨부될 실제 문서가 항목일 수 있습니다.
* 개인화 필드를 사용하면 수신자가 아닌 게재와 관련된 개인화 요소를 만들 수 있습니다. 따라서 특정 대상(환영 오퍼, 할인 등)에 대한 게재에 사용할 값을 만들 수 있습니다. Adobe Campaign에서 만들어지고 를 통해 아웃라인으로 가져옵니다. **[!UICONTROL Import personalization fields...]** 링크를 클릭합니다.

   ![](assets/s_ncs_user_op_add_composition_field.png)

   아웃라인에서 직접 생성할 수도 있습니다. **[!UICONTROL Add]** 목록 영역 오른쪽에 있는 아이콘.

   ![](assets/s_ncs_user_op_add_composition_field_button.png)

* 리소스는 다음을 통해 액세스되는 마케팅 리소스 대시보드에서 생성된 마케팅 리소스입니다. **[!UICONTROL Resources]** 링크 **[!UICONTROL Campaigns]** 탭.

   ![](assets/s_ncs_user_mkg_resource_ovv.png)

   >[!NOTE]
   >
   >마케팅 리소스에 대한 자세한 내용은 다음을 참조하십시오. [마케팅 리소스 관리](../../mrm/using/managing-marketing-resources.md).

#### 윤곽선 선택 {#selecting-an-outline}

다음 예제와 같이 각 게재에 대해 추출 아웃라인에 예약된 섹션에서 연결할 아웃라인을 선택할 수 있습니다.

![](assets/s_ncs_user_op_select_composition.png)

그러면 선택한 아웃라인이 창의 아래 섹션에 표시됩니다. 필드 오른쪽에 있는 아이콘을 사용하여 편집하거나 드롭다운 목록을 사용하여 변경할 수 있습니다.

![](assets/s_ncs_user_op_select_composition_b.png)

다음 **[!UICONTROL Summary]** 게재 탭에는 다음 정보도 표시됩니다.

![](assets/s_ncs_user_op_select_composition_c.png)

#### 추출 결과 {#extraction-result}

추출하여 서비스 공급업체에 보내는 파일에서 아웃라인의 이름과 필요한 경우 해당 특성(비용, 설명 등)을 표시합니다. 서비스 공급자와 연관된 내보내기 템플릿의 정보에 따라 콘텐츠에 추가됩니다.

다음 예제에서는 게재와 연결된 아웃라인에 대한 레이블, 예상 비용 및 설명을 추출 파일에 추가합니다.

![](assets/s_ncs_user_op_composition_in_export_template.png)

내보내기 모델은 관련 게재에 대해 선택한 서비스 공급자와 연결되어야 합니다. 다음을 참조하십시오 [서비스 공급자 및 해당 비용 구조 생성](../../campaign/using/providers--stocks-and-budgets.md#creating-service-providers-and-their-cost-structures).

>[!NOTE]
>
>내보내기에 대한 자세한 내용은 [시작](../../platform/using/get-started-data-import-export.md) 섹션.

#### 튜토리얼 비디오 {#create-email-video}

이 비디오에서는 Adobe Campaign에서 캠페인 및 이메일을 만드는 방법을 설명합니다.

>[!VIDEO](https://video.tv.adobe.com/v/25604?quality=12)

추가 캠페인 방법 비디오를 사용할 수 있습니다 [여기](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=ko).
