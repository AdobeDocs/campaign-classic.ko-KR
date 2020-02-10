---
title: 셀
seo-title: 셀
description: 셀
seo-description: null
page-status-flag: never-activated
uuid: 1b18928f-04e1-4268-ab8e-ff74d78599de
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: f7187d42-56e9-4681-b172-22abd43ecd29
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 셀{#cells}

이 **[!UICONTROL Cells]** 활동은 데이터 열 형태로 다양한 하위 세트 보기를 제공합니다. 이러한 기능은 하위 세트 조작을 용이하게 하며 개인화 가능성을 높이기 위해 고안되었습니다.

![](assets/wf_split_cells.png)

이 활동은 사용자 요구에 따라 특정 매개 변수를 입력하도록 구성할 수 있습니다. 기본적으로 각 하위 세트에 대한 세부 사항은 **[!UICONTROL Selection]** 및 **[!UICONTROL Advanced]** 탭을 통해 전용 창에 자세히 설명되어 있습니다. 아래 예에서는 양식이 수정되었습니다.오퍼의 연관을 활성화하고 각 하위 세트에 대한 우선순위 수준을 활성화하도록 **[!UICONTROL Data]** 탭이 추가되었습니다.

![](assets/wf_split_cells_with_customization.png)

이 구성의 경우 워크플로우 양식(Adobe Campaign 트리의 **[!UICONTROL Administration > Configurations > Input forms]** 노드)에 다음 정보가 추가되었습니다.

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

Adobe Campaign의 시작 양식 개인화는 전문가 사용자를 위해 예약되어 있습니다. For more on this, refer to this [section](../../configuration/using/identifying-a-form.md).
