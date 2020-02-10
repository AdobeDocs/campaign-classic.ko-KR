---
title: 배달 실행
seo-title: 배달 실행
description: 배달 실행
seo-description: null
page-status-flag: never-activated
uuid: d4f4cea7-783b-45d3-b004-297104f0a906
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: afb375de-2de3-47ad-8b37-664cc04864e8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 211556bbf023731ffeab2e90692410a852ab3555

---


# 배달 실행{#delivery-execution}

>[!NOTE]
>
>MTA는 다른 배달보다 트랜잭션 메시지 처리를 우선합니다.

실행 인스턴스에서, 농축 단계가 완료되고 배달 템플릿이 이벤트에 연결되면 배달이 전송됩니다. 모든 배달은 **[!UICONTROL Administration > Production > Message Center > Default > Deliveries]** 폴더에 그룹화됩니다.

![](assets/messagecenter_deliveries_execinstances_001.png)

기본적으로 배달 월별로 하위 폴더로 정렬됩니다.

이 정렬은 아래와 같이 메시지 템플릿 속성에서 변경할 수 있습니다.

![](assets/messagecenter_deliveries_properties_001.png)

>[!NOTE]
>
>호스팅 또는 하이브리드 설치의 경우 향상된 MTA로 업그레이드한 경우 전달 능력, 처리량 및 바운스 처리를 개선하기 위해 모든 트랜잭션 메시지를 Adobe Campaign 향상된 MTA와 함께 전송할 수도 있습니다. 모든 영향은 표준 마케팅 메시지와 동일하며 Adobe Campaign 향상된 MTA [문서에 자세히 설명되어](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html) 있습니다.