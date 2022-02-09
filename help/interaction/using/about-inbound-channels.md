---
product: campaign
title: 인바운드 채널 정보
description: 인바운드 채널 정보
exl-id: 33247728-b865-4dfd-814f-2900965a7187
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 4%

---

# 인바운드 채널 정보{#about-inbound-channels}

![](../../assets/v7-only.svg)

Offers can be presented on various offer spaces using an inbound or outbound channel. This chapter details some specific features for inbound channels.

![](assets/do-not-localize/how-to-video.png) 또한 이것을 볼 수 있습니다 [비디오](https://helpx.adobe.com/campaign/classic/how-to/deliver-an-offer-on-inbound-channel-in-acv6.html) 는 인바운드 채널에 오퍼를 전달하는 방법을 자세히 설명합니다.

오퍼 엔진에서 오퍼를 선택하려면 오퍼를 승인하고 라이브 환경에서 사용할 수 있어야 합니다. 자세한 내용은 [오퍼 승인 및 활성화](../../interaction/using/approving-and-activating-an-offer.md).

연락처가 인바운드 경우 다음 두 가지 가능한 결과가 있습니다. 페이지를 탐색 중인 사용자는 웹 사이트에서 식별할 수 있습니다. The offer engine presents different offers depending on whether or not the user is identified.

인바운드 채널에 오퍼를 표시할 수 있으려면 먼저 오퍼를 표시할 오퍼 엔진 호출을 구성해야 합니다. In most cases for an inbound interaction, this is the Web page.

>[!NOTE]
>
>인바운드 상호 작용의 경우 하나 또는 여러 오퍼를 제공하고 업데이트하도록 오퍼 엔진을 특별히 구성해야 합니다.
>
>또한 오퍼 공간에서 단일 모드를 활성화해야 합니다. For more on this, refer to the [Creating offer spaces](../../interaction/using/creating-offer-spaces.md) section.
