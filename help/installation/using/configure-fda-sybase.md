---
solution: Campaign Classic
product: campaign
title: sybase IQ 액세스 권한 구성
description: FDA에서 Sybase IQ에 대한 액세스를 구성하는 방법 살펴보기
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---


# sybase IQ {#configure-access-to-sybase-iq}에 대한 액세스 구성

캠페인 **통합 데이터 액세스**(FDA) 옵션을 사용하여 외부 데이터베이스에 저장된 정보를 처리할 수 있습니다. sybase IQ에 대한 액세스를 구성하려면 아래 단계를 따르십시오.

1. [Sybase IQ 데이터베이스](#configuring-sybase) 구성
1. Campaign에서 Sybase IQ [외부 계정](#sybase-external) 구성

## sybase IQ 구성 {#configuring-sybase}

FDA에서 Sybase IQ 외부 데이터베이스에 연결하려면 Adobe Campaign 서버에 아래 추가 구성이 필요합니다.

>[!NOTE]
>
>시작하기 전에 **unixodbc** 패키지가 서버에 있는지 확인합니다.

1. **iq_odbc**&#x200B;을 설치합니다. 설치가 끝날 때 오류가 발생할 수 있습니다. 이 오류는 무시될 수 있습니다.

1. **iq_client_common**&#x200B;을 설치합니다. 설치가 끝날 때 Java 오류가 발생할 수 있습니다. 이 오류는 무시될 수 있습니다.

1. ODBC 드라이버를 구성합니다. 구성은 표준 파일에서 수행할 수 있습니다./etc/odbc.ini일반 매개 변수를 위한 방법 및 드라이버 선언용 /etc/odbcinst.ini을 참조하십시오.

   * **/etc/odbc.ini** (문자와  `<server_alias>` 같은 값을 직접 바꾸기):

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

1. LD_LIBRARY_PATH 변수에 새 libobc16.so 라이브러리의 경로를 추가합니다. 이를 수행하려면 다음을 수행하십시오.

   * customer.sh 파일을 사용하여 경로를 선언할 경우:LD_LIBRARY_PATH 변수에 대해 /opt/sybase/IQ-16_0/lib64 경로를 추가합니다.
   * 그렇지 않은 경우 Unix 명령을 사용합니다.

## sybase IQ 외부 계정 {#sybase-external}

sybase IQ 외부 계정을 사용하면 Campaign 인스턴스를 Sybase IQ 외부 데이터베이스에 연결할 수 있습니다.

1. 캠페인 **[!UICONTROL Explorer]**&#x200B;에서 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**&#x200B;을(를) 클릭합니다.

1. **[!UICONTROL New]**&#x200B;을 클릭하고 **[!UICONTROL External database]**&#x200B;을 **[!UICONTROL Type]**(으)로 선택합니다.

1. **[!UICONTROL Sybase IQ]** 외부 계정을 구성하려면 다음을 지정해야 합니다.

   * **[!UICONTROL Type]**:ODBC(Sybase ASE, Sybase IQ)

   * **[!UICONTROL Server]**:5단계에서 정의한 ODBC 연결(`<server_alias>`)에 해당합니다. 서버 자체의 이름이 아닐 수도 있습니다.

   * **[!UICONTROL Account]**:사용자 이름

   * **[!UICONTROL Password]**:사용자 계정 암호

   * **[!UICONTROL Database]**:데이터베이스의 이름

>[!NOTE]
>
>Windows의 경우 Adobe Campaign 서버에 Sybase IQ 클라이언트를 설치하고 ODBC 연결을 만들어야 합니다. Adobe Campaign 서버(nlserver)가 Windows에서 서비스로 실행 중일 때 시스템 데이터 소스를 만들어야 합니다.

