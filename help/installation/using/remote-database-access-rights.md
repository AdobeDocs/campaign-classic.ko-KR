---
product: campaign
title: 외부 데이터베이스 액세스 권한
description: 외부 데이터베이스 액세스 권한
feature: Installation, Instance Settings, Federated Data Access
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용됩니다."
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 3d43010e-53f8-4aa2-a651-c422a02191fe
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '987'
ht-degree: 1%

---

# 원격 데이터베이스 액세스 권한 {#remote-database-access-rights}



먼저 사용자가 FDA를 통해 외부 데이터베이스에서 작업을 수행할 수 있도록 하려면, 후자의 경우 Adobe Campaign에서 명명된 특정 권한이 있어야 합니다.

1. 다음 항목 선택 **[!UICONTROL Administration > Access Management > Named Rights]** Adobe Campaign 탐색기의 노드
1. 선택한 레이블을 지정하여 새 권한을 만듭니다.
1. 다음 **[!UICONTROL Name]** 필드는 다음 형식을 사용해야 합니다. **user:base@server**, 여기서 :

   * **사용자** 는 외부 데이터베이스의 사용자 이름과 일치합니다.
   * **기본** 외부 데이터베이스 이름과 일치합니다.
   * **server** 외부 데이터베이스 서버의 이름과 일치합니다.

     >[!NOTE]
     >
     >다음 **:base** oracle에서 파트는 선택 사항입니다.

1. 명명된 권한을 저장한 다음 선택한 사용자에게 연결합니다. **[!UICONTROL Administration > Access Management > Operators]** Adobe Campaign 탐색기의 노드입니다.

그런 다음 외부 데이터베이스에 포함된 데이터를 처리하려면 Adobe Campaign 사용자가 작업 테이블을 생성할 수 있도록 데이터베이스에 대해 적어도 &#39;쓰기&#39; 권한을 가져야 합니다. Adobe Campaign에 의해 자동으로 삭제됩니다.

일반적으로 다음과 같은 권한이 필요합니다.

* **CONNECT**: 원격 데이터베이스에 연결,
* **데이터 읽기**: 고객 데이터가 포함된 테이블에 대한 읽기 전용 액세스,
* **&quot;메타데이터&quot; 읽기**: 테이블 구조를 얻기 위해 서버 데이터 카탈로그에 액세스,
* **로드**: 작업 테이블의 일괄 로드(컬렉션 및 조인 작업 시 필수),
* **만들기/놓기** 대상 **테이블/인덱스/프로시저/함수** (Adobe Campaign에서 생성한 작업 테이블만 해당),
* **설명** (권장): 문제 발생 시 성능 모니터링
* **데이터 쓰기** ( 통합 시나리오에 따라 다름).

데이터베이스 관리자는 이러한 권한을 각 데이터베이스 엔진에 대한 권한과 일치시켜야 합니다. 자세한 내용은 아래 섹션을 참조하십시오.

## FDA 권한 {#fda-rights}

|   | Snowflake | Redshift | Oracle | SQLServer | PostgreSQL | MySQL |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **원격 데이터베이스에 연결 중** | 웨어하우스 사용량, 데이터베이스 사용량 및 스키마 권한 사용량 | AWS 계정에 연결된 사용자 만들기 | 세션 권한 만들기 | CONNECT 권한 | CONNECT 권한 | 모든 권한이 있는 원격 호스트에 연결된 사용자 만들기 |
| **표 만들기** | 스키마 권한에 대한 테이블 생성 | 권한 만들기 | 테이블 만들기 권한 | 테이블 만들기 권한 | 권한 만들기 | 권한 만들기 |
| **인덱스 생성 중** | N/A | 권한 만들기 | 인덱스 또는 인덱스 만들기 권한 | ALTER 권한 | 권한 만들기 | INDEX 권한 |
| **함수 만들기** | 스키마 권한에 대한 함수 만들기 | 외부 python 스크립트를 호출할 수 있는 USAGE ON LANGUAGE plpythonu 권한 | CREATE PROCEDURE 또는 CREATE ANY PROCEDURE 권한 | 함수 만들기 권한 | 사용 권한 | 루틴 권한 만들기 |
| **프로시저 만들기** | N/A | 외부 python 스크립트를 호출할 수 있는 USAGE ON LANGUAGE plpythonu 권한 | CREATE PROCEDURE 또는 CREATE ANY PROCEDURE 권한 | 프로시저 만들기 권한 | USAGE 권한(프로시저는 함수) | 루틴 권한 만들기 |
| **객체(테이블, 인덱스, 함수, 프로시저) 제거** | 객체 소유 | 개체 소유 또는 수퍼유저 | 모든 &lt; 객체 > 권한 삭제 | ALTER 권한 | 테이블: 테이블 소유 인덱스: 인덱스 소유 함수: 함수 소유 | DROP 권한 |
| **실행 모니터링** | 필수 개체에 대한 MONITOR 권한 | EXPLAIN 명령을 사용하는 데 필요한 권한이 없습니다. | INSERT 및 SELECT 권한과 EXPLAIN PLAN의 기반이 되는 명령문을 실행하는 데 필요한 권한 | SHOWPLAN 권한 | EXPLAIN 문을 사용하는 데 필요한 권한이 없습니다. | 권한 선택 |
| **데이터 쓰기** | INSERT 및/또는 UPDATE 권한(쓰기 작업에 따라 다름) | INSERT 및 UPDATE 권한 | 테이블 권한 삽입 및 갱신 또는 삽입 및 갱신 | 권한 삽입 및 업데이트 | INSERT 및 UPDATE 권한 | INSERT 및 UPDATE 권한 |
| **테이블에 데이터 로드 중** | 스키마에 단계 생성, 대상 테이블에 선택 및 삽입 권한 | SELECT 및 INSERT 권한 | SELECT 및 INSERT 권한 | 대량 작업 삽입, 관리 및 TABLE 권한 변경 | SELECT 및 INSERT 권한 | 파일 권한 |
| **클라이언트 데이터에 액세스** | (향후) 테이블 또는 뷰 권한 선택 | 권한 선택 | 테이블 권한 선택 또는 선택 | 권한 선택 | 권한 선택 | 권한 선택 |
| **메타데이터에 액세스** | INFORMATION_SCHEMA 스키마 권한 선택 | 권한 선택 | DESCRIBE 문을 사용하는 데 필요한 권한이 없습니다. | 정의 보기 권한 | &quot;\d table&quot; 명령을 사용하는 데 필요한 권한이 없습니다. | 권한 선택 |

|   | DB2 UDB | Teradata | InfiniDB | Sybase IQ / Sybase ASE | Netezza | 마스터 데이터 |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **원격 데이터베이스에 연결 중** | CONNECT 기관 | CONNECT 권한 | 모든 권한이 있는 원격 호스트에 연결된 사용자 만들기 | CONNECT 문을 사용하는 데 필요한 권한이 없습니다. | 권한 필요 없음 | CONNECT 권한 |
| **표 만들기** | CREATETAB 기관 | 테이블 또는 테이블 키워드 만들기 | 권한 만들기 | 리소스 권한 및 만들기 권한 | TABLE 권한 | 권한 만들기 |
| **인덱스 생성 중** | INDEX 권한 | INDEX 또는 INDEX 키워드 만들기 | INDEX 권한 | 리소스 권한 및 만들기 권한 | INDEX 권한 | 권한 만들기 |
| **함수 만들기** | IMPLICIT_SCHEMA 권한 또는 CREATEIN 권한 | 함수 또는 함수 키워드 만들기 | 루틴 권한 만들기 | Java 기능에 대한 리소스 권한 또는 DBA 권한 | FUNCTION 권한 | CREATE FUNCTION 권한 |
| **프로시저 만들기** | IMPLICIT_SCHEMA 권한 또는 CREATEIN 권한 | 프로시저 또는 프로시저 키워드 만들기 | 루틴 권한 만들기 | 리소스 권한 | PROCEDURE 권한 | CREATE FUNCTION 권한 |
| **객체(테이블, 인덱스, 함수, 프로시저) 제거** | DROPIN 권한 또는 CONTROL 권한 또는 개체 소유 | DROP &lt; object > 또는 개체 관련 키워드 | DROP 권한 | 객체 또는 DBA 권한 소유 | DROP 권한 | 객체 소유 |
| **실행 모니터링** | 권한 설명 | EXPLAIN 문을 사용하는 데 필요한 권한이 없습니다. | 권한 선택 | 시스템 관리자만 sp_showplan을 실행할 수 있습니다. | EXPLAIN 문을 사용하는 데 필요한 권한이 없습니다. | EXPLAIN 문을 사용하는 데 필요한 권한이 없습니다. |
| **데이터 쓰기** | INSERT 및 UPDATE 권한 또는 데이터 액세스 권한 | INSERT 및 UPDATE 권한 | INSERT 및 UPDATE 권한 | 권한 삽입 및 업데이트 | INSERT 및 UPDATE 권한 | INSERT 및 UPDATE 권한 |
| **테이블에 데이터 로드 중** | 권한 로드 | SELECT 및 INSERT 권한을 사용하여 COPY TO 문과 COPY FROM 문을 각각 사용합니다. | 파일 권한 | 테이블 또는 ALTER 권한의 소유자여야 합니다. -gl 옵션에 따라 사용자에게 DBA 권한이 있는 경우에만 LOAD TABLE이 수행될 수 있습니다 | SELECT 및 INSERT 권한 | SELECT 및 INSERT 권한 |
| **클라이언트 데이터에 액세스** | INSERT/UPDATE 권한 또는 데이터 액세스 권한 | 권한 선택 | 권한 선택 | 권한 선택 | 권한 선택 | 권한 선택 |
| **메타데이터에 액세스** | DESCRIBE 문을 사용하기 위한 권한 부여가 필요하지 않습니다. | 권한 표시 | 권한 선택 | DESCRIBE 문을 사용하는 데 필요한 권한이 없습니다. | &quot;\d table&quot; 명령을 사용하는 데 필요한 권한이 없습니다. | SHOW 명령을 사용하는 데 필요한 권한이 없습니다. |
