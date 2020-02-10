---
title: 추적된 링크를 구성하는 방법
seo-title: 추적된 링크를 구성하는 방법
description: 추적된 링크를 구성하는 방법
seo-description: null
page-status-flag: never-activated
uuid: 0fb41a43-8a84-4a61-bf93-97e1d448a5ec
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: tracking-messages
discoiquuid: 9cae3861-88eb-447a-aa23-9d1de0710eec
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# 추적된 링크를 구성하는 방법{#how-to-configure-tracked-links}

각 전달에 대해 메시지 수신과 메시지 컨텐츠에 삽입된 링크의 활성화를 추적할 수 있습니다. 이렇게 하면 받는 사람이 타깃팅된 전달 작업 이후 받는 사람의 동작을 추적할 수 있습니다.

>[!NOTE]
>
>추적은 메시지에 적용되지만 웹 추적을 통해 받는 사람이 웹 사이트를 검색하는 방식(방문한 페이지, 구매)을 모니터링할 수 있습니다.
>
>웹 추적 구성은 [이 섹션에](../../configuration/using/about-web-tracking.md)설명되어 있습니다.

메시지 추적은 기본적으로 활성화되어 있습니다. URL을 추적하는 방법을 개인화하려면 아래 단계를 따르십시오.

1. 메시지 컨텐츠 아래의 배달 마법사 하단 섹션에서 옵션을 **[!UICONTROL Display URLs]** 선택합니다.

   ![](assets/s_ncs_user_email_del_display_urls.png)

   추적된 URL 목록에서 URL을 선택하면 미러 페이지의 링크와 기본적으로 제공되는 가입 해지 링크를 제외하고 배달 컨텐츠에서 강조 표시됩니다.

   ![](assets/s_ncs_user_email_del_show_urls.png)

1. 메시지의 각 URL에 대해 추적을 활성화할지 여부를 선택합니다.

   >[!CAUTION]
   >
   >링크의 URL을 레이블로 사용하는 경우 피싱으로 인해 거절될 위험을 방지하기 위해 추적을 비활성화하는 것이 좋습니다.
   >
   >예를 들어 www.adobe.com URL이 메시지에 삽입되고 추적이 활성화되면 하이퍼텍스트 링크의 컨텐츠가 https://nlt.adobe.net/r/?id=xxxxxx로 수정됩니다. 즉, 수신자 메시지 클라이언트에서 부정 행위로 간주될 수 있습니다.

1. 필요한 경우 추적 레이블을 변경하고 레이블을 두 번 클릭하고 새 레이블을 입력합니다.

   >[!NOTE]
   >
   >추적된 URL 및 레이블의 레이블을 수정하여 배달을 추적할 때 정보를 쉽게 읽을 수 있습니다. 클릭 수를 계산할 때 이름이 같은 두 개 또는 두 개의 레이블이 함께 추가됩니다.

1. 필요한 경우 추적 모드를 변경하고, 아래에서 보듯이 타깃팅된 링크와 일치하는 새 모드를 **[!UICONTROL Tracking]** 열에서 선택합니다.

   ![](assets/s_ncs_user_select_tracking_mode.png)

   각 개별 URL에 대해 추적 모드를 다음 값 중 하나로 설정할 수 있습니다.

   * **[!UICONTROL Enabled]** :이 URL에 대한 추적을 활성화합니다.
   * **[!UICONTROL Not tracked]** :이 URL에 대한 추적을 비활성화합니다.
   * **[!UICONTROL Always enabled]** :항상 이 URL의 추적을 활성화합니다. 이 정보는 다음에 URL이 향후 메시지 컨텐츠에 다시 나타날 때 추적이 자동으로 활성화되도록 저장됩니다.
   * **[!UICONTROL Never tracked]** :이 URL의 추적을 활성화하지 않습니다. 이 정보는 다음에 URL이 다시 나타날 경우 추적이 자동으로 비활성화되도록 저장됩니다.
   * **[!UICONTROL Opt-out]** :이 URL을 옵트아웃 또는 구독 취소 URL로 간주합니다.
   * **[!UICONTROL Mirror page]** :이 URL이 미러 페이지 URL로 간주합니다.

1. 또한 **[!UICONTROL Category]** 열의 드롭다운 목록에서 추적된 각 URL에 대한 카테고리를 선택할 수 있습니다. 이러한 카테고리는 다음과 같이 보고서를 표시할 수 **[!UICONTROL URLs and click streams]** 있습니다( [이 섹션](../../reporting/using/reports-on-deliveries.md#urls-and-click-streams)참조). 카테고리는 특정 열거형에 정의됩니다.(열거형 **[!UICONTROL urlCategory]** 관리를 [](../../platform/using/managing-enumerations.md)참조하십시오.)
