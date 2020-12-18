---
solution: Campaign Classic
product: campaign
title: 예제
description: 예제
audience: campaign
content-type: reference
topic-tags: distributed-marketing
translation-type: tm+mt
source-git-commit: c625b4109e2cb47446331cd009ff9827c8267c93
workflow-type: tm+mt
source-wordcount: '1297'
ht-degree: 0%

---


# 예제{#examples}

## 로컬 캠페인 만들기(폼) {#creating-a-local-campaign--by-form-}

**By form** 형식 웹 인터페이스는 **웹 응용 프로그램**&#x200B;을 사용합니다. 구성에 따라 이 웹 응용 프로그램에는 정의된 개인화된 요소의 모든 유형이 포함될 수 있습니다. 예를 들어 타겟, 예산, 컨텐츠 등을 평가하는 링크를 제안할 수 있습니다. 전용 API를 통해 제공됩니다.

>[!NOTE]
>
>API는 계약에 따라 달라지는 전용 문서에 자세히 설명되어 있습니다. [API](../../configuration/using/about-web-services.md)을 참조하십시오.
>
>이 예제에 사용되는 웹 응용 프로그램은 Adobe Campaign에 기본적으로 제공되는 웹 앱이 아닙니다. 캠페인에서 양식을 사용하려면 전용 웹 응용 프로그램을 만들어야 합니다.

캠페인 템플릿을 만들 때 **[!UICONTROL Advanced campaign settings...]** 링크의 **[!UICONTROL Web interface]** 옵션 내에서 **[!UICONTROL Zoom]** 아이콘을 클릭하여 웹 응용 프로그램의 세부 정보에 액세스합니다.

![](assets/mkg_dist_local_op_form1.png)

>[!NOTE]
>
>웹 애플리케이션 매개 변수는 캠페인 템플릿에서만 사용할 수 있습니다.

**[!UICONTROL Edit]** 탭에서 **캠페인 주문** 활동을 선택하고 이 활동을 열어 해당 컨텐츠에 액세스합니다.

![](assets/mkg_dist_web_app1.png)

이 예에서 **캠페인 주문** 활동에는 다음이 포함됩니다.

* 주문 도중 로컬 엔티티가 입력하는 필드

   ![](assets/mkg_dist_web_app2.png)

* 로컬 엔티티가 캠페인을 평가할 수 있도록 해주는 링크(예: 대상, 예산, 컨텐츠 등),

   ![](assets/mkg_dist_web_app3.png)

* 이러한 평가의 결과를 계산하고 표시할 수 있는 스크립트입니다.

   ![](assets/mkg_dist_web_app4.png)

이 예에서는 다음 API가 사용됩니다.

* 대상 평가에 대해서는

   ```
   var res = nms.localOrder.EvaluateTarget(ctx.localOrder);
   ```

* 예산 평가를 위해서는

   ```
   var res = nms.localOrder.EvaluateDeliveryBudget(ctx.@deliveryId, NL.XTK.parseNumber(ctx.@compt));
   ```

* 컨텐츠 평가를 위해서는

   ```
   var res = nms.localOrder.EvaluateContent(ctx.localOrder, ctx.@deliveryId, "html", resSeed.@id);
   ```

## 협업 캠페인 만들기(목표 승인 기준) {#creating-a-collaborative-campaign--by-target-approval-}

### 소개 {#introduction}

여러분은 미국 전역에 온라인 스토어와 여러 부티크가 있는 대형 의류 브랜드의 마케팅 매니저입니다. 봄이 온 지금, 여러분은 최고의 고객에게 카탈로그에서 50%의 옷을 제공해줄 특별 제안을 만들기로 결정했어요.

이 할인 혜택은 연초부터 300달러 이상을 지출한 미국 내 최고 고객을 대상으로 마련되었습니다.

따라서 Distributed Marketing을 사용하여 특별한 오퍼가 포함된 이메일 배달을 받을 스토어의 베스트 클라이언트(지역별로 그룹화됨)를 선택할 수 있도록 해주는 협업 캠페인(타겟 승인별)을 만듭니다.

이 예제의 첫 번째 부분에서는 캠페인 만들기 알림을 받는 로컬 엔티티와 캠페인을 평가하고 순서를 지정하는 데 사용할 수 있는 방법을 보여 줍니다.

이 예제의 두 번째 부분에서는 캠페인을 만드는 방법을 설명합니다.

이 단계는 다음과 같습니다.

**로컬 엔티티의 경우**

1. 중앙 엔티티에서 선택한 연락처 목록에 액세스하려면 캠페인 만들기 알림을 사용합니다.
1. 담당자를 선택하고 참여를 승인합니다.

**중앙 엔티티의 경우:**

1. **[!UICONTROL Data distribution]** 활동을 만듭니다.
1. 협업 캠페인을 만듭니다.
1. 캠페인을 게시합니다.

### 로컬 엔티티 측면 {#local-entity-side}

1. 캠페인에 참여하도록 선택된 로컬 엔티티는 이메일 알림을 수신하게 됩니다.

   ![](assets/mkg_dist_use_case_target_valid8.png)

1. **[!UICONTROL Access your contact list and approve targeting]** 링크를 클릭하면 로컬 엔티티에 캠페인에 대해 선택한 클라이언트 목록에 대한 액세스(웹 브라우저를 통해)가 제공됩니다.

   ![](assets/mkg_dist_use_case_target_valid9.png)

1. 연초 이후 유사한 오퍼에 대해 이미 연락되었기 때문에 로컬 엔티티는 목록에서 특정 연락처를 확인합니다.

   ![](assets/mkg_dist_use_case_target_valid10.png)

검사가 승인되면 캠페인이 자동으로 시작될 수 있습니다.

### 중앙 엔티티 쪽 {#central-entity-side}

#### 데이터 배포 활동 만들기 {#creating-a-data-distribution-activity}

1. 공동 작업 캠페인을 설정하려면(타겟 승인을 통해) 먼저 **[!UICONTROL Data distribution activity]**&#x200B;을(를) 만들어야 합니다. **[!UICONTROL Resources > Campaign management > Data distribution]** 노드에서 **[!UICONTROL New]** 아이콘을 클릭합니다.

   ![](assets/mkg_dist_use_case_target_valid3.png)

1. **[!UICONTROL General]** 탭에서 다음을 지정해야 합니다.

   * **[!UICONTROL Targeting dimension]**. 여기서 **데이터 배포**&#x200B;는 **수신자**&#x200B;에서 수행됩니다.
   * **[!UICONTROL Distribution type]**. **고정 크기** 또는 **크기(%**)를 선택할 수 있습니다.
   * **[!UICONTROL Assignment type]**. **로컬 엔티티** 옵션을 선택합니다.
   * **[!UICONTROL Distribution type]**. 여기에서 연락처와 로컬 엔티티 사이의 관계를 식별할 수 있는 **[!UICONTROL Origin (@origin)]** 필드가 수신자 테이블에 표시됩니다.
   * **[!UICONTROL Approval storage]** 필드. **수신자** 로컬 승인 옵션을 선택합니다.

1. **[!UICONTROL Breakdown]** 탭에서 다음을 지정합니다.

   * 예정된 캠페인에 관련된 로컬 개체에 해당하는 **[!UICONTROL Distribution field value]**.
   * 로컬 엔티티 **[!UICONTROL label]**.
   * **[!UICONTROL Size]**(고정 또는 백분율로 고정). **0 기본값**&#x200B;은 로컬 엔터티에 연결된 모든 받는 사람을 선택하는 것을 포함합니다.

   ![](assets/mkg_dist_use_case_target_valid4.png)

1. 새로운 데이터 배포를 저장합니다.

#### 공동 작업 캠페인 만들기 {#creating-a-collaborative-campaign}

1. **[!UICONTROL Campaign management > Campaign]** 노드에서 새 **[!UICONTROL collaborative campaign (by target approval)]**&#x200B;을 만듭니다.
1. **[!UICONTROL Targeting and workflows]** 탭에서 캠페인에 대한 워크플로우를 만듭니다. **[!UICONTROL Data distribution]** 활동에 의해 **[!UICONTROL Record count limitation]**&#x200B;이(가) 정의된 **분할** 활동이 포함되어야 합니다.

   ![](assets/mkg_dist_use_case_target_valid5.png)

1. 다음을 지정할 수 있는 **[!UICONTROL Local approval]** 작업을 추가합니다.

   * 알림에서 로컬 엔티티에 전송될 메시지 내용,
   * 승인 알림
   * 캠페인의 예상 처리.

   ![](assets/mkg_dist_use_case_target_valid7.png)

1. 기록을 저장합니다.

#### 캠페인 {#publishing-the-campaign} 게시

이제 **캠페인** 우주에서 **캠페인 패키지**&#x200B;을 추가할 수 있습니다.

1. **[!UICONTROL Reference campaign]**&#x200B;을 선택합니다. 패키지의 **[!UICONTROL Edit]** 탭에서 캠페인에 사용할 **[!UICONTROL Approval mode]**&#x200B;을 선택할 수 있습니다.

   * **수동** 모드에서 로컬 엔티티가 중앙 엔티티로부터 초대를 수락하면 캠페인에 참여합니다. 캠페인의 참여를 확인하기 위해 미리 선택한 연락처를 삭제하고 관리자의 승인이 필요한 경우 삭제할 수 있습니다.
   * **자동** 모드에서 로컬 엔티티가 캠페인에서 자신을 등록 취소하지 않는 한 캠페인에 참여해야 합니다. 승인하지 않아도 연락처를 삭제할 수 있습니다.

   ![](assets/mkg_dist_use_case_target_valid.png)

1. **[!UICONTROL Description]** 탭에서 캠페인에 대한 설명뿐만 아니라 로컬 엔티티에 보낼 문서를 추가할 수 있습니다.

   ![](assets/mkg_dist_use_case_target_valid1.png)

1. 캠페인 패키지를 승인한 후 패키지를 게시하고 패키지 목록에 있는 모든 로컬 엔티티에서 사용할 수 있도록 하는 워크플로우를 시작합니다.

   ![](assets/mkg_dist_use_case_target_valid2.png)

## 협업 캠페인 만들기(양식 기준) {#creating-a-collaborative-campaign--by-form-}

### 소개 {#introduction-1}

여러분은 미국 전역에 온라인 스토어와 여러 부티크가 있는 대형 화장품 브랜드의 마케팅 매니저입니다. 겨울 재고를 언로드하고 새 재고를 위한 공간을 확보하려면 다음 두 가지 클라이언트 카테고리를 대상으로 하는 특별 오퍼를 만듭니다.나이가 들수록 민감한 피부 관리 제품을 제공할 30대 이상, 그리고 더 기본적인 피부 관리 제품을 제공할 30대 이하의 사람들을 위한 것입니다.

따라서 Distributed Marketing을 사용하여 연령 범위별로 서로 다른 스토어에서 클라이언트를 선택할 수 있도록 해주는 형태별로 협업 캠페인을 생성하기로 합니다. 이러한 클라이언트는 연령 범위에 따라 개인화된 특별 오퍼가 포함된 이메일을 수신하게 됩니다.

이 예제의 첫 번째 부분에서는 캠페인 만들기 알림을 받는 로컬 엔티티와 캠페인을 평가하고 순서를 지정하는 데 사용할 수 있는 방법을 보여 줍니다.

이 예제의 두 번째 부분에서는 캠페인을 만드는 방법을 설명합니다.

이 단계는 다음과 같습니다.

**로컬 엔티티의 경우**

1. 캠페인 만들기 알림을 사용하여 온라인 양식에 액세스합니다.
1. 캠페인(타겟, 컨텐츠, 전달 볼륨)을 개인화합니다.
1. 이러한 필드를 확인하고 필요한 경우 변경합니다.
1. 기여도를 승인합니다.
1. 로컬 엔티티(또는 중앙 엔티티)의 관리자가 구성 및 참여를 승인합니다.

**중앙 엔티티의 경우:**

1. 협업 캠페인을 만듭니다.
1. 로컬 캠페인에서와 마찬가지로 **[!UICONTROL Advanced campaign settings...]**&#x200B;을 구성합니다.
1. 로컬 캠페인에서와 마찬가지로 캠페인 워크플로우와 배달을 구성합니다.
1. 웹 양식을 업데이트합니다.
1. 캠페인 패키지를 만들고 게시합니다.

### 로컬 엔티티 측면 {#local-entity-side-1}

1. 캠페인에 참여하도록 선택한 로컬 엔티티는 캠페인에 참여한다는 내용의 이메일 알림을 받습니다.

   ![](assets/mkg_dist_use_case_form_7.png)

1. 로컬 엔티티는 맞춤형 양식을 작성한 다음 다음을 수행합니다.

   * 목표 및 예산을 평가하고
   * 전달 컨텐츠를 미리 보고
   * 참여에 대한 승인을 참조하십시오.

      ![](assets/mkg_dist_use_case_form_8.png)

1. 주문 유효성 확인을 담당하는 연산자가 해당 참가를 승인합니다.

   ![](assets/mkg_dist_use_case_form_9.png)

### 중앙 엔티티 쪽 {#central-entity-side-1}

1. 협업 캠페인을 구현하려면(폼 기준) **협업 캠페인(양식)** 템플릿을 사용하여 캠페인을 만들어야 합니다.

   ![](assets/mkg_dist_use_case_form_1.png)

1. 캠페인의 **[!UICONTROL Edit]** 탭에서 **[!UICONTROL Advanced campaign settings...]** 링크를 클릭하여 로컬 캠페인으로 구성합니다. [로컬 캠페인 만들기(양식)](#creating-a-local-campaign--by-form-)를 참조하십시오.

   ![](assets/mkg_dist_use_case_form_2.png)

1. 캠페인 워크플로우와 웹 양식을 구성합니다. [로컬 캠페인 만들기(양식)](#creating-a-local-campaign--by-form-)를 참조하십시오.
1. 실행 일정 및 관련 로컬 엔티티를 지정하여 캠페인 패키지를 만듭니다.

   ![](assets/mkg_dist_use_case_form_3.png)

1. **[!UICONTROL Edit]** 탭에서 승인 모드를 선택하여 패키지 구성을 완료합니다.

   ![](assets/mkg_dist_use_case_form_4.png)

1. **[!UICONTROL Description]** 탭에서 캠페인 패키지 설명, 패키지가 게시될 때 로컬 엔티티에 전송될 알림 메시지를 입력하고 캠페인 패키지에 유용한 문서를 첨부할 수 있습니다.

   ![](assets/mkg_dist_use_case_form_5.png)

1. 게시할 패키지를 승인합니다.

   ![](assets/mkg_dist_use_case_form_6.png)

