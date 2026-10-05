---
product: campaign
title: 메시지 센터(실행)
description: 메시지 센터(실행)
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
source-wordcount: '232'
ht-degree: 2%
---

# 메시지 센터(실행){#message-center-execution}



아래에 자세히 설명된 워크플로는 기본적으로 **메시지 센터 - 실행** 추가 기능과 함께 설치됩니다.

자세한 내용은 Campaign 버전에 따라 다음 섹션을 참조하십시오.

![](assets/do-not-localize/v7.jpeg) [Campaign v7 설명서](../../message-center/using/about-transactional-messaging.md)

![](assets/do-not-localize/v8.png) [Campaign v8 설명서](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/transactional.html)

<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블</strong><br /> </td> 
   <td> <strong>내부 이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">이벤트 상태 업데이트</span> <br /> </td> 
   <td> <span class="uicontrol">updateEventsStatus</span> <br /> </td> 
   <td> 이 워크플로우를 통해 이벤트에 상태를 할당할 수 있습니다. 이벤트 상태는 다음과 같습니다. <br /> 
    <ul> 
     <li> <p><strong>보류 중</strong>: 이벤트가 큐에 있습니다. 아직 연결된 메시지 템플릿이 없습니다.</p> </li> 
     <li> <p><strong>게재 보류 중</strong>: 이벤트가 큐에 있고 메시지 템플릿이 연결되어 있으며 현재 게재에서 처리 중입니다.</p> </li> 
     <li> <p><strong>전송됨</strong>: 이 상태는 게재 로그에서 복사됩니다. 게재가 전송되었음을 의미합니다.</p> </li> 
     <li> <p><strong>게재에서 무시됨</strong>: 이 상태는 게재 로그에서 복사됩니다. 게재가 무시되었음을 의미합니다.</p> </li> 
     <li> <p><strong>게재 오류</strong>: 이 상태는 게재 로그에서 복사됩니다. 게재가 실패했다는 뜻입니다.</p> </li> 
     <li> <p><strong>이벤트가 포함되지 않음</strong>: 이벤트를 메시지 템플릿에 연결하지 못했습니다. 이벤트는 재처리되지 않습니다.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">일괄 처리 이벤트 처리</span> <br /> </td> 
   <td> <span class="uicontrol">batchEventsProcessing</span> <br /> </td> 
   <td> 이 워크플로우를 사용하면 메시지 템플릿과 연결하기 전에 일괄 처리 이벤트를 대기열에 넣을 수 있습니다. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">실시간 이벤트 처리</span> <br /> </td> 
   <td> <span class="uicontrol">rtEventsProcessing</span> <br /> </td> 
   <td> 이 워크플로우를 사용하면 실시간 이벤트를 메시지 템플릿과 연결하기 전에 대기열에 넣을 수 있습니다. <br /> </td> 
  </tr> 
 </tbody> 
</table>

