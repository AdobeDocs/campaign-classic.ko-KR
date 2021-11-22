---
product: campaign
title: 지표 계산
description: 지표 계산
audience: reporting
content-type: reference
topic-tags: accessing-built-in-reports
exl-id: 52ca1595-16b3-4323-9122-d1ac13c08147
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '2972'
ht-degree: 2%

---

# 지표 계산 {#indicator-calculation}

![](../../assets/common.svg)

## 사용자 활동 {#user-activities-1}

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>지표 설명</strong> <br /> </th> 
   <th> <strong>지표 계산 공식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 오픈율<br /> </td> 
   <td> @opens<br /> </td> 
   <td> URL 기본 키가 1인 모든 @totalClicks의 합계.<br /> </td> 
   <td> sum(Iif([@url-id]=1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 클릭 수<br /> </td> 
   <td> @clicks<br /> </td> 
   <td> URL 유형을 가진 모든 @totalClicks의 합계가 "이메일 클릭"과 같습니다.<br /> </td> 
   <td> sum(Iif([url/@type]=1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 트랜잭션<br /> </td> 
   <td> @transactions<br /> </td> 
   <td> URL 유형을 가진 모든 @totalClicks의 합계가 "Transaction"과 같습니다.<br /> </td> 
   <td> sum(Iif([url/@type]=5, @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

이 보고서는 **[!UICONTROL Consolidated tracking]** 표(nms:trackingStats). 이 집계 테이블은 보고서를 표시할 때 성능상의 이유로 **[!UICONTROL Recipient tracking logs]** 테이블(nms:trackingLogRcp)이며 실시간으로 계산되지 않습니다. 추적 로그가 검색되면 몇 분 후에 테이블이 생성됩니다. 표시기가 최신 상태이면 결과는 의 표시기와 동일합니다 **지표 추적** 보고서 세트에 대해 설명합니다. 이 @totalclicks 지표는 5분 동안의 총 클릭 수를 나타냅니다.

## 게재 불가 및 이탈 {#non-deliverables-and-bounces-1}

**오류 유형별 분류**

이 보고서는 **[!UICONTROL Delivery and tracking statistics]** 표(nms:deliveryLogStats).

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>지표 설명</strong> <br /> </th> 
   <th> <strong>지표 계산 공식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 처리된 총 메시지 수<br /> </td> 
   <td> @totalProcessed<br /> </td> 
   <td> 상태가 "준비", "전송됨" 또는 "실패"인 메시지의 합계입니다.<br /> </td> 
   <td> @prepared + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> 사용자 알 수 없음<br /> </td> 
   <td> @unknownUser<br /> </td> 
   <td> 상태가 "실패"이고 "사용자 알 수 없음"인 모든 메시지의 수입니다. <br /> </td> 
   <td> Count(@status=2 및 msg/@failureReason=1)<br /> </td> 
  </tr> 
  <tr> 
   <td> 연결할 수 없음 <br /> </td> 
   <td> @unreachable<br /> </td> 
   <td> 상태가 "실패"이고 "도달할 수 없음"인 모든 메시지의 수입니다. <br /> </td> 
   <td> Count(@status=2 및 msg/@failureReason=3)<br /> </td> 
  </tr> 
  <tr> 
   <td> 거부됨<br /> </td> 
   <td> @refused<br /> </td> 
   <td> 상태가 "실패"이고 이유가 "거부"인 모든 메시지의 수입니다. <br /> </td> 
   <td> Count(@status=2 및 msg/@failureReason=20)<br /> </td> 
  </tr> 
  <tr> 
   <td> 잘못된 도메인<br /> </td> 
   <td> @invalidDomain<br /> </td> 
   <td> 상태가 "실패"이고 "잘못된 도메인"인 모든 메시지의 개수입니다. <br /> </td> 
   <td> Count(@status=2 및 msg/@failureReason=2)<br /> </td> 
  </tr> 
  <tr> 
   <td> 계정이 비활성화됨<br /> </td> 
   <td> @disabled<br /> </td> 
   <td> 상태가 "실패"이고 "계정이 비활성화됨"인 모든 메시지의 수입니다.<br /> </td> 
   <td> Count(@status=2 및 msg/@failureReason=4)<br /> </td> 
  </tr> 
  <tr> 
   <td> 받은 편지함 가득 참<br /> </td> 
   <td> @mailBoxFull<br /> </td> 
   <td> 상태가 "실패"이고 이유가 "받은 편지함 가득 참"인 모든 메시지의 수입니다. <br /> </td> 
   <td> Count(@status=2 및 msg/@failureReason=5)<br /> </td> 
  </tr> 
  <tr> 
   <td> 오류<br /> </td> 
   <td> @value<br /> </td> 
   <td> 이 유형의 오류에 대한 실패한 메시지 수입니다.<br /> </td> 
   <td> Count(@status=2 and msg/@failureReason="오류 유형의 값")<br /> </td> 
  </tr> 
  <tr> 
   <td> 기여도<br /> </td> 
   <td> -<br /> </td> 
   <td> 총 오류 메시지 수와 비교하여 이 유형의 오류 비율입니다.<br /> </td> 
   <td> percent(@value,@totalErrors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 분류<br /> </td> 
   <td> -<br /> </td> 
   <td> 처리된 총 메시지 수와 비교하여 이 유형의 오류 비율입니다.<br /> </td> 
   <td> percent(@value,@totalProcessed)<br /> </td> 
  </tr> 
 </tbody> 
</table>

**도메인별 분류**

보고서의 두 번째 부분에서는 오류 유형과 대조적으로 인터넷 도메인별로 실패한 메시지의 분류를 자세히 설명합니다. 에 연결된 공식 **오류** 이 경우 지표(@value)은 다음과 같습니다. Count(@status=2 및 @domain=&quot;도메인 이름의 값&quot;), 즉 이 도메인에 대한 실패 상태의 모든 메시지 수입니다.

## 브라우저 {#browsers-1}

이 보고서는 **[!UICONTROL Internet Browser Statistics]** 표(nms:userAgentsStats).

**글로벌 통계**

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>지표 설명</strong> <br /> </th> 
   <th> <strong>지표 계산 공식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 방문자 수<br /> </td> 
   <td> @totalVisitors<br /> </td> 
   <td> 게재를 한 번 이상 클릭한 이 브라우저의 총 타깃팅된 수신자 수입니다.<br /> </td> 
   <td> Sum(@visitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 페이지 보기 수<br /> </td> 
   <td> @totalPages<br /> </td> 
   <td> 모든 게재에 대해 이 브라우저를 사용하는 게재 링크에 대한 총 클릭 수입니다.<br /> </td> 
   <td> Sum(@pages) <br /> </td> 
  </tr> 
  <tr> 
   <td> 사용 비율<br /> </td> 
   <td> -<br /> </td> 
   <td> 이 브라우저의 방문자 수와 총 방문자 수의 백분율입니다.<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors) <br /> </td> 
  </tr> 
 </tbody> 
</table>

**브라우저당 통계**

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>지표 설명</strong> <br /> </th> 
   <th> <strong>지표 계산 공식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 사용 비율<br /> </td> 
   <td> @visitors<br /> </td> 
   <td> 이 브라우저를 사용하는 일별 방문자 수의 백분율로, 가장 많은 방문 횟수가 있는 날에 측정된 방문자 수와 비교한 것입니다.<br /> </td> 
   <td> percent(sum(@visitors),max(@visitorsOfTheDay)<br /> </td> 
  </tr> 
  <tr> 
   <td> 글로벌 비율<br /> </td> 
   <td> -<br /> </td> 
   <td> 이 버전의 방문자의 백분율로, 모든 브라우저를 사용하는 총 방문자 수와 비교한 것입니다.<br /> </td> 
   <td> percent(@totalVisitors, @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 상대적 가중치<br /> </td> 
   <td> -<br /> </td> 
   <td> 이 버전을 사용하는 총 방문자 수와 비교한 방문자의 백분율입니다.<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors) <br /> </td> 
  </tr> 
 </tbody> 
</table>

## 소셜 네트워크에 공유 {#sharing-to-social-networks-1}

이 보고서는 **[!UICONTROL Delivery]** (nms:delivery), **[!UICONTROL Consolidated tracking]** (nms:trackingStats) 및 **[!UICONTROL Web tracking]** (nms:webTrackingLog) 표를 참조하십시오.

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>지표 설명</strong> <br /> </th> 
   <th> <strong>지표 계산 공식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 게재할 메시지 수<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> 게재 분석 중에 처리된 총 메시지 수입니다.<br /> </td> 
   <td> sum([properties/@totalTarget])<br /> </td> 
  </tr> 
  <tr> 
   <td> 성공한 게재 수<br /> </td> 
   <td> @success<br /> </td> 
   <td> 성공적으로 처리된 메시지 수 <br /> </td> 
   <td> sum([indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 이메일<br /> </td> 
   <td> @email<br /> </td> 
   <td> URL 카테고리가 "이메일"과 같은 모든 @totalClicks의 합계입니다.<br /> </td> 
   <td> Sum(iIf([url/@category]='email',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> URL 카테고리가 "facebook"과 같은 모든 @totalClicks의 합계입니다.<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> URL 카테고리가 "twitter"과 같은 모든 @totalClicks의 합계입니다.<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 맛있는<br /> </td> 
   <td> @delicious<br /> </td> 
   <td> URL 카테고리가 "맛있는"인 모든 @totalClicks의 합계입니다.<br /> </td> 
   <td> Sum(iIf([url/@category]='delicious',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> URL 카테고리가 "digg"와 같은 모든 @totalClicks의 합계입니다.<br /> </td> 
   <td> Sum(iIf([url/@category]='digg',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> URL 카테고리가 "google"과 같은 모든 @totalClicks의 합계입니다.<br /> </td> 
   <td> Sum(iIf([url/@category]='google',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Linkedin<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> URL 카테고리가 "linkedin"과 같은 모든 @totalClicks의 합계입니다.<br /> </td> 
   <td> Sum(iIf([url/@category]='linkedin',@totalClicks,0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

**주식**

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>지표 설명</strong> <br /> </th> 
   <th> <strong>지표 계산 공식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 공유 수<br /> </td> 
   <td> @forward<br /> </td> 
   <td> 이 소셜 네트워크에서 공유된 총 메시지 수입니다.<br /> </td> 
   <td> Sum(iIf([url/@category]="소셜 네트워크 유형의 값",@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 분류<br /> </td> 
   <td> @percent<br /> </td> 
   <td> 이 소셜 네트워크의 주식 수 중 총 주식 수와 비교하여 백분율입니다.<br /> </td> 
   <td> percent(@forward, sum(@forward)<br /> </td> 
  </tr> 
  <tr> 
   <td> 공유율<br /> </td> 
   <td> @rate<br /> </td> 
   <td> 이 네트워크의 공유 수와 전달할 메시지 수를 비교한 것입니다.<br /> </td> 
   <td> @forward / @totalTarget<br /> </td> 
  </tr> 
 </tbody> 
</table>

**열어 본 기록**

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>지표 설명</strong> <br /> </th> 
   <th> <strong>지표 계산 공식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 열기 횟수 <br /> </td> 
   <td> @open<br /> </td> 
   <td> 웹 추적 테이블에 있는 총 추적 라인 수입니다.<br /> </td> 
   <td> 카운트<br /> </td> 
  </tr> 
  <tr> 
   <td> 분류<br /> </td> 
   <td> @percentOpen<br /> </td> 
   <td> 이 소셜 네트워크에서 열린 개수와 총 열기 개수의 비율입니다.<br /> </td> 
   <td> percent(@open, sum(@open)<br /> </td> 
  </tr> 
  <tr> 
   <td> 열기 비율<br /> </td> 
   <td> @rateOpen<br /> </td> 
   <td> 이 소셜 네트워크에서 열 개수와 전달할 총 메시지 수를 비교한 것입니다.<br /> </td> 
   <td> @open / @totalTarget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 활동 공유에 대한 통계 {#statistics-on-sharing-activities-1}

이 보고서는 **[!UICONTROL Delivery]** (nms:delivery), **[!UICONTROL Consolidated tracking]** (nms:trackingStats) 및 **[!UICONTROL Web tracking]** (nms:webTrackingLog) 표를 참조하십시오.

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>지표 설명</strong> <br /> </th> 
   <th> <strong>지표 계산 공식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 새 연락처<br /> </td> 
   <td> @newContacts<br /> </td> 
   <td> 수신자에 연결된 방문자 수<br /> </td> 
   <td> 공식: count(@id)<br /> 필터: @recipient-id!= 0<br /> </td> 
  </tr> 
  <tr> 
   <td> 오픈율<br /> </td> 
   <td> @opened<br /> </td> 
   <td> URL 유형이 "@ids"과 같은 모든 개수의 수입니다.<br /> </td> 
   <td> count (Iif([url/@type] = 2, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 주식<br /> </td> 
   <td> @shared<br /> </td> 
   <td> 'email' , 'facebook' , 'twitter' , '맛있는' , 'digg' , 'google' , 'linkedin'에 포함된 URL 카테고리<br /> "이메일", "facebook", "twitter", "맛있는", "digg", "google" 또는 "linkedin"과 같은 URL 카테고리가 있는 모든 @totalClicks의 개수입니다.<br /> </td> 
   <td> count (Iif([url/@category] IN (전자 메일' , 'facebook' , 'twitter' , '맛있는' , 'digg' , 'google' , 'linkedin'), @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 운영 체제 {#operating-systems-1}

이 보고서는 **[!UICONTROL Internet Browser Statistics]** 표(nms:userAgentsStats).

**글로벌 통계**

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>지표 설명</strong> <br /> </th> 
   <th> <strong>지표 계산 공식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 방문자 수<br /> </td> 
   <td> @totalVisitors / @days<br /> </td> 
   <td> 게재를 한 번 이상 클릭한 운영 체제에서 타겟팅한 총 수신자 수의 일별 평균입니다.<br /> </td> 
   <td> Sum(@visitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 본 페이지<br /> </td> 
   <td> @totalPages / @days<br /> </td> 
   <td> 모든 게재에 대한 운영 체제당 게재 링크에 대한 총 클릭 수의 일별 평균 입니다.<br /> </td> 
   <td> Sum(@pages)<br /> </td> 
  </tr> 
  <tr> 
   <td> 사용 비율<br /> </td> 
   <td> -<br /> </td> 
   <td> 총 방문자 수와 비교하여 운영 체제당 방문자 수 분류<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors)<br /> </td> 
  </tr> 
 </tbody> 
</table>

**운영 체제별 통계**

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>지표 설명</strong> <br /> </th> 
   <th> <strong>지표 계산 공식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 사용 비율<br /> </td> 
   <td> @visitors<br /> </td> 
   <td> 이 운영 체제에서 일별 방문자 수의 백분율로, 가장 많은 방문 횟수가 있는 날에 측정된 방문자 수와 비교됩니다.<br /> </td> 
   <td> percent(sum(@visitors), max(@visitorsOfTheDay)<br /> </td> 
  </tr> 
  <tr> 
   <td> 글로벌 비율<br /> </td> 
   <td> -<br /> </td> 
   <td> 모든 운영 체제에 있는 방문자의 총 수와 비교한 버전당 방문자의 백분율입니다.<br /> </td> 
   <td> percent(@totalVisitors, @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 상대적 비율<br /> </td> 
   <td> -<br /> </td> 
   <td> 이 운영 체제를 사용하는 총 방문자 수와 비교한 버전당 방문자 수의 백분율입니다.<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 구독 추적 {#subscription-tracking-1}

이 보고서는 **[!UICONTROL Services]** 표(nms:service).

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>지표 설명</strong> <br /> </th> 
   <th> <strong>지표 계산 공식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 등록<br /> </td> 
   <td> @_subscriber<br /> </td> 
   <td> 이전 날짜의 등록된 사람 수입니다.<br /> </td> 
   <td> sum(@created &lt; addDays(getDate(), (-1), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 구독<br /> </td> 
   <td> @_subscription<br /> </td> 
   <td> 이전 날짜의 구독 수(@action = 1).<br /> </td> 
   <td> sum(iif(@action = 1 및 @date &gt; addDays(getDate(), (-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 구독 취소<br /> </td> 
   <td> @_unsubscription<br /> </td> 
   <td> 이전 날짜의 구독 취소 수(작업 = 0).<br /> </td> 
   <td> sum(iif(@action = 0 및 @date &gt; addDays(getDate(), (-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 진화<br /> </td> 
   <td> -<br /> </td> 
   <td> 구독 수에서 구독 수를 뺀 것입니다. 이 비율은 총 가입자 수와 관련해서 계산됩니다.<br /> </td> 
   <td> Iif(@_subscription) &gt; number(@_unsubscription), '+', ")+format(@_subscription - @_unsubscription, 'number', '###0')+ Iif(@_subscriber&gt;0,'(' + format(100*percent(@_subscription, @_subscriber), 'number', '#,##0.00')+ '%)')<br /> </td> 
  </tr> 
  <tr> 
   <td> 충성도<br /> </td> 
   <td> -<br /> </td> 
   <td> 관련 기간에 대한 가입자 충성도 비율입니다.<br /> </td> 
   <td> 1%(@_unsubscription,@_subscriber+@_subscription-@_unsubscription)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 지표 추적 {#tracking-indicators-1}

이 보고서는 **[!UICONTROL Delivery and tracking statistics]** (nms:deliveryLogStats) 및 **[!UICONTROL Consolidated tracking]** (nms:trackingStats) 표를 참조하십시오.

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>지표 설명</strong> <br /> </th> 
   <th> <strong>지표 계산 공식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 게재할 메시지<br /> </td> 
   <td> @toDeliver<br /> </td> 
   <td> target 분석 후 broadLogs 수의 개수입니다.<br /> </td> 
   <td> sum([properties/@toDeliver])<br /> </td> 
  </tr> 
  <tr> 
   <td> 성공<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> "시드 주소" 필드가 "아니요"이고 상태가 "서비스 제공자에 의해 고려됨" 또는 "전송됨" 또는 "모바일에서 수신됨"인 메시지 수입니다.<br /> </td> 
   <td> sum([indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 모집단에 도달한 개별 열기<br /> </td> 
   <td> @estimatedRecipientOpen<br /> </td> 
   <td> html 형식으로 된 이메일에 대한 개별적인 열기 수를 기반으로 모든 이메일에 대해 개별적인 열기 수를 계산합니다.<br /> </td> 
   <td> Iif(([@toDeliver] - [@text]) = 0, 0, round(toDouble(@recipientOpen) * [@toDeliver] / ([@toDeliver] - [@text]), 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 도달한 모집단에서 열린 합계<br /> </td> 
   <td> @estimatedTotalRecipientOpen<br /> </td> 
   <td> html 형식의 총 이메일 열기 수를 기반으로 모든 이메일에 대한 총 열기 수를 추출합니다.<br /> </td> 
   <td> Iif(([@toDeliver] - [@text]) = 0, 0, round(toDouble(@totalRecipientOpen) * [@toDeliver] / ([@toDeliver] - [@text]), 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 구독 취소 링크에 대한 클릭 수<br /> </td> 
   <td> @optOut<br /> </td> 
   <td> URL 카테고리가 "옵트아웃"과 같은 모든 @ids의 개수입니다.<br /> </td> 
   <td> count(Iif([url/@type]=3, @id, 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> 미러 페이지에 대한 링크 클릭<br /> </td> 
   <td> @mirrorPage<br /> </td> 
   <td> URL 카테고리가 "미러 페이지"와 동일한 모든 @ids 수.<br /> </td> 
   <td> count(Iif([url/@type]=6, @id, 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> 포워드 추정<br /> </td> 
   <td> @forward<br /> </td> 
   <td> 개별 사용자 수와 이메일을 한 번 이상 클릭한 개별 수신자 수 간의 차이입니다.<br /> </td> 
   <td> @personClick - @recipientClick<br /> </td> 
  </tr> 
  <tr> 
   <td> 전송<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> "시드 주소" 필드가 "아니요"이고 상태가 "수신자에 의해 고려됨" 또는 "전송됨" 또는 "모바일에서 수신됨"과 같은 메시지 수입니다.<br /> </td> 
   <td> sum([indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 컴플레인<br /> </td> 
   <td> @complaints<br /> </td> 
   <td> 상태가 "실패"이고 "주소 설정"인 이유가 있는 메시지 차단 목록 수입니다.<br /> </td> 
   <td> Count(@status=2 및 msg/@failureReason=8)<br /> </td> 
  </tr> 
  <tr> 
   <td> 오픈율<br /> </td> 
   <td> @recipientOpen<br /> </td> 
   <td> 모든 추적 로그에 있는 모든 @broadLog-ids의 카운트입니다.<br /> </td> 
   <td> Countdistinct([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> 클릭 수<br /> </td> 
   <td> @recipientClick<br /> </td> 
   <td> URL 유형이 "이메일 클릭"과 동일한 @broadLog-ids의 고유 수입니다. <br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @broadLog-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 원시 재활동<br /> </td> 
   <td> -<br /> </td> 
   <td> 게재를 한 번 이상 클릭한 수신자 수의 백분율로, 게재를 한 번 이상 연 수신자 수와 비교됩니다.<br /> </td> 
   <td> percent(@recipientClick,@recipientOpen)<br /> </td> 
  </tr> 
  <tr> 
   <td> 모집단에서 개별적인 클릭이 도달했습니다<br /> </td> 
   <td> @personClick<br /> </td> 
   <td> URL 카테고리가 "이메일 클릭"과 동일한 모든 @source-ids.<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @source-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 누적 클릭 수<br /> </td> 
   <td> @totalRecipientClick<br /> </td> 
   <td> "이메일 클릭"과 같은 URL 카테고리가 있는 모든 @ids.<br /> </td> 
   <td> count(Iif([url/@type]=1, @id, 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> 수신자 클릭<br /> </td> 
   <td> @recipientClick<br /> </td> 
   <td> "이메일 클릭"과 같은 URL 유형을 사용하는 @broadLog-ids의 고유 수입니다.<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @broadLog-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 예상 재활동<br /> </td> 
   <td> -<br /> </td> 
   <td> 게재를 한 번 이상 클릭한 수신자 수의 비율을 게재를 한 번 이상 연 수신자 예상 수와 비교했습니다.<br /> </td> 
   <td> 퍼센트(@recipientClick, @estimatedRecipientOpen<br /> </td> 
  </tr> 
  <tr> 
   <td> 방문한 페이지<br /> </td> 
   <td> @totalWebPage<br /> </td> 
   <td> URL 유형이 "Web" 또는 "Transaction"인 모든 @ids.<br /> </td> 
   <td> count(Iif([url/@type]=4 또는 [url/@type]=5, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 트랜잭션<br /> </td> 
   <td> @transaction<br /> </td> 
   <td> URL 유형이 "트랜잭션"과 동일한 모든 @ids.<br /> </td> 
   <td> count(Iif([url/@type]=5, @id, 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> 총 금액<br /> </td> 
   <td> @amount<br /> </td> 
   <td> URL 유형이 "Transaction"인 webTrackingLog/@amounts의 합계입니다. <br /> </td> 
   <td> Sum(Iif([url/@type]=5, webTrackingLog/@amount, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 평균 트랜잭션 금액<br /> </td> 
   <td> -<br /> </td> 
   <td> 트랜잭션 수와 비교한 총 금액의 비율입니다.<br /> </td> 
   <td> div(@amount, @transaction)<br /> </td> 
  </tr> 
  <tr> 
   <td> 항목<br /> </td> 
   <td> @article<br /> </td> 
   <td> "Transaction"과 같은 URL 유형을 사용하는 webTrackingLog/@articles의 합계입니다.<br /> </td> 
   <td> Sum(Iif([url/@type]=5, webTrackingLog/@article, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 트랜잭션당 평균 품목 수<br /> </td> 
   <td> -<br /> </td> 
   <td> 트랜잭션 수와 비교하여 항목 수의 비율입니다.<br /> </td> 
   <td> div(@article, @transaction)<br /> </td> 
  </tr> 
  <tr> 
   <td> 메시지당 평균 금액<br /> </td> 
   <td> -<br /> </td> 
   <td> 게재할 메시지 수와 비교한 총 금액의 비율입니다.<br /> </td> 
   <td> div(@amount, @toDeliver)<br /> </td> 
  </tr> 
  <tr> 
   <td> 이메일<br /> </td> 
   <td> @email<br /> </td> 
   <td> "이메일"과 같은 URL 카테고리가 있는 모든 @totalClicks의 합계.<br /> </td> 
   <td> Sum(iIf([url/@category]='email',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> "facebook"과 같은 URL 카테고리가 있는 모든 @totalClicks의 합계.<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> "twitter"과 같은 URL 카테고리가 있는 모든 @totalClicks의 합계.<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 맛있는<br /> </td> 
   <td> @delicious<br /> </td> 
   <td> "맛있는"과 같은 URL 카테고리가 있는 모든 @totalClicks의 합계.<br /> </td> 
   <td> Sum(iIf([url/@category]='delicious',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> "digg"와 같은 URL 카테고리가 있는 모든 @totalClicks의 합계.<br /> </td> 
   <td> Sum(iIf([url/@category]='digg',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> "google"과 같은 URL 카테고리가 있는 모든 @totalClicks의 합계.<br /> </td> 
   <td> Sum(iIf([url/@category]='google',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Linkedin<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> "linkedin"과 같은 URL 카테고리가 있는 모든 @totalClicks의 합계.<br /> </td> 
   <td> Sum(iIf([url/@category]='linkedin',@totalClicks,0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## URL 및 클릭 스트림 {#urls-and-click-streams-1}

이 보고서는 **[!UICONTROL Delivery]** 표(nms:delivery).

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>지표 설명</strong> <br /> </th> 
   <th> <strong>지표 계산 공식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 재활동<br /> </td> 
   <td> @reactivity<br /> </td> 
   <td> 게재를 한 번 이상 클릭한 대상 수신자 수의 비율을 게재를 한 번 이상 연 예상 대상 수신자 수와 비교하여 보여줍니다.<br /> </td> 
   <td> percent([표시기/@recipientClick], [표시기/@estimatedRecipientOpen])<br /> </td> 
  </tr> 
  <tr> 
   <td> 개별적인 클릭<br /> </td> 
   <td> @distinctClicks<br /> </td> 
   <td> 게재에서 최소 한 번 이상 클릭한 개별 사용자 수의 비율입니다. 성공한 메시지 수와 비교됩니다.<br /> </td> 
   <td> percent([표시기/@personClick], [표시기/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 누적 클릭 수<br /> </td> 
   <td> @totalClicks<br /> </td> 
   <td> 성공과 함께 전달된 메시지 수와 비교하여 타겟팅된 수신자의 총 클릭 수입니다.<br /> </td> 
   <td> percent([표시기/@totalRecipientClick], [표시기/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 클릭 수<br /> </td> 
   <td> @_click<br /> </td> 
   <td> URL 기본 키가 1과 다른 모든 @totalClicks 수<br /> </td> 
   <td> count(Iif([@url-id] != 1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 클릭 수(%)<br /> </td> 
   <td> -<br /> </td> 
   <td> 누적 클릭 수와 비교한 클릭 수의 백분율입니다.<br /> </td> 
   <td> percent(@_click, @_total)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 게재 요약 {#delivery-summary-1}

이 보고서는 **[!UICONTROL Delivery]** 표(nms:delivery).

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>지표 설명</strong> <br /> </th> 
   <th> <strong>지표 계산 공식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 초기 모집단<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> 게재가 타겟팅한 총 수신자 수입니다.<br /> </td> 
   <td> sum([properties/@totalTarget])<br /> </td> 
  </tr> 
  <tr> 
   <td> 규칙에 의해 거부된 메시지<br /> </td> 
   <td> @reject<br /> </td> 
   <td> 유형화 규칙을 유지하면서 분석 중에 무시된 주소 수: 주소가 지정되지 않음, 격리, 차단 목록 등<br /> </td> 
   <td> sum([properties/@reject])<br /> </td> 
  </tr> 
  <tr> 
   <td> 게재할 메시지<br /> </td> 
   <td> @toDeliver<br /> </td> 
   <td> 게재 분석 후 게재할 총 메시지 수입니다.<br /> </td> 
   <td> sum([properties/@toDeliver])<br /> </td> 
  </tr> 
  <tr> 
   <td> 성공<br /> </td> 
   <td> @success<br /> </td> 
   <td> 성공으로 처리된 메시지 수입니다.<br /> </td> 
   <td> sum([indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 오류<br /> </td> 
   <td> @error<br /> </td> 
   <td> 게재 및 자동 반송 처리 중에 누적된 총 오류 수입니다.<br /> </td> 
   <td> sum([indicators/@error])<br /> </td> 
  </tr> 
  <tr> 
   <td> 새 격리<br /> </td> 
   <td> @newQuarantine<br /> </td> 
   <td> 게재 실패 후 격리된 주소 수(사용자 알 수 없음, 잘못된 도메인).<br /> </td> 
   <td> sum([indicators/@newQuarantine])<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 핫 클릭 {#hot-clicks-1}

이 보고서는 배달(nms:delivery)을 기반으로 합니다. **[!UICONTROL Consolidated tracking]** (nms:trackingStats) 표를 참조하십시오.

이 보고서는 각 링크에 대한 클릭 비율( HTML 및/또는 텍스트)을 포함하는 메시지 콘텐츠를 보여줍니다. 개인화 블록은 구독 취소 링크 및 미러 페이지 링크를 합한 총 클릭 수를 고려하지만 보고서에 표시되지 않습니다.

## 통계 추적 {#tracking-statistics-1}

이 보고서는 **[!UICONTROL Delivery]** 표(nms:delivery).

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>지표 설명</strong> <br /> </th> 
   <th> <strong>지표 계산 공식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 트랜잭션<br /> </td> 
   <td> @transactions<br /> </td> 
   <td> "Transaction"과 같은 URL 유형을 사용하는 모든 @totalClicks의 합계입니다.<br /> </td> 
   <td> sum(Iif([url/@type] = 5, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 클릭 수<br /> </td> 
   <td> @clicks<br /> </td> 
   <td> "이메일 클릭"과 같은 URL 유형을 사용하는 모든 @totalClicks의 합계.<br /> </td> 
   <td> sum(Iif([url/@type] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 열기<br /> </td> 
   <td> @opens<br /> </td> 
   <td> URL 기본 키가 1인 모든 @totalClicks의 합계.<br /> </td> 
   <td> sum(Iif([@url-id] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 게재 통계 {#delivery-statistics-1}

이 보고서는 **[!UICONTROL Delivery and tracking statistics]** 표(nms:deliveryLogStats).

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>지표 설명</strong> <br /> </th> 
   <th> <strong>지표 계산 공식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 처리된 이메일<br /> </td> 
   <td> @processed<br /> </td> 
   <td> 상태가 "준비", "전송됨" 또는 "실패"인 총 메시지 수입니다.<br /> </td> 
   <td> @prepared + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> 배달됨<br /> </td> 
   <td> @success<br /> </td> 
   <td> 성공적으로 처리된 메시지 수입니다.<br /> </td> 
   <td> 표시기/@success<br /> </td> 
  </tr> 
  <tr> 
   <td> 하드 바운스 수<br /> </td> 
   <td> @hardBounce<br /> </td> 
   <td> 상태가 "실패"이고 이유가 "사용자 알 수 없음"인 총 메시지 수입니다.<br /> </td> 
   <td> @unknownUser<br /> </td> 
  </tr> 
  <tr> 
   <td> 소프트 바운스<br /> </td> 
   <td> @softBounce<br /> </td> 
   <td> 상태가 "실패"이고 "연결할 수 없음", "받은 편지함 가득 참", "잘못된 도메인", "사용할 수 없는 계정", "연결되지 않음" 또는 "거부"인 이유가 있는 모든 메시지의 합계입니다.<br /> </td> 
   <td> @unreachable + @mailBoxFull + @invalidDomain + @disabled + @notConnected + @refused<br /> </td> 
  </tr> 
  <tr> 
   <td> 오픈율<br /> </td> 
   <td> @recipientOpen<br /> </td> 
   <td> 추적 로그@broadLog-ids 총 횟수입니다.<br /> </td> 
   <td> Countdistinct([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> 클릭 수<br /> </td> 
   <td> @personClick<br /> </td> 
   <td> URL 카테고리가 "이메일 클릭"과 같은 총 @source-ids 수입니다. <br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @source-id, 0)) <br /> </td> 
  </tr> 
  <tr> 
   <td> 구독 취소<br /> </td> 
   <td> @optOut<br /> </td> 
   <td> URL 카테고리가 "옵트아웃"과 같은 총 @ids 수입니다.<br /> </td> 
   <td> count(Iif([url/@type]=3, @id, 0)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 열기 분류 {#breakdown-of-opens-1}

이 보고서는 **게재** (nms:delivery) 및 **추적 로그** (nms:trackingLogRcp) 표를 참조하십시오.

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>지표 설명</strong> <br /> </th> 
   <th> <strong>지표 계산 공식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 오픈율<br /> </td> 
   <td> @totalRecipientOpen<br /> </td> 
   <td> URL 기본 키가 1인 모든 @id의 합계(열려 있음). <br /> </td> 
   <td> count(Iif([@url-id] = 1, @id, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 기타 지표 {#other-indicators}

다음 **전송** 표시기(@sent), **게재(nms:delivery) > 지표** 노드는 서비스 공급자에게 전송된 총 SMS 수에 해당합니다. 이 지표는 SMS 게재에만 사용되며 다른 유형의 게재에는 사용할 수 없습니다(와 혼동하지 않도록) **@success** 및 **@processed** 표시기).

## 표시기 동기화 {#indicator-synchronization}

특정 지표에 대한 비동기화 또는 불일치가 발생하는 경우 Adobe Campaign 탐색기에서 해당 게재를 선택하고 마우스 오른쪽 단추를 클릭한 다음 을 선택합니다 **[!UICONTROL Action>Recompute delivery and tracking indicators]**. 클릭 **[!UICONTROL Next]**&#x200B;를 클릭한 다음 **[!UICONTROL Finish]**.

![](assets/s_ncs_user_recalculate_indicators.png)

## 추적 열기 {#tracking-opens-}

Adobe Campaign에서 메시지를 검색하려면 수신자가 이메일의 이미지를 다운로드해야 합니다. HTML 및 다중 부분/대체 이메일에는 열려 있는 메시지를 감지할 수 있는 0픽셀 이미지가 포함됩니다. 텍스트 형식의 메시지에는 이미지가 포함되지 않으므로 열었는지 여부를 감지할 수 없습니다. 이미지 표시에 연결된 오류 여백에 의해 메시지 열기를 기반으로 계산된 값은 항상 예측됩니다.

## 대상 개인/수신자 {#targeted-persons---recipients}

일부 보고서에서는 Adobe Campaign이 타겟팅된 사람과 타겟팅된 수신자를 구별합니다.

타겟팅된 수신자는 게재를 받은 모든 수신자입니다.

대상자 수에는 타겟팅된 수신자와 이메일을 받은 모든 사람이 포함됩니다. 새 브라우저(메시지가 아직 열리지 않은 경우)를 열거나 클릭할 때마다 통계에 다른 사람이 추가됩니다.

예를 들어 직장에서 이메일(Adobe Campaign에 의해 전송됨)을 받고 열기 또는 클릭하는 경우 타겟팅된 수신자(즉, 수신자=1, person=1)로 카운트됩니다. 이 이메일을 두 친구에게 전송하는 경우 타겟팅된 수신자 수는 여전히 1명이고 사용자 수는 3명입니다. 값 3은 새 브라우저에서 열기/클릭될 때마다 일치합니다.
