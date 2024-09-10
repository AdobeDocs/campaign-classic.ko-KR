---
product: campaign
title: SAP HANA 액세스 구성
description: FDA에서 SAP HANA 액세스를 구성하는 방법 알아보기
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 39bfe775-e182-4a0b-ad3c-b7a901297c90
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# SAP HANA 액세스 구성 {#configure-access-to-sap-hana}



외부 데이터베이스에 저장된 정보를 처리하려면 Campaign [FDA(Federated Data Access](../../installation/using/about-fda.md)) 옵션을 사용하십시오. SAP HANA 액세스를 구성하려면 아래 단계를 따르십시오.

1. [SAP HANA 데이터베이스](#sap-config) 구성
1. Campaign에서 SAP HANA [외부 계정](#sap-external) 구성

## SAP HANA 드라이버 {#sap-config}

FDA에서 SAP HANA 외부 데이터베이스에 연결하려면 Adobe Campaign 서버에 다음과 같은 특정 추가 구성이 필요합니다.

1. 사용하는 운영 체제에 따라 SAP HANA용 ODBC 드라이버를 설치합니다.

   * Linux용 **hdb_client_linux.tgz**. 압축이 풀리면 hdbinst 명령을 실행하고 지침에 따라 드라이버 설치를 완료합니다.
   * Windows용 **hdb_client_windows.zip**. 파일의 압축을 풀고 실행 파일(**hdbinst.exe**)을 시작합니다. 드라이버 설치를 완료하려면 어시스턴트 지침을 따르십시오.

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

     &quot;InstallDir&quot;은 **odbcinst.ini** 파일의 위치에 해당합니다.

   * **/etc/odbcinst.ini**

     ```
     [HDBODBC]
     Description = "SmartCloudPT HANA"
     Driver = /usr/sap/hdbclient/libodbcHDB.so
     ```

1. Adobe Campaign 서버의 환경 변수를 지정합니다.

   * **LD_LIBRARY_PATH**: SAP Hana 클라이언트에 대한 링크(기본적으로 /usr/sap/hdbclient/libodbcHDB.so)가 포함되어야 합니다.
   * **ODBCINI**: odbc.ini 파일의 위치입니다(예: /etc/odbc.ini).

## 외부 계정 SAP HANA{#sap-external}

SAP HANA 외부 계정을 사용하면 Campaign 인스턴스를 SAP HANA 외부 데이터베이스에 연결할 수 있습니다.

1. **[!UICONTROL Explorer]** 캠페인에서 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**&#x200B;을(를) 클릭합니다.

1. **[!UICONTROL New]**&#x200B;을(를) 클릭하고 **[!UICONTROL External database]**&#x200B;을(를) **[!UICONTROL Type]**(으)로 선택합니다.

1. **[!UICONTROL SAP Hana]** 외부 계정을 구성하려면 다음을 지정해야 합니다.

   * **[!UICONTROL Type]**: SAP 하나

   * **[!UICONTROL Server]**: SAP Hana 서버의 URL

   * **[!UICONTROL Account]**: 사용자 이름

   * **[!UICONTROL Password]**: 사용자 계정 암호
