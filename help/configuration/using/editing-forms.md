---
product: campaign
title: 양식 편집
description: 양식 편집
audience: configuration
content-type: reference
topic-tags: input-forms
exl-id: 24604dc9-f675-4e37-a848-f1911be84f3e
source-git-commit: a6549ad4d94b93d65752df66aeec39b90e4c3ec5
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 5%

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

