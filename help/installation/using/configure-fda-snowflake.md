---
solution: Campaign Classic
product: campaign
title: Snowflake 액세스 구성
description: FDA에서 Snowflake 액세스를 구성하는 방법 살펴보기
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 535339b5a9b39625100d630b0b831df143dbeb01
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 10%

---


# Snowflake {#configure-access-to-snowflake} 액세스 구성

외부 데이터베이스에 저장된 정보를 처리하려면 캠페인 **통합 데이터 액세스**(FDA) 옵션을 사용합니다. [!DNL Snowflake]에 대한 액세스를 구성하려면 아래 단계를 따르십시오.

1. [CentOS](#snowflake-centos), [Windows](#snowflake-windows) 또는 [Debian](#snowflake-debian)에서 [!DNL Snowflake] 구성
1. Campaign에서 [!DNL Snowflake] [외부 계정](#snowflake-external) 구성


>[!NOTE]
>
>[!DNL Snowflake] 커넥터는 호스팅 및 온-프레미스 배포에 사용할 수 있습니다. 자세한 정보는 이 [페이지](../../installation/using/capability-matrix.md)를 참조하십시오.

![](assets/snowflake_3.png)

## CentOS {#snowflake-centos}의 Snowflake

CentOS에서 [!DNL Snowflake]을(를) 구성하려면 아래 단계를 따르십시오.

1. [!DNL Snowflake]용 ODBC 드라이버를 다운로드합니다. [여기를 ](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/snowflake-odbc-2.20.2.x86_64.rpm) 클릭하여 다운로드를 시작합니다.
1. 그런 다음 다음 다음 명령을 사용하여 CentOs에 ODBC 드라이버를 설치해야 합니다.

   ```
   rpm -Uvh unixodbc
   rpm -Uvh snowflake-odbc-2.20.2.x86_64.rpm
   ```

1. ODBC 드라이버를 다운로드하고 설치한 후에는 Campaign Classic을 다시 시작해야 합니다. 이렇게 하려면 다음 명령을 실행합니다.

   ```
   /etc/init.d/nlserver6 stop
   /etc/init.d/nlserver6 start
   ```

1. 그런 다음 Campaign에서 [!DNL Snowflake] 외부 계정을 구성할 수 있습니다. 외부 계정을 구성하는 방법에 대한 자세한 내용은 [이 섹션](#snowflake-external)을 참조하십시오.

## Windows {#snowflake-windows}의 Snowflake

1. Windows](https://docs.snowflake.net/manuals/user-guide/odbc-download.html)용 [ODBC 드라이버를 다운로드합니다. 드라이버를 설치하려면 관리자 수준 권한이 필요합니다. 자세한 정보는 이 [페이지](https://docs.snowflake.net/manuals/user-guide/admin-user-management.html)를 참조하십시오

1. ODBC 드라이버를 구성합니다. 자세한 정보는 이 [페이지](https://docs.snowflake.net/manuals/user-guide/odbc-windows.html#step-2-configure-the-odbc-driver)를 참조하십시오

1. 그런 다음 Campaign에서 [!DNL Snowflake] 외부 계정을 구성할 수 있습니다. 외부 계정을 구성하는 방법에 대한 자세한 내용은 [이 섹션](#snowflake-external)을 참조하십시오.

## Debian {#snowflake-debian}의 Snowflake

1. [!DNL Snowflake]용 ODBC 드라이버를 다운로드합니다. [다운로드를 다시 ](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html) 시작합니다.

1. 그런 다음 다음 다음 명령을 사용하여 Debian에 ODBC 드라이버를 설치해야 합니다.

   ```
   apt-get install unixodbc
   apt-get install snowflake-odbc-x.xx.x.x86_64.deb
   ```

1. ODBC 드라이버를 다운로드하고 설치한 후에는 Campaign Classic을 다시 시작해야 합니다. 이렇게 하려면 다음 명령을 실행합니다.

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. 그런 다음 Campaign에서 [!DNL Snowflake] 외부 계정을 구성할 수 있습니다. 외부 계정을 구성하는 방법에 대한 자세한 내용은 [이 섹션](#snowflake-external)을 참조하십시오.

## Snowflake 외부 계정 {#snowflake-external}

캠페인 인스턴스를 [!DNL Snowflake] 외부 데이터베이스에 연결하려면 [!DNL Snowflake] 외부 계정을 만들어야 합니다.

1. 캠페인 **[!UICONTROL Explorer]**&#x200B;에서 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**&#x200B;을(를) 클릭합니다.

1. **[!UICONTROL New]**&#x200B;을(를) 클릭합니다.

1. 외부 계정의 **[!UICONTROL Type]**&#x200B;으로 **[!UICONTROL External database]**&#x200B;을 선택합니다.

1. **[!UICONTROL Snowflake]** 외부 계정을 구성합니다. 다음을 지정해야 합니다.

   * **[!UICONTROL Type]**: [!DNL Snowflake]

   * **[!UICONTROL Server]**:서버의  [!DNL Snowflake] URL

   * **[!UICONTROL Account]**:사용자 이름

   * **[!UICONTROL Password]**:사용자 계정 암호

   * **[!UICONTROL Database]**:데이터베이스의 이름

   ![](assets/snowflake.png)

1. **[!UICONTROL Parameters]** 탭을 클릭한 다음 **[!UICONTROL Deploy functions]** 단추를 클릭하여 함수를 만듭니다.

   ![](assets/snowflake_2.png)

커넥터는 다음 옵션을 지원합니다.

| 옵션 | 설명 |
|---|---|
| 작업 스키마 | 작업 테이블에 사용할 데이터베이스 스키마 |
| warehouse | 사용할 기본 웨어하우스의 이름입니다. 이 값은 사용자의 기본값을 무시합니다. |
| TimeZoneName | 기본적으로 비어 있으면 Campaign Classic 앱 서버의 시스템 시간대가 사용됩니다. 이 옵션을 사용하여 TIMEZONE 세션 매개 변수를 강제 적용할 수 있습니다. <br>자세한 정보는 이 [페이지](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone)를 참조하십시오. |
| WeekStart | WEEK_START 세션 매개 변수. 기본적으로 0으로 설정됩니다. <br>자세한 정보는 이 [페이지](https://docs.snowflake.com/en/sql-reference/parameters.html#week-start)를 참조하십시오. |
| UseCachedResult | USE_CACHED_RESULTS 세션 매개 변수. 기본적으로 TRUE로 설정됩니다. 이 옵션을 사용하여 캐시된 Snowflake 결과를 비활성화할 수 있습니다. <br>자세한 정보는 이 [페이지](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html)를 참조하십시오. |
