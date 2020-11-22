---
solution: Campaign Classic
product: campaign
title: LINE 채널
description: LINE 채널
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 11%

---


# LINE 채널{#line-channel}

아래에 자세히 설명된 워크플로우는 기본적으로 **LINE 채널** 모듈과 함께 설치됩니다. For more on this module, refer to this [section](../../delivery/using/line-channel.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블</strong><br /> </td> 
   <td> <strong>내부 이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">LINE V2 액세스 토큰 업데이트</span> <br /> </td> 
   <td> <span class="uicontrol">updateLineV2AccessToken</span> <br /> </td> 
   <td> 이 워크플로우는 액세스 토큰을 LINE V2로 새로 고칩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">차단된 LINE 사용자 삭제</span> <br /> </td> 
   <td> <span class="uicontrol">deleteBlockedLineUsersV2</span> <br /> </td> 
   <td> 이 워크플로우에서는 LINE V2 사용자의 데이터가 180일 동안 LINE 공식 계정을 차단된 후 삭제됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MID에서 LineUserID 마이그레이션</span> <br /> </td> 
   <td> <span class="uicontrol">MIDToUserIDMigning</span> <br /> </td> 
   <td> 이 워크플로우는 LINE V1에서 LINE V2로 마이그레이션하기 위한 LINE V2 사용자 ID를 생성합니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

