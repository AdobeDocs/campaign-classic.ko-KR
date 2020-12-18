---
solution: Campaign Classic
product: campaign
title: 상호 작용
description: 상호 작용
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: affc541c480ad7e618120fe90270841add06b711
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 3%

---


# 상호 작용{#interaction}

아래에 설명된 워크플로우는 기본적으로 **오퍼 엔진(상호 작용)** 모듈과 함께 설치됩니다. 이 모듈에 대한 자세한 내용은 이 [섹션](../../interaction/using/interaction-and-offer-management.md)을 참조하십시오.

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
   <td> 이 워크플로우는 <strong>오퍼 제안</strong> 큐브에 대한 <strong>Full</strong> 집계를 업데이트합니다. 기본적으로 매일 오전 6시에 트리거됩니다. 이 집계는 다음 차원을 캡처합니다.채널, 전달, 마케팅 제안 및 날짜.<br /> 그런  <strong>다음 오퍼 </strong> 속성 큐브를 사용하여 오퍼를 기반으로 보고서를 생성합니다. <a href="../../reporting/using/about-cubes.md">이 섹션</a>에서 큐브에 대해 자세히 알아볼 수 있습니다.<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">MessageCenter 전체 집계 계산</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> 이 워크플로우는 <strong>메시지 센터</strong> 큐브에 대한 <strong>전체</strong> 집계를 업데이트합니다. 기본적으로 매일 오전 3시에 트리거됩니다. 이 집계는 다음 차원을 캡처합니다.채널, 날짜, 상태 및 이벤트 유형.<br /> 그런 다음  <strong>메시지 </strong> 센터 큐브를 사용하여 이벤트를 기반으로 보고서를 생성합니다. <a href="../../reporting/using/about-cubes.md">이 섹션</a>에서 큐브에 대해 자세히 알아볼 수 있습니다.<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

