---
product: campaign
title: 데이터베이스 정리 워크플로
description: 오래된 데이터를 자동으로 정리하는 방법 알아보기
feature: Monitoring, Workflows
audience: production
content-type: reference
topic-tags: data-processing
exl-id: 75d3a0af-9a14-4083-b1da-2c1b22f57cbe
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '2829'
ht-degree: 0%

---

# 데이터베이스 정리 워크플로{#database-cleanup-workflow}



## 소개 {#introduction}

**[!UICONTROL Database cleanup]** 노드를 통해 액세스할 수 있는 **[!UICONTROL Administration > Production > Technical workflows]** 워크플로를 사용하면 데이터베이스의 기하급수적인 증가를 방지하기 위해 오래된 데이터를 삭제할 수 있습니다. 워크플로우는 사용자의 개입 없이 자동으로 트리거됩니다.

![정리](assets/ncs_cleanup_workflow.png)

## 구성 {#configuration}

데이터베이스 정리는 워크플로 스케줄러와 배포 마법사의 두 가지 수준에서 구성됩니다.

### 워크플로우 스케줄러 {#the-scheduler}

>[!NOTE]
>
>스케줄러에 대한 자세한 내용은 [Campaign v8 설명서](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/flow-control-activities/scheduler.html?lang=ko){target="_blank"}를 참조하세요.

기본적으로 **[!UICONTROL Database cleanup]** 워크플로우는 매일 오전 4시에 시작되도록 구성되어 있습니다. 스케줄러를 사용하여 워크플로우 트리거 빈도를 변경할 수 있습니다. 다음 빈도를 사용할 수 있습니다.

* **[!UICONTROL Several times a day]**
* **[!UICONTROL Daily]**
* **[!UICONTROL Weekly]**
* **[!UICONTROL Once]**

![스케줄러](assets/ncs_cleanup_scheduler.png)

>[!IMPORTANT]
>
>스케줄러에 정의된 날짜 및 시간에 **[!UICONTROL Database cleanup]** 워크플로우를 시작하려면 워크플로우 엔진(wfserver)을 시작해야 합니다.

### 배포 마법사 {#deployment-assistant}

**[!UICONTROL deployment wizard]** 메뉴를 통해 액세스할 수 있는 **[!UICONTROL Tools > Advanced]**&#x200B;을(를) 사용하면 데이터가 저장되는 기간을 구성할 수 있습니다. 값은 일 단위로 표시됩니다. 이 값을 변경하지 않으면 워크플로우는 기본값을 사용합니다.

![](assets/ncs_cleanup_deployment-wizard.png)

**[!UICONTROL Purge of data]** 창의 필드가 다음 옵션과 일치합니다. **[!UICONTROL Database cleanup]** 워크플로에서 실행되는 일부 작업에서 사용됩니다.

* 통합 추적: **NmsCleanup_TrackingStatPurgeDelay**([추적 로그 정리 참조](#cleanup-of-tracking-logs))
* 게재 로그: **NmsCleanup_BroadLogPurgeDelay**([게재 로그 정리 참조](#cleanup-of-delivery-logs))
* 추적 로그: **NmsCleanup_TrackingLogPurgeDelay**([추적 로그 정리 참조](#cleanup-of-tracking-logs))
* 삭제된 게재: **NmsCleanup_RecycedDeliveryPurgeDelay**([삭제되거나 재활용될 게재 정리 참조](#cleanup-of-deliveries-to-be-deleted-or-recycled))
* 가져오기 거부: **NmsCleanup_RejectsPurgeDelay**([가져오기에 의해 생성된 거부 정리 참조](#cleanup-of-rejects-generated-by-imports-))
* 방문자 프로필: **NmsCleanup_VisitorPurgeDelay**([방문자 정리 참조](#cleanup-of-visitors))
* 오퍼 제안: **NmsCleanup_PropositionPurgeDelay**([제안 정리 참조](#cleanup-of-propositions))

  >[!NOTE]
  >
  >**[!UICONTROL Offer propositions]** 필드는 **Interaction** 모듈이 설치된 경우에만 사용할 수 있습니다.

* 이벤트: **NmsCleanup_EventPurgeDelay**([만료된 이벤트 정리 참조](#cleansing-expired-events))
* 보관된 이벤트: **NmsCleanup_EventHistoPurgeDelay**([만료된 이벤트 정리 참조](#cleansing-expired-events))

  >[!NOTE]
  >
  >**[!UICONTROL Events]** 및 **[!UICONTROL Archived events]** 필드는 **메시지 센터** 모듈이 설치된 경우에만 사용할 수 있습니다.

* 감사 추적: **XtkCleanup_AuditTrailPurgeDelay**([감사 추적 정리](#cleanup-of-audit-trail) 참조)

**[!UICONTROL Database cleanup]** 워크플로에서 실행되는 모든 작업은 다음 섹션에 설명되어 있습니다.

## 데이터베이스 정리 워크플로우에서 수행되는 작업 {#tasks-carried-out-by-the-database-cleanup-workflow}

워크플로 스케줄러([스케줄러](#the-scheduler) 참조)에 정의된 날짜 및 시간에 워크플로 엔진이 데이터베이스 정리 프로세스를 시작합니다. 데이터베이스 정리는 데이터베이스에 연결하고 아래 표시된 순서대로 작업을 실행합니다.

>[!IMPORTANT]
>
>이 작업 중 하나가 실패하면 다음 작업이 실행되지 않습니다.
>
>**LIMIT** 특성이 있는 SQL 쿼리는 모든 정보가 처리될 때까지 반복적으로 실행됩니다.


### 정리 삭제 목록 {#lists-to-delete-cleanup}

**[!UICONTROL Database cleanup]** 워크플로에서 실행되는 첫 번째 작업은 **deleteStatus !=** NmsGroup **의 0** 특성. 이러한 그룹에 연결되어 있고 다른 테이블에 있는 레코드도 삭제됩니다.

1. 삭제할 목록은 다음 SQL 쿼리를 사용하여 복구됩니다.

   ```sql
   SELECT iGroupId, sLabel, iType FROM NmsGroup WHERE iDeleteStatus <> 0 OR tsExpirationDate <= GetDate() 
   ```

1. 각 목록에는 다른 테이블에 대한 여러 링크가 있습니다. 이러한 모든 링크는 다음 쿼리를 사용하여 일괄적으로 삭제됩니다.

   ```sql
   DELETE FROM $(relatedTable) WHERE iGroupId=$(l) IN (SELECT iGroupId FROM $(relatedTable) WHERE iGroupId=$(l) LIMIT 5000) 
   ```

   여기서 `$(relatedTable)`은(는) **NmsGroup**&#x200B;과(와) 관련된 테이블이고 `$(l)`은(는) 목록 식별자입니다.

1. 목록이 &#39;목록&#39; 유형 목록인 경우 다음 쿼리를 사용하여 관련 테이블이 삭제됩니다.

   ```sql
   DROP TABLE grp$(l)
   ```

1. 다음 쿼리를 사용하여 작업에 의해 복구된 모든 **Select** 형식 목록을 삭제합니다.

   ```sql
   DELETE FROM NmsGroup WHERE iGroupId=$(l) 
   ```

   여기서 `$(l)`은(는) 목록 식별자입니다.

### 삭제하거나 재활용할 게재 정리 {#cleanup-of-deliveries-to-be-deleted-or-recycled}

이 작업은 삭제하거나 재활용할 모든 게재를 삭제합니다.

1. **[!UICONTROL Database cleanup]** 워크플로에서는 **deleteStatus** 필드의 값이 **[!UICONTROL Yes]** 또는 **[!UICONTROL Recycled]**&#x200B;이고 삭제 날짜가 배포 마법사의 **[!UICONTROL Deleted deliveries]**(**NmsCleanup_RecycedDeliveryPurgeDelay**) 필드에 정의된 기간 이전인 모든 게재를 선택합니다. 자세한 내용은 [배포 마법사](#deployment-assistant)를 참조하세요. 이 기간은 현재 서버 날짜를 기준으로 계산됩니다.
1. 각 중간 소싱 서버에 대해 작업은 삭제할 게재 목록을 선택합니다.
1. **[!UICONTROL Database cleanup]** 워크플로는 게재 로그, 첨부 파일, 미러 페이지 정보 및 기타 모든 관련 데이터를 삭제합니다.
1. 정상적으로 게재를 삭제하기 전에 워크플로우는 다음 표에서 연결된 정보를 삭제합니다.

   * 게재 제외 테이블(**NmsDlvExclusion**)에서는 다음 쿼리가 사용됩니다.

     ```sql
     DELETE FROM NmsDlvExclusion WHERE iDeliveryId=$(l)
     ```

     여기서 **$(l)**&#x200B;은(는) 게재 식별자입니다.

   * 쿠폰 테이블(**NmsCouponValue**)에서 다음 쿼리가 사용됩니다(대량 삭제 포함).

     ```sql
     DELETE FROM NmsCouponValue WHERE iMessageId IN (SELECT iMessageId FROM NmsCouponValue WHERE EXISTS (SELECT B.iBroadLogId FROM $(BroadLogTableName) B WHERE B.iDeliveryId = $(l) AND B.iBroadLogId = iMessageId ) LIMIT 5000)
     ```

     여기서 `$(l)`은(는) 게재 식별자입니다.

   * 게재 로그 테이블(**NmsBroadlogXxx**)에서 대량 삭제는 20,000개의 레코드로 일괄적으로 실행됩니다.
   * 오퍼 제안 테이블(**NmsPropositionXxx**)에서 대량 삭제는 20,000개의 레코드로 일괄적으로 실행됩니다.
   * 추적 로그 테이블(**NmsTrackinglogXxx**)에서 대량 삭제는 20,000개의 레코드로 일괄적으로 실행됩니다.
   * 게재 조각 테이블(**NmsDeliveryPart**)에서 대량 삭제는 50만 개의 레코드로 일괄적으로 실행됩니다. 이 표에는 게재할 나머지 메시지에 대한 개인화 정보가 포함되어 있습니다.
   * 미러 페이지 데이터 조각 테이블(**NmsMirrorPageInfo**)에서 대량 삭제는 만료된 게재 부분 및 완료 또는 취소된 부분에 대해 20,000개의 레코드로 일괄적으로 실행됩니다. 이 표에는 미러 페이지 생성에 사용되는 모든 메시지에 대한 개인화 정보가 포함되어 있습니다.
   * 미러 페이지 검색 테이블(**NmsMirrorPageSearch**)에서 대량 삭제는 20,000개의 레코드로 일괄적으로 실행됩니다. 이 테이블은 **NmsMirrorPageInfo** 테이블에 저장된 개인화 정보에 대한 액세스를 제공하는 검색 색인입니다.
   * 일괄 처리 프로세스 로그 테이블(**XtkJobLog**)에서 대량 삭제는 20,000개의 레코드로 일괄적으로 실행됩니다. 이 표에는 삭제할 게재 로그가 포함되어 있습니다.
   * 게재 URL 추적 테이블(**NmsTrackingUrl**)에서 다음 쿼리가 사용됩니다.

     ```sql
     DELETE FROM NmsTrackingUrl WHERE iDeliveryId=$(l)
     ```

     여기서 `$(l)`은(는) 게재 식별자입니다.

     이 표에는 추적을 활성화하기 위해 삭제할 게재에서 찾은 URL이 포함되어 있습니다.

1. 게재가 게재 테이블(**NmsDelivery**)에서 삭제되었습니다.

   ```sql
   DELETE FROM NmsDelivery WHERE iDeliveryId = $(l)
   ```

   여기서 `$(l)`은(는) 게재 식별자입니다.

#### 중간 소싱을 사용한 게재 {#deliveries-using-mid-sourcing}

**[!UICONTROL Database cleanup]** 워크플로우에서는 중간 소싱 서버의 게재도 삭제합니다.

1. 이를 위해 워크플로우는 각 게재가 비활성 상태임을 확인합니다(상태에 따라 다름). 게재가 활성 상태이면 삭제하기 전에 중지됩니다. 다음 쿼리를 실행하여 확인합니다.

   ```sql
   SELECT iState FROM NmsDelivery WHERE iDeliveryId = $(l) AND iState <> 100;
   ```

   여기서 **$(l)**&#x200B;은(는) 게재 식별자입니다.

1. 상태 값이 **[!UICONTROL Start pending]** , **[!UICONTROL In progress]** , **[!UICONTROL Recovery pending]** , **[!UICONTROL Recovery in progress]** , **[!UICONTROL Pause requested]** , **[!UICONTROL Pause in progress]** 또는 **[!UICONTROL Paused]**(값 51, 55, 61, 62, 71, 72, 75)이면 게재가 중지되고 작업이 연결된 정보를 삭제합니다.

### 만료된 게재 정리 {#cleanup-of-expired-deliveries}

이 작업은 유효 기간이 만료된 게재를 중지합니다.

1. **[!UICONTROL Database cleanup]** 워크플로에서 만료된 게재 목록을 만듭니다. 이 목록에는 **[!UICONTROL Finished]** 이외의 상태로 만료된 모든 게재와 10,000개 이상의 처리되지 않은 메시지가 있는 최근에 중지된 게재가 포함됩니다. 다음 쿼리가 사용됩니다.

   ```sql
   SELECT iDeliveryId, iState FROM NmsDelivery WHERE iDeleteStatus=0 AND iIsModel=0 AND iDeliveryMode=1 AND ( (iState >= 51 AND iState < 85 AND tsValidity IS NOT NULL AND tsValidity < $(currentDate) ) OR (iState = 85 AND DateMinusDays(15) < tsLastModified AND iToDeliver - iProcessed >= 10000 ))
   ```

   여기서 `delivery mode 1`은(는) **[!UICONTROL Mass delivery]** 모드와 일치하고, `state 51`은(는) **[!UICONTROL Start pending]** 상태와 일치하고, `state 85`은(는) **[!UICONTROL Stopped]** 상태와 일치하며, 게재 서버에서 대량 업데이트된 가장 많은 게재 로그 수는 10,000개입니다.

1. 그러면 워크플로우에는 중간 소싱을 사용하는 최근에 만료된 게재 목록이 포함됩니다. 중간 소싱 서버를 통해 아직 게재 로그가 복구되지 않은 게재는 제외됩니다.

   다음 쿼리가 사용됩니다.

   ```sql
   SELECT iDeliveryId, tsValidity, iMidRemoteId, mData FROM NmsDelivery WHERE (iDeliveryMode = 4 AND (iState = 85 OR iState = 95) AND tsValidity IS NOT NULL AND (tsValidity < SubDays(GetDate() , 15) OR tsValidity < $(DateOfLastLogPullUp)) AND tsLastModified > SubDays(GetDate() , 15))
   ```

1. 다음 쿼리는 날짜별로 게재를 필터링하기 위해 외부 계정이 여전히 활성 상태인지 여부를 감지하는 데 사용됩니다.

   ```sql
   SELECT iExtAccountId FROM NmsExtAccount WHERE iActive<>0 AND sName=$(providerName)
   ```

1. 만료된 게재 목록에서 상태가 **[!UICONTROL Pending]**&#x200B;인 게재 로그는 **[!UICONTROL Delivery cancelled]**(으)로 전환되고 이 목록에 있는 모든 게재는 **[!UICONTROL Finished]**(으)로 전환됩니다.

   다음 쿼리가 사용됩니다.

   ```sql
   UPDATE $(BroadLogTableName) SET tsLastModified=$(curdate), iStatus=7, iMsgId=$(bl) WHERE iDeliveryId=$(dl) AND iStatus=6
   ```

   여기서 `$(curdate)`은(는) 데이터베이스 서버의 현재 날짜이고, `$(bl)`은(는) 게재 로그 메시지의 식별자이며, `$(dl)`은(는) 게재 식별자이고, `delivery status 6`은(는) **[!UICONTROL Pending]** 상태와 일치하고, `delivery status 7`은(는) **[!UICONTROL Delivery cancelled]** 상태와 일치합니다.

   ```sql
   UPDATE NmsDelivery SET iState = 95, tsLastModified = $(curdate), tsBroadEnd = tsValidity WHERE iDeliveryId = $(dl)
   ```

   여기서 `delivery state 95`은(는) **[!UICONTROL Finished]** 상태와 일치하고 `$(dl)`은(는) 게재 식별자입니다.

1. 오래된 게재의 모든 조각(**deliveryParts**)이 삭제되고 진행 중인 알림 게재의 오래된 조각이 모두 삭제됩니다. 이 두 작업에는 일괄 삭제가 사용됩니다.

   다음 쿼리가 사용됩니다.

   ```sql
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE iDeliveryId IN (SELECT iDeliveryId FROM NmsDelivery WHERE iState=95 OR iState=85) LIMIT 5000)
   ```

   ```sql
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE tsValidity < $(curDate) LIMIT 500000)
   ```

   여기서 `delivery state 95`은(는) **[!UICONTROL Finished]** 상태와 일치하고 `delivery state 85`은(는) **[!UICONTROL Stopped]** 상태와 일치하며 `$(curDate)`은(는) 현재 서버 날짜입니다.

### 미러 페이지 정리 {#cleanup-of-mirror-pages}

이 작업은 게재에 사용되는 웹 리소스(미러 페이지)를 삭제합니다.

1. 먼저 다음 쿼리를 사용하여 삭제할 게재 목록을 복구합니다.

   ```sql
   SELECT iDeliveryId, iNeedMirrorPage FROM NmsDelivery WHERE iWebResPurged = 0 AND tsWebValidity IS NOT NULL AND tsWebValidity < $(curdate)
   ```

   여기서 `$(curDate)`은(는) 현재 서버 날짜입니다.

1. 그런 다음 필요한 경우 이전에 복구된 게재의 식별자를 사용하여 **NmsMirrorPageInfo** 테이블을 삭제합니다. 대량 삭제는 다음 쿼리를 생성하는 데 사용됩니다.

   ```sql
   DELETE FROM NmsMirrorPageInfo WHERE iMirrorPageInfoId IN (SELECT iMirrorPageInfoId FROM NmsMirrorPageInfo WHERE iDeliveryId = $(dl)) LIMIT 5000
   ```

   ```sql
   DELETE FROM NmsMirrorPageSearch WHERE iMessageId IN (SELECT iMessageId FROM NmsMirrorPageSearch WHERE iDeliveryId = $(dl)) LIMIT 5000
   ```

   여기서 `$(dl)`은(는) 게재 식별자입니다.

1. 그런 다음 항목이 게재 로그에 추가됩니다.
1. 그런 다음 삭제된 게재가 식별되어 나중에 다시 처리할 필요가 없습니다. 다음 쿼리가 실행됩니다.

   ```sql
   UPDATE NmsDelivery SET iWebResPurged = 1 WHERE iDeliveryId IN ($(strIn))
   ```

   여기서 `$(strIn)`은(는) 게재 식별자 목록입니다.

### 작업 테이블 정리 {#cleanup-of-work-tables}

이 작업은 상태가 **[!UICONTROL Being edited]** , **[!UICONTROL Stopped]** 또는 **[!UICONTROL Deleted]**&#x200B;인 게재와 일치하는 모든 작업 테이블을 데이터베이스에서 삭제합니다.

1. 이름이 **wkDlv_**&#x200B;로 시작하는 테이블 목록은 먼저 다음 쿼리(postgresql)를 사용하여 복구됩니다.

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkDlv_%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. 그러면 진행 중인 워크플로우에서 사용하는 표는 제외됩니다. 이를 위해 다음 쿼리를 사용하여 진행 중인 게재 목록을 복구합니다.

   ```sql
   SELECT iDeliveryId FROM NmsDelivery WHERE iDeliveryId<>0 AND iDeleteStatus=0 AND iState NOT IN (0,85,100);
   ```

   여기서 `0`은(는) **[!UICONTROL Being edited]** 게재 상태와 일치하는 값이고 `85`은(는) **[!UICONTROL Stopped]** 상태와 일치하며 `100`은(는) **[!UICONTROL Deleted]** 상태와 일치합니다.

1. 더 이상 사용되지 않는 테이블은 다음 쿼리를 사용하여 삭제됩니다.

   ```sql
   DROP TABLE wkDlv_15487_1;
   ```

### 가져오기에 의해 생성된 거부 정리 {#cleanup-of-rejects-generated-by-imports-}

이 단계에서는 가져오는 동안 모든 데이터가 처리되지 않은 레코드를 삭제할 수 있습니다.

1. 다음 쿼리를 사용하여 **XtkReject** 테이블에서 대량 삭제를 수행합니다.

   ```sql
   DELETE FROM XtkReject WHERE iRejectId IN (SELECT iRejectId FROM XtkReject WHERE tsLog < $(curDate)) LIMIT $(l)
   ```

   여기서 `$(curDate)`은(는) **NmsCleanup_RejectPurgeDelay** 옵션([배포 마법사](#deployment-assistant) 참조)에 대해 정의된 기간을 뺀 현재 서버 날짜이고 `$(l)`은(는) 대량 삭제할 최대 레코드 수입니다.

1. 그런 다음 모든 고아 거부가 다음 쿼리를 사용하여 삭제됩니다.

   ```sql
   DELETE FROM XtkReject WHERE iJobId NOT IN (SELECT iJobId FROM XtkJob)
   ```

### 워크플로우 인스턴스 정리 {#cleanup-of-workflow-instances}

이 작업은 식별자(**lWorkflowId**)와 기록(**lHistory**)을 사용하여 각 워크플로 인스턴스를 제거합니다. 작업 테이블 정리 작업을 다시 실행하여 비활성 테이블을 삭제합니다. 또한 정리 시 삭제된 워크플로우의 모든 분리된 작업 테이블(wkf% 및 wkfhisto%)이 삭제됩니다.

>[!NOTE]
>
>**일 단위 기록** 필드의 각 워크플로우에 대해 내역의 제거 빈도가 지정됩니다(기본값: 30일). 이 필드는 워크플로우 속성의 **실행** 탭에서 찾을 수 있습니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../workflow/using/workflow-properties.md#execution)을 참조하십시오.

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

   여기서 `$(lworkflow)`은(는) 워크플로의 식별자이고 `$(lhistory)`은(는) 기록의 식별자입니다.

1. 사용되지 않은 테이블은 모두 삭제됩니다. 이를 위해 다음 쿼리(postgresql)를 사용하는 **wkf%** 형식 마스크 덕분에 모든 테이블이 수집됩니다.

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

   여기서 `$(strcondition)`은(는) **wkfhisto%** 마스크와 일치하는 테이블 목록입니다.

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

이 작업은 그룹에 연결된 고아 작업 테이블을 삭제합니다. **NmsGroup** 테이블은 정리할 그룹을 저장합니다(형식이 0과 다름). 테이블 이름의 접두사는 **grp**&#x200B;입니다. 정리할 그룹을 식별하려면 다음 쿼리가 사용됩니다.

```sql
SELECT iGroupId FROM NmsGroup WHERE iType>0"
```

### 방문자 정리 {#cleanup-of-visitors}

이 작업은 일괄 삭제를 사용하여 방문자 테이블에서 오래된 레코드를 삭제합니다. 사용되지 않는 레코드는 마지막 수정이 배포 마법사에 정의된 보존 기간보다 이전입니다([배포 마법사](#deployment-assistant) 참조). 다음 쿼리가 사용됩니다.

```sql
DELETE FROM NmsVisitor WHERE iVisitorId IN (SELECT iVisitorId FROM NmsVisitor WHERE iRecipientId = 0 AND tsLastModified < AddDays(GetDate(), -30) AND iOrigin = 0 LIMIT 20000)
```

여기서 `$(tsDate)`은(는) **NmsCleanup_VisitorPurgeDelay** 옵션에 대해 정의된 기간을 뺀 현재 서버 날짜입니다.

### NPAI 정리 {#cleanup-of-npai}

이 작업을 사용하면 **NmsAddress** 테이블에서 유효한 주소와 일치하는 레코드를 삭제할 수 있습니다. 다음 질의를 사용하여 대량 삭제를 수행합니다.

```sql
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=2 AND tsLastModified < $(tsDate1) AND tsLastModified >= $(tsDate2) LIMIT 5000)
```

여기서 `status 2`은(는) **[!UICONTROL Valid]** 상태와 일치하고 `$(tsDate1)`은(는) 현재 서버 날짜이며 `$(tsDate2)`은(는) **NmsCleanup_LastCleanup** 옵션과 일치합니다.

### 구독 정리 {#cleanup-of-subscriptions-}

이 작업은 일괄 삭제를 사용하여 **NmsSubscription** 테이블에서 사용자가 삭제한 모든 구독을 삭제합니다. 다음 쿼리가 사용됩니다.

```sql
DELETE FROM NmsSubscription WHERE iDeleteStatus <>0
```

### 추적 로그 정리 {#cleanup-of-tracking-logs}

이 작업은 추적 및 웹 추적 로그 테이블에서 오래된 레코드를 삭제합니다. 오래된 레코드는 배포 마법사에 정의된 보존 기간보다 이전입니다([배포 마법사](#deployment-assistant) 참조).

1. 먼저 다음 쿼리를 사용하여 추적 로그 테이블 목록을 복구합니다.

   ```sql
   SELECT distinct(sTrackingLogSchema) FROM NmsDeliveryMapping WHERE sTrackingLogSchema IS NOT NULL;
   ```

1. 일괄 삭제는 이전에 복구된 테이블 목록에서 모든 테이블을 삭제하는 데 사용됩니다. 다음 쿼리가 사용됩니다.

   ```sql
   DELETE FROM NmsTrackingLogRcp WHERE iTrackingLogId IN (SELECT iTrackingLogId FROM NmsTrackingLogRcp WHERE tsLog < $(tsDate) LIMIT 5000) 
   ```

   여기서 `$(tsDate)`은(는) **NmsCleanup_TrackingLogPurgeDelay** 옵션에 대해 정의된 기간을 뺀 현재 서버 날짜입니다.

1. 추적 통계 테이블은 일괄 삭제를 사용하여 삭제됩니다. 다음 쿼리가 사용됩니다.

   ```sql
   DELETE FROM NmsTrackingStats WHERE iTrackingStatsId IN (SELECT iTrackingStatsId FROM NmsTrackingStats WHERE tsStart < $(tsDate) LIMIT 5000) 
   ```

   여기서 `$(tsDate)`은(는) **NmsCleanup_TrackingStatPurgeDelay** 옵션에 대해 정의된 기간을 뺀 현재 서버 날짜입니다.

### 게재 로그 정리 {#cleanup-of-delivery-logs}

이 작업을 통해 다양한 테이블에 저장된 게재 로그를 제거할 수 있습니다.

1. 이를 위해 다음 쿼리를 사용하여 게재 로그 스키마 목록을 복구합니다.

   ```sql
   SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL UNION SELECT distinct(sBroadLogExclSchema) FROM NmsDeliveryMapping WHERE sBroadLogExclSchema IS NOT NULL
   ```

1. 중간 소싱을 사용할 때 **NmsBroadLogMid** 테이블이 게재 매핑에서 참조되지 않습니다. **nms:broadLogMid** 스키마가 이전 쿼리에서 복구한 목록에 추가됩니다.
1. 그런 다음 **데이터베이스 정리** 워크플로에서는 이전에 복구한 테이블에서 오래된 데이터를 제거합니다. 다음 쿼리가 사용됩니다.

   ```sql
   DELETE FROM $(tableName) WHERE iBroadLogId IN (SELECT iBroadLogId FROM $(tableName) WHERE tsLastModified < $(option) LIMIT 5000) 
   ```

   여기서 `$(tableName)`은(는) 스키마 목록에 있는 각 테이블의 이름이고 `$(option)`은(는) **NmsCleanup_BroadLogPurgeDelay** 옵션에 대해 정의된 날짜입니다([배포 마법사](#deployment-assistant) 참조).

1. 마지막으로 워크플로는 **NmsProviderMsgId** 테이블이 있는지 확인합니다. 이 경우 다음 쿼리를 사용하여 오래된 모든 데이터가 삭제됩니다.

   ```sql
   DELETE FROM NmsProviderMsgId WHERE iBroadLogId IN (SELECT iBroadLogId FROM NmsProviderMsgId WHERE tsCreated < $(option) LIMIT 5000)
   ```

   여기서 `$(option)`은(는) **NmsCleanup_BroadLogPurgeDelay** 옵션에 대해 정의된 날짜와 일치합니다([배포 마법사](#deployment-assistant) 참조).

### NmsEmailErrorStat 테이블 정리 {#cleanup-of-the-nmsemailerrorstat-table-}

이 작업은 **NmsEmailErrorStat** 테이블을 정리합니다. 기본 프로그램(**coalesceErrors**)은 두 개의 날짜를 정의합니다.

* **시작 날짜**: **NmsLastErrorStatCoalesce** 옵션 또는 테이블의 가장 최근 날짜와 일치하는 다음 프로세스의 날짜.
* **종료 날짜**: 현재 서버 날짜입니다.

시작 일자가 종료 일자보다 크거나 같은 경우 프로세스가 수행되지 않습니다. 이 경우 **coalesceUpToDate** 메시지가 나타납니다.

시작 날짜가 종료 날짜 이전이면 **NmsEmailErrorStat** 테이블이 정리됩니다.

시작 날짜와 종료 날짜 사이의 **NmsEmailErrorStat** 테이블의 총 오류 수는 다음 쿼리를 사용하여 복구됩니다.

```sql
SELECT COUNT(*) FROM NmsEmailErrorStat WHERE tsDate>= $(start) AND tsDate< $(end)
```

여기서 `$end` 및 `$start`은(는) 이전에 정의된 시작 및 종료 날짜입니다.

합계가 0보다 큰 경우:

1. 특정 임계값(20임)을 초과하는 오류만 유지하기 위해 다음 쿼리가 실행됩니다.

   ```sql
   SELECT iMXIP, iPublicId, SUM(iTotalConnections), SUM(iTotalErrors), SUM(iMessageErrors), SUM(iAbortedConnections), SUM(iFailedConnections), SUM(iRefusedConnections), SUM(iTimeoutConnections) FROM NmsEmailErrorStat WHERE tsDate>=$(start ) AND tsDate<$(end ) GROUP BY iMXIP, iPublicId HAVING SUM(iTotalErrors) >= 20
   ```

1. **coalescingErrors** 메시지가 표시됩니다.
1. 시작 날짜와 종료 날짜 사이에 발생한 모든 오류를 삭제하기 위해 새 연결이 만들어집니다. 다음 쿼리가 사용됩니다.

   ```sql
   DELETE FROM NmsEmailErrorStat WHERE tsDate>=$(start) AND tsDate<$(end)
   ```

1. 각 오류는 다음 쿼리를 사용하여 **NmsEmailErrorStat** 테이블에 저장됩니다.

   ```sql
   INSERT INTO NmsEmailErrorStat(iMXIP, iPublicId, tsDate, iTotalConnections, iTotalErrors, iTimeoutConnections, iRefusedConnections, iAbortedConnections, iFailedConnections, iMessageErrors) VALUES($(lmxip ), $(lpublicId ), $(tsstart ), $(lconnections ), $(lconnectionErrors ),$(ltimeoutConnections ), $(lrefusedConnections ), $(labortedConnections ), $(lfailedConnections ), $(lmessageErrors))
   ```

   여기서 각 변수는 이전 쿼리에서 복구한 값과 일치합니다.

1. **start** 변수가 루프를 마치기 위해 이전 프로세스의 값으로 업데이트되었습니다.

루프 및 작업 중지

**NmsEmailError** 및 **cleanupNmsMxDomain** 테이블에서 정리가 실행됩니다.

### NmsEmailError 테이블 정리 {#cleanup-of-the-nmsemailerror-table-}

다음 쿼리가 사용됩니다.

```sql
DELETE FROM NmsEmailError WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

이 쿼리는 **NmsEmailError** 테이블에서 **NmsEmailErrorStat**&#x200B;에 연결된 레코드가 없는 모든 줄을 삭제합니다.

### NmsMxDomain 테이블 정리 {#cleanup-of-the-nmsmxdomain-table-}

다음 쿼리가 사용됩니다.

```sql
DELETE FROM NmsMxDomain WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

이 쿼리는 **NmsMxDomain** 테이블에서 **NmsEmailErrorStat** 테이블에 연결된 레코드가 없는 모든 줄을 삭제합니다.

### 제안 정리 {#cleanup-of-propositions}

**Interaction** 모듈이 설치되어 있으면 이 작업이 실행되어 **NmsPropositionXxx** 테이블을 제거합니다.

다음 쿼리를 사용하여 제안 테이블 목록을 복구하고 각 제안 테이블에서 대량 삭제를 수행합니다.

```sql
DELETE FROM NmsPropositionXxx WHERE iPropositionId IN (SELECT iPropositionId FROM NmsPropositionXxx WHERE tsLastModified < $(option) LIMIT 5000) 
```

여기서 `$(option)`은(는) **NmsCleanup_PropositionPurgeDelay** 옵션에 대해 정의된 날짜입니다([배포 마법사](#deployment-assistant) 참조).

### 시뮬레이션 테이블 정리 {#cleanup-of-simulation-tables}

이 작업은 오퍼 시뮬레이션 또는 게재 시뮬레이션에 더 이상 연결되지 않는 고아 시뮬레이션 테이블을 정리합니다.

1. 정리가 필요한 시뮬레이션 목록을 복구하려면 다음 쿼리가 사용됩니다.

   ```sql
   SELECT iSimulationId FROM NmsSimulation WHERE iSimulationId<>0
   ```

1. 삭제할 테이블의 이름은 **wkSimu_** 접두사와 시뮬레이션 식별자(예: **wkSimu_456831_aggr**)로 구성됩니다.

   ```sql
   DROP TABLE wkSimu_456831_aggr
   ```

### 감사 추적 정리 {#cleanup-of-audit-trail}

다음 쿼리가 사용됩니다.

```sql
DELETE FROM XtkAudit WHERE tsChanged < $(tsDate)
```

여기서 **$(tsDate)**&#x200B;은(는) **XtkCleanup_AuditTrailPurgeDelay** 옵션에 대해 정의된 기간을 뺀 현재 서버 날짜입니다.

### Nmsaddress 정리 {#cleanup-of-nmsaddress}

다음 쿼리가 사용됩니다.

```sql
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=STATUS_QUARANTINE AND tsLastModified < $(NmsCleanup_AppSubscriptionRcpPurgeDelay + 5d) AND iType IN (MESSAGETYPE_IOS, MESSAGETYPE_ANDROID ) LIMIT 5000)
```

이 쿼리는 iOS 및 Android과 관련된 모든 항목을 삭제합니다.

### 통계 업데이트 및 스토리지 최적화 {#statistics-update}

**XtkCleanup_NoStats** 옵션을 사용하면 정리 워크플로우에서 저장소 최적화 단계의 동작을 제어할 수 있습니다.

**XtkCleanup_NoStats** 옵션이 없거나 값이 0인 경우 PostgreSQL에서 세부 정보 표시 모드(VACUUM VERBOSE ANALYZE)로 저장소 최적화를 실행하고 다른 모든 데이터베이스의 통계를 업데이트합니다. 이 명령이 실행되었는지 확인하려면 PostgreSQL 로그를 확인하십시오. VACUUM은 `INFO: vacuuming "public.nmsactivecontact"` 형식의 행을 출력하며 ANALYZE는 `INFO: analyzing "public.nmsactivecontact"` 형식의 행을 출력합니다.

이 옵션의 값이 1이면 어떤 데이터베이스에서도 통계 업데이트가 실행되지 않습니다. `Option 'XtkCleanup_NoStats' is set to '1'` 로그 줄이 워크플로우 로그에 나타납니다.

이 옵션의 값이 2이면 PostgreSQL에서 세부 정보 표시 모드(VERBOSE 분석)로 저장소 분석을 실행하고 다른 모든 데이터베이스의 통계를 업데이트합니다. 이 명령이 실행되었는지 확인하려면 PostgreSQL 로그를 확인하십시오. ANALYZE는 `INFO: analyzing "public.nmsactivecontact"` 형식의 행을 출력합니다.

### 구독 정리(NMAC) {#subscription-cleanup--nmac-}

이 작업은 삭제된 서비스 또는 모바일 애플리케이션과 관련된 모든 구독을 삭제합니다.

broadlog 스키마 목록을 복구하려면 다음 쿼리가 사용됩니다.

```sql
SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL
```

그런 다음 작업은 **appSubscription** 링크에 연결된 테이블 이름을 복구하고 이러한 테이블을 삭제합니다.

또한 이 정리 워크플로는 **NmsCleanup_AppSubscriptionRcpPurgeDelay** 옵션에 설정된 시간 이후 업데이트되지 않은 isabled = 1인 모든 항목을 삭제합니다.

### 세션 정보 정리 {#cleansing-session-information}

이 작업은 **sessionInfo** 테이블에서 정보를 정리합니다. 다음 쿼리가 사용됩니다.

```sql
DELETE FROM XtkSessionInfo WHERE tsexpiration < $(curdate) 
```

### 만료된 이벤트 정리 {#cleansing-expired-events}

이 작업은 실행 인스턴스에 수신 및 저장된 이벤트와 제어 인스턴스에 보관된 이벤트를 정리합니다.

### 세정 반응 {#cleansing-reactions}

이 작업은 가설 자체가 삭제된 반응(테이블 **NmsRemaMatchRcp**)을 정리합니다.
