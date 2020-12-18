---
solution: Campaign Classic
product: campaign
title: SAP HANA 액세스 권한 구성
description: FDA에서 SAP HANA에 대한 액세스를 구성하는 방법 살펴보기
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---


# SAP HANA {#configure-access-to-sap-hana}에 대한 액세스 구성

캠페인 [통합 데이터 액세스](../../installation/using/about-fda.md)(FDA) 옵션을 사용하여 외부 데이터베이스에 저장된 정보를 처리할 수 있습니다. SAP HANA에 대한 액세스를 구성하려면 아래 단계를 따르십시오.

1. [SAP HANA 데이터베이스](#sap-config) 구성
1. Campaign에서 SAP HANA [외부 계정](#sap-external) 구성

## SAP HANA 드라이버 {#sap-config}

FDA에서 SAP HANA 외부 데이터베이스에 연결하려면 Adobe Campaign 서버에 특정 추가 구성이 필요합니다.

1. 사용하는 운영 체제에 따라 SAP HANA용 ODBC 드라이버를 설치합니다.

   * **Linux용 hdb_client_linux.** tgzz 압축을 풀면 hdbinst 명령을 실행하고 지침에 따라 드라이버 설치를 완료하십시오.
   * **hdb_client_windows.** zip for Windows. 파일의 압축을 풀고 실행 파일을 시작합니다.**hdbinst.exe**. 마법사 지침에 따라 드라이버 설치를 완료합니다.

1. ODBC 드라이버를 구성합니다. 구성은 표준 파일에서 수행할 수 있습니다./etc/odbc.ini일반 매개 변수에 대한 자세한 내용과 드라이버 선언용 /etc/odbcinst.ini을 참조하십시오.

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      
      [HDB]
      Driver=HDBODBC
      servernode=localhost:39013 (this value depend of your server)
      User:SYSTEM
      ```

      &quot;InstallDir&quot;은 **odbcinst.ini** 파일의 위치에 해당합니다.

   * **/etc/odbcinst.ini**

      ```
      [HDBODBC]
      Description = "SmartCloudPT HANA"
      Driver = /usr/sap/hdbclient/libodbcHDB.so
      ```

1. Adobe Campaign 서버의 환경 변수를 지정합니다.

   * **LD_LIBRARY_PATH**:여기에는 기본적으로 SAP Hana 클라이언트(/usr/sap/hdbclient/libodbcHDB.so)에 대한 링크가 포함되어야 합니다.
   * **오드치니**:odbc.ini 파일의 위치입니다(예: /etc/odbc.ini).

## SAP HANA 외부 계정{#sap-external}

SAP HANA 외부 계정을 사용하면 Campaign 인스턴스를 SAP HANA 외부 데이터베이스에 연결할 수 있습니다.

1. 캠페인 **[!UICONTROL Explorer]**&#x200B;에서 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**&#x200B;을(를) 클릭합니다.

1. **[!UICONTROL New]**&#x200B;을 클릭하고 **[!UICONTROL External database]**&#x200B;을 **[!UICONTROL Type]**(으)로 선택합니다.

1. **[!UICONTROL SAP Hana]** 외부 계정을 구성하려면 다음을 지정해야 합니다.

   * **[!UICONTROL Type]**:SAP 하나

   * **[!UICONTROL Server]**:SAP 하나 서버의 URL

   * **[!UICONTROL Account]**:사용자 이름

   * **[!UICONTROL Password]**:사용자 계정 암호
