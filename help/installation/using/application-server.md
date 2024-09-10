---
product: campaign
title: 애플리케이션 서버
description: 애플리케이션 서버
feature: Installation
badge-v7-prem: label="온-프레미스/하이브리드만" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 87103c31-1530-4f8d-ab3a-6ff73093b80c
source-git-commit: 7906e9fee164d731659bbb9f96394faca5961240
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 1%

---

# 애플리케이션 서버{#application-server}

필요한 데이터베이스 액세스 계층은 서버에 설치되어 있고 Adobe Campaign 계정에서 액세스할 수 있어야 합니다.

## Java 개발 키트 - JDK {#jdk}

Java 개발 키트(JDK)는 소프트웨어 개발 키트입니다. Java 애플리케이션 및 Java 애플릿 개발을 가능하게 하는 기본 구성 요소입니다.

동적 웹 페이지 생성기는 JSP 기술을 사용합니다. 이를 위해 Tomcat 엔진(Apache의)이 애플리케이션에 포함됩니다. Adobe Campaign 애플리케이션이 설치된 모든 서버에 JDK(Java Development Kit)가 설치되어 있어야 합니다.

동적 웹 페이지(보고서, 웹 양식 등)를 생성하는 데 사용되는 서블릿 컨테이너인 Apache Tomcat이 통합되어 있으므로 먼저 Adobe Campaign 애플리케이션 서버(**nlserver web** 프로세스)를 실행할 컴퓨터에 JDK를 설치해야 합니다.

응용 프로그램이 **OpenJDK**&#x200B;뿐만 아니라 Oracle에서 개발한 JDK(Java Development Kit)에 대해 승인되었습니다.

지원되는 버전은 Campaign [호환성 매트릭스](../../rn/using/compatibility-matrix.md)에 자세히 설명되어 있습니다.


>[!AVAILABILITY]
>
>* v7.4.1부터 Campaign에는 Java JDK 11 이상이 필요합니다. Campaign 서버가 Windows 환경에 설치된 경우 기본적으로 더 이상 제공되지 않으므로 JRE를 생성해야 합니다. Java 런타임 DLL(jvm.dll)을 찾으려면 JRE_HOME 환경 변수가 필요합니다.
>
>* v7.4.1부터 Tomcat 10.1이 기본 버전입니다.
>

### 권장 사항

Java 개발 키트를 설치하고 업그레이드할 때 다음 권장 사항을 적용하십시오.

* 시스템의 다른 애플리케이션에서 이미 사용하고 있는 적절한 JDK 버전을 사용하여 Java 개발 키트를 설치할 수 있습니다.

* JDK를 설치할 때 웹 브라우저와의 통합이 필요하지 않습니다.

* 게재 에이전트(**nlserver mta** 프로세스) 또는 워크플로 서버(**nlserver wfserver** 프로세스)만 실행하는 컴퓨터에서는 JDK를 설치할 필요가 없습니다.

* Java 버전을 업그레이드할 때 먼저 이전 버전을 제거해야 합니다. 동일한 컴퓨터에 설치된 두 Java 버전이 충돌할 수 있습니다.

  온-프레미스 고객은 `LD_LIBRARY_PATH` [환경 변수](installing-packages-with-linux.md#environment-variables)가 최신 버전으로 설정되어 있는지 확인할 수 있습니다(예: java11). 이전 버전으로 설정된 경우(예: Java8)로 업데이트해야 합니다. JDK 11의 경우 JDK 라이브러리를 찾는 경로는 `/usr/lib/jvm/java-11-openjdk-amd64/lib`입니다.


### 설치 단계

Java Development Kit는 플랫폼에 따라 다릅니다. 각 운영 체제에 대해 별도의 설치 관리자가 필요합니다.

JDK를 다운로드하려면 [Oracle 웹 사이트](https://www.oracle.com/technetwork/java/javase/downloads/index.html){target="_blank"}에 연결하세요.

>[!CAUTION]
>
> JRE(Java Runtime Environment)가 아닌 JDK(Java Development Kit)를 다운로드해야 합니다.


Adobe Linux 환경에 JDSL을 설치하려면 패키지 관리자를 사용하는 것이 좋습니다.

Debian의 경우 다음 명령을 사용합니다.

```sql
apt install openjdk-11-jdk-headless
```

RHEL의 경우 다음 명령을 사용합니다.

```sql
dnf install java-11-openjdk-headless
```



## 보고서 내보내기 {#exporting-reports}

Adobe Campaign을 사용하여 보고서를 Microsoft Excel 및 Adobe PDF으로 내보낼 수 있습니다.

* Microsoft Excel 형식의 경우 Adobe Campaign은 **LibreOffice**&#x200B;를 사용합니다.

* Adobe PDF 형식의 경우 Adobe Campaign은 **PhantomJS** 변환기를 사용합니다. PhantomJs는 팩토리 패키지에 포함되어 있으며 LibreOffice는 Adobe Campaign 응용 프로그램 서버가 실행되는 컴퓨터(**nlserver web** 프로세스)에 설치되어 있어야 합니다.

>[!NOTE]
>
>Linux의 경우 글꼴을 추가해야 합니다. 자세한 내용은 [MTA 통계를 위한 글꼴](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics)을 참조하세요.

## SpamAssassin {#spamassassin}

SpamAssassin을 사용하면 이메일에 점수를 할당하여 수신 시 사용되는 스팸 방지 도구에서 바람직하지 않은 것으로 간주하는 메시지가 있는지 여부를 확인할 수 있습니다. 설치는 선택 사항입니다.

SpamAssassin에서 원하지 않는 이메일 자격은 전적으로 필터링 및 채점 규칙에 기반합니다. 따라서 SpamAssassin 설치 및 Adobe Campaign과의 통합이 완전히 작동하고 전송하기 전에 게재에 할당된 점수의 관련성을 보장하려면 이러한 규칙을 하루에 한 번 이상 업데이트해야 합니다. 이 업데이트는 SpamAssassin을 호스팅하는 서버 관리자의 책임입니다.

지원되는 최소 버전은 **3.4**&#x200B;입니다.

SpamAssassin에는 HTTP 인터넷 액세스(tcp/80)가 필요합니다.

SpamAssassin의 설치 및 구성 단계는 [SpamAssassin 구성](../../installation/using/configuring-spamassassin.md)에 표시됩니다.
