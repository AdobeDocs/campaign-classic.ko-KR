---
title: 애플리케이션 서버
seo-title: 애플리케이션 서버
description: 애플리케이션 서버
seo-description: null
page-status-flag: never-activated
uuid: 837c6a5c-53a4-4d1b-a084-9cf77e7a0eee
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
discoiquuid: 7a9e028c-255d-4aad-9827-d19f9a7897b2
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: de04b5d3ceb883a571ee665f630be931a68a5a3e

---


# 애플리케이션 서버{#application-server}

필요한 데이터베이스 액세스 레이어는 서버에 설치되어 있어야 하며 Adobe Campaign 계정에서 액세스할 수 있어야 합니다.

## Java 개발 키트 - JDK {#java-development-kit---jdk}

동적 웹 페이지 생성기는 JSP 1.2 기술을 사용합니다. 이를 위해 Apache의 Tomcat 엔진이 애플리케이션에 포함됩니다. Adobe Campaign 애플리케이션이 설치된 모든 서버에 JDK(Java Development Kit)가 설치되어 있어야 합니다.

Adobe Campaign 응용 프로그램 서버(**nlserver 웹** 프로세스)를 실행할 컴퓨터에 JDK를 먼저 설치해야 합니다. 이 JDK는 서블릿 컨테이너인 Apache Tomcat을 통합하여 동적 웹 페이지(보고서, 웹 양식 등)를 생성하므로 이를 통합해야 합니다.

애플리케이션은 Oracle에서 개발한 JDK(Java Development Kit)와 OpenJDK용으로 **승인되었습니다**.

지원되는 버전은 호환성 매트릭스에 [자세히 설명되어 있습니다](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).

>[!NOTE]
>
>시스템의 다른 응용 프로그램에서 이미 사용한 적절한 JDK 버전을 사용하여 설치할 수 있습니다.
>  
>설치할 때 웹 브라우저와의 통합을 수행할 필요는 없습니다.
>
>배달 에이전트(**nlserver mta** 프로세스) 또는 워크플로 서버(**nlserver wfserver 프로세스)만 실행하는 컴퓨터에서는 JDK를** 설치할 필요가 없습니다.

Java JDK 파섹https://www.oracle.com/technetwork/java/javase/downloads/index.html [](https://www.oracle.com/technetwork/java/javase/downloads/index.html).

**경고:jre가 아닌 JDK를 다운로드해야 합니다.**

>[!CAUTION]
>
>플랫폼 작업 성능을 유지하고 설치된 버전과의 호환성을 보장하려면 Windows 및 Linux에서 자동 JDK 업데이트 기능을 비활성화해야 합니다.

Linux 환경에서 JDSL을 설치하려면 패키지 관리자를 사용하는 것이 좋습니다.

Debian 8 및 9에서는 다음 명령을 사용합니다.

```
aptitude install openjdk-8-jdk
```

RHEL 7의 경우 다음 명령을 사용합니다.

```
yum install java-1.8.0-openjdk
```

## OpenSSL {#openssl}

Linux에서는 OpenSSL을 설치해야 합니다. Adobe Campaign에서 지원하는 버전은 **OpenSSL 1.0.1** 및 **OpenSSL 0.9.8입니다**. 하위 버전 0.9.8g ~ 0.9.8o가 허용됩니다.

## 보고서 내보내기 {#exporting-reports}

Adobe Campaign을 사용하면 플랫폼 보고서를 Microsoft Excel 및 Adobe PDF 형식으로 내보낼 수 있습니다. Microsoft Excel 포맷의 경우 Adobe Campaign은 LibreOffice를 **사용합니다**. Adobe PDF 포맷의 경우 Adobe Campaign은 PhantomJS **변환기를** 사용합니다. PhantomJs는 팩토리 패키지에 포함되며 Adobe Campaign 애플리케이션 서버가 실행되는 시스템(**nlserver 웹** 프로세스)에 LibreOffice가 설치되어 있어야 합니다.

>[!NOTE]
>
>Linux의 경우 글꼴을 추가해야 합니다. 자세한 내용은 MTA 통계를 [위한 글꼴을 참조하십시오](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics).

## SpamAsser {#spamassassin}

SpamCharacter를 사용하면 수신에 사용되는 스팸 방지 도구에서 메시지 위험을 원하지 않는 것으로 간주할지 여부를 결정하기 위해 이메일에 점수를 할당할 수 있습니다. 설치는 선택 사항입니다.

SpamCharacter에서 원하지 않는 이메일의 자격은 필터링 및 점수 규칙에 전적으로 따라 결정됩니다. 따라서 SpamCharacter 설치 및 Adobe Campaign과의 통합이 완전히 기능하고 보내기 전에 게시에 할당된 점수의 연관성을 보장하기 위해 이러한 규칙을 하루에 최소 한 번 업데이트해야 합니다. 이 업데이트는 SpamCharacter를 호스팅하는 서버 관리자의 책임입니다.

지원되는 최소 버전은 다음과 같습니다. **3.4**

SpamAssist는 HTTP 인터넷 액세스(tcp/80)가 필요합니다.

SpamCharacter의 설치 및 구성 단계는 Configuring SpamCharacter에 [나와 있습니다](../../installation/using/configuring-spamassassin.md).
