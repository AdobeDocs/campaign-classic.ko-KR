---
solution: Campaign Classic
product: campaign
title: SpamAssassin 구성
description: SpamAssassin 구성
audience: installation
content-type: reference
topic-tags: additional-configurations
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 0%

---


# SpamAssassin 구성{#configuring-spamassassin}

>[!NOTE]
>
>일부 구성은 Adobe에 의해 호스팅되는 배포에 대해서만 Adobe에서 수행할 수 있습니다. 예를 들어 서버 및 인스턴스 구성 파일에 액세스하려면 다른 배포에 대한 자세한 내용은 [호스팅 모델](../../installation/using/hosting-models.md) 섹션 또는 [이 페이지](../../installation/using/capability-matrix.md)를 참조하십시오.

## 개요 {#overview}

SpamCharacter는 원하지 않는 이메일을 필터링하기 위해 고안된 소프트웨어입니다. 이 소프트웨어와 함께 Adobe Campaign은 이메일에 점수를 할당하여 메시지를 전달하기 전에 원치 않는 것으로 간주될 수 있는지 여부를 결정할 수 있습니다. 이렇게 하려면 Adobe Campaign의 응용 프로그램 서버에 SpamAssist를 설치 및 구성해야 하며 이 경우 특정 수의 추가 Perl 모듈을 설치해야 합니다.

이 장에 설명된 바와 같이 스팸얼라이터의 배포 및 통합은 필터링 및 점수 지정 규칙처럼 기본 소프트웨어 설치를 기반으로 하며, 이는 변경 또는 최적화 없이 스팸캐스터가 제공하는 것입니다. 점수 기여도 및 메시지 자격은 SpamAssessant 옵션 구성 및 필터링 규칙에 대해서만 결정됩니다. 네트워크 관리자는 회사의 요구에 맞게 조정할 책임이 있다.

>[!IMPORTANT]
>
>스팸 암살자가 원하지 않는 이메일의 자격은 필터링 및 채점 규칙에 전적으로 따라 결정됩니다.
>
>따라서 SpamCharacter 설치 및 Adobe Campaign와의 통합이 완벽한 기능을 갖추고 전송하기 전에 제품에 할당된 점수의 연관성을 보장하려면 이러한 규칙을 하루에 한 번 이상 업데이트해야 합니다.
>
>이 업데이트는 SpamCharacter를 호스팅하는 서버 관리자의 책임입니다.

Adobe Campaign에서 SpamCharacter를 사용하면 Adobe Campaign에서 보낸 이메일을 받을 때 SpamCharacter를 사용하는 메일 서버의 작동 가능성에 대한 정보를 제공합니다. 그러나 인터넷 공급자 또는 온라인 메일 서버의 메일 서버가 Adobe Campaign이 보낸 메시지를 여전히 원하지 않는 것으로 간주할 수 있습니다.

Perl에 SpamCharacter 및 해당 모듈을 배포하려면 HTTP 연결(TCP/80 흐름)을 통해 인터넷에 액세스할 수 있는 Adobe Campaign 응용 프로그램 서버가 필요합니다.

## Windows 컴퓨터 {#installing-on-a-windows-machine}에 설치

Adobe Campaign와의 통합을 활성화하기 위해 Windows에 SpamCharacter를 설치하고 구성하려면 다음 단계를 수행하십시오.

1. SpamCharacter 설치
1. Adobe Campaign에 스팸얼을 통합합니다.

### SpamCharacter {#installing-spamassassin} 설치

1. 사용자 자격 증명을 사용하여 [소프트웨어 배포 포털](https://experience.adobe.com/downloads)에 연결합니다. [이 페이지](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en)의 소프트웨어 배포에 대해 자세히 알아보십시오.
1. **Neolane Spam Character(Windows 설치)(2.0)** 파일(neolane_spamasser.2.0.zip)을 다운로드합니다.
1. 이 파일을 Adobe Campaign 서버에 복사한 다음 압축을 해제합니다.

   >[!NOTE]
   >
   >경로가 다음과 같은 정규 표현식 문자로 구성되는 경우 원하는 위치에 있는 파일의 압축을 해제할 수 있습니다.**`-_A-Za-z\xA0-\xFF0-9\.\%\@\=\+\,\/\\\:.`**. 설치 경로에는 공백 문자가 없어야 합니다.

1. 파일의 압축을 푼 다음 **run_me.bat** 파일을 두 번 클릭하여 설치 스크립트를 시작합니다.

   Windows 셸이 나타나고 몇 초 동안 계속 표시되는 경우 설치 및 업데이트가 완료될 때까지 기다렸다가 **Enter**&#x200B;를 클릭합니다.

   Windows 셸이 나타나지 않거나 즉시 표시되지 않는 경우, 다음 단계를 따라 **portableShell.bat** 파일을 두 번 클릭하여 Windows 셸을 표시하고 셸 경로가 **spamasser.zip** 파일의 압축을 해제한 폴더에 해당하는지 확인합니다. 이 경우 **cd** 명령을 사용하여 액세스합니다.

   **run_me.bat**&#x200B;를 입력한 다음 **Enter**&#x200B;를 클릭하여 설치 및 업데이트 프로세스를 시작합니다. 업데이트 결과를 나타내기 위해 다음 값 중 하나를 반환합니다.

   * **0**:업데이트가 수행되었습니다.
   * **1**:사용할 수 있는 새 업데이트가 없습니다.
   * **2**:사용할 수 있는 새 업데이트가 없습니다.
   * **3**:이전 확인 중 업데이트에 실패했습니다.
   * **4**  이상:오류가 발생했습니다.

1. SpamCharacter 설치가 성공했는지 확인하려면 다음 절차를 사용하여 GTUBE 테스트(요청되지 않은 대량 이메일에 대한 일반 테스트)를 사용하십시오.

   1. 텍스트 파일을 만들고 **C:\TestSpamMail.txt** 아래에 저장합니다.
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

   1. **portableShell.bat** 파일을 두 번 클릭하여 Windows Shell을 표시한 다음 명령을 실행합니다(또는 **spamasterer.zip** 파일의 압축을 풀 때 &quot;`<root>`&quot;가 만들어진 폴더를 지정합니다.)

      ```
       "<root>\perl\site\bin\spamassassin" "C:\TestSpamMail.txt"
      ```

      이 테스트 이메일의 내용은 SpamCharacter의 1,000점 점수를 트리거합니다. 이는 원치 않는 것으로 감지되고 설치가 성공적이었으며 모든 기능이 제대로 작동하는지 의미합니다.

### Adobe Campaign {#integrating-spamassassin-into-adobe-campaign}에 SpamCharacter 통합

1. **`[INSTALL]/conf/serverConf.xml`** 파일을 편집합니다. **serverConf.xml**&#x200B;에 사용 가능한 모든 매개 변수가 이 [섹션](../../installation/using/the-server-configuration-file.md)에 나열됩니다.
1. **웹** 노드에서 **spamCheck** 요소&#x200B;**명령** 속성의 값을 변경합니다. 이렇게 하려면 다음 명령을 실행합니다.

   ```
   <spamCheck command='"<absolute path to the folder where you unzipped the zip file>\call_perl_with_args.bat" "<absolute path to nlserver>/spamcheck.pl"'/>
   ```

   >[!NOTE]
   >
   >모든 경로는 절대 경로여야 합니다.

   **[!UICONTROL Adobe Campaign]** 서비스를 중지하고 시작합니다.

1. Adobe Campaign에서 SpamCharacter의 통합을 확인하려면 GTBUE 테스트(원치 않는 대량 이메일에 대한 범용 테스트)를 사용합니다.

   **portableshell.bat** 파일을 두 번 클릭합니다. Windows 셸의 표시를 트리거합니다. 그런 다음 다음 다음 명령을 실행합니다.

   ```
   perl "[INSTALL]\bin\spamcheck.pl" "C:\TestSpamMail.txt"
   ```

   이 테스트 이메일의 내용은 SpamCharacter에서 할당된 1,000개의 포인트를 트리거합니다. 이는 Adobe Campaign의 통합이 성공적이고 완전한 기능을 갖추고 있지 않다는 것을 의미합니다.

1. SpamAssist 필터링 및 점수 지정 규칙 업데이트

   필터링 및 점수 지정 규칙의 초기 업데이트를 보려면 **portableShell.bat**&#x200B;을 시작하고 다음 명령을 실행하십시오.

   ```
   sa-update --no-gpg
   ```

   필터링 및 점수 지정 규칙의 자동 업데이트를 실행하려면 예약된 시스템 작업에서 이 명령을 사용합니다.

   ```
   sa-update --no-gpg
   ```

## Linux 컴퓨터에 설치 {#installing-on-a-linux-machine}

### Debian {#installation-steps-in-debian}의 설치 단계

* 필요한 경우 다음 명령을 사용하여 Perl 및 SpamCharacter를 설치합니다.

   ```
   apt-get install spamassassin libxml-writer-perl
   ```

* **serverConf.xml** 파일(`/usr/local/[INSTALL]/nl6/conf/`에서 사용 가능)에서 **spamCheck** 행을 다음과 같이 변경합니다.

   ```
   <spamCheck command="perl
   /usr/local/[NSTALL]/nl6/bin/spamcheck.pl"/>
   ```

### RHEL/CentOS {#installation-steps-in-rhel-centos}의 설치 단계

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

### 필터 규칙 업데이트 중 {#updating-filter-rules}

필터 규칙은 **sa-update** 도구를 사용하여 자동으로 업데이트할 수 있습니다. 자세한 내용은 공식 SpamCharacter 웹 사이트 [http://spamassassin.apache.org/](http://spamassassin.apache.org/)을 참조하십시오.

Debian에서는 매일 업데이트가 자동으로 수행됩니다.

이 경우(예: Debian이 수동으로 설치된 경우), 규칙 업데이트를 자동화하는 스크립트를 만드십시오.

```
!/bin/sh
test -x /usr/bin/sa-update || exit 0
/usr/sbin/sa-update && /etc/init.d/spamassassin update
```

다음 명령을 사용하여 **crontab**&#x200B;에 이 스크립트를 삽입합니다.

```
crontab-e
```

### 성능 최적화 {#performance-optimization}

Linux에서 성능을 향상시키려면 **/etc/spamassassin/local.cf** 파일을 편집하고 파일 끝에 다음 줄을 추가합니다.

```
dns_available no
```

