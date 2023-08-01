---
product: campaign
title: 유니코드로 전환
description: 유니코드로 전환
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용됩니다."
badge-v7-prem: label="온-프레미스 및 하이브리드" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 4cfecf2f-cf98-42c1-b979-cdd26d5de48b
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 13%

---

# 유니코드로 전환{#switching-to-unicode}



기존 **prod** linux/PostgreSQL에서 유니코드로 전환하는 단계는 다음과 같습니다.

1. 데이터베이스에 쓰는 프로세스를 중지합니다.

   ```
   su - neolane
   nlserver shutdown
   ```

1. 데이터베이스를 덤프합니다.

   ```
   su - postgres
   pg_dump mydatabase > mydatabase.sql
   ```

1. 유니코드 데이터베이스를 만듭니다.

   ```
   createdb -E UNICODE mydatabase_unicode
   ```

1. 데이터베이스 복원:

   ```
   psql mydatabase_unicode < mydatabase.sql
   ```

1. 데이터베이스가 유니코드임을 나타내는 옵션을 업데이트합니다.

   ```
   psql mydatabase_unicode
   update XtkOption set sStringValue = 'u'||sStringValue where sName='XtkDatabaseId' and sStringValue not like 'u%';
   ```

1. 추적 서버에서:

   ```
   su - neolane
   cd nl6/conf
   vi config-prod.xml
   ```

   추가 **u** 데이터베이스 식별자 관련 값 앞에 있는 문자(**databaseId**):

   ```
   <web>
    <redirection databaseId="u7F0000010554364C" trackingPassword="myPassword="/>
   </web>
   ```

1. 데이터베이스를 호출하는 서버:

   ```
   su - neolane
   cd nl6/conf
   vi config-prod.xml
   ```

   데이터베이스 참조를 수정합니다.

   ```
   <dataSource name="default">
    <dbcnx encrypted="1" 
    login="<dbuser>:<base_unicode>" password="xxxx="
    provider="postgresql" server="yyyy"/>
   </dataSource>
   ```

1. 모든 시스템을 재부팅합니다.

   ```
   /etc/init.d/apache stop
   /etc/init.d/nlserver6 stop
   /etc/init.d/nlserver6 start
   /etc/init.d/apache start
   ```

1. 스위치를 확인합니다. 이렇게 하려면 Adobe Campaign 콘솔을 통해 연결하고 다음을 수행하십시오.

   * 데이터가 올바르게 표시되는지, 특히 강조된 문자가 올바르게 표시되는지 확인합니다.
   * 게재를 시작하고 추적 검색이 작동하는지 확인합니다.
