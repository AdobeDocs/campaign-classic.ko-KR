---
title: 중간 소싱으로 전송
description: 중간 소싱 워크플로우로 전송에 대한 자세한 내용
page-status-flag: never-activated
uuid: 6b5be5a0-d1ea-428b-a755-74dd34b1d53d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: 57b873e9-e934-410b-b966-040cebd94e3e
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 7%

---


# 중간 소싱으로 전송{#transfer-to-mid-sourcing}

아래에 자세히 설명된 워크플로우는 기본적으로 중간 소싱 **으로** 전송 모듈과 함께 설치됩니다. For more on this module, refer to this [section](../../installation/using/mid-sourcing-deployment.md).

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
   <td> <p>이 워크플로우는 중간 소싱 서버에서 납품에 대한 카운트 정보를 수집합니다. 배송 수 등과 같은 일반 배달 지표가 카운트 정보에는 포함됩니다.</p> <p>열기 등의 추적 정보는 포함되지 않습니다.</p> <p>기본적으로 10분마다 트리거됩니다.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">중간 소싱(배달 로그)</span> <br /> </td> 
   <td> <span class="uicontrol">defaultMidSourcingLog</span> <br /> </td> 
   <td> 이 워크플로우는 중간 소싱 서버에서 배달 로그를 수집합니다. 기본적으로 매 시간마다 트리거됩니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

