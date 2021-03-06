---
product: campaign
title: 활용 사례
description: 활용 사례
audience: platform
content-type: reference
topic-tags: filtering-data
exl-id: 85ded096-7d27-41b3-8ef2-93f5ca8def82
source-git-commit: f000cb8bae164c22d1ede15db4e763cf50530674
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 2%

---

# 활용 사례{#use-case}

![](../../assets/common.svg)

## 구독자의 이메일 형식에 대한 필터 만들기 {#creating-a-filter-on-the-email-format-of-subscribers}

이 사용 사례에서는 수신자 이메일 형식을 기반으로 뉴스레터 가입을 정렬하는 필터를 만드는 방법을 보여줍니다.

이렇게 하려면 사전 정의된 파일러를 사용해야 합니다. 이러한 필터는 문서 유형에 연결되어 있으며 **[!UICONTROL Administration > Configuration > Predefined filters]** 노드 아래에 있어야 합니다. 이러한 데이터 필터는 애플리케이션에서 각 유형의 편집기(또는 문서)에 사용할 수 있습니다.

데이터 필터는 사전 정의된 필터와 같은 방식으로 만들어지지만 필터를 적용할 문서 유형을 선택할 수 있는 추가 필드가 있습니다.

다음 단계를 적용합니다.

1. 을 통해 새 필터 만들기 **[!UICONTROL Administration > Configuration > Predefined filters]** 노드 아래에 있어야 합니다.
1. 을(를) 클릭합니다. **[!UICONTROL Select link]** 아이콘 을 클릭하여 관련 문서를 선택합니다.

   ![](assets/s_ncs_user_filter_choose_schema.png)

1. 구독 스키마(nms:subscription)를 선택하고 를 클릭합니다. **[!UICONTROL OK]**.

   ![](assets/s_ncs_user_filter_select_schema.png)

1. 클릭 **[!UICONTROL Edit link]** 선택한 문서의 필드를 보려면

   ![](assets/s_ncs_user_filter_edit_schema.png)

   그런 다음 선택한 문서의 내용을 볼 수 있습니다.

   ![](assets/s_ncs_user_filter_view_schema.png)

   이러한 필드에 액세스하여 필터 편집기 본문에서 필터 조건을 정의할 수 있습니다. 응용 프로그램 필터는 고급 필터와 동일한 방식으로 정의됩니다. 자세한 내용은 [고급 필터 만들기](../../platform/using/creating-filters.md#creating-an-advanced-filter).

1. 정의되지 않은 이메일 형식이 있는 구독만 표시하려면 구독에 새 필터를 만듭니다.

   ![](assets/s_ncs_user_filter_parameters.png)

1. 클릭 **[!UICONTROL Save]** 필터를 해당 유형의 목록에 대해 미리 정의된 필터에 추가하려면 다음을 수행하십시오.
1. 이제 다음 위치에서 이 필터를 사용할 수 있습니다 **[!UICONTROL Subscriptions]** 수신자 프로필의 탭 다음 아이콘을 클릭하여 &quot;알 수 없는 이메일 형식&quot; 필터에 액세스할 수 있습니다 **[!UICONTROL Filters]** 버튼을 클릭합니다.

   ![](assets/s_ncs_user_filter_on_events.png)

   현재 필터의 이름이 목록 위에 표시됩니다. 필터를 취소하려면 **[!UICONTROL Delete this filter]** 아이콘.

   ![](assets/s_ncs_user_filter_on_subscriptions.png)
