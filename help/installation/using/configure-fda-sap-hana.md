---
product: campaign
title: SAP HANA 액세스 구성
description: FDA에서 SAP HANA 액세스를 구성하는 방법 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 39bfe775-e182-4a0b-ad3c-b7a901297c90
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# SAP HANA 액세스 구성 {#configure-access-to-sap-hana}



Campaign 사용 [페더레이션 데이터 액세스](../../installation/using/about-fda.md) (FDA) 외부 데이터베이스에 저장된 정보를 처리하는 옵션. SAP HANA 액세스를 구성하려면 아래 단계를 따르십시오.

1. 구성 [SAP HANA 데이터베이스](#sap-config)
1. SAP HANA 구성 [외부 계정](#sap-external) 캠페인에서

## SAP HANA 드라이버 {#sap-config}

FDA에서 SAP HANA 외부 데이터베이스에 연결하려면 Adobe Campaign 서버에 다음과 같은 특정 추가 구성이 필요합니다.

1. 사용하는 운영 체제에 따라 SAP HANA용 ODBC 드라이버를 설치합니다.

   * **hdb_client_linux.tgz** Linux용 압축이 풀리면 hdbinst 명령을 실행하고 지침에 따라 드라이버 설치를 완료합니다.
   * **hdb_client_windows.zip** Windows용 파일의 압축을 풀고 실행 파일을 시작합니다. **hdbinst.exe**. 마법사 지침에 따라 드라이버 설치를 완료합니다.

1. ODBC 드라이버를 구성합니다. 일반 매개 변수의 경우 /etc/odbc.ini에서, 드라이버를 선언하는 경우 /etc/odbcinst.ini에서 구성을 수행할 수 있습니다.

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      
      [HDB]
      Driver=HDBODBC
      servernode=localhost:39013 (this value depend of your server)
      User:SYSTEM
      ```

      &quot;InstallDir&quot;은 **odbcinst.ini** 파일.

   * **/etc/odbcinst.ini**

      ```
      [HDBODBC]
      Description = "SmartCloudPT HANA"
      Driver = /usr/sap/hdbclient/libodbcHDB.so
      ```

1. Adobe Campaign 서버의 환경 변수를 지정합니다.

   * **LD_LIBRARY_PATH**: SAP Hana 클라이언트(기본적으로 /usr/sap/hdbclient/libodbcHDB.so)에 대한 링크가 포함되어야 합니다.
   * **오브치니**: odbc.ini 파일의 위치(예: /etc/odbc.ini)입니다.

## 외부 계정 SAP HANA{#sap-external}

SAP HANA 외부 계정을 사용하면 Campaign 인스턴스를 SAP HANA 외부 데이터베이스에 연결할 수 있습니다.

1. 출처: Campaign **[!UICONTROL Explorer]**, 클릭 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. 클릭 **[!UICONTROL New]** 및 선택 **[!UICONTROL External database]** 다음으로: **[!UICONTROL Type]**.

1. 을(를) 구성하려면 다음을 수행하십시오. **[!UICONTROL SAP Hana]** 외부 계정에서 다음을 지정해야 합니다.

   * **[!UICONTROL Type]**: SAP Hana

   * **[!UICONTROL Server]**: SAP Hana 서버의 URL

   * **[!UICONTROL Account]**: 사용자 이름

   * **[!UICONTROL Password]**: 사용자 계정 암호
