---
title: 연결 임계값
seo-title: 연결 임계값
description: 연결 임계값
seo-description: null
page-status-flag: never-activated
uuid: a4b6959a-0f5b-41a2-b4c3-d7d6613d1a18
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: f3db77db-94cc-4d75-a59b-2dddce776759
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 5%

---


# 연결 임계값{#connection-thresholds}

로드된 서버의 경우 연결 임계값이 초과될 수 있습니다. 어떤 경우든, 그 이유를 알아내는 것이 유용하다.

다음과 같은 세 가지 다른 임계값이 있습니다.

1. 웹 서버에 구성된 웹 연결 임계값 수정하려면 시스템 관리자에게 문의하십시오.
1. 데이터베이스 연결 임계값. 수정하려면 데이터베이스 관리자에게 문의하십시오.
1. Adobe Campaign 연결 임계값:

   * Tomcat 측면:모든 질의는 실제로 Adobe Campaign 톰캣의 고객을 대상으로 합니다.

      이 임계값은 nl6/tomcat-7/conf/server.xml **파일에서** 구성됩니다. maxThreads **** 속성을 사용하면 한 번에 처리되는 쿼리 수의 임계값을 늘릴 수 있습니다. 예를 들어 250으로 변경할 수 있습니다.

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

   * 데이터베이스:프로세스에 의해 데이터베이스에 동시에 열려 있는 모든 연결 집합.

      이 임계값은 nl6/conf/serverConf.xml 파일에 **구성되어 있습니다**. 데이터 소스 풀에 있는 **maxCnx** 속성을 사용하면 동시에 처리된 쿼리 **** 임계값을 늘릴 수 있습니다.

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

