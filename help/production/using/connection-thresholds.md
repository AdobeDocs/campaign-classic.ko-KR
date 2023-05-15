---
product: campaign
title: 연결 임계값
description: 연결 임계값
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 4ee05559-e719-4e6e-b42c-1e82df428871
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 3%

---

# 연결 임계값{#connection-thresholds}



많이 로드된 서버의 경우 연결 임계값이 초과될 수 있습니다. 어떤 경우든, 그 이유를 파악하는 것이 유용하다.

다음과 같은 세 가지 임계값이 있습니다.

* 다음 **웹 연결 임계값**: 웹 서버에 구성되었습니다. 수정하려면 시스템 관리자에게 문의하십시오.

* 다음 **데이터베이스 연결 임계값**. 수정하려면 데이터베이스 관리자에게 문의하십시오.

* 다음 **Adobe Campaign 연결 임계값**, 다음 두 위치에서 사용할 수 있습니다.

   * **Tomcat** 측면: 모든 쿼리는 실제로 Adobe Campaign Tomcat 클라이언트에 도달합니다.

      이 임계값은 **nl6/tomcat-8/conf/server.xml** 파일. 다음 **maxThreads** 속성을 사용하면 한 번에 처리되는 쿼리 수의 임계값을 늘릴 수 있습니다. 예를 들어 250으로 변경할 수 있습니다.

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

   * **데이터베이스**: 프로세스에 의해 데이터베이스에서 동시에 열려 있는 모든 연결 집합입니다.

      이 임계값은 파일에 구성되어 있습니다 **nl6/conf/serverConf.xml**. 다음 **maxCnx** 에 있는 속성 **데이터 소스 풀** 동시에 처리된 쿼리의 임계값을 늘릴 수 있습니다.

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
