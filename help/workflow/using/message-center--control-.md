---
title: 메시지 센터(제어)
seo-title: 메시지 센터(제어)
description: 메시지 센터(제어)
seo-description: null
page-status-flag: never-activated
uuid: bdb3610b-a893-4e60-a9f7-f21d90b66919
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: 69e3e99f-d392-4316-926c-3c3c675415ad
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 메시지 센터(제어){#message-center-control}

아래 설명된 워크플로우는 매 시간마다 실행되도록 예약되어 있습니다. 기본적으로 메시지 센터 - **제어** 모듈과 함께 설치됩니다. 이 모듈에 대한 자세한 내용은 이 [섹션을](../../message-center/using/about-transactional-messaging.md)참조하십시오.

메시지 센터 모듈과 관련된 기술 워크플로우를 구성하는 방법에 대한 자세한 내용은 [이 페이지를](../../message-center/using/technical-workflows.md)참조하십시오.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블</strong><br /> </td> 
   <td> <strong>내부 이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 메시지 센터 &lt;external_account_name&gt;<br /> </td> 
   <td> mcSynch_&lt;external_account_name&gt;<br /> </td> 
   <td> 이 워크플로우:<br /> 
    <ul> 
     <li> <p>작업에 의해 처리된 이벤트 목록을 복구합니다.</p> </li> 
     <li> <p>배달 메시지 자격 조건을 복구하기 위해 NmsBroadLogMsg 테이블과 동기화합니다.</p> </li> 
     <li> <p>NmsBroadLogMsg 테이블과의 동기화가 완료되는 즉시 이벤트 배달 로그를 복구합니다.</p> </li> 
     <li> <p>은 배달 URL에 대한 추적을 복구하기 위해 NmsTrackingUrl 표와 동기화됩니다.</p> </li> 
     <li> <p>nmsTrackingUrl 테이블과의 동기화가 완료되는 즉시 이벤트 추적 URL을 복구합니다.</p> </li> 
     <li> <p>배달을 보낸 후 3시간마다 격리에 배치된 모든 이메일 주소를 복구할 수 있습니다.</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

