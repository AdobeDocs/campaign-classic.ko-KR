---
solution: Campaign Classic
product: campaign
title: 중간 소싱으로 전송
description: 중간 소싱 워크플로우로 전송에 대해 자세히 알아보기
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 7%

---


# 중간 소싱으로 전송{#transfer-to-mid-sourcing}

아래에 자세히 설명된 워크플로우는 기본적으로 **중간 소싱** 모듈로 이전됩니다. 이 모듈에 대한 자세한 내용은 이 [섹션](../../installation/using/mid-sourcing-deployment.md)을 참조하십시오.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블</strong><br /> </td> 
   <td> <strong>내부 이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">중간 소싱(배달 카운터)</span> <br /> </td> 
   <td> <span class="uicontrol">defaultMidSourcingDlv</span> <br /> </td> 
   <td> <p>이 워크플로우는 중간 소싱 서버에서 납품에 대한 카운트 정보를 수집합니다. 개수 정보에는 전송 횟수 등과 같은 일반 배달 지표가 포함되어 있습니다.</p> <p>열기와 같은 추적 정보는 포함되지 않습니다.</p> <p>기본적으로 10분마다 트리거됩니다.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">중간 소싱(배달 로그)</span> <br /> </td> 
   <td> <span class="uicontrol">defaultMidSourcingLog</span> <br /> </td> 
   <td> 이 워크플로우는 중간 소싱 서버의 배달 로그를 수집합니다. 기본적으로 매 시간마다 트리거됩니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

