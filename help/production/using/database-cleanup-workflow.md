---
title: 데이터베이스 정리 워크플로우
description: 오래된 데이터가 자동으로 정리되는 방법 살펴보기
page-status-flag: never-activated
uuid: a7478641-cdf6-4bd4-9dd7-0c84416c9de6
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: data-processing
discoiquuid: 6b188d78-abb4-4f03-80b9-051ce960f43c
translation-type: tm+mt
source-git-commit: 2a82493deada11cb22ef37d215b6eae8274ce890
workflow-type: tm+mt
source-wordcount: '2910'
ht-degree: 0%

---


# 데이터베이스 정리 워크플로우{#database-cleanup-workflow}

## 소개 {#introduction}

노드를 통해 **[!UICONTROL Database cleanup]** 액세스할 수 있는 작업 **[!UICONTROL Administration > Production > Technical workflows]** 과정에서는 오래된 데이터를 삭제하여 데이터베이스의 기하급수적인 증가를 방지할 수 있습니다. 사용자 개입 없이 워크플로우가 자동으로 트리거됩니다.

![](assets/ncs_cleanup_workflow.png)

## 구성 {#configuration}

데이터베이스 정리는 두 가지 수준으로 구성됩니다.을 클릭합니다.

### 워크플로우 스케줄러 {#the-scheduler}

>[!NOTE]
>
>For more on the scheduler, refer to [this section](../../workflow/using/scheduler.md).

기본적으로 워크플로우는 매일 오전 4시에 시작하도록 구성되어 있습니다. **[!UICONTROL Database cleanup]** 스케줄러를 사용하면 빈도를 트리거하는 워크플로우를 변경할 수 있습니다. 다음 주파수를 사용할 수 있습니다.

* **[!UICONTROL Several times a day]**
* **[!UICONTROL Daily]**
* **[!UICONTROL Weekly]**
* **[!UICONTROL Once]**

![](assets/ncs_cleanup_scheduler.png)

>[!CAUTION]
>
>워크플로우가 스케줄러에 정의된 날짜 및 시간에 **[!UICONTROL Database cleanup]** 시작되도록 워크플로우 엔진(wfserver)을 시작해야 합니다. 그렇지 않으면 다음 번에 워크플로 엔진이 시작될 때까지 데이터베이스 청소가 수행되지 않습니다.

### 배포 마법사 {#deployment-wizard}

메뉴 **[!UICONTROL Deployment wizard]**&#x200B;를 통해 액세스되는 **[!UICONTROL Tools > Advanced]** 아이콘을 사용하여 데이터가 저장되는 기간을 구성할 수 있습니다. 값은 일 단위로 표현됩니다. 이러한 값이 변경되지 않으면 워크플로우는 기본값을 사용합니다.

![](assets/ncs_cleanup_deployment-wizard.png)

창의 필드는 다음 옵션과 **[!UICONTROL Purge of data]** 일치합니다. 이러한 작업은 워크플로우에 의해 실행되는 일부 작업에 **[!UICONTROL Database cleanup]** 사용됩니다.

* 통합 추적: **NmsCleanup_TrackingStatPurgeDelay** (추적 로그 [정리 참조](#cleanup-of-tracking-logs))
* 배달 로그: **NmsCleanup_BroadLogPurgeDelay** (배달 로그 [정리 참조](#cleanup-of-delivery-logs))
* 추적 로그: **NmsCleanup_TrackingLogPurgeDelay** (추적 로그 [정리 참조](#cleanup-of-tracking-logs))
* 삭제된 배달: **NmsCleanup_RepetedDeliveryPurgeDelay** (삭제 또는 재활용될 [배달 정리 참조](#cleanup-of-deliveries-to-be-deleted-or-recycled))
* 가져오기 거부: **NmsCleanup_RejectsPurgeDelay** ( [가져오기로 생성된 거부의 정리 참조](#cleanup-of-rejects-generated-by-imports-))
* 방문자 프로필: **NmsCleanup_VisitorPurgeDelay** ( [방문자 정리 참조](#cleanup-of-visitors))
* 제안: **NmsCleanup_ProvisionPurgeDelay** (프로필 [정리 참조](#cleanup-of-propositions))

   >[!NOTE]
   >
   >이 **[!UICONTROL Offer propositions]** 필드는 **상호 작용** 모듈이 설치된 경우에만 사용할 수 있습니다.

* 이벤트: **NmsCleanup_EventPurgeDelay** (만료된 이벤트 [정리 참조](#cleansing-expired-events))
* 보관된 이벤트: **NmsCleanup_EventHitoPurgeDelay** (만료된 이벤트 [정리 참조](#cleansing-expired-events))

   >[!NOTE]
   >
   >**[!UICONTROL Events]** 및 **[!UICONTROL Archived events]** 필드는 **메시지 센터** 모듈이 설치되어 있는 경우에만 사용할 수 있습니다.

* 감사 추적: **XtkCleanup_AuditTrailPurgeDelay** (감사 추적 [정리 참조](#cleanup-of-audit-trail))

워크플로우에 의해 실행되는 모든 **[!UICONTROL Database cleanup]** 작업은 다음 섹션에 설명되어 있습니다.

## 데이터베이스 정리 워크플로에서 수행하는 작업 {#tasks-carried-out-by-the-database-cleanup-workflow}

워크플로우 스케줄러에서 정의된 날짜 및 시간(스케줄러 [](#the-scheduler)참조)에서 워크플로우 엔진은 데이터베이스 정리 프로세스를 시작합니다. 데이터베이스 정리는 데이터베이스에 연결하여 아래 표시된 시퀀스에서 작업을 실행합니다.

>[!CAUTION]
>
>이러한 작업 중 하나가 실패하면 다음 작업이 실행되지 않습니다.\
>LIMIT 특성이 **있는** SQL 쿼리는 모든 정보가 처리될 때까지 반복적으로 실행됩니다.

>[!NOTE]
>
>데이터베이스 정리 워크플로에서 수행하는 작업을 설명하는 아래 섹션은 데이터베이스 관리자 또는 SQL 언어에 익숙한 사용자를 위해 예약되어 있습니다.

### 정리 삭제 목록 {#lists-to-delete-cleanup}

워크플로우에 의해 실행되는 첫 번째 작업은 **[!UICONTROL Database cleanup]** **deleteStatus!= NmsGroup의 0** **속성입니다**. 이러한 그룹에 연결된 레코드와 다른 테이블에 존재하는 레코드도 삭제됩니다.

1. 삭제할 목록은 다음 SQL 쿼리를 사용하여 복구됩니다.

   ```
   SELECT iGroupId, sLabel, iType FROM NmsGroup WHERE iDeleteStatus <> 0 OR tsExpirationDate <= GetDate() 
   ```

1. 각 목록에는 다른 테이블에 대한 여러 링크가 있습니다. 이러한 모든 링크는 다음 쿼리를 사용하여 일괄 삭제됩니다.

   ```
   DELETE FROM $(relatedTable) WHERE iGroupId=$(l) IN (SELECT iGroupId FROM $(relatedTable) WHERE iGroupId=$(l) LIMIT 5000) 
   ```

   여기서 **$(relatedTable)****는** NmsGroup **과 관련된 테이블이고** $(l)은 목록식별자입니다.

1. 목록이 &#39;목록&#39; 유형 목록이면 연결된 테이블이 다음 쿼리를 사용하여 삭제됩니다.

   ```
   DROP TABLE grp$(l)
   ```

1. 작업에서 **복구된 모든** 선택 유형 목록은 다음 쿼리를 사용하여 삭제됩니다.

   ```
   DELETE FROM NmsGroup WHERE iGroupId=$(l) 
   ```

   여기서 **$(l)** 은 목록 식별자입니다.

### 삭제 또는 재활용 될 납품 정리 {#cleanup-of-deliveries-to-be-deleted-or-recycled}

이 작업을 수행하면 삭제 또는 재활용될 모든 게재를 삭제합니다.

1. 삭제 상태 **[!UICONTROL Database cleanup]** 필드가 값 **또는** 삭제 날짜 **[!UICONTROL Yes]** 가 해당 배포 마법사의 정의된 기간(NmsCleanup_RepetedDeliveryPurgeDelayDelayInDependingDependingDependingDeploy) 필드 **[!UICONTROL Recycled]** **[!UICONTROL Deleted deliveries]******&#x200B;보다 빠른 모든 배달을 선택합니다. For more on this, refer to [Deployment wizard](#deployment-wizard). 이 기간은 현재 서버 날짜와 관련하여 계산됩니다.
1. 각 중간 소싱 서버에 대해 삭제할 납품 목록을 선택합니다.
1. 워크플로우는 **[!UICONTROL Database cleanup]** 배달 로그, 첨부 파일, 미러 페이지 정보 및 기타 모든 관련 데이터를 삭제합니다.
1. 해당 배달을 영원히 삭제하기 전에 워크플로우는 다음 테이블에서 연결된 정보를 삭제합니다.

   * 배달 제외 테이블(**NmsDlvExclusion**)에서 다음 쿼리가 사용됩니다.

      ```
      DELETE FROM NmsDlvExclusion WHERE iDeliveryId=$(l)
      ```

      여기서 **$(l)** 은 배달의 식별자입니다.

   * 쿠폰 테이블(**NmsCouponValue**)에서 다음 쿼리가 사용됩니다(대량 삭제 포함).

      ```
      DELETE FROM NmsCouponValue WHERE iMessageId IN (SELECT iMessageId FROM NmsCouponValue WHERE EXISTS (SELECT B.iBroadLogId FROM $(BroadLogTableName) B WHERE B.iDeliveryId = $(l) AND B.iBroadLogId = iMessageId ) LIMIT 5000)
      ```

      여기서 **$(l)** 은 배달의 식별자입니다.

   * 배달 로그 테이블(**NmsBroadlogXxx**)에서 대량 삭제가 20,000개의 레코드 배치로 실행됩니다.
   * 오퍼 제안 표(**NmsProgendationXxx**)에서는 대량 삭제가 20,000개의 레코드로 일괄적으로 실행됩니다.
   * 추적 로그 테이블(**NmsTrackinglogXxx**)에서 대량 삭제가 20,000개의 레코드로 일괄적으로 실행됩니다.
   * 배달 조각 테이블(**NmsDeliveryPart**)에서 대량 삭제가 500,000개의 레코드로 일괄적으로 실행됩니다. 이 표에는 배달될 나머지 메시지에 대한 개인화 정보가 나와 있습니다.
   * 미러 페이지 데이터 조각 테이블(**NmsMirrorPageInfo**)에서 만료된 배달 부품과 완성된 또는 취소된 부품의 경우 대량 삭제가 20,000개의 레코드 배치로 실행됩니다. 이 표에는 미러 페이지 생성에 사용되는 모든 메시지에 대한 개인화 정보가 나와 있습니다.
   * 미러 페이지 검색 테이블(**NmsMirrorPageSearch**)에서 대량 삭제가 20,000개의 레코드 배치로 실행됩니다. 이 표는 NmsMirrorPageInfo 테이블에 저장된 개인화 정보에 대한 액세스를 제공하는 **검색** 색인입니다.
   * 일괄 처리 로그 테이블(**XtkJobLog**)에서 대량 삭제가 20,000개의 레코드로 일괄적으로 실행됩니다. 이 표에는 삭제할 배달 로그가 포함되어 있습니다.
   * 배달 URL 추적 테이블(**NmsTrackingUrl**)에서 다음 쿼리가 사용됩니다.

      ```
      DELETE FROM NmsTrackingUrl WHERE iDeliveryId=$(l)
      ```

      여기서 **$(l)** 은 배달의 식별자입니다.

      이 표에는 추적을 활성화하기 위해 삭제할 배달에서 찾은 URL이 포함되어 있습니다.

1. 배달이 배달 테이블에서&#x200B;**삭제됩니다(NmsDelivery**).

   ```
   DELETE FROM NmsDelivery WHERE iDeliveryId = $(l)
   ```

   여기서 **$(l)** 은 배달의 식별자입니다.

#### 중간 소싱을 사용한 납품 {#deliveries-using-mid-sourcing}

또한 **[!UICONTROL Database cleanup]** 워크플로우는 중간 소싱 서버에서 납품도 삭제합니다.

1. 이를 위해 워크플로우는 각 배달이 비활성(상태에 따라)인지 확인합니다. 게재가 활성 상태인 경우 삭제되기 전에 중단됩니다. 검사는 다음 쿼리를 실행하여 수행됩니다.

   ```
   SELECT iState FROM NmsDelivery WHERE iDeliveryId = $(l) AND iState <> 100;
   ```

   여기서 **$(l)** 은 배달의 식별자입니다.

1. 상태 값이 **[!UICONTROL Start pending]** , **[!UICONTROL In progress]** , **[!UICONTROL Recovery pending]** , **[!UICONTROL Recovery in progress]** **[!UICONTROL Pause requested]** , **[!UICONTROL Pause in progress]** , **[!UICONTROL Paused]** 또는(값 51, 55, 61, 62, 71, 72, 75)이면 배달이 중지되고 작업에 연결된 정보가 삭제됩니다.

### 만료된 배달 정리 {#cleanup-of-expired-deliveries}

이 작업은 유효 기간이 만료된 배달을 중지합니다.

1. 워크플로우는 **[!UICONTROL Database cleanup]** 만료된 배달 목록을 만듭니다. 이 목록에는 상태가 아닌 만료된 배달과 10,000개 이상의 처리되지 않은 메시지가 있는 최근 중단된 배달이 모두 포함됩니다. **[!UICONTROL Finished]** 다음 쿼리가 사용됩니다.

   ```
   SELECT iDeliveryId, iState FROM NmsDelivery WHERE iDeleteStatus=0 AND iIsModel=0 AND iDeliveryMode=1 AND ( (iState >= 51 AND iState < 85 AND tsValidity IS NOT NULL AND tsValidity < $(currentDate) ) OR (iState = 85 AND DateMinusDays(15) < tsLastModified AND iToDeliver - iProcessed >= 10000 ))
   ```

   배달 모드 1이 **모드 1과** 일치하면, 상태 51 **[!UICONTROL Mass delivery]** 이 상태와 일치하고, **state 85는 상태** **[!UICONTROL Start pending]** **** **[!UICONTROL Stopped]** 와 일치하며, 배달 서버에서 대량으로 업데이트되는 배달 로그의 최대 개수는 10,000과 같습니다.

1. 그런 다음 워크플로우에는 중간 소싱을 사용하는 최근 만료된 배달 목록이 포함됩니다. 중간 소싱 서버를 통해 아직 배달 로그가 복구되지 않은 배달은 제외됩니다.

   다음 쿼리가 사용됩니다.

   ```
   SELECT iDeliveryId, tsValidity, iMidRemoteId, mData FROM NmsDelivery WHERE (iDeliveryMode = 4 AND (iState = 85 OR iState = 95) AND tsValidity IS NOT NULL AND (tsValidity < SubDays(GetDate() , 15) OR tsValidity < $(DateOfLastLogPullUp)) AND tsLastModified > SubDays(GetDate() , 15))
   ```

1. 다음 쿼리는 날짜별로 배달 필터링을 위해 외부 계정이 여전히 활성 상태인지 여부를 검색하는 데 사용됩니다.

   ```
   SELECT iExtAccountId FROM NmsExtAccount WHERE iActive<>0 AND sName=$(providerName)
   ```

1. 만료된 배달 목록에서 상태가 **[!UICONTROL Pending]** , , 으로 전환 **[!UICONTROL Delivery cancelled]** 및 이 목록의 모든 배달이 로 전환됩니다 **[!UICONTROL Finished]** .

   다음 쿼리가 사용됩니다.

   ```
   UPDATE $(BroadLogTableName) SET tsLastModified=$(curdate), iStatus=7, iMsgId=$(bl) WHERE iDeliveryId=$(dl) AND iStatus=6
   ```

   여기서 **$(date)** 는 데이터베이스 서버의 현재 날짜이고,$(bl) **은 배달 메시지의 식별자입니다.** $(dl) **배달 ID는 배달 ID이고,** 배달 상태 6배달 상태 6은와 **** **[!UICONTROL Pending]** **** **[!UICONTROL Delivery cancelled]** 는 상태 7ccurrency가 상태와 일치함.

   ```
   UPDATE NmsDelivery SET iState = 95, tsLastModified = $(curdate), tsBroadEnd = tsValidity WHERE iDeliveryId = $(dl)
   ```

   여기서 **배달 상태 95** 는 **[!UICONTROL Finished]** 상태와 일치하고 **$(dl)** 은 배달의 식별자입니다.

1. 오래된 배달의 모든 조각(**deliveryParts**)이 삭제되고 진행 중인 모든 오래된 통지 배달이 삭제됩니다. 이 두 작업 모두에 대량 삭제가 사용됩니다.

   다음 쿼리가 사용됩니다.

   ```
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE iDeliveryId IN (SELECT iDeliveryId FROM NmsDelivery WHERE iState=95 OR iState=85) LIMIT 5000)
   ```

   ```
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE tsValidity < $(curDate) LIMIT 500000)
   ```

   배달 **상태 95가** 상태와 일치하면 배달 상태 85 **[!UICONTROL Finished]** 이 **상태와 일치하고, curDate** **[!UICONTROL Stopped]** **** 는 현재 서버 날짜입니다.

### 미러 페이지 정리 {#cleanup-of-mirror-pages}

이 작업은 게재에 사용되는 웹 리소스(미러 페이지)를 삭제합니다.

1. 먼저, 삭제할 배달 목록은 다음 쿼리를 사용하여 복구됩니다.

   ```
   SELECT iDeliveryId, iNeedMirrorPage FROM NmsDelivery WHERE iWebResPurged = 0 AND tsWebValidity IS NOT NULL AND tsWebValidity < $(curdate)"
   ```

   여기서 **$(curDate)** 는 현재 서버 날짜입니다.

1. 그런 **다음 이전에 복구한 배달의 식별자를 사용하여 필요한 경우 NmsMirrorPageInfo** 테이블을 삭제합니다. 대량 삭제는 다음 쿼리를 생성하는 데 사용됩니다.

   ```
   DELETE FROM NmsMirrorPageInfo WHERE iMirrorPageInfoId IN (SELECT iMirrorPageInfoId FROM NmsMirrorPageInfo WHERE iDeliveryId = $(dl)) LIMIT 5000)
   ```

   ```
   DELETE FROM NmsMirrorPageSearch WHERE iMessageId IN (SELECT iMessageId FROM NmsMirrorPageSearch WHERE iDeliveryId = $(dl)) LIMIT 5000)
   ```

   여기서 **$(dl)** 은 배달의 식별자입니다.

1. 그런 다음 배달 로그에 항목이 추가됩니다.
1. 그런 다음 제거된 배달이 식별되므로 나중에 다시 처리할 필요가 없습니다. 다음 쿼리가 실행됩니다.

   ```
   UPDATE NmsDelivery SET iWebResPurged = 1 WHERE iDeliveryId IN ($(strIn))
   ```

   여기서 **$(strIn)** 은 배달 식별자 목록입니다.

### 작업 테이블 정리 {#cleanup-of-work-tables}

이 작업은 데이터베이스에서 삭제되며, 상태는 **[!UICONTROL Being edited]** , **[!UICONTROL Stopped]****[!UICONTROL Deleted]** 인 게재와 일치하는 모든 작업 테이블이 삭제됩니다.

1. 이름이 wkDlv_ **로 시작하는 테이블** 목록은 다음 쿼리(postgresql)로 먼저 복구됩니다.

   ```
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkDlv_') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. 진행 중인 워크플로우에서 사용하는 표는 제외됩니다. 이를 위해 진행 중인 배달 목록은 다음 쿼리를 사용하여 복구됩니다.

   ```
   SELECT iDeliveryId FROM NmsDelivery WHERE iDeliveryId<>0 AND iDeleteStatus=0 AND iState NOT IN (0,85,100);
   ```

   여기서 0은 **[!UICONTROL Being edited]** 배달 상태와 일치하는 값이고 85는 **[!UICONTROL Stopped]** 상태와 일치하고 100은 **[!UICONTROL Deleted]** 상태와 일치합니다.

1. 더 이상 사용되지 않는 테이블은 다음 쿼리를 사용하여 삭제됩니다.

   ```
   DROP TABLE wkDlv_15487_1;
   ```

### 가져오기로 생성된 거부 정리 {#cleanup-of-rejects-generated-by-imports-}

이 단계에서는 가져오는 동안 모든 데이터가 처리되지 않은 레코드를 삭제할 수 있습니다.

1. 대량 삭제는 다음 쿼리와 함께 **XtkReject** 테이블에서 수행됩니다.

   ```
   DELETE FROM XtkReject WHERE iRejectId IN (SELECT iRejectId FROM XtkReject WHERE tsLog < $(curDate)) LIMIT $(l))
   ```

   여기서 **$(curDate)** 는 NmsCleanup_RejectsPurgeDelay **옵션(** 배포 마법사 [참조)에 대해 정의된 기간을 뺀 현재 서버 날짜입니다](#deployment-wizard). **** 및$(l)이 대량 삭제의 최대 레코드 수입니다.

1. 그런 다음 모든 고아 거부는 다음 쿼리를 사용하여 삭제됩니다.

   ```
   DELETE FROM XtkReject WHERE iJobId NOT IN (SELECT iJobId FROM XtkJob)
   ```

### 워크플로우 인스턴스 정리 {#cleanup-of-workflow-instances}

이 작업은 해당 식별자(**WorkflowId**)와 기록(**History**)을 사용하여 각 워크플로우 인스턴스를삭제합니다. 작업 테이블 정리 작업을 다시 실행하여 비활성 테이블을 삭제합니다. 또한 삭제된 워크플로우의 고아 작업 테이블(wkf% 및 wkfhissto%)도 모두 삭제됩니다.

>[!NOTE]
>
>작업 내역의 삭제 빈도는 일 **의 내역 필드(기본값** 30일)의 각 워크플로우에 대해 지정됩니다. 이 필드는 워크플로우 속성의 **실행** 탭에서 찾을 수 있습니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../workflow/using/workflow-properties.md#execution)을 참조하십시오.

1. 삭제할 워크플로우 목록을 복구하려면 다음 쿼리가 사용됩니다.

   ```
   SELECT iWorkflowId, iHistory FROM XtkWorkflow WHERE iWorkflowId<>0
   ```

1. 이 쿼리는 다음 쿼리를 사용하여 모든 연결된 로그, 완료된 작업 및 완료된 이벤트를 삭제하는 데 사용할 워크플로우 목록을 생성합니다.

   ```
   DELETE FROM XtkWorkflowLog WHERE iWorkflowId=$(lworkflow) AND tsLog < DateMinusDays($(lhistory))
   ```

   ```
   DELETE FROM XtkWorkflowTask WHERE iWorkflowId=$(lworkflow) AND iStatus<>0 AND tsCompletion < DateMinusDays($(lhistory)) 
   ```

   ```
   DELETE FROM XtkWorkflowEvent WHERE iWorkflowId=$(l) AND iStatus>2 AND tsProcessing < DateMinusDays($(lHistory))
   ```

   여기서 **$(lworkflow)** 는 작업 과정의 식별자이며 **$(lhistory)** 는 작업 과정의 식별자입니다.

1. 사용하지 않은 테이블이 모두 삭제됩니다. 이러한 목적으로 다음 쿼리(postgresql)를 사용하는 **wkf%** type 마스크 덕분에 모든 테이블이 수집됩니다.

   ```
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkf%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. 그러면 보류 중인 워크플로우 인스턴스에서 사용하는 모든 테이블이 제외됩니다. 활성 워크플로우 목록은 다음 쿼리를 사용하여 복구됩니다.

   ```
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId<>0 AND iState<>20
   ```

1. 그런 다음 각 워크플로우 식별자를 복구하여 워크플로우가 사용하는 테이블의 이름을 찾습니다. 이러한 이름은 이전에 복구된 테이블 목록에서 제외됩니다.
1. &quot;incremental query&quot; 유형 활동 내역 테이블은 다음 쿼리를 사용하여 제외됩니다.

   ```
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkfhisto%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

   ```
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId IN ($(strCondition))
   ```

   여기서 **$(strcondition)** 는 wkfhitto% **마스크** 와 일치하는 테이블목록입니다.

1. 나머지 테이블은 다음 쿼리를 사용하여 삭제됩니다.

   ```
   DROP TABLE wkf15487_12;
   ```

### 워크플로 로그인 정리 {#cleanup-of-workflow-logins}

이 작업은 다음 쿼리를 사용하여 워크플로 로그인을 삭제합니다.

```
DELETE FROM XtkWorkflowLogin WHERE iWorkflowId NOT IN (SELECT iWorkflowId FROM XtkWorkflow)
```

### 고아 작업 테이블 정리 {#cleanup-of-orphan-work-tables}

그룹에 연결된 고아 작업 테이블이 삭제됩니다. NmsGroup **** 테이블은 정리할 그룹을 저장합니다(0과 다른 유형 포함). 테이블 이름의 접두사는 **grp입니다**. 정리할 그룹을 식별하기 위해 다음 쿼리가 사용됩니다.

```
SELECT iGroupId FROM NmsGroup WHERE iType>0"
```

### 방문자 정리 {#cleanup-of-visitors}

이 작업은 대량 삭제를 사용하여 방문자 테이블에서 오래된 레코드를 삭제합니다. 오래된 레코드는 마지막 수정 사항이 배포 마법사에 정의된 보존 기간보다 빠른 것입니다( [배포 마법사 참조](#deployment-wizard)). 다음 쿼리가 사용됩니다.

```
DELETE FROM NmsVisitor WHERE iVisitorId IN (SELECT iVisitorId FROM NmsVisitor WHERE iRecipientId = 0 AND tsLastModified < AddDays(GetDate(), -30) AND iOrigin = 0 LIMIT 20000)
```

여기서 **$(tsDate)** 는 현재 서버 날짜로서, NmsCleanup_VisitorPurgeDelay **옵션에 대해 정의된 기간을** 제거합니다.

### NAPI 정리 {#cleanup-of-npai}

이 작업을 사용하면 NmsAddress 테이블에서 유효한 주소와 일치하는 레코드를 삭제할 **수** 있습니다. 다음 쿼리는 대량 삭제를 수행하는 데 사용됩니다.

```
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=2 AND tsLastModified < $(tsDate1) AND tsLastModified >= $(tsDate2) LIMIT 5000)
```

여기서 **status 2는** **[!UICONTROL Valid]** 상태와 일치하고, **$(tsDate1)** 는 현재 서버 날짜이고, **$(tsDate2)** 는 cleanup_nmsLastCleanupOption과 **** 일치합니다.

### 구독 정리 {#cleanup-of-subscriptions-}

이 작업은 대량 삭제를 사용하여 NmsSubscription 테이블에서 사용자가 **삭제한** 모든 가입을 삭제합니다. 다음 쿼리가 사용됩니다.

```
DELETE FROM NmsSubscription WHERE iDeleteStatus <>0
```

### 추적 로그 정리 {#cleanup-of-tracking-logs}

이 작업은 추적 및 웹추적 로그 테이블에서 오래된 레코드를 삭제합니다. 사용되지 않는 레코드는 배포 마법사에 정의된 보존 기간보다 이전 [레코드입니다(배포 마법사](#deployment-wizard)참조).

1. 첫째, 다음 쿼리를 사용하여 추적 로그 테이블 목록이 복구됩니다.

   ```
   SELECT distinct(sTrackingLogSchema) FROM NmsDeliveryMapping WHERE sTrackingLogSchema IS NOT NULL;
   ```

1. 대량 삭제는 이전에 복구된 테이블 목록에서 모든 테이블을 삭제하는 데 사용됩니다. 다음 쿼리가 사용됩니다.

   ```
   DELETE FROM XtkTrackingLogRcp WHERE iTrackingLogId IN (SELECT iTrackingLogId FROM XtkTrackingLogRcp WHERE tsLog < $(tsDate) LIMIT 5000) 
   ```

   여기서 **$(tsDate)** 는 NmsCleanup_TrackingLogPurgeDelay **옵션에 대해 정의된 기간을 뺀** 현재 서버 날짜입니다.

1. 추적 통계 테이블은 대량 삭제를 사용하여 삭제됩니다. 다음 쿼리가 사용됩니다.

   ```
   DELETE FROM NmsTrackingStats WHERE iTrackingStatsId IN (SELECT iTrackingStatsId FROM NmsTrackingStats WHERE tsStart < $(tsDate) LIMIT 5000) 
   ```

   여기서 **$(tsDate)** 는 NmsCleanup_TrackingStatPurgeDelay **옵션에 대해 정의된 기간을 뺀** 현재 서버 날짜입니다.

### 배달 로그 정리 {#cleanup-of-delivery-logs}

이 작업을 사용하면 다양한 테이블에 저장된 배달 로그를 삭제할 수 있습니다.

1. 이러한 목적으로 다음 쿼리를 사용하여 배달 로그 스키마 목록을 복구할 수 있습니다.

   ```
   SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL UNION SELECT distinct(sBroadLogExclSchema) FROM NmsDeliveryMapping WHERE sBroadLogExclSchema IS NOT NULL
   ```

1. 중간 소싱을 사용할 때 **NmsBroadLogMid** 테이블이 배달 매핑에서 참조되지 않습니다. 이전 **쿼리에서 복구한 목록에 nms:broadLogMid** 스키마가 추가됩니다.
1. 데이터베이스 **정리** 워크플로우는 이전에 복구된 테이블에서 오래된 데이터를 삭제합니다. 다음 쿼리가 사용됩니다.

   ```
   DELETE FROM $(tableName) WHERE iBroadLogId IN (SELECT iBroadLogId FROM $(tableName) WHERE tsLastModified < $(option) LIMIT 5000) 
   ```

   여기서 **$(tableName)** 은 스키마 목록에 있는 각 테이블의 이름이고,$(옵션) **은 NmsCleanup_BroadLogPurgeDelay** 옵션 **에 대해 정의된 날짜입니다(** [](#deployment-wizard)배포 마법사 참조).

1. 마지막으로 워크플로우는 NmsProviderMsgId **테이블이 있는지** 확인합니다. 이 경우, 오래된 데이터는 모두 다음 쿼리를 사용하여 삭제됩니다.

   ```
   DELETE FROM NmsProviderMsgId WHERE iBroadLogId IN (SELECT iBroadLogId FROM NmsProviderMsgId WHERE tsCreated < $(option) LIMIT 5000)
   ```

   여기서 **$(옵션)****은 NmsCleanup_BroadLogPurgeDelay** 옵션에 대해 정의된 [날짜와 일치합니다(](#deployment-wizard)배포 마법사 참조).

### NmsEmailErrorStat 테이블 정리 {#cleanup-of-the-nmsemailerrorstat-table-}

이 작업은 NmsEmailError **Stat 테이블을** 정리합니다. 주 프로그램(**coalesceErrors**)은

* **시작 날짜**:NmsLastErrorStatCoalesce **옵션 또는 표의 최신** 날짜와 일치하는 다음 프로세스의 날짜입니다.
* **종료 날짜**:현재 서버 날짜입니다.

시작 날짜가 종료 날짜보다 크거나 같은 경우 프로세스는 발생하지 않습니다. 이 경우 **coalesceUpToDate** 메시지가 나타납니다.

시작 날짜가 종료 날짜보다 더 빠른 경우 **NmsEmailErrorStat** 테이블이 정리됩니다.

시작 날짜와 종료 날짜 사이의 **NmsEmailErrorStat** 테이블의 총 오류 수는 다음 쿼리를 사용하여 복구됩니다.

```
"SELECT COUNT(*) FROM NmsEmailErrorStat WHERE tsDate>= $(start) AND tsDate< $(end)"
```

여기서 **$end** 및 **$start** 는 이전에 정의된 시작 및 종료 날짜입니다.

합계가 0보다 큰 경우:

1. 다음 쿼리는 특정 임계값(20과 같음)을 초과하여 오류만 유지하려면 실행됩니다.

   ```
   "SELECT iMXIP, iPublicId, SUM(iTotalConnections), SUM(iTotalErrors), SUM(iMessageErrors), SUM(iAbortedConnections), SUM(iFailedConnections), SUM(iRefusedConnections), SUM(iTimeoutConnections) FROM NmsEmailErrorStat WHERE tsDate>=$(start ) AND tsDate<$(end ) GROUP BY iMXIP, iPublicId HAVING SUM(iTotalErrors) >= 20"
   ```

1. coalescingErrors **메시지가** 표시됩니다.
1. 시작 날짜와 종료 날짜 사이에 발생한 모든 오류를 삭제하기 위해 새 연결이 만들어집니다. 다음 쿼리가 사용됩니다.

   ```
   "DELETE FROM NmsEmailErrorStat WHERE tsDate>=$(start) AND tsDate<$(end)"
   ```

1. 각 오류는 다음 쿼리를 사용하여 **NmsEmailErrorStat** 테이블에 저장됩니다.

   ```
   "INSERT INTO NmsEmailErrorStat(iMXIP, iPublicId, tsDate, iTotalConnections, iTotalErrors, iTimeoutConnections, iRefusedConnections, iAbortedConnections, iFailedConnections, iMessageErrors) VALUES($(lmxip ), $(lpublicId ), $(tsstart ), $(lconnections ), $(lconnectionErrors ),$(ltimeoutConnections ), $(lrefusedConnections ), $(labortedConnections ), $(lfailedConnections ), $(lmessageErrors))"
   ```

   여기서 각 변수는 이전 쿼리에서 복구한 값과 일치합니다.

1. **start** 변수는 루프를 완료하기 위해 이전 프로세스 값으로 업데이트됩니다.

루프와 작업이 중지됩니다.

정리 작업은 NmsEmailError 및 **cleanupNmsMxDomain** 테이블에서 **** 실행됩니다.

### NmsEmailError 테이블 정리 {#cleanup-of-the-nmsemailerror-table-}

다음 쿼리가 사용됩니다.

```
DELETE FROM NmsEmailError WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

이 쿼리는 NmsEmailError **테이블의 NmsEmailErrorStat에 연결된 레코드** 가 **없는 모든 행을** 삭제합니다.

### NmsMxDomain 테이블 정리 {#cleanup-of-the-nmsmxdomain-table-}

다음 쿼리가 사용됩니다.

```
DELETE FROM NmsMxDomain WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

이 쿼리는 NmsMxDomain **테이블의** NmsEmailErrorStat **테이블에 연결된 레코드가 없는 모든** 행을 삭제합니다.

### 제안 정리 {#cleanup-of-propositions}

상호 **작용** 모듈이 설치되어 있는 경우 이 작업을 실행하여 NmsProvisionXxx **테이블을** 삭제합니다.

proposition 테이블 목록은 복구되고 다음 쿼리를 사용하여 각 테이블에 대해 일괄 삭제가 수행됩니다.

```
DELETE FROM NmsPropositionXxx WHERE iPropositionId IN (SELECT iPropositionId FROM NmsPropositionXxx WHERE tsLastModified < $(option) LIMIT 5000) 
```

여기서 **$(옵션)** 는 NmsCleanup_PromisePurgeDelay **옵션(** 배포 마법사 참조)에 대해 정의된 [날짜입니다](#deployment-wizard).

### 시뮬레이션 테이블 정리 {#cleanup-of-simulation-tables}

이 작업은 고아 시뮬레이션 테이블을 정리합니다(더 이상 오퍼 시뮬레이션 또는 배달 시뮬레이션에 연결되지 않음).

1. 정리가 필요한 시뮬레이션 목록을 복구하려면 다음 쿼리가 사용됩니다.

   ```
   SELECT iSimulationId FROM NmsSimulation WHERE iSimulationId<>0
   ```

1. 삭제할 테이블의 이름은 **wkSimu_** 접두사와 시뮬레이션의 식별자(예: **wkSimu_456831_aggr**):

   ```
   DROP TABLE wkSimu_456831_aggr
   ```

### 감사 추적 정리 {#cleanup-of-audit-trail}

다음 쿼리가 사용됩니다.

```
DELETE FROM XtkAudit WHERE tsChanged < $(tsDate)
```

여기서 **$(tsDate)** 는 XtkCleanup_AuditTrailPurgeDelay **옵션에 대해 정의된 기간이 하위 처리되는 현재 서버** 날짜입니다.

### nmsaddress 정리 {#cleanup-of-nmsaddress}

다음 쿼리가 사용됩니다.

```
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=STATUS_QUARANTINE AND tsLastModified < $(NmsCleanup_AppSubscriptionRcpPurgeDelay + 5d) AND iType IN (MESSAGETYPE_IOS, MESSAGETYPE_ANDROID ) LIMIT 5000)
```

이 쿼리는 iOS 및 Android와 관련된 모든 항목을 삭제합니다.

### 통계 업데이트 및 스토리지 최적화 {#statistics-update}

XtkCleanup_ **NoStats** 옵션을 사용하면 정리 워크플로의 저장소 최적화 단계의 동작을 제어할 수 있습니다.

XtkCleanup_ **NoStats** 옵션이 없거나 값이 0인 경우 PostgreSQL에서 세부 정보 표시 모드(INNOVATIVE VERBOSE ANALYZE)로 스토리지 최적화를 실행하고 다른 모든 데이터베이스에 대한 통계를 업데이트합니다. 이 명령이 실행되는지 확인하려면 PostgreSQL 로그를 확인하십시오. INSPAN은 다음 형식으로 라인을 출력합니다. `INFO: vacuuming "public.nmsactivecontact"` and ANALYZE will output lines in the format: `INFO: analyzing "public.nmsactivecontact"`.

옵션 값이 1이면 어떤 데이터베이스에서도 통계 업데이트가 실행되지 않습니다. 다음 로그 줄이 워크플로우 로그에 표시됩니다. `Option 'XtkCleanup_NoStats' is set to '1'`.

옵션 값이 2이면 PostgreSQL에서 자세한 정보 표시 모드(ANALYZE VERBOSE)로 스토리지 분석을 실행하고 다른 모든 데이터베이스에 대한 통계를 업데이트합니다. 이 명령이 실행되는지 확인하려면 PostgreSQL 로그를 확인하십시오. ANALYZE는 다음 형식으로 라인을 출력합니다. `INFO: analyzing "public.nmsactivecontact"`.

### 구독 정리(NMAC) {#subscription-cleanup--nmac-}

이 작업을 수행하면 삭제된 서비스 또는 모바일 애플리케이션과 관련된 모든 구독이 삭제됩니다.

브로드로그 스키마 목록을 복구하려면 다음 쿼리가 사용됩니다.

```
SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL
```

그런 다음 이 작업은 appSubscription **** 링크에 연결된 테이블의 이름을 복원하고 이 테이블을 삭제합니다.

또한 이 정리 워크플로우는 NmsCleanup_AppSubscriptionRcpPurgeDelay **** 옵션에 설정된 시간 이후 업데이트되지 않은 indisabled = 1인 모든 항목을 삭제합니다.

### 세션 정보 정리 {#cleansing-session-information}

이 작업은 sessionInfo **테이블에서 정보를** 정리하고 다음 쿼리가 사용됩니다.

```
 DELETE FROM XtkSessionInfo WHERE tsexpiration < $(curdate) 
```

### 만료된 이벤트 정리 {#cleansing-expired-events}

이 작업을 수행하면 받은 이벤트가 정리되어 실행 인스턴스와 제어 인스턴스에 보관된 이벤트에 저장됩니다.

### 정화 반응 {#cleansing-reactions}

이 작업은 가설이 삭제된 **반응(테이블 NmsRemaMatchRcp**)을 지웁니다.
