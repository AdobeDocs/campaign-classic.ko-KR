---
solution: Campaign Classic
product: campaign
title: 외부 데이터베이스에 액세스할 수 있는 권한
description: 외부 데이터베이스 액세스 권한
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1019'
ht-degree: 1%

---


# 원격 데이터베이스 액세스 권한 {#remote-database-access-rights}

우선 FDA를 통해 외부 데이터베이스에 대한 작업을 수행할 수 있도록 Adobe Campaign에서 특정 명칭을 사용해야 한다.

1. Adobe Campaign 탐색기에서 **[!UICONTROL Administration > Access Management > Named Rights]** 노드를 선택합니다.
1. 선택한 레이블을 지정하여 새 권한을 만듭니다.
1. 이 **[!UICONTROL Name]** 필드는 다음 형식 **user:base@server**, where:

   * **사용자가** 외부 데이터베이스의 사용자 이름과 일치합니다.
   * **base** 는 외부 데이터베이스 이름과 일치합니다.
   * **서버는** 외부 데이터베이스 서버의 이름과 일치합니다.

      >[!NOTE]
      >
      >oracle에서 **기본** 부분은 선택 사항입니다.

1. 이름을 저장한 다음 Adobe Campaign 탐색기의 노드에서 선택한 사용자에게 **[!UICONTROL Administration > Access Management > Operators]** 연결합니다.

그런 다음 외부 데이터베이스에 포함된 데이터를 처리하려면, 작업 테이블을 만들 수 있도록 데이터베이스에 대해 &#39;쓰기&#39; 권한이 있어야 합니다. Adobe Campaign이 자동으로 삭제합니다.

일반적으로 다음과 같은 권한이 필요합니다.

* **CONNECT**:원격 데이터베이스에 연결,
* **데이터 읽기**:고객 데이터가 포함된 테이블에 대한 읽기 전용 액세스
* **&#39;MetaData&#39;**&#x200B;보기:서버 데이터 카탈로그에 액세스하여 테이블 구조를 가져옵니다.
* **로드**:작업 테이블에 대량 로드(컬렉션 및 조인 작업 시 필요),
* **테이블/인덱스/** 프로시저/함수 **** 생성/삭제(Adobe Campaign에서 생성한 작업표에만 해당),
* **설명** (권장):문제가 있을 경우 공연을 모니터링하기 위해
* **WRITE 데이터** (통합 시나리오에 따라 다름).

데이터베이스 관리자는 이러한 권한이 각 데이터베이스 엔진별 권한과 일치해야 합니다. 자세한 내용은 아래 섹션을 참조하십시오.

## FDA 권리 {#fda-rights}

|   | Snowflake | Redshift | Oracle | SQLServer | PostgreSQL | MySQL |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **원격 데이터베이스에 연결** | 웨어하우스의 사용, 데이터베이스에 대한 사용 및 스키마 권한에 대한 사용 | AWS 계정에 연결된 사용자 생성 | 세션 권한 만들기 | CONNECT 권한 | CONNECT 권한 | 모든 권한이 있는 원격 호스트에 연결된 사용자 만들기 |
| **표 만들기** | 스키마 권한에 대한 테이블 만들기 | 권한 만들기 | 테이블 권한 만들기 | 테이블 만들기 권한 | 권한 만들기 | 권한 만들기 |
| **인덱스 만들기** | N/A | 권한 만들기 | 인덱스 또는 인덱스 권한 만들기 | ALTER permission | 권한 만들기 | INDEX 권한 |
| **함수 만들기** | 스키마 권한에 대한 함수 만들기 | 외부 Python 스크립트를 호출할 수 있는 USAGE ON LANGUAGE Pythonu 권한 | 프로시저 만들기 또는 프로시저 권한 만들기 | 함수 만들기 권한 | 사용 권한 | 루틴 권한 만들기 |
| **절차 만들기** | N/A | 외부 Python 스크립트를 호출할 수 있는 USAGE ON LANGUAGE Pythonu 권한 | 프로시저 만들기 또는 프로시저 권한 만들기 | 프로시저 만들기 권한 | 사용 권한(절차는 기능임) | 루틴 권한 만들기 |
| **객체 제거(테이블, 인덱스, 함수, 절차)** | 개체 소유 | 객체 소유 또는 수퍼유저 | 모든 &lt; 객체 > 권한 삭제 | ALTER permission | 표:테이블 인덱스 소유:인덱스 함수 소유:함수 소유 | DROP 권한 |
| **실행 모니터링** | 필요한 개체에 대한 MONITOR 권한 | EXPLAIN 명령을 사용하는 데 필요한 권한이 없습니다. | EXPLAIN PLAN이 기반으로 하는 문을 실행하기 위한 INSERT and SELECT 권한 및 필요한 권한 | SHOWPLAN 권한 | EXPLAIN 문을 사용하는 데 필요한 권한이 없습니다. | 권한 선택 |
| **데이터 쓰기** | INSERT 및/또는 UPDATE 권한(쓰기 작업에 따라 다름) | 권한 삽입 및 업데이트 | 테이블 권한 삽입 및 업데이트 또는 삽입 및 업데이트 | 권한 삽입 및 업데이트 | 권한 삽입 및 업데이트 | 권한 삽입 및 업데이트 |
| **표에 데이터 로드** | 스키마에 스테이지 만들기, 대상 테이블 권한에 대해 선택 및 삽입 | 권한 선택 및 삽입 | 권한 선택 및 삽입 | 일괄 작업 삽입, 관리 및 테이블 권한 변경 | 권한 선택 및 삽입 | 파일 권한 |
| **클라이언트 데이터에 액세스** | (향후) 테이블 또는 뷰 권한을 선택합니다. | 권한 선택 | 테이블 권한 선택 또는 선택 | 권한 선택 | 권한 선택 | 권한 선택 |
| **메타데이터 액세스** | INFORMATION_SCHEMA 권한 선택 | 권한 선택 | DESCRIBE 문을 사용하는 데 필요한 권한 없음 | 정의 권한 보기 | &quot;\d table&quot; 명령을 사용할 권한이 없습니다. | 권한 선택 |

|   | DB2 UDB | teradata | InfiniDB | sybase IQ / Sybase ASE | Netezza | 그린플럼 | AsterData |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **원격 데이터베이스에 연결** | CONNECT 당국 | CONNECT 권한 | 모든 권한이 있는 원격 호스트에 연결된 사용자 만들기 | CONNECT 문을 사용할 권한이 없습니다. | 권한 필요 없음 | CONNECT 권한 | CONNECT 권한 |
| **표 만들기** | CREATETAB 권한 | 표 또는 표 키워드 만들기 | 권한 만들기 | 리소스 권한 및 만들기 권한 | 테이블 권한 | 권한 만들기 | 권한 만들기 |
| **인덱스 만들기** | INDEX 권한 | 색인 또는 색인 키워드 만들기 | INDEX 권한 | 리소스 권한 및 만들기 권한 | INDEX 권한 | 권한 만들기 | 권한 만들기 |
| **함수 만들기** | IMPLICIT_SCHEMA 권한 또는 CREATEIN 권한 | 함수 또는 함수 키워드 만들기 | 루틴 권한 만들기 | Java 기능에 대한 RESOURCE authority 또는 DBA | 함수 권한 | 사용 권한 | 함수 권한 만들기 |
| **절차 만들기** | IMPLICIT_SCHEMA 권한 또는 CREATEIN 권한 | 프로시저 또는 프로시저 키워드 만들기 | 루틴 권한 만들기 | 리소스 권한 | 절차 권한 | 사용 권한 | 함수 권한 만들기 |
| **객체 제거(테이블, 인덱스, 함수, 절차)** | DROPPIN 권한 또는 CONTROL 권한 또는 개체 소유 | DROP &lt; object > 또는 객체 관련 키워드 | DROP 권한 | 객체 또는 DBA 권한 소유 | DROP 권한 | 개체 소유 | 개체 소유 |
| **실행 모니터링** | 권한 설명 | EXPLAIN 문을 사용하는 데 필요한 권한이 없습니다. | 권한 선택 | 시스템 관리자만 sp_showplan을 실행할 수 있습니다. | EXPLAIN 문을 사용하는 데 필요한 권한이 없습니다. | EXPLAIN 문을 사용하는 데 필요한 권한이 없습니다. | EXPLAIN 문을 사용하는 데 필요한 권한이 없습니다. |
| **데이터 쓰기** | DATAACCESS 권한 또는 권한 삽입 및 업데이트 | 권한 삽입 및 업데이트 | 권한 삽입 및 업데이트 | 권한 삽입 및 업데이트 | 권한 삽입 및 업데이트 | 권한 삽입 및 업데이트 | 권한 삽입 및 업데이트 |
| **표에 데이터 로드** | LOAD authority | COPY TO 및 COPY FROM 문을 각각 사용하려면 SELECT 및 INSERT 권한 | 파일 권한 | 테이블 또는 ALTER 권한이 있어야 합니다. -gl 옵션에 따라, LOAD TABLE은 사용자가 DBA 권한을 가지고 있는 경우에만 수행할 수 있습니다 | 권한 선택 및 삽입 | 권한 선택 및 삽입 | 권한 선택 및 삽입 |
| **클라이언트 데이터에 액세스** | 삽입/업데이트 권한 또는 DATAACCESS 기관 | 권한 선택 | 권한 선택 | 권한 선택 | 권한 선택 | 권한 선택 | 권한 선택 |
| **메타데이터 액세스** | DESCRIBE 문을 사용하는 데 필요한 권한 없음 | 권한 표시 | 권한 선택 | DESCRIBE 문을 사용할 수 있는 권한이 없습니다. | &quot;\d table&quot; 명령을 사용할 권한이 없습니다. | &quot;\d table&quot; 명령을 사용할 권한이 없습니다. | SHOW 명령을 사용하는 데 필요한 권한 없음 |