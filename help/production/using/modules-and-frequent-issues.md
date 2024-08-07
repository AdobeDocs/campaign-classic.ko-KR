---
product: campaign
title: 모듈 및 자주 발생하는 문제
description: 모듈 및 자주 발생하는 문제
feature: Monitoring, Troubleshooting
badge-v7-prem: label="온-프레미스/하이브리드만" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: dbd50178-0a16-46ed-bfad-47beb3c2a420
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 7%

---

# 모듈 및 자주 발생하는 문제{#modules-and-frequent-issues}



다음은 빈번한 문제의 영향을 받는 모듈 목록입니다.

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
   <td> 이 내보내기를 예약한 연산자는 내보내기를 다시 실행해야 합니다. 델타 또는 전체 다시 시작.<br /> </td> 
  </tr> 
  <tr> 
   <td> 가져오기 </td> 
   <td> 가져오기 프로세스 실행<br /> </td> 
   <td> 이 내보내기를 예약한 연산자는 내보내기를 다시 실행해야 합니다. 데이터베이스에서 중복 항목을 확인합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> inMail </td> 
   <td> 바운스 사서함 <br />을(를) 읽는 중 </td> 
   <td> 바운스 메일이 더 이상 전달되지 않는 경우 이 모듈을 확인하십시오.<br /> </td> 
  </tr> 
  <tr> 
   <td> MTA </td> 
   <td> 이메일 배달<br /> </td> 
   <td> 메일이 더 이상 전송되지 않으면 이 모듈을 확인하십시오.<br /> </td> 
  </tr> 
  <tr> 
   <td> 통계 </td> 
   <td> MTA 연결 통계 유지 관리<br /> </td> 
   <td> 메일이 더 이상 전송되지 않으면 이 모듈을 확인하십시오.<br /> </td> 
  </tr> 
  <tr> 
   <td> syslogd </td> 
   <td> 로그 쓰기<br /> </td> 
   <td> 일부 로그가 로그 파일에 없는 경우 모듈이 포트 6666을 사용하고 있는지 확인하십시오. <a href="../../production/using/general-architecture.md#list-of-open-ports" target="_blank">열린 포트 목록</a>.<br />을 참조하세요. </td> 
  </tr> 
  <tr> 
   <td> 추적 </td> 
   <td> 추적 로그 통합 및 검색<br /> </td> 
   <td> 추적 로그가 더 이상 전달되지 않으면 이 모듈을 확인하십시오.<br /> </td> 
  </tr> 
  <tr> 
   <td> trackinglogd </td> 
   <td> 추적 로그 쓰기 및 서버 <br /> 제거 </td> 
   <td> 추적 로그가 더 이상 전달되지 않고 서버의 파일에 로그 추적이 없는 경우 이 모듈을 확인하십시오. <a href="../../production/using/tracking-logs-issues.md" target="_blank">추적 로그 문제</a>.<br />를 참조하세요. </td> 
  </tr> 
  <tr> 
   <td> 감시 </td> 
   <td> 인스턴스 <br /> 시작 및 모니터링 </td> 
   <td> 프로세스가 시작되지 않으면 이 모듈을 확인하십시오.<br /> </td> 
  </tr> 
  <tr> 
   <td> 웹 </td> 
   <td> 응용 프로그램 서버(HTTP 및 SOAP)<br /> </td> 
   <td> 콘솔 및 웹 연결이 작동하지 않는 경우 이 모듈을 확인하고 <strong>xtk:session</strong> 유형 오류를 트리거합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> wfserver </td> 
   <td> 워크플로 인스턴스 실행을 제어합니다.<br /> </td> 
   <td> 문제가 발생하면 이 모듈을 다시 시작합니다. 필요한 경우 <a href="../../production/using/log-precision.md" target="_blank">로그 정밀도</a> 섹션에 자세히 설명된 로그 정밀도 향상을 위한 절차를 적용합니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>
