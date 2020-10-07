---
title: 공동 작업 캠페인 만들기
seo-title: 공동 작업 캠페인 만들기
description: 공동 작업 캠페인 만들기
seo-description: null
page-status-flag: never-activated
uuid: 13d8ff65-1480-422a-85b6-40b553a3c151
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: distributed-marketing
discoiquuid: 01d8be92-7312-4386-b5f5-651af31308f7
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '916'
ht-degree: 4%

---


# 공동 작업 캠페인 만들기{#creating-a-collaborative-campaign-intro}

중앙 엔터티는 분산 마케팅 캠페인 템플릿에서 **공동 캠페인을** 만듭니다. [이 페이지](../../campaign/using/about-distributed-marketing.md#collaborative-campaign)를 참조하십시오.

## 공동 작업 캠페인 만들기 {#creating-a-collaborative-campaign}

공동 작업 캠페인을 구성하려면 노드를 클릭한 다음 **[!UICONTROL Campaign management > Campaigns]** **[!UICONTROL New]** 아이콘을 클릭합니다.

>[!NOTE]
>
>또한 웹 인터페이스 **[!UICONTROL collaborative campaigns (by campaign)]**&#x200B;를 통해 이러한 캠페인을 구성하고 실행할 수 있습니다.

공동 작업 캠페인 데이터베이스의 구성 프로세스는 로컬 캠페인 템플릿의 구성 프로세스와 유사합니다. 서로 다른 협업 캠페인 유형의 사양은 아래에 자세히 설명되어 있습니다.

### 양식별 {#by-form}

양식에서 협업 캠페인을 만들려면 템플릿을 선택해야 **[!UICONTROL Collaborative campaign (by form)]** 합니다.

![](assets/mkg_dist_mutual_op_form2.png)

탭에서 **[!UICONTROL Edit]** 링크를 클릭하여 **[!UICONTROL Advanced campaign settings...]** 분산 마케팅 **** 탭에 액세스합니다.

양식 **웹 인터페이스별로** 선택합니다. 이 유형의 인터페이스를 사용하면 캠페인을 정렬할 때 로컬 엔티티에서 사용할 개인화 필드를 만들 수 있습니다. 로컬 캠페인 [만들기(양식별)를 참조하십시오](../../campaign/using/examples.md#creating-a-local-campaign--by-form-).

캠페인을 저장합니다. 이제 **캠페인** 우주의 **캠페인 패키지** 보기에서 **[!UICONTROL Create]** 단추를 클릭하여사용할 수있습니다.

서로 다른 조직 개체에 대한 캠페인을 만들기 위해 기본 또는 중복 캠페인 템플릿과 공동 캠페인에 대한 참조 캠페인을 함께 사용할 수 있는 보기입니다. **[!UICONTROL Campaign Package]**

![](assets/mkg_dist_mutual_op_form1b.png)

### 캠페인별 {#by-campaign}

협업 캠페인(캠페인별)을 만들려면 템플릿을 **[!UICONTROL Collaborative campaign (by campaign) (opCollaborativeByCampaign)]** 선택해야 합니다.

![](assets/mkg_dist_mutual_op_by_op2.png)

캠페인 순서를 지정할 때 로컬 엔티티는 중앙 엔티티에 의해 사전 정의된 기준을 완료하고 캠페인을 정렬하기 전에 평가할 수 있습니다.

중앙 엔티티에서 **협업 캠페인(캠페인별)** 주문이 승인되면 로컬 엔티티에 대해 하위 캠페인이 생성됩니다. 로컬 엔티티가 다음 사항을 수정할 수 있습니다.

* 캠페인 워크플로우,
* 유형 분류 규칙,
* 개인화 필드

로컬 엔티티가 하위 캠페인을 실행합니다. 중앙 엔티티는 상위 캠페인을 실행합니다.

중앙 엔터티는 이 대시보드(링크를 통해)에서 **공동 작업 캠페인(캠페인별)** 에 연결된 모든 하위 캠페인을 **[!UICONTROL List of associated campaigns]** 볼 수 있습니다.

![](assets/mkg_dist_mutual_op_by_op.png)

### 대상 승인별 {#by-target-approval}

공동 작업 캠페인을 만들려면(대상 승인별) 템플릿을 **[!UICONTROL Collaborative campaign (by target approval)]** 선택해야 합니다.

![](assets/mkg_dist_mutual_op_by_valid.png)

>[!NOTE]
>
>이 모드에서는 중앙 엔티티가 로컬 엔티티를 지정할 필요가 없습니다.

캠페인 워크플로우는 **로컬 승인** 유형 활동을 통합해야 합니다. 활동 매개 변수는 다음과 같습니다.

* **[!UICONTROL Action to perform]** :Target 승인 알림.
* **[!UICONTROL Distribution context]** :명시적.
* **[!UICONTROL Data distribution]** :로컬 엔티티 배포.

**로컬 엔티티 배포** 유형 데이터 배포를 만들어야 합니다. 데이터 배포 템플릿을 사용하면 그룹화 값 목록에서 레코드 수를 제한할 수 있습니다. 에서 **[!UICONTROL Resources > Campaign management > Data distribution]**&#x200B;아이콘을 **[!UICONTROL New]** 클릭하여 새 아이콘을 만듭니다 **[!UICONTROL Data distribution]**. 데이터 배포에 대한 자세한 내용은 워크플로우 [안내서를](../../workflow/using/using-the-local-approval-activity.md#step-1--creating-the-data-distribution-template-) 참조하십시오.

![](assets/mkg_dist_data_distribution.png)

Select the **Targeting dimension** and the **[!UICONTROL Distribution field]**. 에 대해 **[!UICONTROL Assignment type]**&#x200B;로컬 엔티티 **를 선택합니다**.

탭에서 **[!UICONTROL Distribution]** 각 로컬 엔티티에 대한 필드를 추가하고 값을 지정합니다.

![](assets/mkg_dist_data_distribution2.png)

배달 유형 활동 후 두 번째 **Target** 승인을 **추가하여** 보고서를 구성할 수 있습니다.

캠페인 만들기 알림 메시지에서 로컬 엔티티는 중앙 엔티티 매개 변수에 의해 사전 정의된 연락처 목록을 받습니다.

![](assets/mkg_dist_mutual_op_by_valid1.png)

로컬 엔터티는 캠페인 컨텐츠를 기반으로 특정 연락처를 삭제할 수 있습니다.

![](assets/mkg_dist_mutual_op_by_valid2.png)

### 단순 {#simple}

간단한 공동 작업 캠페인을 만들려면 템플릿을 선택해야 **[!UICONTROL Collaborative campaign (simple)]** 합니다.

## Creating a collaborative campaign package {#creating-a-collaborative-campaign-package}

로컬 엔티티에서 캠페인을 사용할 수 있게 하려면 중앙 엔티티가 캠페인 패키지를 생성해야 합니다.

다음 단계를 적용합니다.

1. 캠페인 **[!UICONTROL Navigation]** 페이지의 **섹션에서** **[!UICONTROL Campaign packages]** 링크를 클릭합니다.
1. **[!UICONTROL Create]** 버튼을 클릭합니다.
1. 창 상단의 섹션에서 템플릿을 선택할 수 **[!UICONTROL New collaborative package (mutualizedEmpty)]** 있습니다.
1. 참조 캠페인을 선택합니다.
1. 캠페인 패키지의 레이블, 폴더 및 실행 일정을 지정합니다.

### 날짜 {#dates}

시작 및 종료 날짜는 캠페인 패키지 목록에서 캠페인의 가시성 기간을 정의합니다.

공동 **캠페인의 경우**&#x200B;중앙 엔티티는 등록 및 개인화 마감일을 지정해야 합니다.

>[!NOTE]
>
>캠페인 구성에 사용할 문서(스프레드시트, 이미지)를 로컬 엔티티가 배달해야 하는 기한을 중앙 엔티티에서 선택할 수 **[!UICONTROL Personalization deadline]** 있도록 해줍니다. 이것은 필수 옵션이 아닙니다. 이 날짜를 사이드 단계 지정해도 캠페인 구현에 영향을 주지 않습니다.

![](assets/s_advuser_mkg_dist_create_mutual_entry.png)

### 대상자 {#audience}

중앙 엔터티는 공동 작업 캠페인을 만드는 즉시 캠페인별로 관련된 로컬 개체를 지정해야 합니다.

![](assets/s_advuser_mkg_dist_create_mutual_entry2.png)

>[!CAUTION]
>
>**[!UICONTROL Simple, by form and by campaign collaborative campaign kits]** 관련 로컬 개체를 지정하지 않으면 승인할 수 없습니다.

### 승인 모드 {#approval-modes}

협업 **캠페인의**&#x200B;경우 주문 승인 모드를 지정할 수 있습니다.

![](assets/mkg_dist_edit_kit1.png)

수동 모드에서 로컬 엔티티가 참여하려면 캠페인에 가입해야 합니다.

자동 모드에서는 로컬 엔티티가 캠페인에 사전 구독됩니다. 중앙 엔티티의 승인 없이 캠페인 가입을 취소하거나 매개 변수를 수정할 수 있습니다.

![](assets/mkg_dist_edit_kit2.png)

### 알림 {#notifications}

알림에 대한 구성은 로컬 엔티티에 대한 알림과 동일합니다. [이 섹션](../../campaign/using/creating-a-local-campaign.md#notifications)을 참조하십시오.

## 캠페인 순서 지정 {#ordering-a-campaign}

협업 캠페인이 캠페인 패키지 목록에 추가되면 중앙 엔티티에 의해 정의된 대상에 속하는 로컬 개체에 알림이 표시됩니다( **공동 캠페인(대상 승인 기준)** 에는 사전 정의된 대상이 없습니다.). 전송된 메시지에는 아래와 같이 캠페인에 등록할 수 있는 링크가 포함되어 있습니다.

![](assets/mkg_dist_mutual_op_notification.png)

또한 이 메시지를 사용하면 로컬 개체가 패키지를 만든 중앙 연산자가 입력한 설명과 캠페인에 연결된 문서를 볼 수 있습니다. 이러한 지표는 캠페인 자체에 속하지 않지만 캠페인 자체에 속하지 않습니다.

로컬 운영자가 웹 인터페이스를 통해 로그온하면 주문하려는 공동 작업 캠페인에 개인화된 정보를 입력할 수 있습니다.

![](assets/mkg_dist_mutual_op_command.png)

로컬 엔티티가 등록을 완료하면 중앙 엔티티에 주문을 승인하는 이메일 알림을 받게 됩니다.

![](assets/mkg_dist_mutual_op_valid_command.png)

For more on this, refer to the [Approval process](../../campaign/using/creating-a-local-campaign.md#approval-process) section.

## 주문 승인 {#approving-an-order}

협업 캠페인 패키지 순서를 승인하는 프로세스는 로컬 캠페인에 대해 승인하는 경우와 동일합니다. [이 섹션](../../campaign/using/creating-a-local-campaign.md#approving-an-order)을 참조하십시오.
