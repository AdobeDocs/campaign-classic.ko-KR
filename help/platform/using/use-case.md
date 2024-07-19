---
product: campaign
title: 활용 사례
description: 활용 사례
feature: Subscriptions, Email, Data Management
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
audience: platform
content-type: reference
topic-tags: filtering-data
exl-id: 85ded096-7d27-41b3-8ef2-93f5ca8def82
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 2%

---

# 활용 사례{#use-case}



## 구독자의 이메일 형식에 대한 필터 만들기 {#creating-a-filter-on-the-email-format-of-subscribers}

이 사용 사례에서는 수신자 이메일 형식을 기반으로 뉴스레터 구독을 정렬하는 필터를 만드는 방법을 보여 줍니다.

이렇게 하려면 미리 정의된 필터를 사용해야 합니다. 이러한 필터는 문서 형식에 연결되고 **[!UICONTROL Administration > Configuration > Predefined filters]** 노드를 통해 액세스됩니다. 이러한 데이터 필터는 애플리케이션에서 각 유형의 편집기(또는 문서)에 사용할 수 있습니다.

데이터 필터는 사전 정의된 필터와 동일한 방식으로 만들어지지만, 필터가 적용될 문서 유형을 선택하는 추가 필드가 있습니다.

다음 단계를 적용합니다.

1. **[!UICONTROL Administration > Configuration > Predefined filters]** 노드를 통해 새 필터를 만듭니다.
1. 관련 문서를 선택하려면 **[!UICONTROL Select link]** 아이콘을 클릭하십시오.

   ![](assets/s_ncs_user_filter_choose_schema.png)

1. 구독 스키마(nms:subscription)를 선택하고 **[!UICONTROL OK]**&#x200B;을(를) 클릭합니다.

   ![](assets/s_ncs_user_filter_select_schema.png)

1. 선택한 문서의 필드를 보려면 **[!UICONTROL Edit link]**&#x200B;을(를) 클릭하십시오.

   ![](assets/s_ncs_user_filter_edit_schema.png)

   그런 다음 선택한 문서의 컨텐트를 볼 수 있습니다.

   ![](assets/s_ncs_user_filter_view_schema.png)

   이러한 필드에 액세스하여 필터 편집기의 본문에 필터 조건을 정의할 수 있습니다. 애플리케이션 필터는 고급 필터와 동일한 방식으로 정의됩니다. [고급 필터 만들기](../../platform/using/creating-filters.md#creating-an-advanced-filter)를 참조하십시오.

1. 구독에 대한 새 필터를 만들어 정의되지 않은 이메일 형식의 구독만 표시합니다.

   ![](assets/s_ncs_user_filter_parameters.png)

1. **[!UICONTROL Save]**&#x200B;을(를) 클릭하여 이 유형의 목록에 대해 미리 정의된 필터에 필터를 추가합니다.
1. 이제 수신자 프로필의 **[!UICONTROL Subscriptions]** 탭에서 이 필터를 사용할 수 있습니다. **[!UICONTROL Filters]** 버튼을 클릭하여 &quot;알 수 없는 이메일 형식&quot; 필터에 액세스할 수 있습니다.

   ![](assets/s_ncs_user_filter_on_events.png)

   현재 필터의 이름이 목록 위에 표시됩니다. 필터를 취소하려면 **[!UICONTROL Delete this filter]** 아이콘을 클릭합니다.

   ![](assets/s_ncs_user_filter_on_subscriptions.png)
