---
solution: Campaign Classic
product: campaign
title: 이벤트 재활용
description: 이벤트 재활용
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%

---


# 이벤트 재활용{#event-recycling}

특정 채널에서 메시지 배달이 실패할 경우, Adobe Campaign은 다른 채널을 사용하여 메시지를 다시 보낼 수 있습니다. 예를 들어 SMS 채널에서의 배달이 실패할 경우 이메일 채널을 사용하여 메시지가 다시 전송됩니다.

이렇게 하려면 모든 이벤트를 **배달 오류** 상태로 다시 만들고 다른 채널을 할당하는 워크플로우를 구성해야 합니다.

>[!CAUTION]
>
>이 단계는 워크플로우를 사용해야만 수행할 수 있으므로 전문가 사용자용으로 예약됩니다. 자세한 내용은 Adobe 계정 담당자에게 문의하십시오.

