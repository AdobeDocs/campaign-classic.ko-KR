---
solution: Campaign Classic
product: campaign
title: 애플리케이션 서버
description: 애플리케이션 서버
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 1%

---


# 애플리케이션 서버{#application-server}

필요한 데이터베이스 액세스 레이어는 서버에 설치되어 있어야 하며 Adobe Campaign 계정에서 액세스할 수 있어야 합니다.

## Java 개발 키트 - JDK {#java-development-kit---jdk}

동적 웹 페이지 생성기는 JSP 1.2 기술을 사용합니다. 이를 위해 Apache의 Tomcat 엔진이 응용 프로그램에 포함됩니다. Adobe Campaign 애플리케이션이 설치된 모든 서버에 JDK(Java Development Kit)가 설치되어 있어야 합니다.

Adobe Campaign 응용 프로그램 서버를 실행할 컴퓨터에 먼저 JDK를 설치해야 합니다(**nlserver web** 프로세스). 이 JDK는 동적 웹 페이지(보고서, 웹 양식 등)를 생성하는 데 사용되는 서블릿 컨테이너, Apache Tomcat를 통합하기 때문입니다.

애플리케이션이 Oracle에서 개발한 JDK(Java Development Kit)와 **OpenJDK**&#x200B;에 대해 승인되었습니다.

지원되는 버전은 캠페인 [호환성 매트릭스](../../rn/using/compatibility-matrix.md)에 자세히 설명되어 있습니다.

>[!NOTE]
>
>컴퓨터의 다른 응용 프로그램에서 이미 사용한 적절한 JDK 버전을 사용하여 설치할 수 있습니다.
>  
>설치할 때 웹 브라우저와의 통합을 수행할 필요는 없습니다.
>
>배달 에이전트(**nlserver mta** 프로세스) 또는 워크플로 서버(**nlserver wfserver** 프로세스)만 실행하는 컴퓨터에서는 JDK를 설치할 필요가 없습니다.

Java JDK를 다운로드하려면 다음에 연결합니다.[https://www.oracle.com/technetwork/java/javase/downloads/index.html](https://www.oracle.com/technetwork/java/javase/downloads/index.html).

**경고:JRE이 아니라 JDK를 다운로드해야 합니다.**

>[!CAUTION]
>
>플랫폼 작업 성능을 유지하고 설치된 버전과의 호환성을 보장하려면 Windows 및 Linux에서 자동 JDK 업데이트 기능을 비활성화해야 합니다.

Linux 환경에 JDSL을 설치하려면 패키지 관리자를 사용하는 것이 좋습니다.

Debian 8 및 9에서는 다음 명령을 사용합니다.

```
aptitude install openjdk-8-jdk
```

RHEL 7의 경우 다음 명령을 사용합니다.

```
yum install java-1.8.0-openjdk
```

## OpenSSL {#openssl}

Linux에서는 OpenSSL을 설치해야 합니다. Adobe Campaign에서 지원하는 버전은 **OpenSSL 1.0.1** 및 **OpenSSL 0.9.8**&#x200B;입니다. 하위 버전 0.9.8g~0.9.8o가 허용됩니다.

## 보고서 내보내기 {#exporting-reports}

Adobe Campaign을 사용하면 플랫폼 보고서를 Microsoft Excel 및 Adobe PDF 형식으로 내보낼 수 있습니다. Microsoft Excel 형식의 경우 Adobe Campaign에서는 **LibreOffice**&#x200B;를 사용합니다. Adobe PDF 형식의 경우 Adobe Campaign은 **PhantomJS** 변환기를 사용합니다. PhantomJs는 팩토리 패키지에 포함되어 있으며 Adobe Campaign 응용 프로그램 서버가 실행되는 컴퓨터(**nlserver web** 프로세스)에 LibreOffice를 설치해야 합니다.

>[!NOTE]
>
>Linux의 경우 글꼴을 추가해야 합니다. 자세한 내용은 [MTA 통계용 글꼴](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics)을 참조하십시오.

## SpamAssassin {#spamassassin}

SpamAssaker를 사용하면 수신에 사용되는 스팸 방지 도구에 의해 메시지 위험이 바람직하지 않은 것으로 간주되는지 여부를 결정하기 위해 이메일에 점수를 할당할 수 있습니다. 설치는 선택 사항입니다.

스팸 암살자가 원하지 않는 이메일의 자격은 필터링 및 채점 규칙에 전적으로 따라 결정됩니다. 따라서 SpamCharacter 설치 및 Adobe Campaign와의 통합이 완벽한 기능을 갖추고 전송하기 전에 제품에 할당된 점수의 연관성을 보장하려면 이러한 규칙을 하루에 한 번 이상 업데이트해야 합니다. 이 업데이트는 SpamCharacter를 호스팅하는 서버 관리자의 책임입니다.

지원되는 최소 버전은 다음과 같습니다.**3.4**

SpamCharacter를 사용하려면 HTTP 인터넷 액세스(tcp/80)가 필요합니다.

SpamCharacter의 설치 및 구성 단계는 [Configuring SpamAssesser](../../installation/using/configuring-spamassassin.md)에 있습니다.
