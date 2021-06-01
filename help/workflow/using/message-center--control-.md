---
product: campaign
title: 메시지 센터(제어)
description: 메시지 센터(제어)
audience: workflow
content-type: reference
topic-tags: technical-workflows
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 7%

---


# 메시지 센터(제어){#message-center-control}

아래에 자세히 설명된 워크플로우는 매시간마다 실행되도록 예약되어 있습니다. 기본적으로 **메시지 센터 - 컨트롤** 모듈과 함께 설치됩니다. 이 모듈에 대한 자세한 내용은 이 [섹션](../../message-center/using/about-transactional-messaging.md)을 참조하십시오.

메시지 센터 모듈과 관련된 기술 워크플로우를 구성하는 방법에 대한 자세한 내용은 [이 페이지](../../message-center/using/technical-workflows.md)를 참조하십시오.

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
   <td> 이 워크플로:<br /> 
    <ul> 
     <li> <p>작업으로 처리된 이벤트 목록을 복구합니다.</p> </li> 
     <li> <p>배달 메시지 자격을 복구하기 위해 NmsBroadLogMsg 테이블과 동기화합니다.</p> </li> 
     <li> <p>NmsBroadLogMsg 테이블과의 동기화가 완료되는 즉시 이벤트 게재 로그를 복구합니다.</p> </li> 
     <li> <p>는 배달 URL에 대한 추적을 복구하기 위해 NmsTrackingUrl 테이블과 동기화합니다.</p> </li> 
     <li> <p>NmsTrackingUrl 테이블과의 동기화가 완료되는 즉시 이벤트 추적 URL을 복구합니다.</p> </li> 
     <li> <p>게재를 보낸 후 3시간마다 격리된 모든 이메일 주소를 복구할 수 있습니다.</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

