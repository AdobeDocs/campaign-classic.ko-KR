---
product: campaign
title: 마케팅 캠페인 문서 및 게재 개요
description: 마케팅 캠페인 문서 및 게재 개요에 대해 자세히 알아보기
feature: Campaigns
exl-id: 891252b0-4700-4a2a-a632-63aad5ce75d7
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 1%

---

# 관련 문서 관리 {#managing-associated-documents}

![](../../assets/v7-only.svg)

보고서, 사진, 웹 페이지, 다이어그램 등 다양한 문서를 캠페인에 연결할 수 있습니다. 이러한 문서는 모든 형식(Microsoft Word, PowerPoint, PNG, JPG, Acrobat PDF 등)으로 제공됩니다.

>[!IMPORTANT]
>
>이 기능은 작은 에셋 및 문서에 예약되어 있습니다.

캠페인에서 프로모션 쿠폰, 특정 브랜드 또는 스토어와 관련된 특별 오퍼 등과 같은 다른 항목을 참조할 수도 있습니다. 이러한 요소를 아웃라인에 포함하면 DM 게재와 연결할 수 있습니다. 다음을 참조하십시오 [게재 개요를 통해 연결된 리소스 연결 및 구조](#associating-and-structuring-resources-linked-via-a-delivery-outline).

>[!NOTE]
>
>Campaign 마케팅 리소스 관리 모듈을 사용하는 경우 여러 사용자가 공동 작업에 사용할 수 있는 마케팅 리소스 라이브러리를 관리할 수도 있습니다. [자세히 알아보기](../../mrm/using/managing-marketing-resources.md)

## 문서 추가 {#adding-documents}

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

## 게재 개요를 통해 연결된 리소스 연결 및 구조 {#associating-and-structuring-resources-linked-via-a-delivery-outline}

>[!NOTE]
>
>게재 개요는 DM 캠페인 컨텍스트에서만 사용됩니다.

게재 개요는 구조화된 요소 세트(문서, 스토어, 프로모션 쿠폰 등)를 나타냅니다. 회사에서 만든 다음 특정 캠페인을 위해 만듭니다.

이러한 요소는 게재 개요로 그룹화되고 각 게재 개요는 게재와 연계됩니다. 이 요소는 로 전송된 추출 파일에서 참조됩니다. **서비스 공급자** 게재에 첨부하기 위해. 예를 들어 분기와 분기가 사용하는 마케팅 브로셔를 참조하는 게재 개요를 만들 수 있습니다.

캠페인의 경우 게재 개요를 사용하면 관련 분기, 승인된 프로모션 오퍼, 로컬 이벤트 초대 등의 특정 기준에 따라 게재와 연결할 외부 요소를 구성할 수 있습니다.

### 개요 만들기 {#creating-an-outline}

아웃라인을 생성하려면 다음을 누릅니다. **[!UICONTROL Delivery outlines]** 의 하위 탭 **[!UICONTROL Edit > Documents]** 관련 캠페인의 탭입니다.

>[!NOTE]
>
>이 탭이 없으면 이 캠페인에서 이 기능을 사용할 수 없습니다. 캠페인 템플릿 구성을 참조하십시오.
>   
>템플릿에 대한 자세한 내용은 [이 섹션](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

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
   >마케팅 리소스에 대한 자세한 내용은 다음을 참조하십시오. [이 섹션](../../mrm/using/managing-marketing-resources.md).

### 윤곽선 선택 {#selecting-an-outline}

다음 예제와 같이 각 게재에 대해 추출 아웃라인에 예약된 섹션에서 연결할 아웃라인을 선택할 수 있습니다.

![](assets/s_ncs_user_op_select_composition.png)

그러면 선택한 아웃라인이 창의 아래 섹션에 표시됩니다. 필드 오른쪽에 있는 아이콘을 사용하여 편집하거나 드롭다운 목록을 사용하여 변경할 수 있습니다.

![](assets/s_ncs_user_op_select_composition_b.png)

다음 **[!UICONTROL Summary]** 게재 탭에는 다음 정보도 표시됩니다.

![](assets/s_ncs_user_op_select_composition_c.png)

### 추출 결과 {#extraction-result}

추출하여 서비스 공급업체에 보내는 파일에서 아웃라인의 이름과 필요한 경우 해당 특성(비용, 설명 등)을 표시합니다. 서비스 공급자와 연관된 내보내기 템플릿의 정보에 따라 콘텐츠에 추가됩니다.

다음 예제에서는 게재와 연결된 아웃라인에 대한 레이블, 예상 비용 및 설명을 추출 파일에 추가합니다.

![](assets/s_ncs_user_op_composition_in_export_template.png)

내보내기 모델은 관련 게재에 대해 선택한 서비스 공급자와 연결되어야 합니다. [이 섹션](../../campaign/using/providers--stocks-and-budgets.md#creating-service-providers-and-their-cost-structures)을 참조하십시오.

>[!NOTE]
>
>내보내기에 대한 자세한 내용은 [이 섹션](../../platform/using/get-started-data-import-export.md) 섹션.
