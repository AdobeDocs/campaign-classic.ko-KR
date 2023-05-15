---
product: campaign
title: Adobe Campaign에서 Tomcat 버전 찾기
description: Adobe Campaign 인스턴스에 사용된 포함된 Tomcat 웹 서블릿의 현재 버전을 확인하는 방법을 배웁니다
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 76411b29-d300-4aaa-8d3b-d8ff74c3ce93
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# Tomcat 버전 찾기{#locate-tomcat-version}



Adobe Campaign은 **Apache Tomcat이라는 포함된 웹 서블릿** 를 눌러 응용 프로그램과 외부 인터페이스(클라이언트 콘솔, 추적된 URL 링크, SOAP 호출 등) 간에 HTTP/HTTPS 요청을 처리합니다. 외부 대면 Adobe Campaign 인스턴스에 대한 외부 웹 서버(일반적으로 IIS 또는 Apache)가 이 서버 앞에 있는 경우가 많습니다.

에서 사용되는 Tomcat의 정확한 버전을 확인하려면 아래 절차를 따르십시오. **온-프레미스 인스턴스 Campaign Classic** 를 사용하여 문제를 해결할 수 있습니다.

## Adobe Campaign에 사용된 Tomcat

Tomcat은 Java에서 실행되며 JDK를 설치해야 합니다. 자세한 내용은 [Campaign 호환성 매트릭스](../../rn/using/compatibility-matrix.md) 섹션을 참조하십시오.

Adobe Campaign에 사용되는 Tomcat은 일반적으로 사용 가능한 전체 Tomcat 릴리스의 모든 기능을 사용하지 않으며 전체 버전의 취약점이 모두 발생하지 않을 수 있는 사용자 지정된 포함 버전입니다. Tomcat도 외부 인터넷에 노출되어서는 안 되며, 노출된 모든 Adobe Campaign 인스턴스에는 외부 웹 서버(IIS, Apache 등)가 있어야 합니다. Tomcat 앞에서 그것을 보호하기 위해.

포함된 버전의 새 또는 업그레이드된 버전의 Tomcat은 Adobe Campaign 빌드 외부의 별도의 패치로서가 아니라 Adobe Campaign 자체의 새 빌드에서만 릴리스됩니다.

## 포함된 Tomcat 버전을 찾는 방법

Adobe Campaign 인스턴스에서 포함된 Tomcat 버전을 찾으려면 아래 단계를 따르십시오.

>[!NOTE]
>
>확인해야 하는 Adobe Campaign 서버의 파일에 액세스할 수 있어야 합니다. 아래 설명된 절차는 **온-프레미스 호스팅 모델**.

1. 로 이동합니다 *\tomcat-7\lib* Adobe Campaign 설치 폴더 내의 하위 폴더(예: *C:\Program Files\ [Installation_folder]* Windows 또는 */usr/local/neolane/nl6* ( Linux).

   Tomcat v6을 사용하여 이전 버전의 Adobe Campaign을 실행하는 경우 *\tomcat-6\lib*.

1. 파일 복사 *catalina.jar* 외부 임시 폴더(예: 데스크탑)로 이동하고 확장자를 .jar에서 .zip로 변경합니다.

1. 복사한 파일의 압축을 해제합니다. 이렇게 되면 많은 하위 폴더와 파일이 생성됩니다.

1. 압축을 푼 파일/폴더 내에서 텍스트 편집기를 사용하여 다음 포함된 파일을 열거나 읽습니다. *org/apache/catalina/util/ServerInfo.properties*. 텍스트 편집기를 사용하여 쉽게 열기 위해 .txt 확장자를 추가해야 할 수 있습니다.

1. 완료되면 서버 컴퓨터에 있는 경우 만든 임시 파일을 삭제합니다.

예를 들어, *ServerInfo.properties* Adobe Campaign용 파일에는 Tomcat v8.5.X를 나타내는 다음 정보가 포함됩니다.

*server.info=Apache Tomcat/8.5.X*

*server.number=8.5.X.Y*

*server.build=MM DD YYY HH:MM:SS*

특정 인스턴스에 사용된 정확한 버전의 Tomcat을 설정할 수 있게 되면 Tomcat 관련 문제를 해결하는 데 도움이 될 수 있습니다.

>[!NOTE]
>
>포함된 Tomcat의 주요 버전은 Adobe Campaign의 주요 버전이 변경되는 경우에만 업그레이드됩니다(이전 버전은 더 이상 공식적으로 지원되지 않을 수 있지만 일부 고객이 이러한 버전을 계속 실행 중일 수 있으므로 정보가 유용할 수 있습니다.).
>
>예를 들어 Adobe Campaign v6.02는 항상 Tomcat v6.x를 사용합니다.
