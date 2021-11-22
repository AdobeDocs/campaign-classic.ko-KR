---
product: campaign
title: 애플리케이션 서버
description: 애플리케이션 서버
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 87103c31-1530-4f8d-ab3a-6ff73093b80c
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 1%

---

# 애플리케이션 서버{#application-server}

![](../../assets/v7-only.svg)

필요한 데이터베이스 액세스 계층은 서버에 설치하고 Adobe Campaign 계정에서 액세스할 수 있어야 합니다.

## Java 개발 키트 - JDK {#java-development-kit---jdk}

동적 웹 페이지 생성기는 JSP 1.2 기술을 사용합니다. 이를 위해 Apache의 Tomcat 엔진이 애플리케이션에 포함됩니다. Adobe Campaign 애플리케이션이 설치된 모든 서버에 JDK(Java Development Kit)가 설치되어 있어야 합니다.

먼저 Adobe Campaign 애플리케이션 서버(**nlserver 웹** process)를 결합하면 동적 웹 페이지(보고서, 웹 양식 등)를 생성하는 데 사용되는 서블릿 컨테이너 Apache Tomcat이 통합됩니다.

이 애플리케이션은 Oracle 뿐만 아니라 **OpenJDK**.

지원되는 버전은 Campaign에 자세히 설명되어 있습니다 [호환성 매트릭스](../../rn/using/compatibility-matrix.md).

>[!NOTE]
>
>시스템의 다른 애플리케이션에서 이미 사용하고 있는 적절한 JDK 버전을 사용하여 설치할 수 있습니다.
>  
>설치할 때 웹 브라우저와의 통합을 수행할 필요가 없습니다.
>
>게재 에이전트만 실행하는 시스템에서 (**nlserver mta** 프로세스) 또는 워크플로 서버(**nlserver wfserver** 프로세스), JDK를 설치할 필요가 없습니다.

Java JDK를 다운로드하려면 다음 항목에 연결합니다. [https://www.oracle.com/technetwork/java/javase/downloads/index.html](https://www.oracle.com/technetwork/java/javase/downloads/index.html).

**경고: JRE가 아닌 JDK를 다운로드해야 합니다.**

>[!CAUTION]
>
>플랫폼 작업 성능을 유지하고 설치된 버전과 호환되도록 하려면 Windows 및 Linux에서 자동 JDK 업데이트 기능을 비활성화해야 합니다.

Linux 환경에 JDSL을 설치하려면 패키지 관리자를 사용하는 것이 좋습니다.

Debian 8 및 9에서 다음 명령을 사용합니다.

```
aptitude install openjdk-8-jdk
```

RHEL 7의 경우 다음 명령을 사용합니다.

```
yum install java-1.8.0-openjdk
```

## OpenSSL {#openssl}

Linux에서 OpenSSL을 설치해야 합니다. Adobe Campaign에서 지원하는 버전은 다음과 같습니다 **OpenSSL 1.0.1** 및 **OpenSSL 0.9.8**. 하위 버전 0.9.8g~0.9.8o가 허용됩니다.

## 보고서 내보내기 {#exporting-reports}

Adobe Campaign을 사용하여 플랫폼 보고서를 Microsoft Excel 및 Adobe PDF 형식으로 내보낼 수 있습니다. Microsoft Excel 형식의 경우 Adobe Campaign에서는 **LibreOffice**. Adobe PDF 형식의 경우 Adobe Campaign에서는 **PhantomJS** 변환기. PhantomJs는 공장 패키지에 포함되어 있으며 LibreOffice는 Adobe Campaign 애플리케이션 서버가 실행되는 시스템( )에 설치되어 있어야 합니다.**nlserver 웹** 처리)할 수 있습니다.

>[!NOTE]
>
>Linux의 경우 글꼴을 추가해야 합니다. 자세한 내용은 [MTA 통계용 글꼴](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics).

## SpamAssassin {#spamassassin}

SpamAssassin을 사용하면 수신에 사용되는 스팸 방지 도구에 의해 원치 않는 메시지 위험으로 간주되는지 여부를 확인하기 위해 전자 메일에 점수를 할당할 수 있습니다. 설치는 선택 사항입니다.

SpamAssassin에서 원치 않는 전자 메일의 자격은 필터링 및 점수 규칙에 전적으로 따라 결정됩니다. 따라서 SpamAssassin 설치 및 Adobe Campaign와의 통합이 완벽한 기능을 유지하고 전송하기 전에 게재에 할당된 점수의 관련성을 보장하려면 하루에 최소 한 번 이상 이러한 규칙을 업데이트해야 합니다. 이 업데이트는 SpamAssassin을 호스팅하는 서버 관리자의 책임입니다.

지원되는 최소 버전은 다음과 같습니다. **3.4**

SpamAssassin에는 HTTP 인터넷 액세스(tcp/80)가 필요합니다.

SpamAssassin의 설치 및 구성 단계는 [SpamAssassin 구성](../../installation/using/configuring-spamassassin.md).
