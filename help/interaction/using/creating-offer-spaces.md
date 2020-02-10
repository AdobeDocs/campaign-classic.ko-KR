---
title: 오퍼 공간 만들기
seo-title: 오퍼 공간 만들기
description: 오퍼 공간 만들기
seo-description: null
page-status-flag: never-activated
uuid: 2ad38697-db14-4dc0-abb8-9b71d57e0e35
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-environments
discoiquuid: 0fae2149-0980-466d-ac9e-8afec2e278be
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 215e4d1ca78938b38b53cae0357612deebf7727b

---


# 오퍼 공간 만들기{#creating-offer-spaces}

오퍼 공간 생성은 오퍼 공간 하위 폴더에 대한 액세스 권한이 있는 **기술 관리자만** 수행할 수 있습니다. 오퍼 공간은 디자인 환경에서만 만들 수 있으며 오퍼 승인 중에 라이브 환경에 자동으로 복제됩니다.

카탈로그 오퍼의 컨텐츠는 오퍼 공간에 구성됩니다. 기본적으로 컨텐츠에는 다음 필드가 포함될 수 있습니다. **[!UICONTROL Title]**&#x200B;및 **[!UICONTROL Destination URL]****[!UICONTROL Image URL]**&#x200B;를 **[!UICONTROL HTML content]** 선택합니다 **[!UICONTROL Text content]**. 필드 시퀀스는 오퍼 공간에 구성됩니다.

고급 매개 변수를 사용하면 연락처 식별 키(예: 이름 및 이메일 필드)를 동시에 지정할 수 있습니다. 자세한 내용은 식별된 오퍼 [표시](../../interaction/using/integration-via-javascript--client-side-.md#presenting-an-identified-offer) 섹션을 참조하십시오.

HTML 또는 XML 렌더링은 렌더링 함수를 통해 만들어집니다. 렌더링 함수에 정의된 필드의 시퀀스는 컨텐츠에 구성된 시퀀스와 동일해야 합니다.

![](assets/offer_space_create_009.png)

새 오퍼 공간을 만들려면 다음 프로세스를 적용합니다.

1. 오퍼 공간 목록으로 이동하여 을 클릭합니다 **[!UICONTROL New]**.

   ![](assets/offer_space_create_001.png)

1. 사용할 채널을 선택하고 오퍼 공간의 레이블을 변경합니다.

   ![](assets/offer_space_create_002.png)

1. 다음 사례 중 하나가 적용되는 경우 **[!UICONTROL Enable unitary mode]** 상자를 선택합니다.

   * 메시지 센터에서 상호 작용을 사용하고 있습니다.
   * 상호 작용의 단일 모드(인바운드 상호 작용)를 사용하고 있습니다.

1. 창으로 **[!UICONTROL Content field]** 이동하여 을 클릭합니다 **[!UICONTROL Add]**.

   ![](assets/offer_space_create_003.png)

1. 노드를 **[!UICONTROL Content]** 선택하고 다음 순서로 필드를 선택합니다. **[!UICONTROL Title]**&#x200B;그럼 **[!UICONTROL Image URL]**&#x200B;그 **[!UICONTROL HTML content]**&#x200B;다음에 **[!UICONTROL Destination URL]**&#x200B;주세요

   ![](assets/offer_space_create_004.png)

1. 각 필드를 필수 필드로 만들려면 **[!UICONTROL Required]** 확인란을 선택합니다.

   >[!NOTE]
   >
   >이 구성은 미리 보기에서 사용되며 관련 오퍼에서 필수 요소 중 하나가 누락된 경우 게시할 때 오퍼 공백이 잘못되었습니다. 하지만 오퍼가 이미 오퍼 공간에서 라이브된 경우 이러한 기준을 고려하지는 않습니다.

   ![](assets/offer_space_create_005.png)

1. 을 **[!UICONTROL Edit functions]** 클릭하여 렌더링 함수를 만듭니다.

   이러한 함수는 오퍼 공간에서 오퍼 표현을 생성하는 데 사용됩니다. 다음과 같은 몇 가지 형식을 사용할 수 있습니다.아웃바운드 인터랙션 및 인바운드 인터랙션을 위한 HTML 또는 텍스트.

   ![](assets/offer_space_create_006.png)

1. 탭으로 이동한 후 **[!UICONTROL HTML rendering]** 선택합니다 **[!UICONTROL Overload the HTML rendering function]**.
1. 렌더링 기능을 삽입합니다.

   ![](assets/offer_space_create_007.png)

필요한 경우 인바운드 상호 작용에 대한 XML 렌더링 함수를 오버로드할 수 있습니다. 아웃바운드 상호 작용에 대해 HTML 및 텍스트 렌더링 함수를 오버로드할 수도 있습니다. 자세한 내용은 인바운드 [채널](../../interaction/using/about-inbound-channels.md)정보를 참조하십시오.

## 제안 상태 {#offer-proposition-statuses}

제안 제안에는 타깃팅된 모집단과의 상호 작용에 따라 다양한 상태가 있을 수 있습니다. 상호 작용은 라이프 사이클 동안 제안 제안에 적용할 수 있는 값 집합과 함께 제공됩니다. 하지만, 오퍼 제안이 만들어지고 수락될 때 상태가 변경되도록 플랫폼을 구성해야 합니다.

>[!NOTE]
>
>제안 제안의 상태는 즉시 업데이트되지 않습니다. 이것은 매 시간마다 트리거되는 추적 워크플로우에 의해 수행됩니다.

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
>오퍼가 &quot;전송&quot; 상태의 게재와 연결된 경우 제안 제안의 상태가 자동으로 &quot;제시됨&quot;으로 변경됩니다.

### 제안을 만들 때 상태 구성 {#configuring-the-status-when-the-proposition-is-created}

상호 작용 엔진에서 오퍼 제안이 생성되면 내부 상호 작용인지 아웃바운드 상호 작용인지 여부가 변경됩니다. 이러한 두 값 중 선택은 **[!UICONTROL Design]** 환경에서 오퍼 공간이 구성되는 방식에 따라 달라집니다

각 공간에 대해 제안 보고서에 표시할 정보에 따라 제안을 만들 때 적용할 상태를 구성할 수 있습니다.

이렇게 하려면 다음 프로세스를 사용하십시오.

1. 원하는 공간의 **[!UICONTROL Storage]** 탭으로 이동합니다.
1. 제안을 만들 때 해당 제안에 적용할 상태를 선택합니다.

   ![](assets/offer_update_status_001.png)

### 제안이 수락될 때 상태 구성 {#configuring-the-status-when-the-proposition-is-accepted}

제안 제안이 수락되면 기본적으로 제공되는 값 중 하나를 사용하여 제안의 새 상태를 구성할 수 있습니다. 이 업데이트는 수신자가 오퍼의 링크를 클릭하여 상호 작용 엔진을 호출하는 경우에 적용됩니다.

이렇게 하려면 다음 프로세스를 사용하십시오.

1. 원하는 공간의 **[!UICONTROL Storage]** 탭으로 이동합니다.
1. 제안이 수락될 때 해당 제안에 적용할 상태를 선택합니다.

   ![](assets/offer_update_status_002.png)

**인바운드 상호 작용**

이 **[!UICONTROL Storage]** 탭에서는 **제안된** 및 **수락된** 오퍼제안의 상태만 정의할 수 있습니다. 인바운드 상호 작용의 경우 오퍼 제안 상태는 인터페이스를 통해 지정하는 것이 아니라 오퍼 엔진 호출에 대한 URL에서 직접 지정해야 합니다. 이렇게 하면 제안 제안이 거부되는 경우 등 다른 경우에 적용할 상태를 지정할 수 있습니다.

```
<BASE_URL>?a=UpdateStatus&p=<PRIMARY_KEY_OF_THE_PROPOSITION>&st=<NEW_STATUS_OF_THE_PROPOSITION>&r=<REDIRECT_URL>
```

예를 들어, 뉴뱅크 **사이트에 표시된 홈**&#x200B;보험 **오퍼와 일치하는 제안(식별자** 40004) **에는** 다음 URL이포함되어 있습니다.

```
<BASE_URL>?a=UpdateStatus&p=<40004>&st=<3>&r=<"http://www.neobank.com/insurance/subscribe.html">
```

방문자가 오퍼를 클릭하고 따라서 URL을 클릭하자마자 **[!UICONTROL Accepted]** 상태(값 **3**)가 제안에 적용되며 방문자는 보험 계약을 **수행하기 위해 뉴뱅크** 사이트의 새 페이지로 리디렉션됩니다.

>[!NOTE]
>
>URL에서 다른 상태를 지정하려면(예: 오퍼 제안이 거부된 경우) 원하는 상태에 해당하는 값을 사용합니다. 예: **[!UICONTROL Rejected]** = &quot;5&quot;, **[!UICONTROL Presented]** = &quot;1&quot; 등입니다.
>
>상태 및 해당 값은 **[!UICONTROL Offer propositions (nms)]** 데이터 스키마에서 검색할 수 있습니다. For more on this, refer to [this page](../../configuration/using/data-schemas.md).

**아웃바운드 상호 작용**

아웃바운드 상호 작용의 경우 전달에 링크가 들어 있을 때 자동으로 **[!UICONTROL Interested]** 상태를 제안 제안에 적용할 수 있습니다. 링크에 **_urlType=&quot;11&quot;** 값을 추가하면 됩니다.

```
<a _urlType="11" href="<DEST_URL>">Link inserted into the delivery</a>
```

## 공간당 오퍼 미리 보기 {#offer-preview-per-space}

이 탭에서 선택한 방법을 통해 수신자가 자격이 있는 오퍼를 볼 수 있습니다. 아래 예에서, 수신자는 세 가지 제안을 이메일로 받을 수 있습니다.

![](assets/offer_space_overview_002.png)

수신자가 어떤 오퍼도 사용할 수 없는 경우 미리 보기에 표시됩니다.

![](assets/offer_space_overview_001.png)

공백으로 제한된 경우 미리 보기는 컨텍스트를 무시할 수 있습니다. 이 경우 상호 작용 스키마가 인바운드 채널을 사용하여 공간에서 참조된 필드를 추가하도록 확장되었을 때(자세한 내용은 확장 [예제](../../interaction/using/extension-example.md)참조).
