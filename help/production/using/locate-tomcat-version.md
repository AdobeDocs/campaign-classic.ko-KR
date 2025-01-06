---
product: campaign
title: Adobe Campaign에서 Tomcat 버전 찾기
description: Adobe Campaign 인스턴스에 사용된 Embedded Tomcat 웹 서블릿의 현재 버전을 확인하는 방법을 알아봅니다
feature: Monitoring
badge-v7-prem: label="온-프레미스/하이브리드만" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 76411b29-d300-4aaa-8d3b-d8ff74c3ce93
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---

# Tomcat 버전 찾기{#locate-tomcat-version}

Adobe Campaign은 Apache Tomcat **이라는**&#x200B;포함된 웹 서블릿을 사용하여 애플리케이션과 모든 외부 인터페이스(클라이언트 콘솔, 추적된 URL 링크, SOAP 호출 등) 간의 HTTP/HTTPS 요청을 처리합니다. 모든 외부 대상 Adobe Campaign 인스턴스의 경우 종종 이 앞에 외부 웹 서버(일반적으로 IIS 또는 Apache)가 있습니다.

문제를 해결하기 위해 **Campaign Classic 온-프레미스 인스턴스**&#x200B;에서 사용되는 Tomcat의 정확한 버전을 확인하려면 아래 절차를 따르십시오.

## Adobe Campaign에서 사용된 Tomcat

Tomcat은 Java에서 실행되며 JDK를 설치해야 합니다. 자세한 내용은 [Campaign 호환성 매트릭스](../../rn/using/compatibility-matrix.md) 섹션의 JDK(Java Development Kit)를 참조하십시오.

Adobe Campaign에서 사용되는 Tomcat은 일반적으로 사용 가능한 전체 Tomcat 릴리스의 모든 기능을 사용하지 않는 사용자 정의 내장 버전이며 전체 버전의 모든 취약성을 겪지 않을 수 있습니다. 또한 Tomcat은 외부 인터넷에 노출되지 않아야 하며 노출된 모든 Adobe Campaign 인스턴스에는 Tomcat 앞에 외부 웹 서버(IIS, Apache 등)가 있어야 보호됩니다.

Tomcat의 내장 버전의 새 버전 또는 업그레이드된 버전은 Adobe Campaign 빌드의 외부에 별도의 패치가 아닌 Adobe Campaign 자체의 새 빌드와 함께 출시됩니다.

>[!AVAILABILITY]
>
>
>* Campaign v7.4.1부터 Tomcat 10.1이 기본 버전입니다.
>
>* Adobe Campaign Classic은 WebSocket 및 HTTP2 프로토콜을 사용하지 않습니다.
>


## 포함된 Tomcat 버전을 찾는 방법

Adobe Campaign 인스턴스에서 포함된 Tomcat 버전을 찾으려면 아래 단계를 따르십시오.

>[!NOTE]
>
>확인해야 하는 Adobe Campaign 서버의 파일에 대한 액세스 권한이 있어야 합니다. 아래에 설명된 프로시저는 **온-프레미스 호스팅 모델**&#x200B;에만 적용됩니다.

1. Adobe Campaign 설치 폴더 내의 *\tomcat-11\lib* 하위 폴더로 이동합니다(예: Windows의 *C:\Program Files\ [Installation_folder]* 또는 Linux의 */usr/local/neolane/nl6*).

1. *catalina.jar* 파일을 외부 임시 폴더(예: 데스크톱)에 복사하고 확장명을 .jar에서 .zip으로 변경합니다.

1. 복사된 파일의 압축을 풉니다. 이렇게 하면 많은 하위 폴더와 파일이 생성됩니다.

1. 압축 해제된 파일/폴더에서 텍스트 편집기를 사용하여 다음 포함된 파일을 열거나 읽습니다. *org/apache/catalina/util/ServerInfo.properties*. 텍스트 편집기로 쉽게 열 수 있도록 .txt 확장자를 추가해야 할 수 있습니다.

1. 완료되면 만든 임시 파일을 서버 시스템에 있는 경우 삭제합니다.

예를 들어 Adobe Campaign용 *ServerInfo.properties* 파일에는 Tomcat v11.X를 나타내는 다음 정보가 포함되어 있습니다.

*`server.info=Apache Tomcat/11.X`*

*`server.number=A.B.X.Y`*

*`server.built=MM DD YYY HH:MM:SS`*

특정 인스턴스에서 사용되는 Tomcat의 정확한 버전을 설정할 수 있으면 Tomcat 관련 문제를 해결하는 데 도움이 될 수 있습니다.

>[!NOTE]
>
>임베드된 Tomcat의 주요 버전은 Adobe Campaign의 주요 버전이 변경될 때만 업그레이드됩니다(이전 버전이 더 이상 공식적으로 지원되지 않을 수 있지만 일부 고객이 이러한 버전을 계속 실행하고 있을 수 있으므로 정보가 유용할 수 있음).
>

