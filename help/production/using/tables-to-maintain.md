---
product: campaign
title: 유지 관리할 테이블
description: 유지 관리할 테이블
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용됩니다."
badge-v7-prem: label="온-프레미스 및 하이브리드" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: 194f12de-4671-4a56-8cdc-cd5e3dac147b
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '1148'
ht-degree: 3%

---

# 유지 관리할 테이블{#tables-to-maintain}



유지 관리할 테이블 목록은 사용 중인 Adobe Campaign 버전, 사용 방법 및 데이터 모델 구성에 따라 다릅니다.

다음 목록에는 조각화가 가장 많이 적용되는 표만 포함되어 있습니다. 그 영향은 다음과 같습니다.

* 디스크 공간 과소비로 인해 데이터베이스 액세스에 영향을 미침
* 정기적으로 업데이트되지 않은 인덱스이므로 쿼리 성능이 느려집니다.

## Adobe Campaign 테이블 {#adobe-campaign-tables}

<table> 
 <thead> 
  <tr> 
   <th> <strong>테이블 이름 </strong><br /> </th> 
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
   <td> 게재 작업당 하나의 레코드가 있습니다. 단일 레코드는 게재 진행률을 반영하도록 여러 번 업데이트할 수 있으므로 이 테이블의 색인은 빠르게 조각화되는 경향이 있습니다. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryPart<br /> </td> 
   <td> 미디엄<br /> </td> 
   <td> 삽입, 업데이트, 삭제<br /> </td> 
   <td> 게재를 준비하는 동안 레코드가 삽입되는 작업 테이블입니다. 그런 다음 게재 중에 업데이트되고, 게재가 완료되면 최종적으로 삭제됩니다.<br /> 이 표는 평균 크기가 상당히 제한되어 있음에도 불구하고 빠르게 조각화되는 경향이 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMirrorPageInfo<br /> </td> 
   <td> 대형<br /> </td> 
   <td> 삽입, 삭제<br /> </td> 
   <td> 이 표에는 개인화된 미러 페이지를 생성하는 데 필요한 정보가 포함되어 있습니다. 여기에는 메모(CLOB) 필드가 포함되어 있으며, 따라서 매우 큰 경향이 있습니다. 볼륨은 보관된 미러 페이지 기록에 정비례합니다. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryStat<br /> </td> 
   <td> 미디엄<br /> </td> 
   <td> 삽입, 업데이트, 삭제<br /> </td> 
   <td> 이 표에는 게재 프로세스에 대한 통계가 포함되어 있습니다. 그 기록은 정기적으로 갱신된다. <br /> </td> 
  </tr> 
  <tr> 
   <td> Nms 주소<br /> </td> 
   <td> 미디엄<br /> </td> 
   <td> 업데이트, 삽입<br /> </td> 
   <td> 이 표에는 이메일 주소에 대한 정보가 포함되어 있습니다. 격리 프로세스의 일부로 자주 업데이트됩니다(첫 번째 게재 오류 시 레코드가 만들어지고, 게재가 성공하면 카운터가 변경되어 삭제됨). <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflow<br /> </td> 
   <td> 작음<br /> </td> 
   <td> 업데이트<br /> </td> 
   <td> 워크플로우 인스턴스당 하나의 레코드가 있으므로 레코드는 매우 적습니다. 그러나 이 테이블은 상태와 진행률을 반영하도록 정기적으로 업데이트됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowTask<br /> </td> 
   <td> 작음<br /> </td> 
   <td> 삽입, 업데이트, 삭제<br /> </td> 
   <td> 워크플로우 활동을 실행할 때마다 이 표에 레코드가 생성됩니다. 삭제 메커니즘은 만료되면 삭제됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowEvent<br /> </td> 
   <td> 작음<br /> </td> 
   <td> 삽입, 업데이트, 삭제<br /> </td> 
   <td> 워크플로우의 작업 간에 활성화된 각 전환은 이 표에 레코드를 만듭니다. 삭제 메커니즘은 만료되면 삭제됩니다. <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowJob<br /> </td> 
   <td> 매우 작음 <br /> </td> 
   <td> 삽입, 업데이트, 삭제<br /> </td> 
   <td> 이 테이블은 워크플로우 엔진에만 해당됩니다. 워크플로우에 명령(예: 시작, 중지, 일시 중지)을 전송할 수 있습니다. 이 테이블은 작지만 워크플로우에 연결된 트랜잭션 표를 제거하는 동안 고려됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLog<br /> </td> 
   <td> 가장 크게<br /> </td> 
   <td> 삽입, 업데이트, 삭제<br /> </td> 
   <td> 이것은 시스템에서 가장 큰 테이블입니다. 보낸 메시지당 하나의 레코드가 있으며 이러한 레코드는 삽입되고 업데이트되어 게재 상태를 추적하며 기록이 삭제될 때 삭제됩니다. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLog<br /> </td> 
   <td> 대형<br /> </td> 
   <td> 삽입, 삭제<br /> </td> 
   <td> 추적 로그는 기록이 삭제되더라도 업데이트되지 않을 때 삽입 및 삭제됩니다. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadlogMsg <br /> </td> 
   <td> 작음<br /> </td> 
   <td> 업데이트<br /> </td> 
   <td> 이 표에는 SMTP 오류 자격에 사용되는 정보가 포함되어 있습니다. 상당히 작지만 대량으로 업데이트되므로 이 테이블의 색인은 빠르게 조각화되는 경향이 있습니다. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEmailErrorStat<br /> </td> 
   <td> 미디엄<br /> </td> 
   <td> 삽입, 업데이트, 삭제<br /> </td> 
   <td> 이 표에는 도메인별로 정렬된 SMTP 오류에 대한 합계가 포함되어 있습니다. 처음에는 오래된 정리 작업이 되면 해당 작업에 의해 집계되는 자세한 정보가 포함됩니다. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogMid(중간 소싱 인스턴스)<br /> </td> 
   <td> 대형<br /> </td> 
   <td> 삽입, 업데이트, 삭제<br /> </td> 
   <td> 5.10(또는 이상) 인스턴스가 중간 소싱 인스턴스로 사용되는 경우에만 해당합니다. 데이터베이스에서 가장 큰 테이블 중 하나입니다. 보낸 메시지당 하나의 레코드가 있으며 이러한 레코드는 삽입되고 업데이트되어 게재 상태를 추적하며 기록이 삭제될 때 삭제됩니다. 중간 소싱을 사용할 때 권장 사항은 내역을 제한하는 것입니다(일반적으로 2개월 미만). 따라서 이 테이블은 크기 측면에서 합리적으로 유지되지만(6,000만 행에 대해 300개 미만, 데이터+색인), 간혹 다시 빌드하는 것이 매우 중요합니다. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRcp(NmsRecipient 테이블이 사용되는 경우) <br /> </td> 
   <td> 대형<br /> </td> 
   <td> 삽입, 업데이트, 삭제<br /> </td> 
   <td> 이것은 시스템에서 가장 큰 테이블입니다. 보낸 메시지당 하나의 레코드가 있으며 이러한 레코드는 삽입되고 업데이트되어 게재 상태를 추적하며 기록이 삭제될 때 삭제됩니다. 5.10 버전에서는 SMTP 메시지 텍스트가 5.10 버전의 NmsBroadLogMsg 테이블에서 인수분해되므로 이 테이블은 4.05(NmsBroadLog)의 해당 테이블보다 작습니다. 그러나 이 표를 정기적으로(2주마다 시작하여) 다시 색인화하고, 때때로(한 달에 한 번 또는 성능에 영향을 미칠 때) 완전히 다시 빌드하는 것이 중요합니다. <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyBroadLogXxx (외부 수신자 테이블이 사용되는 경우)<br /> </td> 
   <td> 대형<br /> </td> 
   <td> 삽입, 업데이트, 삭제<br /> </td> 
   <td> NmsBroadLogRcp와 동일하지만 외부 수신자 테이블이 있습니다. 게재 매핑의 값으로 Yyy와 Xxx를 조정하십시오. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRcp(NmsRecipient 테이블을 사용하는 경우) <br /> </td> 
   <td> 대형<br /> </td> 
   <td> 삽입, 삭제<br /> </td> 
   <td> 추적 로그는 기록이 삭제되더라도 업데이트되지 않을 때 삽입 및 삭제됩니다. 볼륨은 데이터 보존 기간에 따라 다릅니다. <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyTrackingLogXxx (외부 수신자 테이블이 사용되는 경우)<br /> </td> 
   <td> 대형<br /> </td> 
   <td> 삽입, 삭제<br /> </td> 
   <td> NmsTrackingLogRcp와 동일하지만 외부 수신자 테이블이 있습니다. 게재 매핑에 사용된 값으로 Yyy 및 Xxx를 조정하십시오. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRtEvent(메시지 센터 실행 인스턴스)<br /> </td> 
   <td> 대형<br /> </td> 
   <td> 삽입, 업데이트, 삭제<br /> </td> 
   <td> 다른 Broadlog 테이블과 비슷하지만 NmsRecipient 대신 NmsRtEvent가 사용됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRtEvent( 메시지 센터 실행 인스턴스)<br /> </td> 
   <td> 대형<br /> </td> 
   <td> 삽입, 삭제<br /> </td> 
   <td> 다른 trackingLog 테이블과 비슷하지만 NmsRecipient 대신 NmsRtEvent 테이블이 사용됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsRtEvent(메시지 센터 실행 인스턴스)<br /> </td> 
   <td> 대형<br /> </td> 
   <td> 삽입, 업데이트, 삭제<br /> </td> 
   <td> 메시지 센터 이벤트 큐가 포함된 테이블. 이러한 이벤트가 처리되면 메시지 센터에서 해당 이벤트의 상태를 업데이트합니다. 삭제 작업은 삭제 중에 수행됩니다. 이 테이블의 인덱스를 정기적으로 다시 만들고 다시 빌드하는 것이 좋습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEventHisto(메시지 센터 제어 인스턴스)<br /> </td> 
   <td> 대형<br /> </td> 
   <td> 삽입, 업데이트, 삭제<br /> </td> 
   <td> NmsRtEvent와 유사합니다. 이 테이블은 모든 실행 인스턴스의 모든 이벤트를 보관합니다. 실시간 프로세스가 없으며 보고서에서만 사용됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMobileApp<br /> </td> 
   <td> 매우 작음<br /> </td> 
   <td> 삽입, 업데이트, 삭제<br /> </td> 
   <td> 모바일 애플리케이션 및 해당 구성을 포함하는 표입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAppSubscriptionRcp<br /> </td> 
   <td> 대형<br /> </td> 
   <td> 삽입, 업데이트<br /> </td> 
   <td> 알림을 전송하는 데 사용되는 모바일 장치(주소)의 식별자를 포함하는 테이블(수신자 테이블과 유사).<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogAppSubRcp<br /> </td> 
   <td> 대형<br /> </td> 
   <td> 삽입, 업데이트, 삭제<br /> </td> 
   <td> 다른 Broadlog 테이블과 비슷하지만 NmsRecipient 대신 NmsappSubscriptionRcp가 사용됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogAppSubRcp<br /> </td> 
   <td> 대형<br /> </td> 
   <td> 삽입, 삭제<br /> </td> 
   <td> 다른 trackingLog 테이블과 유사하지만 NmsRecipient 대신 NmsappSubscriptionRcp 테이블이 사용됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkSessionInfo<br /> </td> 
   <td> 작음<br /> </td> 
   <td> 삽입, 삭제<br /> </td> 
   <td> 사용자 세션을 포함하는 표입니다. 삽입 및 삭제 횟수는 매우 중요합니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 고객 테이블 {#customer-tables}

위의 목록 외에도, 플랫폼 설정 중에 고객이 만든 (Adobe Campaign 데이터 모델에 존재하지 않는) 테이블이 포함된 테이블은 특히 데이터 로드 또는 동기화 절차 중에 자주 업데이트되는 경우 조각화의 영향을 받을 수 있습니다. 이러한 테이블은 기본 Adobe Campaign 데이터 모델의 일부일 수 있습니다(예: **NmsRecipient**). 이 경우 이러한 사용자 정의 테이블을 찾기 위해 특정 데이터베이스 모델을 감사하는 것은 Adobe Campaign 플랫폼 관리자의 책임입니다. 이러한 표는 유지 관리 절차에서 명시적으로 언급되지 않습니다.
