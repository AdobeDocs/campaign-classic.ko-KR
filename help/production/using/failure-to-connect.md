---
product: campaign
title: 연결 실패
description: 연결 실패
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3c793dc1-9654-4289-a3d2-30c3078fd848
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 4%

---

# 연결 실패{#failure-to-connect}



연결 문제의 이유는 여러 가지일 수 있으며 다양한 컨텍스트에 따라 다릅니다.

다음 테스트를 시도할 수 있으며 연결 오류가 지속되면 [고객 지원 Adobe](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).



<table> 
<thead> 
<tr> 
<th>검사<br /> </th> 
<th>해결 방법<br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td>컴퓨터에서 인터넷에 접속할 수 있나요?</td> 
<td>인터넷에서 웹 사이트에 연결할 수 있는지 확인합니다(예). 연결할 수 없으면 시스템에 문제가 있습니다. 시스템 관리자에게 문의하십시오.</td>
</tr>
<tr> 
<td>다른 서비스를 통해 Adobe Campaign을 호스팅하는 서버에 연결할 수 있습니까?</td> 
<td>SSH 또는 기타 수단을 통해 서버에 연결합니다. 불가능한 경우 호스트 회사에 문제가 있습니다. 시스템 관리자에게 문의하십시오.</td>
</tr>
<tr> 
<td>웹 서버가 응답합니까?</td> 
<td>웹 브라우저를 사용하여 Adobe Campaign 서버 액세스 URL에 연결합니다. <b>http(s):// &lt;urlserver&gt;</b>. 응답하지 않으면 웹 서버가 시스템에서 중지됩니다. 서비스를 다시 시작하려면 호스트 회사의 시스템 관리자에게 문의하십시오.</td>
</tr>
<tr> 
<td>Adobe Campaign이 올바르게 통합되었습니까?</td> 
<td>에 로그인합니다. <b>http(s)://&lt;urlserver&gt;/r/test</b> URL. 서버는 다음 유형의 메시지를 반환해야 합니다. &lt;redir status="OK" date="YYYY/MM/DD HH&lt;span id="0" translate="no"/&gt;SS" build="XXXX" host="&lt;hostname&gt;" localhost="&lt;server&gt;" /&gt;
이 결과를 얻지 못한 경우 통합이 고려되는 웹 서버 구성을 확인하십시오.:MM:</td>
</tr>
<tr> 
<td>다음 URL에 연결합니다. <b>http(s)://&lt;urlserver&gt;/nl/jsp/logon.jsp</b></td>
<td>Tomcat Java 오류를 가져오는 경우 JAVA 통합이 올바르게 수행되었는지 확인합니다. 이 파일은 [응용 프로그램 경로]/nl6/customer.sh 파일에 통합됩니다</td>
</tr>
<tr> 
<td>다음 URL에 연결합니다. <b>http(s)://&lt;urlserver&gt;/nl/jsp/logon.jsp</b></td>
<td>빈 페이지가 표시되면 Adobe Campaign 웹 모듈이 시작되었는지 확인합니다. nlserver pdump 명령은 DD/MM/YYYY의 Adobe Campaign Classic(7.X YY.R 빌드 XXX@SHA1)용 응용 프로그램 서버를 반환해야 합니다. 그렇지 않으면 nlserver start web 명령을 사용하여 모듈을 다시 시작합니다</td>
</tr>
<tr>
<td>보안 영역의 일반 구성을 확인합니다.</td>
<td>보안 영역 구성에 대한 자세한 내용은 <a href="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/configuring-campaign-server.html?lang=en#configuring-campaign-server"/>이 섹션.</a></td>
</tr>
<tr>
<td>nlserver pdump 명령은 다음을 반환합니다. <b>작업 없음</b></td>
<td>전체 Adobe Campaign 애플리케이션을 다시 시작해야 합니다. 이렇게 하려면 다음 명령을 사용합니다. <b>nlserver watchdog -svc -noconsole</b></td>
</tr>
</tbody> 
</table>
