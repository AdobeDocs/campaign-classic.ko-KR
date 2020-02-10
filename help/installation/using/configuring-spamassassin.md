---
title: SpamAsser 구성
seo-title: SpamAsser 구성
description: SpamAsser 구성
seo-description: null
page-status-flag: never-activated
uuid: 327548c0-d621-4417-9fc9-b0bf30251dc0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: aa37bdc6-0f85-4eca-859f-e8b15083cfb5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: edb99a13d8b2f39f991e8ceb6718291d92504242

---


# SpamAsser 구성{#configuring-spamassassin}

>[!NOTE]
>
>일부 구성은 Adobe가 호스팅하는 배포를 위해서만 수행할 수 있습니다. 예를 들어 서버 및 인스턴스 구성 파일에 액세스하려면 다른 배포에 대한 자세한 내용은 호스팅 모델 [섹션](../../installation/using/hosting-models.md) 또는 [이 문서를](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html)참조하십시오.

## 개요 {#overview}

SpamCharacter는 원하지 않는 이메일을 필터링하기 위해 고안된 소프트웨어입니다. 이 소프트웨어와 함께 Adobe Campaign은 이메일에 점수를 할당하고 메시지를 전달하기 전에 원치 않는 것으로 간주될 수 있는지 여부를 결정할 수 있습니다. 이렇게 하려면 Adobe Campaign의 응용 프로그램 서버에 SpamAsser를 설치하고 구성해야 하며 특정 수의 추가 Perl 모듈이 필요합니다.

이 장에서 설명한 바와 같이 SpamCharacter의 배포 및 통합은 필터링 및 채점 규칙과 같이 변경이나 최적화 없이 SpamCharacter에서 제공하는 기본 소프트웨어 설치를 기반으로 합니다. 점수 기여도 및 메시지 자격은 SpamAssist 옵션 구성 및 필터링 규칙에 기준합니다. 네트워크 관리자는 회사의 요구 사항에 맞게 조정할 책임이 있습니다.

>[!CAUTION]
>
>SpamCharacter에서 원하지 않는 이메일의 자격은 필터링 및 점수 규칙에 전적으로 따라 결정됩니다.
>
>따라서 SpamCharacter 설치 및 Adobe Campaign과의 통합이 완전히 기능하고 보내기 전에 게시에 할당된 점수의 연관성을 보장하기 위해 이러한 규칙을 하루에 최소 한 번 업데이트해야 합니다.
>
>이 업데이트는 SpamCharacter를 호스팅하는 서버 관리자의 책임입니다.

Adobe Campaign에서 SpamCharacter를 사용하면 Adobe Campaign에서 발송한 이메일을 수신할 때 SpamCharacter를 사용하는 메일 서버의 작동 가능성에 대한 표시를 제공합니다. 그러나 인터넷 공급자 또는 온라인 메일 서버의 메일 서버가 여전히 Adobe Campaign에서 보낸 메시지를 원하지 않는 것으로 간주할 수 있습니다.

Perl에서 SpamCharacter 및 해당 모듈을 배포하려면 HTTP 연결을 통한 인터넷 액세스 기능을 갖춘 Adobe Campaign 애플리케이션 서버가 필요합니다(TCP/80 흐름).

## Windows 시스템에 설치 {#installing-on-a-windows-machine}

Adobe Campaign과의 통합을 사용하도록 Windows에 SpamAsser를 설치하고 구성하려면 다음 단계를 수행하십시오.

1. SpamAsser 설치
1. Adobe Campaign에 스팸 분석 통합

### SpamAsser 설치 {#installing-spamassassin}

1. 사용자 자격 [증명을 사용하여 엑스트라넷 포털에](http://support.neolane.net) 연결합니다.
1. 다운로드 **센터로** 이동한 다음 페이지를 검색하여 도구 **섹션을 찾습니다** .
1. 스팸 **암살자(Windows 설치)(1.0)** 파일을 다운로드합니다.
1. 이 파일을 Adobe Campaign 서버에 복사한 다음 압축을 해제합니다.

   >[!NOTE]
   >
   >경로가 다음과 같은 정규 표현식 문자로 구성된 경우 원하는 위치에 있는 파일의 압축을 해제할 수 있습니다. **`-_A-Za-z\xA0-\xFF0-9\.\%\@\=\+\,\/\\\:.`** Adobe 설치 경로에는 공백 문자가 없어야 합니다.

1. 파일의 압축을 푼 파일로 이동한 다음 **run_me.bat** 파일을 두 번 클릭하여 설치 스크립트를 실행합니다.

   Windows 셸이 표시되고 몇 초 동안 계속 표시되는 경우 설치가 완료될 때까지 기다렸다가 Enter 키를 **클릭합니다**.

   Windows Shell이 바로 사라지기 전에 표시되지 않거나 표시되지 않는 경우 다음 단계에 따라 **portableShell.bat** 파일을 두 번 클릭하여 Windows 셸을 표시하고 셸 경로가 **spamasser.zip** 파일의 압축을 해제한 폴더에 해당하는지 확인합니다. 그렇지 않은 경우 **cd** 명령을 사용하여 액세스합니다.

   run_ **me.bat를** 입력한 다음 **Enter를** 클릭하여 설치 및 업데이트 프로세스를 시작합니다. 이 작업은 업데이트 결과를 나타내기 위해 다음 값 중 하나를 반환합니다.

   * **0**:업데이트가 수행되었습니다.
   * **1**:사용할 수 있는 새 업데이트가 없습니다.
   * **2**:새 업데이트를 사용할 수 없습니다.
   * **3**:이전 확인 중에 업데이트하지 못했습니다.
   * **4** 이상:오류가 발생했습니다.

1. SpamAssist 설치가 성공했는지 확인하려면 다음 절차를 사용하여 GTUBE 테스트(요청되지 않은 대량 이메일에 대한 일반 테스트)를 사용하십시오.

   1. 텍스트 파일을 만들고 C:\TestSpamMail.txt아래에 저장합니다 ****.
   1. 파일에 다음 컨텐츠를 삽입합니다.

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

   1. portableShell.bat **파일을 두 번** 클릭하여 Windows Shell을`<root>`표시한 다음 다음 명령을 실행합니다(또는 **&quot;를 통해 spamasser.zip** 파일의 압축을 풀 때 생성된 폴더를 지정합니다.)

      ```
       "<root>\perl\site\bin\spamassassin" "C:\TestSpamMail.txt"
      ```

      이 테스트 이메일의 내용은 SpamAsser의 1,000점 점수를 트리거합니다. 이는 원치 않는 것으로 감지되었고 설치가 성공적이었고 완전히 작동됨을 의미합니다.

### Adobe Campaign에 스팸 분류 통합 {#integrating-spamassassin-into-adobe-campaign}

1. 파일을 **`[INSTALL]/conf/serverConf.xml`** 편집합니다. serverConf.xml에서 사용할 수 있는 **모든 매개 변수가** 이 [섹션에](../../installation/using/the-server-configuration-file.md)나열됩니다.
1. 웹 노드에서 spamCheck **요소의** **명령** 속성 값을 **변경합니다** . 이렇게 하려면 다음 명령을 실행합니다.

   ```
   <spamCheck command='"<absolute path to the folder where you unzipped the zip file>\call_perl_with_args.bat" "<absolute path to nlserver>/spamcheck.pl"'/>
   ```

   >[!NOTE]
   >
   >모든 경로는 절대 경로여야 합니다.

   서비스를 중지하고 **[!UICONTROL Adobe Campaign]** 시작합니다.

1. Adobe Campaign에서 SpamCharacter의 통합을 확인하려면 GTBUE 테스트(요청되지 않은 대량 이메일에 대한 일반 테스트)를 사용하십시오.

   portableshell.bat **파일을 두 번** 클릭합니다. Windows 셸의 표시를 트리거합니다. 그런 다음 다음 명령을 실행합니다.

   ```
   perl "[INSTALL]\bin\spamcheck.pl" "C:\TestSpamMail.txt"
   ```

   이 테스트 이메일의 내용은 SpamAssist에서 할당한 1,000개의 포인트를 트리거합니다. 이는 Adobe Campaign의 통합이 성공적이고 완전히 기능적으로 감지되지 않음을 의미합니다.

1. 스팸 필터링 및 점수 규칙 업데이트

   필터링 및 점수 지정 규칙의 초기 업데이트를 위해 portableShell.bat **를** 시작하고 다음 명령을 실행하십시오.

   ```
   sa-update --no-gpg
   ```

   필터링 및 점수 지정 규칙의 자동 업데이트를 실행하려면 예약된 시스템 작업에서 이 동일한 명령을 사용합니다.

   ```
   sa-update --no-gpg
   ```

## Linux 시스템에 설치 {#installing-on-a-linux-machine}

### Debian의 설치 단계 {#installation-steps-in-debian}

* 필요한 경우 다음 명령을 사용하여 Perl 및 SpamCharacter를 설치합니다.

   ```
   apt-get install spamassassin libxml-writer-perl
   ```

* serverConf. **xml** 파일(에서 사용 가능) `/usr/local/[INSTALL]/nl6/conf/`에서 **spamCheck** 라인을 다음과 같이 변경합니다.

   ```
   <spamCheck command="perl
   /usr/local/[NSTALL]/nl6/bin/spamcheck.pl"/>
   ```

### RHEL/CentOS의 설치 단계 {#installation-steps-in-rhel-centos}

필요한 경우 Perl을 설치하고 CPAN을 사용하여 패키지를 복구하십시오.

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

필터 규칙은 **sa-update** 도구를 사용하여 자동으로 업데이트할 수 있습니다. 자세한 내용은 공식 SpamAssist 웹 사이트 [http://spamassassin.apache.org/](http://spamassassin.apache.org/) 를 참조하십시오.

Debian에서는 매일 업데이트가 자동으로 수행됩니다.

이 경우가 아니면(예: Debian이 수동으로 설치된 경우) 스크립트를 만들어 규칙 업데이트를 자동화합니다.

```
!/bin/sh
test -x /usr/bin/sa-update || exit 0
/usr/sbin/sa-update && /etc/init.d/spamassassin update
```

다음 명령을 사용하여 이 스크립트를 **crontab** 에 삽입합니다.

```
crontab-e
```

### 성능 최적화 {#performance-optimization}

Linux의 성능을 향상시키려면 /etc/spamassassin/local.cf **파일을** 편집하고 파일 끝에 다음 줄을 추가합니다.

```
dns_available no
```

