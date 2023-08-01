---
product: campaign
title: Campaign Tomcat 구성
description: Campaign Tomcat 구성
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용됩니다."
badge-v7-prem: label="온-프레미스 및 하이브리드" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a2126458-2ae5-47c6-ad13-925f0e067ecf
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 3%

---

# Apache Tomcat 구성 {#configuring-tomcat}



Adobe Campaign은 **Apache Tomcat이라는 포함된 웹 서블릿** 클라이언트 콘솔, 추적된 URL 링크, SOAP 호출 등 모든 외부 인터페이스와 응용 프로그램 간 HTTP/HTTPS 요청을 처리합니다. 모든 외부 대상 Adobe Campaign 인스턴스의 경우 종종 이 앞에 외부 웹 서버(일반적으로 IIS 또는 Apache)가 있습니다.

Campaign의 Tomcat에 대해 자세히 알아보고 Tomcat 버전을 찾는 방법을 알아봅니다. [이 페이지](../../production/using/locate-tomcat-version.md).

>[!NOTE]
>
>이 절차는 다음으로 제한됩니다. **온-프레미스** 배포.
>

## Apache Tomcat의 기본 포트 {#default-port-for-tomcat}

Tomcat 서버의 8080 수신 포트가 구성에 필요한 다른 응용 프로그램으로 이미 사용 중인 경우 8080 포트를 사용 가능한 포트(예: 8090)로 교체해야 합니다. 변경하려면 **server.xml** 에 저장된 파일 **/tomcat-8/conf** Adobe Campaign 설치 폴더의 디렉터리입니다.

그런 다음 JSP 릴레이 페이지의 포트를 수정합니다. 이렇게 하려면 **serverConf.xml** 에 저장된 파일 **/conf** Adobe Campaign 설치 디렉토리의 디렉토리.

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

## Apache Tomcat에서 폴더 매핑 {#mapping-a-folder-in-tomcat}

고객별 설정을 정의하려면 다음을 만들 수 있습니다 **user_contexts.xml** 파일 위치: **/tomcat-8/conf** 폴더를 채우는 데 사용됩니다. **contexts.xml** 파일.

이 파일에는 다음 유형의 정보가 포함됩니다.

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

필요한 경우 서버측에서 이 작업을 재현할 수 있습니다.

## Tomcat 오류 보고서 숨기기 {#hide-tomcat-error-report}

보안상의 이유로 Tomcat 오류 보고서를 숨기는 것이 좋습니다. 단계는 다음과 같습니다.

1. 를 엽니다. **server.xml** 파일 위치: **/tomcat-8/conf** Adobe Campaign 설치 폴더의 디렉터리:  `/usr/local/neolane/nl6/tomcat-8/conf`
1. 기존의 모든 컨텍스트 요소 뒤에 다음 요소를 맨 아래에 추가합니다.

   ```
   <Valve className="org.apache.catalina.valves.ErrorReportValve" showReport="false" showServerInfo="false"/>
   ```

1. nlserver 및 Apache 웹 서버를 다시 시작합니다.
