---
product: campaign
title: 추적되는 링크를 구성하는 방법
description: 추적되는 링크를 구성하는 방법
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Monitoring
exl-id: ed88e1d6-c0d5-4a85-9f3e-be670f4bcc10
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 10%

---

# 추적되는 링크를 구성하는 방법{#how-to-configure-tracked-links}



각 게재에 대해 메시지 수신 및 메시지 콘텐츠에 삽입된 링크의 활성화를 추적할 수 있습니다. 이렇게 하면 수신자가 타겟팅된 게재 작업 이후 수신자의 동작을 추적할 수 있습니다.

추적은 메시지에 적용되지만 웹 추적을 사용하면 수신자가 웹 사이트를 검색하는 방법(페이지 방문, 구매)을 모니터링할 수 있습니다. 웹 추적 구성은 [이 섹션](../../configuration/using/about-web-tracking.md)에 있습니다.

>[!NOTE]
>
>개인화가 포함된 이메일 콘텐츠의 링크에는 특정 구문을 추적해야 합니다. 개인화할 수 있고 추적을 지원하는 이메일에 링크를 추가하는 방법에 대한 자세한 내용은 다음을 참조하십시오 [이 섹션](tracking-personalized-links.md).

에서는 URL을 구분 기호로 묶는 것이 좋습니다 **[!UICONTROL Text content]** 탭을 클릭하여 추적하십시오. 이 탭에 입력하는 URL 구분 기호는 Adobe Campaign에서 문자 문자열 내의 URL을 식별하는 데 사용됩니다. 다음 구분 기호 쌍을 사용할 수 있습니다.
* 괄호 ( )
* 대괄호 [ ]
* 중괄호 { }

이 예에서 URL https://www.adobe.com 뒤에는 세미콜론이 있습니다. 세미콜론은 수신자 이메일 클라이언트가 URL의 일부로 해석할 수 있습니다. 따라서 링크가 끊어질 수 있습니다. 이 문제를 방지하려면 다음 방법 중 하나로 URL을 구분 기호로 묶을 수 있습니다.
* (https://www.adobe.com)
* [https://www.adobe.com];
* {https://www.adobe.com};

메시지 추적은 기본적으로 활성화되어 있습니다. URL을 추적하는 방법을 개인화하려면 아래 단계를 따르십시오.

1. 을(를) 선택합니다 **[!UICONTROL Display URLs]** 옵션을 클릭합니다.

   ![](assets/s_ncs_user_email_del_display_urls.png)

   추적된 URL 목록에서 URL을 선택하면 게재 컨텐츠에서 강조 표시됩니다. 대신 미러 페이지의 링크와 기본적으로 제공되는 구독 취소 링크가 있습니다.

   ![](assets/s_ncs_user_email_del_show_urls.png)

1. 메시지의 각 URL에 대해 추적을 활성화할지 여부를 선택합니다.

   >[!IMPORTANT]
   >
   >링크의 URL을 레이블로 사용하는 경우 피싱으로 인해 거부 위험이 발생하지 않도록 추적을 비활성화하는 것이 좋습니다.
   >
   >예를 들어 www.adobe.com URL이 메시지에 삽입되고 추적 기능이 활성화되면 하이퍼텍스트 링크의 컨텐츠가 https://nlt.adobe.net/r/?id=xxxxxx으로 수정됩니다. 즉, 수신자 메시지 클라이언트가 수신한 메시지를 사기라고 간주할 수 있습니다.

1. 필요한 경우 추적 레이블을 변경하고 레이블을 두 번 클릭하고 새 레이블을 입력합니다.

   >[!NOTE]
   >
   >게재를 추적할 때 추적된 URL 및 레이블의 레이블을 수정하여 정보 읽기를 단순화할 수 있습니다. 클릭 수를 계산할 때 이름이 같은 두 개의 URL 또는 두 개의 레이블이 함께 추가됩니다.

1. 필요한 경우 추적 모드를 변경하고, **[!UICONTROL Tracking]** 아래와 같이 타깃팅된 링크와 일치하는 열입니다.

   ![](assets/s_ncs_user_select_tracking_mode.png)

   각 개별 URL에 대해 추적 모드를 다음 값 중 하나로 설정할 수 있습니다.

   * **[!UICONTROL Enabled]** : 이 URL에서 추적을 활성화합니다.
   * **[!UICONTROL Not tracked]** : 이 URL에 대한 추적을 비활성화합니다.
   * **[!UICONTROL Always enabled]** : 항상 이 URL의 추적을 활성화합니다. 이 정보는 저장되므로 다음에 메시지 콘텐츠에 URL이 다시 표시되면 해당 추적이 자동으로 활성화됩니다.
   * **[!UICONTROL Never tracked]** : 이 URL의 추적을 활성화하지 않습니다. 이 정보는 저장되므로 다음에 URL이 향후 메시지에 다시 표시되면 해당 추적은 자동으로 비활성화됩니다.
   * **[!UICONTROL Opt-out]** : 은 이 URL을 옵트아웃 또는 구독 취소 URL로 간주합니다.
   * **[!UICONTROL Mirror page]** : 는 이 URL이 미러 페이지 URL인 것으로 간주합니다.

1. 또한, **[!UICONTROL Category]** 열. 이러한 카테고리는 다음과 같이 보고서를 표시할 수 있습니다 **[!UICONTROL URLs and click streams]** 자세한 내용은 [이 섹션](../../reporting/using/reports-on-deliveries.md#urls-and-click-streams)). 카테고리는 특정 열거형에 정의됩니다. **[!UICONTROL urlCategory]** 자세한 내용은 [열거형 관리](../../platform/using/managing-enumerations.md)).
