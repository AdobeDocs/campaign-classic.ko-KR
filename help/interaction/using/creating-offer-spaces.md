---
product: campaign
title: 오퍼 공간 만들기
description: 오퍼 공간 만들기
feature: Interaction, Offers
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용됩니다."
audience: interaction
content-type: reference
topic-tags: managing-environments
exl-id: bdda98f7-a083-4f3b-b691-c28ec79af780
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '988'
ht-degree: 1%

---

# 오퍼 공간 만들기{#creating-offer-spaces}



오퍼 공간 만들기는 **기술 관리자** (오퍼 공간 하위 폴더에 대한 액세스 권한 포함) 오퍼 공간은 디자인 환경에서만 만들 수 있으며 오퍼 승인 중에 라이브 환경에 자동으로 복제됩니다.

카탈로그 오퍼의 콘텐츠는 오퍼 공간에 구성됩니다. 기본적으로 콘텐츠에는 다음 필드가 포함될 수 있습니다. **[!UICONTROL Title]**, **[!UICONTROL Destination URL]**, **[!UICONTROL Image URL]**, **[!UICONTROL HTML content]** 및 **[!UICONTROL Text content]**. 오퍼 공간에 필드 시퀀스가 구성되어 있습니다.

고급 매개 변수를 사용하면 연락처 식별 키(예: 다양한 요소, 이름 및 이메일 필드로 동시에 구성할 수 있음)를 지정할 수 있습니다. 자세한 내용은 [식별된 오퍼 표시](../../interaction/using/integration-via-javascript--client-side-.md#presenting-an-identified-offer) 섹션.

HTML 또는 XML 렌더링은 렌더링 함수를 통해 생성됩니다. 렌더링 함수에 정의된 필드의 시퀀스는 콘텐츠에 구성된 시퀀스와 동일해야 합니다.

![](assets/offer_space_create_009.png)

새 오퍼 공간을 만들려면 다음 프로세스를 적용합니다.

1. 오퍼 공간 목록으로 이동한 다음 **[!UICONTROL New]**.

   ![](assets/offer_space_create_001.png)

1. 사용할 채널을 선택하고 오퍼 공간의 레이블을 변경합니다.

   ![](assets/offer_space_create_002.png)

1. 다음 확인: **[!UICONTROL Enable unitary mode]** box를 사용할 수 없습니다.

   * 메시지 센터와 상호 작용을 사용하고 있습니다.
   * 상호 작용의 단일 모드(인바운드 상호 작용)를 사용 중입니다.

1. 로 이동 **[!UICONTROL Content field]** 창에서 클릭 **[!UICONTROL Add]**.

   ![](assets/offer_space_create_003.png)

1. 로 이동 **[!UICONTROL Content]** 노드를 선택하고 다음 순서로 필드를 선택합니다. **[!UICONTROL Title]**, 그런 다음 **[!UICONTROL Image URL]**, 그런 다음 **[!UICONTROL HTML content]**, 그런 다음 **[!UICONTROL Destination URL]**.

   ![](assets/offer_space_create_004.png)

1. 다음 확인: **[!UICONTROL Required]** 각 필드를 필수 항목으로 만드는 상자.

   >[!NOTE]
   >
   >이 구성은 미리보기에서 사용되며 필수 요소 중 하나가 관련 오퍼에서 누락된 경우 게시할 때 오퍼 공백을 유효하지 않게 합니다. 그러나 오퍼가 이미 오퍼 공간에 있는 경우 이러한 기준은 고려되지 않습니다.

   ![](assets/offer_space_create_005.png)

1. 클릭 **[!UICONTROL Edit functions]** 렌더링 함수를 만듭니다.

   이러한 함수는 오퍼 공간에서 오퍼 표시를 생성하는 데 사용됩니다. 아웃바운드 상호 작용의 경우 HTML 또는 텍스트, 인바운드 상호 작용의 경우 XML 등의 몇 가지 형식이 있습니다.

   ![](assets/offer_space_create_006.png)

1. 로 이동 **[!UICONTROL HTML rendering]** 탭하고 선택 **[!UICONTROL Overload the HTML rendering function]**.
1. 렌더링 함수를 삽입합니다.

   ![](assets/offer_space_create_007.png)

필요한 경우 인바운드 상호 작용을 위해 XML 렌더링 함수를 오버로드할 수 있습니다. 아웃바운드 상호 작용에 대해 HTML 및 텍스트 렌더링 함수를 오버로드할 수도 있습니다. 자세한 내용은 다음을 참조하십시오. [인바운드 채널 정보](../../interaction/using/about-inbound-channels.md).

## 오퍼 제안 상태 {#offer-proposition-statuses}

오퍼 제안은 타겟팅된 모집단과의 상호 작용에 따라 다양한 상태를 가질 수 있습니다. 상호 작용은 해당 수명 주기 전반에 걸쳐 오퍼 제안에 적용할 수 있는 값 세트와 함께 제공됩니다. 그러나 오퍼 제안을 만들고 수락할 때 상태가 변경되도록 플랫폼을 구성해야 합니다.

>[!NOTE]
>
>오퍼 제안 상태가 즉시 업데이트되지 않습니다. 매시간 트리거되는 추적 워크플로우에 의해 수행됩니다.

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
>오퍼가 &quot;전송됨&quot; 상태의 게재에 연결된 경우 오퍼 제안 상태가 자동으로 &quot;표시됨&quot;으로 변경됩니다.

### 제안 생성 시 상태 구성 {#configuring-the-status-when-the-proposition-is-created}

상호 작용 엔진에서 오퍼 제안을 만들면 오퍼 제안 상태가 인바운드 상호 작용이든 아웃바운드 상호 작용이든 변경됩니다. 이 두 값 간의 선택은 오퍼가 **[!UICONTROL Design]** 환경

오퍼 보고서에 표시할 정보에 따라 각 공간에 대해 제안이 생성될 때 적용할 상태를 구성할 수 있습니다.

이렇게 하려면 다음 프로세스를 사용합니다.

1. 로 이동 **[!UICONTROL Storage]** 원하는 스페이스의 탭입니다.
1. 제안 생성 시 제안에 적용할 상태를 선택합니다.

   ![](assets/offer_update_status_001.png)

### 제안이 수락될 때의 상태 구성 {#configuring-the-status-when-the-proposition-is-accepted}

오퍼 제안이 수락되면 기본적으로 제공되는 값 중 하나를 사용하여 제안의 새 상태를 구성할 수 있습니다. 업데이트는 수신자가 상호 작용 엔진을 호출하는 오퍼의 링크를 클릭하는 경우 적용됩니다.

이렇게 하려면 다음 프로세스를 사용합니다.

1. 로 이동 **[!UICONTROL Storage]** 원하는 스페이스의 탭입니다.
1. 제안이 수락될 때 적용할 상태를 선택합니다.

   ![](assets/offer_update_status_002.png)

**인바운드 상호 작용**

다음 **[!UICONTROL Storage]** 탭을 사용하여 다음 상태를 정의할 수 있습니다. **제안됨** 및 **수락됨** 오퍼 제안만. 인바운드 상호 작용의 경우 인터페이스를 통해서가 아니라 오퍼 엔진을 호출하기 위한 URL에 오퍼 제안 상태를 직접 지정해야 합니다. 이렇게 하면 오퍼 제안이 거부되는 등의 다른 경우에 적용할 상태를 지정할 수 있습니다.

```
<BASE_URL>?a=UpdateStatus&p=<PRIMARY_KEY_OF_THE_PROPOSITION>&st=<NEW_STATUS_OF_THE_PROPOSITION>&r=<REDIRECT_URL>
```

예: 제안(식별자) **40004**)와 일치하는 **주택 보험** 오퍼가에 표시됨 **Neobank** 사이트에는 다음 URL이 포함됩니다.

```
<BASE_URL>?a=UpdateStatus&p=<40004>&st=<3>&r=<"http://www.neobank.com/insurance/subscribe.html">
```

방문자가 오퍼를 클릭하여 URL인 **[!UICONTROL Accepted]** 상태(값) **3**)이 제안에 적용되고 방문자는 의 새 페이지로 리디렉션됩니다. **Neobank** 보험 계약을 체결할 장소.

>[!NOTE]
>
>URL에 다른 상태를 지정하려면(예: 오퍼 제안이 거부된 경우) 원하는 상태에 해당하는 값을 사용하십시오. 예: **[!UICONTROL Rejected]** = &quot;5&quot;, **[!UICONTROL Presented]** = &quot;1&quot; 등입니다.
>
>상태 및 해당 값은 **[!UICONTROL Offer propositions (nms)]** 데이터 스키마. 자세한 정보는 이 [페이지](../../configuration/using/data-schemas.md)를 참조하십시오.

**아웃바운드 상호 작용**

아웃바운드 상호 작용의 경우 다음을 자동으로 적용할 수 있습니다 **[!UICONTROL Interested]** 게재에 링크가 포함된 경우 오퍼 제안에 대한 상태. 간단히 추가 **_urlType=&quot;11&quot;** 링크의 값:

```
<a _urlType="11" href="<DEST_URL>">Link inserted into the delivery</a>
```

## 공간별 오퍼 미리보기 {#offer-preview-per-space}

이 탭에서는 선택한 방법을 통해 수신자가 적격한 오퍼를 볼 수 있습니다. 아래 예에서 수신자는 메일을 통해 3개의 오퍼 제안을 받을 수 있습니다.

![](assets/offer_space_overview_002.png)

수신자가 오퍼에 적합하지 않은 경우 미리보기에 표시됩니다.

![](assets/offer_space_overview_001.png)

컨텍스트가 공백으로 제한되면 미리보기에서 해당 컨텍스트를 무시할 수 있습니다. 이는 인바운드 채널을 사용하여 공간에서 참조된 필드를 추가하기 위해 상호 작용 스키마를 확장한 경우입니다(자세한 내용은 다음을 참조하십시오.) [확장 예제](../../interaction/using/extension-example.md)).
