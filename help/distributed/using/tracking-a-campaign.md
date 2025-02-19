---
product: campaign
title: 캠페인 추적
description: Campaign Distributed Marketing으로 캠페인을 추적하는 방법에 대해 알아보기
feature: Distributed Marketing
hide: true
hidefromtoc: true
exl-id: 87d1909c-d2eb-47ce-a860-0e78a64d2914
source-git-commit: 36fe54cf6d4d762d96205bd637311a426c741427
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 1%

---

# 캠페인 추적{#tracking-a-campaign}



중앙 엔티티 운영자는 캠페인 패키지 목록에서 캠페인 주문을 추적할 수 있습니다.

이렇게 하면 다음과 같은 작업을 수행할 수 있습니다.

* [패키지 필터링](#filter-packages),
* [패키지 편집](#edit-packages),
* [패키지 취소](#cancel-a-package),
* [패키지를 다시 초기화합니다](#reinitializing-a-package).

## 패키지 필터링 {#filter-packages}

**[!UICONTROL Campaigns]** 탭에서 기존의 모든 Distributed Marketing 캠페인을 다시 그룹화하는 **[!UICONTROL Campaign packages]** 목록을 표시할 수 있습니다. 게시, 지연, 승인 보류 등 상태의 캠페인만 표시되도록 이 목록을 필터링할 수 있습니다. 이렇게 하려면 이 보기의 위쪽 섹션에 있는 링크를 클릭하거나 **[!UICONTROL Filter list]** 링크를 사용하고 표시할 캠페인 패키지 상태를 선택하십시오.

![](assets/mkg_dist_catalog_filter.png)

## 패키지 편집 {#edit-packages}

**[!UICONTROL Campaign packages]** 페이지에서 각 패키지의 요약을 볼 수 있습니다.

이 요약에는 레이블, 캠페인 유형, 생성된 캠페인 이름 및 폴더와 같은 정보가 표시됩니다.

패키지 이름을 클릭하여 편집합니다. 로컬 엔티티별 및 상태별로 주문을 볼 수도 있습니다.

이 정보는 모든 주문을 나열하는 **[!UICONTROL Campaign orders]** 보기에서도 제공됩니다.

![](assets/mkg_dist_catalog_op_command_details.png)

중앙 연산자는 순서를 편집할 수 있습니다. 두 가지 방법으로 이 작업을 수행할 수 있습니다.

1. 연산자는 주문 이름을 클릭하여 편집할 수 있습니다. 이렇게 하면 주문 세부 사항이 표시됩니다.

   ![](assets/mkg_dist_catalog_op_command_edit1.png)

   **[!UICONTROL Edit > General]** 탭에서는 로컬 엔터티가 캠페인을 주문했을 때 입력한 정보를 볼 수 있습니다.

   ![](assets/mkg_dist_catalog_op_command_edit1a.png)

1. 운영자는 캠페인 패키지 레이블을 클릭하여 편집하고 특정 설정을 변경할 수 있습니다.

   ![](assets/mkg_dist_catalog_op_command_edit2.png)

## 패키지 취소 {#cancel-a-package}

중앙 엔티티는 언제든지 캠페인 패키지를 취소할 수 있습니다.

캠페인 패키지 **[!UICONTROL Dashboard]**&#x200B;에서 **[!UICONTROL Cancel]**&#x200B;을(를) 클릭합니다.

![](assets/mkg_dist_cancel_op_from_dashboard.png)

**[!UICONTROL Comment]** 필드를 사용하면 취소를 강제 적용할 수 있습니다.

**로컬 캠페인**&#x200B;의 경우 패키지를 취소하면 사용 가능한 마케팅 캠페인 목록에서 패키지가 제거됩니다.

**공동 작업 캠페인**&#x200B;의 경우 패키지를 취소하면 다음과 같은 여러 작업이 트리거됩니다.

1. 이 패키지와 관련된 모든 주문이 취소되었습니다.

   ![](assets/mkg_dist_mutual_op_cancelled.png)

1. 참조 캠페인이 취소되고 모든 활성 프로세스(워크플로우, 게재)가 중지됩니다.

   ![](assets/mkg_dist_mutual_op_cancelled1.png)

1. 관련 모든 로컬 엔티티에 알림이 전송됩니다.

   ![](assets/mkg_dist_mutual_op_cancelled2.png)

취소된 패키지는 여전히 필요한 경우 중앙 엔터티(아래 참조)에 의해 액세스하고 다시 초기화할 수 있습니다. 이 지표는 승인 및 시작되면 로컬 엔티티에 다시 대해서만 제공됩니다. 패키지 재초기화 프로세스는 아래에 나와 있습니다.

## 패키지 다시 초기화 {#reinitializing-a-package}

이미 게시된 Campaign 패키지는 다시 초기화 및 수정하여 로컬 엔터티에서 사용할 수 있습니다.

1. 관련 패키지를 선택합니다.
1. **[!UICONTROL Reinitialize the package to reuse it]** 링크를 클릭하고 **[!UICONTROL OK]**&#x200B;을(를) 클릭합니다.

   ![](assets/mkg_dist_mutual_op_reinit.png)

1. 패키지 다시 초기화를 승인하려면 **[!UICONTROL Save]** 단추를 클릭하십시오.

   ![](assets/mkg_dist_mutual_op_reinit2.png)

1. 패키지 상태가 **[!UICONTROL Being edited]**(으)로 변경됩니다. 수정, 승인 및 다시 게시하여 캠페인 패키지 목록으로 복원합니다.

>[!NOTE]
>
>취소된 캠페인 패키지를 다시 초기화할 수도 있습니다.
