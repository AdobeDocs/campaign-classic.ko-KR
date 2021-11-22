---
product: campaign
title: Snowflake 액세스 구성
description: FDA에서 Snowflake 액세스를 구성하는 방법을 배웁니다.
audience: platform
content-type: reference
topic-tags: connectors
exl-id: bdb5e422-ecfe-42eb-bd15-39fe5ec0ff1d
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 10%

---

# Snowflake 액세스 구성 {#configure-access-to-snowflake}

![](../../assets/v7-only.svg)

캠페인 사용 **페더레이션 데이터 액세스** (FDA) 옵션을 사용하여 외부 데이터베이스에 저장된 정보를 처리합니다. 아래 절차에 따라 액세스 권한을 구성하십시오 [!DNL Snowflake].

1. 구성 [!DNL Snowflake] on [CentOS](#snowflake-centos), [Windows](#snowflake-windows) 또는 [데비안](#snowflake-debian)
1. 구성 [!DNL Snowflake] [외부 계정](#snowflake-external) in Campaign


>[!NOTE]
>
>[!DNL Snowflake] 커넥터는 호스팅 및 온-프레미스 배포에 사용할 수 있습니다. 자세한 정보는 이 [페이지](../../installation/using/capability-matrix.md)를 참조하십시오.

![](assets/snowflake_3.png)

## CentOS의 Snowflake {#snowflake-centos}

구성하려면 [!DNL Snowflake] centOS에서 아래 절차를 따르십시오.

1. ODBC 드라이버 다운로드 [!DNL Snowflake]. [여기를 클릭하십시오.](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/snowflake-odbc-2.20.2.x86_64.rpm) 다운로드 를 시작하려면 다음을 수행하십시오.
1. 다음 명령을 사용하여 CentOs에 ODBC 드라이버를 설치해야 합니다.

   ```
   rpm -Uvh unixodbc
   rpm -Uvh snowflake-odbc-2.20.2.x86_64.rpm
   ```

1. ODBC 드라이버를 다운로드하여 설치한 후에는 Campaign Classic을 다시 시작해야 합니다. 이렇게 하려면 다음 명령을 실행합니다.

   ```
   /etc/init.d/nlserver6 stop
   /etc/init.d/nlserver6 start
   ```

1. Campaign에서 다음을 구성할 수 있습니다 [!DNL Snowflake] 외부 계정. 외부 계정을 구성하는 방법에 대한 자세한 내용은 [이 섹션](#snowflake-external).

## Windows의 Snowflake {#snowflake-windows}

1. 다운로드 [Windows용 ODBC 드라이버](https://docs.snowflake.net/manuals/user-guide/odbc-download.html). 드라이버를 설치하려면 관리자 수준 권한이 필요합니다. 자세한 정보는 이 [페이지](https://docs.snowflake.net/manuals/user-guide/admin-user-management.html)를 참조하십시오

1. ODBC 드라이버를 구성합니다. 자세한 정보는 이 [페이지](https://docs.snowflake.net/manuals/user-guide/odbc-windows.html#step-2-configure-the-odbc-driver)를 참조하십시오

1. Campaign에서 다음을 구성할 수 있습니다 [!DNL Snowflake] 외부 계정. 외부 계정을 구성하는 방법에 대한 자세한 내용은 [이 섹션](#snowflake-external).

## 데비안 Snowflake {#snowflake-debian}

1. ODBC 드라이버 다운로드 [!DNL Snowflake]. [여기를 클릭하십시오.](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html) 다운로드를 시작합니다.

1. 다음 명령을 사용하여 Debian에 ODBC 드라이버를 설치해야 합니다.

   ```
   apt-get install unixodbc
   apt-get install snowflake-odbc-x.xx.x.x86_64.deb
   ```

1. ODBC 드라이버를 다운로드하여 설치한 후에는 Campaign Classic을 다시 시작해야 합니다. 이렇게 하려면 다음 명령을 실행합니다.

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. Campaign에서 다음을 구성할 수 있습니다 [!DNL Snowflake] 외부 계정. 외부 계정을 구성하는 방법에 대한 자세한 내용은 [이 섹션](#snowflake-external).

## 외부 계정 Snowflake {#snowflake-external}

을(를) 만들어야 합니다 [!DNL Snowflake] 캠페인 인스턴스를 [!DNL Snowflake] 외부 데이터베이스.

1. Campaign에서 **[!UICONTROL Explorer]**&#x200B;를 클릭합니다. **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. **[!UICONTROL New]**&#x200B;를 클릭합니다.

1. 선택 **[!UICONTROL External database]** 외부 계정 **[!UICONTROL Type]**.

1. 구성 **[!UICONTROL Snowflake]** 외부 계정입니다. 다음을 지정해야 합니다.

   * **[!UICONTROL Type]**: [!DNL Snowflake]

   * **[!UICONTROL Server]**: 의 URL [!DNL Snowflake] server

   * **[!UICONTROL Account]**: 사용자의 이름

   * **[!UICONTROL Password]**: 사용자 계정 암호

   * **[!UICONTROL Database]**: 데이터베이스 이름

   ![](assets/snowflake.png)

1. 을(를) 클릭합니다. **[!UICONTROL Parameters]** 탭을 클릭한 다음 **[!UICONTROL Deploy functions]** 버튼을 클릭하여 함수를 만듭니다.

   ![](assets/snowflake_2.png)

커넥터는 다음 옵션을 지원합니다.

| 옵션 | 설명 |
|---|---|
| 작업 스키마 | 작업 테이블에 사용할 데이터베이스 스키마 |
| 데이터 웨어하우스 | 사용할 기본 웨어하우스의 이름입니다. 사용자의 기본값을 덮어씁니다. |
| 표준 시간대 이름 | 기본적으로 비어 있음: Campaign Classic 앱 서버의 시스템 시간대가 사용됨을 의미합니다. 옵션을 사용하여 TIMEZONE 세션 매개 변수를 강제 적용할 수 있습니다. <br>자세한 정보는 이 [페이지](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone)를 참조하십시오. |
| WeekStart | WEEK_START 세션 매개 변수입니다. 기본적으로 0으로 설정됩니다. <br>자세한 정보는 이 [페이지](https://docs.snowflake.com/en/sql-reference/parameters.html#week-start)를 참조하십시오. |
| UseCachedResult | USE_CACHED_RESULTS 세션 매개변수 기본적으로 TRUE로 설정됩니다. 이 옵션을 사용하여 캐시된 Snowflake 결과를 비활성화할 수 있습니다. <br>자세한 정보는 이 [페이지](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html)를 참조하십시오. |
