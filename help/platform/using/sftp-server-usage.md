---
product: campaign
title: SFTP 서버 사용
description: SFTP 서버 우수 사례 및 문제 해결에 대해 자세히 알아보십시오.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: d585a5d4-ea33-43c8-aa37-4d892025374a
source-git-commit: 1d32161d60f6b382188012b104c642f504e28645
workflow-type: tm+mt
source-wordcount: '1150'
ht-degree: 14%

---

# SFTP 서버 모범 사례 및 문제 해결 {#sftp-server-usage}

![](../../assets/common.svg)

## SFTP 서버 글로벌 권장 사항 {#global-recommendations}

ETL 목적으로 파일 및 데이터를 관리할 때 이러한 파일은 Adobe에서 제공하는 호스팅 SFTP 서버에 저장됩니다. SFTP 서버를 사용할 때는 아래 권장 사항을 따라야 합니다.

* 암호 만료를 방지하려면 암호 인증 대신 키 기반 인증을 사용하십시오(암호는 90일). 또한 키 기반 인증을 사용하면 여러 엔티티를 관리할 때와 같이 여러 키를 생성할 수 있습니다. 반면, 암호 인증에서는 관리하고 있는 모든 엔티티와 암호를 공유해야 합니다.

   지원되는 키 형식은 SSH-2 RSA 2048입니다. 키는 PyTTY(Windows) 또는 ssh-keygen(Unix)과 같은 도구를 사용하여 생성할 수 있습니다.를 통해 Adobe 지원 팀에 공개 키를 제공해야 합니다 [고객 지원 Adobe](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 를 Campaign 서버에 업로드하도록 했습니다.

* 워크플로우뿐만 아니라 SFTP 업로드에서도 일괄 처리를 사용합니다.

* 오류/예외를 처리합니다.

* 기본적으로 작성하는 모든 폴더는 식별자에만 대한 읽기/쓰기 모드입니다. Campaign에서 액세스해야 하는 폴더를 만들 때는 전체 그룹에 대한 읽기/쓰기 권한이 있는 폴더를 구성해야 합니다. 그렇지 않으면 보안상의 이유로 동일한 그룹 내에서 다른 식별자로 실행되기 때문에 워크플로우에서 파일을 만들거나 삭제할 수 없습니다.

* SFTP 연결을 시작하려는 공용 IP를 Campaign 인스턴스의에 추가해야 허용 목록에 추가하다 합니다. 에 IP 주소 추가허용 목록에 추가하다는 를 통해 요청할 수 있습니다. [고객 지원 Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## 데이터베이스 사용 모범 사례 {#sftp-server-best-practices}

SFTP 서버는 파일의 보관 및 삭제를 제어할 수 있는 임시 저장 공간으로 설계되었습니다.

올바르게 사용하거나 모니터링하지 않으면 이러한 공백은 서버에서 사용할 수 있는 물리적 공간을 빠르게 채워 파일을 후속 업로드에서 잘리게 할 수 있습니다. 공간이 포화되면 자동 제거는 SFTP 저장소에서 가장 오래된 파일을 트리거하고 지울 수 있습니다.

이러한 문제를 방지하기 위해 아래 모범 사례를 따를 것을 권장합니다.

>[!NOTE]
>
>인스턴스가 AWS에서 호스팅되는 경우 Campaign Classic을 사용하여 SFTP 서버 저장소를 모니터링할 수 있습니다 [Campaign 컨트롤 패널](https://experienceleague.adobe.com/docs/control-panel/using/sftp-management/sftp-storage-management.html). 인스턴스가 AWS에서 호스팅되는지 확인하려면 [이 페이지](https://experienceleague.adobe.com/docs/control-panel/using/faq.html)에 설명된 단계를 수행합니다.
>
>Campaign 컨트롤 패널은 모든 관리 사용자가 액세스할 수 있습니다. 사용자에게 관리자 권한을 부여하는 단계는 [이 페이지](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=ko#discover-control-panel)에 자세히 설명되어 있습니다.
>
>인스턴스는 [최신 GA 빌드](../../rn/using/rn-overview.md). [이 섹션](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)에서 사용 중인 버전을 확인하는 방법을 알아봅니다.

* 서버 크기 기능은 라이센스에 따라 다릅니다. 어떤 경우든 최소 데이터를 가능한 한 유지하고 필요한 기간(15일은 최대 시간 제한)에만 데이터를 유지합니다.

* 워크플로우를 사용하여 데이터를 올바르게 삭제합니다(데이터를 사용하는 워크플로우에서 보존을 관리합니다).

* 때때로 SFTP에 로그인하여 무엇이 있는지 직접 확인합니다.

* SFTP 디스크 관리는 주로 사용자의 책임입니다.

## 외부 SFTP 서버 사용 {#external-SFTP-server}

고유한 SFTP 서버를 사용하는 경우 위의 권장 사항을 가능한 한 많이 따르도록 하십시오.

또한 Campaign Classic에서 외부 SFTP 서버의 경로를 지정할 때 경로 구문은 SFTP 서버 운영 체제에 따라 다릅니다.

* SFTP 서버가 켜져 있는 경우 **Windows**&#x200B;를 채울 때는 항상 상대 경로를 사용하십시오.
* STP 서버가 켜져 있는 경우 **Linux**&#x200B;를 채울 때는 항상 홈에 상대적인 경로(&quot;~/&quot;로 시작)나 절대 경로(&quot;/&quot;로 시작)를 사용하십시오.

## Adobe 호스팅 SFTP 서버와 관련된 연결 문제 {#sftp-server-troubleshooting}

아래 섹션에는 를 통해 Adobe 지원 팀에 확인하고 제공할 정보가 나와 있습니다. [고객 지원 Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 호스팅된 Adobe의 SFTP 서버 연결 문제가 발생하는 경우.

1. 인스턴스가 실행 중인지 확인합니다. 이렇게 하려면 브라우저를 열고 을(를) 만듭니다 **[!UICONTROL GET]** 인스턴스에 대한 호출 **[!UICONTROL /r/test]** endpoint:

   ```
   https://instanceUrl/r/test
   ```

   인스턴스가 실행 중인 경우 다음 유형의 응답을 가져와야 합니다.

   ```
   <redir status='OK' date='YYYY-MM-DD HH:MM:SS' build='XXXX' instance='instanceName'
   sourceIP='AAA.BB.CCC.DD' host='instanceUrl' localHost='instanceName'/>
   ```

   어떤 경우든 지원 티켓에서 명령 응답을 제공합니다.

1. SFTP 연결을 시작하려는 사이트에서 아웃바운드 포트 22가 열려 있는지 확인합니다. 이렇게 하려면 다음 명령을 사용합니다.

   ```
   bash-3.2$ nc -vz <SFTP_URL> 22
   # Replace the SFTP_URL with actual SFTP instance URL
   # If the port 22 is opened you will see output similar to the below one
   # for e.g. the  output for the command on myCompany-stage-sftp.neolane.net after ssh-out, will give
   bash-3.2$ nc -vz myCompagny-stage-sftp.neolane.net 22
   myCompany-stage-sftp.neolane.net [AAA.BBB.CCC.D] 22 (ssh) open
   ```

   >[!NOTE]
   >
   >Netcat 도구를 사용하면 다양한 운영 체제에서 네트워크 연결을 쉽게 관리할 수 있습니다( [https://eternallybored.org/misc/netcat/](https://eternallybored.org/misc/netcat/)).

   포트가 열리지 않은 경우, 쪽에서 아웃바운드 연결을 열고 다시 시도하십시오. 여전히 연결 문제가 발생하는 경우 명령의 출력을 [고객 지원 Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 팀

1. SFTP 연결을 시작하려는 공용 IP가 Adobe 지원허용 목록에 추가하다에 제공한 IP인지 확인합니다.
1. 암호 기반 인증을 사용하는 경우 암호가 만료되었을 수 있습니다(암호는 90일 유효 기간). 따라서 키 기반 인증을 사용하는 것이 좋습니다(참조 [SFTP 서버 우수 사례](#sftp-server-best-practices)).
1. 키 기반 인증을 사용하는 경우 사용 중인 키가 제공한 키와 같은지 확인합니다 [고객 지원 Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 팀 구성
1. FileZilla 또는 이와 동등한 FTP 도구를 사용하는 경우 지원 티켓에 연결 로그 세부 사항을 제공합니다.

## &quot;호스트 이름을 확인할 수 없습니다.&quot; 오류

이 섹션에서는 Campaign Classic에서 FTP 서버에 연결한 후 &quot;호스트 이름을 확인할 수 없습니다&quot; 오류를 가져올 때 수행할 검사 및 작업에 대한 정보를 제공합니다.

워크플로우 분기에는 다음 로그가 표시됩니다.

```
16/05/2016 12:49:03    fileTransfer    Upload error in cURL
16/05/2016 12:49:03    fileTransfer    Couldn't resolve host name
16/05/2016 12:49:03    fileTransfer    Couldn't resolve host name
16/05/2016 12:49:03    fileTransfer    Starting transfer of '/usr/local/neolane/nl6/var/williamreed/export/Recipients' to 'ftp://213.253.61.250/Recipients'
16/05/2016 12:49:03    fileTransfer    1 file(s) to transfer
```

이 오류는 FileZilla 또는 WinSCP를 사용하여 FTP를 통해 연결할 수 있는 동안 워크플로우에서 FTP 서버를 연결하고 서버에서 파일을 다운로드할 때 발생합니다.

이 오류는 FTP 서버 도메인 이름을 제대로 확인할 수 없음을 나타냅니다. 문제를 해결하려면 다음을 수행하십시오.

1. 문제 해결 **DNS 서버 구성**:

   1. 서버 이름이 로컬 DNS 서버에 추가되었는지 확인합니다.
   1. yes인 경우 Adobe Campaign 서버에서 다음 명령을 실행하여 IP 주소를 가져옵니다.

      `nslookup <server domain name>`

      이를 통해 FTP 서버가 작동 중이고 Adobe Campaign 애플리케이션 서버에서 연결할 수 있습니다.

1. 문제 해결 **세션 로그**:

   1. 워크플로우에서 [파일 전송](../../workflow/using/file-transfer.md) 활동.
   1. 이동 **[!UICONTROL File Transfer]** 탭을 클릭한 다음 **[!UICONTROL Advanced Parameters]**.
   1. **[!UICONTROL Display the session logs]** 옵션을 선택합니다.

      ![](assets/sftp-error-display-logs.png)

   1. 워크플로우 감사로 이동하고 로그에 &#39;호스트 이름을 확인할 수 없음&#39; 오류가 표시되는지 확인합니다.

1. SFTP 서버가 Adobe에 의해 호스팅되는 경우 고객 지원 센터에 문의하여 IP가에 추가되었는지 허용 목록에 추가하다 확인하십시오.

   그렇지 않으면 유효성을 검사합니다.

   * 암호에는 &#39;@&#39;이(가) 없습니다. 암호에 &#39;@&#39;가 있으면 연결하지 못했습니다.
   * Adobe Campaign 애플리케이션 서버와 SFTP 서버 간의 통신을 방해하는 방화벽 문제가 없습니다.
   * 캠페인 서버에서 sftp로 tracert 및 telnet 명령을 실행하여 연결 문제가 있는지 확인합니다.
   * 통신 프로토콜 문제가 없습니다.
   * 포트가 열려 있습니다.
