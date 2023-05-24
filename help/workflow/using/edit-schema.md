---
product: campaign
title: 스키마 편집
description: 스키마 편집 워크플로우 활동에 대해 자세히 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Targeting Activity
exl-id: d26966a8-b5db-4fa4-85ec-7ebd770c4ef3
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 3%

---

# 스키마 편집{#edit-schema}



데이터는 변환, 정규화되고 필요한 경우 를 사용하여 워크플로우에서 보강될 수 있습니다. **[!UICONTROL Edit schema]** 활동. 일반적으로 데이터 구조를 정규화하는 데 사용됩니다. 예를 들어 필드나 집계의 평균 값을 계산하여 출력 열의 이름을 바꾸거나 해당 내용을 수정할 수 있습니다.

이 활동은 작업 테이블의 데이터를 변경하지 않고 해당 스키마(데이터의 논리적 보기)만 변경합니다.

![](assets/wf_manipulation_box.png)

를 통해 다른 작업테이블과 조인을 생성할 수도 있습니다. **[!UICONTROL Links]** 탭.

![](assets/wf_manipulation_box_link_tab.png)

아래 섹션에서는 조인 조건 목록(두 테이블의 데이터를 조정하는 데 사용되는 기준)을 구성할 수 있습니다.
