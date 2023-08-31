---
product: campaign
title: 추적되는 링크를 구성하는 방법
description: 추적되는 링크를 구성하는 방법
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Monitoring
role: User, Developer
exl-id: ed88e1d6-c0d5-4a85-9f3e-be670f4bcc10
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 10%

---

# 추적되는 링크를 구성하는 방법{#how-to-configure-tracked-links}



각 게재에 대해 메시지 수신 및 메시지 콘텐츠에 삽입된 링크의 활성화를 추적할 수 있습니다. 이렇게 하면 수신자가 타겟팅된 게재 작업 이후 수신자의 동작을 추적할 수 있습니다.

추적은 메시지에 적용되지만 웹 추적은 수신자가 웹 사이트를 탐색하는 방법(방문한 페이지, 구매)을 모니터링할 수 있습니다. 웹 추적 구성은 [이 섹션](../../configuration/using/about-web-tracking.md)에 있습니다.

>[!NOTE]
>
>개인화가 포함된 이메일 콘텐츠의 링크는 추적할 특정 구문이 필요합니다. 개인화할 수 있고 추적을 지원하는 이메일에 링크를 추가하는 방법에 대한 자세한 내용은 을 참조하십시오. [이 섹션](tracking-personalized-links.md).

에 URL을 구분 기호로 묶는 것이 좋습니다. **[!UICONTROL Text content]** 추적 공식을 적용하기 전의 탭입니다. 이 탭에 입력하는 URL 구분 기호는 Adobe Campaign에서 문자 문자열 내에서 URL을 식별하는 데 사용됩니다. 다음 구분 기호 쌍을 사용할 수 있습니다.
* 괄호( )
* 대괄호 [ ]
* 중괄호 { }

이 예제에서는 URL https://www.adobe.com 뒤에 세미콜론이 옵니다. 세미콜론은 수신자 이메일 클라이언트들에 의해 URL의 일부로서 해석될 수 있다. 그 결과 링크가 끊어질 수 있습니다. 이 문제를 방지하려면 다음 방법 중 하나로 URL을 구분 기호로 묶을 수 있습니다.
* (https://www.adobe.com);
* [https://www.adobe.com];
* {https://www.adobe.com};

메시지 추적은 기본적으로 활성화되어 있습니다. URL을 추적하는 방법을 개인화하려면 아래 단계를 따르십시오.

1. 다음 항목 선택 **[!UICONTROL Display URLs]** 게재 마법사의 메시지 내용 아래에 있는 옵션입니다.

   ![](assets/s_ncs_user_email_del_display_urls.png)

   추적된 URL 목록에서 URL을 선택하면 게재 콘텐츠에서 강조 표시됩니다. 단, 미러 페이지의 링크 및 기본적으로 제공되는 구독 취소 링크는 예외입니다.

   ![](assets/s_ncs_user_email_del_show_urls.png)

1. 메시지의 각 URL에 대해 추적을 활성화할지 여부를 선택합니다.

   >[!IMPORTANT]
   >
   >링크의 URL을 레이블로 사용할 경우 피싱으로 인한 거부 위험을 방지하기 위해 추적을 비활성화하는 것이 좋습니다.
   >
   >예를 들어 www.adobe.com URL이 메시지에 삽입되고 해당 URL에서 추적이 활성화되면 하이퍼텍스트 링크의 콘텐츠가 https://nlt.adobe.net/r/?id=xxxxxx으로 수정됩니다. 이는 수신자 메시지 클라이언트에 의해 사기라고 간주될 수 있음을 의미한다.

1. 필요한 경우 추적 레이블을 변경하고 레이블을 두 번 클릭한 다음 새 레이블을 입력합니다.

   >[!NOTE]
   >
   >게재 추적 시 정보 읽기를 간소화하도록 추적된 URL의 레이블과 레이블을 수정할 수 있습니다. 클릭 수를 계산할 때 이름이 같은 URL 두 개 또는 레이블 두 개가 함께 추가됩니다.

1. 필요한 경우 추적 모드를 변경하고 **[!UICONTROL Tracking]** 아래 표시된 대로 타겟팅된 링크와 일치하는 열:

   ![](assets/s_ncs_user_select_tracking_mode.png)

   각 개별 URL에 대해 추적 모드를 다음 값 중 하나로 설정할 수 있습니다.

   * **[!UICONTROL Enabled]** : 이 URL에 대한 추적을 활성화합니다.
   * **[!UICONTROL Not tracked]** : 이 URL에 대한 추적을 비활성화합니다.
   * **[!UICONTROL Always enabled]** : 항상 이 URL의 추적을 활성화합니다. 이 정보는 다음에 URL이 향후 메시지 콘텐츠에 다시 나타나는 경우 해당 추적이 자동으로 활성화되도록 저장됩니다.
   * **[!UICONTROL Never tracked]** : 이 URL 추적을 활성화하지 않습니다. 이 정보는 다음에 URL이 향후 메시지에 다시 나타나는 경우 해당 추적이 자동으로 비활성화되도록 저장됩니다.
   * **[!UICONTROL Opt-out]** : 이 URL을 옵트아웃 또는 구독 취소 URL로 간주합니다.
   * **[!UICONTROL Mirror page]** : 이 URL을 미러 페이지 URL로 간주합니다.

1. 또한 의 드롭다운 목록에서 각 추적된 URL에 대한 카테고리를 선택할 수 있습니다. **[!UICONTROL Category]** 열. 이러한 범주는 다음과 같이 보고서에 표시될 수 있습니다. **[!UICONTROL URLs and click streams]** (참조 [이 섹션](../../reporting/using/reports-on-deliveries.md#urls-and-click-streams)). 범주는 특정 열거형에 정의됩니다. **[!UICONTROL urlCategory]** (참조 [열거형 관리](../../platform/using/managing-enumerations.md)).
