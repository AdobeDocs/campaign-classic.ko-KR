---
solution: Campaign Classic
product: campaign
title: 모듈 및 자주 발생하는 문제
description: 모듈 및 자주 발생하는 문제
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 5%

---


# 모듈 및 자주 발생하는 문제{#modules-and-frequent-issues}

다음은 자주 발생하는 문제로 인해 영향을 받는 모듈 목록입니다.

<table> 
 <thead> 
  <tr> 
   <th> 모듈 </th> 
   <th> 실행 범위 </th> 
   <th> 문제 해결 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 내보내기 </td> 
   <td> 내보내기 프로세스 실행<br /> </td> 
   <td> 이 내보내기를 예약한 연산자가 다시 실행해야 합니다. 델타 또는 전체 다시 시작합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> import </td> 
   <td> 가져오기 프로세스 실행<br /> </td> 
   <td> 이 내보내기를 예약한 연산자가 다시 실행해야 합니다. 데이터베이스에 중복 항목이 있는지 확인하십시오.<br /> </td> 
  </tr> 
  <tr> 
   <td> inMail </td> 
   <td> 바운스 메일 상자 읽기<br /> </td> 
   <td> 바운스 메일이 더 이상 전달되지 않으면 이 모듈을 확인하십시오.<br /> </td> 
  </tr> 
  <tr> 
   <td> mta </td> 
   <td> 이메일 배달<br /> </td> 
   <td> 메일이 더 이상 전송되지 않으면 이 모듈을 확인하십시오.<br /> </td> 
  </tr> 
  <tr> 
   <td> stat </td> 
   <td> MTA 연결 통계 유지<br /> </td> 
   <td> 메일이 더 이상 전송되지 않으면 이 모듈을 확인하십시오.<br /> </td> 
  </tr> 
  <tr> 
   <td> sylogd </td> 
   <td> 로그 쓰기<br /> </td> 
   <td> 로그 파일에 일부 로그가 없는 경우 모듈이 포트 6666을 사용하고 있는지 확인하십시오. <a href="../../production/using/general-architecture.md#list-of-open-ports" target="_blank">열려 있는 포트 목록</a>을 참조하십시오.<br /> </td> 
  </tr> 
  <tr> 
   <td> 추적 </td> 
   <td> 추적 로그 통합 및 검색<br /> </td> 
   <td> 추적 로그가 더 이상 전달되지 않으면 이 모듈을 확인하십시오.<br /> </td> 
  </tr> 
  <tr> 
   <td> trackinglogs </td> 
   <td> 추적 로그 쓰기 및 제거 서버<br /> </td> 
   <td> 추적 로그가 더 이상 전달되지 않고 서버의 파일에 로그 추적이 없는지 이 모듈을 확인하십시오. 추적 로그 문제</a>를 참조하십시오.<br /><a href="../../production/using/tracking-logs-issues.md" target="_blank"> </a></td> 
  </tr> 
  <tr> 
   <td> 감시 </td> 
   <td> 시작 및 모니터링 인스턴스<br /> </td> 
   <td> 프로세스가 시작되지 않은 경우 이 모듈을 확인하십시오.<br /> </td> 
  </tr> 
  <tr> 
   <td> 웹 </td> 
   <td> 응용 프로그램 서버(HTTP 및 SOAP)<br /> </td> 
   <td> 콘솔 및 웹 연결이 작동하지 않고 <strong>xtk:session</strong> 유형 오류<br />를 트리거하는 경우 이 모듈을 확인하십시오. </td> 
  </tr> 
  <tr> 
   <td> wfserver </td> 
   <td> 워크플로 인스턴스 실행을 제어합니다.<br /> </td> 
   <td> 문제가 발생하면 이 모듈을 다시 시작하십시오. 필요한 경우 절차를 적용하여 <a href="../../production/using/log-precision.md" target="_blank">로그 정밀도</a> 섹션에 자세히 설명된 로그의 정확도를 높입니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

