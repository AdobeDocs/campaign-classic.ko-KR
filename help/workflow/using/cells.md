---
product: campaign
title: 셀
description: 셀
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Targeting Activity
exl-id: 7b562dba-7e4b-40a7-91db-7b9379de44ca
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 8%

---

# 셀{#cells}



다음 **[!UICONTROL Cells]** 활동은 데이터 열의 형태로 다양한 하위 집합의 보기를 제공합니다. 이는 하위 집합 조작을 용이하게 하며 개인화 가능성을 장려하도록 설계되기도 한다.

![](assets/wf_split_cells.png)

이 활동은 사용자 요구에 따라 특정 매개 변수를 입력하도록 구성할 수 있습니다. 기본적으로 각 하위 집합의 세부 정보는 다음을 통해 전용 창에 자세히 설명되어 있습니다. **[!UICONTROL Selection]** 및 **[!UICONTROL Advanced]** 탭. 아래 예에서는 양식이 수정되었습니다. a **[!UICONTROL Data]** 각 하위 집합에 대해 오퍼와 우선 순위 수준을 연결할 수 있도록 탭이 추가되었습니다.

![](assets/wf_split_cells_with_customization.png)

이 구성의 경우 워크플로 양식에 다음 정보가 추가되었습니다( **[!UICONTROL Administration > Configurations > Input forms]** Adobe Campaign 트리의 노드):

```
<container img="nms:miniatures/mini-enrich.png" label="Data">
                <input xpath="@code"/>
                <container xpath="select/node[@alias='@numTest']">
                  <input alwaysActive="true" expr="'long'" type="expr" xpath="@type"/>
                  <input alwaysActive="true" expr="'Priority'" type="expr" xpath="@label"/>
                  <input label="Priority" maxValue="12" minValue="0" type="number"
                         xpath="@value" xpathEditFromType="@type"/>
                </container>
                <container xpath="select/node[@alias='@test']">
                  <input alwaysActive="true" expr="'string'" type="expr" xpath="@type"/>
                  <input alwaysActive="true" expr="'Identifier'" type="expr" xpath="@label"/>
                  <input label="Cell identifier" xpath="@value"/>
                </container>
                <container xpath="select/node[@alias='linkTest']">
                  <input alwaysActive="true" expr="'link'" type="expr" xpath="@type"/>
                  <input alwaysActive="true" expr="'nms:offer'" type="expr" xpath="@dataType"/>
                  <input alwaysActive="true" expr="'Offre'" type="expr" xpath="@label"/>
                  <input computeStringAlias="@valueLabel" label="Offers" notifyPathList="@_cs|@valueLabel"
                         schema="nms:offer" type="linkEdit" xpath="@value"/>
                </container>
```

Adobe Campaign의 시작 양식 개인화는 전문가 사용자용으로 예약되어 있습니다. 자세한 정보는 이 [섹션](../../configuration/using/identifying-a-form.md)을 참조하십시오.
