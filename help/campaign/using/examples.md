---
product: campaign
title: 예제
description: 예제
audience: campaign
content-type: reference
topic-tags: distributed-marketing
exl-id: 2bef6b5e-887e-4c56-bb4b-3583472ca333
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1296'
ht-degree: 0%

---

# 예제{#examples}

## 로컬 캠페인 만들기(양식 기준) {#creating-a-local-campaign--by-form-}

**By form** 형식 웹 인터페이스에는 **웹 응용 프로그램**&#x200B;을 사용하는 작업이 포함됩니다. 구성에 따라 이 웹 애플리케이션에는 정의된 개인화된 요소의 유형이 포함될 수 있습니다. 예를 들어 대상, 예산, 콘텐츠 등을 평가하는 링크를 제안할 수 있습니다. 전용 API를 통해

>[!NOTE]
>
>API는 계약에 따라 액세스 권한이 부여된 전용 문서에 자세히 설명되어 있습니다. [API](../../configuration/using/about-web-services.md)를 참조하십시오.
>
>이 예제에 사용되는 웹 애플리케이션은 Adobe Campaign을 통해 기본적으로 제공되는 웹 앱이 아닙니다. 캠페인에서 양식을 사용하려면 전용 웹 애플리케이션을 만들어야 합니다.

캠페인 템플릿을 만들 때 **[!UICONTROL Advanced campaign settings...]** 링크의 **[!UICONTROL Web interface]** 옵션 내에서 **[!UICONTROL Zoom]** 아이콘을 클릭하여 웹 애플리케이션의 세부 정보에 액세스합니다.

![](assets/mkg_dist_local_op_form1.png)

>[!NOTE]
>
>웹 애플리케이션 매개 변수는 캠페인 템플릿에서만 사용할 수 있습니다.

**[!UICONTROL Edit]** 탭에서 **캠페인 순서** 활동을 선택하고 이를 열어 해당 콘텐츠에 액세스합니다.

![](assets/mkg_dist_web_app1.png)

이 예에서 **캠페인 순서** 활동에는 다음이 포함됩니다.

* 주문 중에 로컬 엔티티가 입력할 필드

   ![](assets/mkg_dist_web_app2.png)

* 로컬 엔티티가 캠페인을 평가할 수 있도록 해주는 링크(예: 대상, 예산, 콘텐츠 등),

   ![](assets/mkg_dist_web_app3.png)

* 이러한 평가의 결과를 계산하고 표시할 수 있는 스크립트입니다.

   ![](assets/mkg_dist_web_app4.png)

이 예에서는 다음 API가 사용됩니다.

* 타겟 평가를 위해

   ```
   var res = nms.localOrder.EvaluateTarget(ctx.localOrder);
   ```

* 예산 평가를 위해

   ```
   var res = nms.localOrder.EvaluateDeliveryBudget(ctx.@deliveryId, NL.XTK.parseNumber(ctx.@compt));
   ```

* 컨텐츠 평가를 위해

   ```
   var res = nms.localOrder.EvaluateContent(ctx.localOrder, ctx.@deliveryId, "html", resSeed.@id);
   ```

## 공동 작업 캠페인 만들기(대상 승인) {#creating-a-collaborative-campaign--by-target-approval-}

### 소개 {#introduction}

당신은 미국 전역에 온라인 매장과 여러 부티크가 있는 대형 의류 브랜드의 마케팅 매니저입니다. 봄이 온 지금, 당신은 최고의 고객에게 당신의 카탈로그의 모든 드레스를 50퍼센트 할인해주는 특별 제안을 만들기로 결심한다.

이 오퍼는 연초 이후 300달러 이상을 소비한 미국 상점 최고의 고객을 대상으로 합니다.

따라서 특별 오퍼가 포함된 이메일 배달을 받을 스토어의 우수 고객(지역별 그룹화된)을 선택할 수 있는 협업 캠페인(타겟 승인별)을 만들기 위해 분산 마케팅을 사용하도록 결정합니다.

이 예제의 첫 번째 부분에서는 캠페인 만들기 알림을 받는 로컬 엔티티와 캠페인 만들기 알림을 사용하여 캠페인을 평가하고 순서를 지정하는 방법을 보여줍니다.

이 예제의 두 번째 부분에서는 캠페인을 만드는 방법을 설명합니다.

단계는 다음과 같습니다.

**로컬 엔티티에 대해**

1. 캠페인 만들기 알림을 사용하여 중앙 엔티티가 선택한 연락처 목록에 액세스합니다.
1. 연락처를 선택하고 기여도를 승인합니다.

**중앙 엔티티의 경우:**

1. **[!UICONTROL Data distribution]** 활동을 만듭니다.
1. 공동 작업 캠페인을 만듭니다.
1. 캠페인을 게시합니다.

### 로컬 엔터티 측 {#local-entity-side}

1. 캠페인에 참여하도록 선택한 로컬 엔티티는 이메일 알림을 받게 됩니다.

   ![](assets/mkg_dist_use_case_target_valid8.png)

1. **[!UICONTROL Access your contact list and approve targeting]** 링크를 클릭하면 로컬 엔티티에 웹 브라우저를 통해 캠페인에 대해 선택한 클라이언트 목록에 액세스할 수 있습니다.

   ![](assets/mkg_dist_use_case_target_valid9.png)

1. 해당 지역 엔티티는 연초부터 이미 유사한 오퍼에 접촉하여 목록에서 특정 연락처를 확인 해제합니다.

   ![](assets/mkg_dist_use_case_target_valid10.png)

확인이 승인되면 캠페인이 자동으로 시작될 수 있습니다.

### 중앙 엔터티 측 {#central-entity-side}

#### 데이터 배포 활동 만들기 {#creating-a-data-distribution-activity}

1. 공동 작업 캠페인을 설정하려면(대상 승인을 통해) 먼저 **[!UICONTROL Data distribution activity]**&#x200B;을 만들어야 합니다. **[!UICONTROL Resources > Campaign management > Data distribution]** 노드에서 **[!UICONTROL New]** 아이콘을 클릭합니다.

   ![](assets/mkg_dist_use_case_target_valid3.png)

1. **[!UICONTROL General]** 탭에서 다음을 지정해야 합니다.

   * **[!UICONTROL Targeting dimension]** 여기서 **데이터 배포**&#x200B;는 **수신자**&#x200B;에서 수행됩니다.
   * **[!UICONTROL Distribution type]** **고정 크기** 또는 **크기를 백분율**&#x200B;로 선택할 수 있습니다.
   * **[!UICONTROL Assignment type]** **로컬 엔티티** 옵션을 선택합니다.
   * **[!UICONTROL Distribution type]** 여기에서 연락처와 로컬 엔티티 간의 관계를 식별할 수 있는 **[!UICONTROL Origin (@origin)]** 필드가 수신자 테이블에 표시됩니다.
   * **[!UICONTROL Approval storage]** 필드. **수신자의 로컬 승인** 옵션을 선택합니다.

1. **[!UICONTROL Breakdown]** 탭에서 다음을 지정합니다.

   * 예정된 캠페인에 포함된 로컬 엔티티에 해당하는 **[!UICONTROL Distribution field value]**.
   * 로컬 엔터티 **[!UICONTROL label]**&#x200B;입니다.
   * **[!UICONTROL Size]**(고정 또는 백분율로) **0 기본값**&#x200B;에는 로컬 엔터티에 연결된 모든 수신자를 선택하는 작업이 포함됩니다.

   ![](assets/mkg_dist_use_case_target_valid4.png)

1. 새 데이터 배포를 저장합니다.

#### 공동 작업 캠페인 만들기 {#creating-a-collaborative-campaign}

1. **[!UICONTROL Campaign management > Campaign]** 노드에서 새 **[!UICONTROL collaborative campaign (by target approval)]**&#x200B;을 만듭니다.
1. **[!UICONTROL Targeting and workflows]** 탭에서 캠페인에 대한 워크플로우를 만듭니다. 여기에는 **[!UICONTROL Data distribution]** 활동에 의해 **[!UICONTROL Record count limitation]**&#x200B;가 정의된 **Split** 활동이 포함되어야 합니다.

   ![](assets/mkg_dist_use_case_target_valid5.png)

1. 지정할 수 있는 **[!UICONTROL Local approval]** 작업을 추가합니다.

   * 알림에서 로컬 엔티티로 전송할 메시지 콘텐츠,
   * 승인 알림
   * 캠페인의 예상 처리.

   ![](assets/mkg_dist_use_case_target_valid7.png)

1. 레코드를 저장합니다.

#### 캠페인 {#publishing-the-campaign} 게시

이제 **[!UICONTROL Campaigns]** 탭에서 **캠페인 패키지**&#x200B;를 추가할 수 있습니다.

1. **[!UICONTROL Reference campaign]**&#x200B;을(를) 선택합니다. 패키지의 **[!UICONTROL Edit]** 탭에서 캠페인에 사용할 **[!UICONTROL Approval mode]**&#x200B;을(를) 선택할 수 있습니다.

   * **수동** 모드에서 로컬 엔티티가 중앙 엔티티의 초대를 수락하면 캠페인에 참여합니다. 사전 선택된 연락처가 캠페인의 참여를 확인하기 위해 필요한 경우 삭제하고 관리자의 승인이 필요한 경우 삭제할 수 있습니다.
   * **자동** 모드에서 로컬 엔티티는 자체등록을 취소하지 않는 한 캠페인에 참여해야 합니다. 승인이 필요 없이 연락처를 삭제할 수 있습니다.

   ![](assets/mkg_dist_use_case_target_valid.png)

1. **[!UICONTROL Description]** 탭에서 캠페인에 대한 설명과 로컬 엔티티로 전송할 문서를 추가할 수 있습니다.

   ![](assets/mkg_dist_use_case_target_valid1.png)

1. 캠페인 패키지를 승인한 다음 워크플로우를 시작하여 패키지를 게시하고 패키지 목록의 모든 로컬 엔티티가 사용할 수 있도록 합니다.

   ![](assets/mkg_dist_use_case_target_valid2.png)

## 공동 작업 캠페인 만들기(양식 기준) {#creating-a-collaborative-campaign--by-form-}

### 소개 {#introduction-1}

여러분은 미국 전역에 온라인 가게와 몇 개의 부티크가 있는 큰 화장 브랜드의 마케팅 매니저입니다. 겨울 스톡을 언로드하고 새 주식을 위한 공간을 만들려면 두 가지 클라이언트 카테고리를 대상으로 하는 특별 오퍼를 생성하기로 합니다.나이 들어갈 수록 민감한 피부관리 제품과 30대 미만은 기본이다.

따라서 나이 범위별로 서로 다른 저장소에서 클라이언트를 선택할 수 있는 공동 작업 캠페인(양식 기준)을 만들기 위해 분산 마케팅을 사용하도록 결정합니다. 이러한 고객은 연령 범위에 따라 개인화된 특별 오퍼와 함께 이메일 배달을 받게 됩니다.

이 예제의 첫 번째 부분에서는 캠페인 만들기 알림을 받는 로컬 엔티티와 캠페인 만들기 알림을 사용하여 캠페인을 평가하고 순서를 지정하는 방법을 보여줍니다.

이 예제의 두 번째 부분에서는 캠페인을 만드는 방법을 설명합니다.

단계는 다음과 같습니다.

**로컬 엔티티에 대해**

1. 캠페인 만들기 알림을 사용하여 온라인 양식에 액세스합니다.
1. 캠페인(target, 콘텐츠, 게재 볼륨)을 개인화합니다.
1. 이러한 필드를 확인하고 필요한 경우 변경합니다.
1. 기여도를 승인합니다.
1. 로컬 엔티티(또는 중앙 엔티티)의 관리자가 구성 및 기여도를 승인합니다.

**중앙 엔티티의 경우:**

1. 공동 작업 캠페인을 만듭니다.
1. 로컬 캠페인에 대해 하듯이 **[!UICONTROL Advanced campaign settings...]**&#x200B;을 구성합니다.
1. 로컬 캠페인에 대해 하듯이 캠페인 워크플로우와 게재를 구성합니다.
1. 웹 양식을 업데이트합니다.
1. 캠페인 패키지를 만들고 게시합니다.

### 로컬 엔터티 측 {#local-entity-side-1}

1. 캠페인에 참여하도록 선택한 로컬 엔티티는 캠페인에 참여했음을 알리는 이메일 알림을 받습니다.

   ![](assets/mkg_dist_use_case_form_7.png)

1. 로컬 엔티티는 개인화된 양식을 완료한 다음 다음과 같습니다.

   * 목표물과 예산을 평가하고
   * 게재 콘텐츠 미리 보기,
   * 기여도를 승인합니다.

      ![](assets/mkg_dist_use_case_form_8.png)

1. 주문 유효성 검사를 담당하는 연산자가 참가 승인을 합니다.

   ![](assets/mkg_dist_use_case_form_9.png)

### 중앙 엔터티 측 {#central-entity-side-1}

1. 공동 작업 캠페인을 구현하려면(양식 기준) **공동 작업 캠페인(양식)** 템플릿을 사용하여 캠페인을 만들어야 합니다.

   ![](assets/mkg_dist_use_case_form_1.png)

1. 캠페인의 **[!UICONTROL Edit]** 탭에서 **[!UICONTROL Advanced campaign settings...]** 링크를 클릭하여 로컬 캠페인으로 구성합니다. [로컬 캠페인 만들기(양식 기준)](#creating-a-local-campaign--by-form-)를 참조하십시오.

   ![](assets/mkg_dist_use_case_form_2.png)

1. 캠페인 워크플로우와 웹 양식을 구성합니다. [로컬 캠페인 만들기(양식 기준)](#creating-a-local-campaign--by-form-)를 참조하십시오.
1. 실행 일정 및 관련 로컬 엔티티를 지정하여 캠페인 패키지를 만듭니다.

   ![](assets/mkg_dist_use_case_form_3.png)

1. **[!UICONTROL Edit]** 탭에서 승인 모드를 선택하여 패키지 구성을 완료합니다.

   ![](assets/mkg_dist_use_case_form_4.png)

1. **[!UICONTROL Description]** 탭에서 캠페인 패키지 설명, 패키지를 게시할 때 로컬 엔티티로 전송할 알림 메시지를 입력하고 모든 유용한 문서를 캠페인 패키지에 첨부할 수 있습니다.

   ![](assets/mkg_dist_use_case_form_5.png)

1. 패키지를 승인하여 게시합니다.

   ![](assets/mkg_dist_use_case_form_6.png)
