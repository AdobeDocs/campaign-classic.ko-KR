---
product: campaign
title: Linux에서 캠페인 설치 사전 요구 사항
description: Linux에서 Campaign 설치의 전제 조건
feature: Installation, Instance Settings
badge-v7-prem: label="온프레미스/하이브리드 전용" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용됩니다"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: acbd2873-7b1c-4d81-bc62-cb1246c330af
source-git-commit: f032ed3bdc0b402c8281bc34e6cb29f3c575aaf9
workflow-type: tm+mt
source-wordcount: '829'
ht-degree: 0%

---

# Linux에 Campaign을 설치하기 위한 사전 요구 사항{#prerequisites-of-campaign-installation-in-linux}

## 소프트웨어 사전 요구 사항 {#software-prerequisites}

이 섹션에서는 Adobe Campaign을 설치하기 전에 필요한 사전 구성 단계에 대해 자세히 설명합니다.

Adobe Campaign 설치에 필요한 기술 및 소프트웨어 구성은 [호환성 매트릭스](../../rn/using/compatibility-matrix.md).

다시 말해서 다음 구성 요소를 설치하고 올바르게 구성해야 합니다.

* Apache는 을 참조하십시오. [호환성 매트릭스](../../rn/using/compatibility-matrix.md),
* Java JDK 및 OpenJDK는 다음을 참조하십시오. [Java 개발 키트 - JDK](../../installation/using/application-server.md#jdk),
* 라이브러리는 을 참조하십시오. [라이브러리](#libraries),
* 데이터베이스 액세스 계층은 다음을 참조하십시오. [데이터베이스 액세스 계층](#database-access-layers),
* LibreOffice에서 다음을 참조하십시오. [LibreOffice for Debian 설치](#installing-libreoffice-for-debian) 및 [CentOS용 LibreOffice 설치](#installing-libreoffice-for-centos),
* 글꼴은 을 참조하십시오. [MTA 통계용 글꼴](#fonts-for-mta-statistics) 및 [일본어 인스턴스용 글꼴](#fonts-for-japanese-instances).


### 라이브러리 {#libraries}

Linux에 Adobe Campaign을 설치하려면 필요한 라이브러리가 있는지 확인하십시오.

* 라이브러리 C는 TLS(스레드 로컬 저장소) 모드를 지원할 수 있어야 합니다. 이 모드는 Xen 지원이 비활성화된 일부 커널을 제외하고는 대부분의 경우에 활성화됩니다.

  이를 확인하려면 예를 들어 uname -a | grep xen **명령을 사용할**&#x200B;수 있습니다.

  명령이 빈 줄을 반환하지 않으면 구성이 올바르다는 의미입니다.

* OpenSSL 버전이 있어야 합니다. **1.0.2** 또는 그 이상

  RHEL 배포의 경우 OpenSSL 버전 1.0이 필요합니다.

* Adobe Campaign을 사용하려면 다음을 수행해야 합니다. **리비쿠** 라이브러리가 설치되었습니다.

### SELinux {#selinux}

사용하는 경우 SELinux 모듈 모듈을 올바르게 구성해야 합니다.

이렇게 하려면 root로 로그온하고 다음 명령을 입력합니다.

```
echo 0 >/selinux/enforce
```

이 외에도 **/etc/sysconfig/httpd** Adobe Campaign 환경 구성 스크립트를 참조하기 위해 다음 줄을 추가했습니다.

```
. ~neolane/nl6/env.sh
```

RHEL 및 CentOS에서는 SELinux가 활성화되면 데이터베이스의 클라이언트 계층에 호환성 문제가 발생합니다. Adobe Campaign이 올바르게 작동할 수 있도록 SELinux를 비활성화하는 것이 좋습니다.

**다음 프로세스를 적용합니다.**

* 파일 편집 **/etc/selinux/config**

* 다음과 같이 SELINUX 줄을 수정합니다.

```
SELINUX=disabled
```

### MTA 통계용 글꼴 {#fonts-for-mta-statistics}

MTA 통계(nms/fra/jsp/stat.jsp)에 대한 보고서가 올바르게 표시되도록 하려면 글꼴을 추가합니다.

Debian에서 다음 명령을 추가합니다.

```
apt install xfonts-base xfonts-75dpi ttf-bitstream-vera ttf-dejavu
```

RHEL에 대해 다음 명령을 사용합니다.

```
dnf install xorg-x11-fonts-misc xorg-x11-fonts-75dpi dejavu-lgc-sans-fonts  dejavu-sans-fonts dejavu-sans-mono-fonts dejavu-serif-fonts
```

### 일본어 인스턴스용 글꼴 {#fonts-for-japanese-instances}

보고서를 PDF 포맷로 내보내려면 일본어 인스턴스에 특정 문자 글꼴이 필요합니다.

Debian에서 다음 명령을 추가합니다.

```
apt install fonts-ipafont
```

RHEL의 경우 다음 명령을 추가합니다.

```
dnf install epel-release # if required
dnf install vlgothic-fonts
```

### LibreOffice for Debian 설치 {#installing-libreoffice-for-debian}

Debian의 경우 다음 구성이 필요합니다.

1. 다음 표준 패키지를 설치합니다.

   ```
   apt-get install libreoffice-writer libreoffice-calc libreoffice-java-common
   ```

1. 다음 글꼴을 설치합니다(선택 사항이지만 일본어 인스턴스에 적극 권장됨).

   ```
   apt-get install fonts-ipafont
   ```

### CentOS용 LibreOffice 설치 {#installing-libreoffice-for-centos}

CentOS에는 다음 구성이 필요합니다.

```
yum install libreoffice-headless libreoffice-writer libreoffice-calc
```

## 데이터베이스 액세스 계층 {#database-access-layers}

사용 중인 데이터베이스 엔진에 대한 액세스 계층은 서버에 설치되어 있어야 하며 Adobe Campaign 계정 통해 액세스할 수 있어야 합니다. 버전 및 설치 모드는 사용되는 데이터베이스 엔진에 따라 달라질 수 있습니다.

지원되는 파일럿 버전은 다음에 자세히 설명되어 있습니다 [호환성 매트릭스](../../rn/using/compatibility-matrix.md).

일반 항목도 확인합니다. [데이터베이스](../../installation/using/database.md) 섹션.

### PostgreSQL {#postgresql}

Adobe Campaign은 버전 9.6의 모든 PostgreSQL 클라이언트 라이브러리 버전을 지원합니다. **libpq.so.5**.

Adobe Campaign과 함께 PostgreSQL을 사용하려면 해당 을 설치해야 합니다 **흑단 암호** 라이브러리.

### Oracle {#oracle}

64비트 Debian의 라이브러리 버전(예 **: libclntsh.so**, **libclntsh.so.19.1**, **libclntsh.so.18.1**, **libclntsh.so.12.1**, **libclntsh.so.11.1** 또는 **libclntsh.so.10.1**)을 검색합니다.

Oracle Technology Network에서 Linux RPM 패키지를 얻을 수 있습니다.

>[!NOTE]
>
>Oracle 클라이언트를 이미 설치했지만 전역 환경(인스턴스: /etc/profile)이 제대로 구성되지 않은 경우 nl6/customer.sh 스크립트에 **누락된 정보를 추가할 수 있습니다](../../installation/using/installing-packages-with-linux.md#environment-variables) 자세한 내용은 환경 변수를 참조하십시오[.**

**문제 해결 및 우수 사례**

oracle 클라이언트 또는 서버 업데이트, 버전 변경 또는 인스턴스의 첫 번째 설치 후에 문제가 나타날 수 있습니다.

클라이언트 콘솔에서 로그, 워크플로우 마지막 처리, 다음 처리 등에 예기치 않은 시간 지연(1시간 이상)이 있는 것을 발견하면 Oracle 클라이언트의 라이브러리와 Oracle 서버 간에 문제가 발생할 수 있습니다. 이러한 문제를 방지하려면

1. 다음을 사용하십시오. **전체 클라이언트**.

   Oracle Instant Client 버전을 사용할 때 다양한 문제가 확인되었습니다. 또한 인스턴트 클라이언트에서 시간대 파일을 변경할 수 없습니다.

1. 클라이언트 버전&#x200B;**과 데이터베이스 서버 버전이** **동일**&#x200B;한지 ****&#x200B;확인합니다.

   oracle의 호환성 매트릭스와 권장 사항에도 불구하고 버전을 혼합하여 클라이언트 및 서버 버전을 맞추면 문제가 발생하는 것으로 알려져 있습니다.

   또한 ORACLE_HOME 값을 확인하여 예상되는 클라이언트 버전(컴퓨터에 여러 버전이 설치된 경우)을 가리키는지 확인합니다.

1. 클라이언트와 서버가 동일한 것을 사용하도록 하십시오. **시간대 파일**.

## 구현 단계 {#implementation-steps}

Linux용 Adobe Campaign 설치는 서버 설치 후 인스턴스 구성의 순서로 수행해야 합니다.

설치 프로세스는 이 장에 설명되어 있습니다. 설치 단계는 다음과 같습니다.

* 1단계: 응용 프로그램 서버 설치 [Linux를 사용하여 패키지 설치](../../installation/using/installing-packages-with-linux.md).
* 2단계: 웹 서버와 통합(배포된 구성 요소에 따라 선택 사항)

설치 단계가 완료되면 인스턴스, 데이터베이스 및 서버를 구성해야 합니다. 자세한 내용은 다음을 참조하십시오. [초기 구성 정보](../../installation/using/about-initial-configuration.md).
