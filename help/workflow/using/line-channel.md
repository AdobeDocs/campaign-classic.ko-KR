---
product: campaign
title: LINE 채널
description: LINE 채널
hide: true
feature: Workflows
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 2%
---

# LINE 채널{#line-channel}



아래에 설명된 워크플로는 기본적으로 **LINE 채널** 모듈과 함께 설치됩니다. 이 모듈에 대한 자세한 정보는 이 [섹션](../../delivery/using/line-channel.md)을 참조하세요.

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
   <td> 이 워크플로는 액세스 토큰을 LINE V2.<br />로 새로 고칩니다. </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">차단된 LINE 사용자 삭제</span> <br /> </td> 
   <td> <span class="uicontrol">deleteBlockedLineUsersV2</span> <br /> </td> 
   <td> 이 워크플로우에서는 LINE V2 사용자가 180일 동안 LINE 공식 계정을 차단한 후 해당 사용자의 데이터를 삭제합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MID에서 LineUserID로 마이그레이션</span> <br /> </td> 
   <td> <span class="uicontrol">MIDToUserIDMigration</span> <br /> </td> 
   <td> 이 워크플로우는 LINE V1에서 LINE V2로 마이그레이션할 LINE V2 사용자 ID를 생성합니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

