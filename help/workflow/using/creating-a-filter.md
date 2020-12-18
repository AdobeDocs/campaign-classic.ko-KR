---
solution: Campaign Classic
product: campaign
title: 필터 만들기
description: 쿼리를 수행할 때 필터를 만드는 방법을 알아봅니다.
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
>필터 만들기에 대한 자세한 내용은 [이 섹션](../../platform/using/filtering-options.md)을 참조하십시오.

**[!UICONTROL Administration > Configuration > Predefined filters]** 노드에는 목록 및 오버뷰에 사용된 모든 필터가 포함되어 있습니다.

예를 들어 연산자 목록을 **[!UICONTROL Active accounts]**&#x200B;으로 필터링할 수 있습니다.

![](assets/query_editor_filter_sample_1.png)

일치 필터는 **[!UICONTROL Operators]** 스키마의 **[!UICONTROL Account disabled]** 값에 대한 쿼리를 포함합니다.

![](assets/query_editor_filter_sample_2.png)

동일한 목록에 대해 **[!UICONTROL By login or label]** 필터를 사용하면 필터 필드에 입력한 값을 기반으로 목록의 데이터를 필터링할 수 있습니다.

![](assets/query_editor_filter_sample_3.png)

다음과 같이 빌드됩니다.

![](assets/query_editor_filter_sample_4.png)

필터링 조건을 일치시키려면 연산자 계정은 다음 조건 중 하나를 확인해야 합니다.

* 레이블에는 입력 필드에 입력한 문자가 포함되어 있습니다.
* 연산자 이름에는 입력 필드에 입력한 문자가 포함되어 있습니다.
* 설명 영역의 내용은 입력 필드에 입력된 문자를 포함합니다.

>[!NOTE]
>
>**[!UICONTROL Upper]** 함수를 사용하면 대소문자를 구분하는 함수를 비활성화할 수 있습니다.

**[!UICONTROL Taken into account if]** 열을 사용하여 이러한 필터링 조건에 대한 응용 프로그램 기준을 정의할 수 있습니다. 여기에서 **$(/tmp/@text)** 문자는 필터에 연결된 입력 필드의 내용을 나타냅니다.

![](assets/query_editor_filter_sample_5.png)

여기, **$(/tmp/@text)=&#39;agency&#39;**

**$(/tmp/@text)!=&quot;** 표현식은 입력 필드가 비어 있지 않을 때 각 조건을 적용합니다.
