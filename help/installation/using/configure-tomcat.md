---
product: campaign
title: Campaign Tomcat 구성
description: Campaign Tomcat 구성
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a2126458-2ae5-47c6-ad13-925f0e067ecf,b4a422b4-4b8b-4883-8d74-0dccda4a5ef3
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---

# Apache Tomcat {#configuring-tomcat} 구성

Adobe Campaign은 Apache Tomcat **이라는 포함된 웹 서블릿을 사용하여 애플리케이션과 외부 인터페이스(클라이언트 콘솔, 추적된 URL 링크, SOAP 호출 등) 간의 HTTP/HTTPS 요청을 처리합니다.** 외부 대면 Adobe Campaign 인스턴스에 대한 외부 웹 서버(일반적으로 IIS 또는 Apache)가 이 서버 앞에 있는 경우가 많습니다.

Campaign의 Tomcat과 이 페이지](../../production/using/locate-tomcat-version.md)에서 Tomcat 버전을 찾는 방법에 대해 자세히 알아보십시오.[

>[!NOTE]
>
>이 절차는 **온-프레미스** 배포로 제한됩니다.


## Apache Tomcat {#default-port-for-tomcat}의 기본 포트

Tomcat 서버의 8080 수신 대기 포트가 구성에 필요한 다른 응용 프로그램으로 이미 사용 중인 경우 8080 포트를 무료 포트(예: 8090)로 교체해야 합니다. 변경하려면 Adobe Campaign 설치 폴더의 **/tomcat-8/conf** 디렉토리에 저장된 **server.xml** 파일을 편집합니다.

그런 다음 JSP 릴레이 페이지의 포트를 수정합니다. 이렇게 하려면 Adobe Campaign 설치 디렉토리의 **/conf** 디렉토리에 저장된 **serverConf.xml** 파일을 변경합니다.

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

## Apache Tomcat {#mapping-a-folder-in-tomcat}에 폴더 매핑

고객별 설정을 정의하기 위해 **/tomcat-8/conf** 폴더에 **user_contexts.xml** 파일을 만들고 이 폴더에 **contexts.xml** 파일도 포함시킬 수 있습니다.

이 파일에는 다음 유형의 정보가 포함됩니다.

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

필요한 경우 서버 측에서 이 작업을 재현할 수 있습니다.
