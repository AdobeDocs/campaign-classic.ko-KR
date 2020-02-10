---
title: 유니코드로 전환
seo-title: 유니코드로 전환
description: 유니코드로 전환
seo-description: null
page-status-flag: never-activated
uuid: 5f15b285-7377-453a-aa98-ca4cf14a4c80
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
discoiquuid: 0f5399a8-860d-4a1b-86a9-9011b973346b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 유니코드로 전환{#switching-to-unicode}

Linux/PostgreSQL의 기존 **prod** 인스턴스의 경우 유니코드로 전환하는 단계는 다음과 같습니다.

1. 데이터베이스에 쓰는 프로세스를 중지합니다.

   ```
   su - neolane
   nlserver shutdown
   ```

1. 데이터베이스 덤프:

   ```
   su - postgres
   pg_dump mydatabase > mydatabase.sql
   ```

1. 유니코드 데이터베이스 만들기:

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

1. 추적 서버에서 다음을 수행합니다.

   ```
   su - neolane
   cd nl6/conf
   vi config-prod.xml
   ```

   데이터베이스 식별자( **databaseId** )와 관련된 값 앞에 u **문자를**&#x200B;추가합니다.

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

1. 스위치를 확인합니다. 이렇게 하려면 Adobe Campaign 콘솔을 통해 연결하고 다음을 수행합니다.

   * 특히 강조된 문자에서 데이터가 올바로 표시되는지 확인합니다.
   * 게재를 실행하고 추적 검색이 작동하는지 확인합니다.

