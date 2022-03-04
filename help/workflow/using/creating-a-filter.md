---
product: campaign
title: 필터 만들기
description: 쿼리를 수행할 때 필터를 만드는 방법을 알아봅니다
feature: Workflows
exl-id: 297ea1e1-39ef-4b99-aaaa-9e88611fb1bf
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 2%

---

# 필터 만들기 {#creating-a-filter}

![](../../assets/common.svg)

Adobe Campaign에서 사용할 수 있는 필터는 쿼리와 동일한 운영 모드를 사용하여 만들어지는 필터링 조건을 통해 정의됩니다.

>[!NOTE]
>
>필터 만들기에 대한 자세한 내용은 [이 섹션](../../platform/using/filtering-options.md).

다음 **[!UICONTROL Administration > Configuration > Predefined filters]** 노드에는 목록 및 개요에 사용되는 모든 필터가 포함되어 있습니다.

예를 들어 연산자 목록은 **[!UICONTROL Active accounts]**:

![](assets/query_editor_filter_sample_1.png)

일치하는 필터에 **[!UICONTROL Account disabled]** 값 **[!UICONTROL Operators]** 스키마:

![](assets/query_editor_filter_sample_2.png)

동일한 목록에 대해서는 **[!UICONTROL By login or label]** 필터를 사용하면 필터 필드에 입력한 값을 기반으로 목록에서 데이터를 필터링할 수 있습니다.

![](assets/query_editor_filter_sample_3.png)

다음과 같이 빌드됩니다.

![](assets/query_editor_filter_sample_4.png)

필터링 조건을 일치시키려면 연산자 계정이 다음 조건 중 하나를 선택해야 합니다.

* 해당 레이블에는 입력 필드에 입력한 문자가 포함되어 있습니다.
* 연산자 이름에는 입력 필드에 입력한 문자가 포함됩니다.
* 설명 영역의 콘텐츠는 입력 필드에 입력한 문자를 포함합니다.

>[!NOTE]
>
>다음 **[!UICONTROL Upper]** 함수를 사용하면 대/소문자를 구분하는 함수를 비활성화할 수 있습니다.

다음 **[!UICONTROL Taken into account if]** 열에서 이러한 필터링 조건에 대한 애플리케이션 기준을 정의할 수 있습니다. 여기, **$(/tmp/@text)** 문자는 필터에 연결된 입력 필드의 내용을 나타냅니다.

![](assets/query_editor_filter_sample_5.png)

여기, **$(/tmp/@text=&#39;agency&#39;**

다음 **$(/tmp/@text)!=&quot;** 입력 필드가 비어 있지 않으면 표현식이 각 조건을 적용합니다.
