---
solution: Campaign Classic
product: campaign
title: 연결 실패
description: 연결 실패
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: eb7e1c98f69ba20ef4222bfefea74fdaf6072397
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 2%

---


# 연결 실패{#failure-to-connect}

연결 문제의 원인은 여러 개이며 다양한 컨텍스트에 따라 달라질 수 있습니다.

다음 테스트를 수행할 수 있으며 연결 오류가 계속되면 **Adobe Campaign 지원에 문의하십시오**.



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
   <td>SSH 또는 다른 수단을 통해 서버에 연결합니다. 이 경우 호스트 회사에 문제가 발생합니다. 시스템 관리자에게 문의하십시오.</td>
  </tr>
  <tr> 
   <td>웹 서버가 응답합니까?</td> 
   <td>웹 브라우저를 사용하여 Adobe Campaign 서버에 연결: <b>http(s)://&lt;urlserver&gt;</b>. 응답하지 않으면 컴퓨터에서 웹 서버가 중지됩니다. 서비스를 다시 시작하려면 호스트 회사의 시스템 관리자에게 문의하십시오.</td>
  </tr>
  <tr> 
   <td>Adobe Campaign이 제대로 통합되었습니까?</td> 
   <td>다음에 로그온합니다. <b>http(s)://&lt;urlserver&gt;/r/test</b> URL. 서버는 다음 유형의 메시지를 반환해야 합니다.

    &lt;pre>
    &lt;redir status=&#39;OK&#39; date=&#39;YYYY/MM/DD HH:MM:SS&#39; build=&#39;XXXX&#39; host=&#39;&lt;hostname>&#39; localHost=&#39;&lt;server>&#39;/>
    &lt;/pre>
    
    이 결과를 얻지 않으면 통합을 고려하는 웹 서버 구성을 확인하십시오.&lt;/td>
</tr>
  <tr> 
   <td>Adobe Campaign 웹 모듈이 실행되었습니까?</td> 
   <td>
   다음 URL에 연결: <b>http(s)://&gt;URLSERVER&lt;/nl/jsp/logon.jsp</b>* Tomcat Java 오류가 발생하는 경우:

    JAVA 통합이 올바르게 수행됩니까? Adobe Campaign은 SUN JDK가 필요합니다.
    
    이 파일은 [응용 프로그램의 경로]/nl6/customer.sh
    
    *라는 파일에 통합되어 있습니다. 빈 페이지를 받은 경우: Adobe Campaign 웹 모듈
    
    이 시작되었습니까? DD/
    
    MM/YYYY
    [..]web@default (27515) - 55.2Mb
    [..]
    nlserver pdumpHH:MM:SS > Adobe Campaign Classic용 응용 프로그램 서버(7.X YY.R 빌드 XXX@SHA1)을 구해야 합니다
    
    
    
    
    
    
    
    
    
    ..... /pre>*이 없는 경우 다음 명령을 사용하여 다시 시작하십시오.>neclserver start webStart&lt;/pre>td.
</tr>
  <tr>
  	<td>보안 영역의 일반 구성을 확인합니다.</td>
  	<td>보안 영역 구성에 대한 자세한 내용은 [이 섹션](../../installation/using/configuring-campaign-server.md#defining-security-zones)을 참조하십시오.</td>
  </tr>
 </tbody> 
</table>
