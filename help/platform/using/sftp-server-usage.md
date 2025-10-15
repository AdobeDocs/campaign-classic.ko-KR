---
product: campaign
title: SFTP 서버 사용
description: SFTP 서버 모범 사례 및 문제 해결에 대해 자세히 알아보기
feature: Troubleshooting
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: d585a5d4-ea33-43c8-aa37-4d892025374a
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '1076'
ht-degree: 9%

---

# SFTP 서버 모범 사례 및 문제 해결 {#sftp-server-usage}

## SFTP 서버 글로벌 권장 사항 {#global-recommendations}

ETL 목적으로 파일 및 데이터를 관리할 때 이러한 파일은 Adobe에서 제공하는 호스팅 SFTP 서버에 저장됩니다. SFTP 서버를 사용할 때는 아래 권장 사항을 따라야 합니다.

* 암호 만료를 방지하려면 암호 인증 대신 키 기반 인증을 사용하십시오(암호는 유효 기간이 90일입니다). 또한 키 기반 인증을 사용하면 여러 엔티티 관리 등 여러 키를 생성할 수 있습니다. 반대로 암호 인증은 관리하는 모든 엔티티와 암호를 공유해야 합니다.

  지원되는 키 형식은 SSH-2 RSA 2048입니다. Windows용 SSH 키를 생성하는 도구는 PuTTYgen이며 Linux용 ssh-keygen입니다. Campaign Campaign 컨트롤 패널을 통해 공개 SSH 키를 업로드할 수 있습니다. [자세히 알아보기](https://experienceleague.adobe.com/en/docs/control-panel/using/sftp-management/key-management){target="_blank"}

* 워크플로뿐만 아니라 SFTP 업로드에서도 배치 처리를 사용합니다.

* 오류/예외를 처리합니다.

* 기본적으로 생성하는 모든 폴더는 식별자에 대해서만 읽기/쓰기 모드에 있습니다. Campaign에서 액세스해야 하는 폴더를 만들 때 전체 그룹에 대한 읽기/쓰기 권한으로 구성해야 합니다. 그렇지 않으면 보안상의 이유로 워크플로우가 동일한 그룹 내에서 다른 식별자로 실행되므로 파일을 만들거나 삭제하지 못할 수 있습니다.

* SFTP 연결을 시작하려는 퍼블릭 IP는 Campaign 인스턴스의 허용 목록에 추가하다에 추가해야 합니다. 공개 IP는 Campaign 컨트롤 패널을 통해 추가할 수 있습니다. [자세히 알아보기](https://experienceleague.adobe.com/en/docs/control-panel/using/sftp-management/ip-range-allow-listing){target="_blank"}

## SFTP 스토리지 사용 모범 사례 {#sftp-server-best-practices}

SFTP 서버는 파일의 보존 및 삭제를 제어할 수 있는 임시 저장소 공간으로 설계되었습니다.

올바르게 사용하거나 모니터링하지 않으면 이러한 공백이 서버에서 사용 가능한 실제 공간을 빠르게 채우고 이후 업로드 시 파일이 잘릴 수 있습니다. Adobe에서 호스팅하는 SFTP 서버에서 SFTP 스토리지가 80% 임계값에 도달하면 파일이 압축됩니다. 이 프로세스는 자동으로 수행되며 Adobe 모니터링 시스템에 의해 트리거됩니다.

이러한 문제를 방지하기 위해 Adobe에서는 아래 모범 사례를 따를 것을 권장합니다.

>[!NOTE]
>
>* Campaign Classic [Campaign 컨트롤 패널](https://experienceleague.adobe.com/docs/control-panel/using/sftp-management/sftp-storage-management.html){target="_blank"}를 사용하여 SFTP 서버 저장소를 모니터링할 수 있습니다.
>
>* 컨트롤 패널은 모든 관리 사용자가 액세스할 수 있습니다. 사용자에게 관리자 권한을 부여하는 단계는 [이 페이지](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=ko#discover-control-panel){target="_blank"}에 자세히 설명되어 있습니다.
>
>* 인스턴스를 [최신 GA 빌드](../../rn/using/rn-overview.md)로 업그레이드해야 합니다. [이 섹션](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version){target="_blank"}에서 버전을 확인하는 방법을 알아보세요.

* 서버 크기 기능은 사용 중인 라이센스에 따라 다릅니다. 어떤 경우든 가능한 최소 데이터를 유지하고 필요한 동안만 데이터를 유지합니다(15일이 최대 시간 제한).

* 워크플로를 사용하여 데이터를 올바르게 삭제합니다(데이터를 사용하는 워크플로에서 보존을 관리합니다).

* 때때로 SFTP에 로그인하여 무엇이 있는지 직접 확인합니다.

* SFTP 디스크 관리는 주로 사용자의 책임입니다.

## 외부 SFTP 서버 사용 {#external-SFTP-server}

자체 SFTP 서버를 사용하는 경우 위의 권장 사항을 최대한 준수하십시오.

또한 Campaign Classic에서 외부 SFTP 서버에 대한 경로를 지정할 때 경로 구문은 SFTP 서버 운영 체제에 따라 다릅니다.

* SFTP 서버가 **Windows**&#x200B;에 있는 경우 항상 상대 경로를 사용하십시오.
* STP 서버가 **Linux**&#x200B;에 있는 경우 항상 홈을 기준으로 하는 경로(&quot;~/&quot;로 시작) 또는 절대 경로(&quot;/&quot;로 시작)를 사용하십시오.

## Adobe 호스팅 SFTP 서버 연결 문제 {#sftp-server-troubleshooting}

아래 섹션에는 Adobe 호스팅 SFTP 서버에 연결 문제가 발생할 때 [Adobe 고객 지원 센터](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"}를 통해 Adobe 지원 팀에 확인하고 제공하는 정보가 나열되어 있습니다.

1. 인스턴스가 실행 중인지 확인하십시오. 이렇게 하려면 브라우저를 연 다음 인스턴스 **[!UICONTROL GET]** 끝점에서 **[!UICONTROL /r/test]**&#x200B;을(를) 호출합니다.

   ```xml
   https://instanceUrl/r/test
   ```

   인스턴스가 실행 중인 경우 다음 유형의 응답을 받아야 합니다.

   ```xml
   <redir status='OK' date='YYYY-MM-DD HH:MM:SS' build='XXXX' instance='instance-name'
   sourceIP='AAA.BB.CCC.DD' host='instanceUrl' localHost='instance-name'/>
   ```

   어떤 경우든 지원 티켓에 명령 응답을 제공하십시오.

1. SFTP 연결을 시작하려는 사이트에서 아웃바운드 포트 22가 열려 있는지 확인합니다. 이렇게 하려면 다음 명령을 사용합니다.

   ```xml
   bash-3.2$ nc -vz <SFTP_URL> 22
   # Replace the SFTP_URL with actual SFTP instance URL
   # If the port 22 is opened you will see output similar to the below one
   # for e.g. the  output for the command on myCompany-stage-sftp.neolane.net after ssh-out, will give
   bash-3.2$ nc -vz myCompagny-stage-sftp.neolane.net 22
   myCompany-stage-sftp.neolane.net [AAA.BBB.CCC.D] 22 (ssh) open
   ```

   포트가 열리지 않으면 측에서 아웃바운드 연결을 열어야 합니다. 그런 다음 다시 시도하십시오. 여전히 연결 문제가 발생하면 명령 출력을 [Adobe 고객 지원 센터](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 팀과 공유하십시오.

1. SFTP 연결을 시작하려는 퍼블릭 IP가 Adobe 지원 for 허용 목록에 추가하다에 제공한 IP인지 확인합니다.
1. 암호 기반 인증을 사용하는 경우 암호가 만료되었을 수 있습니다(암호에는 90일의 유효 기간이 있음). 따라서 키 기반 인증을 사용하는 것이 좋습니다([SFTP 서버 모범 사례](#sftp-server-best-practices) 참조).
1. 키 기반 인증을 사용하는 경우 사용 중인 키가 인스턴스 구성을 위해 [Adobe 고객 지원 센터](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 팀에 제공한 키와 같은지 확인하십시오.
1. FileZilla 또는 이와 동등한 FTP 도구를 사용하는 경우 지원 티켓에 연결 로그 세부 사항을 입력합니다.

## &quot;호스트 이름을 확인할 수 없음&quot; 오류

이 섹션에서는 Campaign Classic에서 FTP 서버에 연결한 후 &quot;호스트 이름을 확인할 수 없습니다.&quot; 오류를 가져올 때 수행할 검사 및 작업에 대한 정보를 제공합니다.

워크플로우 저널에는 다음 로그가 표시됩니다.

```xml
16/05/2016 12:49:03    fileTransfer    Upload error in cURL
16/05/2016 12:49:03    fileTransfer    Couldn't resolve host name
16/05/2016 12:49:03    fileTransfer    Couldn't resolve host name
16/05/2016 12:49:03    fileTransfer    Starting transfer of '/usr/local/neolane/nl6/var/williamreed/export/Recipients' to 'ftp://213.253.61.250/Recipients'
16/05/2016 12:49:03    fileTransfer    1 file(s) to transfer
```

이 오류는 FileZilla 또는 WinSCP를 사용하여 FTP를 통해 계속 연결할 수 있는 동안 워크플로우에서 FTP 서버에 연결하고 서버에서 파일을 다운로드할 때 발생합니다.

이 오류는 FTP 서버 도메인 이름을 제대로 확인할 수 없음을 나타냅니다. 문제를 해결하려면 다음을 수행하십시오.

1. **DNS 서버 구성 문제 해결**:

   1. 서버 이름이 로컬 DNS 서버에 추가되었는지 확인합니다.
   1. 그렇다면 Adobe Campaign 서버에서 다음 명령을 실행하여 IP 주소를 가져옵니다.

      `nslookup <server domain name>`

      FTP 서버가 작동하며 Adobe Campaign 애플리케이션 서버에서 연결할 수 있는지 확인합니다.

1. **세션 로그** 문제 해결:

   1. 워크플로우에서 [파일 전송](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/event-activities/file-transfer.html){target="_blank"} 활동을 두 번 클릭합니다.
   1. **[!UICONTROL File Transfer]** 탭으로 이동한 다음 **[!UICONTROL Advanced Parameters]**&#x200B;을(를) 클릭합니다.
   1. **[!UICONTROL Display the session logs]** 옵션을 선택합니다.

      ![](assets/sftp-error-display-logs.png)

   1. 워크플로우 감사로 이동하여 로그에 &#39;호스트 이름을 확인할 수 없습니다&#39; 오류가 표시되는지 확인합니다.

1. SFTP 서버가 Adobe에서 호스팅되는 경우 고객 지원 센터에 문의하여 IP가 허용 목록에 추가하다에 추가되었는지 확인하십시오.

   그렇지 않으면 다음을 확인합니다.

   * 암호에 `@` 문자가 포함되어 있지 않습니다. 암호에 `@` 문자가 있으면 연결이 실패합니다.
   * Adobe Campaign 애플리케이션 서버와 SFTP 서버 간의 통신을 방해할 수 있는 방화벽 문제는 없습니다.
   * Campaign 서버에서 sftp로 tracert 및 telnet 명령을 실행하여 연결 문제가 있는지 확인합니다.
   * 통신 프로토콜 문제가 없습니다.
   * 포트가 열려 있습니다.
