---
product: campaign
title: 캠페인 추적
description: Campaign Distributed Marketing을 사용하여 캠페인을 추적하는 방법을 알아봅니다
exl-id: 87d1909c-d2eb-47ce-a860-0e78a64d2914
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 1%

---

# 캠페인 추적{#tracking-a-campaign}

![](../../assets/v7-only.svg)

중앙 엔티티 운영자는 캠페인 패키지 목록에서 캠페인 주문을 추적할 수 있습니다.

이를 통해 다음과 같은 작업을 수행할 수 있습니다.

* [패키지 필터링](#filter-packages),
* [패키지 편집](#edit-packages),
* [패키지 취소](#cancel-a-package),
* [패키지 다시 초기화](#reinitializing-a-package).

## 패키지 필터링 {#filter-packages}

에서 **[!UICONTROL Campaigns]** 탭에서 **[!UICONTROL Campaign packages]** 기존 모든 분산 마케팅 캠페인을 다시 그룹화하는 역할을 합니다. 게시, 지연, 승인 대기 중인 캠페인만 표시되도록 이 목록을 필터링할 수 있습니다. 이렇게 하려면 이 보기의 위쪽 섹션에 있는 링크를 클릭하거나 **[!UICONTROL Filter list]** 을 링크하고 표시할 캠페인 패키지 상태를 선택합니다.

![](assets/mkg_dist_catalog_filter.png)

## 패키지 편집 {#edit-packages}

다음 **[!UICONTROL Campaign packages]** 페이지를 통해 각 패키지의 요약을 볼 수 있습니다.

이 요약에는 다음 정보가 표시됩니다. 레이블, 캠페인 유형, 생성된 캠페인의 이름 및 폴더

패키지 이름을 클릭하여 편집합니다. 로컬 엔티티와 해당 상태별로 주문을 볼 수도 있습니다.

이 정보는 **[!UICONTROL Campaign orders]** 모든 주문을 나열하는 보기.

![](assets/mkg_dist_catalog_op_command_details.png)

중앙 연산자가 순서를 편집할 수 있습니다. 다음 두 가지 방법으로 데이터를 수집할 수 있습니다.

1. 연산자가 주문 이름을 클릭하여 편집할 수 있습니다. 주문 세부 사항이 표시됩니다.

   ![](assets/mkg_dist_catalog_op_command_edit1.png)

   다음 **[!UICONTROL Edit > General]** 탭에서는 캠페인 순서를 지정할 때 로컬 엔티티가 입력한 정보를 볼 수 있습니다.

   ![](assets/mkg_dist_catalog_op_command_edit1a.png)

1. 연산자는 캠페인 패키지 레이블을 클릭하여 편집하고 특정 설정을 변경할 수 있습니다.

   ![](assets/mkg_dist_catalog_op_command_edit2.png)

## 패키지 취소 {#cancel-a-package}

중앙 엔티티는 언제든지 캠페인 패키지를 취소할 수 있습니다.

클릭 **[!UICONTROL Cancel]** 캠페인 패키지에서 **[!UICONTROL Dashboard]**.

![](assets/mkg_dist_cancel_op_from_dashboard.png)

다음 **[!UICONTROL Comment]** 필드를 사용하면 취소를 정당화할 수 있습니다.

대상 **로컬 캠페인**&#x200B;를 취소하면 사용 가능한 마케팅 캠페인 목록에서 패키지를 제거합니다.

대상 **공동 캠페인**&#x200B;를 취소하면 패키지를 취소하면 다양한 작업이 트리거됩니다.

1. 이 패키지와 관련된 주문은 모두 취소됩니다.

   ![](assets/mkg_dist_mutual_op_cancelled.png)

1. 참조 캠페인이 취소되고 모든 활성 프로세스(워크플로우, 게재)가 중지되며

   ![](assets/mkg_dist_mutual_op_cancelled1.png)

1. 관련 모든 로컬 엔티티에 알림이 전송됩니다.

   ![](assets/mkg_dist_mutual_op_cancelled2.png)

필요한 경우 중앙 엔터티가 취소한 패키지에 계속 액세스하고 다시 초기화할 수 있습니다(아래 참조). 로컬 엔티티는 승인되고 시작되면 다시 제공됩니다. 패키지 재초기화 프로세스는 아래에 나와 있습니다.

## 패키지 다시 초기화 {#reinitializing-a-package}

이미 게시된 캠페인 패키지는 다시 초기화, 수정 및 로컬 엔터티에서 사용할 수 있도록 만들 수 있습니다.

1. 관련 패키지를 선택합니다.
1. 을(를) 클릭합니다. **[!UICONTROL Reinitialize the package to reuse it]** 링크를 클릭하고 를 클릭합니다. **[!UICONTROL OK]**.

   ![](assets/mkg_dist_mutual_op_reinit.png)

1. 을(를) 클릭합니다. **[!UICONTROL Save]** 패키지 재초기화를 승인하는 단추.

   ![](assets/mkg_dist_mutual_op_reinit2.png)

1. 패키지 상태가 **[!UICONTROL Being edited]**. 수정, 승인 및 다시 게시하여 캠페인 패키지 목록에 복원합니다.

>[!NOTE]
>
>취소된 캠페인 패키지를 다시 초기화할 수도 있습니다.
