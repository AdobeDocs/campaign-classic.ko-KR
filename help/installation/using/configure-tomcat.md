---
product: campaign
title: Campaign Tomcat 구성
description: Campaign Tomcat 구성
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a2126458-2ae5-47c6-ad13-925f0e067ecf
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---

# Apache Tomcat 구성 {#configuring-tomcat}



Adobe Campaign은 **Apache Tomcat이라는 포함된 웹 서블릿** 를 눌러 응용 프로그램과 외부 인터페이스(클라이언트 콘솔, 추적된 URL 링크, SOAP 호출 등) 간에 HTTP/HTTPS 요청을 처리합니다. 외부 대면 Adobe Campaign 인스턴스에 대한 외부 웹 서버(일반적으로 IIS 또는 Apache)가 이 서버 앞에 있는 경우가 많습니다.

Campaign의 Tomcat과 에서 Tomcat 버전을 찾는 방법에 대해 자세히 알아보십시오 [이 페이지](../../production/using/locate-tomcat-version.md).

>[!NOTE]
>
>이 절차는 **온-프레미스** 배포.

## Apache Tomcat의 기본 포트 {#default-port-for-tomcat}

Tomcat 서버의 8080 수신 대기 포트가 구성에 필요한 다른 응용 프로그램으로 이미 사용 중인 경우 8080 포트를 무료 포트(예: 8090)로 교체해야 합니다. 변경하려면 **server.xml** 에 저장된 파일 **/tomcat-8/conf** Adobe Campaign 설치 폴더의 디렉토리입니다.

그런 다음 JSP 릴레이 페이지의 포트를 수정합니다. 이렇게 하려면 **serverConf.xml** 에 저장된 파일 **/conf** Adobe Campaign 설치 디렉토리의 디렉토리.

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

## Apache Tomcat에서 폴더 매핑 {#mapping-a-folder-in-tomcat}

고객별 설정을 정의하기 위해 **user_contexts.xml** 파일의 **/tomcat-8/conf** 폴더 - 에도 포함 **contexts.xml** 파일.

이 파일에는 다음 유형의 정보가 포함됩니다.

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

필요한 경우 서버 측에서 이 작업을 재현할 수 있습니다.

## Tomcat 오류 보고서 숨기기 {#hide-tomcat-error-report}

보안상의 이유로 Tomcat 오류 보고서를 숨기는 것이 좋습니다. 다음은 단계입니다.

1. 를 엽니다. **server.xml** 에 있는 파일 **/tomcat-8/conf** Adobe Campaign 설치 폴더의 디렉토리:  `/usr/local/neolane/nl6/tomcat-8/conf`
1. 모든 기존 컨텍스트 요소 뒤에 다음 요소를 맨 아래에 추가합니다.

   ```
   <Valve className="org.apache.catalina.valves.ErrorReportValve" showReport="false" showServerInfo="false"/>
   ```

1. nlserver 및 Apache 웹 서버를 다시 시작합니다.
