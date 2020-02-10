---
title: 분산 마케팅 정보
seo-title: 분산 마케팅 정보
description: 분산 마케팅 정보
seo-description: null
page-status-flag: never-activated
uuid: 7f7ece67-c644-4072-a06c-c5b49f3acb5d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: distributed-marketing
discoiquuid: 6d694f5c-1d1f-4686-b3bf-8697d919a0c8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b47dcfa0e4ee2e5e43e7aa14b94e12fd70ff9c2d

---


# 분산 마케팅 정보{#about-distributed-marketing}

## 소개 {#introduction}

Adobe Campaign은 **중앙 조직** (본사, 마케팅 부서 등) 간의 협력 캠페인을 구현하는 데 필요한 분산 마케팅 애플리케이션을 제공합니다. 및 해당 지역 업체(판매 지점, 지역 기관 등)와 이러한 협력은 중앙에서 만든 캠페인 템플릿과 인스턴스가 로컬 엔티티에 제공되는 **[!UICONTROL list of campaign packages]**&#x200B;으로 알려진 공유 작업 영역을 기반으로 합니다.

중앙 엔티티는 로컬 엔티티가 사용할 수 있는 캠페인을 제공합니다. 캠페인은 로컬 또는 협업 캠페인을 나타내는 패키지로 구체화됩니다. 캠페인을 사용하려면 로컬 엔티티가 캠페인을 주문해야 하며 주문은 승인되어야 합니다.

>[!CAUTION]
>
>분산 마케팅 모듈은 캠페인 **옵션입니다** . 사용권 계약을 확인하십시오.

## 용어 {#terminology}

### 중앙 엔티티 {#central-entities}

중앙 개체는 커뮤니케이션을 지정하고 해당 지역의 개체가 마케팅 캠페인을 실행할 수 있도록 지원하는 마케팅 운영자로 구성됩니다.

분산 마케팅 모듈에서는 중앙 엔티티가 다음을 수행할 수 있습니다.

* 로컬 개체에 대한 마케팅 캠페인 패키지 설정,
* 고객/잠재 고객 커뮤니케이션, 타깃팅, 컨텐츠 등에서 기업의 선택에 대한 자율성을 높입니다.
* 비용 관리 및 제어
* 기관망을 처리하다.

### 로컬 엔티티 {#local-entities}

지역 실체는 특정 지역 운영자(국가 또는 지역 관리자, 브랜드 관리자 등)의 기관, 스토어 또는 그룹이 될 수 있습니다.

Distributed Marketing을 사용하면 로컬 엔티티는 실행 비용을 최적화하는 동시에 더 많은 자율성을 확보할 수 있습니다.

### 현지화 {#localization}

현지화는 캠페인의 타겟 및 컨텐츠를 수정하는 로컬 엔티티의 용수입니다. 현지화의 가능한 수준은 캠페인 유형 및 구현에 따라 다릅니다.

### 캠페인 패키지 목록 {#list-of-campaign-packages}

캠페인 패키지 목록에는 로컬 엔티티에 사용할 수 있는 캠페인이 포함되어 있습니다.

### 캠페인 패키지 {#campaign-package}

중앙 엔티티가 만들고 로컬 엔티티 세트에 사용할 수 있도록 만들어진 템플릿(또는 캠페인 인스턴스).

### 로컬 캠페인 {#local-campaign}

로컬 캠페인은 **[!UICONTROL campaign packages]** 특정 실행 일정이 ****&#x200B;있는 목록에서 참조하는 템플릿에서 만든 인스턴스입니다. 이 캠페인의 목표는 중앙 엔티티에 의해 설정 및 구성된 캠페인 템플릿을 사용하여 로컬 커뮤니케이션 요구 사항을 충족하는 것입니다.

지방자치의 자치도는 사용에 따라 달라진다.

로컬 [캠페인](../../campaign/using/creating-a-local-campaign.md)만들기를 참조하십시오.

### 협업 캠페인 {#collaborative-campaign}

협업 캠페인은 로컬 엔티티가 사용할 수 있는 중앙 엔티티에 의해 **실행 일정이 정의된** 캠페인입니다. 컨텐츠는 각 로컬 엔티티에 대해 동일하게 유지되지만 비용은 공유됩니다. 참가하려면 로컬 개체가 공동 작업 캠페인에 구독합니다.

* **[!UICONTROL Collaborative campaign (by form)]**:최대 300개의 로컬 엔티티를 포함하는 캠페인에 권장됩니다. 로컬 엔티티는 타깃팅 및 컨텐츠 개인화를 위한 사전 정의된 매개 변수를 웹 양식에 입력할 수 있습니다. 양식은 Adobe Campaign 양식 또는 외부 양식(엑스트라넷 클라이언트)이 될 수 있습니다. 기능 관리자는 통합자가 정의한 양식 템플릿을 기반으로 양식을 정의하고 구성할 수 있습니다. 캠페인을 주문하려면 로컬 엔티티에는 웹 액세스만 있으면 됩니다.
* **[!UICONTROL Collaborative campaign (by campaign)]**:수십 개의 로컬 엔티티를 대상으로 한 캠페인에 권장됩니다. 이 유형의 캠페인은 각 로컬 엔티티에 대해 하위 캠페인을 만듭니다. 중앙 엔티티가 **[!UICONTROL collaborative campaign (by campaign)]** 캠페인을 승인하면 해당 캠페인을 수정할 수 있는 로컬 엔티티가 캠페인을 사용할 수 있습니다. 실행은 상위 캠페인과 하위 캠페인 간에 자동으로 동기화됩니다. 로컬 엔티티는 캠페인을 주문하고 참여하려면 인스턴스에 액세스할 수 있어야 합니다.
* **[!UICONTROL Collaborative campaign (by target approval)]**:수천 개의 로컬 엔티티를 대상으로 한 캠페인에 권장됩니다. 로컬 엔티티는 중앙 엔티티에 의해 사전 정의된 연락처 목록을 받습니다. 로컬 엔티티는 웹 양식을 통해 캠페인 컨텐츠를 기준으로 특정 연락처를 유지할지 여부를 결정합니다. 로컬 개체는 선택한 연락처 목록에서 추론됩니다. 캠페인에 참여하려면 로컬 엔티티는 웹 액세스만 있으면 됩니다.
* **[!UICONTROL Collaborative campaign (simple)]**:이 모드에서는 이전 버전의 특정 실행 프로세스와 호환됩니다.

협업 [캠페인](../../campaign/using/creating-a-collaborative-campaign.md)만들기를 참조하십시오.

### 캠페인 패키지 주문 {#ordering-campaign-packages}

로컬 엔티티가 캠페인에 등록하면 캠페인 현지화와 관련된 모든 정보를 다시 그룹화하는 순서로 만들어집니다.

## 작업 영역 {#workspace}

캠페인 패키지 목록은 캠페인 우주에서 액세스할 수 **있습니다** .링크를 **[!UICONTROL Campaign packages]** 클릭합니다.

![](assets/mkg_dist_home_local_op.png)

이 창에서는 모든 로컬 연산자가 해당 지역 에이전시에서 사용할 수 있는 캠페인을 볼 수 있습니다.

중앙 기관의 경우 이 창은 캠페인 패키지 목록에서 사용할 수 있는 모든 패키지를 표시하고 목록 편집을 위한 추가 링크를 제공합니다.

## 연산자 및 엔티티 {#operators-and-entities}

먼저 **[!UICONTROL Access management]** 폴더를 통해 중앙 및 로컬 엔티티 연산자를 지정합니다.

![](assets/s_advuser_mkg_dist_tree.png)

### 연산자 {#operators}

중앙 및 로컬 연산자를 만들어야 합니다.

중앙 연산자는 **[!UICONTROL Central management]** 연산자 그룹에 속하거나 **[!UICONTROL CENTRAL]** 명명된 권한을 가져야 합니다.

로컬 연산자는 **[!UICONTROL Local management]** 연산자 그룹에 속하거나 **[!UICONTROL LOCAL]** 명명된 권한을 가져야 합니다. 로컬 엔티티에도 연결되어 있어야 합니다.

![](assets/s_advuser_mkg_dist_local_create.png)

### 조직 구성 요소 {#organizational-entities}

조직 엔티티를 만들려면 **[!UICONTROL Administration > Access management > Organizational entities]** 노드를 클릭하고 엔티티 목록 위에 있는 **[!UICONTROL New]** 아이콘을 클릭합니다.

![](assets/s_advuser_mkg_dist_local_list.png)

각 조직 실체에는 식별 정보(레이블, 내부 이름, 연락처 정보 등)가 포함되어 있습니다. 및 주문 승인 프로세스와 관련된 그룹 이러한 항목은 **[!UICONTROL Notifications and approvals]** 탭에 있는 **[!UICONTROL General]** 섹션에 정의됩니다.

* 패키지 알림 그룹 정의:이 그룹의 연산자는 새 패키지가 캠페인 패키지 목록에 추가되고 캠페인을 사용할 수 있을 때마다 알림을 받게 됩니다.
* 주문 승인을 담당하는 검토자 그룹(예: 로컬 엔티티에서 주문한 캠페인 승인 담당자)을 선택합니다.
* 마지막으로 로컬 캠페인(타겟, 컨텐츠, 예산 등)을 승인하는 업무를 담당하는 검토자 그룹을 선택합니다. 이 그룹은 템플릿에 따라 캠페인을 주문할 때 추가할 수 있습니다.

>[!NOTE]
>
>승인 프로세스는 승인 [프로세스](../../campaign/using/creating-a-local-campaign.md#approval-process) 섹션에 나와 있습니다.

## 구현 {#implementation}

분산 마케팅 캠페인은 중앙 엔티티에서 만들고 게시합니다. 필요에 따라 로컬 및 중앙 개체 모두에서 사용할 수 있습니다.

구현 절차는 사용된 캠페인 패키지 유형과 로컬 엔티티 위임 수준에 따라 달라집니다.

### 통합자 측면 {#integrator-side}

1. 로컬 엔티티를 만듭니다.
1. 수신자를 로컬 엔티티를 관리하는 연산자와 연결합니다.

   ![](assets/mkg_dist_local_entity_association.png)

1. 로컬 엔티티에 대한 권한 및 검색 규칙 지정
1. 캠페인 현지화에 필요한 필드 세트를 지정합니다.

   * 타겟 정의 및 최대 크기,
   * 컨텐츠 정의,
   * 실행 일정(연락처 날짜 및 추출 날짜), **로컬 연산자만**,
   * 필요한 모든 추가 필드를 포함하는 주문 스키마 확장.

1. 로컬라이제이션 매개 변수를 표시하고 타겟 및 예산을 평가하고 컨텐츠를 미리 보고 주문을 승인할 수 있는 웹 양식(Adobe 또는 엑스트라넷)을 만듭니다.

   협업 **캠페인(목표 승인별)**&#x200B;의 경우 각 로컬 엔티티에 대한 승인이 저장되는 테이블을 만듭니다.

### 기능 관리자 측 {#functional-administrator-side}

각 캠페인을 만들 때는 이러한 단계를 수행해야 합니다.

1. 캠페인 현지화에 사용되는 필드로 양식을 업데이트합니다.
1. 적절한 캠페인 템플릿(협업 캠페인)에서 인스턴스를 만들거나 캠페인 템플릿(로컬 캠페인)을 복제합니다.
1. 현지화 필드 및 양식 참조로 캠페인을 구성합니다.
1. 캠페인을 게시합니다.

### 로컬 연산자 측 {#local-operator-side}

이러한 단계는 각 캠페인에 대해 수행해야 합니다.

1. 캠페인 패키지의 가용성에 대한 알림을 받으면 캠페인 위치를 지정합니다(선택 사항).
1. 목표, 예산 등을 평가합니다.
1. 캠페인 콘텐츠 미리 보기
1. 캠페인을 주문합니다.

