---
product: campaign
title: 목록 업데이트
description: 목록 업데이트
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Targeting Activity
exl-id: fcc51131-15d0-4d39-95cb-371d7044373b
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 2%

---

# 목록 업데이트{#list-update}



A **목록 업데이트** 활동은 전환에 지정된 모집단을 수신자 목록에 저장합니다.

![](assets/s_user_segmentation_update_group.png)

기존 그룹 목록에서 목록을 선택할 수 있습니다.

를 사용하여 만들 수도 있습니다. **[!UICONTROL Create the list if necessary (Computed name)]** 및 **[!UICONTROL Create the list if necessary (Computed Folder and Name)]** 옵션. 이러한 옵션을 사용하면 목록에서 원하는 레이블을 선택하고 나중에 저장할 폴더를 선택할 수 있습니다. 동적 필드 또는 스크립트를 삽입하여 레이블을 자동으로 생성할 수도 있습니다. 레이블 오른쪽에 있는 팝업 메뉴에서 다양한 동적 필드를 사용할 수 있습니다.

![](assets/s_user_segmentation_update_list_calc.png)

목록이 이미 있는 경우 다음을 확인하지 않는 한 수신자는 기존 콘텐츠에 추가됩니다. **[!UICONTROL Purge the list if it exists (otherwise add to the list)]** 옵션을 선택합니다. 이 경우 업데이트 전에 목록의 콘텐츠가 삭제됩니다.

만들거나 업데이트한 목록에서 수신자 테이블 이외의 테이블을 사용하려면 **[!UICONTROL Create or use a list with its own table]** 옵션을 선택합니다.

이 옵션을 사용하려면 관련 특정 테이블이 Adobe Campaign 인스턴스에 구성되어 있어야 합니다.

일반적으로 대상을 목록에 저장하면 워크플로우의 끝이 표시됩니다. 기본적으로 **[!UICONTROL List update]** 따라서 활동에 아웃바운드 전환이 없습니다. 다음 확인: **[!UICONTROL Generate an outbound transition]** 옵션을 사용하여 하나를 추가합니다.

![](assets/do-not-localize/how-to-video.png) [비디오에서 탐색기를 사용하여 수신자 목록을 만드는 방법을 알아봅니다](#video)

## 예: 목록 업데이트 {#example--list-update}

다음 예에서 목록 업데이트 활동은 프랑스에 거주하는 30세 이상 남성을 타겟으로 하는 쿼리를 따릅니다. 처음에는 쿼리 결과에서 목록이 만들어집니다. 그런 다음 워크플로우에서 실행될 때마다 업데이트됩니다. 예를 들어 캠페인을 위한 타겟팅된 프로모션 오퍼에 정기적으로 사용할 수 있습니다.

1. 추가 **[!UICONTROL list update activity]** 쿼리 바로 뒤에 있는 다음 열어 편집합니다.

   워크플로우에서 쿼리를 만드는 방법에 대한 자세한 내용은 [쿼리](query.md).

1. 활동에 대한 레이블을 선택할 수 있습니다.
1. 다음 항목 선택 **[!UICONTROL Create the list if necessary (Calculated name)]** 첫 번째 워크플로우가 실행되면 목록이 만들어지고 다음 실행으로 업데이트됨을 표시하는 옵션입니다.
1. 목록을 저장할 폴더를 선택합니다.
1. 목록에 대한 레이블을 입력합니다. 동적 필드를 삽입하여 목록에서 이름을 자동으로 생성할 수 있습니다. 이 예제에서 목록은 콘텐츠를 쉽게 식별할 수 있도록 쿼리와 동일한 이름을 갖습니다.
1. 나가기 **[!UICONTROL Purge the list if it exists (otherwise add to the list)]** 타겟팅 기준과 일치하지 않는 수신자를 삭제하고 새 수신자를 목록에 삽입하기 위해 옵션이 선택되었습니다.
1. 또한 **[!UICONTROL Create or use a list with its own table]** 옵션이 선택되었습니다.
1. 나가기 **[!UICONTROL Generate an outbound transition]** 옵션을 선택 취소했습니다.
1. 클릭 **[!UICONTROL Ok]** 그런 다음 워크플로우를 시작합니다.

   ![](assets/s_user_segmentation_update_list_calc_example.png)

   그러면 일치하는 수신자 목록이 생성되거나 업데이트됩니다.

## 입력 매개 변수 {#input-parameters}

* tableName
* 스키마

그룹에 저장할 모집단을 식별합니다.

## 출력 매개 변수 {#output-parameters}

* groupId: 그룹 식별자.

## 튜토리얼 비디오 {#video}

이 비디오는 Explorer에서 수신자 목록을 만드는 방법을 보여 줍니다.

>[!VIDEO](https://video.tv.adobe.com/v/25602/quality=12)

추가 Campaign Classic 방법 비디오를 사용할 수 있습니다 [여기](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=ko).
