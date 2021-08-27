---
product: campaign
title: 중간 소싱으로 전송
description: 중간 소싱 워크플로우로 전송에 대해 자세히 알아보십시오
audience: workflow
content-type: reference
topic-tags: technical-workflows
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 7%

---


# 중간 소싱으로 전송{#transfer-to-mid-sourcing}

![](../../assets/common.svg)

아래 자세히 설명된 워크플로우는 기본적으로 **중간 소싱으로 전송** 모듈과 함께 설치됩니다. 이 모듈에 대한 자세한 내용은 [Campaign Classic v7 설치 안내서](../../installation/using/mid-sourcing-deployment.md)를 참조하십시오.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블</strong><br /> </td> 
   <td> <strong>내부 이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">중간 소싱(게재 카운터)</span> <br /> </td> 
   <td> <span class="uicontrol">defaultMidSourcingDlv</span> <br /> </td> 
   <td> <p>이 워크플로우는 중간 소싱 서버의 게재에 대한 카운트 정보를 수집합니다. 카운트 정보에는 전송된 게재 수 등과 같은 일반 게재 지표가 포함되어 있습니다.</p> <p>열기와 같은 추적 정보는 포함되지 않습니다.</p> <p>기본적으로 10분마다 트리거됩니다.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">중간 소싱(게재 로그)</span> <br /> </td> 
   <td> <span class="uicontrol">defaultMidSourcingLog</span> <br /> </td> 
   <td> 이 워크플로우는 중간 소싱 서버에서 게재 로그를 수집합니다. 기본적으로 매시간 트리거됩니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

