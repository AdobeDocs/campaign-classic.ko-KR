---
title: SFTP 서버 사용
seo-title: SFTP 서버 사용
description: SFTP 서버 사용
seo-description: null
page-status-flag: never-activated
uuid: 5281058d-91bd-4f98-835d-1d46dc7b8b1f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
discoiquuid: f449ccd5-3965-4ab8-b5a9-993f3260aba9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1e8492d8e91d679ac13da875974e27d0f7791dc3

---


# SFTP 서버 사용{#sftp-server-usage}

## SFTP 서버 우수 사례 {#sftp-server-best-practices}

ETL을 위해 파일 및 데이터를 관리할 때 이러한 파일은 Adobe에서 제공하는 호스팅 SFTP 서버에 저장됩니다. 이 SFTP 파섹

올바로 사용되거나 모니터링되지 않는 경우 이 공간은 서버에서 사용할 수 있는 물리적 공간을 빠르게 채우고 후속 업로드에서 파일이 잘릴 수 있습니다. 공간이 포화되면 자동 제거는 SFTP 저장소에서 가장 오래된 파일을 트리거하고 지울 수 있습니다.

이러한 문제를 방지하려면 아래 우수 사례를 따르는 것이 좋습니다.

>[!NOTE]
>
>인스턴스가 AWS에서 호스팅되는 경우 Campaign Classic 제어판에서 SFTP 서버 스토리지를 모니터링할 [수 있습니다](https://docs.adobe.com/content/help/en/control-panel/using/sftp-management/sftp-storage-management.html).
>
>인스턴스가 AWS에서 호스팅되는지 확인하려면 [이 섹션에](https://docs.adobe.com/content/help/en/control-panel/using/faq.html#ims-org-id) 설명된 단계를 따르십시오.

* 서버 크기 기능은 라이센스에 따라 다릅니다. 어떤 경우든, 최소 데이터를 최대한 유지하고 필요한 기간(최대 시간 제한은 15일)에 대해서만 데이터를 보관하십시오.
* 암호 만료를 방지하려면 암호 인증 대신 키 기반 인증을 사용하십시오(암호의 유효 기간이 90일입니다). 또한 키 기반 인증을 사용하면 여러 개의 키(예: 여러 개체 관리)를 생성할 수 있습니다. 반면에 암호 인증에서는 관리하는 모든 엔티티와 암호를 공유해야 합니다.

   지원되는 키 형식은 SSH-2 RSA 2048입니다. 키는 PyTTY(Windows) 또는 ssh-keygen(Unix)과 같은 도구를 사용하여 생성할 수 있습니다. Campaign 서버에 업로드하려면 [지원 티켓을](https://support.neolane.net) 통해 Adobe 지원 팀에 공개 키를 제공해야 합니다.

* 워크플로우를 사용하여 데이터를 적절하게 삭제합니다(데이터를 사용하는 워크플로우에서 보존 관리).
* 워크플로우뿐만 아니라 SFTP 업로드에서도 일괄 처리를 사용합니다.
* 오류/예외 처리
* 경우에 따라 SFTP에 로그인하여 SFTP에 있는 내용을 직접 확인할 수 있습니다.
* SFTP 디스크 관리는 주로 사용자의 책임입니다.
* 기본적으로 모든 폴더는 식별자에 대해서만 읽기/쓰기 모드에 있습니다. Campaign에서 액세스해야 하는 폴더를 만들 때는 전체 그룹에 대한 읽기/쓰기 권한을 사용하여 폴더를 구성해야 합니다. 그렇지 않으면 보안상의 이유로 동일한 그룹 내에서 다른 식별자로 실행되므로 워크플로우에서 파일을 만들거나 삭제할 수 없습니다.
* SFTP 연결을 시작하려는 공개 IP는 캠페인 인스턴스에서 허용 목록에 포함되어야 합니다. IP 주소 허용 표시는 [지원 티켓을](https://support.neolane.net)통해 요청할 수 있습니다.

>[!CAUTION]
>
>자체 SFTP 서버를 사용하는 경우 위의 권장 사항을 가능한 한 많이 따라야 합니다.

## SFTP 서버 문제 해결 {#sftp-server-troubleshooting}

아래 섹션에는 Adobe 호스팅 SFTP 서버와 연결 문제가 발생할 때 [지원 티켓을](https://support.neolane.net) 통해 Adobe 지원 팀에 확인하고 제공하는 정보가 나와 있습니다.

1. 인스턴스가 실행 중인지 확인합니다. 이렇게 하려면 브라우저를 열고 인스턴스 **[!UICONTROL GET]** 끝점을 **[!UICONTROL /r/test]** 호출합니다.

   ```
   https://instanceUrl/r/test
   ```

   인스턴스가 실행 중인 경우 다음과 같은 유형의 응답을 얻을 수 있습니다.

   ```
   <redir status='OK' date='YYYY-MM-DD HH:MM:SS' build='XXXX' instance='instanceName'
   sourceIP='AAA.BB.CCC.DD' host='instanceUrl' localHost='instanceName'/>
   ```

   어떤 경우든 지원 티켓에 명령 응답을 제공합니다.

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
   >Netcat 도구를 사용하면 다양한 운영 체제에서 네트워크 연결을 쉽게 관리할 수 [있습니다(https://eternallybored.org/misc/netcat/](https://eternallybored.org/misc/netcat/)참조).

   포트가 열려 있지 않은 경우 측면 에서 아웃바운드 연결을 열고 다시 시도하십시오. 여전히 연결 문제가 발생하면 명령 출력을 Adobe 지원 팀과 공유합니다.

1. SFTP 연결을 시작하려는 공개 IP가 허용 목록에 대해 Adobe 지원에 제공한 IP인지 확인하십시오.
1. 암호 기반 인증을 사용하는 경우 암호가 만료되었을 수 있습니다(암호는 90일 유효 기간). 따라서 키 기반 인증을 사용하는 것이 좋습니다(SFTP [서버 우수 사례](#sftp-server-best-practices)참조).
1. 키 기반 인증을 사용하는 경우 사용 중인 키가 인스턴스 구성에 대해 Adobe 지원 팀에 제공한 키와 동일한지 확인하십시오.
1. FileZilla 또는 이와 동등한 FTP 도구를 사용하는 경우 지원 티켓에 연결 로그 세부 정보를 제공합니다.

