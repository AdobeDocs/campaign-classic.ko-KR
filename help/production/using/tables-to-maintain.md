---
solution: Campaign Classic
product: campaign
title: 유지 관리할 표
description: 유지 관리할 표
audience: production
content-type: reference
topic-tags: database-maintenance
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1123'
ht-degree: 0%

---


# 유지 관리할 표{#tables-to-maintain}

유지 관리할 테이블 목록은 사용 중인 Adobe Campaign 버전, 사용 방법 및 데이터 모델 구성에 따라 다릅니다.

다음 목록에는 가장 세분화된 테이블만 포함되어 있습니다. 효과는 다음과 같습니다.

* 디스크 공간 과소비로 인해 데이터베이스 액세스에 영향을 미칩니다.
* 정기적으로 업데이트되지 않은 인덱스를 통해 쿼리 성능이 저하됩니다.

## Adobe Campaign 테이블 {#adobe-campaign-tables}

<table> 
 <thead> 
  <tr> 
   <th> <strong>테이블 이름  </strong><br /> </th> 
   <th> <strong>크기</strong><br /> </th> 
   <th> <strong>활동의 기본 유형</strong><br /> </th> 
   <th> <strong>댓글</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> NmsDelivery<br /> </td> 
   <td> 작음<br /> </td> 
   <td> 업데이트<br /> </td> 
   <td> 배달 작업당 한 개의 레코드가 있습니다. 단일 레코드를 여러 번 업데이트하여 배달 진행 상황을 반영할 수 있으므로 이 테이블의 인덱스는 빠르게 조각하는 경향이 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryPart<br /> </td> 
   <td> 중간<br /> </td> 
   <td> 삽입, 업데이트, 삭제<br /> </td> 
   <td> 배달 준비 중에 삽입되는 레코드가 포함된 작업 테이블 그런 다음 배달 중에 업데이트되고 배달이 완료되면 마지막으로 삭제됩니다.<br /> 이 테이블은 평균 크기가 상당히 제한되지만 빠르게 조각나는 경향이 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMirrorPageInfo<br /> </td> 
   <td> 큼<br /> </td> 
   <td> 삽입, 삭제<br /> </td> 
   <td> 이 표에는 개인화된 미러 페이지를 생성하는 데 필요한 정보가 포함되어 있습니다. 메모(CLOB) 필드가 포함되어 있으므로 매우 큰 경향이 있습니다. 볼륨은 보관된 미러 페이지 내역에 바로 비례합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryStat<br /> </td> 
   <td> 중간<br /> </td> 
   <td> 삽입, 업데이트, 삭제<br /> </td> 
   <td> 이 테이블에는 배달 프로세스에 대한 통계가 들어 있습니다. 그 기록들은 정기적으로 갱신된다.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAddress<br /> </td> 
   <td> 중간<br /> </td> 
   <td> 업데이트, 삽입<br /> </td> 
   <td> 이 표에는 이메일 주소에 대한 정보가 들어 있습니다. 격리 프로세스의 일부로 자주 업데이트됩니다. 이 경우 첫 번째 배달 오류가 발생하면 레코드가 만들어지고, 카운터가 변경되면 업데이트되고 배달이 성공한 후에는 삭제됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflow<br /> </td> 
   <td> 작음<br /> </td> 
   <td> 업데이트<br /> </td> 
   <td> 워크플로우 인스턴스당 하나의 레코드가 있으므로 레코드는 거의 없습니다. 하지만 상태 및 진행 상태를 반영하도록 이 테이블이 정기적으로 업데이트됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowTask<br /> </td> 
   <td> 작음<br /> </td> 
   <td> 삽입, 업데이트, 삭제<br /> </td> 
   <td> 워크플로우 활동을 실행할 때마다 이 표에 레코드가 생성됩니다. 제거 메커니즘은 만료되면 삭제됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowEvent<br /> </td> 
   <td> 작음<br /> </td> 
   <td> 삽입, 업데이트, 삭제<br /> </td> 
   <td> 워크플로우에서 작업 간에 활성화된 각 전환은 이 표에 레코드가 생성됩니다. 제거는 만료되면 삭제됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowJob<br /> </td> 
   <td> 매우 작음 <br /> </td> 
   <td> 삽입, 업데이트, 삭제<br /> </td> 
   <td> 이 표는 워크플로 엔진에만 적용됩니다. 워크플로우(예: 시작, 중지, 일시 중지)로 명령을 보낼 수 있습니다. 이 표는 작지만 워크플로우에 연결된 트랜잭션 테이블을 제거하는 동안 이 표를 고려합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLog<br /> </td> 
   <td> 가장 큰<br /> </td> 
   <td> 삽입, 업데이트, 삭제<br /> </td> 
   <td> 이 테이블이 시스템에서 가장 큰 테이블입니다. 전송된 메시지당 한 개의 레코드가 있으며 이러한 레코드는 삽입되고, 배달 상태를 추적하도록 업데이트되며, 기록이 삭제될 때 삭제됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLog<br /> </td> 
   <td> 큼<br /> </td> 
   <td> 삽입, 삭제<br /> </td> 
   <td> 추적 로그는 작업 내역을 삭제할 때 삽입되고 삭제되지만 업데이트되지 않습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadlogMsg <br /> </td> 
   <td> 작음<br /> </td> 
   <td> 업데이트<br /> </td> 
   <td> 이 테이블에는 SMTP 오류 적격 관련 정보가 포함됩니다. 크기는 꽤 작지만 상당히 업데이트되므로 이 표의 인덱스는 빠르게 조각하는 경향이 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEmailErrorStat<br /> </td> 
   <td> 중간<br /> </td> 
   <td> 삽입, 업데이트, 삭제<br /> </td> 
   <td> 이 테이블에는 도메인별로 정렬된 SMTP 오류에 대한 합계가 포함되어 있습니다. 처음에는 정리 작업이 오래되면 정리 작업에 의해 집계된 세부 정보가 포함됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogMid(중간 소싱 인스턴스에서)<br /> </td> 
   <td> 큼<br /> </td> 
   <td> 삽입, 업데이트, 삭제<br /> </td> 
   <td> 5.10 이상 인스턴스를 중간 소싱 인스턴스로 사용하는 경우에만 해당됩니다. 이것은 데이터베이스에서 가장 큰 테이블 중 하나입니다. 전송된 메시지당 한 개의 레코드가 있으며 이러한 레코드는 삽입되고, 배달 상태를 추적하도록 업데이트되며, 기록이 삭제될 때 삭제됩니다. 중간 소싱을 사용할 때 권장 사항은 내역을 제한(보통 2개월 미만)하는 것이므로, 이 테이블은 크기 측면에서 적절히 유지되지만(6,000만 개의 행에 대해 30개 미만, 데이터+인덱스), 때때로 다시 구성하는 것이 매우 중요합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRcp(NmsRecipient 테이블을 사용하는 경우) <br /> </td> 
   <td> 큼<br /> </td> 
   <td> 삽입, 업데이트, 삭제<br /> </td> 
   <td> 이 테이블이 시스템에서 가장 큰 테이블입니다. 전송된 메시지당 한 개의 레코드가 있으며 이러한 레코드는 삽입되고, 배달 상태를 추적하도록 업데이트되며, 기록이 삭제될 때 삭제됩니다. 5.10 버전에서는 SMTP 메시지 텍스트가 5.10 버전의 NmsBroadLogMsg 테이블에서 팩터링되므로 이 테이블은 4.05(NmsBroadLog)에 해당하는 것보다 작습니다. 그러나 이 표를 정기적으로 다시 색인화하고(다음으로 시작하는 격주에 한 번씩), 때때로(또는 성능에 영향을 주는 경우) 다시 구성하는 것이 중요합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> YyyBroadLogXxx(외부 수신자 테이블을 사용하는 경우)<br /> </td> 
   <td> 큼<br /> </td> 
   <td> 삽입, 업데이트, 삭제<br /> </td> 
   <td> NmsBroadLogRcp와 동일하지만 외부 받는 사람 테이블입니다. 배달 매핑 시 Yyy 및 Xxx 값을 조정하십시오.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRcp(NmsRecipient 테이블을 사용하는 경우) <br /> </td> 
   <td> 큼<br /> </td> 
   <td> 삽입, 삭제<br /> </td> 
   <td> 추적 로그는 작업 내역을 삭제할 때 삽입되고 삭제되지만 업데이트되지 않습니다. 볼륨은 데이터 보존 기간에 따라 다릅니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> YyyTrackingLogXxx(외부 받는 사람 테이블을 사용하는 경우)<br /> </td> 
   <td> 큼<br /> </td> 
   <td> 삽입, 삭제<br /> </td> 
   <td> NmsTrackingLogRcp와 동일하지만 외부 받는 사람 테이블입니다. 배달 매핑에 사용된 값과 함께 Yyy 및 Xxx를 조정합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRtEvent(메시지 센터 실행 인스턴스)<br /> </td> 
   <td> 큼<br /> </td> 
   <td> 삽입, 업데이트, 삭제<br /> </td> 
   <td> 다른 브로드로그 테이블과 유사하지만 NmsRecipient 대신 NmsRtEvent가 있는 경우<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRtEvent( 메시지 센터 실행 인스턴스)<br /> </td> 
   <td> 큼<br /> </td> 
   <td> 삽입, 삭제<br /> </td> 
   <td> 다른 trackingLog 테이블과 유사하지만 NmsRecipient 대신 NmsRtEvent 테이블이 있는 경우<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsRtEvent(메시지 센터 실행 인스턴스)<br /> </td> 
   <td> 큼<br /> </td> 
   <td> 삽입, 업데이트, 삭제<br /> </td> 
   <td> 메시지 센터 이벤트 큐가 포함된 표. 이러한 이벤트의 상태는 처리 시 메시지 센터에 의해 업데이트됩니다. 삭제 작업은 제거 중에 수행됩니다. 이 표의 색인을 정기적으로 다시 만들고 다시 구성하는 것이 좋습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEventHisto(메시지 센터 제어 인스턴스)<br /> </td> 
   <td> 큼<br /> </td> 
   <td> 삽입, 업데이트, 삭제<br /> </td> 
   <td> NmsRtEvent와 유사합니다. 이 표에서는 모든 실행 인스턴스에서 모든 이벤트를 보관합니다. 실시간 프로세스가 아닌 보고서에서만 사용됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMobileApp<br /> </td> 
   <td> 매우 작음<br /> </td> 
   <td> 삽입, 업데이트, 삭제<br /> </td> 
   <td> 모바일 응용 프로그램 및 해당 구성을 포함하는 표입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAppSubscriptionRcp<br /> </td> 
   <td> 큼<br /> </td> 
   <td> 삽입, 업데이트<br /> </td> 
   <td> 알림을 보내는 데 사용되는 모바일 장치(주소)의 식별자를 포함하는 표(수신자 테이블과 유사).<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogAppSubRcp<br /> </td> 
   <td> 큼<br /> </td> 
   <td> 삽입, 업데이트, 삭제<br /> </td> 
   <td> 다른 브로드로그 테이블과 유사하지만 NmsRecipient 대신 NmsappSubscriptionRcp가 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogAppSubRcp<br /> </td> 
   <td> 큼<br /> </td> 
   <td> 삽입, 삭제<br /> </td> 
   <td> 다른 trackingLog 테이블과 유사하지만 NmsRecipient 대신 NmsappSubscriptionRcp 테이블이 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkSessionInfo<br /> </td> 
   <td> 작음<br /> </td> 
   <td> 삽입, 삭제<br /> </td> 
   <td> 사용자 세션이 포함된 표. 삽입 및 삭제 수가 매우 중요합니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 고객 테이블 {#customer-tables}

위의 목록 외에, 플랫폼 설정 중에 고객이 만든 테이블(Adobe Campaign 데이터 모델에 존재하지 않음)도 단편화되어 있을 수 있습니다. 특히 데이터 로드 또는 동기화 절차 중에 자주 업데이트되는 경우 더욱 그렇습니다. 이러한 테이블은 기본 Adobe Campaign 데이터 모델의 일부일 수 있습니다(예: **NmsRecipient**). 이 경우 Adobe Campaign 플랫폼의 관리자가 특정 데이터베이스 모델에 대한 감사를 수행하여 이러한 사용자 정의 테이블을 찾습니다. 이러한 테이블이 유지 관리 절차에서 반드시 명시적으로 언급되는 것은 아닙니다.
