---
title: Adobe Experience Cloud 트리거 기본 정보
description: Adobe Experience Cloud 트리거 구현 시작하기
page-status-flag: never-activated
uuid: c523822f-8178-4989-bd88-ab402470e540
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 0d617f1c-0d0b-489f-9027-a92b1f1eee37
translation-type: tm+mt
source-git-commit: 48acf8cbc52a54a2dd08f0b8f29be57d4e5e006f
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 16%

---


# Adobe Experience Cloud 트리거 시작하기{#about-adobe-experience-triggers}

[!DNL Triggers] 이 파이프라인을 사용한 Adobe Campaign과 Adobe Analytics의 통합. 파이프라인은 웹 사이트에서 사용자의 작업 또는 트리거를 검색합니다. 장바구니 포기는 트리거의 예입니다. 트리거는 Adobe Campaign에서 처리되어 거의 실시간으로 이메일을 보냅니다.

>[!CAUTION]
>
>이 기능은 제품의 일부로 기본 제공되지 않습니다. 구현하려면 Adobe Consulting 서비스가 필요합니다. 자세한 내용은 Adobe 담당자에게 문의하십시오

[!DNL Triggers] 사용자의 조치에 따라 짧은 시간 내에 마케팅 작업을 실행합니다. 일반적인 응답 시간은 1시간 미만입니다.

구성이 최소화되고 서드파티와 관련이 없기 때문에 더욱 민첩한 통합이 가능합니다.
또한 마케팅 활동의 성과에 영향을 주지 않고 많은 양의 트래픽을 지원합니다. 예를 들어 통합은 시간당 100만 개의 트리거를 처리할 수 있습니다.

## [!DNL Triggers] 아키텍처 {#triggers-architecture}

이 [!DNL pipelined] 프로세스는 항상 Adobe Campaign 마케팅 서버에서 실행됩니다. 파이프라인에 연결하여 이벤트를 검색하고 즉시 처리합니다.

![](assets/triggers_2.png)

프로세스는 인증 서비스를 사용하여 Experience Cloud에 로그인하고 개인 키를 전송합니다. [!DNL pipelined] 인증 서비스는 토큰을 반환합니다. 토큰을 사용하여 이벤트를 검색할 때 인증합니다.

For more information on authentication, refer to this [page](../../integrations/using/configuring-adobe-io.md).
