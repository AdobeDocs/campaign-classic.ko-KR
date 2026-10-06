---
product: campaign
title: 인터랙션
description: 인터랙션
hide: true
feature: Workflows, Interaction, Offers
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 65702805-0026-5ca1-843a-144fa79f0883
    internal-label: Interaction
  - id: ea08db70-4682-59a2-9408-9aedd9548e07
    internal-label: Offers
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 2%
---

# 인터랙션{#interaction}



아래에 설명된 워크플로는 기본적으로 **오퍼 엔진(상호 작용)** 추가 기능으로 설치됩니다.

자세한 내용은 Campaign 버전에 따라 다음 섹션을 참조하십시오.

![](assets/do-not-localize/v7.jpeg) [Campaign v7 설명서](../../interaction/using/interaction-and-offer-management.md)

![](assets/do-not-localize/v8.png) [Campaign v8 설명서](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/interaction/interaction.html)


<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블</strong><br /> </td> 
   <td> <strong>내부 이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">전체 집계 계산(propositionrcp 큐브)</span> <br /> </td> 
   <td> <span class="uicontrol">agg_nmspropositionrcp_full</span> <br /> </td> 
   <td> 이 워크플로우는 <strong>오퍼 제안</strong> 큐브에 대한 <strong>전체</strong> 집계를 업데이트합니다. 기본적으로 매일 오전 6시에 트리거됩니다. 이 집계는 채널, 게재, 마케팅 오퍼 및 날짜 차원을 캡처합니다.<br /> 그런 다음 <strong>오퍼 제안</strong> 큐브를 사용하여 오퍼를 기반으로 보고서를 생성합니다. 큐브에 대한 자세한 내용은 <a href="../../reporting/using/ac-cubes.md">이 섹션</a>.<br />을 참조하세요. </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">MessageCenter 전체 집계 계산</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> 이 워크플로는 <strong>메시지 센터</strong> 큐브에 대한 <strong>전체</strong> 집계를 업데이트합니다. 기본적으로 매일 오전 3시에 트리거됩니다. 이 집계는 채널, 날짜, 상태 및 이벤트 유형 차원을 캡처합니다.<br /> 그러면 <strong>메시지 센터</strong> 큐브를 사용하여 이벤트를 기반으로 보고서를 생성합니다. 큐브에 대한 자세한 내용은 <a href="../../reporting/using/ac-cubes.md">이 섹션</a>.<br />을 참조하세요. </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

