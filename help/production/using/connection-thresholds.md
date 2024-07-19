---
product: campaign
title: 연결 임계값
description: 연결 임계값
feature: Monitoring
badge-v7-prem: label="온-프레미스/하이브리드만" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 4ee05559-e719-4e6e-b42c-1e82df428871
source-git-commit: 757e3a5395f24e0bdd04737aba0458881e4ea780
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 4%

---

# 연결 임계값{#connection-thresholds}



부하가 높은 서버의 경우 연결 임계값을 초과할 수 있습니다. 어떤 경우든 그 이유를 알아보는 것은 유용하다.

세 가지 다른 임계값이 있습니다.

* 웹 서버에 구성된 **웹 연결 임계값**&#x200B;입니다. 수정하려면 시스템 관리자에게 문의하십시오.

* **데이터베이스 연결 임계값**&#x200B;입니다. 수정하려면 데이터베이스 관리자에게 문의하십시오.

* **Adobe Campaign 연결 임계값**&#x200B;은(는) 다음 두 위치에서 사용할 수 있습니다.

   * **Tomcat**&#x200B;측: Adobe Campaign Tomcat 클라이언트에 실제로 도착하는 모든 쿼리

     이 임계값은 **nl6/tomcat-X/conf/server.xml** 파일에 구성되어 있습니다. **maxThreads** 특성을 사용하면 한 번에 처리되는 쿼리 수의 임계값을 늘릴 수 있습니다. 예를 들어 250으로 변경할 수 있습니다.

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

   * **데이터베이스**: 모든 연결 집합은 프로세스에서 동시에 열려 있습니다.

     이 임계값은 **nl6/conf/serverConf.xml** 파일에 구성되어 있습니다. **데이터 원본 풀**&#x200B;에 있는 **maxCnx** 특성을 사용하면 동시에 처리되는 쿼리의 임계값을 늘릴 수 있습니다.

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
