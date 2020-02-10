---
title: 이벤트 재활용
seo-title: 이벤트 재활용
description: 이벤트 재활용
seo-description: null
page-status-flag: never-activated
uuid: 55624a41-65a1-4759-8087-6e5d2c5c5b62
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: 568a9dec-5818-4666-b858-aa41fe827b92
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 이벤트 재활용{#event-recycling}

특정 채널에서 메시지 배달이 실패하는 경우 Adobe Campaign은 다른 채널을 사용하여 메시지를 다시 보낼 수 있습니다. 예를 들어, SMS 채널에서 배달이 실패하는 경우 이메일 채널을 사용하여 메시지를 다시 보냅니다.

이렇게 하려면 배달 오류 **상태로 모든 이벤트를 다시 만들고 다른 채널을 할당하는** 워크플로우를 구성해야 합니다.

>[!CAUTION]
>
>이 단계는 워크플로우를 통해서만 수행할 수 있으므로 전문가 사용자용으로 예약됩니다. 자세한 내용은 Adobe 계정 담당자에게 문의하십시오.

