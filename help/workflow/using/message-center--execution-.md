---
title: 메시지 센터(실행)
seo-title: 메시지 센터(실행)
description: 메시지 센터(실행)
seo-description: null
page-status-flag: never-activated
uuid: 8dfb09d1-da00-43fb-9df4-243bb915cbde
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: dc3d8998-9493-4d71-b3e2-6f9531cb9bac
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 메시지 센터(실행){#message-center-execution}

아래에 자세히 설명된 워크플로우는 기본적으로 메시지 센터 - **실행** 모듈과 함께 설치됩니다. 이 모듈에 대한 자세한 내용은 이 [섹션을](../../message-center/using/about-transactional-messaging.md)참조하십시오.

메시지 센터 모듈과 관련된 기술 워크플로우를 구성하는 방법에 대한 자세한 내용은 [이 페이지를](../../message-center/using/technical-workflows.md)참조하십시오.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블</strong><br /> </td> 
   <td> <strong>내부 이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">이벤트 상태</span> 업데이트 <br /> </td> 
   <td> <span class="uicontrol">updateEventsStatus</span><br /> </td> 
   <td> 이 워크플로우에서는 이벤트에 상태를 지정할 수 있습니다. 이벤트 상태는 다음과 같습니다.<br /> 
    <ul> 
     <li> <p><strong>보류 중</strong>:이벤트가 대기열에 있습니다. 연결된 메시지 템플릿이 없습니다.</p> </li> 
     <li> <p><strong>배달</strong>대기 중:이벤트가 대기열에 있고 메시지 템플릿이 연결되어 현재 배달에서 처리 중입니다.</p> </li> 
     <li> <p><strong>전송</strong>:이 상태는 배달 로그에서 복사됩니다. 배달이 전송되었음을 의미합니다.</p> </li> 
     <li> <p><strong>배달에서</strong>무시됨:이 상태는 배달 로그에서 복사됩니다. 배달이 무시되었음을 의미합니다.</p> </li> 
     <li> <p><strong>배달 오류</strong>:이 상태는 배달 로그에서 복사됩니다. 배달이 실패했다는 뜻입니다.</p> </li> 
     <li> <p><strong>이벤트가 포함되지</strong>않음:이벤트를 메시지 템플릿과 연결하지 못했습니다. 이벤트가 다시 처리되지 않습니다.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">일괄 처리 이벤트</span> 처리 <br /> </td> 
   <td> <span class="uicontrol">batchEventsProcessing</span><br /> </td> 
   <td> 이 워크플로에서는 배치 이벤트를 메시지 템플릿과 연결하기 전에 대기열에 넣을 수 있습니다. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">실시간 이벤트</span> 처리 <br /> </td> 
   <td> <span class="uicontrol">rtEvents처리</span><br /> </td> 
   <td> 이 워크플로에서는 실시간 이벤트를 메시지 템플릿과 연결하기 전에 대기열에 넣을 수 있습니다. <br /> </td> 
  </tr> 
 </tbody> 
</table>

