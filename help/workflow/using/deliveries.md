---
product: campaign
title: 게재
description: 기본 게재 워크플로우에 대해 자세히 알아봅니다
audience: workflow
content-type: reference
topic-tags: technical-workflows
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 6%

---


# 게재{#deliveries}

![](../../assets/common.svg)

아래 자세히 설명된 워크플로우는 기본적으로 **게재** 모듈과 함께 설치됩니다.

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
   <td> 이 워크플로우 업데이트는 보고서에 사용되는 합계를 업데이트합니다. 기본적으로 매일 오전 2시에 트리거됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">과금</span> <br /> </td> 
   <td> <span class="uicontrol">billing</span> <br /> </td> 
   <td> 이 워크플로우는 '청구' 운영자에게 전자 메일로 시스템 활동 보고서를 보냅니다. 기본적으로 매월 25일에 트리거됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">청구(활성 프로필)</span> <br /> </td> 
   <td> <span class="uicontrol">billingActiveContactCount</span> <br /> </td> 
   <td> <p>이 워크플로우는 활성 프로필 수를 계산합니다. 기본적으로 매일 밤 1시에 트리거됩니다.</p> <p>"<strong>프로필</strong>"은 정보의 레코드를 의미합니다(예: 최종 고객, 잠재 고객 또는 리드를 나타내는 쿠키 ID, 고객 ID, 모바일 식별자 또는 특정 채널과 관련된 기타 정보가 포함된 외부 테이블 또는 nmsRecipient 테이블의 레코드. 청구에는 "활성" 상태인 프로필만 포함됩니다. 지난 12개월 내에 모든 채널을 통해 프로필을 타겟팅하거나 통신한 경우 프로필이 "활성"으로 간주됩니다.</p> <p>페이스북과 트위터 채널은 고려되지 않습니다.</p> <p><span class="uicontrol">관리</span> &gt; <span class="uicontrol">캠페인 관리</span> &gt; <span class="uicontrol">고객 지표</span> 메뉴에서 <span class="uicontrol">활성 프로필 수</span>에 대한 개요를 알 수 있습니다.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">별칭 정리</span> <br /> </td> 
   <td> <span class="uicontrol">aliasCleaning</span> <br /> </td> 
   <td> 이 워크플로우는 열거형 값을 표준화합니다. 기본적으로 매일 오전 3시에 트리거됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">게재 능력을 위한 업데이트</span> <br /> </td> 
   <td> <span class="uicontrol">게재능력업데이트</span> <br /> </td> 
   <td> 이 워크플로우를 통해 반송 메일 자격 규칙 목록과 플랫폼에 있는 도메인 및 MX 목록을 만들 수 있습니다. 이 워크플로우는 HTTPS 포트가 열려 있는 경우에만 작동합니다. 이 목록은 게재 가능성 모듈이 설치되어 있지 않으면 업데이트되지 않습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">데이터베이스 정리</span> <br /> </td> 
   <td> <span class="uicontrol">cleanup</span> <br /> </td> 
   <td> <p>이 워크플로우는 데이터베이스 유지 관리 워크플로우입니다. 통계 및 프로세스와 다른 계산을 수행하고 배포 도우미에서 정의된 구성에 따라 데이터베이스에서 오래된 데이터를 삭제합니다. 기본적으로 매일 오전 4시에 트리거됩니다.</p> <p>자세한 내용은 이 <a href="../../production/using/database-cleanup-workflow.md">page</a>을 참조하십시오.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">일시 중지된 워크플로우 정리</span> <br /> </td> 
   <td> <span class="uicontrol">cleanupPausedWorkflows</span> <br /> </td> 
   <td> <p>이 워크플로우는 심각도가 정상으로 설정된 일시 중지된 워크플로우를 분석하고 너무 오랫동안 일시 중지되면 경고 및 알림을 트리거합니다. 한 달 후 일시 중지된 기술 워크플로우는 무조건 중지됩니다. 기본적으로 매주 월요일 오전 5시에 트리거됩니다.</p> <p>자세한 내용은 <a href="monitoring-workflow-execution.md#handling-of-paused-workflows" target="_blank">일시 중지된 워크플로우 처리</a>를 참조하십시오.</p></td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">오퍼 알림</span> <br /> </td> 
   <td> <span class="uicontrol">offerMgt</span> <br /> </td> 
   <td> 이 워크플로우는 오퍼 카탈로그에 포함된 모든 카테고리와 온라인 환경에 승인된 오퍼를 배포합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">예측</span> <br /> </td> 
   <td> <span class="uicontrol">forecasting</span> <br /> </td> 
   <td> 이 워크플로우는 임시 달력에 저장된 게재를 분석합니다(임시 로그 만들기). 기본적으로 매일 오전 1시에 트리거됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">추적</span> <br /> </td> 
   <td> <span class="uicontrol">추적</span> <br /> </td> 
   <td> 이 워크플로우에서는 추적 정보의 복구 및 통합을 수행합니다. 또한 추적 및 게재 통계, 특히 Message Center 아카이빙 워크플로우에서 사용되는 통계 수를 재계산할 수 있습니다. 기본적으로 시간당 한 번 트리거됩니다. <br /> </td> 
  </tr> 
 </tbody> 
</table>

