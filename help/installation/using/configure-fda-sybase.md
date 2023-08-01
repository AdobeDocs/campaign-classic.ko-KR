---
product: campaign
title: sybase IQ 액세스 구성
description: FDA에서 Sybase IQ에 대한 액세스를 구성하는 방법 알아보기
feature: Installation, Federated Data Access
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용됩니다."
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 0fdf8259-5cab-4a9d-adb3-6c55ec5c8851
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 1%

---

# sybase IQ 액세스 구성 {#configure-access-to-sybase-iq}



Campaign 사용 **페더레이션 데이터 액세스** (FDA) 외부 데이터베이스에 저장된 정보를 처리하는 옵션. sybase IQ에 대한 액세스를 구성하려면 아래 단계를 따르십시오.

1. 구성 [Sybase IQ 데이터베이스](#configuring-sybase)
1. sybase IQ 구성 [외부 계정](#sybase-external) 캠페인에서

## Sybase IQ 구성 {#configuring-sybase}

FDA에서 Sybase IQ 외부 데이터베이스에 연결하려면 Adobe Campaign 서버에서 아래 추가 구성이 필요합니다.

>[!NOTE]
>
>시작하기 전에 다음을 확인하십시오 **unixodbc** 패키지가 서버에 있습니다.

1. 설치 **iq_odbc**. 설치 종료 시 오류가 발생할 수 있습니다. 이 오류는 무시할 수 있습니다.

1. 설치 **iq_client_common**. 설치 종료 시 Java 오류가 발생할 수 있습니다. 이 오류는 무시할 수 있습니다.

1. ODBC 드라이버를 구성합니다. 일반 매개 변수의 경우 /etc/odbc.ini에서, 드라이버를 선언하는 경우 /etc/odbcinst.ini에서 구성을 수행할 수 있습니다.

   * **/etc/odbc.ini** (다음과 같이 값 바꾸기) `<server_alias>` 자(직접 입력):

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

1. LD_LIBRARY_PATH 변수에 새 libodbc16.so 라이브러리의 경로를 추가합니다. 방법은 다음과 같습니다.

   * customer.sh 파일을 사용하여 경로를 선언하는 경우: LD_LIBRARY_PATH 변수에 대한 경로 /opt/sybase/IQ-16_0/lib64를 추가합니다.
   * 그렇지 않으면 Unix 명령을 사용합니다.

## Sybase IQ 외부 계정 {#sybase-external}

sybase IQ 외부 계정을 사용하면 Campaign 인스턴스를 Sybase IQ 외부 데이터베이스에 연결할 수 있습니다.

1. 출처: Campaign **[!UICONTROL Explorer]**, 클릭 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. 클릭 **[!UICONTROL New]** 및 선택 **[!UICONTROL External database]** 다음으로: **[!UICONTROL Type]**.

1. 을(를) 구성하려면 다음을 수행하십시오. **[!UICONTROL Sybase IQ]** 외부 계정에서 다음을 지정해야 합니다.

   * **[!UICONTROL Type]**: ODBC (Sybase ASE, Sybase IQ)

   * **[!UICONTROL Server]**: ODBC 연결에 해당합니다(`<server_alias>`)을 추가합니다. 반드시 서버 자체의 이름은 아닙니다.

   * **[!UICONTROL Account]**: 사용자 이름

   * **[!UICONTROL Password]**: 사용자 계정 암호

   * **[!UICONTROL Database]**: 데이터베이스 이름

>[!NOTE]
>
>Windows의 경우 Adobe Campaign 서버에 Sybase IQ 클라이언트를 설치하고 ODBC 연결을 만들어야 합니다. Adobe Campaign 서버(nlserver)가 Windows에서 서비스로 실행될 때 시스템 데이터 소스를 만들어야 합니다.
