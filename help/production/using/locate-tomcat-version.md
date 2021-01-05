---
solution: Campaign Classic
product: campaign
title: Adobe Campaign에서 Tomcat 버전 찾기
description: Adobe Campaign 인스턴스에 사용된 포함된 Tomcat 웹 서블릿의 현재 버전을 확인하는 방법을 알아봅니다.
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 49e49d5e35d14a31236cc4f78188cdf77353fbbf
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 0%

---


# Tomcat 버전 찾기{#locate-tomcat-version}

Adobe Campaign은 응용 프로그램과 외부 인터페이스(클라이언트 콘솔, 추적된 URL 링크, SOAP 호출 등) 사이의 HTTP/HTTPS 요청을 처리하기 위해 Apache Tomcat **라는 포함된 웹 서블릿을 사용합니다.** 외부 Adobe Campaign 인스턴스에 대해 이 서버 앞에 외부 웹 서버(일반적으로 IIS 또는 Apache)가 있는 경우가 많습니다.

문제를 해결하는 데 도움이 되도록 **Campaign Classic 온-프레미스 인스턴스**&#x200B;에 사용된 Tomcat의 정확한 버전을 확인하려면 아래 절차를 따르십시오.

## Adobe Campaign에서 사용된 Tomcat

Tomcat은 Java에서 실행되므로 JDK를 설치해야 합니다. 자세한 내용은 [캠페인 호환성 매트릭스](../../rn/using/compatibility-matrix.md) 섹션의 JDK(Java 개발 키트)를 참조하십시오.

Adobe Campaign에서 사용되는 Tomcat은 Tomcat의 정식 릴리스의 모든 기능을 사용하지 않는 사용자 정의 내장 버전이며, 정식 버전의 모든 취약점이 악용되지 않을 수 있습니다. Tomcat은 외부 인터넷에 노출되어서는 안 되며, 노출되는 모든 Adobe Campaign 인스턴스에는 외부 웹 서버(IIS, Apache 등)가 있어야 합니다. Tomcat 앞에서 그것을 보호하기 위해.

Tomcat의 새 버전 또는 업그레이드된 버전은 Adobe Campaign 빌드의 외부에 별도의 패치가 아니라 Adobe Campaign 자체의 새 빌드만을 사용하여 릴리스됩니다.

## 포함된 Tomcat 버전을 찾는 방법

Adobe Campaign 인스턴스에서 포함된 Tomcat 버전을 찾으려면 아래 단계를 따르십시오.

>[!NOTE]
>
>확인해야 하는 Adobe Campaign 서버의 파일에 액세스할 수 있어야 합니다. 아래 설명된 절차는 **온-프레미스 호스팅 모델**&#x200B;에만 적용됩니다.

1. Adobe Campaign 설치 폴더 내의 *\tomcat-7\lib* 하위 폴더(예: Windows의 경우 *C:\Program Files\ [Installation_folder]* 또는 Linux의 */usr/local/neolane/nl6*)로 이동합니다.

   Tomcat v6을 사용하여 이전 버전의 Adobe Campaign을 실행하는 경우 *\tomcat-6\lib*&#x200B;을(를) 사용하십시오.

1. *catalina.jar* 파일을 외부 임시 폴더(예: 바탕 화면)에 복사하고 확장명을 .jar에서 .zip으로 변경합니다.

1. 복사한 파일의 압축을 해제합니다. 그러면 많은 하위 폴더와 파일이 만들어집니다.

1. 압축을 푼 파일/폴더 내에서 텍스트 편집기를 사용하여 다음 포함 파일을 열거나 읽습니다.*org/apache/catalina/util/ServerInfo.properties*. 텍스트 편집기를 사용하여 쉽게 열 수 있도록 .txt 확장명을 추가해야 할 수도 있습니다.

1. 완료되면 서버 컴퓨터에 있는 경우 만든 임시 파일을 삭제합니다.

예를 들어 Adobe Campaign용 *ServerInfo.properties* 파일에는 Tomcat v8.5.X를 나타내는 다음 정보가 포함됩니다.

*server.info=Apache Tomcat/8.5.X*

*server.number=8.5.X.Y*

*server.built=MM DD YYY HH:MM:SS*

특정 인스턴스에서 사용되는 Tomcat의 정확한 버전을 설정할 수 있게 되면 Tomcat 관련 문제를 해결하는 데 도움이 될 수 있습니다.

>[!NOTE]
>
>포함된 Tomcat의 주 버전은 Adobe Campaign의 주요 버전이 변경된 경우에만 업그레이드됩니다(이전 버전은 더 이상 공식적으로 지원되지 않을 수 있지만 일부 고객이 이러한 버전을 계속 실행 중일 수 있으므로 정보가 유용할 수 있습니다).
>
>예를 들어 Adobe Campaign v6.02는 항상 Tomcat v6.x를 사용합니다.