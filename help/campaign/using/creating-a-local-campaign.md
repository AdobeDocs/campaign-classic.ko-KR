---
title: 로컬 캠페인 만들기
seo-title: 로컬 캠페인 만들기
description: 로컬 캠페인 만들기
seo-description: null
page-status-flag: never-activated
uuid: 86e78d9e-26cb-4aea-b8ce-5e52ae352b48
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: distributed-marketing
discoiquuid: bd057441-8524-49e6-b5d5-fbd0ec5bca85
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e97183256ef6d3f2068dd0fbc8eb3c3f32e0bae0
workflow-type: tm+mt
source-wordcount: '1573'
ht-degree: 0%

---


# 로컬 캠페인 만들기{#creating-a-local-campaign}

로컬 캠페인은 **[!UICONTROL campaign packages]** 특정 실행 일정이 있는 목록 **에서 참조하는 템플릿에서 만든 인스턴스입니다**. 목표는 중앙 엔티티가 설정하고 구성한 캠페인 템플릿을 사용하여 로컬 커뮤니케이션 요구 사항을 충족하는 것입니다. 로컬 작업을 구현하는 기본 단계는 다음과 같습니다.

**중앙 엔티티**

1. 로컬 캠페인 템플릿 만들기를 참조하십시오.
1. 템플릿에서 캠페인 패키지 생성
1. 캠페인 패키지 게시를 참조하십시오.
1. 주문 승인.

**로컬 엔티티**

1. 캠페인 순서 지정
1. 캠페인 실행을 참조하십시오.

## 로컬 캠페인 템플릿 만들기 {#creating-a-local-campaign-template}

캠페인 패키지를 만들려면 먼저 노드를 통해 **캠페인 템플릿을** 만들어야 **[!UICONTROL Resources > Templates]** 합니다.

새 로컬 템플릿을 만들려면 기본 템플릿을 **[!UICONTROL Local campaign (opLocal)]** 복제합니다.

![](assets/mkg_dist_local_op_creation.png)

캠페인 템플릿의 이름을 지정하고 사용 가능한 필드를 완료합니다.

![](assets/mkg_dist_local_op_creation1.png)

캠페인 창에서 **[!UICONTROL Edit]** 탭을 클릭한 다음 **[!UICONTROL Advanced campaign settings...]** 링크를 클릭합니다.

![](assets/mkt_distr_4.png)

### 웹 인터페이스 {#web-interface}

분산 **마케팅** 탭에서 웹 인터페이스 유형을 선택하고 로컬 엔티티가 주문을 할 때 입력할 기본값 및 매개 변수를 지정할 수 있습니다.

웹 인터페이스는 캠페인 순서를 지정할 때 로컬 엔티티가 채울 양식과 일치합니다.

템플릿에서 만든 캠페인에 적용할 웹 인터페이스 유형을 선택합니다.

![](assets/mkt_distr_1.png)

사용 가능한 웹 인터페이스에는 다음 네 가지 유형이 있습니다.

* **[!UICONTROL By brief]** : 로컬 엔터티는 캠페인 구성을 설명하는 설명을 제공해야 합니다. 주문이 승인되면 중앙 엔티티는 캠페인을 전체적으로 구성하고 실행합니다.

   ![](assets/mkt_distr_6.png)

* **[!UICONTROL By form]** : 로컬 엔터티는 사용된 템플릿에 따라 컨텐츠, 타겟, 최대 크기, 개인화 필드를 사용한 작성 및 추출 날짜를 편집할 수 있는 웹 양식에 액세스할 수 있습니다. 로컬 엔터티는 대상을 평가하고 이 웹 양식의 콘텐츠를 미리 볼 수 있습니다.

   ![](assets/mkt_distr_8.png)

   제공된 양식은 웹 애플리케이션에서 지정되며, 템플릿 **[!UICONTROL Web Interface]** **[!UICONTROL Advanced campaign settings...]** 링크의 필드 드롭다운 목록에서 선택해야 합니다. 로컬 캠페인 [만들기(양식별)를 참조하십시오](../../campaign/using/examples.md#creating-a-local-campaign--by-form-).

   >[!NOTE]
   >
   >이 예제에서 사용되는 웹 응용 프로그램이 그 예입니다. 양식을 사용할 수 있으려면 특정 웹 앱을 만들어야 합니다. API [를 참조하십시오](../../configuration/using/about-web-services.md).

   ![](assets/mkt_distr_7.png)

* **[!UICONTROL By external form]** : 로컬 엔터티는 엑스트라넷의 캠페인 매개 변수에 액세스할 수 있습니다(Adobe Campaign이 아님). 이러한 매개 변수는 **로컬 캠페인(양식)의 매개 변수와 동일합니다**.
* **[!UICONTROL Pre-set]** : 로컬 엔티티는 지역화하지 않고 기본 양식을 사용하여 캠페인을 주문합니다.

   ![](assets/mkt_distr_5.png)

### 기본값 {#default-values}

로컬 엔티티 **[!UICONTROL Default values]** 에서 작성할 항목을 선택합니다. 예:

* 연락처 및 추출 날짜
* 타겟 특성(연령 세그먼트 등)

![](assets/mkg_dist_local_op_creation2.png)

필드 **[!UICONTROL Parent marketing program]** 를 **[!UICONTROL Charge]** 완료합니다.

![](assets/mkg_dist_local_op_creation3.png)

### 승인 {#approvals}

링크에서 **[!UICONTROL Advanced parameters for campaign entry]** 최대 검토자 수를 지정할 수 있습니다.

![](assets/s_advuser_mkg_dist_add_valid_op1.png)

캠페인을 주문하면 로컬 엔티티가 검토자를 입력합니다.

![](assets/mkt_distr_5.png)

캠페인에 대한 검토자의 이름을 지정하지 않으려면 0을 입력합니다.

### 문서 {#documents}

로컬 엔티티 연산자가 문서(텍스트 파일, 스프레드시트, 이미지, 캠페인 설명 등)를 연결하도록 허용할 수 있습니다. 순서를 만들 때 로컬 캠페인으로 이동합니다. 이 **[!UICONTROL Advanced parameters for campaign entry...]** 링크를 통해 문서 수를 제한할 수 있습니다. 이렇게 하려면 필드에 허용되는 최대 수를 **[!UICONTROL Number of documents]** 입력하십시오.

![](assets/s_advuser_mkg_dist_local_docs.png)

캠페인 패키지의 순서를 지정할 때 양식은 템플릿의 해당 필드에 지정된 만큼 문서를 연결하는 것이 좋습니다.

![](assets/s_advuser_mkg_dist_add_docs.png)

문서 업로드 필드를 표시하지 않으려면 필드 **[!UICONTROL 0]** 에 **[!UICONTROL Number of documents]** 입력합니다.

>[!NOTE]
>
>을 **[!UICONTROL Advanced parameters for campaign entry]** 선택하면 비활성화할 수 있습니다 **[!UICONTROL Do not display the page used to enter the campaign parameters]**.

![](assets/s_advuser_mkg_dist_disable_op_parameters.png)

### 워크플로우 {#workflow}

탭에서 **[!UICONTROL Targeting and workflows]** 에 **[!UICONTROL Default values]** 지정된 항목을 수집하고 배달을 만드는 캠페인 **[!UICONTROL Advanced campaign settings...]** 워크플로우를 만듭니다.

![](assets/mkg_dist_local_op_creation4b.png)

활동을 두 번 클릭하여 지정된 내용에 따라 구성합니다 **[!UICONTROL Query]** **[!UICONTROL Default values]**.

![](assets/mkt_dist_local_campaign_localize_query.png)

### 게재 {#delivery}

탭에서 **[!UICONTROL Audit]** 아이콘을 **[!UICONTROL Detail...]** 클릭하여 선택한 게재에 **[!UICONTROL Scheduling]** 대한 내용을 확인합니다.

![](assets/mkg_dist_local_op_creation4c.png)

이 **[!UICONTROL Scheduling]** 아이콘을 사용하여 게재 연락처와 실행 날짜를 구성할 수 있습니다.

![](assets/mkg_dist_local_op_creation4d.png)

필요한 경우 배달의 최대 크기를 구성합니다.

![](assets/mkg_dist_local_op_creation4e.png)

게재의 HTML을 찾습니다. 예를 들어, 에서 **[!UICONTROL Delivery > Current order > Additional fields]**&#x200B;이 **[!UICONTROL Age segment]** 필드를 사용하여 대상 연령에 따라 배달을 찾습니다.

![](assets/mkt_dist_local_campaign_localize_html.png)

캠페인 템플릿을 저장합니다. 이제 **캠페인** 우주의 **캠페인 패키지** 보기에서 **[!UICONTROL Create]** 단추를 클릭하여사용할 수있습니다.

![](assets/mkt_distr_9.png)

>[!NOTE]
>
>캠페인 템플릿과 일반 구성은 [캠페인 템플릿에 자세히 설명되어 있습니다](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

## 캠페인 패키지 만들기 {#creating-the-campaign-package}

캠페인 템플릿을 로컬 엔티티에서 사용할 수 있게 하려면 목록에 추가해야 합니다. 이를 위해서는 중앙부처에서 새 패키지를 만들어야 한다.

다음 단계를 적용합니다.

1. 캠페인 **[!UICONTROL Navigation]** 페이지의 **섹션에서** **[!UICONTROL Campaign packages]** 링크를 클릭합니다.
1. **[!UICONTROL Create]** 버튼을 클릭합니다. 

   ![](assets/mkg_dist_add_an_entry.png)

1. 창 위의 섹션에서 [이전에](#creating-a-local-campaign-template) 지정한 캠페인 패키지 템플릿을 선택할 수 있습니다.

   기본적으로 템플릿은 **[!UICONTROL New local campaign package (localEmpty)]** 로컬 캠페인에 사용됩니다.

1. 캠페인 패키지의 레이블, 폴더 및 실행 일정을 지정합니다.

### 날짜 {#dates}

시작 및 종료 날짜는 캠페인 패키지 목록에서 캠페인의 가시성 기간을 정의합니다.

가용 일자는 캠페인을 로컬 개체에 사용할 수 있게 되는 날짜입니다(주문 예정).

>[!CAUTION]
>
>로컬 엔티티가 마감 전에 캠페인을 예약하지 않으면 캠페인을 사용할 수 없습니다.

이 정보는 아래와 같이 로컬 에이전시에 보낸 알림 메시지에서 찾을 수 있습니다.

![](assets/s_advuser_mkg_dist_local_notif.png)

### 대상자 {#audience}

로컬 캠페인의 경우 중앙 엔티티는 해당 항목을 확인하여 관련 로컬 엔티티를 지정할 수 있습니다 **[!UICONTROL Limit the package to a set of local entities]**.

![](assets/s_advuser_mkg_dist_create_mutual_entry3.png)

### 추가 설정 {#additional-settings}

패키지가 저장되면 중앙 엔티티가 **[!UICONTROL Edit]** 탭에서 편집할 수 있습니다.

![](assets/mkg_dist_edit_kit.png)

탭에서 중앙 엔티티는 **[!UICONTROL General]** 다음을 수행할 수 있습니다.

* 링크에서 캠페인 패키지 검토자를 **[!UICONTROL Approval parameters...]** 구성합니다.
* 실행 일정을 검토하고
* 로컬 엔티티를 추가하거나 삭제합니다.

>[!NOTE]
>
>기본적으로 각 엔티티는 **로컬 캠페인을 한 번만** 주문할 수 있습니다.
>   
>캠페인 패키지에서 여러 로컬 캠페인을 만들 수 있도록 하려면 **[!UICONTROL Enable multiple creation]** 옵션을 선택합니다.

![](assets/mkg_dist_local_op_multi_crea.png)

### 알림 {#notifications}

캠페인을 사용할 수 있게 되거나 등록 마감일에 도달하면 로컬 알림 그룹 운영자에게 메시지가 전송됩니다. For more on this, refer to [Organizational entities](../../campaign/using/about-distributed-marketing.md#organizational-entities).

## 캠페인 순서 지정 {#ordering-a-campaign}

캠페인 패키지는 승인된 후 구현 기간이 시작되면 로컬 엔티티에서 액세스할 수 있게 됩니다. 로컬 엔터티는 새 캠페인 패키지를 사용할 수 있음을 알리는 이메일을 수신합니다(가용 날짜에 도달하자마자).

>[!NOTE]
>
>캠페인 패키지를 만들 때 일부 로컬 개체가 지정된 경우 알림을 받는 유일한 개체가 됩니다. 로컬 엔티티를 지정하지 않은 경우 모든 로컬 엔티티가 알림을 받게 됩니다.

![](assets/mkg_dist_local_op_notification.png)

중앙 엔티티에서 제공하는 캠페인을 사용하려면 로컬 엔티티가 캠페인을 주문해야 합니다.

캠페인을 주문하려면

1. 알림 메시지 **[!UICONTROL Order campaign]** 에서 또는 Adobe Campaign의 해당 단추를 클릭합니다.

   캠페인을 주문하려면 ID와 암호를 입력합니다. 인터페이스는 웹 응용 프로그램에 정의된 페이지 세트로 구성됩니다.

   >[!NOTE]
   >
   >웹 애플리케이션은 [웹 기능](../../web/using/about-web-applications.md) 안내서에 자세히 설명되어 있습니다.

1. 첫 번째 페이지에 필요한 정보를 입력하고(주문 레이블 및 주석) 을 클릭합니다 **[!UICONTROL Next]**.

   ![](assets/mkg_dist_subscribe_step1.png)

1. 사용 가능한 매개 변수를 작성하고 주문을 승인합니다.

1. 이 주문을 승인하기 위해 로컬 엔티티가 속한 조직 엔티티의 관리자에게 알림이 전송됩니다.

   ![](assets/mkg_dist_subscribe_step3.png)

1. 정보는 로컬 및 중앙 엔티티로 반환됩니다. 로컬 엔티티는 자체 주문만 볼 수 있지만 중앙 엔티티는 아래와 같이 로컬 엔티티의 모든 주문을 볼 수 있습니다.

   ![](assets/mkg_dist_subscribe_central_view.png)

   연산자는 주문 세부 사항을 표시할 수 있습니다.

   ![](assets/mkg_dist_local_op_catalog_detail_1.png)

   이 **[!UICONTROL Edit]** 탭에는 캠페인을 정렬할 때 로컬 엔티티가 입력한 정보가 포함되어 있습니다.

   ![](assets/mkg_dist_local_op_catalog_detail_1b.png)

1. 이 주문은 중앙 실체가 승인하여 마무리해야 한다.

   ![](assets/mkg_dist_local_op_catalog_detail_3.png)

   자세한 내용은 승인 프로세스 [섹션을 참조하십시오](#approval-process) .

1. 그런 다음 로컬 운영자에게 캠페인을 사용할 수 있다는 알림이 표시됩니다. 캠페인 가용성은 **캠페인 우주 내의 캠페인 패키지 목록에서 찾을 수 있습니다** . 그런 다음 캠페인을 사용할 수 있습니다. For more on this, refer to [Accessing campaigns](../../campaign/using/accessing-campaigns.md).

   이 **[!UICONTROL Start targeting with order approval]** 옵션을 사용하면 주문이 승인되는 즉시 로컬 엔티티가 캠페인을 실행할 수 있습니다.

   ![](assets/mkg_dist_local_op_catalog_use.png)

## 주문 승인 {#approving-an-order}

캠페인 주문을 확인하려면 중앙 엔티티가 승인해야 합니다.

캠페인 **[!UICONTROL Campaign orders]** 우주를 통해 액세스되는 **개요** 를 사용하면 캠페인 주문 상태를 보고 승인할 수 있습니다.

>[!NOTE]
>
>로컬 엔티티는 승인될 때까지 주문을 변경할 수 있습니다.

### 승인 프로세스 {#approval-process}

#### 이메일 알림 {#email-notification}

캠페인이 로컬 엔티티로 주문되면 해당 검토자에게 아래와 같이 이메일을 통해 알립니다.

![](assets/mkg_dist_valid_notif_email.png)

>[!NOTE]
>
>검토자 선택은 [검토자](#reviewers) 섹션에 표시됩니다. 그들은 그 명령을 수락하거나 거부할 수 있다.

![](assets/mkg_dist_command_valid_web.png)

#### Adobe Campaign 콘솔을 통해 승인 {#approving-via-the-adobe-campaign-console}

또한 캠페인 주문 개요에서 콘솔을 통해 주문을 승인할 수 있습니다. 주문을 승인하려면 주문을 선택하고 클릭합니다 **[!UICONTROL Approve the order]**.

![](assets/mkg_dist_local_order_valid.png)

>[!NOTE]
>
>캠페인 가용성 날짜까지 캠페인을 편집하고 다시 구성할 수 있습니다. 로컬 엔티티는 **[!UICONTROL Cancel]** 단추를 클릭하여 캠페인을 거부할 수도 있습니다.

#### 캠페인 만들기 {#creating-a-campaign}

캠페인 주문이 승인되면 로컬 엔티티에서 구성하고 실행할 수 있습니다.

![](assets/mkg_dist_mutual_op_created.png)

For more on this, refer to [Accessing campaigns](../../campaign/using/accessing-campaigns.md).

### 승인 거부 {#rejecting-an-approval}

승인 담당자는 주문 또는 캠페인 패키지를 거부할 수 있습니다.

![](assets/mkg_dist_do_not_valid.png)

검토자가 주문을 거부하면 관련 알림이 관련 로컬 엔티티에 자동으로 전송됩니다. 승인을 거부한 연산자가 입력한 댓글이 표시됩니다.

캠페인 패키지 목록 페이지 또는 캠페인 주문 페이지에 정보가 표시됩니다. Adobe Campaign 콘솔에 액세스할 수 있는 로컬 엔티티에 이러한 거부에 대한 정보가 표시됩니다.

![](assets/mkg_dist_do_not_valid_view.png)

캠페인 패키지의 **[!UICONTROL Edit]** 탭에서 관련 댓글을 볼 수 있습니다.

![](assets/mkg_dist_do_not_valid_tab.png)

### 검토자 {#reviewers}

승인이 필요할 때마다 검토자는 이메일로 통보를 받습니다.

각 로컬 엔티티에 대해 캠페인 주문 승인 및 캠페인 승인을 위해 검토자가 선택됩니다. 로컬 검토자 선택에 대한 자세한 내용은 조직 [엔티티를 참조하십시오](../../campaign/using/about-distributed-marketing.md#organizational-entities).

>[!NOTE]
>
>이러한 선택이 가능하려면 주문 승인이 아직 유효하지 않아야 합니다.

### 주문 취소 {#canceling-an-order}

중앙 기관은 주문 대시보드에 있는 **[!UICONTROL Delete]** 단추를 사용하여 주문을 취소할 수 있습니다.

![](assets/mkg_dist_local_op_cancel.png)

이렇게 하면 보기에서 캠페인이 **[!UICONTROL Campaign orders]** 취소됩니다.
