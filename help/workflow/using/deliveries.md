---
product: campaign
title: 게재
description: 기본 게재 워크플로우에 대해 자세히 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 6%

---


# 게재{#deliveries}



아래에 설명된 워크플로우는 **게재** 기본적으로 모듈입니다.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블</strong><br /> </td> 
   <td> <strong>내부 이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">합계 보고</span> <br /> </td> 
   <td> <span class="uicontrol">reportingAggregates</span> <br /> </td> 
   <td> 이 워크플로우는 보고서에 사용되는 합계를 업데이트합니다. 기본적으로 매일 오전 2시에 트리거됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">과금</span> <br /> </td> 
   <td> <span class="uicontrol">billing</span> <br /> </td> 
   <td> 이 워크플로우는 '과금' 운영자에게 이메일로 시스템 활동 보고서를 보냅니다. 기본적으로 매월 25일에 트리거됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">별칭 정리</span> <br /> </td> 
   <td> <span class="uicontrol">aliasCleaning</span> <br /> </td> 
   <td> 이 워크플로우는 열거형 값을 표준화합니다. 기본적으로 매일 오전 3시에 트리거됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">게재 가능성을 위해 새로 고침</span> <br /> </td> 
   <td> <span class="uicontrol">게재능력업데이트</span> <br /> </td> 
   <td> 이 워크플로우를 사용하면 반송 메일 자격 규칙 목록과 플랫폼에 있는 도메인 및 MX 목록을 만들 수 있습니다. 이 워크플로우는 HTTPS 포트가 열려 있는 경우에만 작동합니다. 게재 기능 모듈이 설치되지 않은 경우 이러한 목록은 업데이트되지 않습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">데이터베이스 정리</span> <br /> </td> 
   <td> <span class="uicontrol">cleanup</span> <br /> </td> 
   <td> <p>이 워크플로우는 데이터베이스 유지 관리 워크플로우입니다. 통계 및 프로세스에서 다른 계산을 수행하고 배포 도우미에 정의된 구성에 따라 데이터베이스에서 오래된 데이터를 삭제합니다. 기본적으로 매일 오전 4시에 트리거됩니다.</p> <p>자세한 내용은 다음을 참조하십시오. <a href="../../production/using/database-cleanup-workflow.md">페이지</a>.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">일시 중지된 워크플로우 정리</span> <br /> </td> 
   <td> <span class="uicontrol">cleanupPausedWorkflows</span> <br /> </td> 
   <td> <p>이 워크플로우는 심각도가 정상으로 설정된 일시 중지된 워크플로우를 분석하고, 너무 오랫동안 일시 중지된 경우 경고 및 알림을 트리거합니다. 한 달 후 일시 중지된 기술 워크플로우는 무조건 중지됩니다. 기본적으로 매주 월요일 오전 5시에 트리거됩니다.</p> <p>자세한 내용은 다음을 참조하십시오. <a href="monitoring-workflow-execution.md#handling-of-paused-workflows" target="_blank">일시 중지된 워크플로우 처리</a>.</p></td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">오퍼 알림</span> <br /> </td> 
   <td> <span class="uicontrol">offerManager</span> <br /> </td> 
   <td> 이 워크플로는 승인된 오퍼를 오퍼 카탈로그에 포함된 모든 범주와 온라인 환경에 배포합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">예측</span> <br /> </td> 
   <td> <span class="uicontrol">forecasting</span> <br /> </td> 
   <td> 이 워크플로우는 임시 캘린더에 저장된 게재를 분석합니다(임시 로그 생성). 기본적으로 매일 오전 1시에 트리거됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">추적</span> <br /> </td> 
   <td> <span class="uicontrol">추적</span> <br /> </td> 
   <td> 이 워크플로우는 추적 정보의 복구 및 통합을 수행합니다. 또한 특히 메시지 센터 아카이빙 워크플로우에서 사용하는 추적 및 게재 통계를 다시 계산할 수 있습니다. 기본적으로 시간당 한 번 트리거됩니다. <br /> </td> 
  </tr> 
 </tbody> 
</table>

