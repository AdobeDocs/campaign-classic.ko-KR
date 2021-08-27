---
product: campaign
title: 상호 작용
description: 상호 작용
audience: workflow
content-type: reference
topic-tags: technical-workflows
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 6%

---


# 상호 작용{#interaction}

![](../../assets/common.svg)

아래 자세히 설명된 워크플로우는 기본적으로 **오퍼 엔진(상호 작용)** 추가 기능과 함께 설치됩니다.

자세한 내용은 Campaign 버전에 따라 다음 섹션을 참조하십시오.

![](assets/do-not-localize/v7.jpeg)[  Campaign v7 설명서](../../interaction/using/interaction-and-offer-management.md)

![](assets/do-not-localize/v8.png)[  Campaign v8 설명서](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/interaction/interaction.html)


<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블</strong><br /> </td> 
   <td> <strong>내부 이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">전체 합계 계산(propositionrcp 큐브)</span> <br /> </td> 
   <td> <span class="uicontrol">agg_nmspropositionrcp_full</span> <br /> </td> 
   <td> 이 워크플로우는 <strong>오퍼 제안</strong> 큐브에 대한 <strong>Full</strong> 집계를 업데이트합니다. 기본적으로 매일 오전 6시에 트리거됩니다. 이 집계는 다음 차원을 캡처합니다. 채널, 게재, 마케팅 오퍼 및 날짜.<br /> 그런 다음  <strong>오퍼 </strong> 포지셔티브 큐브를 사용하여 오퍼를 기반으로 보고서를 생성합니다. <a href="../../reporting/using/about-cubes.md">이 섹션</a>에서 큐브에 대해 자세히 알 수 있습니다.<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">MessageCenter 전체 집계 계산</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> 이 워크플로우는 <strong>메시지 센터</strong> 큐브에 대한 <strong>전체</strong> 집계를 업데이트합니다. 기본적으로 매일 오전 3시에 트리거됩니다. 이 집계는 다음 차원을 캡처합니다. 채널, 날짜, 상태 및 이벤트 유형.<br /> 그런 다음  <strong>메시지 </strong> 센터 큐브를 사용하여 이벤트를 기반으로 보고서를 생성합니다. <a href="../../reporting/using/about-cubes.md">이 섹션</a>에서 큐브에 대해 자세히 알 수 있습니다.<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

