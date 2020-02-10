---
title: 인터랙션
seo-title: 인터랙션
description: 인터랙션
seo-description: null
page-status-flag: never-activated
uuid: 5c8e2353-bb76-4e8d-95d7-61b6c111b6b3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: 1683477a-9233-4a25-b0d0-0c81051eb440
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 28a32c9a5300c28784ae7a2837075b4dc3aad1fa

---


# 인터랙션{#interaction}

아래에 자세히 설명된 워크플로우는 기본적으로 오퍼 엔진( **상호 작용)** 모듈과 함께 설치됩니다. 이 모듈에 대한 자세한 내용은 이 [섹션을](../../interaction/using/interaction-and-offer-management.md)참조하십시오.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블</strong><br /> </td> 
   <td> <strong>내부 이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">전체 합계 계산(propositionrcp 큐브)</span><br /> </td> 
   <td> <span class="uicontrol">agg_nmspropositionrcp_full</span><br /> </td> 
   <td> 이 워크플로우는 오퍼 <strong>제안</strong> 큐브의 전체 <strong>집계를 업데이트합니다</strong> . 기본적으로 매일 오전 6시에 트리거됩니다. 이 집계는 다음 차원을 캡처합니다.채널, 전달, 마케팅 제안 및 날짜.<br /> 그런 <strong>다음 오퍼 제안</strong> 큐브를 사용하여 오퍼를 기반으로 보고서를 생성합니다. 이 <a href="../../reporting/using/about-cubes.md">섹션에서</a>정육면체에 대해 자세히 알아볼 수 있습니다.<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">MessageCenter 전체 합계 계산</span><br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span><br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

