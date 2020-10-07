---
title: 예제
seo-title: 예제
description: 예제
seo-description: null
page-status-flag: never-activated
uuid: bfc9bb13-500b-4435-b56a-550588a240bb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: distributed-marketing
discoiquuid: 7b0aef75-345d-45be-b7d0-a9f6944ee678
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1298'
ht-degree: 0%

---


# 예제{#examples}

## 로컬 캠페인 만들기(폼) {#creating-a-local-campaign--by-form-}

By **양식** 유형 웹 인터페이스에서는 **웹 애플리케이션을 사용합니다**. 구성에 따라 이 웹 애플리케이션에는 정의된 개인화된 요소의 모든 유형이 포함될 수 있습니다. 예를 들어 대상, 예산, 컨텐츠 등을 평가하는 링크를 제안할 수 있습니다. 전용 API를 통해

>[!NOTE]
>
>API는 계약에 따라 액세스하는 전용 문서에 자세히 설명되어 있습니다. API [를 참조하십시오](../../configuration/using/about-web-services.md).
>
>이 예에서 사용되는 웹 응용 프로그램은 Adobe Campaign에서 바로 사용할 수 있는 웹 앱이 아닙니다. 캠페인에서 양식을 사용하려면 전용 웹 응용 프로그램을 만들어야 합니다.

캠페인 템플릿을 만들 때 웹 애플리케이션의 세부 정보에 액세스하려면 **[!UICONTROL Zoom]** 링크의 **[!UICONTROL Web interface]** 옵션 **[!UICONTROL Advanced campaign settings...]** 내에 있는 아이콘을 클릭합니다.

![](assets/mkg_dist_local_op_form1.png)

>[!NOTE]
>
>웹 애플리케이션 매개 변수는 캠페인 템플릿에서만 사용할 수 있습니다.

탭 **[!UICONTROL Edit]** 에서 **캠페인 주문** 활동을 선택하고 열어 해당 컨텐츠에 액세스합니다.

![](assets/mkg_dist_web_app1.png)

이 예에서 **캠페인 주문** 활동에는 다음이 포함됩니다.

* 주문 도중 로컬 엔티티가 입력할 필드

   ![](assets/mkg_dist_web_app2.png)

* 로컬 엔티티가 캠페인을 평가할 수 있도록 해주는 링크(예: 대상, 예산, 컨텐츠 등),

   ![](assets/mkg_dist_web_app3.png)

* 이러한 평가의 결과를 계산하고 표시할 수 있는 스크립트입니다.

   ![](assets/mkg_dist_web_app4.png)

이 예에서 다음 API가 사용됩니다.

* 대상 평가를 위해

   ```
   var res = nms.localOrder.EvaluateTarget(ctx.localOrder);
   ```

* 예산을 평가하려면

   ```
   var res = nms.localOrder.EvaluateDeliveryBudget(ctx.@deliveryId, NL.XTK.parseNumber(ctx.@compt));
   ```

* 컨텐츠 평가를 위해

   ```
   var res = nms.localOrder.EvaluateContent(ctx.localOrder, ctx.@deliveryId, "html", resSeed.@id);
   ```

## 협업 캠페인 만들기(타겟 승인별) {#creating-a-collaborative-campaign--by-target-approval-}

### 소개 {#introduction}

여러분은 미국 전역의 온라인 상점과 몇 개의 부티크가 있는 대형 의류 브랜드의 마케팅 매니저입니다. 봄을 맞아 최고의 고객에게 카탈로그에서 50% 할인된 가격의 드레스를 제공하는 특별 프로모션을 마련하기로 했습니다.

이 할인 혜택은 연초부터 300달러 이상을 지출한 미국 내 최고 고객을 대상으로 마련되었습니다.

따라서 Distributed Marketing을 사용하여 특별 오퍼가 포함된 이메일 배달을 받을 스토어의 최상의 클라이언트(지역별로 그룹화됨)를 선택할 수 있도록 해주는 협업 캠페인(타겟 승인별)을 만듭니다.

이 예제의 첫 번째 부분에서는 캠페인 생성 알림을 받는 로컬 엔터티와 이를 사용하여 캠페인을 평가하고 순서를 지정하는 방법을 보여 줍니다.

이 예제의 두 번째 부분에서는 캠페인을 만드는 방법을 설명합니다.

단계는 다음과 같습니다.

**로컬 엔티티**

1. 캠페인 만들기 알림을 사용하여 중앙 엔티티에서 선택한 연락처 목록에 액세스합니다.
1. 연락처를 선택하고 참여를 승인합니다.

**중앙 엔티티의 경우:**

1. 활동을 **[!UICONTROL Data distribution]** 만듭니다.
1. 협업 캠페인을 만듭니다.
1. 캠페인을 게시합니다.

### 로컬 엔티티 측면 {#local-entity-side}

1. 캠페인에 참여하도록 선택한 로컬 엔티티는 이메일 알림을 받게 됩니다.

   ![](assets/mkg_dist_use_case_target_valid8.png)

1. 이 **[!UICONTROL Access your contact list and approve targeting]** 링크를 클릭하면 로컬 엔티티에는 캠페인에 대해 선택한 클라이언트 목록에 대한 액세스(웹 브라우저를 통해)가 제공됩니다.

   ![](assets/mkg_dist_use_case_target_valid9.png)

1. 해당 지역 엔터티는 연초부터 유사한 오퍼를 위해 이미 연락되었기 때문에 목록에서 특정 연락처를 확인하지 않습니다.

   ![](assets/mkg_dist_use_case_target_valid10.png)

확인이 승인되면 캠페인을 자동으로 시작할 수 있습니다.

### 중앙 엔티티 쪽 {#central-entity-side}

#### 데이터 배포 활동 만들기 {#creating-a-data-distribution-activity}

1. 공동 작업 캠페인을 설정하려면(타겟 승인별) 먼저 캠페인을 만들어야 합니다 **[!UICONTROL Data distribution activity]**. 노드에서 **[!UICONTROL New]** 아이콘을 **[!UICONTROL Resources > Campaign management > Data distribution]** 클릭합니다.

   ![](assets/mkg_dist_use_case_target_valid3.png)

1. 탭에서 다음을 **[!UICONTROL General]** 지정해야 합니다.

   * the **[!UICONTROL Targeting dimension]**. 여기에서 **데이터 배포는** 수신자에게 **수행됩니다**.
   * the **[!UICONTROL Distribution type]**. 고정 크기 **또는** 크기를 백분율로 선택할 수 있습니다 ****.
   * the **[!UICONTROL Assignment type]**. 로컬 엔티티 **옵션을** 선택합니다.
   * the **[!UICONTROL Distribution type]**. 여기에서 연락처 및 로컬 엔티티 간의 관계를 식별할 수 있는 수신자 테이블에 있는 **[!UICONTROL Origin (@origin)]** 필드입니다.
   * 필드 **[!UICONTROL Approval storage]** . [수신자 **로컬 승인] 옵션을** 선택합니다.

1. In the **[!UICONTROL Breakdown]** tab, specify:

   * 이 **[!UICONTROL Distribution field value]**&#x200B;는 향후 캠페인에 관련된 로컬 개체에 해당합니다.
   * 로컬 엔티티입니다 **[!UICONTROL label]**.
   * ( **[!UICONTROL Size]** 고정 또는 백분율). 기본값 **0은** 로컬 엔티티에 연결된 수신자를 모두 선택하는 것을 포함합니다.

   ![](assets/mkg_dist_use_case_target_valid4.png)

1. 새로운 데이터 배포 저장

#### 공동 작업 캠페인 만들기 {#creating-a-collaborative-campaign}

1. 노드에서 **[!UICONTROL Campaign management > Campaign]** 새 노드를 만듭니다 **[!UICONTROL collaborative campaign (by target approval)]**.
1. 탭에서 **[!UICONTROL Targeting and workflows]** 캠페인에 대한 워크플로우를 만듭니다. 여기에는 활동에 의해 정의된 **분할** 활동 **[!UICONTROL Record count limitation]** 이 **[!UICONTROL Data distribution]** 포함되어야 합니다.

   ![](assets/mkg_dist_use_case_target_valid5.png)

1. 지정할 수 있는 **[!UICONTROL Local approval]** 작업을 추가합니다.

   * 알림에서 로컬 엔티티로 전송될 메시지 내용,
   * 승인 알림
   * 캠페인의 예상 처리.

   ![](assets/mkg_dist_use_case_target_valid7.png)

1. 기록 저장

#### 캠페인 게시 {#publishing-the-campaign}

이제 캠페인 우주에서 **캠페인 패키지** 를 추가할 수 **있습니다** .

1. 원하는 컨텐츠를 **[!UICONTROL Reference campaign]**&#x200B;선택하십시오. 패키지의 **[!UICONTROL Edit]** 탭에서 캠페인에 사용할 항목 **[!UICONTROL Approval mode]** 을 선택할 수 있습니다.

   * 수동 **** 모드에서 로컬 개체가 중앙 엔티티의 초대를 수락하면 캠페인에 참여합니다. 캠페인의 참여를 확인하기 위해 관리자의 승인이 필요한 경우 사전 선택된 연락처를 삭제할 수 있습니다.
   * 자동 **** 모드에서 로컬 엔티티가 캠페인에서 자신을 등록 해제하지 않는 한 캠페인에 참여해야 합니다. 승인하지 않고 연락처를 삭제할 수 있습니다.

   ![](assets/mkg_dist_use_case_target_valid.png)

1. 탭에서 **[!UICONTROL Description]** 캠페인에 대한 설명과 로컬 엔티티로 전송할 문서를 추가할 수 있습니다.

   ![](assets/mkg_dist_use_case_target_valid1.png)

1. 캠페인 패키지를 승인한 후 워크플로우를 시작하여 패키지를 게시하고 패키지 목록에 있는 모든 로컬 엔티티에서 사용할 수 있도록 합니다.

   ![](assets/mkg_dist_use_case_target_valid2.png)

## 양식에서 협업 캠페인 만들기 {#creating-a-collaborative-campaign--by-form-}

### 소개 {#introduction-1}

여러분은 미국 전역의 온라인 상점과 몇 개의 부티크가 있는 대형 화장 브랜드의 마케팅 매니저입니다. 겨울 재고를 언로드하고 새 재고를 위한 공간을 확보하려면 다음 두 가지 클라이언트 카테고리를 대상으로 하는 특별 오퍼를 만듭니다.나이가 들수록 민감한 피부 관리 제품을 제공할 30대 이상, 그리고 보다 기본적인 피부 관리 제품을 제공할 30대 미만을 제공합니다.

따라서 Distributed Marketing을 사용하여 연령별로 서로 다른 저장소에서 클라이언트를 선택할 수 있도록 해주는 형태별 협업 캠페인을 생성하기로 합니다. 이러한 고객은 연령 범위에 따라 개인화된 특별 오퍼가 포함된 이메일을 받게 됩니다.

이 예제의 첫 번째 부분에서는 캠페인 생성 알림을 받는 로컬 엔터티와 이를 사용하여 캠페인을 평가하고 순서를 지정하는 방법을 보여 줍니다.

이 예제의 두 번째 부분에서는 캠페인을 만드는 방법을 설명합니다.

단계는 다음과 같습니다.

**로컬 엔티티**

1. 캠페인 만들기 알림을 사용하여 온라인 양식에 액세스합니다.
1. 캠페인(타겟, 컨텐츠, 전달 볼륨)을 개인화합니다.
1. 이러한 필드를 확인하고 필요한 경우 변경합니다.
1. 기여도 승인
1. 로컬 엔티티(또는 중앙 엔티티)의 관리자가 구성 및 참여를 승인합니다.

**중앙 엔티티의 경우:**

1. 협업 캠페인을 만듭니다.
1. 로컬 캠페인에 대해 **[!UICONTROL Advanced campaign settings...]** 원하는 대로 구성합니다.
1. 로컬 캠페인에서와 마찬가지로 캠페인 워크플로우와 배달을 구성합니다.
1. 웹 양식을 업데이트합니다.
1. 캠페인 패키지를 만들고 게시합니다.

### 로컬 엔티티 측면 {#local-entity-side-1}

1. 캠페인에 참여하도록 선택한 로컬 엔티티는 캠페인에 참여한다는 내용의 이메일 알림을 받습니다.

   ![](assets/mkg_dist_use_case_form_7.png)

1. 로컬 엔티티는 맞춤형 양식을 작성한 다음 다음을 수행합니다.

   * 타겟과 예산을 평가하고
   * 전달 내용 미리 보기,
   * 참여 승인

      ![](assets/mkg_dist_use_case_form_8.png)

1. 주문 유효성 확인을 담당하는 연산자가 해당 참여를 승인합니다.

   ![](assets/mkg_dist_use_case_form_9.png)

### 중앙 엔티티 쪽 {#central-entity-side-1}

1. 양식에서 협업 캠페인을 구현하려면 **협업 캠페인(양식 기준)** 템플릿을 사용하여 캠페인을 만들어야 합니다.

   ![](assets/mkg_dist_use_case_form_1.png)

1. 캠페인의 **[!UICONTROL Edit]** 탭에서 **[!UICONTROL Advanced campaign settings...]** 링크를 클릭하여 로컬 캠페인으로 구성합니다. 로컬 캠페인 [만들기(양식별)를 참조하십시오](#creating-a-local-campaign--by-form-).

   ![](assets/mkg_dist_use_case_form_2.png)

1. 캠페인 워크플로우와 웹 양식을 구성합니다. 로컬 캠페인 [만들기(양식별)를 참조하십시오](#creating-a-local-campaign--by-form-).
1. 실행 일정 및 관련 로컬 엔티티를 지정하여 캠페인 패키지를 생성합니다.

   ![](assets/mkg_dist_use_case_form_3.png)

1. 탭에서 승인 모드를 선택하여 패키지 구성을 **[!UICONTROL Edit]** 마무리합니다.

   ![](assets/mkg_dist_use_case_form_4.png)

1. 이 **[!UICONTROL Description]** 탭에서 캠페인 패키지 설명, 패키지가 게시될 때 로컬 개체에 전송할 알림 메시지를 입력하고 모든 정보를 제공하는 문서를 캠페인 패키지에 첨부할 수 있습니다.

   ![](assets/mkg_dist_use_case_form_5.png)

1. 패키지를 승인하여 게시합니다.

   ![](assets/mkg_dist_use_case_form_6.png)

