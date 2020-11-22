---
solution: Campaign Classic
product: campaign
title: 유니코드로 전환
description: 유니코드로 전환
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 7%

---


# 유니코드로 전환{#switching-to-unicode}

Linux/PostgreSQL의 기존 **제품** 인스턴스의 경우 유니코드로 전환하는 단계는 다음과 같습니다.

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

1. 추적 서버에서:

   ```
   su - neolane
   cd nl6/conf
   vi config-prod.xml
   ```

   데이터베이스 식별자( **databaseId** )와 관련된 값 앞에 u ****&#x200B;문자를 추가합니다.

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

   * 특히 강조된 문자에서 데이터가 올바르게 표시되는지 확인하십시오.
   * 배달을 실행하고 추적 검색이 작동하는지 확인합니다.

