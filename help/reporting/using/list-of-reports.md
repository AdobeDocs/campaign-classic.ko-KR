---
product: campaign
title: 보고서 목록
description: 보고서 목록
audience: reporting
content-type: reference
topic-tags: accessing-built-in-reports
exl-id: c01f4850-ab17-44ac-a5e0-ff082ec206b3
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1007'
ht-degree: 1%

---

# 보고서 목록{#list-of-reports}

## 게재 보고서 {#reports-on-deliveries}

Adobe Campaign에서 제공하는 기본 제공 보고서는 아래 표에 나와 있습니다.

이러한 보고서의 내용에 대한 자세한 내용은 [이 섹션](../../reporting/using/delivery-reports.md)을 참조하십시오.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블 및 내부 이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
   <td> <strong>스키마</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 사용자 활동(recipientActivity)<br /> </td> 
   <td> 기간별 열기, 클릭 및 트랜잭션 분류<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 게재 처리량(처리량)<br /> </td> 
   <td> 게재 처리량 차트, 메시지/시간 및 Mbit/s.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 실패 및 반송(오류)<br /> </td> 
   <td> 원인 및 도메인에 의한 바운스 수 및 게재 불가.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 추적 표시기(deliveryFeedback)<br /> </td> 
   <td> 받는 사람 동작 추적을 위한 주요 지표의 요약입니다.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 추적 표시기(mobileAppDeliveryFeedback)<br /> </td> 
   <td> 모바일 애플리케이션에 게재 표시기를 추적합니다.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 브라우저(browserStatistics)<br /> </td> 
   <td> 메시지를 클릭한 수신자가 사용하는 브라우저에 대한 통계입니다.<br /> </td> 
   <td> xtk:none<br /> </td> 
  </tr> 
  <tr> 
   <td> 소셜 네트워크에 공유(deliveryForward)<br /> </td> 
   <td> 활동 및 메일 열기 통계를 공유하는 중입니다.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 핫 클릭(호출)<br /> </td> 
   <td> 메시지와 겹쳐진 클릭률을 표시합니다.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 가설 보고서(delivery가설)<br /> </td> 
   <td> 게재 가식에 대한 측정값 요약을 표시합니다.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 게재 통계(statisticsPerDelivery)<br /> </td> 
   <td> 이메일 도메인별 통계(처리된 메시지, 게재된 메시지, 하드 바운스, 소프트 바운스, 클릭, 구독 취소)입니다.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 활동 통계 공유(forwardActivities)<br /> </td> 
   <td> 기간당 활동, 열기 및 구독 공유 분석<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 추적 통계(trackingStatistics)<br /> </td> 
   <td> 및 트랜잭션 비율 보고서를 엽니다.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 게재 요약(deliverySending)<br /> </td> 
   <td> 게재 지표 요약:대상, 제외 및 메시지를 보냈습니다.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 게재 요약(deliveryStatistics)<br /> </td> 
   <td> 선택한 게재에 대한 요약 테이블:Target, 제외 및 메시지를 보냈습니다.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 운영 체제(osStatistics)<br /> </td> 
   <td> 메시지를 클릭한 수신자가 사용하는 운영 체제에 대한 통계입니다.<br /> </td> 
   <td> xtk:none<br /> </td> 
  </tr> 
  <tr> 
   <td> 반응성 비율(deliveryFeedbackSocial)<br /> </td> 
   <td> 배달 반응률 및 반응 분류입니다.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> URL 및 클릭 처리량(topUrlDelivery)<br /> </td> 
   <td> 대부분의 활성 URL 및 연결된 클릭 스트림입니다.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 캠페인 보고서 {#reports-on-campaigns}

캠페인에 대한 보고서는 **nms:operation** 테이블의 데이터를 다룹니다.

Adobe Campaign에서 제공하는 기본 제공 보고서는 아래 표에 나와 있습니다.

이러한 보고서의 내용에 대한 자세한 내용은 [이 섹션](../../campaign/using/designing-marketing-campaigns.md)을 참조하십시오.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블 및 내부 이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 사용자 활동(operationRecipientActivity)<br /> </td> 
   <td> 기간별 열기, 클릭 및 트랜잭션 분류는 Campaign에 따라 다릅니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 게재 처리량(operationThroughput)<br /> </td> 
   <td> 게재 처리량 차트(메일/시간 및 Mbits/s)는 Campaign에 따라 다릅니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 캠페인 비용(budgetOperationExpenses)<br /> </td> 
   <td> 캠페인 라인 항목을 자세히 표시합니다. 이 항목은 캠페인에 따라 다릅니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 실패 및 반송(operationErrors)<br /> </td> 
   <td> 원인 및 도메인별 바운스 수 및 게재 불가 기능은 Campaign에 따라 다릅니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 비용 라인 탐색(budgetExplorerOperation)<br /> </td> 
   <td> 원가 라인의 설명 분석(MRM<br />에 따라 다름) </td> 
  </tr> 
  <tr> 
   <td> 추적 표시기(operationFeedback)<br /> </td> 
   <td> 주요 추적 지표 개요:열기, 클릭 수 및 거래는 Campaign에 따라 다릅니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 소셜 네트워크에 공유(operationForward)<br /> </td> 
   <td> 활동 및 메일 열기 통계를 공유하는 것은 Campaign에 따라 다릅니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 가설 보고서(operation가설)<br /> </td> 
   <td> Campaign에 따라 캠페인 게재에 대한 가설 측정 요약을 표시합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 활동 통계 공유(forwardActivityOpt)<br /> </td> 
   <td> 기간당 활동, 열기 및 구독 공유에 대한 분석은 Campaign에 따라 다릅니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 배달 요약(operationStatistics)<br /> </td> 
   <td> 캠페인 게재의 요약 차트:Target, 제외 및 메시지를 보냈습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> URL 및 클릭 처리량(operationTopUrlDelivery)<br /> </td> 
   <td> 대부분의 활성 URL 및 연결된 클릭 스트림은 Campaign에 따라 다릅니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 서비스 보고서 {#reports-on-services}

서비스에 대한 보고서는 **nms:service** 테이블의 데이터와 관련이 있습니다.

Adobe Campaign에서 제공하는 기본 제공 보고서는 아래 표에 나와 있습니다.

이러한 보고서의 내용에 대한 자세한 내용은 관련 안내서를 참조하십시오.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블 및 내부 이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 팬 인수(socialAcquisitionByWebapp)<br /> </td> 
   <td> 잠재 고객 인수를 가능하게 한 웹 애플리케이션은 무엇입니까? 소셜 마케팅 추가 기능에 따라 다릅니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 구독 분류(mobileAppDistribution)<br /> </td> 
   <td> 모바일 애플리케이션별 활성 구독의 분류입니다. 은 모바일 앱 채널 추가 기능에 따라 다릅니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 구독 추적(subscriptionsProgress)<br /> </td> 
   <td> 정보 서비스에 대한 구독의 발전<br /> </td> 
  </tr> 
  <tr> 
   <td> 반응성 비율(socialReactionRate)<br /> </td> 
   <td> 최신 게재의 반응성 비율은 얼마입니까? 소셜 마케팅 추가 기능에 따라 다릅니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 반응성 비율(mobileAppReactivityRate)<br /> </td> 
   <td> 최신 게재에 대한 반응성 비율은 모바일 앱 채널 추가 기능에 따라 다릅니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 예산 보고서 {#budget-reports}

Adobe Campaign에서 제공하는 기본 제공 보고서는 아래 표에 나와 있습니다.

이러한 보고서의 내용에 대한 자세한 내용은 [이 섹션](../../campaign/using/designing-marketing-campaigns.md)을 참조하십시오.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블 및 내부 이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
   <td> <strong>스키마</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 프로그램에 연결된 비용(budgetProgramCost)<br /> </td> 
   <td> 프로그램 비용 분류<br /> </td> 
   <td> nms:program<br /> </td> 
  </tr> 
  <tr> 
   <td> 예산 진화(budgetEvolution)<br /> </td> 
   <td> 약정 레벨별 예산 비용 진화<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> 예산의 누적 진화(budgetCumulativeEvolution)<br /> </td> 
   <td> 누적 예산 비용의 진화는 쉼표<br /> 개각 수준별로 분류됩니다. </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> 비용 라인 탐색(budgetExplorerBudget)<br /> </td> 
   <td> 원가 라인의 설명 분석.<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> 비용 라인 탐색(budgetExplorer)<br /> </td> 
   <td> 원가 라인의 설명 분석.<br /> </td> 
   <td> nms:costLine<br /> </td> 
  </tr> 
  <tr> 
   <td> 비용 라인 탐색(budgetExplorerPlan)<br /> </td> 
   <td> 원가 라인의 설명 분석.<br /> </td> 
   <td> nms:plan<br /> </td> 
  </tr> 
  <tr> 
   <td> 비용 라인 탐색(budgetExplorerProgram)<br /> </td> 
   <td> 원가 라인의 설명 분석.<br /> </td> 
   <td> nms:program<br /> </td> 
  </tr> 
  <tr> 
   <td> 예산 요약(예산)<br /> </td> 
   <td> 기본 비용, 비용 범주 및 예산에 대한 스냅샷입니다.<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 시뮬레이션 보고서 {#reports-on-simulations}

시뮬레이션에 대한 보고서는 **nms:simulation** 테이블의 데이터를 참조합니다.

Adobe Campaign에서 제공하는 기본 제공 보고서는 아래 표에 나와 있습니다.

이러한 보고서의 내용에 대한 자세한 내용은 관련 안내서를 참조하십시오.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블 및 내부 이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 시뮬레이션 제외 세부 정보(dlvSimuLossDetail)<br /> </td> 
   <td> 제외의 모든 원인에 대한 자세한 표입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 순위(offerSimulationRanking)별 오퍼 분류<br /> </td> 
   <td> 등급별로 시뮬레이션에서 오퍼의 분류.<br /> </td> 
  </tr> 
  <tr> 
   <td> 시뮬레이션 요약(dlvSimuLossSummary)<br /> </td> 
   <td> 시뮬레이션 볼륨 및 제외 요약<br /> </td> 
  </tr> 
  <tr> 
   <td> 겹치기 통계(dlvSimuOverlapping)<br /> </td> 
   <td> 배달 대상이 겹치는 볼륨입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 시뮬레이션으로 인한 제외 요약(dlvSimuLossSimu)<br /> </td> 
   <td> 시뮬레이션으로 인한 제외 테이블입니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 웹 응용 프로그램 보고서 {#reports-on-web-applications}

웹 응용 프로그램에 대한 보고서는 **nms:WebApp** 테이블의 데이터를 참조합니다.

Adobe Campaign에서 제공하는 기본 제공 보고서는 아래 표에 나와 있습니다.

이러한 보고서의 내용에 대한 자세한 내용은 [이 섹션](../../web/using/about-web-applications.md)을 참조하십시오.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블 및 내부 이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 설명서(surveyDictionary)<br /> </td> 
   <td> 설문 조사 구조에 대한 설명은 설문 조사 관리자 추가 기능에 따라 다릅니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 기본(surveyProperties)<br /> </td> 
   <td> 설문 조사 속성<br /> </td> 
  </tr> 
  <tr> 
   <td> 응답 분류(surveyDistribution)<br /> </td> 
   <td> 질문에 대한 응답 분류<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 기타 ootb 보고서 {#other-ootb-reports}

다음 보고서가 기본 제공됩니다. 자세한 내용은 관련 기능에 대한 문서를 참조하십시오.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블 및 내부 이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
   <td> <strong>스키마</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 오퍼 분석(offerAnalysis)<br /> </td> 
   <td> 날짜 및 채널별 오퍼 분석, 상호 작용 추가 기능에 따라 달라집니다.<br /> </td> 
   <td> nms:offer<br /> </td> 
  </tr> 
  <tr> 
   <td> 리마케팅 효율성(remarketingEffect)<br /> </td> 
   <td> 리마케팅 효율성 측정<br /> </td> 
   <td> nms:webEvent<br /> </td> 
  </tr> 
  <tr> 
   <td> 소셜 잠재 고객 획득 내역(socialVisitorStatistics)<br /> </td> 
   <td> twitter 및 Facebook 잠재 고객 취득의 역사는 Social Marketing 추가 기능에 따라 다릅니다.<br /> </td> 
   <td> nms:visitor<br /> </td> 
  </tr> 
  <tr> 
   <td> 최근 제안 추적(recentProposition)<br /> </td> 
   <td> 실시간 제안 추적<br /> </td> 
   <td> nms:provisionRcp<br /> </td> 
  </tr> 
 </tbody> 
</table>
