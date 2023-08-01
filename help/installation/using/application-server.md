---
product: campaign
title: 애플리케이션 서버
description: 애플리케이션 서버
feature: Installation
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용됩니다."
badge-v7-prem: label="온-프레미스 및 하이브리드" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 87103c31-1530-4f8d-ab3a-6ff73093b80c
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 3%

---

# 애플리케이션 서버{#application-server}



필요한 데이터베이스 액세스 계층은 서버에 설치되어 있고 Adobe Campaign 계정에서 액세스할 수 있어야 합니다.

## Java 개발 키트 - JDK {#java-development-kit---jdk}

동적 웹 페이지 생성기는 JSP 1.2 기술을 사용합니다. 이를 위해 Tomcat 엔진(Apache의)이 애플리케이션에 포함됩니다. Adobe Campaign 애플리케이션이 설치된 모든 서버에 JDK(Java Development Kit)가 설치되어 있어야 합니다.

먼저 Adobe Campaign 애플리케이션 서버( )를 실행할 컴퓨터에 JDK를 설치해야 합니다.**nlserver 웹** 프로세스) 동적 웹 페이지(보고서, 웹 양식 등)를 생성하는 데 사용되는 서블릿 컨테이너인 Apache Tomcat이 통합되어 있습니다.

oracle에서 개발한 JDK(Java Development Kit)와 **오픈JDK**.

지원되는 버전은 Campaign에 자세히 설명되어 있습니다 [호환성 매트릭스](../../rn/using/compatibility-matrix.md).

>[!NOTE]
>
>시스템의 다른 애플리케이션에서 이미 사용하고 있는 적절한 JDK 버전을 사용하여 설치할 수 있습니다.
>  
>설치할 때 웹 브라우저와의 통합을 수행할 필요가 없습니다.
>
>게재 에이전트만 실행하는 컴퓨터(**nlserver mta** process) 또는 워크플로 서버(**nlserver wfserver** 프로세스), JDK 설치는 필요하지 않습니다.

Java JDK를 다운로드하려면 다음 위치에 연결하십시오. [https://www.oracle.com/technetwork/java/javase/downloads/index.html](https://www.oracle.com/technetwork/java/javase/downloads/index.html).

**경고: JRE가 아닌 JDK를 다운로드해야 합니다.**

>[!CAUTION]
>
>플랫폼 작업 성능을 유지하고 설치된 버전과의 호환성을 보장하려면 Windows 및 Linux에서 자동 JDK 업데이트 기능을 비활성화해야 합니다.

Linux 환경에 JDSL을 설치하려면 패키지 관리자를 사용하는 것이 좋습니다.

Debian 8 및 9에서 다음 명령을 사용합니다.

```
aptitude install openjdk-8-jdk
```

RHEL 7의 경우 다음 명령을 사용합니다.

```
yum install java-1.8.0-openjdk
```

## Openssl {#openssl}

Linux에서 OpenSSL을 설치해야 합니다. Adobe Campaign은 OpenSSL 버전 1.0.2 이상을 지원합니다.

## 보고서 내보내기 {#exporting-reports}

Adobe Campaign을 사용하면 플랫폼 보고서를 Microsoft Excel 및 Adobe PDF 형식으로 내보낼 수 있습니다. Microsoft Excel 형식의 경우 Adobe Campaign은 **LibreOffice**. Adobe PDF 형식의 경우 Adobe Campaign은 **팬텀JS** 변환기. PhantomJs는 팩토리 패키지에 포함되어 있으며 Adobe Campaign 애플리케이션 서버가 실행되는 컴퓨터에 LibreOffice가 설치되어 있어야 합니다(**nlserver 웹** 프로세스).

>[!NOTE]
>
>Linux의 경우 글꼴을 추가해야 합니다. 자세한 내용은 다음을 참조하십시오. [MTA 통계용 글꼴](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics).

## SpamAssassin {#spamassassin}

SpamAssassin을 사용하면 이메일에 점수를 할당하여 수신 시 사용되는 스팸 방지 도구에서 바람직하지 않은 것으로 간주하는 메시지가 있는지 여부를 확인할 수 있습니다. 설치는 선택 사항입니다.

SpamAssassin에서 원하지 않는 이메일 자격은 전적으로 필터링 및 채점 규칙에 기반합니다. 따라서 SpamAssassin 설치 및 Adobe Campaign과의 통합이 완전히 작동하고 전송하기 전에 게재에 할당된 점수의 관련성을 보장하려면 이러한 규칙을 하루에 한 번 이상 업데이트해야 합니다. 이 업데이트는 SpamAssassin을 호스팅하는 서버 관리자의 책임입니다.

지원되는 최소 버전은 다음과 같습니다. **3.4**

SpamAssassin에는 HTTP 인터넷 액세스(tcp/80)가 필요합니다.

SpamAssassin의 설치 및 구성 단계는 [SpamAssassin 구성](../../installation/using/configuring-spamassassin.md).
