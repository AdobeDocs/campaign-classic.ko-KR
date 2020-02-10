---
title: 배달
seo-title: 배달
description: 배달
seo-description: null
page-status-flag: never-activated
uuid: d323eb4d-937b-4b37-8400-942336f0a1b4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: 37612f62-68c0-4f73-a9a1-6d017aab862f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cfb1b02a6261c001392b5cc6430f00206e802bb8

---


# 배달{#deliveries}

아래에 자세히 설명된 워크플로우는 기본적으로 설치됩니다.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블</strong><br /> </td> 
   <td> <strong>내부 이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">보고 집계</span><br /> </td> 
   <td> <span class="uicontrol">reportingAggregate</span><br /> </td> 
   <td> 이 워크플로우 업데이트는 보고서에 사용된 합계를 계산합니다. 기본적으로 매일 오전 2시에 트리거됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">청구</span><br /> </td> 
   <td> <span class="uicontrol">청구</span><br /> </td> 
   <td> 이 워크플로우는 시스템 활동 보고서를 이메일로 '과금' 운영자에게 보냅니다. 기본적으로 매월 25일에 트리거됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">활성 청구 프로파일</span> 수 <br /> </td> 
   <td> <span class="uicontrol">billingActiveContactCount</span><br /> </td> 
   <td> <p>이 워크플로우는 활성 프로필 수를 계산합니다. 매일 밤 1시에 트리거됩니다.</p> <p>"<strong>프로필</strong>"은 정보(예:최종 고객, 잠재 고객 또는 리드를 나타내는 nmsRecipient 테이블 또는 특정 채널과 관련된 쿠키 ID, 고객 ID, 모바일 식별자 또는 기타 정보가 포함된 외부 테이블의 레코드입니다. 청구 시 "활성" 상태인 프로필만 고려됩니다. 지난 12개월 이내에 모든 채널을 통해 프로파일을 타깃팅하거나 커뮤니케이션한 경우 프로파일은 "활성"으로 간주됩니다.</p> <p>Facebook 및 Twitter 채널은 고려되지 않습니다.</p> <p>[관리] &gt; [캠페인 관리 <span class="uicontrol">] &gt; [</span> 고객 지표 <span class="uicontrol">] 메뉴에서 활성 프로필</span> 수에 <span class="uicontrol">대한</span> 개요를 <span class="uicontrol">확인할 수</span> 있습니다.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">별칭 정리</span><br /> </td> 
   <td> <span class="uicontrol">aliasCleaning</span><br /> </td> 
   <td> 이 워크플로우는 열거형 값을 표준화합니다. 기본적으로 매일 오전 3시에 트리거됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">전달</span> 업데이트 <br /> </td> 
   <td> <span class="uicontrol">deliverabilityUpdate</span><br /> </td> 
   <td> 이 워크플로에서는 바운스 메일 자격 규칙 목록과 플랫폼의 도메인 및 MX 목록을 만들 수 있습니다. 이 워크플로우는 HTTPS 포트가 열려 있는 경우에만 작동합니다. 이 목록은 제공 가능성 모듈이 설치되어 있지 않으면 업데이트되지 않습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">데이터베이스 정리</span><br /> </td> 
   <td> <span class="uicontrol">정리</span><br /> </td> 
   <td> <p>이 워크플로우는 데이터베이스 유지 관리 워크플로우입니다.통계 및 프로세스와 다른 계산을 수행하고 배포 길잡이의 정의된 구성에 따라 데이터베이스에서 오래된 데이터를 삭제합니다. 기본적으로 매일 오전 4시에 트리거됩니다.</p> <p>자세한 내용은 이 <a href="../../production/using/database-cleanup-workflow.md">페이지를</a>참조하십시오.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">일시 중지된 워크플로우 정리</span><br /> </td> 
   <td> <span class="uicontrol">cleanupPausedWorkflows</span><br /> </td> 
   <td> <p>이 워크플로우는 심각도가 정상으로 설정된 일시 중지된 워크플로우를 분석하고 너무 오랫동안 일시 중지되면 경고 및 알림을 트리거합니다. 한 달 후 일시 중지된 기술 워크플로우는 무조건 중지됩니다. 기본적으로 매주 월요일 오전 5시에 트리거됩니다.</p> <p>자세한 내용은 일시 중지된 <a href="../../workflow/using/monitoring-workflow-execution.md#handling-of-paused-workflows" target="_blank">워크플로우</a>처리를 참조하십시오.</p></td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">오퍼 알림</span><br /> </td> 
   <td> <span class="uicontrol">offerMgt</span><br /> </td> 
   <td> 이 워크플로우는 승인된 오퍼를 오퍼 카탈로그에 포함된 모든 카테고리뿐만 아니라 온라인 환경에 배포합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">미리 보기</span><br /> </td> 
   <td> <span class="uicontrol">예측</span><br /> </td> 
   <td> 이 워크플로우는 임시 달력에 저장된 전달을 분석합니다(임시 로그 생성). 기본적으로 매일 오전 1시에 트리거됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">추적</span><br /> </td> 
   <td> <span class="uicontrol">추적</span><br /> </td> 
   <td> 이 워크플로우는 추적 정보의 복구 및 통합을 수행합니다. 또한 추적 및 배달 통계, 특히 메시지 센터 아카이빙 워크플로우에서 사용되는 통계 수를 다시 계산할 수 있습니다. 기본적으로 시간당 한 번씩 트리거됩니다. <br /> </td> 
  </tr> 
 </tbody> 
</table>

