---
product: campaign
title: 오퍼 공간 만들기
description: 오퍼 공간 만들기
audience: interaction
content-type: reference
topic-tags: managing-environments
exl-id: bdda98f7-a083-4f3b-b691-c28ec79af780
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 1%

---

# 오퍼 공간 만들기{#creating-offer-spaces}

![](../../assets/v7-only.svg)

오퍼 공간 만들기는 **기술 관리자** 오퍼 공간 하위 폴더에 대한 액세스 권한 사용. 오퍼 공간은 디자인 환경에서만 만들 수 있으며, 오퍼 승인 중에 라이브 환경에 자동으로 복제됩니다.

카탈로그 오퍼의 컨텐츠는 오퍼 공간에 구성됩니다. 기본적으로 컨텐츠에는 다음 필드가 포함될 수 있습니다. **[!UICONTROL Title]**, **[!UICONTROL Destination URL]**, **[!UICONTROL Image URL]**, **[!UICONTROL HTML content]** 및 **[!UICONTROL Text content]**. 필드 시퀀스는 오퍼 공간에서 구성됩니다.

고급 매개 변수를 사용하면 연락처 식별 키(예: 이름 및 이메일 필드)를 동시에 지정할 수 있습니다. 자세한 내용은 [식별된 오퍼 표시](../../interaction/using/integration-via-javascript--client-side-.md#presenting-an-identified-offer) 섹션을 참조하십시오.

렌더링 함수를 통해 HTML 또는 XML 렌더링이 만들어집니다. 렌더링 함수에 정의된 필드의 시퀀스는 컨텐츠에 구성된 시퀀스와 동일해야 합니다.

![](assets/offer_space_create_009.png)

새 오퍼 공간을 만들려면 다음 프로세스를 적용합니다.

1. 오퍼 공간 목록으로 이동한 후 를 클릭합니다 **[!UICONTROL New]**.

   ![](assets/offer_space_create_001.png)

1. 사용할 채널을 선택하고 오퍼 공간의 레이블을 변경합니다.

   ![](assets/offer_space_create_002.png)

1. 을(를) 확인합니다. **[!UICONTROL Enable unitary mode]** 다음 사례 중 하나가 적용되는 경우 상자를 선택합니다.

   * 메시지 센터와 상호 작용을 사용하고 있습니다
   * 상호 작용의 단일 모드(인바운드 상호 작용)를 사용하고 있습니다

1. 로 이동합니다. **[!UICONTROL Content field]** 을(를) 클릭하고 **[!UICONTROL Add]**.

   ![](assets/offer_space_create_003.png)

1. 로 이동합니다. **[!UICONTROL Content]** 노드 및 다음 순서로 필드를 선택합니다. **[!UICONTROL Title]**, 그런 다음 **[!UICONTROL Image URL]**, 그런 다음 **[!UICONTROL HTML content]**, 그런 다음 **[!UICONTROL Destination URL]**.

   ![](assets/offer_space_create_004.png)

1. 을(를) 확인합니다. **[!UICONTROL Required]** 상자를 사용하여 각 필드를 필수로 지정합니다.

   >[!NOTE]
   >
   >이 구성은 미리 보기에서 사용되며, 관련 오퍼에서 필수 요소 중 하나가 누락된 경우 게시할 때 오퍼 공간이 유효하지 않게 됩니다. 그러나 오퍼가 이미 오퍼 공간에서 라이브 상태인 경우, 이러한 기준은 고려되지 않습니다.

   ![](assets/offer_space_create_005.png)

1. 클릭 **[!UICONTROL Edit functions]** 렌더링 함수를 만들려면 다음을 수행하십시오.

   이러한 함수는 오퍼 공간에 대한 오퍼 표현을 생성하는 데 사용됩니다. 다음과 같은 몇 가지 가능한 형식이 있습니다. 아웃바운드 상호 작용과 인바운드 상호 작용을 위한 XML에 대한 HTML 또는 텍스트입니다.

   ![](assets/offer_space_create_006.png)

1. 로 이동합니다. **[!UICONTROL HTML rendering]** 탭을 선택하고 **[!UICONTROL Overload the HTML rendering function]**.
1. 렌더링 함수를 삽입합니다.

   ![](assets/offer_space_create_007.png)

필요한 경우 인바운드 상호 작용에 대해 XML 렌더링 함수를 오버로드할 수 있습니다. 아웃바운드 상호 작용에 대해 HTML 및 텍스트 렌더링 함수를 오버로드할 수도 있습니다. 자세한 내용은 [인바운드 채널 정보](../../interaction/using/about-inbound-channels.md).

## 오퍼 제안 상태 {#offer-proposition-statuses}

오퍼 제안은 타겟팅된 모집단과의 상호 작용에 따라 다양한 상태를 가질 수 있습니다. 상호 작용은 라이프 사이클 동안 오퍼 제안에 적용할 수 있는 값 집합과 함께 제공됩니다. 그러나 오퍼 제안을 만들고 수락할 때 상태가 변경되도록 플랫폼을 구성해야 합니다.

>[!NOTE]
>
>오퍼 제안 상태가 즉시 업데이트되지 않습니다. 매시간마다 트리거되는 추적 워크플로우에 의해 수행됩니다.

### 상태 목록 {#status-list}

상호 작용은 오퍼 제안 상태를 평가하는 데 사용할 수 있는 다음 값과 함께 제공됩니다.

* **[!UICONTROL Accepted]**.
* **[!UICONTROL Scheduled]**.
* **[!UICONTROL Generated]**.
* **[!UICONTROL Interested]**.
* **[!UICONTROL Presented]**.
* **[!UICONTROL Rejected]**.

이러한 값은 기본적으로 적용되지 않습니다. 구성해야 합니다.

>[!NOTE]
>
>오퍼가 &quot;전송됨&quot; 상태가 있는 게재에 연결된 경우 오퍼 제안 상태가 자동으로 &quot;제공됨&quot;으로 변경됩니다.

### 제안을 만들 때 상태 구성 {#configuring-the-status-when-the-proposition-is-created}

상호 작용 엔진에 의해 오퍼 제안을 만들면 상태가 변경되며 이것은 인바운드 또는 아웃바운드 상호 작용인지 입니다. 이 두 값 간의 선택은 **[!UICONTROL Design]** 환경

각 공간에 대해 제안 생성 시 적용할 상태를 오퍼 보고서에 표시할 정보에 따라 구성할 수 있습니다.

이렇게 하려면 다음 프로세스를 사용합니다.

1. 로 이동합니다. **[!UICONTROL Storage]** 원하는 공간의 탭.
1. 제안 생성 시 해당 제안에 적용할 상태를 선택합니다.

   ![](assets/offer_update_status_001.png)

### 제안이 수락될 때 상태 구성 {#configuring-the-status-when-the-proposition-is-accepted}

제안 제안이 수락되면 기본적으로 제공되는 값 중 하나를 사용하여 제안 상태의 새 상태를 구성할 수 있습니다. 이 업데이트는 수신자가 상호 작용 엔진을 호출하는 오퍼의 링크를 클릭할 때 효과적입니다.

이렇게 하려면 다음 프로세스를 사용합니다.

1. 로 이동합니다. **[!UICONTROL Storage]** 원하는 공간의 탭.
1. 제안 승인 시 해당 제안을 적용할 상태를 선택합니다.

   ![](assets/offer_update_status_002.png)

**인바운드 상호 작용**

다음 **[!UICONTROL Storage]** 탭에서는 상태를 정의할 수 있습니다 **제안** 및 **허용** 오퍼 프로필만 제공합니다. 인바운드 상호 작용의 경우 인터페이스를 통해서가 아니라 오퍼 엔진 호출을 위해 URL에 오퍼 제안 상태를 직접 지정해야 합니다. 이 방법으로, 예를 들어 오퍼 제안이 거부되는 경우 등 다른 경우에 적용할 상태를 지정할 수 있습니다.

```
<BASE_URL>?a=UpdateStatus&p=<PRIMARY_KEY_OF_THE_PROPOSITION>&st=<NEW_STATUS_OF_THE_PROPOSITION>&r=<REDIRECT_URL>
```

예를 들어, 제안(식별자) **40004**)에 사용할 수 있습니다. **주택 보험** 에 표시되는 오퍼 **뉴뱅크** 사이트에는 다음 URL이 포함되어 있습니다.

```
<BASE_URL>?a=UpdateStatus&p=<40004>&st=<3>&r=<"http://www.neobank.com/insurance/subscribe.html">
```

방문자가 오퍼를 클릭하는 즉시 따라서 URL은 **[!UICONTROL Accepted]** 상태(값) **3**)이 제안에 적용되며 방문자는 페이지의 새 페이지로 리디렉션됩니다 **뉴뱅크** 보험 계약을 따내기 위한 현장.

>[!NOTE]
>
>URL에 다른 상태를 지정하려면(예: 오퍼 제안이 거부되는 경우) 원하는 상태에 해당하는 값을 사용하십시오. 예: **[!UICONTROL Rejected]** = &quot;5&quot;, **[!UICONTROL Presented]** = &quot;1&quot; 등.
>
>상태 및 값은 **[!UICONTROL Offer propositions (nms)]** 데이터 스키마. 자세한 정보는 이 [페이지](../../configuration/using/data-schemas.md)를 참조하십시오.

**아웃바운드 상호 작용**

아웃바운드 상호 작용의 경우 **[!UICONTROL Interested]** 게재에 링크가 포함되어 있을 때 제안 제안 상태에 있는 상태. 간단히 을(를) 추가합니다 **_urlType=&quot;11&quot;** 값을 링크에 추가합니다.

```
<a _urlType="11" href="<DEST_URL>">Link inserted into the delivery</a>
```

## 공간당 오퍼 미리 보기 {#offer-preview-per-space}

이 탭에서는 선택한 방법을 통해 수신자가 자격이 있는 오퍼를 볼 수 있습니다. 아래 예에서는 수신자는 메일을 통해 세 개의 오퍼 제안을 받을 수 있습니다.

![](assets/offer_space_overview_002.png)

수신자가 오퍼에 적합하지 않으면 미리 보기에 표시됩니다.

![](assets/offer_space_overview_001.png)

공백으로 제한될 때 미리 보기는 컨텍스트를 무시할 수 있습니다. 이는 상호 작용 스키마가 확장되어 인바운드 채널을 사용하여 스페이스에서 참조되는 필드를 추가하는 경우입니다(자세한 내용은 다음을 참조하십시오) [확장 예제](../../interaction/using/extension-example.md)).
