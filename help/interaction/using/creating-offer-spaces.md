---
solution: Campaign Classic
product: campaign
title: 오퍼 공간 만들기
description: 오퍼 공간 만들기
audience: interaction
content-type: reference
topic-tags: managing-environments
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 1%

---


# 오퍼 공간 만들기{#creating-offer-spaces}

오퍼 공간 만들기는 오퍼 공간 하위 폴더에 액세스할 수 있는 **기술 관리자만** 수행할 수 있습니다. 오퍼 공간은 디자인 환경에서만 만들 수 있으며 오퍼 승인 동안 라이브 환경에 자동으로 복제됩니다.

카탈로그 오퍼의 컨텐츠는 오퍼 공간에 구성됩니다. 기본적으로 컨텐츠에는 다음 필드가 포함될 수 있습니다. **[!UICONTROL Title]**, **[!UICONTROL Destination URL]**, **[!UICONTROL Image URL]**, **[!UICONTROL HTML content]** and **[!UICONTROL Text content]**&#x200B;를 참조하십시오. 필드 시퀀스는 오퍼 공간에 구성됩니다.

고급 매개 변수를 사용하면 연락처 식별 키(예: 이름 및 이메일 필드)를 동시에 지정할 수 있습니다. 자세한 내용은 식별된 오퍼 [표시 섹션을](../../interaction/using/integration-via-javascript--client-side-.md#presenting-an-identified-offer) 참조하십시오.

HTML 또는 XML 렌더링은 렌더링 함수를 통해 만들어집니다. 렌더링 함수에 정의된 필드의 시퀀스는 컨텐츠에 구성된 시퀀스와 동일해야 합니다.

![](assets/offer_space_create_009.png)

새 오퍼 공간을 만들려면 다음 프로세스를 적용합니다.

1. 오퍼 공간 목록으로 이동하여 을 클릭합니다 **[!UICONTROL New]**.

   ![](assets/offer_space_create_001.png)

1. 사용할 채널을 선택하고 오퍼 공간의 레이블을 변경합니다.

   ![](assets/offer_space_create_002.png)

1. 다음 **[!UICONTROL Enable unitary mode]** 사례 중 하나가 적용되는 경우 상자를 선택합니다.

   * 메시지 센터에서 상호 작용을 사용하고 있습니다.
   * 상호 작용의 단일 모드(인바운드 상호 작용)를 사용하고 있습니다.

1. 창으로 **[!UICONTROL Content field]** 가서 을 클릭합니다 **[!UICONTROL Add]**.

   ![](assets/offer_space_create_003.png)

1. 노드로 **[!UICONTROL Content]** 이동하고 다음 순서로 필드를 선택합니다. **[!UICONTROL Title]**, **[!UICONTROL Image URL]** then **[!UICONTROL HTML content]**, then **[!UICONTROL Destination URL]**.

   ![](assets/offer_space_create_004.png)

1. 각 필드를 필수 **[!UICONTROL Required]** 필드로 지정하려면 확인란을 선택합니다.

   >[!NOTE]
   >
   >이 구성은 미리 보기에서 사용되며, 해당 오퍼에서 필수 요소 중 하나가 누락된 경우 게시할 때 오퍼 공백이 잘못되었습니다. 하지만 오퍼가 이미 오퍼 공간에 존재하는 경우 이러한 기준을 고려하지 않습니다.

   ![](assets/offer_space_create_005.png)

1. 을 **[!UICONTROL Edit functions]** 클릭하여 렌더링 함수를 만듭니다.

   이러한 기능은 오퍼 공간에서 오퍼 표현을 생성하는 데 사용됩니다. 다음과 같은 몇 가지 형식을 사용할 수 있습니다.아웃바운드 상호 작용과 인바운드 상호 작용에 대한 HTML 또는 텍스트.

   ![](assets/offer_space_create_006.png)

1. 탭으로 **[!UICONTROL HTML rendering]** 가서 선택합니다 **[!UICONTROL Overload the HTML rendering function]**.
1. 렌더링 함수를 삽입합니다.

   ![](assets/offer_space_create_007.png)

필요한 경우 인바운드 상호 작용에 대한 XML 렌더링 함수를 오버로드할 수 있습니다. 아웃바운드 상호 작용에 대해 HTML 및 텍스트 렌더링 기능을 오버로드할 수도 있습니다. 자세한 내용은 인바운드 채널 [정보를 참조하십시오](../../interaction/using/about-inbound-channels.md).

## 제안 상태 {#offer-proposition-statuses}

제안 제안은 타깃팅된 모집단과의 상호 작용에 따라 다양한 상태를 가질 수 있습니다. 상호 작용은 라이프 사이클 동안 제안 제안에 적용할 수 있는 일련의 값들과 함께 제공됩니다. 그러나, 제안 제안이 만들어지고 수락될 때 상태가 변경되도록 플랫폼을 구성해야 합니다.

>[!NOTE]
>
>제안 제안의 상태는 즉시 업데이트되지 않습니다. 이것은 매 시간마다 실행되는 추적 워크플로우에 의해 수행됩니다.

### 상태 목록 {#status-list}

상호 작용은 제안 제안 상태를 평가하는 데 사용할 수 있는 다음 값들과 함께 제공됩니다.

* **[!UICONTROL Accepted]**.
* **[!UICONTROL Scheduled]**.
* **[!UICONTROL Generated]**.
* **[!UICONTROL Interested]**.
* **[!UICONTROL Presented]**.
* **[!UICONTROL Rejected]**.

이러한 값은 기본적으로 적용되지 않습니다.구성해야 합니다.

>[!NOTE]
>
>오퍼가 &quot;전송&quot; 상태의 게재와 연결된 경우 제안 제안의 상태는 자동으로 &quot;제안&quot;으로 변경됩니다.

### 제안을 만들 때 상태 구성 {#configuring-the-status-when-the-proposition-is-created}

상호 작용 엔진에서 제안 제안이 생성되면 내부 상호 작용인지 아웃바운드 상호 작용인지 여부 상태가 변경됩니다. 이 두 값 간의 선택은 오퍼가 환경에서 구성되는 방식에 따라 **[!UICONTROL Design]** 달라집니다

각 공간에 대해 제안 보고서에 표시할 정보에 따라 제안을 만들 때 적용할 상태를 구성할 수 있습니다.

이렇게 하려면 다음 프로세스를 사용하십시오.

1. 원하는 공간의 **[!UICONTROL Storage]** 탭으로 이동합니다.
1. 제안을 만들 때 해당 제안에 적용할 상태를 선택합니다.

   ![](assets/offer_update_status_001.png)

### 제안을 수락할 때 상태 구성 {#configuring-the-status-when-the-proposition-is-accepted}

제안 제안이 수락되면, 기본적으로 제공된 값 중 하나를 사용하여 제안의 새로운 상태를 구성할 수 있습니다. 이 업데이트는 수신자가 오퍼의 링크를 클릭하는 경우에 효과적이며, 이 링크를 클릭하면 상호 작용 엔진이 호출됩니다.

이렇게 하려면 다음 프로세스를 사용하십시오.

1. 원하는 공간의 **[!UICONTROL Storage]** 탭으로 이동합니다.
1. 제안을 수락할 때 해당 제안에 적용할 상태를 선택합니다.

   ![](assets/offer_update_status_002.png)

**인바운드 상호 작용**

탭 **[!UICONTROL Storage]** 을 사용하면 제안 및 **수락된** 오퍼 **제안** 상태에 대한 상태만정의할수 있습니다. 인바운드 상호 작용의 경우, 오퍼 엔진 호출을 위해 인터페이스가 아닌 URL에서 오퍼 제안 상태를 직접 지정해야 합니다. 이렇게 하면 제안 제안이 거부되는 경우 등 다른 경우에 적용할 상태를 지정할 수 있습니다.

```
<BASE_URL>?a=UpdateStatus&p=<PRIMARY_KEY_OF_THE_PROPOSITION>&st=<NEW_STATUS_OF_THE_PROPOSITION>&r=<REDIRECT_URL>
```

예를 들어 Neobank **사이트에 표시되는**&#x200B;홈 보험 **오퍼와 일치하는 제안(식별자** 40004 **)에는** 다음 URL이포함되어 있습니다.

```
<BASE_URL>?a=UpdateStatus&p=<40004>&st=<3>&r=<"http://www.neobank.com/insurance/subscribe.html">
```

방문자가 오퍼를 클릭하고 따라서 URL을 클릭하는 즉시 상태(값 **[!UICONTROL Accepted]** 3 **)가 제안에 적용되며 방문자는**&#x200B;뉴뱅크 **사이트의 새 페이지로 리디렉션되어 보험 계약을** 해지하게 됩니다.

>[!NOTE]
>
>URL에서 다른 상태를 지정하려면(예: 제안 제안이 거부되는 경우) 원하는 상태에 해당하는 값을 사용합니다. 예: **[!UICONTROL Rejected]** = &quot;5&quot;, **[!UICONTROL Presented]** = &quot;1&quot; 등.
>
>상태 및 해당 값은 **[!UICONTROL Offer propositions (nms)]** 데이터 스키마에서 검색할 수 있습니다. 자세한 정보는 이 [페이지](../../configuration/using/data-schemas.md)를 참조하십시오.

**아웃바운드 상호 작용**

아웃바운드 상호 작용의 경우 게재에 링크가 들어 있을 때 **[!UICONTROL Interested]** 상태를 제안 제안에 자동으로 적용할 수 있습니다. 링크에 **_urlType=&quot;11&quot;** 값을 추가하면 됩니다.

```
<a _urlType="11" href="<DEST_URL>">Link inserted into the delivery</a>
```

## 공간당 오퍼 미리 보기 {#offer-preview-per-space}

이 탭에서 선택한 방법을 통해 수신자가 사용할 수 있는 오퍼를 볼 수 있습니다. 아래 예에서 수신자는 3개의 제안을 우편으로 받을 수 있습니다.

![](assets/offer_space_overview_002.png)

수신자가 오퍼에 적합하지 않으면 미리 보기에 표시됩니다.

![](assets/offer_space_overview_001.png)

공백으로 제한된 경우 미리 보기는 컨텍스트를 무시할 수 있습니다. 이것은 상호 작용 스키마가 인바운드 채널을 사용하여 공간에서 참조된 필드를 추가하도록 확장되었을 때 발생합니다(자세한 내용은 [확장 예제](../../interaction/using/extension-example.md)참조).
