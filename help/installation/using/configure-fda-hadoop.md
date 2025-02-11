---
product: campaign
title: hadoop 액세스 구성
description: FDA에서 Hadoop 액세스를 구성하는 방법 알아보기
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: e3a97e55-dd8b-41e1-b48c-816d973f62a8
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 1%

---

# hadoop 액세스 구성 {#configure-access-to-hadoop}



외부 데이터베이스에 저장된 정보를 처리하려면 Campaign **FDA(Federated Data Access**) 옵션을 사용하십시오. hadoop 액세스를 구성하려면 아래 단계를 따르십시오.

1. [Hadoop 데이터베이스](#configuring-hadoop) 구성
1. Campaign에서 Hadoop [외부 계정](#hadoop-external) 구성

## hadoop 3.0 구성 {#configuring-hadoop}

FDA에서 Hadoop 외부 데이터베이스에 연결하려면 Adobe Campaign 서버에서 다음 구성이 필요합니다. 이 구성은 Windows와 Linux 모두에서 사용할 수 있습니다.

1. OS 버전에 따라 Hadoop을 위한 ODBC 드라이버를 다운로드합니다. 드라이버는 [이 페이지](https://www.cloudera.com/downloads.html)에서 찾을 수 있습니다.

1. 그런 다음 ODBC 드라이버를 설치하고 Hive 연결에 대한 DSN을 만들어야 합니다. 지침은 [이 페이지](https://docs.cloudera.com/documentation/other/connectors/hive-odbc/2-6-5/Cloudera-ODBC-Driver-for-Apache-Hive-Install-Guide.pdf)에서 찾을 수 있습니다

1. ODBC 드라이버를 다운로드하고 설치한 후 Campaign Classic을 다시 시작해야 합니다. 이렇게 하려면 다음 명령을 실행합니다.

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. 그런 다음 Campaign Classic에서 [!DNL Hadoop] 외부 계정을 구성할 수 있습니다. 외부 계정을 구성하는 방법에 대한 자세한 내용은 [이 섹션](#hadoop-external)을 참조하세요.

## 외부 계정 hadoop {#hadoop-external}

[!DNL Hadoop] 외부 계정을 사용하면 Campaign 인스턴스를 Hadoop 외부 데이터베이스에 연결할 수 있습니다.

1. Campaign Classic에서 [!DNL Hadoop] 외부 계정을 구성합니다. **[!UICONTROL Explorer]**&#x200B;에서 **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**&#x200B;을(를) 클릭합니다.

1. **[!UICONTROL New]**&#x200B;를 클릭합니다.

1. **[!UICONTROL External database]**&#x200B;을(를) 외부 계정의 **[!UICONTROL Type]**(으)로 선택합니다.

1. **[!UICONTROL Hadoop]** 외부 계정을 구성하십시오. 다음을 지정해야 합니다.

   * **[!UICONTROL Type]**: ODBC(Sybase ASE, Sybase IQ)

   * **[!UICONTROL Server]**: DNS 이름

   * **[!UICONTROL Account]**: 사용자 이름

   * **[!UICONTROL Password]**: 사용자 계정 암호

   * **[!UICONTROL Database]**: DSN에 지정되지 않은 경우 데이터베이스의 이름입니다. DSN에 지정된 경우 비워 둘 수 있습니다.

   * **[!UICONTROL Time zone]**: 서버 시간대

   ![](assets/hadoop3.png)

커넥터가 지원하는 ODBC 옵션은 다음과 같습니다.

| 이름 | 값 |
|---|---|
| ODBCMgr | iODBC |
| warehouse | 1/2/4 |

커넥터는 다음 하이브 옵션도 지원합니다.

| 이름 | 값 | 설명 |
|---|---|---|
| bulkKey | Azure blob 또는 DataLake 액세스 키 | wasb:// 또는 wasbs:// 벌크 로더의 경우(즉, 벌크 로드 도구가 wasb:// 또는 wasbs://으로 시작하는 경우). <br>대량 로드를 위한 Blob 또는 DataLake 버킷의 액세스 키입니다. |
| hdfsPort | 포트 번호 <br>이(가) 기본적으로 8020으로 설정됨 | HDFS 벌크 로드의 경우(즉, 벌크 로드 도구가 webhdfs:// 또는 webhdfss://으로 시작하는 경우). |
| bucketsNumber | 20 | 클러스터형 테이블을 생성할 때 버킷 수입니다. |
| 파일 형식 | 쪽모이 | 작업 테이블의 기본 파일 형식입니다. |


## hadoop 2.1 구성 {#configure-access-hadoop-2}

hadoop 2.1에 연결해야 하는 경우 [Windows](#for-windows) 또는 [Linux](#for-linux)에 대해 아래에 설명된 단계를 따르십시오.

### Windows용 hadoop 2.1 {#for-windows}

1. Windows용 ODBC 및 [Azure HD Insight](https://www.microsoft.com/en-us/download/details.aspx?id=40886) 드라이버를 설치합니다.
1. ODBC DataSource Administrator 도구를 실행하여 DSN(Data Source Name)을 만듭니다. 수정할 수 있도록 Hive용 시스템 DSN 샘플이 제공됩니다.

   ```
   Description: vorac (or any name you like)
   Host: vorac.azurehdinsight.net
   Port: 443
   Database: sm_tst611 (or your database name)
   Mechanism: Azure HDInsight Service
   User/Password: admin/<your password here>
   ```

1. [이 섹션](#hadoop-external)에 자세히 설명된 대로 Hadoop 외부 계정을 만듭니다.

### Linux용 hadoop 2.1 {#for-linux}

1. Linux용 unixodbc를 설치합니다.

   ```
   apt-get install unixodbc
   ```

1. HortonWorks에서 Apache Hive용 ODBC 드라이버를 다운로드하여 설치하십시오. [https://www.cloudera.com/downloads.html](https://www.cloudera.com/downloads.html).

   ```
   dpkg -i hive-odbc-native_2.1.10.1014-2_amd64.deb
   ```

1. ODBC 파일 위치를 확인하십시오.

   ```
   root@campadpac71:/tmp# odbcinst -j
   unixODBC 2.3.1
   DRIVERS............: /etc/odbcinst.ini
   SYSTEM DATA SOURCES: /etc/odbc.ini
   FILE DATA SOURCES..: /etc/ODBCDataSources
   USER DATA SOURCES..: /root/.odbc.ini
   SQLULEN Size.......: 8
   SQLLEN Size........: 8
   SQLSETPOSIROW Size.: 8
   ```

1. DSN(Data Source Name)을 만들고 odbc.ini 파일을 편집합니다. 그런 다음 Hive 연결에 대한 DSN을 만듭니다.

   다음은 HDInsight에서 &quot;viral&quot;이라는 연결을 설정하는 예입니다.

   ```
   [ODBC Data Sources]
   vorac 
   
   [vorac]
   Driver=/usr/lib/hive/lib/native/Linux-amd64-64/libhortonworkshiveodbc64.so
   HOST=vorac.azurehdinsight.net
   PORT=443
   Schema=sm_tst611
   HiveServerType=2
   AuthMech=6
   UID=admin
   PWD=<your password here>
   HTTPPath=
   UseNativeQuery=1
   ```

   >[!NOTE]
   >
   >**UseNativeQuery** 매개 변수는 매우 중요합니다. Campaign은 하이브를 인식하며 UseNativeQuery를 설정하지 않으면 제대로 작동하지 않습니다. 일반적으로 드라이버 또는 Hive SQL 커넥터는 쿼리를 다시 작성하고 열 순서를 변경합니다.

   인증 설정은 하이브/Hadoop 구성에 따라 다릅니다. 예를 들어 HD Insight의 경우 [여기](https://www.simba.com/products/Spark/doc/ODBC_InstallGuide/unix/content/odbc/hi/configuring/authenticating/azuresvc.htm)에 설명된 대로 사용자/암호 인증에 AuthMech=6을 사용합니다.

1. 변수를 내보냅니다.

   ```
   export ODBCINI=/etc/myodbc.ini
   export ODBCSYSINI=/etc/myodbcinst.ini
   ```

1. /usr/lib/hive/lib/native/Linux-amd64-64/hortonworks.hiveodbc.ini를 통해 Hortonworks 드라이버를 설정합니다.

   Campaign 및 unix-odbc(libodbcinst)와 연결하려면 UTF-16을 사용해야 합니다.

   ```
   [Driver]
   
   DriverManagerEncoding=UTF-16
   ErrorMessagesPath=/usr/lib/hive/lib/native/hiveodbc/ErrorMessages/
   LogLevel=0
   LogPath=/tmp/hive
   SwapFilePath=/tmp
   
   ODBCInstLib=libodbcinst.so
   ```

1. 이제 isql을 사용하여 연결을 테스트할 수 있습니다.

   ```
   isql vorac
   isql vorac -v
   ```

1. [이 섹션](#hadoop-external)에 자세히 설명된 대로 Hadoop 외부 계정을 만듭니다.
