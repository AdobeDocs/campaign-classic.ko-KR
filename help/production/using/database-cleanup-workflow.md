---
product: campaign
title: 데이터베이스 정리 워크플로우
description: 오래된 데이터를 자동으로 정리하는 방법 알아보기
feature: Monitoring, Workflows
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용됩니다."
audience: production
content-type: reference
topic-tags: data-processing
exl-id: 75d3a0af-9a14-4083-b1da-2c1b22f57cbe
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '2830'
ht-degree: 0%

---

# 데이터베이스 정리 워크플로우{#database-cleanup-workflow}



## 소개 {#introduction}

다음 **[!UICONTROL Database cleanup]** 을 통해 액세스할 수 있는 워크플로우 **[!UICONTROL Administration > Production > Technical workflows]** 노드를 사용하면 데이터베이스의 기하급수적인 증가를 방지하기 위해 오래된 데이터를 삭제할 수 있습니다. 워크플로우는 사용자의 개입 없이 자동으로 트리거됩니다.

![cleanup](assets/ncs_cleanup_workflow.png)

## 구성 {#configuration}

데이터베이스 정리는 워크플로 스케줄러와 배포 마법사의 두 가지 수준에서 구성됩니다.

### 워크플로우 스케줄러 {#the-scheduler}

>[!NOTE]
>
>스케줄러에 대한 자세한 내용은 [이 섹션](../../workflow/using/scheduler.md).

기본적으로 **[!UICONTROL Database cleanup]** 워크플로우가 매일 오전 4시에 시작되도록 구성되었습니다. 스케줄러를 사용하여 워크플로우 트리거 빈도를 변경할 수 있습니다. 다음 빈도를 사용할 수 있습니다.

* **[!UICONTROL Several times a day]**
* **[!UICONTROL Daily]**
* **[!UICONTROL Weekly]**
* **[!UICONTROL Once]**

![예약](assets/ncs_cleanup_scheduler.png)

>[!IMPORTANT]
>
>주문: **[!UICONTROL Database cleanup]** 워크플로우가 스케줄러에 정의된 날짜와 시간에 시작되도록 하려면 워크플로우 엔진(wfserver)을 시작해야 합니다.

### 배포 마법사 {#deployment-wizard}

다음 **[!UICONTROL Deployment wizard]**, 를 통해 액세스됨 **[!UICONTROL Tools > Advanced]** 메뉴에서 데이터를 저장할 기간을 구성할 수 있습니다. 값은 일 단위로 표시됩니다. 이 값을 변경하지 않으면 워크플로우는 기본값을 사용합니다.

![](assets/ncs_cleanup_deployment-wizard.png)

의 필드 **[!UICONTROL Purge of data]** 창은 다음 옵션과 일치합니다. 이 템플릿은 **[!UICONTROL Database cleanup]** 워크플로:

* 통합 추적: **NmsCleanup_TrackingStatPurgeDelay** (참조: [추적 로그 정리](#cleanup-of-tracking-logs))
* 게재 로그: **NmsCleanup_BroadLogPurgeDelay** (참조: [게재 로그 정리](#cleanup-of-delivery-logs))
* 추적 로그: **NmsCleanup_TrackingLogPurgeDelay** (참조: [추적 로그 정리](#cleanup-of-tracking-logs))
* 삭제된 게재: **NmsCleanup_RecycedDeliveryPurgeDelay** (참조: [삭제하거나 재활용할 게재 정리](#cleanup-of-deliveries-to-be-deleted-or-recycled))
* 가져오기 거부: **NmsCleanup_RejectPurgeDelay** (참조: [가져오기에 의해 생성된 거부 정리](#cleanup-of-rejects-generated-by-imports-))
* 방문자 프로필: **NmsCleanup_VisitorPurgeDelay** (참조: [방문자 정리](#cleanup-of-visitors))
* 제안: **NmsCleanup_PropositionPurgeDelay** (참조: [제안 정리](#cleanup-of-propositions))

  >[!NOTE]
  >
  >다음 **[!UICONTROL Offer propositions]** 필드는 다음 경우에만 사용할 수 있습니다 **상호 작용** 모듈이 설치되었습니다.

* 이벤트: **NmsCleanup_EventPurgeDelay** (참조: [만료된 이벤트 정리](#cleansing-expired-events))
* 보관된 이벤트: **NmsCleanup_EventHistoPurgeDelay** (참조: [만료된 이벤트 정리](#cleansing-expired-events))

  >[!NOTE]
  >
  >다음 **[!UICONTROL Events]** 및 **[!UICONTROL Archived events]** 필드는 다음 경우에만 사용할 수 있습니다 **메시지 센터** 모듈이 설치되었습니다.

* 감사 추적: **XtkCleanup_AuditTrailPurgeDelay** (참조: [감사 추적 정리](#cleanup-of-audit-trail))

에 의해 실행된 모든 작업 **[!UICONTROL Database cleanup]** 워크플로우는 다음 섹션에 설명되어 있습니다.

## 데이터베이스 정리 워크플로우에서 수행되는 작업 {#tasks-carried-out-by-the-database-cleanup-workflow}

워크플로우 스케줄러에 정의된 날짜 및 시간( 참조) [스케줄러](#the-scheduler)), 워크플로우 엔진은 데이터베이스 정리 프로세스를 시작합니다. 데이터베이스 정리는 데이터베이스에 연결하고 아래 표시된 순서대로 작업을 실행합니다.

>[!IMPORTANT]
>
>이 작업 중 하나가 실패하면 다음 작업이 실행되지 않습니다.
>
>SQL 쿼리 **제한** 속성은 모든 정보가 처리될 때까지 반복적으로 실행됩니다.


### 정리 삭제 목록 {#lists-to-delete-cleanup}

에서 실행한 첫 번째 작업 **[!UICONTROL Database cleanup]** 워크플로는 이 있는 모든 그룹을 삭제합니다. **deleteStatus != 0** 속성 위치: **Nms 그룹**. 이러한 그룹에 연결되어 있고 다른 테이블에 있는 레코드도 삭제됩니다.

1. 삭제할 목록은 다음 SQL 쿼리를 사용하여 복구됩니다.

   ```sql
   SELECT iGroupId, sLabel, iType FROM NmsGroup WHERE iDeleteStatus <> 0 OR tsExpirationDate <= GetDate() 
   ```

1. 각 목록에는 다른 테이블에 대한 여러 링크가 있습니다. 이러한 모든 링크는 다음 쿼리를 사용하여 일괄적으로 삭제됩니다.

   ```sql
   DELETE FROM $(relatedTable) WHERE iGroupId=$(l) IN (SELECT iGroupId FROM $(relatedTable) WHERE iGroupId=$(l) LIMIT 5000) 
   ```

   위치 `$(relatedTable)` 은(는) 관련 테이블입니다. **Nms 그룹** 및 `$(l)` 는 목록 식별자입니다.

1. 목록이 &#39;목록&#39; 유형 목록인 경우 다음 쿼리를 사용하여 관련 테이블이 삭제됩니다.

   ```sql
   DROP TABLE grp$(l)
   ```

1. 매 **선택** 작업에 의해 복구된 유형 목록은 다음 쿼리를 사용하여 삭제됩니다.

   ```sql
   DELETE FROM NmsGroup WHERE iGroupId=$(l) 
   ```

   위치 `$(l)` 목록 식별자입니다.

### 삭제하거나 재활용할 게재 정리 {#cleanup-of-deliveries-to-be-deleted-or-recycled}

이 작업은 삭제하거나 재활용할 모든 게재를 삭제합니다.

1. 다음 **[!UICONTROL Database cleanup]** 워크플로우는 다음 대상이 되는 모든 게재를 선택합니다 **deleteStatus** 필드에 값이 있음 **[!UICONTROL Yes]** 또는 **[!UICONTROL Recycled]** 및 의 삭제 날짜가 다음에 정의된 기간 이전인 경우 **[!UICONTROL Deleted deliveries]** (**NmsCleanup_RecycedDeliveryPurgeDelay**) 배포 마법사의 필드입니다. 자세한 내용은 다음을 참조하십시오. [배포 마법사](#deployment-wizard). 이 기간은 현재 서버 날짜를 기준으로 계산됩니다.
1. 각 중간 소싱 서버에 대해 작업은 삭제할 게재 목록을 선택합니다.
1. 다음 **[!UICONTROL Database cleanup]** 워크플로는 게재 로그, 첨부 파일, 미러 페이지 정보 및 기타 모든 관련 데이터를 삭제합니다.
1. 정상적으로 게재를 삭제하기 전에 워크플로우는 다음 표에서 연결된 정보를 삭제합니다.

   * 게재 제외 테이블(**NmsDlvExclusion**), 다음 쿼리가 사용됩니다.

     ```sql
     DELETE FROM NmsDlvExclusion WHERE iDeliveryId=$(l)
     ```

     위치 **$(l)** 는 게재 식별자입니다.

   * 쿠폰 테이블 (**NmsCouponValue**), 다음 쿼리가 사용됩니다(대량 삭제 사용).

     ```sql
     DELETE FROM NmsCouponValue WHERE iMessageId IN (SELECT iMessageId FROM NmsCouponValue WHERE EXISTS (SELECT B.iBroadLogId FROM $(BroadLogTableName) B WHERE B.iDeliveryId = $(l) AND B.iBroadLogId = iMessageId ) LIMIT 5000)
     ```

     위치 `$(l)` 는 게재 식별자입니다.

   * 게재 로그 테이블(**NmsBroadlogXxx**), 대량 삭제는 20,000개의 레코드로 일괄 실행됩니다.
   * 오퍼 제안 테이블 (**NmsPropositionXxx**), 대량 삭제는 20,000개의 레코드로 일괄 실행됩니다.
   * 추적 로그 테이블 (**NmsTrackinglogXxx**), 대량 삭제는 20,000개의 레코드로 일괄 실행됩니다.
   * 게재 조각 테이블(**NmsDeliveryPart**), 대량 삭제는 500,000개의 레코드로 일괄 실행됩니다. 이 표에는 게재할 나머지 메시지에 대한 개인화 정보가 포함되어 있습니다.
   * 미러 페이지 데이터 조각 테이블(**NmsMirrorPageInfo**)에서 대량 삭제는 만료된 게재 부분 및 완료 또는 취소된 부분에 대해 20,000개의 레코드로 일괄적으로 실행됩니다. 이 표에는 미러 페이지 생성에 사용되는 모든 메시지에 대한 개인화 정보가 포함되어 있습니다.
   * 미러 페이지 검색 표에서 (**NmsMirrorPageSearch**), 대량 삭제는 20,000개의 레코드로 일괄 실행됩니다. 이 테이블은 다음에 저장된 개인화 정보에 대한 액세스를 제공하는 검색 색인입니다. **NmsMirrorPageInfo** 테이블.
   * 배치 프로세스 로그 테이블(**XtkJobLog**), 대량 삭제는 20,000개의 레코드로 일괄 실행됩니다. 이 표에는 삭제할 게재 로그가 포함되어 있습니다.
   * 게재 URL 추적 테이블(**NmsTrackingUrl**), 다음 쿼리가 사용됩니다.

     ```sql
     DELETE FROM NmsTrackingUrl WHERE iDeliveryId=$(l)
     ```

     위치 `$(l)` 는 게재 식별자입니다.

     이 표에는 추적을 활성화하기 위해 삭제할 게재에서 찾은 URL이 포함되어 있습니다.

1. 게재가 게재 테이블에서 삭제됩니다(**NmsDelivery**):

   ```sql
   DELETE FROM NmsDelivery WHERE iDeliveryId = $(l)
   ```

   위치 `$(l)` 는 게재 식별자입니다.

#### 중간 소싱을 사용한 게재 {#deliveries-using-mid-sourcing}

다음 **[!UICONTROL Database cleanup]** 또한 워크플로우에서는 중간 소싱 서버에서 게재를 삭제합니다.

1. 이를 위해 워크플로우는 각 게재가 비활성 상태임을 확인합니다(상태에 따라 다름). 게재가 활성 상태이면 삭제하기 전에 중지됩니다. 다음 쿼리를 실행하여 확인합니다.

   ```sql
   SELECT iState FROM NmsDelivery WHERE iDeliveryId = $(l) AND iState <> 100;
   ```

   위치 **$(l)** 는 게재 식별자입니다.

1. 상태 값이 인 경우 **[!UICONTROL Start pending]** , **[!UICONTROL In progress]** , **[!UICONTROL Recovery pending]** , **[!UICONTROL Recovery in progress]** , **[!UICONTROL Pause requested]** , **[!UICONTROL Pause in progress]** , 또는 **[!UICONTROL Paused]** (값 51, 55, 61, 62, 71, 72, 75), 게재가 중지되고 작업이 연결된 정보를 삭제합니다.

### 만료된 게재 정리 {#cleanup-of-expired-deliveries}

이 작업은 유효 기간이 만료된 게재를 중지합니다.

1. 다음 **[!UICONTROL Database cleanup]** 워크플로우가 만료된 게재 목록을 만듭니다. 이 목록에는 상태가 이 아닌 만료된 모든 게재가 포함됩니다. **[!UICONTROL Finished]** 는 물론 처리되지 않은 메시지가 10,000개가 넘는 상황에서 최근 중단된 게재도 포함됩니다. 다음 쿼리가 사용됩니다.

   ```sql
   SELECT iDeliveryId, iState FROM NmsDelivery WHERE iDeleteStatus=0 AND iIsModel=0 AND iDeliveryMode=1 AND ( (iState >= 51 AND iState < 85 AND tsValidity IS NOT NULL AND tsValidity < $(currentDate) ) OR (iState = 85 AND DateMinusDays(15) < tsLastModified AND iToDeliver - iProcessed >= 10000 ))
   ```

   위치 `delivery mode 1` 와 일치 **[!UICONTROL Mass delivery]** 모드, `state 51` 와 일치 **[!UICONTROL Start pending]** state, `state 85` 와 일치 **[!UICONTROL Stopped]** 상태 및 게재 서버에서 대량 업데이트된 가장 많은 게재 로그 수는 10,000개입니다.

1. 그러면 워크플로우에는 중간 소싱을 사용하는 최근에 만료된 게재 목록이 포함됩니다. 중간 소싱 서버를 통해 아직 게재 로그가 복구되지 않은 게재는 제외됩니다.

   다음 쿼리가 사용됩니다.

   ```sql
   SELECT iDeliveryId, tsValidity, iMidRemoteId, mData FROM NmsDelivery WHERE (iDeliveryMode = 4 AND (iState = 85 OR iState = 95) AND tsValidity IS NOT NULL AND (tsValidity < SubDays(GetDate() , 15) OR tsValidity < $(DateOfLastLogPullUp)) AND tsLastModified > SubDays(GetDate() , 15))
   ```

1. 다음 쿼리는 날짜별로 게재를 필터링하기 위해 외부 계정이 여전히 활성 상태인지 여부를 감지하는 데 사용됩니다.

   ```sql
   SELECT iExtAccountId FROM NmsExtAccount WHERE iActive<>0 AND sName=$(providerName)
   ```

1. 만료된 게재 목록에서 상태가 인 게재 로그 **[!UICONTROL Pending]** , 다음으로 전환 **[!UICONTROL Delivery cancelled]** 및 이 목록의 모든 게재가 다음으로 전환됨 **[!UICONTROL Finished]** .

   다음 쿼리가 사용됩니다.

   ```sql
   UPDATE $(BroadLogTableName) SET tsLastModified=$(curdate), iStatus=7, iMsgId=$(bl) WHERE iDeliveryId=$(dl) AND iStatus=6
   ```

   위치 `$(curdate)`는 데이터베이스 서버의 현재 날짜입니다. `$(bl)` 은 게재 로그 메시지의 식별자입니다. `$(dl)` 은 게재 식별자, `delivery status 6` 와 일치 **[!UICONTROL Pending]** 상태 및 `delivery status 7` 와 일치 **[!UICONTROL Delivery cancelled]** 상태.

   ```sql
   UPDATE NmsDelivery SET iState = 95, tsLastModified = $(curdate), tsBroadEnd = tsValidity WHERE iDeliveryId = $(dl)
   ```

   위치 `delivery state 95` 와 일치 **[!UICONTROL Finished]** 상태 및 `$(dl)` 는 게재 식별자입니다.

1. 모든 조각(**deliveryPart**)의 오래된 게재가 삭제되고 진행 중인 알림 게재의 오래된 조각이 모두 삭제됩니다. 이 두 작업에는 일괄 삭제가 사용됩니다.

   다음 쿼리가 사용됩니다.

   ```sql
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE iDeliveryId IN (SELECT iDeliveryId FROM NmsDelivery WHERE iState=95 OR iState=85) LIMIT 5000)
   ```

   ```sql
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE tsValidity < $(curDate) LIMIT 500000)
   ```

   위치 `delivery state 95` 와 일치 **[!UICONTROL Finished]** 상태, `delivery state 85` 와 일치 **[!UICONTROL Stopped]** 상태 및 `$(curDate)` 는 현재 서버 날짜입니다.

### 미러 페이지 정리 {#cleanup-of-mirror-pages}

이 작업은 게재에 사용되는 웹 리소스(미러 페이지)를 삭제합니다.

1. 먼저 다음 쿼리를 사용하여 삭제할 게재 목록을 복구합니다.

   ```sql
   SELECT iDeliveryId, iNeedMirrorPage FROM NmsDelivery WHERE iWebResPurged = 0 AND tsWebValidity IS NOT NULL AND tsWebValidity < $(curdate)
   ```

   위치 `$(curDate)` 는 현재 서버 날짜입니다.

1. 다음 **NmsMirrorPageInfo** 필요한 경우 이전에 복구된 게재의 식별자를 사용하여 테이블을 삭제합니다. 대량 삭제는 다음 쿼리를 생성하는 데 사용됩니다.

   ```sql
   DELETE FROM NmsMirrorPageInfo WHERE iMirrorPageInfoId IN (SELECT iMirrorPageInfoId FROM NmsMirrorPageInfo WHERE iDeliveryId = $(dl)) LIMIT 5000
   ```

   ```sql
   DELETE FROM NmsMirrorPageSearch WHERE iMessageId IN (SELECT iMessageId FROM NmsMirrorPageSearch WHERE iDeliveryId = $(dl)) LIMIT 5000
   ```

   위치 `$(dl)` 는 게재 식별자입니다.

1. 그런 다음 항목이 게재 로그에 추가됩니다.
1. 그런 다음 삭제된 게재가 식별되어 나중에 다시 처리할 필요가 없습니다. 다음 쿼리가 실행됩니다.

   ```sql
   UPDATE NmsDelivery SET iWebResPurged = 1 WHERE iDeliveryId IN ($(strIn))
   ```

   위치 `$(strIn)` 는 게재 식별자 목록입니다.

### 작업 테이블 정리 {#cleanup-of-work-tables}

이 작업은 상태가 인 게재와 일치하는 모든 작업 테이블을 데이터베이스에서 삭제합니다. **[!UICONTROL Being edited]** , **[!UICONTROL Stopped]** 또는 **[!UICONTROL Deleted]** .

1. 이름이 다음으로 시작하는 테이블 목록 **wkDlv_** 는 다음 쿼리(postgresql)를 사용하여 먼저 복구됩니다.

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkDlv_') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. 그러면 진행 중인 워크플로우에서 사용하는 표는 제외됩니다. 이를 위해 다음 쿼리를 사용하여 진행 중인 게재 목록을 복구합니다.

   ```sql
   SELECT iDeliveryId FROM NmsDelivery WHERE iDeliveryId<>0 AND iDeleteStatus=0 AND iState NOT IN (0,85,100);
   ```

   위치 `0` 는 와 일치하는 값입니다. **[!UICONTROL Being edited]** 게재 상태, `85` 와 일치 **[!UICONTROL Stopped]** 상태 및 `100` 와 일치 **[!UICONTROL Deleted]** 상태.

1. 더 이상 사용되지 않는 테이블은 다음 쿼리를 사용하여 삭제됩니다.

   ```sql
   DROP TABLE wkDlv_15487_1;
   ```

### 가져오기에 의해 생성된 거부 정리 {#cleanup-of-rejects-generated-by-imports-}

이 단계에서는 가져오는 동안 모든 데이터가 처리되지 않은 레코드를 삭제할 수 있습니다.

1. 대량 삭제는 **XtkReject** 다음 쿼리가 있는 테이블:

   ```sql
   DELETE FROM XtkReject WHERE iRejectId IN (SELECT iRejectId FROM XtkReject WHERE tsLog < $(curDate)) LIMIT $(l)
   ```

   위치 `$(curDate)` 는 다음에 대해 정의된 기간을 뺀 현재 서버 날짜입니다. **NmsCleanup_RejectPurgeDelay** 옵션(참조: [배포 마법사](#deployment-wizard)) 및 `$(l)` 대량 삭제할 최대 레코드 수입니다.

1. 그런 다음 모든 고아 거부가 다음 쿼리를 사용하여 삭제됩니다.

   ```sql
   DELETE FROM XtkReject WHERE iJobId NOT IN (SELECT iJobId FROM XtkJob)
   ```

### 워크플로우 인스턴스 정리 {#cleanup-of-workflow-instances}

이 작업은 해당 식별자( )를 사용하여 각 워크플로 인스턴스를 삭제합니다.**lWorkflowId**) 및 기록(**병력**). 작업 테이블 정리 작업을 다시 실행하여 비활성 테이블을 삭제합니다. 또한 정리 시 삭제된 워크플로우의 모든 분리된 작업 테이블(wkf% 및 wkfhisto%)이 삭제됩니다.

>[!NOTE]
>
>기록 삭제 빈도는 의 각 워크플로우에 대해 지정됩니다. **기록(일)** 필드 (기본값 30일). 이 필드는 다음에서 찾을 수 있습니다 **실행** 워크플로 속성의 탭입니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../workflow/using/workflow-properties.md#execution)을 참조하십시오.

1. 삭제할 워크플로우 목록을 복구하려면 다음 쿼리가 사용됩니다.

   ```sql
   SELECT iWorkflowId, iHistory FROM XtkWorkflow WHERE iWorkflowId<>0
   ```

1. 이 쿼리는 다음 쿼리를 사용하여 연결된 모든 로그, 완료된 작업 및 완료된 이벤트를 삭제하는 데 사용할 워크플로 목록을 생성합니다.

   ```sql
   DELETE FROM XtkWorkflowLog WHERE iWorkflowId=$(lworkflow) AND tsLog < DateMinusDays($(lhistory))
   ```

   ```sql
   DELETE FROM XtkWorkflowTask WHERE iWorkflowId=$(lworkflow) AND iStatus<>0 AND tsCompletion < DateMinusDays($(lhistory)) 
   ```

   ```sql
   DELETE FROM XtkWorkflowEvent WHERE iWorkflowId=$(l) AND iStatus>2 AND tsProcessing < DateMinusDays($(lHistory))
   ```

   위치 `$(lworkflow)` 은 워크플로우의 식별자이며, `$(lhistory)` 는 내역의 식별자입니다.

1. 사용되지 않은 테이블은 모두 삭제됩니다. 이를 위해 모든 테이블은 **wkf%** 다음 쿼리(postgresql)를 사용하여 마스크를 입력합니다.

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkf%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. 그러면 보류 중인 워크플로우 인스턴스에서 사용하는 모든 테이블이 제외됩니다. 활성 워크플로우 목록은 다음 쿼리를 사용하여 복구됩니다.

   ```sql
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId<>0 AND iState<>20
   ```

1. 그런 다음 각 워크플로우 식별자를 복구하여 진행 중인 워크플로우에서 사용하는 테이블의 이름을 찾습니다. 이러한 이름은 이전에 복구된 테이블 목록에서 제외됩니다.
1. &quot;증분 쿼리&quot; 유형의 활동 기록 테이블은 다음 쿼리를 사용하여 제외됩니다.

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkfhisto%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

   ```sql
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId IN ($(strCondition))
   ```

   위치 `$(strcondition)` 는 다음과 일치하는 테이블 목록입니다. **wkfhisto%** 마스크.

1. 나머지 테이블은 다음 쿼리를 사용하여 삭제됩니다.

   ```sql
   DROP TABLE wkf15487_12;
   ```

### 워크플로우 로그인 정리 {#cleanup-of-workflow-logins}

이 작업은 다음 쿼리를 사용하여 워크플로 로그인을 삭제합니다.

```sql
DELETE FROM XtkWorkflowLogin WHERE iWorkflowId NOT IN (SELECT iWorkflowId FROM XtkWorkflow)
```

### 고아 작업 표 정리 {#cleanup-of-orphan-work-tables}

이 작업은 그룹에 연결된 고아 작업 테이블을 삭제합니다. 다음 **Nms 그룹** 표는 정리할 그룹을 저장합니다(0과 다른 유형). 테이블 이름의 접두사는 입니다. **grp**. 정리할 그룹을 식별하려면 다음 쿼리가 사용됩니다.

```sql
SELECT iGroupId FROM NmsGroup WHERE iType>0"
```

### 방문자 정리 {#cleanup-of-visitors}

이 작업은 일괄 삭제를 사용하여 방문자 테이블에서 오래된 레코드를 삭제합니다. 사용되지 않는 레코드는 마지막 수정이 배포 마법사에 정의된 보존 기간보다 이전인 레코드입니다( 참조) [배포 마법사](#deployment-wizard)). 다음 쿼리가 사용됩니다.

```sql
DELETE FROM NmsVisitor WHERE iVisitorId IN (SELECT iVisitorId FROM NmsVisitor WHERE iRecipientId = 0 AND tsLastModified < AddDays(GetDate(), -30) AND iOrigin = 0 LIMIT 20000)
```

위치 `$(tsDate)` 는 현재 서버 날짜이며, 여기서 에 대해 정의된 기간을 뺍니다. **NmsCleanup_VisitorPurgeDelay** 옵션을 선택합니다.

### NPAI 정리 {#cleanup-of-npai}

이 작업을 사용하면 유효한 주소와 일치하는 레코드를 **Nms 주소** 테이블. 다음 질의를 사용하여 대량 삭제를 수행합니다.

```sql
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=2 AND tsLastModified < $(tsDate1) AND tsLastModified >= $(tsDate2) LIMIT 5000)
```

위치 `status 2` 와 일치 **[!UICONTROL Valid]** 상태, `$(tsDate1)` 는 현재 서버 날짜이고, `$(tsDate2)` 와 일치 **NmsCleanup_LastCleanup** 옵션을 선택합니다.

### 구독 정리 {#cleanup-of-subscriptions-}

이 작업은 사용자가에서 삭제된 모든 구독을 삭제합니다. **Nms구독** 테이블, 일괄 삭제 사용. 다음 쿼리가 사용됩니다.

```sql
DELETE FROM NmsSubscription WHERE iDeleteStatus <>0
```

### 추적 로그 정리 {#cleanup-of-tracking-logs}

이 작업은 추적 및 웹 추적 로그 테이블에서 오래된 레코드를 삭제합니다. 사용되지 않는 레코드는 배포 마법사에 정의된 보존 기간보다 이전입니다( 참조). [배포 마법사](#deployment-wizard)).

1. 먼저 다음 쿼리를 사용하여 추적 로그 테이블 목록을 복구합니다.

   ```sql
   SELECT distinct(sTrackingLogSchema) FROM NmsDeliveryMapping WHERE sTrackingLogSchema IS NOT NULL;
   ```

1. 일괄 삭제는 이전에 복구된 테이블 목록에서 모든 테이블을 삭제하는 데 사용됩니다. 다음 쿼리가 사용됩니다.

   ```sql
   DELETE FROM NmsTrackingLogRcp WHERE iTrackingLogId IN (SELECT iTrackingLogId FROM NmsTrackingLogRcp WHERE tsLog < $(tsDate) LIMIT 5000) 
   ```

   위치 `$(tsDate)` 는 다음에 대해 정의된 기간을 뺀 현재 서버 날짜입니다. **NmsCleanup_TrackingLogPurgeDelay** 옵션을 선택합니다.

1. 추적 통계 테이블은 일괄 삭제를 사용하여 삭제됩니다. 다음 쿼리가 사용됩니다.

   ```sql
   DELETE FROM NmsTrackingStats WHERE iTrackingStatsId IN (SELECT iTrackingStatsId FROM NmsTrackingStats WHERE tsStart < $(tsDate) LIMIT 5000) 
   ```

   위치 `$(tsDate)` 는 다음에 대해 정의된 기간을 뺀 현재 서버 날짜입니다. **NmsCleanup_TrackingStatPurgeDelay** 옵션을 선택합니다.

### 게재 로그 정리 {#cleanup-of-delivery-logs}

이 작업을 통해 다양한 테이블에 저장된 게재 로그를 제거할 수 있습니다.

1. 이를 위해 다음 쿼리를 사용하여 게재 로그 스키마 목록을 복구합니다.

   ```sql
   SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL UNION SELECT distinct(sBroadLogExclSchema) FROM NmsDeliveryMapping WHERE sBroadLogExclSchema IS NOT NULL
   ```

1. 중간 소싱을 사용할 때 **NmsBroadLogMid** 게재 매핑에서 테이블이 참조되지 않습니다. 다음 **nms:broadLogMid** 스키마가 이전 쿼리에서 복구한 목록에 추가됩니다.
1. 다음 **데이터베이스 정리** 그런 다음 워크플로우는 이전에 복구한 테이블에서 오래된 데이터를 삭제합니다. 다음 쿼리가 사용됩니다.

   ```sql
   DELETE FROM $(tableName) WHERE iBroadLogId IN (SELECT iBroadLogId FROM $(tableName) WHERE tsLastModified < $(option) LIMIT 5000) 
   ```

   위치 `$(tableName)` 는 스키마 목록에 있는 각 테이블의 이름입니다. `$(option)` 은(는) 다음에 대해 정의된 날짜입니다. **NmsCleanup_BroadLogPurgeDelay** 옵션(참조: [배포 마법사](#deployment-wizard)).

1. 마지막으로 워크플로우는 **NmsProviderMsgId** 테이블이 있습니다. 이 경우 다음 쿼리를 사용하여 오래된 모든 데이터가 삭제됩니다.

   ```sql
   DELETE FROM NmsProviderMsgId WHERE iBroadLogId IN (SELECT iBroadLogId FROM NmsProviderMsgId WHERE tsCreated < $(option) LIMIT 5000)
   ```

   위치 `$(option)` 에 대해 정의된 날짜와 일치 **NmsCleanup_BroadLogPurgeDelay** 옵션(참조: [배포 마법사](#deployment-wizard)).

### NmsEmailErrorStat 테이블 정리 {#cleanup-of-the-nmsemailerrorstat-table-}

이 작업은 **NmsEmailErrorStat** 테이블. 기본 프로그램(**coalesceErrors**) 두 개의 날짜를 정의합니다.

* **시작일**: 다음 프로세스에 일치하는 날짜 **NmsLastErrorStatCoalesce** 선택 사항 또는 테이블의 가장 최근 날짜입니다.
* **종료일**: 현재 서버 날짜입니다.

시작 일자가 종료 일자보다 크거나 같은 경우 프로세스가 수행되지 않습니다. 이 경우 **coalesceUpToDate** 메시지가 나타납니다.

시작 일자가 종료 일자 이전이면 **NmsEmailErrorStat** 탁자가 깨끗해졌다.

의 총 오류 수 **NmsEmailErrorStat** 시작 날짜와 종료 날짜 사이의 테이블은 다음 쿼리를 사용하여 복구됩니다.

```sql
SELECT COUNT(*) FROM NmsEmailErrorStat WHERE tsDate>= $(start) AND tsDate< $(end)
```

위치 `$end` 및 `$start` 는 이전에 정의된 시작 및 종료 날짜입니다.

합계가 0보다 큰 경우:

1. 특정 임계값(20임)을 초과하는 오류만 유지하기 위해 다음 쿼리가 실행됩니다.

   ```sql
   SELECT iMXIP, iPublicId, SUM(iTotalConnections), SUM(iTotalErrors), SUM(iMessageErrors), SUM(iAbortedConnections), SUM(iFailedConnections), SUM(iRefusedConnections), SUM(iTimeoutConnections) FROM NmsEmailErrorStat WHERE tsDate>=$(start ) AND tsDate<$(end ) GROUP BY iMXIP, iPublicId HAVING SUM(iTotalErrors) >= 20
   ```

1. 다음 **병합 오류** 메시지가 표시됩니다.
1. 시작 날짜와 종료 날짜 사이에 발생한 모든 오류를 삭제하기 위해 새 연결이 만들어집니다. 다음 쿼리가 사용됩니다.

   ```sql
   DELETE FROM NmsEmailErrorStat WHERE tsDate>=$(start) AND tsDate<$(end)
   ```

1. 각 오류가에 저장됩니다. **NmsEmailErrorStat** 다음 쿼리를 사용하는 테이블:

   ```sql
   INSERT INTO NmsEmailErrorStat(iMXIP, iPublicId, tsDate, iTotalConnections, iTotalErrors, iTimeoutConnections, iRefusedConnections, iAbortedConnections, iFailedConnections, iMessageErrors) VALUES($(lmxip ), $(lpublicId ), $(tsstart ), $(lconnections ), $(lconnectionErrors ),$(ltimeoutConnections ), $(lrefusedConnections ), $(labortedConnections ), $(lfailedConnections ), $(lmessageErrors))
   ```

   여기서 각 변수는 이전 쿼리에서 복구한 값과 일치합니다.

1. 다음 **시작** 변수는 루프를 마치기 위해 이전 프로세스의 값으로 업데이트됩니다.

루프 및 작업 중지

정리 작업은 다음에서 실행됩니다. **NmsEmailError** 및 **cleanupNmsMxDomain** 테이블.

### NmsEmailError 테이블 정리 {#cleanup-of-the-nmsemailerror-table-}

다음 쿼리가 사용됩니다.

```sql
DELETE FROM NmsEmailError WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

이 쿼리는 연결된 레코드가 없는 모든 줄을 **NmsEmailErrorStat** 다음에서 **NmsEmailError** 테이블.

### NmsMxDomain 테이블 정리 {#cleanup-of-the-nmsmxdomain-table-}

다음 쿼리가 사용됩니다.

```sql
DELETE FROM NmsMxDomain WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

이 쿼리는 연결된 레코드가 없는 모든 줄을 **NmsEmailErrorStat** 의 테이블 **NmsMxDomain** 테이블.

### 제안 정리 {#cleanup-of-propositions}

다음과 같은 경우 **상호 작용** 모듈이 설치되었습니다. 이 작업은 다음을 제거하기 위해 실행됩니다. **NmsPropositionXxx** 테이블.

다음 쿼리를 사용하여 제안 테이블 목록을 복구하고 각 제안 테이블에서 대량 삭제를 수행합니다.

```sql
DELETE FROM NmsPropositionXxx WHERE iPropositionId IN (SELECT iPropositionId FROM NmsPropositionXxx WHERE tsLastModified < $(option) LIMIT 5000) 
```

위치 `$(option)` 은(는) 다음에 대해 정의된 날짜입니다. **NmsCleanup_PropositionPurgeDelay** 옵션(참조: [배포 마법사](#deployment-wizard)).

### 시뮬레이션 테이블 정리 {#cleanup-of-simulation-tables}

이 작업은 오퍼 시뮬레이션 또는 게재 시뮬레이션에 더 이상 연결되지 않는 고아 시뮬레이션 테이블을 정리합니다.

1. 정리가 필요한 시뮬레이션 목록을 복구하려면 다음 쿼리가 사용됩니다.

   ```sql
   SELECT iSimulationId FROM NmsSimulation WHERE iSimulationId<>0
   ```

1. 삭제할 테이블의 이름은 **wkSimu_** 접두사 뒤에 시뮬레이션 식별자가 옵니다(예: **wkSimu_456831_aggr**):

   ```sql
   DROP TABLE wkSimu_456831_aggr
   ```

### 감사 추적 정리 {#cleanup-of-audit-trail}

다음 쿼리가 사용됩니다.

```sql
DELETE FROM XtkAudit WHERE tsChanged < $(tsDate)
```

위치 **$(tsDate)** 은 기간에 대해 정의된 현재 서버 날짜입니다. **XtkCleanup_AuditTrailPurgeDelay** 옵션을 뺍니다.

### Nmsaddress 정리 {#cleanup-of-nmsaddress}

다음 쿼리가 사용됩니다.

```sql
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=STATUS_QUARANTINE AND tsLastModified < $(NmsCleanup_AppSubscriptionRcpPurgeDelay + 5d) AND iType IN (MESSAGETYPE_IOS, MESSAGETYPE_ANDROID ) LIMIT 5000)
```

이 쿼리는 iOS 및 Android와 관련된 모든 항목을 삭제합니다.

### 통계 업데이트 및 스토리지 최적화 {#statistics-update}

다음 **XtkCleanup_NoStats** 옵션을 사용하면 정리 워크플로우에서 스토리지 최적화 단계의 동작을 제어할 수 있습니다.

다음과 같은 경우 **XtkCleanup_NoStats** 옵션이 없거나 값이 0인 경우 PostgreSQL에서 세부 정보 표시 모드(VACUUM VERBOSE ANALYZE)로 스토리지 최적화를 실행하고 다른 모든 데이터베이스의 통계를 업데이트합니다. 이 명령이 실행되었는지 확인하려면 PostgreSQL 로그를 확인하십시오. VACUUM은 다음 형식으로 선을 출력합니다. `INFO: vacuuming "public.nmsactivecontact"` 및 ANALYZE는 다음 형식의 행을 출력합니다. `INFO: analyzing "public.nmsactivecontact"`.

이 옵션의 값이 1이면 어떤 데이터베이스에서도 통계 업데이트가 실행되지 않습니다. 워크플로우 로그에 다음 로그 줄이 나타납니다. `Option 'XtkCleanup_NoStats' is set to '1'`.

이 옵션의 값이 2이면 PostgreSQL에서 세부 정보 표시 모드(VERBOSE 분석)로 저장소 분석을 실행하고 다른 모든 데이터베이스의 통계를 업데이트합니다. 이 명령이 실행되었는지 확인하려면 PostgreSQL 로그를 확인하십시오. ANALYZE는 다음 형식으로 라인을 출력합니다. `INFO: analyzing "public.nmsactivecontact"`.

### 구독 정리(NMAC) {#subscription-cleanup--nmac-}

이 작업은 삭제된 서비스 또는 모바일 애플리케이션과 관련된 모든 구독을 삭제합니다.

broadlog 스키마 목록을 복구하려면 다음 쿼리가 사용됩니다.

```sql
SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL
```

그런 다음 작업은 연결된 테이블 이름을 복구합니다. **appSubscription** 이러한 테이블을 연결하고 삭제합니다.

또한 이 정리 워크플로우는 의 시간 설정 이후 업데이트되지 않은 idisabled = 1인 모든 항목을 삭제합니다. **NmsCleanup_AppSubscriptionRcpPurgeDelay** 옵션을 선택합니다.

### 세션 정보 정리 {#cleansing-session-information}

이 작업은 다음에서 정보를 정리합니다. **sessionInfo** 이 표에서는 다음 쿼리가 사용됩니다.

```sql
DELETE FROM XtkSessionInfo WHERE tsexpiration < $(curdate) 
```

### 만료된 이벤트 정리 {#cleansing-expired-events}

이 작업은 실행 인스턴스에 수신 및 저장된 이벤트와 제어 인스턴스에 보관된 이벤트를 정리합니다.

### 세정 반응 {#cleansing-reactions}

이 작업은 반응을 정리합니다(테이블). **NmsRemaMatchRcp**) 가설 자체가 삭제되었습니다.
