---
product: campaign
title: 양식 편집
description: 양식 편집
audience: configuration
content-type: reference
topic-tags: input-forms
exl-id: 24604dc9-f675-4e37-a848-f1911be84f3e
source-git-commit: 0dfce3b514fefef490847d669846e515b714d222
workflow-type: tm+mt
source-wordcount: '1105'
ht-degree: 2%

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


## 간단한 양식 만들기 {#create-simple-form}

양식을 만들려면 다음 단계를 수행합니다.

1. 메뉴에서 **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Input forms]**.
1. 을(를) 클릭합니다. **[!UICONTROL New]** 목록의 오른쪽 상단에 있는 버튼.

   ![](assets/input-form-create-1.png)

1. 양식 속성을 지정합니다.

   * 양식 이름과 네임스페이스를 지정합니다.

      양식 이름 및 네임스페이스가 관련 데이터 스키마와 일치할 수 있습니다.  이 예제에서는 `cus:order` 데이터 스키마:

      ```xml
      <form entitySchema="xtk:form" img="xtk:form.png" label="Order" name="order" namespace="cus" type="iconbox" xtkschema="xtk:form">
        […]
      </form>
      ```

      또는 데이터스키마를에서 명시적으로 지정할 수 있습니다 `entity-schema` 속성을 사용합니다.

      ```xml
      <form entity-schema="cus:stockLine" entitySchema="xtk:form" img="xtk:form.png" label="Stock order" name="stockOrder" namespace="cus" xtkschema="xtk:form">
        […]
      </form>
      ```

   * 양식에 표시할 레이블을 지정합니다.
   * 원할 경우 양식 유형을 지정합니다. 양식 유형을 지정하지 않으면 기본적으로 콘솔 화면 유형이 사용됩니다.

      ![](assets/input-form-create-2.png)

      다중 페이지 양식을 디자인하는 경우에는 `<form>` 요소를 포함하고 컨테이너에서 유형을 지정합니다.

1. **[!UICONTROL Save]**&#x200B;를 클릭합니다.

1. 양식 요소를 삽입합니다.

   예를 들어 입력 필드를 삽입하려면 `<input>` 요소를 생성하지 않습니다. 설정 `xpath` 속성을 XPath 식으로 지정합니다. [자세한 내용](schema-structure.md#referencing-with-xpath).

   이 예제에서는 `nms:recipient` 스키마.

   ```xml
   <input xpath="@firstName"/>
   <input xpath="@lastName"/>
   ```

1. 양식이 특정 스키마 유형을 기반으로 하는 경우 다음 스키마에 대한 필드를 조회할 수 있습니다.

   1. 클릭 **[!UICONTROL Insert]** > **[!UICONTROL Document fields]**.

      ![](assets/input-form-create-4.png)

   1. 필드를 선택하고 을(를) 클릭합니다 **[!UICONTROL OK]**.

      ![](assets/input-form-create-5.png)

1. 필드 편집기를 지정합니다(선택 사항).

   기본 필드 편집기는 각 데이터 유형과 연결됩니다.
   * 날짜 유형 필드의 경우 양식에 입력 달력이 표시됩니다.
   * 열거형 유형 필드의 경우 양식에 선택 목록이 표시됩니다.

   다음과 같은 필드 편집기 유형을 사용할 수 있습니다.

   | 필드 편집기 | 양식 속성 |
   | --- | --- |
   | 라디오 단추 | `type="radiobutton"` |
   | 확인란 | `type="checkbox"` |
   | 트리 편집 | `type="tree"` |

   자세한 내용 [메모리 목록 컨트롤](form-structure.md#memory-list-controls).

1. 필드에 대한 액세스를 정의합니다(선택적).

   | 요소 | 속성 | 설명 |
   | --- | --- | --- |
   | `<input>` | `read-only:"true"` | 필드에 읽기 전용 액세스 권한을 제공합니다 |
   | `<container>` | `type="visibleGroup" visibleIf="`*edit-expr*`"` | 조건부로 필드 그룹을 표시합니다. |
   | `<container>` | `type="enabledGroup" enabledIf="`*edit-expr*`"` | 조건부로 필드 그룹을 활성화합니다 |

   예제:

   ```xml
   <container type="enabledGroup" enabledIf="@gender=1">
     […]
   </container>
   <container type="enabledGroup" enabledIf="@gender=2">
     […]
   </container>
   ```

1. 컨테이너를 사용하여 필드를 섹션으로 그룹화합니다(선택적).

   ```xml
   <container type="frame" label="Name">
      <input xpath="@firstName"/>
      <input xpath="@lastName"/>
   </container>
   <container type="frame" label="Contact details">
      <input xpath="@email"/>
      <input xpath="@phone"/>
   </container>
   ```

   ![](assets/input-form-create-3.png)

## 다중 페이지 양식 만들기 {#create-multipage-form}

다중 페이지 양식을 만들 수 있습니다. 다른 양식 내에 양식을 중첩할 수도 있습니다.

### 만들기 `iconbox` 양식

를 사용하십시오 `iconbox` 양식 유형은 양식 왼쪽에 아이콘을 표시하여 사용자가 양식의 다른 페이지로 이동하게 합니다.

![](assets/iconbox_form_preview.png)

기존 양식의 유형을 `iconbox`다음 단계를 수행합니다.

1. 변경 `type` 의 속성 `<form>` 요소 대상 `iconbox`:

   ```xml
   <form […] type="iconbox">
   ```

1. 각 양식 페이지에 대한 컨테이너를 설정합니다.

   1. 추가 `<container>` 요소의 하위 `<form>` 요소를 생성하지 않습니다.
   1. 아이콘에 대한 레이블과 이미지를 정의하려면 `label` 및 `img` 속성을 사용합니다.

      ```xml
      <form entitySchema="xtk:form" name="Service provider" namespace="nms" type="iconbox" xtkschema="xtk:form">
          <container img="xtk:properties.png" label="General">
              <input xpath="@label"/>
              <input xpath="@name"/>
              […]
          </container>
          <container img="nms:msgfolder.png" label="Details">
              <input xpath="@address"/>
              […]
          </container>
          <container img="nms:supplier.png" label="Services">
              […]
          </container>
      </form>
      ```
   또는, `type="frame"` 기존 속성의 특성 `<container>` 요소를 생성하지 않습니다.

### 전자 필기장 양식 만들기

를 사용하십시오 `notebook` 양식 유형은 양식의 맨 위에 탭을 표시하여 사용자를 다른 페이지로 안내하는 데 사용합니다.

![](assets/notebook_form_preview.png)

기존 양식의 유형을 `notebook`다음 단계를 수행합니다.

1. 변경 `type` 의 속성 `<form>` 요소 대상 `notebook`:

   ```xml
   <form […] type="notebook">
   ```

1. 각 양식 페이지에 대한 컨테이너를 추가합니다.

   1. 추가 `<container>` 요소의 하위 `<form>` 요소를 생성하지 않습니다.
   1. 아이콘의 레이블과 이미지를 정의하려면 `label` 및 `img` 속성을 사용합니다.

   ```xml
     <form entitySchema="xtk:form" name="Service provider" namespace="nms" type="notebook" xtkschema="xtk:form">
         <container label="General">
             <input xpath="@label"/>
             <input xpath="@name"/>
             […]
         </container>
         <container label="Details">
             <input xpath="@address"/>
             […]
         </container>
         <container label="Services">
             […]
         </container>
     </form>
   ```

   또는, `type="frame"` 기존 속성의 특성 `<container>` 요소를 생성하지 않습니다.

### 양식 중첩 {#nest-forms}

다른 양식 내에 양식을 중첩할 수 있습니다. 예를 들어 전자 필기장 양식을 iconbox 양식 내에 중첩할 수 있습니다.

중첩 컨트롤 탐색 수준입니다. 사용자는 하위 양식으로 드릴다운할 수 있습니다.

다른 양식 내에 양식을 중첩하려면 `<container>` 요소 및 설정 `type` 속성을 폼 형식으로 지정합니다. 최상위 양식의 경우 외부 컨테이너 또는 `<form>` 요소를 생성하지 않습니다.

### 예제

이 예는 복잡한 양식을 보여 줍니다.

* 최상위 양식은 iconbox 양식입니다. 이 양식은 두 개의 컨테이너를 포함하고 있습니다 **일반** 및 **세부 사항**.

   따라서 외부 양식에 **일반** 및 **세부 사항** 상위 수준의 페이지. 이러한 페이지에 액세스하려면 양식 왼쪽의 아이콘을 클릭합니다.

* 하위 폼은 **일반** 컨테이너. 하위 폼은 레이블이 지정된 컨테이너 두 개를 포함합니다 **이름** 및 **연락처**.

```xml
<form _cs="Profile (nms)" entitySchema="xtk:form" img="xtk:form.png" label="Profile" name="profile" namespace="nms" xtkschema="xtk:form">
  <container type="iconbox">
    <container img="ncm:general.png" label="General">
      <container type="notebook">
        <container label="Name">
          <input xpath="@firstName"/>
          <input xpath="@lastName"/>
        </container>
        <container label="Contact">
          <input xpath="@email"/>
        </container>
      </container>
    </container>
    <container img="ncm:detail.png" label="Details">
      <input xpath="@birthDate"/>
    </container>
  </container>
</form>
```

따라서, **일반** 외부 양식의 페이지에 **이름** 및 **연락처** 탭.

![](assets/nested_forms_preview.png)
