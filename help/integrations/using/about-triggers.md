---
product: campaign
title: Adobe Experience Cloud Triggers 기본 정보
description: Adobe Experience Cloud Triggers 구현 시작
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
exl-id: 0e337620-a49f-4e14-8c67-9279d74736f1
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 8%

---

# Campaign을 Experience Cloud 트리거와 함께 사용하기{#about-adobe-experience-triggers}



[!DNL Triggers] 는 파이프라인을 사용하여 Adobe Campaign과 Adobe Analytics을 통합한 것입니다. 파이프라인은 사용자의 작업 또는 트리거를 웹 사이트에서 검색합니다. 장바구니 포기는 트리거의 예입니다. 트리거는 거의 실시간으로 이메일을 보내기 위해 Adobe Campaign에서 처리됩니다.

>[!CAUTION]
>
>이 기능은 제품의 일부로 기본 제공되지 않습니다. 이 구현의 경우 먼저 Adobe 지원에서 티켓을 열어야 합니다. 그런 다음 이 섹션에 자세히 설명된 단계를 따를 수 있습니다 [페이지](../../integrations/using/configuring-pipeline.md#prerequisites).

[!DNL Triggers] 사용자 작업 후 짧은 시간 내에 마케팅 작업을 실행합니다. 일반적인 응답 시간은 1시간 미만입니다.

구성이 최소한이고 서드파티가 관련이 없기 때문에 더 애자일 통합을 허용합니다.
또한 마케팅 활동의 성능에 영향을 주지 않고 많은 양의 트래픽을 지원합니다. 예를 들어 통합은 시간당 백만 개의 트리거를 처리할 수 있습니다.

## [!DNL Triggers] 아키텍처 {#triggers-architecture}

다음 [!DNL pipelined] 프로세스는 항상 Adobe Campaign 마케팅 서버에서 실행됩니다. 파이프라인에 연결하고 이벤트를 검색한 다음 즉시 처리합니다.

![](assets/triggers_2.png)

다음 [!DNL pipelined] 프로세스 가 인증 서비스를 사용하여 Experience Cloud에 로그인하고 개인 키를 보냅니다. 인증 서비스가 토큰을 반환합니다. 토큰을 사용하여 이벤트를 검색할 때 인증합니다.

인증에 대한 자세한 내용은 다음을 참조하십시오. [페이지](../../integrations/using/configuring-adobe-io.md).
