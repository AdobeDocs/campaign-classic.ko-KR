---
product: campaign
title: 로컬 캠페인 만들기
description: 로컬 캠페인 만들기
feature: Distributed Marketing
exl-id: 17b5865a-5e04-4b3b-8b6a-12d5c1a9c1da
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1565'
ht-degree: 1%

---

# 로컬 캠페인 만들기{#creating-a-local-campaign}



로컬 캠페인은 **특정 실행 일정**&#x200B;을(를) 사용하여 **[!UICONTROL campaign packages]** 목록에서 참조된 템플릿에서 만든 인스턴스입니다. 중앙 엔티티에 의해 설정 및 구성된 캠페인 템플릿을 사용하여 로컬 통신 요구 사항을 충족하는 것이 목표입니다. 로컬 작업을 구현하는 주요 단계는 다음과 같습니다.

**중앙 엔터티의 경우**

1. 로컬 캠페인 템플릿 만들기.
1. 템플릿에서 캠페인 패키지 만들기
1. 캠페인 패키지 게시.
1. 주문 승인.

**로컬 엔터티의 경우**

1. 캠페인 주문.
1. 캠페인 실행.

## 로컬 캠페인 템플릿 만들기 {#creating-a-local-campaign-template}

캠페인 패키지를 만들려면 먼저 **[!UICONTROL Resources > Templates]** 노드를 통해 **캠페인 템플릿**&#x200B;을 만들어야 합니다.

새 로컬 템플릿을 만들려면 기본 **[!UICONTROL Local campaign (opLocal)]** 템플릿을 복제하십시오.

![](assets/mkg_dist_local_op_creation.png)

캠페인 템플릿 이름을 지정하고 사용 가능한 필드를 작성합니다.

![](assets/mkg_dist_local_op_creation1.png)

캠페인 창에서 **[!UICONTROL Edit]** 탭을 클릭한 다음 **[!UICONTROL Advanced campaign settings...]** 링크를 클릭합니다.

![](assets/mkt_distr_4.png)

### 웹 인터페이스 {#web-interface}

**분산 마케팅** 탭에서 웹 인터페이스의 유형을 선택하고 로컬 엔터티가 주문을 할 때 입력할 기본값과 매개 변수를 지정할 수 있습니다.

웹 인터페이스는 캠페인 주문 시 로컬 엔티티가 채울 양식에 해당합니다.

템플릿에서 만든 캠페인에 적용할 웹 인터페이스 유형을 선택합니다.

![](assets/mkt_distr_1.png)

다음 네 가지 유형의 웹 인터페이스를 사용할 수 있습니다.

* **[!UICONTROL By brief]** : 로컬 엔터티가 캠페인 구성을 설명하는 설명을 제공해야 합니다. 주문이 승인되면 중앙 엔티티는 캠페인 전체를 구성하고 실행합니다.

  ![](assets/mkt_distr_6.png)

* **[!UICONTROL By form]** : 로컬 엔터티는 사용된 템플릿에 따라 콘텐츠, 대상, 최대 크기, 개인화 필드를 사용한 만들기 및 추출 날짜를 편집할 수 있는 웹 양식에 액세스할 수 있습니다. 로컬 엔티티는 이 웹 양식에서 타겟을 평가하고 콘텐츠를 미리 볼 수 있습니다.

  ![](assets/mkt_distr_8.png)

  제공된 양식이 템플릿의 **[!UICONTROL Advanced campaign settings...]** 링크에 있는 **[!UICONTROL web Interface]** 필드의 드롭다운 목록에서 선택해야 하는 웹 응용 프로그램에 지정되었습니다. [로컬 캠페인 만들기(양식으로)](examples.md#creating-a-local-campaign--by-form-)를 참조하세요.

  >[!NOTE]
  >
  >이 예제에 사용된 웹 응용 프로그램이 예입니다. 양식을 사용하려면 특정 웹 앱을 만들어야 합니다. [API](../../configuration/using/about-web-services.md)을(를) 참조하세요.

  ![](assets/mkt_distr_7.png)

* **[!UICONTROL By external form]** : 로컬 엔터티가 엑스트라넷의 캠페인 매개 변수에 액세스할 수 있습니다(Adobe Campaign 아님). 이러한 매개 변수는 **로컬 캠페인(양식 기준)**&#x200B;의 매개 변수와 동일합니다.
* **[!UICONTROL Pre-set]** : 로컬 엔터티는 기본 양식을 현지화하지 않고 사용하여 캠페인을 주문합니다.

  ![](assets/mkt_distr_5.png)

### 기본값 {#default-values}

로컬 엔터티에서 완료할 **[!UICONTROL Default values]**&#x200B;을(를) 선택하십시오. 예제:

* 연락 및 추출 일자,
* 대상 특성(연령 세그먼트 등).

![](assets/mkg_dist_local_op_creation2.png)

**[!UICONTROL Parent marketing program]** 및 **[!UICONTROL Charge]** 필드를 완료합니다.

![](assets/mkg_dist_local_op_creation3.png)

### 승인 {#approvals}

**[!UICONTROL Advanced parameters for campaign entry]** 링크에서 최대 검토자 수를 지정할 수 있습니다.

![](assets/s_advuser_mkg_dist_add_valid_op1.png)

검토자는 캠페인 주문 시 로컬 엔티티에 의해 입력됩니다.

![](assets/mkt_distr_5.png)

캠페인에 대한 검토자의 이름을 지정하지 않으려면 0을 입력합니다.

### 문서 {#documents}

로컬 엔티티 운영자가 문서(텍스트 파일, 스프레드시트, 이미지, 캠페인 설명 등)를 연결할 수 있도록 할 수 있습니다. 주문을 생성할 때 로컬 캠페인에 사용됩니다. **[!UICONTROL Advanced parameters for campaign entry...]** 링크를 사용하여 문서 수를 제한할 수 있습니다. 이렇게 하려면 **[!UICONTROL Number of documents]** 필드에 허용된 최대 수를 입력하기만 하면 됩니다.

![](assets/s_advuser_mkg_dist_local_docs.png)

캠페인 패키지를 주문할 때 양식에서 템플릿의 해당 필드에 표시된 만큼의 문서를 연결할 것을 제안합니다.

![](assets/s_advuser_mkg_dist_add_docs.png)

문서 업로드 필드를 표시하지 않으려면 **[!UICONTROL Number of documents]** 필드에 **[!UICONTROL 0]**&#x200B;을(를) 입력하십시오.

>[!NOTE]
>
>**[!UICONTROL Do not display the page used to enter the campaign parameters]**&#x200B;을(를) 확인하여 **[!UICONTROL Advanced parameters for campaign entry]**&#x200B;을(를) 비활성화할 수 있습니다.

![](assets/s_advuser_mkg_dist_disable_op_parameters.png)

### 워크플로 {#workflow}

**[!UICONTROL Targeting and workflows]** 탭에서 **[!UICONTROL Advanced campaign settings...]**&#x200B;에 지정된 **[!UICONTROL Default values]**&#x200B;을(를) 수집하고 게재를 만드는 캠페인 워크플로우를 만듭니다.

![](assets/mkg_dist_local_op_creation4b.png)

**[!UICONTROL Query]** 활동을 두 번 클릭하여 지정된 **[!UICONTROL Default values]**&#x200B;에 따라 구성합니다.

![](assets/mkt_dist_local_campaign_localize_query.png)

### 게재 {#delivery}

**[!UICONTROL Audit]** 탭에서 **[!UICONTROL Detail...]** 아이콘을 클릭하여 선택한 게재에 대한 **[!UICONTROL Scheduling]**&#x200B;을(를) 봅니다.

![](assets/mkg_dist_local_op_creation4c.png)

**[!UICONTROL Scheduling]** 아이콘을 사용하면 게재의 연락처 및 실행 날짜를 구성할 수 있습니다.

![](assets/mkg_dist_local_op_creation4d.png)

필요한 경우 게재의 최대 크기를 구성합니다.

![](assets/mkg_dist_local_op_creation4e.png)

게재 HTML을 찾습니다. 예를 들어 **[!UICONTROL Delivery > Current order > Additional fields]**&#x200B;에서 **[!UICONTROL Age segment]** 필드를 사용하여 대상 기간에 따라 게재를 찾습니다.

![](assets/mkt_dist_local_campaign_localize_html.png)

캠페인 템플릿을 저장합니다. 이제 **[!UICONTROL Create]** 단추를 클릭하여 **[!UICONTROL Campaigns]** 탭의 **[!UICONTROL Campaign packages]** 보기에서 사용할 수 있습니다.

![](assets/mkt_distr_9.png)

>[!NOTE]
>
>캠페인 템플릿 및 일반 구성은 [캠페인 템플릿](../../campaign/using/marketing-campaign-templates.md#campaign-templates)에 자세히 설명되어 있습니다.

## 캠페인 패키지 만들기 {#creating-the-campaign-package}

캠페인 템플릿을 로컬 엔티티에서 사용할 수 있으려면 목록에 추가해야 합니다. 이를 위해서는 중앙 기관이 새로운 패키지를 만들 필요가 있다.

다음 단계를 적용합니다.

1. **캠페인** 페이지의 **[!UICONTROL Navigation]** 섹션에서 **[!UICONTROL Campaign packages]** 링크를 클릭합니다.
1. **[!UICONTROL Create]** 버튼을 클릭합니다.

   ![](assets/mkg_dist_add_an_entry.png)

1. 창 위의 섹션에서 지정된 [이전](#creating-a-local-campaign-template) 캠페인 패키지 템플릿을 선택할 수 있습니다.

   기본적으로 **[!UICONTROL New local campaign package (localEmpty)]** 템플릿은 로컬 캠페인에 사용됩니다.

1. 캠페인 패키지의 레이블, 폴더 및 실행 일정을 지정합니다.

### 날짜 {#dates}

시작 및 종료 날짜는 캠페인 패키지 목록에서 캠페인의 가시성 기간을 정의합니다.

가용 일자는 로컬 엔티티(주문)가 캠페인을 사용할 수 있는 일자입니다.

>[!CAUTION]
>
>마감일 이전에 지역 엔티티가 캠페인을 예약하지 않으면 사용할 수 없습니다.

이 정보는 아래와 같이 로컬 에이전시로 전송되는 알림 메시지에서 찾을 수 있습니다.

![](assets/s_advuser_mkg_dist_local_notif.png)

### 대상자 {#audience}

로컬 캠페인의 경우 중앙 엔터티는 **[!UICONTROL Limit the package to a set of local entities]**&#x200B;을(를) 확인하여 관련된 로컬 엔터티를 지정할 수 있습니다.

![](assets/s_advuser_mkg_dist_create_mutual_entry3.png)

### 추가 설정 {#additional-settings}

패키지가 저장되면 중앙 엔터티는 **[!UICONTROL Edit]** 탭에서 편집할 수 있습니다.

![](assets/mkg_dist_edit_kit.png)

**[!UICONTROL General]** 탭에서 중앙 엔터티는 다음을 수행할 수 있습니다.

* **[!UICONTROL Approval parameters...]** 링크에서 캠페인 패키지 검토자를 구성합니다.
* 실행 일정 검토,
* 로컬 엔티티를 추가하거나 삭제합니다.

>[!NOTE]
>
>기본적으로 각 엔터티는 **로컬 캠페인**&#x200B;을(를) 한 번만 주문할 수 있습니다.
>   
>캠페인 패키지에서 여러 개의 로컬 캠페인을 만들 수 있도록 하려면 **[!UICONTROL Enable multiple creation]** 옵션을 선택하십시오.

![](assets/mkg_dist_local_op_multi_crea.png)

### 알림 {#notifications}

캠페인을 사용할 수 있거나 등록 기한에 도달하면 로컬 알림 그룹의 운영자에게 메시지가 전송됩니다. 자세한 내용은 [조직 엔터티](about-distributed-marketing.md#organizational-entities)를 참조하세요.

## 캠페인 주문 {#ordering-a-campaign}

로컬 엔티티가 승인되고 구현 기간이 시작되면 Campaign 패키지에 액세스할 수 있습니다. 로컬 엔티티는 새 캠페인 패키지를 사용할 수 있음을 알리는 이메일을 받습니다(사용 가능한 날짜에 도달하자마자).

>[!NOTE]
>
>캠페인 패키지를 생성할 때 일부 로컬 엔티티를 지정한 경우 해당 엔티티만 알림을 받습니다. 로컬 엔티티를 지정하지 않은 경우 모든 로컬 엔티티에 알림이 전송됩니다.

![](assets/mkg_dist_local_op_notification.png)

중앙 엔티티가 제공하는 캠페인을 사용하려면 로컬 엔티티가 주문해야 합니다.

캠페인을 주문하려면 다음을 수행하십시오.

1. 알림 메시지에서 **[!UICONTROL Order campaign]**&#x200B;을(를) 클릭하거나 Adobe Campaign에서 해당 단추를 클릭합니다.

   캠페인을 주문하려면 ID와 암호를 입력합니다. 인터페이스는 웹 애플리케이션에 정의된 페이지 세트로 구성됩니다.

   >[!NOTE]
   >
   >웹 응용 프로그램에 대한 자세한 내용은 [이 섹션](../../web/using/about-web-applications.md)을 참조하세요.

1. 첫 페이지(주문 레이블 및 댓글)에 필요한 정보를 입력하고 **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다.

   ![](assets/mkg_dist_subscribe_step1.png)

1. 사용 가능한 매개 변수를 완료하고 주문을 승인합니다.

1. 이 주문을 승인하려면 로컬 엔티티가 속한 조직 엔티티의 관리자에게 알림이 전송됩니다.

   ![](assets/mkg_dist_subscribe_step3.png)

1. 이 정보는 로컬 및 중앙 엔티티에 반환됩니다. 로컬 엔티티는 자체 주문만 볼 수 있지만, 중앙 엔티티는 아래와 같이 로컬 엔티티의 모든 주문을 볼 수 있습니다.

   ![](assets/mkg_dist_subscribe_central_view.png)

   연산자는 주문 세부 사항을 표시할 수 있습니다.

   ![](assets/mkg_dist_local_op_catalog_detail_1.png)

   **[!UICONTROL Edit]** 탭에는 캠페인을 정렬할 때 로컬 엔터티에서 입력한 정보가 포함되어 있습니다.

   ![](assets/mkg_dist_local_op_catalog_detail_1b.png)

1. 이 명령은 최종 확정되려면 중앙 기관의 승인을 받아야 한다.

   ![](assets/mkg_dist_local_op_catalog_detail_3.png)

   자세한 내용은 [승인 프로세스](#approval-process) 섹션을 참조하세요.

1. 그런 다음 로컬 운영자에게 캠페인이 사용 가능하다는 알림이 표시됩니다. 캠페인 가용성은 **캠페인** 탭 내의 캠페인 패키지 목록에서 찾을 수 있습니다. 그런 다음 캠페인을 사용할 수 있습니다. 자세한 내용은 [캠페인 액세스](accessing-campaigns.md)를 참조하세요.

   **[!UICONTROL Start targeting with order approval]** 옵션을 사용하면 로컬 엔터티에서 주문이 승인되는 즉시 캠페인을 실행할 수 있습니다.

   ![](assets/mkg_dist_local_op_catalog_use.png)

## 주문 승인 {#approving-an-order}

캠페인 주문을 확인하려면 중앙 엔티티가 승인해야 합니다.

**캠페인** 탭을 통해 액세스할 수 있는 **[!UICONTROL Campaign orders]** 개요를 사용하면 캠페인 주문 상태를 보고 승인할 수 있습니다.

>[!NOTE]
>
>로컬 엔티티는 승인될 때까지 순서를 변경할 수 있습니다.

### 승인 프로세스 {#approval-process}

#### 이메일 알림 {#email-notification}

캠페인이 로컬 엔티티에 의해 주문되면 해당 검토자는 아래와 같이 이메일로 알림을 받습니다.

![](assets/mkg_dist_valid_notif_email.png)

>[!NOTE]
>
>검토자를 선택하면 [검토자](#reviewers) 섹션에 표시됩니다. 그들은 그 명령을 받아들이거나 거부할 수 있다.

![](assets/mkg_dist_command_valid_web.png)

#### Adobe Campaign 콘솔을 통해 승인 {#approving-via-the-adobe-campaign-console}

캠페인 주문 개요에서 콘솔을 통해 주문을 승인할 수도 있습니다. 주문을 승인하려면 주문을 선택하고 **[!UICONTROL Approve the order]**&#x200B;을(를) 클릭합니다.

![](assets/mkg_dist_local_order_valid.png)

>[!NOTE]
>
>캠페인 가용 날짜까지 캠페인을 계속 편집 및 재구성할 수 있습니다. 로컬 엔터티가 **[!UICONTROL Cancel]** 단추를 클릭하여 캠페인을 거부할 수도 있습니다.

#### 캠페인 만들기 {#creating-a-campaign}

캠페인 주문이 승인되면 로컬 엔티티에 의해 구성되고 실행될 수 있습니다.

![](assets/mkg_dist_mutual_op_created.png)

자세한 내용은 [캠페인 액세스](accessing-campaigns.md)를 참조하세요.

### 승인 거부 {#rejecting-an-approval}

승인을 담당하는 운영자는 주문이나 캠페인 패키지를 거부할 수 있습니다.

![](assets/mkg_dist_do_not_valid.png)

검토자가 주문을 거부하면 관련 알림이 관련 로컬 엔티티에 자동으로 전송됩니다. 여기에는 승인을 거부한 운영자가 입력한 댓글이 표시됩니다.

정보는 캠페인 패키지 목록 페이지 또는 캠페인 주문 페이지에 표시됩니다. Adobe Campaign 콘솔에 액세스할 수 있는 경우 로컬 엔티티에 이 거부에 대한 알림이 표시됩니다.

![](assets/mkg_dist_do_not_valid_view.png)

캠페인 패키지의 **[!UICONTROL Edit]** 탭에서 관련 주석을 볼 수 있습니다.

![](assets/mkg_dist_do_not_valid_tab.png)

### 검토자 {#reviewers}

승인이 필요할 때마다 검토자에게 이메일로 알림이 전송됩니다.

각 로컬 엔티티에 대해 캠페인 주문 승인 및 캠페인 승인을 위해 검토자가 선택됩니다. 로컬 검토자 선택에 대한 자세한 내용은 [조직 엔터티](about-distributed-marketing.md#organizational-entities)를 참조하세요.

>[!NOTE]
>
>이 선택이 가능하려면 주문 승인이 아직 효과적이지 않아야 합니다.

### 주문 취소 {#canceling-an-order}

중앙 에이전트에서 주문 대시보드에 있는 **[!UICONTROL Delete]** 버튼을 사용하여 주문을 취소할 수 있습니다.

![](assets/mkg_dist_local_op_cancel.png)

**[!UICONTROL Campaign orders]** 보기에서 캠페인을 취소합니다.
