---
solution: Campaign Classic
product: campaign
title: 상호 작용
description: 상호 작용
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '99'
ht-degree: 5%

---


# 상호 작용{#interaction}

아래에 자세히 설명된 워크플로우는 기본적으로 **오퍼 엔진(상호 작용)** 모듈과 함께 설치됩니다. For more on this module, refer to this [section](../../interaction/using/interaction-and-offer-management.md).

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
   <td> 이 워크플로우는 <strong>오퍼 제안</strong> 큐브에 대한 전체 <strong>집계를</strong> 업데이트합니다. 기본적으로 매일 오전 6시에 트리거됩니다. 이 집계는 다음 차원을 캡처합니다.채널, 전달, 마케팅 제안 및 날짜.<br /> 그런 다음 <strong>오퍼 제안</strong> 큐브를 사용하여 오퍼를 기반으로 보고서를 생성합니다. 이 섹션에서 정육면체에 대해 자세히 알아볼 수 <a href="../../reporting/using/about-cubes.md">있습니다</a>.<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">MessageCenter 전체 집계 계산</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

