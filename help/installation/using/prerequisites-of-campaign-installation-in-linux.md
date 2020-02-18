---
title: Linux에서 캠페인 설치 사전 요구 사항
seo-title: Linux에서 캠페인 설치 사전 요구 사항
description: Linux에서 캠페인 설치 사전 요구 사항
seo-description: null
page-status-flag: never-activated
uuid: 65c7af3f-ca1d-4255-b54a-6a3c83af40ae
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
discoiquuid: 3e2ccb70-6c0c-435f-9c06-f3e5e40367bb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: de04b5d3ceb883a571ee665f630be931a68a5a3e

---


# Linux에서 캠페인 설치 사전 요구 사항{#prerequisites-of-campaign-installation-in-linux}

## 소프트웨어 사전 요구 사항 {#software-prerequisites}

이 섹션에서는 Adobe Campaign을 설치하기 전에 필요한 예비 구성 단계에 대해 자세히 설명합니다.

Adobe Campaign을 설치하는 데 필요한 기술 및 소프트웨어 구성은 호환성 [매트릭스에](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)설명되어 있습니다.

다음 구성 요소를 설치하고 올바르게 구성해야 합니다.

* Apache, 호환성 [매트릭스](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html),
* Java JDK 및 OpenJDK는 Java [Development Kit - JDK](../../installation/using/application-server.md#java-development-kit---jdk),
* 라이브러리, 라이브러리 [참조](#libraries),
* 데이터베이스 액세스 레이어는 데이터베이스 [액세스 레이어를](#database-access-layers)참조하십시오.
* LibreOffice의 경우 Debian용 [LibreOffice 설치](#installing-libreoffice-for-debian) 및 [LibreOffice for CentOS](#installing-libreoffice-for-centos),
* 글꼴은 MTA [통계를](#fonts-for-mta-statistics) 위한 글꼴 및 일본어 [인스턴스를](#fonts-for-japanese-instances)참조하십시오.

>[!NOTE]
>
>CentOS 7 및 Debian 8 플랫폼에 8709보다 작거나 같은 빌드를 설치하려면 apache access_compat 모듈이 활성화되어 있어야 합니다.

### 라이브러리 {#libraries}

Linux에서 Adobe Campaign을 설치하려면 필요한 라이브러리가 있어야 합니다.

* 라이브러리 C는 TLS(스레드 로컬 저장소) 모드를 지원할 수 있어야 합니다. 이 모드는 Xen 지원이 비활성화된 일부 커널을 제외한 대부분의 경우 활성화됩니다.

   이를 확인하려면 **uname -a| grep xen** 명령(예:

   명령이 아무 것도 반환하지 않으면(빈 행) 구성이 올바르다는 것을 의미합니다.

* OpenSSL의 **버전은 0.9.8** 또는 **1.0** 이어야합니다.

   RHEL 7 배포의 경우 OpenSSL 버전 1.0이 필요합니다.

* Adobe Campaign을 사용하려면 **라이브러리** 라이브러리가 설치되어 있어야 합니다.

   다음 버전의 **libicu** (32비트 또는 64비트)가 지원됩니다.

   * RHEL 7, CentOS 7:libicu50
   * 데비안 8:libicu52
   * 데비안 9:libicu57
   Adobe Campaign을 사용하려면 libc-ares 라이브러리가 설치되어 있어야 합니다. RHEL/CentOS에서 다음 명령을 실행합니다.

   ```
   yum install c-ares
   ```

   데비안:

   ```
   aptitude install libc-ares2
   ```

### SELinux {#selinux}

SELinux 모듈을 사용할 경우 SELinux 모듈이 제대로 구성되어야 합니다.

이렇게 하려면 루트로 로그온하고 다음 명령을 입력합니다.

```
echo 0 >/selinux/enforce
```

또한 **/etc/sysconfig/httpd** 파일에서 Adobe Campaign 환경 구성 스크립트를 참조하기 위해 다음 줄이 추가되었습니다.

```
. ~neolane/nl6/env.sh
```

RHEL 및 CentOS에서는 SELinux가 활성화되면 데이터베이스 클라이언트 레이어의 호환성 문제가 명시되었습니다. Adobe Campaign이 제대로 작동하는지 확인하려면 SELinux를 비활성화하는 것이 좋습니다.

**다음 프로세스를 적용합니다.**

* 파일 편집 **/etc/selecux/config**

* 다음과 같이 SELINUX 라인을 수정합니다.

```
SELINUX=disabled
```

### MTA 통계를 위한 글꼴 {#fonts-for-mta-statistics}

MTA 통계 보고서(nms/fra/jsp/stat.jsp)가 올바로 표시되도록 하려면 글꼴을 추가합니다.

Debian에서 명령을 추가합니다.

```
aptitude install xfonts-base xfonts-75dpi ttf-bitstream-vera ttf-dejavu
```

Redhat에서 다음 명령을 사용합니다.

```
yum install xorg-x11-fonts-base xorg-x11-fonts-75dpi bitstream-vera-fonts dejavu-lgc-fonts
```

### 일본어 인스턴스용 글꼴 {#fonts-for-japanese-instances}

보고서를 PDF 형식으로 내보내려면 일본어 인스턴스에서 특정 문자의 글꼴이 필요합니다.

Debian에서 명령을 추가합니다.

```
aptitude install fonts-ipafont
```

Red Hat에서 명령을 추가합니다.

```
yum install ipa-gothic-fonts ipa-mincho-fonts
```

### Debian용 LibreOffice 설치 {#installing-libreoffice-for-debian}

Debian의 경우 다음 구성이 필요합니다.

1. 다음 표준 패키지를 설치합니다.

   ```
   apt-get install libreoffice-writer libreoffice-calc libreoffice-java-common
   ```

1. 다음 글꼴을 설치합니다(선택 사항이지만 일본어 인스턴스에는 권장됨).

   ```
   apt-get install fonts-ipafont
   ```

### CentOS용 LibreOffice 설치 {#installing-libreoffice-for-centos}

CentOS에서는 다음 구성이 필요합니다.

1. 다음 표준 패키지를 설치합니다.

   ```
   yum install libreoffice-headless libreoffice-writer libreoffice-calc
   ```

1. 다음 글꼴을 설치합니다(선택 사항이지만 일본어 인스턴스에는 권장됨).

   ```
   yum install ipa-gothic-fonts ipa-mincho-fonts
   ```

## 데이터베이스 액세스 레이어 {#database-access-layers}

사용 중인 데이터베이스 엔진의 액세스 레이어는 서버에 설치되어 있어야 하며 Adobe Campaign 계정을 통해 액세스할 수 있어야 합니다. 버전 및 설치 모드는 사용된 데이터베이스 엔진에 따라 다를 수 있습니다.

지원되는 파일럿 버전은 호환성 매트릭스에 [자세히 설명되어 있습니다](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).

일반 데이터베이스 [섹션도](../../installation/using/database.md) 확인합니다.

### PostgreSQL {#postgresql}

Adobe Campaign은 버전 7.2에서 모든 버전의 PostgreSQL 클라이언트 라이브러리를 지원합니다.(**pq.so.5**, **libpq.so.4**, **libpq.so.3.2** 및 **** libpq libpq.so.3.16).

Adobe Campaign과 함께 PostgreSQL을 사용하려면 해당 **pgcrypto 라이브러리를 설치해야** 합니다.

### Oracle {#oracle}

64비트 Debian용 라이브러리 버전 검색(예: **libclntsh.so**, **libclntsh.so.11.1** 및 **libclntsh.so.10.1**.

Oracle 기술 네트워크에서 Linux RPM 패키지를 얻을 수 있습니다.

>[!NOTE]
>
>Oracle 클라이언트를 이미 설치했지만 글로벌 환경(예:/etc/profile)이 제대로 구성되지 않은 경우 nl6/customer.sh **스크립트에** 누락된 정보를 추가할 수 있습니다. 자세한 내용은 환경 변수를 [참조하십시오](../../installation/using/installing-packages-with-linux.md#environment-variables).

**문제 해결 및 우수 사례**

Oracle 클라이언트 또는 서버 업데이트, 버전 변경 또는 인스턴스의 첫 번째 설치 후에 문제가 나타날 수 있습니다.

클라이언트 콘솔에서 로그, 워크플로우 마지막 처리, 다음 처리 등에 예기치 않은 시간 경과(1시간 이상)가 발생하는 경우 Oracle 클라이언트의 라이브러리와 Oracle Server 사이에 문제가 있을 수 있습니다. 이러한 문제를 피하려면

1. 반드시 **전체 클라이언트를**&#x200B;사용하십시오.

   Oracle Instant Client 버전을 사용할 때 다양한 문제가 발견되었습니다. 또한 인스턴트 클라이언트에서 표준 시간대 파일을 변경할 수 없습니다.

1. **클라이언트 버전과** **데이터베이스 서버 버전이** **동일한지 확인합니다**.

   Oracle의 호환성 매트릭스와 클라이언트 및 서버 버전을 정렬하기 위한 권장 사항에도 불구하고 버전을 혼합하면 문제가 발생하는 것으로 알려져 있습니다.

   또한 ORACLE_HOME 값이 예상 클라이언트 버전을 가리키는지 확인하십시오(시스템에 여러 버전이 설치된 경우).

1. 클라이언트와 서버가 동일한 **표준 시간대 파일을**&#x200B;사용하는지 확인합니다.

### DB2 {#db2}

지원되는 라이브러리 버전은 **libdb2.so**.

## 구현 단계 {#implementation-steps}

Linux용 Adobe Campaign 설치는 다음 순서로 수행해야 합니다.서버 설치 후 인스턴스 구성을 따릅니다.

설치 프로세스는 이 장에 설명되어 있습니다. 설치 단계는 다음과 같습니다.

* 1단계:응용 프로그램 서버 설치는 Linux를 [사용하여 패키지 설치를 참조하십시오](../../installation/using/installing-packages-with-linux.md).
* 2단계:웹 서버와 통합(선택적, 배포된 구성 요소에 따라 다름).

설치 단계가 완료되면 인스턴스, 데이터베이스 및 서버를 구성해야 합니다. 자세한 내용은 초기 구성 [정보를 참조하십시오](../../installation/using/about-initial-configuration.md).
