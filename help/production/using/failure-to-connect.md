---
product: campaign
title: 연결 실패
description: 연결 실패
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용됩니다."
badge-v7-prem: label="온-프레미스 및 하이브리드" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3c793dc1-9654-4289-a3d2-30c3078fd848
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 6%

---

# 연결 실패{#failure-to-connect}



연결 문제의 원인은 다양할 수 있으며 다양한 컨텍스트에 따라 다릅니다.

다음 테스트를 시도할 수 있으며 연결 오류가 지속되면 [Adobe 고객 지원 센터](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).



<table> 
<thead> 
<tr> 
<th>확인<br /> </th> 
<th>해결 방법<br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td>컴퓨터에서 인터넷에 액세스할 수 있습니까?</td> 
<td>예를 들어 인터넷에서 웹 사이트에 연결할 수 있는지 확인합니다. 연결할 수 없는 경우 시스템에 문제가 있습니다. 시스템 관리자에게 문의하십시오.</td>
</tr>
<tr> 
<td>다른 서비스를 통해 Adobe Campaign을 호스팅하는 서버에 연결할 수 있습니까?</td> 
<td>SSH 또는 다른 방법을 통해 서버에 연결합니다. 이것이 불가능할 경우 주최사에 문제가 있습니다. 해당 시스템 관리자에게 문의하십시오.</td>
</tr>
<tr> 
<td>웹 서버가 응답합니까?</td> 
<td>웹 브라우저를 사용하여 Adobe Campaign 서버 액세스 URL에 연결합니다. <b>http(s):/ &lt;urlserver&gt;</b>. 응답하지 않으면 웹 서버가 시스템에서 중지됩니다. 서비스를 다시 시작하려면 호스트 회사의 시스템 관리자에게 문의하십시오.</td>
</tr>
<tr> 
<td>Adobe Campaign이 올바르게 통합되었습니까?</td> 
<td>다음에 로그온합니다. <b>http(s):/&lt;urlserver&gt;/r/test</b> URL. 서버는 다음 유형의 메시지를 반환해야 합니다. &lt;redir status="OK" date="YYYY/MM/DD HH&lt;span id="0" translate="no"/&gt;SS" build="XXXX" host="&lt;hostname&gt;" localhost="&lt;server&gt;" /&gt;
이 결과를 얻지 못한 경우 웹 서버 구성에서 통합을 고려했는지 확인하십시오.:MM:</td>
</tr>
<tr> 
<td>다음 URL에 연결합니다. <b>http(s):/&lt;urlserver&gt;/nl/jsp/logon.jsp</b></td>
<td>Tomcat Java 오류가 발생하면 JAVA 통합이 올바르게 수행되었는지 확인합니다. [application path of application]/nl6/customer.sh 파일에 통합됩니다.</td>
</tr>
<tr> 
<td>다음 URL에 연결합니다. <b>http(s):/&lt;urlserver&gt;/nl/jsp/logon.jsp</b></td>
<td>빈 페이지가 표시되면 Adobe Campaign 웹 모듈이 시작되었는지 확인합니다. nlserver pdump 명령은 DD/MM/YYYY의 Adobe Campaign Classic용 애플리케이션 서버(7.X YY.R 빌드 XXX@SHA1)를 반환해야 합니다. 그렇지 않으면 nlserver start web 명령을 사용하여 모듈을 재시작합니다.</td>
</tr>
<tr>
<td>보안 영역의 일반 구성을 확인합니다.</td>
<td>보안 영역 구성에 대한 자세한 내용은 <a href="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/configuring-campaign-server.html#configuring-campaign-server"/>이 섹션.</a></td>
</tr>
<tr>
<td>nlserver pdump 명령이 <b>작업 없음</b></td>
<td>전체 Adobe Campaign 애플리케이션을 다시 시작해야 합니다. 이렇게 하려면 다음 명령을 사용합니다. <b>nlserver watchdog -svc -noconsole</b></td>
</tr>
</tbody> 
</table>
