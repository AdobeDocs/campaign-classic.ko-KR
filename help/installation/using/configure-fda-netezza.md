---
product: campaign
title: netezza 액세스 구성
description: FDA에서 Netezza 액세스를 구성하는 방법 알아보기
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: b148d34b-4060-4c54-9cb2-9e712a7c17d7
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# netezza 액세스 구성 {#configure-access-to-netezza}



외부 데이터베이스에 저장된 정보를 처리하려면 Campaign [FDA(Federated Data Access](../../installation/using/about-fda.md)) 옵션을 사용하십시오. netezza 액세스를 구성하려면 아래 단계를 따르십시오.

1. [Netezza 드라이버 설치 및 구성](#netezza-config)
1. Campaign에서 Netezza [외부 계정](#netezza-external) 구성

## Netezza 구성 {#netezza-config}

FDA에서 Netezza 외부 데이터베이스에 연결하려면 Adobe Campaign 서버에서 아래 추가 구성이 필요합니다.

1. 사용하는 운영 체제에 따라 Netezza용 ODBC 드라이버를 설치합니다.

   * Linux용 **nz-linuxclient-v7.2.0.0.tar.gz**. 운영 체제(linux 또는 linux64)에 해당하는 폴더를 선택하고 unpack 명령을 시작합니다. 기본적으로 제안된 저장소에 설치를 수행할 수 있습니다. &quot;/usr/local/nz&quot;.
   * Windows용 **nz-winclient-v7.2.0.0.zip**. 파일의 압축을 풀고 운영 체제에 해당하는 실행 스크립트 nzodbcsetup.exe 또는 nzodbcsetup64.exe를 시작합니다. 마법사 지침에 따라 드라이버 설치를 완료합니다.

1. ODBC 드라이버를 구성합니다. 일반 매개 변수의 경우 **/etc/odbc.ini**, 드라이버 선언의 경우 **/etc/odbcinst.ini** 표준 파일에서 구성을 수행할 수 있습니다.

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
   * **ODBCINI**: odbc.ini 파일의 위치입니다(예: /etc/odbc.ini).
   * **NZ_ODBC_INI_PATH**: odbc.ini 파일의 위치입니다. Netezza을 사용하려면 odbc.ini 파일을 사용하려면 이 두 번째 변수도 필요합니다.

## 외부 계정 netezza {#netezza-external}

netezza 외부 계정을 사용하면 Campaign 인스턴스를 Netezza 외부 데이터베이스에 연결할 수 있습니다.

1. **[!UICONTROL Explorer]** 캠페인에서 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**&#x200B;을(를) 클릭합니다.

1. **[!UICONTROL New]**&#x200B;을(를) 클릭하고 **[!UICONTROL External database]**&#x200B;을(를) **[!UICONTROL Type]**(으)로 선택합니다.

1. **[!UICONTROL Netezza]** 외부 계정을 구성하려면 다음을 지정해야 합니다.

   * **[!UICONTROL Type]**: Netezza

   * **[!UICONTROL Server]**: Netezza 서버의 URL

   * **[!UICONTROL Account]**: 사용자 이름

   * **[!UICONTROL Password]**: 사용자 계정 암호

   * **[!UICONTROL Database]**: 데이터베이스 이름

>[!NOTE]
>
>자동으로 생성된 기본 키가 포함된 스키마에 대한 작업은 고려되지 않습니다.
>
>스키마에 정의된 첫 번째 인덱스에서 **Organize on** 절을 사용합니다. 이 절은 Netezza이 있는 1~4개의 열로 제한되므로 이 인덱스는 4개 이상의 열을 포함할 수 없습니다.
