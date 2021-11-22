---
product: campaign
title: Sybase IQ 액세스 구성
description: FDA에서 Sybase IQ 액세스를 구성하는 방법을 배웁니다.
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 0fdf8259-5cab-4a9d-adb3-6c55ec5c8851
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Sybase IQ 액세스 구성 {#configure-access-to-sybase-iq}

![](../../assets/v7-only.svg)

캠페인 사용 **페더레이션 데이터 액세스** (FDA) 옵션을 사용하여 외부 데이터베이스에 저장된 정보를 처리합니다. 아래 절차에 따라 Sybase IQ 액세스를 구성합니다.

1. 구성 [sybase IQ 데이터베이스](#configuring-sybase)
1. Sybase IQ 구성 [외부 계정](#sybase-external) in Campaign

## sybase IQ 구성 {#configuring-sybase}

FDA에서 Sybase IQ 외부 데이터베이스에 연결하려면 Adobe Campaign 서버에서 아래에 추가 구성이 필요합니다.

>[!NOTE]
>
>시작하기 전에 **unixodbc** 패키지가 서버에 있습니다.

1. 설치 **iq_odbc**. 설치 종료 시 오류가 발생할 수 있습니다. 이 오류는 무시할 수 있습니다.

1. 설치 **iq_client_common**. 설치 종료 시 Java 오류가 발생할 수 있습니다. 이 오류는 무시할 수 있습니다.

1. ODBC 드라이버를 구성합니다. 구성은 표준 파일에서 수행할 수 있습니다. 일반 매개 변수의 경우 /etc/odbc.ini, 드라이버 선언의 경우 /etc/odbcinst.ini:

   * **/etc/odbc.ini** 다음 값 바꾸기 `<server_alias>` 문자 수:

      ```
      [ODBC Data Sources]
      <server_alias>=libdbodbc.so
      
      [<server_alias>]
      Driver=/opt/sybase/IQ-16_0/lib64/libdbodbc16.so
      Description=<description>
      Username=<username>
      Password=<password>
      ServerName=<server_name>
      CommLinks=tcpip(host=<host>)
      ```

   * **/etc/odbcinst.ini**

      ```
      [ODBC DRIVERS]
      SAP SybaseIQ=Installed
      
      [SAP SybaseIQ]
      Driver=/opt/sybase/IQ-16_0/lib64/libdbodbc16.so
      ```

1. LD_LIBRARY_PATH 변수에 새 libodbc16.so 라이브러리에 대한 경로를 추가합니다. 방법은 다음과 같습니다.

   * customer.sh 파일을 사용하여 경로를 선언할 경우: LD_LIBRARY_PATH 변수에 대한 /opt/sybase/IQ-16_0/lib64 경로를 추가합니다.
   * 그렇지 않으면 Unix 명령을 사용합니다.

## sybase IQ 외부 계정 {#sybase-external}

Sybase IQ 외부 계정을 사용하면 Campaign 인스턴스를 Sybase IQ 외부 데이터베이스에 연결할 수 있습니다.

1. Campaign에서 **[!UICONTROL Explorer]**&#x200B;를 클릭합니다. **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. 클릭 **[!UICONTROL New]** 을(를) 선택합니다. **[!UICONTROL External database]** 로서의 **[!UICONTROL Type]**.

1. 를 구성하려면 **[!UICONTROL Sybase IQ]** 외부 계정입니다. 다음을 지정해야 합니다.

   * **[!UICONTROL Type]**: ODBC(Sybase ASE, Sybase IQ)

   * **[!UICONTROL Server]**: ODBC 연결에 해당합니다(`<server_alias>`)에 정의된 횟수 5단계에서 반드시 서버 자체의 이름일 필요는 없습니다.

   * **[!UICONTROL Account]**: 사용자의 이름

   * **[!UICONTROL Password]**: 사용자 계정 암호

   * **[!UICONTROL Database]**: 데이터베이스 이름

>[!NOTE]
>
>Windows의 경우 Adobe Campaign 서버에 Sybase IQ 클라이언트를 설치하고 ODBC 연결을 만들어야 합니다. Adobe Campaign 서버(nlserver)가 Windows에서 서비스로 실행 중일 때 시스템 데이터 소스를 만들어야 합니다.
