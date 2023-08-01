---
product: campaign
title: netezza 액세스 구성
description: FDA에서 Netezza 액세스를 구성하는 방법 알아보기
feature: Installation, Federated Data Access
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용됩니다."
audience: platform
content-type: reference
topic-tags: connectors
exl-id: b148d34b-4060-4c54-9cb2-9e712a7c17d7
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# netezza 액세스 구성 {#configure-access-to-netezza}



Campaign 사용 [페더레이션 데이터 액세스](../../installation/using/about-fda.md) (FDA) 외부 데이터베이스에 저장된 정보를 처리하는 옵션. netezza 액세스를 구성하려면 아래 단계를 따르십시오.

1. 설치 및 구성 [Netezza 드라이버](#netezza-config)
1. netezza 구성 [외부 계정](#netezza-external) 캠페인에서

## Netezza 구성 {#netezza-config}

FDA에서 Netezza 외부 데이터베이스에 연결하려면 Adobe Campaign 서버에서 아래 추가 구성이 필요합니다.

1. 사용하는 운영 체제에 따라 Netezza용 ODBC 드라이버를 설치합니다.

   * **nz-linuxclient-v7.2.0.0.tar.gz** Linux용 운영 체제(linux 또는 linux64)에 해당하는 폴더를 선택하고 unpack 명령을 시작합니다. 기본적으로 제안된 저장소에 설치를 수행할 수 있습니다. &quot;/usr/local/nz&quot;.
   * **nz-winclient-v7.2.0.0.zip** Windows용 파일의 압축을 풀고 운영 체제에 해당하는 실행 스크립트 nzodbcsetup.exe 또는 nzodbcsetup64.exe를 시작합니다. 마법사 지침에 따라 드라이버 설치를 완료합니다.

1. ODBC 드라이버를 구성합니다. 구성은 표준 파일에서 수행할 수 있습니다. **/etc/odbc.ini** 일반 매개 변수 및 **/etc/odbcinst.ini** 드라이버 선언.

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

   * **LD_LIBRARY_PATH**: /usr/local/nz/lib 및 /usr/local/nz/lib64. &quot;/usr/local/nz&quot;는 드라이버를 설치할 때 기본적으로 제공되는 설치 저장소에 해당합니다. 여기에서 설치용으로 선택한 저장소를 지정해야 합니다.
   * **오브치니**: odbc.ini 파일의 위치(예: /etc/odbc.ini)입니다.
   * **NZ_ODBC_INI_PATH**: odbc.ini 파일의 위치입니다. Netezza을 사용하려면 odbc.ini 파일을 사용하려면 이 두 번째 변수도 필요합니다.

## 외부 계정 netezza {#netezza-external}

netezza 외부 계정을 사용하면 Campaign 인스턴스를 Netezza 외부 데이터베이스에 연결할 수 있습니다.

1. 출처: Campaign **[!UICONTROL Explorer]**, 클릭 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. 클릭 **[!UICONTROL New]** 및 선택 **[!UICONTROL External database]** 다음으로: **[!UICONTROL Type]**.

1. 을(를) 구성하려면 다음을 수행하십시오. **[!UICONTROL Netezza]** 외부 계정에서 다음을 지정해야 합니다.

   * **[!UICONTROL Type]**: Netezza

   * **[!UICONTROL Server]**: Netezza 서버의 URL

   * **[!UICONTROL Account]**: 사용자 이름

   * **[!UICONTROL Password]**: 사용자 계정 암호

   * **[!UICONTROL Database]**: 데이터베이스 이름

>[!NOTE]
>
>자동으로 생성된 기본 키가 포함된 스키마에 대한 작업은 고려되지 않습니다.
>
>표에서 **구성 일자** 스키마에 정의된 첫 번째 인덱스의 조항입니다. 이 절은 Netezza이 있는 1~4개의 열로 제한되므로 이 인덱스는 4개 이상의 열을 포함할 수 없습니다.
