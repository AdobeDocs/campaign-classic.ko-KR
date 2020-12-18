---
solution: Campaign Classic
product: campaign
title: 메시지 센터(실행)
description: 메시지 센터(실행)
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 6%

---


# 메시지 센터(실행){#message-center-execution}

아래에 설명된 워크플로우는 기본적으로 **메시지 센터 - 실행** 모듈과 함께 설치됩니다. 이 모듈에 대한 자세한 내용은 이 [섹션](../../message-center/using/about-transactional-messaging.md)을 참조하십시오.

메시지 센터 모듈과 관련된 기술 워크플로우를 구성하는 방법에 대한 자세한 내용은 [이 페이지](../../message-center/using/technical-workflows.md)를 참조하십시오.

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
   <td> 이 워크플로우에서는 이벤트에 상태를 할당할 수 있습니다. 이벤트 상태는 다음과 같습니다.<br /> 
    <ul> 
     <li> <p><strong>보류 중</strong>:이벤트가 큐에 있습니다. 아직 연결된 메시지 템플릿이 없습니다.</p> </li> 
     <li> <p><strong>배달 보류</strong>:이벤트가 큐에 있고, 메시지 템플릿이 연결되어 있으며 현재 배달에서 처리 중입니다.</p> </li> 
     <li> <p><strong>전송</strong>:이 상태는 배달 로그에서 복사됩니다. 배달이 전송되었음을 의미합니다.</p> </li> 
     <li> <p><strong>배달에서 무시됨</strong>:이 상태는 배달 로그에서 복사됩니다. 배달이 무시되었음을 의미합니다.</p> </li> 
     <li> <p><strong>배달 오류</strong>:이 상태는 배달 로그에서 복사됩니다. 배달이 실패했다는 의미입니다.</p> </li> 
     <li> <p><strong>다루지 않은 이벤트</strong>:이벤트를 메시지 템플릿과 연결하지 못했습니다. 이벤트는 다시 처리되지 않습니다.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">일괄 처리 이벤트 처리</span> <br /> </td> 
   <td> <span class="uicontrol">batchEventsProcessing</span> <br /> </td> 
   <td> 이 워크플로우에서는 일괄 처리 이벤트를 메시지 템플릿과 연결하기 전에 큐에 넣을 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">실시간 이벤트 처리</span> <br /> </td> 
   <td> <span class="uicontrol">rtEvents처리</span> <br /> </td> 
   <td> 이 워크플로우에서는 실시간 이벤트를 메시지 템플릿과 연결하기 전에 큐에 넣을 수 있습니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

