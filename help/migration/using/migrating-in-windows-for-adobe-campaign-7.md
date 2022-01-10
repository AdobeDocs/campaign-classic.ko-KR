---
product: campaign
title: Microsoft Windows 플랫폼을 Adobe Campaign v7로 마이그레이션
description: Microsoft Windows 플랫폼을 Adobe Campaign v7로 마이그레이션하는 방법을 알아봅니다
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
exl-id: 3743d018-3316-4ce3-ae1c-25760aaf5785
source-git-commit: 63aca25a8d1ae24ef83849b35a44d1b37cfa5e96
workflow-type: tm+mt
source-wordcount: '1504'
ht-degree: 0%

---

# Microsoft Windows 플랫폼을 Campaign v7로 마이그레이션{#migrating-in-windows-for-adobe-campaign}

![](../../assets/v7-only.svg)

Microsoft Windows 환경의 경우 마이그레이션 단계는 다음과 같습니다.

1. 모든 서비스 중지 - [추가 정보](#service-stop).
1. 데이터베이스 백업 - [추가 정보](#back-up-the-database).
1. 플랫폼 마이그레이션 - [추가 정보](#deploying-adobe-campaign-v7).
1. 리디렉션 서버(IIS) 마이그레이션 - [추가 정보](#migrating-the-redirection-server--iis-).
1. 서비스 다시 시작 - [추가 정보](#re-starting-the-services).
1. 이전 Adobe Campaign 버전 삭제 및 정리 - [추가 정보](#deleting-and-cleansing-adobe-campaign-previous-version).

## 서비스 중지 {#service-stop}

먼저 관련 모든 컴퓨터에서 데이터베이스에 대한 액세스 권한을 가진 모든 프로세스를 중지합니다.

1. 리디렉션 모듈을 사용하는 모든 서버(**webmdl** 서비스)를 중지해야 합니다. IIS의 경우 다음 명령을 실행하십시오.

   ```
   iisreset /stop
   ```

1. 다음 **mta** 모듈 및 해당 하위 모듈(**mtachild**)은 다음 명령을 사용하여 중지해야 합니다.

   ```
   nlserver stop mta@<instance name>
   nlserver stop mtachild@<instance name>
   ```

1. 모든 서버에서 Adobe Campaign 서비스를 중지합니다. 관리자 권한으로 로그인하고 다음 명령을 실행합니다.

   ```
   net stop nlserver6
   ```

   v5.11에서 마이그레이션하는 경우 다음 명령을 실행하십시오.

   ```
   net stop nlserver5
   ```

1. 각 서버에 대해 Adobe Campaign 서비스가 제대로 중지되었는지 확인하십시오. 관리자 권한으로 로그인하고 다음 명령을 실행합니다.

   ```
   tasklist /FI "IMAGENAME eq nlserver*"
   ```

   활성 프로세스 목록과 해당 ID(PID)가 표시됩니다.

   ```
   Image Name                     PID Session Name        Session#    Mem Usage
   ========================= ======== ================ =========== ============
   nlserver.exe                  3192 Console                    1     13,108 K
   ```

1. 몇 분 후에도 하나 이상의 Adobe Campaign 프로세스가 여전히 활성 상태이거나 차단되면 해당 프로세스를 종료하십시오. 관리자 권한으로 로그인하고 다음 명령을 실행합니다.

   ```
   taskkill /IM nlserver* /T
   ```

1. 일부 프로세스가 몇 분 후에도 여전히 활성 상태인 경우 명령을 사용하여 해당 프로세스를 강제로 닫을 수 있습니다.

   ```
   taskkill /F /IM nlserver* /T
   ```

## Campaign 데이터베이스 백업 {#back-up-the-database}

절차는 Adobe Campaign 이전 버전에 따라 다릅니다.

### Adobe Campaign v5.11용 {#migrating-from-adobe-campaign-v5-11}

1. Adobe Campaign 데이터베이스를 백업합니다.
1. 의 백업 **Neolane v5** 다음 명령을 사용하는 디렉토리:

   ```
   ren "Neolane v5" "Neolane v5.back"
   ```

   >[!IMPORTANT]
   >
   >예방 조치로, **Neolane v5.back** 폴더를 만든 다음 서버 이외의 안전한 위치에 저장합니다.

1. windows 서비스 관리 콘솔에서 5.11 응용 프로그램 서버 서비스의 자동 시작을 비활성화합니다. 다음 명령을 사용할 수도 있습니다.

   ```
   sc config nlserver5 start= disabled
   ```

1. 편집 **config-`<instance name>`.xml** ( **Neolane v5. 뒤로** 폴더)를 클릭하여 **mta**, **wfserver**, **stat**&#x200B;등 서비스가 자동으로 시작됩니다. 예를 들어, **autoStart** with **_autoStart**.

   ```
   <?xml version='1.0'?>
   <serverconf>
     <shared>
       <dataStore hosts="myServer*" lang="en_US">
         <dataSource name="default">
           <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
         </dataSource>
       </dataStore>
     </shared>
   
     <mta _autoStart="true" statServerAddress="myStatServer"/>
     <stat _autoStart="true"/>
     <wfserver _autoStart="true"/>
     <inMail _autoStart="true"/>
     <sms _autoStart="false"/>
   </serverconf>
   ```

### Adobe Campaign v6.02의 경우 {#migrating-from-adobe-campaign-v6-02}

1. Adobe Campaign 데이터베이스를 백업합니다.
1. 의 백업 **Neolane v6** 다음 명령을 사용하는 디렉토리:

   ```
   ren "Neolane v6" "Neolane v6.back"
   ```

   >[!IMPORTANT]
   >
   >예방 조치로, **Neolane v6.back** 폴더를 만든 다음 서버 이외의 안전한 위치에 저장합니다.

1. Windows 서비스 관리자에서 6.02 응용 프로그램 서버의 자동 시작을 비활성화합니다. 다음 명령을 사용할 수도 있습니다.

   ```
   sc config nlserver6 start= disabled
   ```

1. 편집 **config-`<instance name>`.xml** ( **Neolane v6. 뒤로** 폴더)를 클릭하여 **mta**, **wfserver**, **stat**&#x200B;등 서비스가 자동으로 시작됩니다. 예를 들어, **autoStart** with **_autoStart**.

   ```
   <?xml version='1.0'?>
   <serverconf>
     <shared>
       <dataStore hosts="myServer*" lang="en_US">
         <dataSource name="default">
           <dbcnx encrypted="1" login="myLogin" password="myPassword" provider="postgresql" server="myServer"/>
         </dataSource>
       </dataStore>
     </shared>
   
     <mta _autoStart="true" statServerAddress="myStatServer"/>
     <stat _autoStart="true"/>
     <wfserver _autoStart="true"/>
     <inMail _autoStart="true"/>
     <sms _autoStart="false"/>
   </serverconf>
   ```

### Adobe Campaign v6.1의 경우 {#migrating-from-adobe-campaign-v6-1}

1. Adobe Campaign 데이터베이스를 백업합니다.
1. 의 백업 **Adobe Campaign v6** 다음 명령을 사용하는 디렉토리:

   ```
   ren "Adobe Campaign v6" "Adobe Campaign v6.back"
   ```

   >[!IMPORTANT]
   >
   >예방 조치로, **Adobe Campaign v6.back** 폴더를 만든 다음 서버 이외의 안전한 위치에 저장합니다.

1. windows 서비스 관리 콘솔에서 6.11 응용 프로그램 서버 서비스의 자동 시작을 비활성화합니다. 다음 명령을 사용할 수도 있습니다.

   ```
   sc config nlserver6 start= disabled
   ```

## Adobe Campaign v7 배포 {#deploying-adobe-campaign-v7}

Adobe Campaign 배포에는 두 단계가 있습니다.

* 빌드 v7 설치: 이 작업은 각 서버에서 수행해야 합니다.
* 업그레이드 후: 이 명령은 각 인스턴스에서 시작해야 합니다.

Adobe Campaign을 배포하려면 다음 단계를 수행합니다.

1. 를 실행하여 최신 Adobe Campaign v7 빌드를 설치합니다 **setup.exe** 설치 파일입니다. Windows에서 Adobe Campaign 서버 설치에 대한 자세한 내용은 [이 섹션](../../installation/using/installing-the-server.md).

   ![](assets/migration_wizard_1_7.png)

   >[!NOTE]
   >
   >Adobe Campaign v7는 기본적으로 **C:\Program Files\Adobe\Adobe Campaign v7** 디렉토리.

1. 클라이언트 콘솔 설치 프로그램을 사용하려면 **setup-client-7.0.XXXX.exe** 파일을 Adobe Campaign 설치 디렉토리에 넣습니다. **C:\Program Files\Adobe\Adobe Campaign v7\datakit\nl\eng\jsp**.

   >[!NOTE]
   >
   >Windows에서 Adobe Campaign 설치에 대한 자세한 내용은 [이 섹션](../../installation/using/installing-the-server.md).

1. 다음 명령을 사용하여 처음 사용할 인스턴스를 시작합니다.

   ```
   net start nlserver6-v7
   net stop nlserver6-v7
   ```

   >[!NOTE]
   >
   >이러한 명령을 사용하여 Adobe Campaign v7 내부 파일 시스템을 만들 수 있습니다. **conf** 디렉토리( **config-default.xml** 및 **serverConf.xml** 파일), **var** 디렉토리 등

1. 를 통해 각 인스턴스의 구성 파일 및 하위 폴더를 복사하여 붙여넣기(덮어쓰기) **Neolane v5.back**, **Neolane v6.back** 또는 **Adobe Campaign v6.back** 백업 파일(마이그레이션 중인 버전에 따라 - 참조 [이 섹션](#back-up-the-database-and-the-current-installation)).
1. 마이그레이션하려는 버전에 따라 다음 명령을 실행합니다.

   ```
   copy "Neolane v5.back"/conf/config-<instance name>.xml "Adobe Campaign v7"/conf/
   copy "Neolane v5.back"/customers/* "Adobe Campaign v7"/customers/
   copy "Neolane v5.back"/var/* "Adobe Campaign v7"/var/
   ```

   ```
   copy "Neolane v6.back"/conf/config-<instance name>.xml "Adobe Campaign v7"/conf/
   copy "Neolane v6.back"/customers/* "Adobe Campaign v7"/customers/
   copy "Neolane v6.back"/var/* "Adobe Campaign v7"/var/
   ```

   ```
   copy "Adobe Campaign v6.back"/conf/config-<instance name>.xml "Adobe Campaign v7"/conf/
   copy "Adobe Campaign v6.back"/customers/* "Adobe Campaign v7"/customers/
   copy "Adobe Campaign v6.back"/var/* "Adobe Campaign v7"/var/
   ```

   >[!IMPORTANT]
   >
   >위의 첫 번째 명령에 대해 **config-default.xml** 파일.

1. 에서 **serverConf.xml** 및 **config-default.xml** Adobe Campaign v7 파일의 경우 Adobe Campaign 이전 버전에서 지정한 특정 구성을 적용합니다. 대상 **serverConf.xml** 파일에서 **Neolane v5/conf/serverConf.xml.diff**, **Neolane v6/conf/serverConf.xml.diff** 또는 **Adobe Campaign v6/conf/serverConf.xml.diff** 파일.

   >[!NOTE]
   >
   >Adobe Campaign 이전 버전에서 Adobe Campaign v7로 구성을 보고할 때 실제 디렉토리에 대한 경로가 Adobe Campaign v7(Neolane v5, Neolane v6 또는 Adobe Campaign v6가 아님)로 연결되는지 확인하십시오.

1. 다음 명령을 사용하여 Adobe Campaign v7 구성을 다시 로드합니다.

   ```
   nlserver config -reload
   ```

1. 다음 명령을 사용하여 업그레이드 후 프로세스를 시작합니다.

   ```
   nlserver config -postupgrade -instance:<instance name>
   ```

>[!IMPORTANT]
>
>아직 Adobe Campaign 서비스를 시작하지 마십시오. IIS에서 일부 변경 작업을 수행해야 합니다.

## 리디렉션 서버 마이그레이션 {#migrating-the-redirection-server--iis-}

이 단계에서는 IIS 서버를 중지해야 합니다. 을(를) 참조하십시오. [서비스 중지](#service-stop).

1. 를 엽니다. **IIS(인터넷 정보 서비스) 관리자** 콘솔.
1. Adobe Campaign 이전 버전에 사용되는 사이트의 바인딩(수신 포트)을 변경합니다.

   * Adobe Campaign 이전 버전에 사용된 사이트를 마우스 오른쪽 단추로 클릭하고 를 선택합니다 **[!UICONTROL Edit bindings]**.
   * 각 수신 포트 유형에 대해 (**[!UICONTROL http]** 및/또는 **[!UICONTROL https]**). 적절한 줄을 선택하고 를 클릭합니다 **[!UICONTROL Edit]**.
   * 다른 포트를 입력합니다. 기본적으로 수신 포트는 http의 경우 80이고 https의 경우 443입니다. 새 포트를 사용할 수 있는지 확인합니다.

      ![](assets/_migration_iis_3_611.png)

      >[!NOTE]
      >
      >IIS 서버에 고급 구성(공유 포트 및 다른 IP 주소)을 사용하는 Adobe Campaign용 웹 사이트가 여러 개 포함된 경우 관리자에게 문의하십시오.

1. Adobe Campaign v7용 새 웹 사이트 만들기:

   * 마우스 오른쪽 단추를 클릭합니다. **[!UICONTROL Sites]** 폴더를 선택하고 **[!UICONTROL Add Web Site...]**.

      ![](assets/_migration_iis_4.png)

   * 사이트의 이름을 입력합니다. **Adobe Campaign v7** 예를 들어,
   * 웹 사이트의 기본 디렉터리에 대한 액세스 경로는 사용되지 않지만 **[!UICONTROL Physical access path]** 필드를 입력해야 합니다. 기본 IIS 액세스 경로를 입력하십시오. **C:\inetpub\wwwroot**.
   * 을(를) 클릭합니다. **[!UICONTROL Connect as...]** 버튼을 누르고 **[!UICONTROL Application user]** 옵션이 선택되어 있습니다.
   * 기본값을 **[!UICONTROL IP address]** 및 **[!UICONTROL Port]** 필드. 다른 값을 사용하려면 IP 주소 및/또는 포트를 사용할 수 있는지 확인하십시오.
   * 을(를) 확인합니다. **[!UICONTROL Start Web site immediately]** 상자.

      ![](assets/_migration_iis_5_7.png)

1. 를 실행합니다 **iis_neolane_setup.vbs** 앞에서 만든 가상 디렉터리에서 Adobe Campaign 서버가 사용하는 리소스를 자동으로 구성하는 스크립트입니다.

   * 이 파일은 **`[Adobe Campaign v7]`\conf** 디렉토리, 위치 **`[Adobe Campaign v7]`** 은 Adobe Campaign 설치 디렉토리의 액세스 경로입니다. 스크립트를 실행하는 명령은 다음과 같습니다(관리자용).

      ```
      cd C:\Program Files (x86)\Adobe Campaign\Adobe Campaign v7\conf
      cscript iis_neolane_setup.vbs
      ```

   * 클릭 **[!UICONTROL OK]** 스크립트 실행을 확인하려면 다음을 수행하십시오.

      ![](assets/s_ncs_install_iis7_parameters_step2_7.png)

   * Adobe Campaign v7용으로 이전에 만든 웹 사이트의 수를 입력하고 **[!UICONTROL OK]**.

      ![](assets/s_ncs_install_iis7_parameters_step3_7.png)

   * 확인 메시지가 표시됩니다.

      ![](assets/s_ncs_install_iis7_parameters_step7_7.png)

   * 에서 **[!UICONTROL Content view]** 탭에서 웹 사이트 구성이 Adobe Campaign 리소스로 올바르게 구성되었는지 확인합니다.

      ![](assets/s_ncs_install_iis7_parameters_step6_7.png)

      >[!NOTE]
      >
      >트리 구조가 표시되지 않으면 IIS를 다시 시작하십시오.
      >
      >다음 IIS 구성 단계는 [이 섹션](../../installation/using/integration-into-a-web-server-for-windows.md#configuring-the-iis-web-server).

## 보안 영역 {#security-zones}

v6.02 이전 버전에서 마이그레이션하는 경우 서비스를 시작하기 전에 보안 영역을 구성해야 합니다. [자세히 알아보기](../../migration/using/general-configurations.md#security)

## 서비스 다시 시작 {#re-starting-the-services}

다음 각 서버에서 IIS 및 Adobe Campaign 서비스를 시작합니다.

1. 추적 및 리디렉션 서버입니다.
1. 중간 소싱 서버.
1. 마케팅 서버입니다.

다음 단계로 이동하기 전에 새 설치에 대한 전체 테스트를 실행하고 회귀를 수행하지 않는지 그리고 의 모든 권장 사항을 수행하여 모든 것이 작동하는지 확인합니다. [이 페이지](../../migration/using/general-configurations.md).

## 이전 버전을 삭제합니다 {#deleting-and-cleansing-adobe-campaign-previous-version}

절차는 Adobe Campaign 이전 버전에 따라 다릅니다.

### Adobe Campaign v5용 {#adobe-campaign-v5}

Adobe Campaign v5 설치를 삭제하고 정리하려면 먼저 다음 권장 사항을 적용해야 합니다.

* 기능 팀이 새 설치를 모두 점검하도록 합니다.
* 롤백이 필요하지 않은지 확인한 후 Adobe Campaign v5만 제거하십시오.

1. IIS에서 **Neolane v5** 웹 사이트, **Neolane v5** 응용 프로그램 풀.
1. 이름 바꾸기 **Neolane v5.back** 폴더로 **Neolane v5**.
1. 구성 요소 추가/제거 마법사를 사용하여 Adobe Campaign v5를 제거합니다.

   ![](assets/migration_wizard_2.png)

1. 삭제 **nlserver5** 다음 명령을 사용하는 Windows 서비스:

   ```
   sc delete nlserver5
   ```

1. 서버를 다시 시작합니다.

### Adobe Campaign v6.02의 경우 {#adobe-campaign-v6-02}

Adobe Campaign v6.02 설치를 삭제하고 정리하려면 먼저 다음 권장 사항을 적용해야 합니다.

* 기능 팀이 새 설치를 모두 점검하도록 합니다.
* 롤백이 필요하지 않은지 확인한 후 Adobe Campaign v6.02만 제거하십시오.

1. IIS에서 **Neolane v6** 웹 사이트, **Neolane v6** 응용 프로그램 풀.
1. 이름 바꾸기 **Neolane v6.back** 폴더로 **Neolane v6**.
1. 구성 요소 추가/제거 마법사를 사용하여 Adobe Campaign v6.02를 제거합니다.

   ![](assets/migration_wizard_2.png)

1. 서버를 다시 시작합니다.

### Adobe Campaign v6.1의 경우 {#adobe-campaign-v6-1}

Adobe Campaign v6 설치를 삭제하고 정리하려면 먼저 다음 권장 사항을 적용해야 합니다.

* 기능 팀이 새 설치를 모두 점검하도록 합니다.
* 롤백이 필요하지 않은지 확인한 후 Adobe Campaign v6만 제거하십시오.

1. IIS에서 **Adobe Campaign v6** 웹 사이트, **Adobe Campaign v6** 응용 프로그램 풀.
1. 이름 바꾸기 **Adobe Campaign v6.back** 폴더로 **Adobe Campaign v6**.
1. 구성 요소 추가/제거 마법사를 사용하여 Adobe Campaign v6를 제거합니다.

   ![](assets/migration_wizard_2.png)

1. 서버를 다시 시작합니다.
