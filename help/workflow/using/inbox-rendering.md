---
title: Adobe Campaign Classic의 받은 편지함 렌더링 기술 워크플로우
description: 이 섹션에서는 Adobe Campaign Classic의 받은 편지함 렌더링 패키지와 함께 설치되는 기술 워크플로우에 대해 설명합니다.
page-status-flag: never-activated
uuid: f60a09f0-47a0-4fc0-b0ac-47178af6ad55
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: da0779dc-b734-483b-81e9-ff4706a2b6de
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e1bd878c45576932e085b579f91eb72f5d36d6fd

---


# 받은 편지함 렌더링(IR){#inbox-rendering}

아래에 자세히 설명된 워크플로우는 기본적으로 받은 편지함 **렌더링(IR)** 모듈과 함께 설치됩니다. 받은 편지함 렌더링에 대한 자세한 내용은 이 [섹션을](../../delivery/using/inbox-rendering.md)참조하십시오.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블</strong><br /> </td> 
   <td> <strong>내부 이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>받은 편지함 렌더링을 위한 시드 네트워크 업데이트</strong><br /> </td> 
   <td> <span class="uicontrol">updateRenderingSeeds</span><br /> </td> 
   <td> 이 워크플로우는 받은 편지함 렌더링에 사용되는 이메일 주소를 업데이트하며, HTTPS 포트가 <strong>deliverability.neolane.net</strong>용으로 열려 있는 경우에만 작동합니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

