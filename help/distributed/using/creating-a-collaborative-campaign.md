---
product: campaign
title: 공동 캠페인 만들기
description: 공동 작업 캠페인을 만드는 방법을 알아봅니다
feature: Distributed Marketing
exl-id: 17313fe5-ad42-45ca-a35a-1e7aa89380ef
source-git-commit: d36e1881726af6238c4e0caecb7b299b594691f2
workflow-type: tm+mt
source-wordcount: '915'
ht-degree: 3%

---

# 공동 캠페인 만들기{#creating-a-collaborative-campaign-intro}

![](../../assets/common.svg)

중앙 엔티티는 **분산 마케팅** 캠페인 템플릿. [이 페이지](about-distributed-marketing.md#collaborative-campaign)를 참조하십시오.

## 공동 캠페인 만들기 {#creating-a-collaborative-campaign}

공동 작업 캠페인을 구성하려면 **[!UICONTROL Campaign management > Campaigns]** 노드, **[!UICONTROL New]** 아이콘.

>[!NOTE]
>
>외주 **[!UICONTROL collaborative campaigns (by campaign)]**, 웹 인터페이스를 통해 이러한 캠페인을 구성하고 실행할 수 있습니다.

공동 작업 캠페인 데이터베이스의 구성 프로세스는 로컬 캠페인 템플릿의 구성 프로세스와 유사합니다. 다양한 유형의 공동 작업 캠페인에 대한 사양은 아래에 자세히 설명되어 있습니다.

### 양식 기준 {#by-form}

협업 캠페인을 만들기 위한(양식 기준) **[!UICONTROL Collaborative campaign (by form)]** 템플릿을 선택해야 합니다.

![](assets/mkg_dist_mutual_op_form2.png)

에서 **[!UICONTROL Edit]** 탭에서 **[!UICONTROL Advanced campaign settings...]** 액세스 링크 **분산 마케팅** 탭.

을(를) 선택합니다 **양식 기준** 웹 인터페이스. 이 유형의 인터페이스를 사용하면 캠페인을 정렬할 때 로컬 엔티티가 사용할 개인화 필드를 만들 수 있습니다. 을(를) 참조하십시오. [로컬 캠페인 만들기(양식 기준)](examples.md#creating-a-local-campaign--by-form-).

캠페인을 저장합니다. 이제 다음 위치에서 사용할 수 있습니다. **Campaign 패키지** 에서 보기 **캠페인** 탭을 클릭하여 **[!UICONTROL Create]** 버튼을 클릭합니다.

다음 **[!UICONTROL Campaign Package]** 보기를 사용하면 다른 조직 엔터티를 위한 캠페인을 만들기 위해 로컬 캠페인 템플릿(기본 제공 또는 중복된)과 공동 작업 캠페인을 위한 참조 캠페인을 사용할 수 있습니다.

![](assets/mkg_dist_mutual_op_form1b.png)

### 캠페인별 {#by-campaign}

공동 작업 캠페인(캠페인별)을 만들려면 **[!UICONTROL Collaborative campaign (by campaign) (opCollaborativeByCampaign)]** 템플릿을 선택해야 합니다.

![](assets/mkg_dist_mutual_op_by_op2.png)

캠페인 순서를 지정할 때 로컬 엔티티는 중앙 엔티티에 의해 사전 정의된 기준을 완료하고 캠페인을 정렬하기 전에 평가할 수 있습니다.

주문 **공동 작업 캠페인(캠페인별)** 중앙 엔티티가 승인하면 로컬 엔티티에 대해 하위 캠페인이 만들어집니다. 로컬 엔티티가 사용 가능하면 다음을 수정할 수 있습니다.

* 캠페인 워크플로우,
* 유형화 규칙,
* 및 개인화 필드.

로컬 엔티티는 하위 캠페인을 실행합니다. 중앙 엔티티는 상위 캠페인을 실행합니다.

중앙 엔티티는 **공동 작업 캠페인(캠페인별)** 이 대시보드에서 **[!UICONTROL List of associated campaigns]** 링크를 클릭합니다.

![](assets/mkg_dist_mutual_op_by_op.png)

### 대상 승인별 {#by-target-approval}

공동 작업 캠페인을 만들려면(대상 승인을 통해) **[!UICONTROL Collaborative campaign (by target approval)]** 템플릿을 선택해야 합니다.

![](assets/mkg_dist_mutual_op_by_valid.png)

>[!NOTE]
>
>이 모드에서는 중앙 엔티티가 로컬 엔티티를 지정할 필요가 없습니다.

캠페인 워크플로우를 통합해야 합니다 **로컬 승인** 유형 활동. 활동 매개 변수는 다음과 같습니다.

* **[!UICONTROL Action to perform]** : Target 승인 알림.
* **[!UICONTROL Distribution context]** : 명시적.
* **[!UICONTROL Data distribution]** : 로컬 엔터티 배포입니다.

**로컬 엔터티 배포** 형식 데이터 배포를 만들어야 합니다. 데이터 배포 템플릿을 사용하면 그룹화 값 목록에서 레코드 수를 제한할 수 있습니다. in **[!UICONTROL Resources > Campaign management > Data distribution]**&#x200B;를 클릭하고 **[!UICONTROL New]** 아이콘을 클릭하여 새 만들기 **[!UICONTROL Data distribution]**. 데이터 배포에 대한 자세한 내용은 [워크플로우](../../workflow/using/using-the-local-approval-activity.md#step-1--creating-the-data-distribution-template-) 안내서.

![](assets/mkg_dist_data_distribution.png)

을(를) 선택합니다 **타겟팅 차원** 그리고 **[!UICONTROL Distribution field]**. 대상 **[!UICONTROL Assignment type]**, 선택 **로컬 엔티티**.

에서 **[!UICONTROL Distribution]** 탭에서 각 로컬 엔티티에 대한 필드를 추가하고 값을 지정합니다.

![](assets/mkg_dist_data_distribution2.png)

한 초 추가할 수 있습니다 **Target 승인** 후 **배달** 활동에 대한 보고서를 구성할 활동을 입력합니다.

캠페인 만들기 알림 메시지에서 로컬 엔티티는 중앙 엔티티 매개 변수에 의해 사전 정의된 연락처 목록을 받습니다.

![](assets/mkg_dist_mutual_op_by_valid1.png)

로컬 엔터티는 캠페인 콘텐츠를 기반으로 특정 연락처를 삭제할 수 있습니다.

![](assets/mkg_dist_mutual_op_by_valid2.png)

### 단순 {#simple}

간단한 공동 작업 캠페인을 만들려면 **[!UICONTROL Collaborative campaign (simple)]** 템플릿을 선택해야 합니다.

## 공동 작업 캠페인 패키지 만들기 {#creating-a-collaborative-campaign-package}

로컬 엔티티가 캠페인을 사용할 수 있도록 하려면 중앙 엔티티가 캠페인 패키지를 만들어야 합니다.

다음 단계를 적용합니다.

1. 에서 **[!UICONTROL Navigation]** 섹션에 **캠페인** 페이지에서 **[!UICONTROL Campaign packages]** 링크를 클릭합니다.
1. **[!UICONTROL Create]** 버튼을 클릭합니다.
1. 창 상단의 섹션에서 **[!UICONTROL New collaborative package (mutualizedEmpty)]** 템플릿.
1. 참조 캠페인을 선택합니다.
1. 캠페인 패키지에 대한 레이블, 폴더 및 실행 일정을 지정합니다.

### 날짜 {#dates}

시작 및 종료 날짜는 캠페인 패키지 목록에서 캠페인의 가시성 기간을 정의합니다.

대상 **공동 캠페인**&#x200B;를 지정하는 경우 중앙 엔티티는 등록 및 개인화 마감일을 지정해야 합니다.

>[!NOTE]
>
>다음 **[!UICONTROL Personalization deadline]** 에서는 중앙 엔티티가 캠페인을 구성하는 데 사용할 문서(스프레드시트, 이미지)를 로컬 엔티티가 배달해야 하는 기한을 선택할 수 있습니다. 필수 옵션이 아닙니다. 이 날짜를 side-stepping하면 캠페인 구현에 영향을 주지 않습니다.

![](assets/s_advuser_mkg_dist_create_mutual_entry.png)

### 대상자 {#audience}

중앙 엔티티는 공동 작업 캠페인을 만드는 즉시 캠페인별로 연관된 로컬 엔티티를 지정해야 합니다.

![](assets/s_advuser_mkg_dist_create_mutual_entry2.png)

>[!CAUTION]
>
>**[!UICONTROL Simple, by form and by campaign collaborative campaign kits]** 해당 로컬 엔터티가 지정되지 않은 경우 승인할 수 없습니다.

### 승인 모드 {#approval-modes}

대상 **공동 캠페인**&#x200B;주문 승인 모드를 지정할 수 있습니다.

![](assets/mkg_dist_edit_kit1.png)

수동 모드에서는 로컬 엔티티가 참여하기 위해 캠페인에 가입해야 합니다.

자동 모드에서는 로컬 엔티티가 캠페인에 미리 구독됩니다. 중앙 엔티티의 승인 없이 캠페인 구독을 취소하거나 매개 변수를 수정할 수 있습니다.

![](assets/mkg_dist_edit_kit2.png)

### 알림 을 참조하십시오 {#notifications}

알림에 대한 구성은 로컬 엔티티에 대한 알림과 동일합니다. [이 섹션](creating-a-local-campaign.md#notifications)을 참조하십시오.

## 캠페인 주문 {#ordering-a-campaign}

공동 작업 캠페인이 캠페인 패키지 목록에 추가되면 중앙 엔티티가 정의한 대상에 속하는 로컬 엔티티에 대한 알림이 표시됩니다(ID **협업 캠페인(target 승인별)** 사전 정의된 대상이 없음). 전송된 메시지에는 아래와 같이 캠페인에 등록할 수 있는 링크가 포함되어 있습니다.

![](assets/mkg_dist_mutual_op_notification.png)

또한 이 메시지를 사용하면 로컬 엔티티가 패키지를 만든 중앙 연산자가 입력한 설명과 캠페인에 연결된 문서를 볼 수 있습니다. 이러한 지표는 캠페인에 대한 추가 정보를 제공하지만 캠페인 자체에 속하지 않습니다.

로컬 운영자가 웹 인터페이스를 통해 로그온하면 주문하려는 공동 작업 캠페인에 개인화된 정보를 입력할 수 있습니다.

![](assets/mkg_dist_mutual_op_command.png)

로컬 엔티티가 등록을 완료하면 중앙 엔티티가 전자 메일로 주문을 승인하라는 알림을 받습니다.

![](assets/mkg_dist_mutual_op_valid_command.png)

자세한 내용은 [승인 프로세스](creating-a-local-campaign.md#approval-process) 섹션을 참조하십시오.

## 주문 승인 {#approving-an-order}

공동 작업 캠페인 패키지 순서를 승인하는 프로세스는 로컬 캠페인에 대해 그렇게 할 때와 동일합니다. [이 섹션](creating-a-local-campaign.md#approving-an-order)을 참조하십시오.
