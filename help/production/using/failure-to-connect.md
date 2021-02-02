---
solution: Campaign Classic
product: campaign
title: 연결 실패
description: 연결 실패
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 3139a9bf5036086831e23acef21af937fcfda740
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 2%

---


# 연결 실패{#failure-to-connect}

연결 문제의 원인은 여러 개이며 다양한 컨텍스트에 따라 다릅니다.

다음 테스트를 시도해 볼 수 있으며 연결 오류가 계속되면 [Adobe 고객 지원 센터](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)에 문의하십시오.



<table> 
<thead> 
<tr> 
<th>검사<br /> </th> 
<th>해결 방법<br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td>컴퓨터에서 인터넷 연결이 되나요?</td> 
<td>인터넷의 웹 사이트에 연결할 수 있는지(예:) 확인합니다. 연결할 수 없는 경우 컴퓨터에 문제가 있습니다. 시스템 관리자에게 문의하십시오.</td>
</tr>
<tr> 
<td>다른 서비스를 통해 Adobe Campaign을 호스팅하는 서버에 연결할 수 있습니까?</td> 
<td>SSH 또는 다른 수단을 통해 서버에 연결합니다. 가능하지 않은 경우 호스트 회사에 문제가 있습니다. 시스템 관리자에게 문의하십시오.</td>
</tr>
<tr> 
<td>웹 서버가 응답합니까?</td> 
<td>웹 브라우저를 사용하여 Adobe Campaign 서버 액세스 URL에 연결:<b>http(s):// &lt;urlserver&gt;</b>. 응답하지 않으면 웹 서버가 컴퓨터에서 중지됩니다. 서비스를 다시 시작하려면 호스트 회사의 시스템 관리자에게 문의하십시오.</td>
</tr>
<tr> 
<td>Adobe Campaign이 올바르게 통합되었습니까?</td> 
<td>다음에 로그온합니다.<b>http(s)://&lt;urlserver&gt;/r/test</b> URL 서버는 다음 유형의 메시지를 반환해야 합니다.&lt;redir status='OK' date='YYYY/MM/DD HH:MM:SS' 빌드='XXXX' 호스트='&lt;호스트 이름&gt;' localHost='&lt;서버&gt;'/&gt;
이 결과를 얻지 못한 경우 통합을 고려하려는 웹 서버 구성을 확인하십시오.</td>
</tr>
<tr> 
<td>다음 URL에 연결:<b>http(s)://&lt;URLSERVER&gt;/nl/jsp/logon.jsp</b></td>
<td>Tomcat Java 오류가 발생하는 경우 JAVA 통합이 올바르게 수행되었는지 확인하십시오. [응용 프로그램 경로]/nl6/customer.sh 파일에 통합되어 있습니다.</td>
</tr>
<tr> 
<td>다음 URL에 연결:<b>http(s)://&lt;URLSERVER&gt;/nl/jsp/logon.jsp</b></td>
<td>빈 페이지가 표시되면 Adobe Campaign 웹 모듈이 시작되었는지 확인합니다. 명령 nlserver pdump는 DD/MM/YYYY의 Adobe Campaign Classic(7.X YY.R 빌드 XXX@SHA1)용 응용 프로그램 서버를 반환해야 합니다. 그렇지 않은 경우 nlserver 시작 웹 명령을 사용하여 모듈을 다시 시작합니다.</td>
</tr>
<tr>
<td>보안 영역의 일반 구성을 확인합니다.</td>
<td>보안 영역 구성에 대한 자세한 내용은 <a href="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/configuring-campaign-server.html?lang=en#configuring-campaign-server"/>이 섹션을 참조하십시오.</a></td>
</tr>
<tr>
<td>명령 nlserver pdump는 <b>작업 없음</b>을 반환합니다.</td>
<td>전체 Adobe Campaign 응용 프로그램을 다시 시작해야 합니다. 이렇게 하려면 다음 명령을 사용합니다.<b>nlserver watchdog -svc -noconsole</b></td>
</tr>
</tbody> 
</table>
