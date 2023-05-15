---
product: campaign
title: netezza 액세스 구성
description: FDA에서 Netezza 액세스를 구성하는 방법을 배웁니다.
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: b148d34b-4060-4c54-9cb2-9e712a7c17d7
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# netezza 액세스 구성 {#configure-access-to-netezza}



캠페인 사용 [페더레이션 데이터 액세스](../../installation/using/about-fda.md) (FDA) 옵션을 사용하여 외부 데이터베이스에 저장된 정보를 처리합니다. netezza 액세스를 구성하려면 아래 단계를 따르십시오.

1. 설치 및 구성 [Netezza 드라이버](#netezza-config)
1. netezza 구성 [외부 계정](#netezza-external) in Campaign

## Netezza 구성 {#netezza-config}

FDA에서 Netezza 외부 데이터베이스에 연결하려면 Adobe Campaign 서버에서 아래에 추가 구성이 필요합니다.

1. 사용하는 운영 체제에 따라 Netezza용 ODBC 드라이버를 설치합니다.

   * **nz linux-xclient-v7.2.0.0.tar.gz** Linux용 운영 체제(linux 또는 linux64)에 해당하는 폴더를 선택하고 압축 해제 명령을 시작합니다. 기본적으로 제안되는 저장소에서 설치가 수행되도록 둘 수 있습니다. &quot;/usr/local/nz&quot;
   * **nz-winclient-v7.2.0.0.zip** Windows용 파일의 압축을 풀고 운영 체제에 해당하는 실행 파일을 시작합니다. nzodbcsetup.exe 또는 nzodbcsetup64.exe 마법사 지침에 따라 드라이버 설치를 완료합니다.

1. ODBC 드라이버를 구성합니다. 구성은 표준 파일에서 수행할 수 있습니다. **/etc/odbc.ini** 일반 매개 변수와 **/etc/odbcinst.ini** 드라이버 선언

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

   * **LD_LIBRARY_PATH**: /usr/local/nz/lib 및 /usr/local/nz/lib64 &quot;/usr/local/nz&quot;는 드라이버를 설치할 때 기본적으로 제공되는 설치 저장소에 해당합니다. 여기에서 설치를 위해 선택한 저장소를 지정해야 합니다.
   * **오디치니**: odbc.ini 파일의 위치(예: /etc/odbc.ini)입니다.
   * **NZ_ODBC_INI_PATH**: odbc.ini 파일의 위치입니다. Netezza은 odbc.ini 파일을 사용하는 데 이 두 번째 변수도 필요합니다.

## 외부 계정 netezza {#netezza-external}

netezza 외부 계정을 사용하면 Campaign 인스턴스를 Netezza 외부 데이터베이스에 연결할 수 있습니다.

1. Campaign에서 **[!UICONTROL Explorer]**&#x200B;를 클릭합니다. **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. 클릭 **[!UICONTROL New]** 을(를) 선택합니다. **[!UICONTROL External database]** 로서의 **[!UICONTROL Type]**.

1. 를 구성하려면 **[!UICONTROL Netezza]** 외부 계정입니다. 다음을 지정해야 합니다.

   * **[!UICONTROL Type]**: Netezza

   * **[!UICONTROL Server]**: netezza 서버의 URL

   * **[!UICONTROL Account]**: 사용자의 이름

   * **[!UICONTROL Password]**: 사용자 계정 암호

   * **[!UICONTROL Database]**: 데이터베이스 이름

>[!NOTE]
>
>자동으로 생성된 기본 키가 포함된 스키마에 대한 작업은 고려되지 않습니다.
>
>테이블이 **설정** 스키마에 정의된 첫 번째 인덱스에 대한 절. 이 절은 Netezza이 있는 열 1~4개로 제한되므로 이 인덱스는 4개 이상의 열을 포함할 수 없습니다.
