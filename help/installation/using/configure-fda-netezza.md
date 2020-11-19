---
title: netezza 액세스 구성
description: FDA에서 Netezza 이용 권한 구성 방법 살펴보기
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
translation-type: tm+mt
source-git-commit: 9bbde65aea6735e30e95e75c2b6ae5445d4a2bdd
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---


# netezza 액세스 구성 {#configure-access-to-netezza}

FDA(Campaign [Federated Data Access](../../installation/using/about-fda.md) ) 옵션을 사용하여 외부 데이터베이스에 저장된 정보를 처리할 수 있습니다. 아래 절차에 따라 Netezza에 대한 액세스를 구성합니다.

1. [Netezza 드라이버 설치 및 구성](#netezza-config)
1. Campaign에서 Netezza [외부 계정](#netezza-external) 구성

## Netezza 구성 {#netezza-config}

FDA에서 Netezza 외부 데이터베이스에 연결하려면 Adobe Campaign 서버에 아래 추가 구성이 필요합니다.

1. 사용하는 운영 체제에 따라 Netezza용 ODBC 드라이버를 설치합니다.

   * **Linux용 nz-linuxclient-v7.2.0.0.tar.gz** . 운영 체제(linux 또는 linux64)에 해당하는 폴더를 선택하고 압축 해제 명령을 시작합니다. 기본적으로 제안된 저장소에서 설치되도록 둘 수 있습니다.&quot;/usr/local/nz&quot;
   * **Windows용 nz-winclient-v7.2.0.0.zip** . 파일의 압축을 풀고 운영 체제에 해당하는 실행 스크립트를 시작합니다.nzodbcsetup.exe 또는 nzodbcsetup64.exe. 마법사 지침에 따라 드라이버 설치를 마칩니다.

1. ODBC 드라이버를 구성합니다. 구성은 표준 파일에서 수행할 수 있습니다. **/etc/odbc.ini** for general parameters and **/etc/odbcinst.ini** for decoring driver.

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      ```

      &quot;InstallDir&quot;은 odbcinst.ini 파일의 위치에 해당합니다.

   * **/etc/odbcinst.ini**

      ```
      [ODBC Drivers]
      NetezzaSQL = Installed
      
      [NetezzaSQL]
      Driver           = /usr/local/nz/lib/libnzsqlodbc3.so
      Setup            = /usr/local/nz/lib/libnzsqlodbc3.so
      APILevel         = 1
      ConnectFunctions = YYN
      Description      = Netezza ODBC driver
      DriverODBCVer    = 03.51
      DebugLogging     = false
      LogPath          = /tmp
      UnicodeTranslationOption = utf8
      CharacterTranslationOption = all
      PreFetch         = 256
      Socket           = 16384
      ```

1. Adobe Campaign 서버의 환경 변수를 지정합니다.

   * **LD_LIBRARY_PATH**:/usr/local/nz/lib 및 /usr/local/nz/lib64. &quot;/usr/local/nz&quot;는 드라이버를 설치할 때 기본적으로 제공되는 설치 저장소에 해당합니다. 여기에서 설치를 위해 선택한 저장소를 지정해야 합니다.
   * **ODBCINI**:odbc.ini 파일의 위치입니다(예: /etc/odbc.ini).
   * **NZ_ODBC_INI_PATH**:odbc.ini 파일의 위치입니다. 또한 netezza은 odbc.ini 파일을 사용하기 위해 이 두 번째 변수를 필요로 합니다.

## Netezza 외부 계정 {#netezza-external}

netezza 외부 계정을 사용하면 캠페인 인스턴스를 Netezza 외부 데이터베이스에 연결할 수 있습니다.

1. 캠페인 **[!UICONTROL Explorer]**&#x200B;에서 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39;을 클릭합니다 **[!UICONTROL External accounts]**.

1. 을 **[!UICONTROL New]** 클릭하고 **[!UICONTROL External database]** 으로 선택합니다 **[!UICONTROL Type]**.

1. 외부 계정을 구성하려면 다음을 **[!UICONTROL Netezza]** 지정해야 합니다.

   * **[!UICONTROL Type]**:Netezza

   * **[!UICONTROL Server]**:netezza 서버의 URL

   * **[!UICONTROL Account]**:사용자의 이름

   * **[!UICONTROL Password]**:사용자 계정 암호

   * **[!UICONTROL Database]**:데이터베이스 이름

>[!NOTE]
>
>자동으로 생성된 기본 키를 포함하는 스키마에 대한 작업은 고려되지 않습니다.
>
>테이블에 스키마에 정의된 첫 번째 인덱스의 **Organize on** 절을 사용합니다. 이 절은 Netezza이 있는 1-4개의 열로 제한되므로 이 색인은 4개 이상의 열을 포함할 수 없습니다.
