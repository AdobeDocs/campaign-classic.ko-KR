---
product: campaign
title: 필터 만들기
description: 쿼리를 수행할 때 필터를 만드는 방법을 알아봅니다
feature: Query Editor, Workflows
hide: true
hidefromtoc: true
exl-id: 297ea1e1-39ef-4b99-aaaa-9e88611fb1bf
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 2%

---

# 필터 만들기 {#creating-a-filter}



Adobe Campaign에서 사용할 수 있는 필터는 쿼리와 동일한 운영 모드를 사용하여 만드는 필터링 조건을 통해 정의됩니다.

>[!NOTE]
>
>필터 만들기에 대한 자세한 내용은 [이 섹션](../../platform/using/filtering-options.md)을 참조하세요.

**[!UICONTROL Administration > Configuration > Predefined filters]** 노드에는 목록 및 개요에 사용된 모든 필터가 포함되어 있습니다.

예를들어 연산자 목록은 **[!UICONTROL Active accounts]**(으)로 필터링될 수 있습니다.

![](assets/query_editor_filter_sample_1.png)

일치하는 필터에 **[!UICONTROL Operators]** 스키마의 **[!UICONTROL Account disabled]** 값에 대한 쿼리가 포함되어 있습니다.

![](assets/query_editor_filter_sample_2.png)

동일한 목록의 경우 **[!UICONTROL By login or label]** 필터를 사용하여 필터 필드에 입력한 값을 기준으로 목록의 데이터를 필터링할 수 있습니다.

![](assets/query_editor_filter_sample_3.png)

다음과 같이 빌드됩니다.

![](assets/query_editor_filter_sample_4.png)

필터링 조건을 일치시키려면 연산자 계정은 다음 조건 중 하나를 확인해야 합니다.

* 레이블에는 입력 필드에 입력한 문자,
* 연산자 이름에는 입력 필드에 입력한 문자,
* 설명 영역의 내용은 입력 필드에 입력한 문자를 포함합니다.

>[!NOTE]
>
>**[!UICONTROL Upper]** 함수를 사용하면 대/소문자를 구분하는 함수를 비활성화할 수 있습니다.

**[!UICONTROL Taken into account if]** 열을 사용하면 이러한 필터링 조건에 대한 응용 프로그램 조건을 정의할 수 있습니다. 여기서 **$(/tmp/@text)**&#x200B;자는 필터에 연결된 입력 필드의 내용을 나타냅니다.

![](assets/query_editor_filter_sample_5.png)

여기, **$(/tmp/@text)=&#39;agency&#39;**

**$(/tmp/@text)!=&#39;&#39;** 식은 입력 필드가 비어 있지 않을 때 각 조건을 적용합니다.
