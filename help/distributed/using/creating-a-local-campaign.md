---
product: campaign
title: 로컬 캠페인 만들기
description: 로컬 캠페인 만들기
feature: Distributed Marketing
exl-id: 17b5865a-5e04-4b3b-8b6a-12d5c1a9c1da
source-git-commit: 36e546a34d8c2345fefed5d459095a76c6224a38
workflow-type: tm+mt
source-wordcount: '1564'
ht-degree: 1%

---

# 로컬 캠페인 만들기{#creating-a-local-campaign}

![](../../assets/v7-only.svg)

로컬 캠페인은 다음 중 목록에서 참조하는 템플릿에서 만든 인스턴스입니다 **[!UICONTROL campaign packages]** 사용 **특정 실행 일정**. 목표는 중앙 엔티티가 설정하고 구성한 캠페인 템플릿을 사용하여 로컬 통신 요구를 충족하는 것입니다. 로컬 작업을 구현하는 기본 단계는 다음과 같습니다.

**중앙 엔티티에 대해**

1. 로컬 캠페인 템플릿 만들기
1. 템플릿에서 캠페인 패키지 만들기
1. 캠페인 패키지 게시.
1. 주문 승인.

**로컬 엔티티에 대해**

1. 캠페인 순서 지정.
1. 캠페인 실행.

## 로컬 캠페인 템플릿 만들기 {#creating-a-local-campaign-template}

캠페인 패키지를 만들려면 먼저 **캠페인 템플릿** 사용 **[!UICONTROL Resources > Templates]** 노드 아래에 있어야 합니다.

새 로컬 템플릿을 만들려면 기본값을 복제합니다 **[!UICONTROL Local campaign (opLocal)]** 템플릿.

![](assets/mkg_dist_local_op_creation.png)

캠페인 템플릿에 이름을 지정하고 사용 가능한 필드를 작성합니다.

![](assets/mkg_dist_local_op_creation1.png)

캠페인 창에서 **[!UICONTROL Edit]** 탭을 클릭한 다음 **[!UICONTROL Advanced campaign settings...]** 링크를 클릭합니다.

![](assets/mkt_distr_4.png)

### 웹 인터페이스 {#web-interface}

에서 **분산 마케팅** 탭에서 웹 인터페이스 유형을 선택하고 로컬 엔티티가 주문을 지정할 때 입력할 기본값과 매개변수를 지정할 수 있습니다.

웹 인터페이스는 캠페인을 정렬할 때 로컬 엔티티가 채울 양식에 해당합니다.

템플릿에서 만든 캠페인에 적용할 웹 인터페이스 유형을 선택합니다.

![](assets/mkt_distr_1.png)

사용할 수 있는 웹 인터페이스는 다음 네 가지 유형이 있습니다.

* **[!UICONTROL By brief]** : 로컬 엔터티는 캠페인 구성을 설명하는 설명을 제공해야 합니다. 주문이 승인되면 중앙 엔티티는 캠페인을 전체적으로 구성하고 실행합니다.

   ![](assets/mkt_distr_6.png)

* **[!UICONTROL By form]** : 로컬 엔터티는 사용되는 템플릿에 따라 콘텐츠, 대상, 최대 크기를 편집할 수 있고 개인화 필드를 사용하여 만들기 및 추출 날짜를 편집할 수 있는 웹 양식에 액세스할 수 있습니다. 로컬 엔터티는 이 웹 양식의 대상을 평가하고 콘텐츠를 미리 볼 수 있습니다.

   ![](assets/mkt_distr_8.png)

   제공된 양식은 웹 응용 프로그램에서 지정되며, 이 경우 **[!UICONTROL web Interface]** 템플릿의 필드 **[!UICONTROL Advanced campaign settings...]** 링크를 클릭합니다. 을(를) 참조하십시오. [로컬 캠페인 만들기(양식 기준)](examples.md#creating-a-local-campaign--by-form-).

   >[!NOTE]
   >
   >이 예제에서 사용되는 웹 응용 프로그램은 예제입니다. 양식을 사용할 수 있으려면 특정 웹 앱을 만들어야 합니다. 을(를) 참조하십시오. [API](../../configuration/using/about-web-services.md).

   ![](assets/mkt_distr_7.png)

* **[!UICONTROL By external form]** : 로컬 엔티티는 엑스트라넷(Adobe Campaign 아님)의 campaign 매개 변수에 액세스할 수 있습니다. 이러한 매개 변수는 **로컬 캠페인(양식 기준)**.
* **[!UICONTROL Pre-set]** : 로컬 엔티티는 현지화하지 않고 기본 양식을 사용하여 캠페인을 주문합니다.

   ![](assets/mkt_distr_5.png)

### 기본값 {#default-values}

을(를) 선택합니다 **[!UICONTROL Default values]** 로컬 엔티티에 의해 완료됩니다. 예제:

* 연락 및 추출 날짜
* 타겟 특성(연령 세그먼트 등)은

![](assets/mkg_dist_local_op_creation2.png)

을(를) 완료합니다 **[!UICONTROL Parent marketing program]** 및 **[!UICONTROL Charge]** 필드.

![](assets/mkg_dist_local_op_creation3.png)

### 승인 {#approvals}

에서 **[!UICONTROL Advanced parameters for campaign entry]** 링크를 통해 최대 검토자 수를 지정할 수 있습니다.

![](assets/s_advuser_mkg_dist_add_valid_op1.png)

캠페인을 주문할 때 로컬 엔티티가 검토자를 입력합니다.

![](assets/mkt_distr_5.png)

캠페인에 대한 검토자의 이름을 지정하지 않으려면 0을 입력합니다.

### 문서 {#documents}

로컬 엔티티 연산자를 사용하여 문서(텍스트 파일, 스프레드시트, 이미지, 캠페인 설명 등)를 연결할 수 있습니다. 주문을 만들 때 로컬 캠페인에 전달하는 것이 좋습니다. 다음 **[!UICONTROL Advanced parameters for campaign entry...]** 링크를 통해 문서 수를 제한할 수 있습니다. 이렇게 하려면 **[!UICONTROL Number of documents]** 필드.

![](assets/s_advuser_mkg_dist_local_docs.png)

캠페인 패키지를 순서 지정할 때 양식은 템플릿의 해당 필드에 표시된 만큼 문서에 연결하는 것을 제안합니다.

![](assets/s_advuser_mkg_dist_add_docs.png)

문서 업로드 필드를 표시하지 않으려면 을 입력합니다. **[!UICONTROL 0]** 에서 **[!UICONTROL Number of documents]** 필드.

>[!NOTE]
>
>다음 **[!UICONTROL Advanced parameters for campaign entry]** 을(를) 확인하여 비활성화할 수 있습니다. **[!UICONTROL Do not display the page used to enter the campaign parameters]**.

![](assets/s_advuser_mkg_dist_disable_op_parameters.png)

### 워크플로우 {#workflow}

에서 **[!UICONTROL Targeting and workflows]** 탭에서 다음을 수집하는 캠페인 워크플로우를 만듭니다 **[!UICONTROL Default values]** 에 지정됨 **[!UICONTROL Advanced campaign settings...]** 게재를 만듭니다.

![](assets/mkg_dist_local_op_creation4b.png)

을(를) 두 번 클릭합니다. **[!UICONTROL Query]** 활동을 통해 지정된 대로 구성 **[!UICONTROL Default values]**.

![](assets/mkt_dist_local_campaign_localize_query.png)

### 게재 {#delivery}

에서 **[!UICONTROL Audit]** 탭에서 **[!UICONTROL Detail...]** 아이콘을 클릭하여 **[!UICONTROL Scheduling]** 을 선택합니다.

![](assets/mkg_dist_local_op_creation4c.png)

다음 **[!UICONTROL Scheduling]** 아이콘을 사용하면 게재 연락처 및 실행 날짜를 구성할 수 있습니다.

![](assets/mkg_dist_local_op_creation4d.png)

필요한 경우 게재 최대 크기를 구성합니다.

![](assets/mkg_dist_local_op_creation4e.png)

게재의 HTML을 찾습니다. 예, 에서 **[!UICONTROL Delivery > Current order > Additional fields]**&#x200B;를 사용하려면 **[!UICONTROL Age segment]** 타겟 나이에 따라 게재를 찾을 필드입니다.

![](assets/mkt_dist_local_campaign_localize_html.png)

캠페인 템플릿을 저장합니다. 이제 다음 위치에서 사용할 수 있습니다. **[!UICONTROL Campaign packages]** 에서 보기 **[!UICONTROL Campaigns]** 탭을 클릭하여 **[!UICONTROL Create]** 버튼을 클릭합니다.

![](assets/mkt_distr_9.png)

>[!NOTE]
>
>캠페인 템플릿과 일반적인 구성은 [캠페인 템플릿](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

## 캠페인 패키지 만들기 {#creating-the-campaign-package}

캠페인 템플릿을 로컬 엔티티에서 사용할 수 있도록 하려면 목록에 추가해야 합니다. 이를 위해서는 중앙기관이 새 패키지를 만들어야 한다.

다음 단계를 적용합니다.

1. 에서 **[!UICONTROL Navigation]** 섹션에 **캠페인** 페이지에서 **[!UICONTROL Campaign packages]** 링크를 클릭합니다.
1. **[!UICONTROL Create]** 버튼을 클릭합니다.

   ![](assets/mkg_dist_add_an_entry.png)

1. 창 위의 섹션에서 [이전](#creating-a-local-campaign-template) 지정한 캠페인 패키지 템플릿입니다.

   기본적으로 **[!UICONTROL New local campaign package (localEmpty)]** 템플릿은 로컬 캠페인에 사용됩니다.

1. 캠페인 패키지에 대한 레이블, 폴더 및 실행 일정을 지정합니다.

### 날짜 {#dates}

시작 및 종료 날짜는 캠페인 패키지 목록에서 캠페인의 가시성 기간을 정의합니다.

가용성 날짜는 로컬 엔티티(주문)에 대해 캠페인을 사용할 수 있는 날짜입니다.

>[!CAUTION]
>
>로컬 엔티티가 최종 기한 전에 캠페인을 예약하지 않으면 캠페인을 사용할 수 없습니다.

이 정보는 아래와 같이 지역 에이전시에 전송되는 알림 메시지에서 찾을 수 있습니다.

![](assets/s_advuser_mkg_dist_local_notif.png)

### 대상자 {#audience}

로컬 캠페인의 경우 중앙 엔티티는 를 확인하여 관련 로컬 엔티티를 지정할 수 있습니다 **[!UICONTROL Limit the package to a set of local entities]**.

![](assets/s_advuser_mkg_dist_create_mutual_entry3.png)

### 추가 설정 {#additional-settings}

패키지가 저장되면 중앙 엔티티가 **[!UICONTROL Edit]** 탭.

![](assets/mkg_dist_edit_kit.png)

에서 **[!UICONTROL General]** 탭에서 중앙 엔티티는 다음을 수행할 수 있습니다.

* 에서 캠페인 패키지 검토자를 구성합니다. **[!UICONTROL Approval parameters...]** 링크,
* 실행 일정을 검토하고
* 로컬 엔티티를 추가하거나 삭제합니다.

>[!NOTE]
>
>기본적으로 각 엔티티는 **로컬 캠페인** 한 번만
>   
>을(를) 확인합니다. **[!UICONTROL Enable multiple creation]** 여러 로컬 캠페인을 캠페인 패키지에서 만들 수 있는 옵션.

![](assets/mkg_dist_local_op_multi_crea.png)

### 알림 을 참조하십시오 {#notifications}

캠페인을 사용할 수 있게 되거나 등록 마감일이 되면 로컬 알림 그룹의 운영자에게 메시지가 전송됩니다. 자세한 내용은 [조직 엔터티](about-distributed-marketing.md#organizational-entities).

## 캠페인 순서 지정 {#ordering-a-campaign}

로컬 엔티티가 승인되고 구현 기간이 시작되면 Campaign 패키지에 액세스할 수 있습니다. 로컬 엔티티는 새 캠페인 패키지를 사용할 수 있음을 알리는 이메일을 수신하게 됩니다(사용 가능 날짜가 되는 즉시).

>[!NOTE]
>
>캠페인 패키지를 만들 때 일부 로컬 엔티티가 지정된 경우 알림을 받는 유일한 로컬 엔티티가 됩니다. 로컬 엔터티가 지정되지 않은 경우 모든 로컬 엔터티가 알림을 받습니다.

![](assets/mkg_dist_local_op_notification.png)

중앙 엔티티가 제공하는 캠페인을 사용하려면 로컬 엔티티가 캠페인을 주문해야 합니다.

캠페인을 주문하려면:

1. 클릭 **[!UICONTROL Order campaign]** 알림 메시지에서 또는 Adobe Campaign에서 해당 버튼을 클릭합니다.

   캠페인 순서를 지정하려면 ID와 암호를 입력합니다. 인터페이스는 웹 애플리케이션에 정의된 페이지 세트로 구성됩니다.

   >[!NOTE]
   >
   >웹 응용 프로그램은 [이 섹션](../../web/using/about-web-applications.md).

1. 첫 번째 페이지(주문 레이블 및 주석)에 필요한 정보를 입력하고 **[!UICONTROL Next]**.

   ![](assets/mkg_dist_subscribe_step1.png)

1. 사용 가능한 매개 변수를 완료하고 주문을 승인합니다.

1. 이 순서를 승인하기 위해 로컬 엔티티가 속한 조직 엔터티의 관리자에게 알림이 전송됩니다.

   ![](assets/mkg_dist_subscribe_step3.png)

1. 정보는 로컬 및 중앙 엔티티로 반환됩니다. 로컬 엔티티는 고유한 주문만 볼 수 있지만 중앙 엔티티는 아래와 같이 로컬 엔티티의 모든 주문을 볼 수 있습니다.

   ![](assets/mkg_dist_subscribe_central_view.png)

   연산자는 주문 세부 사항을 표시할 수 있습니다.

   ![](assets/mkg_dist_local_op_catalog_detail_1.png)

   다음 **[!UICONTROL Edit]** 탭에는 캠페인을 정렬할 때 로컬 엔티티가 입력한 정보가 포함되어 있습니다.

   ![](assets/mkg_dist_local_op_catalog_detail_1b.png)

1. 이 주문은 중앙 엔티티가 승인하여 마무리해야 합니다.

   ![](assets/mkg_dist_local_op_catalog_detail_3.png)

   자세한 내용은 [승인 프로세스](#approval-process) 섹션을 참조하십시오.

1. 그러면 로컬 운영자에게 캠페인을 사용할 수 있다는 알림을 보냅니다. campaign 가용성은 **캠페인** 탭. 그런 다음 캠페인을 사용할 수 있습니다. 자세한 내용은 [캠페인 액세스](accessing-campaigns.md).

   다음 **[!UICONTROL Start targeting with order approval]** 옵션을 사용하면 주문이 승인되는 즉시 로컬 엔티티가 캠페인을 실행할 수 있습니다.

   ![](assets/mkg_dist_local_op_catalog_use.png)

## 주문 승인 {#approving-an-order}

캠페인 순서를 확인하려면 중앙 엔티티가 이를 승인해야 합니다.

다음 **[!UICONTROL Campaign orders]** 개요, 를 통해 액세스 **캠페인** 탭에서는 캠페인 주문의 상태를 보고 승인할 수 있습니다.

>[!NOTE]
>
>로컬 엔티티는 승인될 때까지 주문을 변경할 수 있습니다.

### 승인 프로세스 {#approval-process}

#### 이메일 알림 {#email-notification}

로컬 엔티티에 의해 캠페인 순서가 지정되면 해당 검토자에게 아래와 같이 전자 메일로 알림을 보냅니다.

![](assets/mkg_dist_valid_notif_email.png)

>[!NOTE]
>
>검토자를 선택하는 방법은 [검토자](#reviewers) 섹션을 참조하십시오. 그들은 그 명령을 수락하거나 거부할 수 있다.

![](assets/mkg_dist_command_valid_web.png)

#### Adobe Campaign 콘솔을 통한 승인 {#approving-via-the-adobe-campaign-console}

또한, 캠페인 순서 개요에서 콘솔을 통해 주문을 승인할 수 있습니다. 주문을 승인하려면 주문을 선택하고 을(를) 클릭합니다 **[!UICONTROL Approve the order]**.

![](assets/mkg_dist_local_order_valid.png)

>[!NOTE]
>
>캠페인 가용성은 여전히 캠페인 가용 날짜까지 편집하고 재구성할 수 있습니다. 로컬 엔티티는 **[!UICONTROL Cancel]** 버튼을 클릭합니다.

#### 캠페인 만들기 {#creating-a-campaign}

캠페인 순서가 승인되면 로컬 엔티티에 의해 구성 및 실행될 수 있습니다.

![](assets/mkg_dist_mutual_op_created.png)

자세한 내용은 [캠페인 액세스](accessing-campaigns.md).

### 승인 거부 {#rejecting-an-approval}

승인 담당자는 주문 또는 캠페인 패키지를 거부할 수 있습니다.

![](assets/mkg_dist_do_not_valid.png)

검토자가 주문을 거부하면 관련 알림이 관련 로컬 엔티티에 자동으로 전송됩니다. 승인을 거부한 연산자가 입력한 설명을 표시합니다.

정보는 캠페인 패키지 목록 페이지 또는 캠페인 순서 페이지에 표시됩니다. Adobe Campaign 콘솔에 액세스할 수 있는 로컬 엔티티는 이러한 거부 통보를 받습니다.

![](assets/mkg_dist_do_not_valid_view.png)

캠페인 패키지의 **[!UICONTROL Edit]** 탭.

![](assets/mkg_dist_do_not_valid_tab.png)

### 검토자 {#reviewers}

승인이 필요할 때마다 검토자에게 전자 메일로 알림을 보냅니다.

각 로컬 엔티티에 대해 캠페인 주문 승인 및 캠페인 승인을 위해 검토자가 선택됩니다. 로컬 검토자 선택에 대한 자세한 내용은 [조직 엔터티](about-distributed-marketing.md#organizational-entities).

>[!NOTE]
>
>이러한 선택이 가능하려면 주문 승인이 아직 유효하지 않아야 합니다.

### 주문 취소 {#canceling-an-order}

중앙기관은 **[!UICONTROL Delete]** 단추, 주문 대시보드에 있습니다.

![](assets/mkg_dist_local_op_cancel.png)

이렇게 하면 **[!UICONTROL Campaign orders]** 보기.
