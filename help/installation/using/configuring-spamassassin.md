---
product: campaign
title: SpamAssassin 구성
description: SpamAssassin 구성
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용됩니다."
badge-v7-prem: label="온-프레미스 및 하이브리드" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 1f1004e2-dcd2-4ec5-98ec-720c205646d5
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '1008'
ht-degree: 2%

---

# SpamAssassin 구성{#configuring-spamassassin}



>[!NOTE]
>
>일부 구성은 Adobe에서 호스팅하는 배포에 대해 Adobe에 의해서만 수행될 수 있습니다. 예를 들어 서버 및 인스턴스 구성 파일에 액세스합니다. 다양한 배포에 대한 자세한 내용은 [호스팅 모델](../../installation/using/hosting-models.md) 섹션 또는 종료 [이 페이지](../../installation/using/capability-matrix.md).

## 개요 {#overview}

SpamAssassin은 원치 않는 이메일을 필터링하도록 설계된 소프트웨어의 일부입니다. 이 소프트웨어와 함께 Adobe Campaign은 이메일에 점수를 할당하고 게재를 시작하기 전에 메시지가 바람직하지 않은 것으로 간주되는지 여부를 결정할 수 있습니다. 이를 위해서는 Adobe Campaign의 애플리케이션 서버에 SpamAssassin을 설치 및 구성해야 하며, 작동하려면 일정 수의 추가 Perl 모듈이 필요합니다.

이 장에 설명된 SpamAssassin의 배포 및 통합은 기본 소프트웨어 설치와 필터링 및 채점 규칙을 기반으로 하며, 이는 변경 또는 최적화 없이 SpamAssassin에서 제공하는 규칙입니다. 스코어 속성 및 메시지 자격은 SpamAssassin 옵션의 구성 및 필터링 규칙을 기반으로 합니다. 네트워크 관리자는 회사의 필요에 맞게 이를 조정할 책임이 있습니다.

>[!IMPORTANT]
>
>SpamAssassin에서 원하지 않는 이메일 자격은 전적으로 필터링 및 채점 규칙에 기반합니다.
>
>따라서 SpamAssassin 설치 및 Adobe Campaign과의 통합이 완전히 작동하고 전송하기 전에 게재에 할당된 점수의 관련성을 보장하려면 이러한 규칙을 하루에 한 번 이상 업데이트해야 합니다.
>
>이 업데이트는 SpamAssassin을 호스팅하는 서버 관리자의 책임입니다.

Adobe Campaign에서 SpamAssassin을 사용하면 Adobe Campaign에서 보낸 이메일을 받을 때 SpamAssassin을 사용하는 메일 서버의 가능한 동작에 대한 표시를 제공합니다. 그러나 인터넷 공급자나 온라인 메일 서버의 메일 서버는 여전히 Adobe Campaign이 보낸 메시지를 바람직하지 않은 것으로 간주할 수 있습니다.

Perl에 SpamAssassin 및 해당 모듈을 배포하려면 HTTP 연결(TCP/80 흐름)을 통한 인터넷 액세스가 제공되는 Adobe Campaign 애플리케이션 서버가 필요합니다.

## Windows 시스템에 설치 {#installing-on-a-windows-machine}

Adobe Campaign과의 통합을 활성화하기 위해 Windows에서 SpamAssassin을 설치하고 구성하려면 다음 단계를 적용합니다.

1. SpamAssassin 설치
1. Adobe Campaign에 SpamAssassin 통합

### SpamAssassin 설치 {#installing-spamassassin}

1. 에 연결 [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/ko/campaign.html) 사용자 자격 증명을 사용합니다. 에서 소프트웨어 배포에 대해 자세히 알아보기 [이 페이지](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=ko).
1. 다운로드 **Neolane Spam Assassin(Windows 설치)(2.0)** 파일(neolane_spamassassin.2.0.zip).
1. 이 파일을 Adobe Campaign 서버에 복사한 다음 압축을 풉니다.

   >[!NOTE]
   >
   >경로가 다음 정규 표현식 문자 중 하나로 구성되는 경우 원하는 위치에 파일의 압축을 풀 수 있습니다. **`-_A-Za-z\xA0-\xFF0-9\.\%\@\=\+\,\/\\\:.`**. 설치 경로에는 공백 문자를 사용할 수 없습니다.

1. 파일의 압축을 푼 파일로 이동한 다음 **run_me.bat** 설치 스크립트를 실행할 파일입니다.

   Windows 셸이 나타나고 몇 초 동안 계속 표시되는 경우 설치 및 업데이트가 완료될 때까지 기다린 다음 을 클릭합니다. **입력**.

   Windows 셸이 나타나지 않거나 즉시 사라지기 전에 표시되지 않는 경우 다음 단계를 따라 다음을 두 번 클릭합니다. **portableShell.bat** Windows 셸을 표시하고 셸 경로가 **spamassassin.zip** 파일의 압축이 풀렸습니다. 그렇지 않은 경우 **cd** 명령입니다.

   입력 **run_me.bat** 그런 다음 을 클릭합니다. **입력** 설치 및 업데이트 프로세스를 시작합니다. 이 작업에서는 업데이트 결과를 표시하기 위해 다음 값 중 하나를 반환합니다.

   * **0**: 업데이트가 수행되었습니다.
   * **1**: 사용 가능한 새 업데이트가 없습니다.
   * **2**: 사용 가능한 새 업데이트가 없습니다.
   * **3**: 이전 확인 중에 업데이트하지 못했습니다.
   * **4** 이상: 오류가 발생했습니다.

1. SpamAssassin 설치가 성공했는지 확인하려면 다음 절차를 사용하여 GTUBE 테스트(요청하지 않은 대량 이메일에 대한 일반 테스트)를 사용합니다.

   1. 텍스트 파일을 만들고 아래에 저장합니다. **C:\TestSpamMail.txt**.
   1. 파일에 다음 내용을 삽입합니다.

      ```
      Subject: Test Spam Mail (GTUBE)
      Message-ID: <1010101@example.net>
      Date: MM-DD-YY
      From: Sender <sender@example.net>
      To: Recipient <recipient@example.net>
      Precedence: junk
      MIME-Version: 1.0
      Content-Type: text/plain; charset=us-ascii
      Content-Transfer-Encoding: 7bit
      
      XJS*C4JDBQADN1.NSBN3*2IDNEN*GTUBE-STANDARD-ANTI-UBE-TEST-EMAIL*C.34X
      ```

   1. 를 두 번 클릭합니다. **portableShell.bat** Windows 셸을 표시하는 파일 또는 &quot;`<root>`의 압축을 풀 때 생성된 폴더를 지정합니다.  **spamassassin.zip** file):

      ```
       "<root>\perl\site\bin\spamassassin" "C:\TestSpamMail.txt"
      ```

      이 테스트 이메일의 콘텐츠는 SpamAssassin의 1,000점 점수를 트리거합니다. 즉, 바람직하지 않은 설치로 감지되었으며 설치가 성공적이고 정상적으로 작동하고 있음을 의미합니다.

### Adobe Campaign에 SpamAssassin 통합 {#integrating-spamassassin-into-adobe-campaign}

1. 편집 **`[INSTALL]/conf/serverConf.xml`** 파일. 에서 사용할 수 있는 모든 매개 변수 **serverConf.xml** 다음에 나열됨 [섹션](../../installation/using/the-server-configuration-file.md).
1. 값 변경 **스팸 확인** 요소 **명령** 의 속성 **웹** 노드. 이렇게 하려면 다음 명령을 실행합니다.

   ```
   <spamCheck command='"<absolute path to the folder where you unzipped the zip file>\call_perl_with_args.bat" "<absolute path to nlserver>/spamcheck.pl"'/>
   ```

   >[!NOTE]
   >
   >모든 경로는 절대 경로여야 합니다.

   중지 및 시작 **[!UICONTROL Adobe Campaign]** 서비스.

1. Adobe Campaign에서 SpamAssassin의 통합을 확인하려면 GTBUE 테스트(요청되지 않은 대량 이메일에 대한 일반 테스트)를 사용합니다.

   를 두 번 클릭합니다. **portableshelll.bat** 파일. Windows 셸 표시를 트리거합니다. 그런 다음 다음 다음 명령을 실행합니다.

   ```
   perl "[INSTALL]\bin\spamcheck.pl" "C:\TestSpamMail.txt"
   ```

   이 테스트 이메일의 콘텐츠는 SpamAssassin이 할당한 1,000포인트를 트리거합니다. 즉, 바람직하지 않은 것으로 감지되었으며 Adobe Campaign에서의 통합이 성공적이고 완전히 작동합니다.

1. SpamAssassin 필터링 및 채점 규칙 업데이트

   필터링 및 채점 규칙의 초기 업데이트를 보려면 다음을 시작하십시오. **portableShell.bat** 다음 명령을 실행합니다.

   ```
   sa-update --no-gpg
   ```

   필터링 및 채점 규칙의 자동 업데이트를 실행하려면 예약된 시스템 작업에서 이와 동일한 명령을 사용합니다.

   ```
   sa-update --no-gpg
   ```

## Linux 시스템에 설치 {#installing-on-a-linux-machine}

### Debian의 설치 단계 {#installation-steps-in-debian}

* 필요한 경우 다음 명령을 사용하여 Perl 및 SpamAssassin을 설치합니다.

  ```
  apt-get install spamassassin libxml-writer-perl
  ```

* 다음에서 **serverConf.xml** 파일(다음 위치에서 사용 가능) `/usr/local/[INSTALL]/nl6/conf/`), **스팸 확인** 다음과 같은 줄:

  ```
  <spamCheck command="perl
  /usr/local/[NSTALL]/nl6/bin/spamcheck.pl"/>
  ```

### RHEL/CentOS의 설치 단계 {#installation-steps-in-rhel-centos}

필요한 경우 Perl을 설치하고 CPAN을 사용하여 패키지를 복구합니다.

```
cpan Digest::SHA1
cpan HTML::Parser
cpan Net::DNS
cpan Mail::SPF 
cpan XML::LibXML
cpan XML::Writer
cpan Mail::SpamAssassin
```

### 필터 규칙 업데이트 {#updating-filter-rules}

필터 규칙은 다음을 사용하여 자동으로 업데이트할 수 있습니다 **sa-update** 도구. 공식 SpamAssassin 웹 사이트를 참조하십시오 [https://spamassassin.apache.org/](https://spamassassin.apache.org/) 추가 정보.

Debian에서는 매일 업데이트가 자동으로 수행됩니다.

그렇지 않은 경우(예: Debian을 수동으로 설치하는 경우) 규칙 업데이트를 자동화하는 스크립트를 만듭니다.

```
!/bin/sh
test -x /usr/bin/sa-update || exit 0
/usr/sbin/sa-update && /etc/init.d/spamassassin update
```

에 이 스크립트 삽입 **crontab** 다음 명령 사용:

```
crontab-e
```

### 성능 최적화 {#performance-optimization}

Linux의 성능을 향상시키려면 **/etc/spamassassin/local.cf** 을(를) 파일하고 파일 끝에 다음 줄을 추가합니다.

```
dns_available no
```
