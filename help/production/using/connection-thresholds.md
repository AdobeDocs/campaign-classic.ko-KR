---
product: campaign
title: 연결 임계값
description: 연결 임계값
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 4ee05559-e719-4e6e-b42c-1e82df428871
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 3%

---

# 연결 임계값{#connection-thresholds}

많이 로드된 서버의 경우 연결 임계값이 초과될 수 있습니다. 어떤 경우든, 그 이유를 파악하는 것이 유용하다.

다음과 같은 세 가지 임계값이 있습니다.

* 웹 서버에 구성된 **웹 연결 임계값** 수정하려면 시스템 관리자에게 문의하십시오.

* **데이터베이스 연결 임계값**&#x200B;입니다. 수정하려면 데이터베이스 관리자에게 문의하십시오.

* **Adobe Campaign 연결 임계값**&#x200B;은 다음 두 위치에서 사용할 수 있습니다.

   * **** Tomcatside:모든 쿼리는 실제로 Adobe Campaign Tomcat 클라이언트에 도달합니다.

      이 임계값은 **nl6/tomcat-8/conf/server.xml** 파일에 구성되어 있습니다. **maxThreads** 속성을 사용하면 한 번에 처리된 쿼리 수의 임계값을 늘릴 수 있습니다. 예를 들어 250으로 변경할 수 있습니다.

      ```
      <Connector protocol="HTTP/1.1" port="8080"
                     maxThreads="75"
                     minSpareThreads="5"
                     enableLookups="true" redirectPort="8443"
                     acceptCount="100" connectionTimeout="20000"
                     disableUploadTimeout="true" />
          <Engine name="Tomcat-Standalone" defaultHost="localhost">
            <Host name="localhost" appBase="./"
                  unpackWARs="true" autoDeploy="true">
      ```

   * **데이터베이스**:프로세스에 의해 데이터베이스에서 동시에 열려 있는 모든 연결 집합입니다.

      이 임계값은 **nl6/conf/serverConf.xml** 파일에 구성되어 있습니다. **데이터 소스 풀**&#x200B;에 있는 **maxCnx** 속성을 사용하면 동시에 처리되는 쿼리의 임계값을 늘릴 수 있습니다.

      ```
          <!-- Data source
               -->
            <dataSource name="default">
              <dbcnx NChar="" bulkCopyUtility="" dbSchema="" encrypted="" login="" password="" provider="" server="" timezone="" unicodeData="" useTimestampTZ=""/>
              <sqlParams funcPrefix="">
                <postConnectSQL/>
              </sqlParams>
              <pool aliveTestDelaySec="600" freeCnx="0" maxCnx="90" maxIdleDelaySec="1200"/>
            </dataSource>
      ```
