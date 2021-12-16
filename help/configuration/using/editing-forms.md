---
product: campaign
title: 양식 편집
description: 양식 편집
audience: configuration
content-type: reference
topic-tags: input-forms
exl-id: 24604dc9-f675-4e37-a848-f1911be84f3e
source-git-commit: f4b9ac3300094a527b5ec1b932d204f0e8e5ee86
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 4%

---


# 양식 편집{#editing-forms}

![](../../assets/common.svg)

## 개요

마케터와 운영자는 입력 양식을 사용하여 레코드를 작성, 수정 및 미리 봅니다. Forms은 정보를 시각적으로 보여줍니다.

입력 양식을 만들고 수정할 수 있습니다.

* 기본적으로 제공되는 출하 시 입력 양식을 수정할 수 있습니다. 공장 입력 양식은 출하 시 데이터 스키마를 기반으로 합니다.
* 정의한 데이터 스키마를 기반으로 하여 사용자 정의 입력 양식을 만들 수 있습니다.

Forms은 의 엔티티입니다 `xtk:form` 유형. 에서 입력 양식 구조를 볼 수 있습니다 `xtk:form` 스키마. 이 스키마를 보려면 **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]** 메뉴 아래의 제품에서 사용할 수 있습니다. 자세한 내용 [양식 구조](form-structure.md).

입력 양식에 액세스하려면 **[!UICONTROL Administration]> [!UICONTROL Configuration] >[!UICONTROL Input forms]** 메뉴에서:

![](assets/d_ncs_integration_form_arbo.png)

양식을 디자인하려면 XML 편집기에서 XML 내용을 편집합니다.

![](assets/d_ncs_integration_form_edit.png)

[자세한 내용](form-structure.md#formatting).

양식을 미리 보려면 **[!UICONTROL Preview]** 탭:

![](assets/d_ncs_integration_form_preview.png)

## 양식 유형

다양한 유형의 입력 양식을 만들 수 있습니다. 양식 유형은 사용자가 양식을 탐색하는 방법을 결정합니다.

* 콘솔 화면

   기본 양식 유형입니다. 상기 양식은 하나의 페이지로 이루어진다.

   ![](assets/console_screen_form.png)

* 콘텐츠 관리

   콘텐츠 관리를 위해 이 양식 유형을 사용합니다. 다음 보기 [사용 사례](../../delivery/using/use-case--creating-content-management.md).

   ![](../../delivery/using/assets/d_ncs_content_form13.png)

* 마법사

   이 양식은 특정 시퀀스로 정렬된 여러 부동 화면으로 구성됩니다. 사용자가 한 화면에서 다음 화면으로 이동합니다. [자세한 내용](form-structure.md#wizards).

* Iconbox

   이 양식은 여러 페이지로 구성됩니다. 양식을 탐색하려면 양식 왼쪽에서 아이콘을 선택합니다.

   ![](assets/iconbox_form_preview.png)

* 노트북

   이 양식은 여러 페이지로 구성됩니다. 양식을 탐색하려면 양식 상단에 있는 탭을 선택합니다.

   ![](assets/notebook_form_preview.png)

* 세로 창

   이 양식은 탐색 트리를 보여 줍니다.

* 가로 창

   이 양식에 항목 목록이 표시됩니다.

## 컨테이너

양식에서 컨테이너를 다양한 용도로 사용할 수 있습니다.

* 양식 내에서 컨텐츠 구성
* 입력 필드에 대한 액세스 정의
* 다른 양식 내에 양식 중첩

[자세한 내용](form-structure.md#containers).

### 컨텐츠 구성

컨테이너를 사용하여 양식 내에서 컨텐츠를 구성할 수 있습니다.

* 필드를 섹션으로 그룹화할 수 있습니다.
* 다중 페이지 양식에 페이지를 추가할 수 있습니다.

컨테이너를 삽입하려면 `<container>` 요소를 생성하지 않습니다. [자세한 내용](form-structure.md#containers).

#### 그룹 필드

컨테이너를 사용하여 입력 필드를 구성된 섹션으로 그룹화합니다.

양식에 섹션을 삽입하려면 다음 요소를 사용합니다. `<container type="frame">`. 섹션 제목을 추가하려면 `label` 속성을 사용합니다.

구문: `<container type="frame" label="`*section_title*`"> […] </container>`

이 예에서 컨테이너는 **만들기** 섹션을 포함하는 **[!UICONTROL Created by]** 및 **[!UICONTROL Name]** 입력 필드:

```xml
<form _cs="Coupons (nms)" entitySchema="xtk:form" img="xtk:form.png" label="Coupons"
      name="coupon" namespace="nms" type="default" xtkschema="xtk:form">
  <input xpath="@code"/>
  <input xpath="@type"/>
  <container label="Creation" type="frame">
    <input xpath="createdBy"/>
    <input xpath="createdBy/@name"/>
  </container>
</form>
```

![](assets/console_screen_form.png)

#### 다중 페이지 양식에 페이지 추가

다중 페이지 양식의 경우 컨테이너를 사용하여 양식 페이지를 만듭니다.

이 예는 **일반** 및 **세부 사항** 양식의 페이지:

```xml
<container img="ncm:book.png" label="General">
[…]
</container>
<container img="ncm:detail.png" label="Details">
[…]
</container>
```

### 필드에 대한 액세스 정의

컨테이너를 사용하여 표시되는 내용을 정의하고 필드에 대한 액세스를 정의합니다. 필드 그룹을 켜거나 끌 수 있습니다.

### 양식 중첩

컨테이너를 사용하여 다른 양식 내에 양식을 중첩합니다. [자세한 내용](#add-pages-to-multipage-forms).

## 이미지에 대한 참조

이미지를 찾으려면 **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Images]** 메뉴 아래의 제품에서 사용할 수 있습니다.

예를 들어 아이콘과 같은 양식의 요소에 이미지를 연결하려면 이미지에 참조를 추가할 수 있습니다. 를 사용하십시오 `img` 속성(예: `<container>` 요소를 생성하지 않습니다.

구문: `img="`*`namespace`*`:`*`filename`*`.`*`extension`*`"`

이 예는 `book.png` 및 `detail.png` 의 이미지 `ncm` namespace:

```xml
<container img="ncm:book.png" label="General">
[…]
</container>
<container img="ncm:detail.png" label="Details">
[…]
</container>
```

이 이미지는 사용자가 다중 페이지 양식을 탐색하기 위해 클릭하는 아이콘에 사용됩니다.

![](assets/nested_forms_preview.png)
