---
title: LINE 채널
seo-title: LINE 채널
description: LINE 채널
seo-description: null
page-status-flag: never-activated
uuid: 0b0e34b2-7ee9-456a-9ed9-7ede889584b6
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: 367314a2-eb6d-4710-8a47-5a51049ad924
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# LINE 채널{#line-channel}

아래에 자세히 설명된 워크플로우는 기본적으로 LINE **채널** 모듈과 함께 설치됩니다. 이 모듈에 대한 자세한 내용은 이 [섹션을](../../delivery/using/line-channel.md)참조하십시오.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블</strong><br /> </td> 
   <td> <strong>내부 이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">LINE V2 액세스 토큰 업데이트</span><br /> </td> 
   <td> <span class="uicontrol">updateLineV2AccessToken</span> <br /> </td> 
   <td> 이 워크플로우는 액세스 토큰을 LINE V2로 새로 고칩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">차단된 LINE 사용자</span> 삭제 <br /> </td> 
   <td> <span class="uicontrol">deleteBlockedLineUsersV2</span> <br /> </td> 
   <td> 이 워크플로우에서는 LINE V2 사용자의 데이터가 180일 동안 LINE 공식 계정을 차단하면 삭제됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MID에서 LineUserID로 마이그레이션</span><br /> </td> 
   <td> <span class="uicontrol">MIDToUserIDMigation</span><br /> </td> 
   <td> 이 워크플로우는 LINE V1에서 LINE V2로 마이그레이션하기 위한 LINE V2 사용자 ID를 생성합니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

