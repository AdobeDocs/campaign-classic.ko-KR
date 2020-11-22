---
solution: Campaign Classic
product: campaign
title: 필터 만들기
description: 쿼리를 수행할 때 필터를 만드는 방법 알아보기
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 2%

---


# 필터 만들기 {#creating-a-filter}

Adobe Campaign에서 사용할 수 있는 필터는 쿼리와 동일한 운영 모드를 사용하여 만들어진 필터링 조건을 통해 정의됩니다.

>[!NOTE]
>
>For more on creating filters, refer to [this section](../../platform/using/filtering-options.md).

노드 **[!UICONTROL Administration > Configuration > Predefined filters]** 는 목록 및 개요 보기에서 사용되는 모든 필터를 포함합니다.

예를 들어 연산자 목록을 다음과 같이 필터링할 수 있습니다. **[!UICONTROL Active accounts]**

![](assets/query_editor_filter_sample_1.png)

일치 필터에는 스키마 값 **[!UICONTROL Account disabled]** 에 대한 **[!UICONTROL Operators]** 쿼리가 포함되어 있습니다.

![](assets/query_editor_filter_sample_2.png)

동일한 목록에 대해 필터 **[!UICONTROL By login or label]** 필터를 사용하면 필터 필드에 입력한 값을 기반으로 목록의 데이터를 필터링할 수 있습니다.

![](assets/query_editor_filter_sample_3.png)

다음과 같이 빌드됩니다.

![](assets/query_editor_filter_sample_4.png)

필터링 조건을 일치시키려면 연산자 계정은 다음 조건 중 하나를 선택해야 합니다.

* 레이블에는 입력 필드에 입력한 문자가 포함되어 있습니다.
* 연산자 이름에는 입력 필드에 입력한 문자가 포함됩니다.
* 설명 영역의 내용은 입력 필드에 입력된 문자를 포함합니다.

>[!NOTE]
>
>이 **[!UICONTROL Upper]** 함수를 사용하면 대소문자를 구분하는 함수를 비활성화할 수 있습니다.

이 **[!UICONTROL Taken into account if]** 열을 사용하면 이러한 필터링 조건에 대한 응용 프로그램 기준을 정의할 수 있습니다. 여기에서 **$(/tmp/@text)** 문자는 필터에 연결된 입력 필드의 내용을 나타냅니다.

![](assets/query_editor_filter_sample_5.png)

여기, **$(/tmp/@text)=&#39;agency&#39;**

$(/tmp/@text)! **=&quot;** 표현식은 입력 필드가 비어 있지 않을 때 각 조건을 적용합니다.
