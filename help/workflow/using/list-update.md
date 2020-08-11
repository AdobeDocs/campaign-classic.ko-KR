---
title: 목록 업데이트
seo-title: 목록 업데이트
description: 목록 업데이트
seo-description: null
page-status-flag: never-activated
uuid: 1446f115-3f64-4b95-8e04-6426ab1b8dab
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: ca2cd5bf-78a2-4e43-955d-206f4474d1e0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: bc54cef4c44be4c694e062f56685dbb09d2fcf8e
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---


# 목록 업데이트{#list-update}

목록 **업데이트** 활동은 전환 시 지정한 모집단을 수신자 목록에 저장합니다.

![](assets/s_user_segmentation_update_group.png)

기존 그룹 목록에서 목록을 선택할 수 있습니다.

또한 **[!UICONTROL Create the list if necessary (Computed name)]** 및 **[!UICONTROL Create the list if necessary (Computed Folder and Name)]** 옵션을 사용하여 만들 수도 있습니다. 이러한 옵션을 사용하면 목록을 만들 레이블과 나중에 저장할 폴더를 선택할 수 있습니다. 동적 필드나 스크립트를 삽입하여 레이블을 자동으로 생성할 수도 있습니다. 레이블 오른쪽의 팝업 메뉴에서 다양한 동적 필드를 사용할 수 있습니다.

![](assets/s_user_segmentation_update_list_calc.png)

목록이 이미 있는 경우 옵션을 선택하지 않으면 수신자가 기존 컨텐츠에 추가됩니다 **[!UICONTROL Purge the list if it exists (otherwise add to the list)]** . 이 경우 업데이트 전에 목록의 내용이 삭제됩니다.

생성되거나 업데이트된 목록에서 수신자 테이블 이외의 테이블을 사용하려면 **[!UICONTROL Create or use a list with its own table]** 옵션을 선택합니다.

이 옵션을 사용하려면 관련 특정 테이블이 Adobe Campaign 인스턴스에 구성되어야 합니다.

일반적으로 목록에 대상을 저장하면 작업 과정의 끝을 표시합니다. 기본적으로 **[!UICONTROL List update]** 활동에는 아웃바운드 전환이 없습니다. 옵션을 **[!UICONTROL Generate an outbound transition]** 선택하여 추가합니다.

## 예:목록 업데이트 {#example--list-update}

다음 예에서 목록 업데이트 활동은 프랑스에 거주하는 30명 이상의 남성을 대상으로 하는 쿼리를 따릅니다. 목록은 처음에 쿼리 결과에서 만들어집니다. 그러면 워크플로우에서 실행할 때마다 업데이트됩니다. 예를 들어 캠페인의 타깃팅된 프로모션 오퍼에 정기적으로 사용할 수 있습니다.

1. 쿼리 **[!UICONTROL list update activity]** 바로 다음에 쿼리를 추가한 다음 열어 편집합니다.

   워크플로우에서 쿼리를 만드는 방법에 대한 자세한 내용은 [쿼리를 참조하십시오](../../workflow/using/query.md).

1. 활동의 레이블을 선택할 수 있습니다.
1. 첫 번째 워크플로우가 실행되면 목록이 생성된다는 것을 **[!UICONTROL Create the list if necessary (Calculated name)]** 표시하려면 옵션을 선택하고 다음 실행으로 업데이트합니다.
1. 목록을 저장할 폴더를 선택합니다.
1. 목록의 레이블을 입력합니다. 동적 필드를 삽입하여 목록에서 이름을 자동으로 생성할 수 있습니다. 이 예에서, 목록의 이름은 해당 컨텐츠를 쉽게 식별할 수 있는 쿼리와 동일합니다.
1. 타깃팅 기준과 일치하지 않는 수신자를 삭제하고 새 수신자를 목록에 삽입하려면 이 옵션을 선택된 상태로 두십시오 **[!UICONTROL Purge the list if it exists (otherwise add to the list)]** .
1. 또한 옵션을 **[!UICONTROL Create or use a list with its own table]** 선택된 상태로 둡니다.
1. 옵션을 **[!UICONTROL Generate an outbound transition]** 선택 취소하지 않습니다.
1. Click **[!UICONTROL Ok]** then start the workflow.

   ![](assets/s_user_segmentation_update_list_calc_example.png)

   그런 다음 일치하는 받는 사람 목록을 만들거나 업데이트합니다.

자세한 내용은 수신자 [목록 만들기 비디오를](https://docs.adobe.com/content/help/en/campaign-classic-learn/tutorials/profile-management/creating-a-list-of-recipients.html) 참조하십시오.

## 입력 매개 변수 {#input-parameters}

* tableName
* 스키마

그룹에 저장할 모집단을 식별합니다.

## 출력 매개 변수 {#output-parameters}

* groupId:그룹 식별자입니다.
