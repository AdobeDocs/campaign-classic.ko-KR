---
title: 분산 아키텍처
seo-title: 분산 아키텍처
description: 분산 아키텍처
seo-description: null
page-status-flag: never-activated
uuid: f672446f-18e6-4fff-81a1-01ee22792755
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: advanced-parameters
discoiquuid: 811a42a4-552c-49cb-bffd-7e124ef83735
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1013'
ht-degree: 1%

---


# 분산 아키텍처{#distributed-architectures}

## 원칙 {#principle}

확장성을 지원하고 인바운드 채널에서 24시간 연중무휴 서비스를 제공하려면 분산 아키텍처와 상호 작용을 사용할 수 있습니다. 이 유형의 아키텍처는 메시지 센터에서 이미 사용되고 있으며 다음과 같은 여러 인스턴스로 구성됩니다.

* 마케팅 및 환경 디자인 기반이 포함된 아웃바운드 채널에 전용 하나 또는 여러 개의 컨트롤 인스턴스
* 인바운드 채널에 전용 하나 또는 여러 개의 실행 인스턴스

![](assets/interaction_powerbooster_schema.png)

>[!NOTE]
>
>제어 인스턴스는 인바운드 채널에 전용되며 카탈로그의 온라인 버전을 포함합니다. 모든 실행 인스턴스는 독립적이며 하나의 연락처 세그먼트 전용(예: 국가당 하나의 실행 인스턴스)입니다. 오퍼 엔진 호출은 실행에 대해 직접 수행해야 합니다(실행 인스턴스당 하나의 특정 URL). 인스턴스 간 동기화가 자동으로 수행되지 않으므로 동일한 연락처의 상호 작용이 동일한 인스턴스를 통해 전송되어야 합니다.

## 제안 동기화 {#proposition-synchronization}

오퍼 동기화는 패키지를 통해 수행됩니다. 실행 인스턴스의 경우 모든 카탈로그 개체가 외부 계정 이름으로 접두사로 추가됩니다. 즉, 동일한 실행 인스턴스에서 여러 제어 인스턴스(예: 개발 및 프로덕션 인스턴스)를 지원할 수 있습니다.

>[!CAUTION]
>
>짧고 명시적인 내부 이름을 사용하는 것이 좋습니다.

오퍼는 자동으로 배포되고 실행 및 제어 인스턴스에 게시됩니다.

디자인 환경에서 삭제된 오퍼는 모든 온라인 인스턴스에서 비활성화됩니다. 사용되지 않는 프로필 및 오퍼는 제거 기간(각 인스턴스의 배포 길잡이에 지정됨) 및 슬라이딩 기간(들어오는 속성의 유형 규칙에 지정됨) 이후 모든 인스턴스에서 자동으로 삭제됩니다.

![](assets/interaction_powerbooster_schema2.png)

제안 동기화를 위한 각 환경 및 외부 계정에 대해 워크플로우가 생성됩니다. 동기화 빈도는 각 환경 및 외부 계정에 맞게 조정할 수 있습니다.

## 제한 사항 {#limitations}

* 익명 환경에서 식별된 환경으로 폴백 기능을 사용하는 경우 이러한 두 환경이 동일한 실행 인스턴스에 있어야 합니다.
* 여러 실행 인스턴스 간의 동기화가 실시간으로 수행되지 않습니다. 동일한 연락처의 상호 작용은 동일한 인스턴스로 전송되어야 합니다. 컨트롤 인스턴스는 아웃바운드 채널 전용(실시간 아님)이어야 합니다.
* 마케팅 데이터베이스가 자동으로 동기화되지 않습니다. 가중치 및 자격 조건 규칙에 사용된 마케팅 데이터는 실행 인스턴스에 복제되어야 합니다. 이 프로세스는 표준이 아닙니다. 통합 기간 동안 개발해야 합니다.
* 제안 동기화는 FDA 연결에서만 수행됩니다.
* 동일한 인스턴스에서 상호 작용 및 메시지 센터를 사용하는 경우 두 경우 모두 FDA 프로토콜을 통해 동기화가 발생합니다.

## 패키지 구성 {#packages-configuration}

상호 작용 **에** 직접 연결된 모든 스키마 확장 를 실행 인스턴스에 배포해야 합니다.

상호 작용 패키지는 모든 인스턴스(제어 및 실행)에 설치해야 합니다. 두 개의 추가 패키지를 사용할 수 있습니다.컨트롤 인스턴스에 설치할 패키지 하나와 각 실행 인스턴스에 설치할 패키지 하나.

>[!NOTE]
>
>패키지를 설치할 때 **nms:promise** 표(예: 제안 ID)의 **긴** 유형 필드가 **int64** 유형 필드가 됩니다. 이 유형의 데이터는 [이 섹션에 자세히 설명되어 있습니다](../../configuration/using/schema-structure.md#mapping-the-types-of-adobe-campaign-dbms-data).

데이터 유지 기간은 각 인스턴스에 구성해야 합니다(배포 마법사의 창 **[!UICONTROL Data purge]** 을 통해). 실행 인스턴스의 경우 이 기간은 분류 규칙(슬라이딩 기간) 및 계산할 자격 조건 규칙에 필요한 내역 깊이에 해당되어야 합니다.

컨트롤 인스턴스:

1. 실행 인스턴스별로 외부 계정 만들기:

   ![](assets/interaction_powerbooster1.png)

   * 레이블을 작성하고 간단하고 명시적인 내부 이름을 추가합니다.
   * **[!UICONTROL Execution instance]**&#x200B;을(를) 선택합니다.
   * **[!UICONTROL Enabled]** 옵션을 선택합니다.
   * 실행 인스턴스의 연결 매개 변수를 완료합니다.
   * 모든 실행 인스턴스는 ID에 연결해야 합니다. 이 ID는 단추를 클릭하면 **[!UICONTROL Initialize connection]** 할당됩니다.
   * 사용되는 응용 프로그램 유형을 확인합니다. **[!UICONTROL Message Center]**, **[!UICONTROL Interaction]**&#x200B;또는 both.
   * 사용한 FDA 계정을 입력합니다. 연산자는 실행 인스턴스에 생성되어야 하며 해당 인스턴스의 데이터베이스에 다음과 같은 읽기 및 쓰기 권한이 있어야 합니다.

      ```
      grant SELECT ON nmspropositionrcp, nmsoffer, nmsofferspace, xtkoption, xtkfolder TO user;
      grant DELETE, INSERT, UPDATE ON nmspropositionrcp TO user;
      ```
   >[!NOTE]
   >
   >제어 인스턴스의 IP 주소는 실행 인스턴스에 대해 인증되어야 합니다.

1. 환경 구성:

   ![](assets/interaction_powerbooster2.png)

   * 실행 인스턴스 목록을 추가합니다.
   * 각 항목에 대해 동기화 기간 및 필터 기준(예: 국가별)을 지정합니다.

      >[!NOTE]
      >
      >오류가 발생하면 동기화 워크플로우와 알림을 제공할 수 있습니다. 이러한 내용은 애플리케이션의 기술 워크플로우에서 확인할 수 있습니다.

최적화 이유로 마케팅 데이터베이스의 일부만 실행 인스턴스에 복제되는 경우 환경에 연결된 제한된 스키마를 지정하여 사용자가 실행 인스턴스에서 사용할 수 있는 데이터만 사용하도록 허용할 수 있습니다. 실행 인스턴스에서 사용할 수 없는 데이터를 사용하여 오퍼를 만들 수 있습니다. 이렇게 하려면 아웃바운드 채널(필드)에서 이 규칙을 제한하여 다른 채널의 규칙을&#x200B;**[!UICONTROL Taken into account if]** 비활성화해야 합니다.

![](assets/ita_filtering.png)

## 유지 관리 옵션 {#maintenance-options}

다음은 제어 인스턴스에서 사용할 수 있는 유지 관리 옵션 목록입니다.

>[!CAUTION]
>
>이러한 옵션은 특정 유지 관리 케이스에만 사용해야 합니다.

* **`NmsInteraction_LastOfferEnvSynch_<offerEnvId>_<executionInstanceId>`**:지정된 인스턴스에서 환경이 동기화된 마지막 날짜입니다.
* **`NmsInteraction_LastPropositionSynch_<propositionSchema>_<executionInstanceIdSource>_<executionInstanceIdTarget>`**:지정된 스키마에서 다른 인스턴스로 메시지가 동기화된 마지막 날짜입니다.
* **`NmsInteraction_MapWorkflowId`**:생성된 모든 동기화 워크플로우 목록이 포함된 옵션

실행 인스턴스에서 다음 옵션을 사용할 수 있습니다.

**NmsExecutionInstanceId**:옵션을 포함합니다.

## 패키지 설치 {#packages-installation}

인스턴스에 이전에 상호 작용 패키지가 없는 경우 마이그레이션이 필요하지 않습니다. 기본적으로 패키지는 설치된 후 제안 테이블이 64비트로 표시됩니다.

>[!CAUTION]
>
>인스턴스에 있는 기존 속성의 볼륨에 따라 이 작업에 시간이 걸릴 수 있습니다.

* 인스턴스에 제안이 거의 없거나 없는 경우 제안 테이블을 수동으로 수정할 필요가 없습니다. 패키지가 설치되면 수정 작업이 수행됩니다.
* 인스턴스에 많은 문제가 있는 경우 제어 패키지를 설치하고 실행하기 전에 프로필 테이블의 구조를 변경하는 것이 좋습니다. 활동이 낮은 기간 동안 쿼리를 실행하는 것이 좋습니다.

>[!NOTE]
>
>제안 표에서 특정 구성을 수행한 경우 이에 따라 쿼리를 조정합니다.

### PostgreSQL {#postgresql}

두 가지 방법이 있습니다. 첫 번째(작업 테이블 사용)는 약간 더 빠릅니다.

**작업 테이블**

```
CREATE TABLE NmsPropositionRcp_tmp AS SELECT * FROM nmspropositionrcp WHERE 0=1;
ALTER TABLE nmspropositionrcp_tmp
  ALTER COLUMN ipropositionid TYPE bigint,
  ALTER COLUMN iinteractionid TYPE bigint;
INSERT INTO nmspropositionrcp_tmp SELECT * FROM nmspropositionrcp;
DROP TABLE nmspropositionrcp;
CREATE INDEX proposition_id ON NmsPropositionRcp (ipropositionid);
CREATE INDEX nmspropositionrcp_deliveryid ON NmsPropositionRcp (ideliveryid);
CREATE INDEX nmspropositionrcp_lastmodified ON NmsPropositionRcp (tslastmodified);
CREATE INDEX nmspropositionrcp_offerid ON NmsPropositionRcp (iofferid);
CREATE INDEX nmspropositionrcp_offerspaceid ON NmsPropositionRcp (iofferspaceid);
CREATE INDEX nmspropositionrcp_recipientidid ON NmsPropositionRcp (irecipientid);
ALTER TABLE nmspropositionrcp_tmp RENAME TO nmspropositionrcp;
```

**테이블 변경**

```
ALTER TABLE nmspropositionrcp
  ALTER COLUMN ipropositionid TYPE bigint,
  ALTER COLUMN iinteractionid TYPE bigint;
```

### Oracle {#oracle}

숫자 유형의 크기를 편집해도 **값** 또는 인덱스가 다시 작성되지 않습니다. 그러므로 그것은 즉각적이다.

실행할 쿼리는 다음과 같습니다.

```
ALTER TABLE nmspropositionrcp MODIFY (
ipropositionid NUMBER(19, 0),
iinteractionid NUMBER(19, 0)
);
```

### MSSQL {#mssql}

실행할 쿼리는 다음과 같습니다.

```
SELECT * INTO NmsPropositionRcp_tmp FROM NmsPropositionRcp WHERE 1 = 0;
GO
ALTER TABLE NmsPropositionRcp_tmp ALTER COLUMN ipropositionid BIGINT;
GO
ALTER TABLE NmsPropositionRcp_tmp ALTER COLUMN iinteractionid BIGINT;
GO
INSERT INTO NmsPropositionRcp_tmp SELECT * FROM NmsPropositionRcp;
GO
DROP TABLE NmsPropositionRcp;
GO
sp_rename 'NmsPropositionRcp_tmp', NmsPropositionRcp
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR dWeight
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iDeliveryId
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iEngineType
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iInteractionId
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iOfferId
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iOfferSpaceId
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iPropositionId
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iRank
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iRecipientId
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iStatus
GO
CREATE NONCLUSTERED INDEX NmsPropositionRcp_deliveryId ON NmsPropositionRcp (iDeliveryId)
GO
CREATE NONCLUSTERED INDEX NmsPropositionRcp_eventDate ON NmsPropositionRcp (tsEvent)
GO
CREATE UNIQUE NONCLUSTERED INDEX NmsPropositionRcp_id ON NmsPropositionRcp (iPropositionId)
GO
CREATE NONCLUSTERED INDEX NmsPropositionRcp_lastModified ON NmsPropositionRcp (tsLastModified)
GO
CREATE NONCLUSTERED INDEX NmsPropositionRcp_offerId ON NmsPropositionRcp (iOfferId)
GO
CREATE NONCLUSTERED INDEX NmsPropositionRcp_offerSpaceI ON NmsPropositionRcp (iOfferSpaceId)
GO
CREATE NONCLUSTERED INDEX NmsPropositionRcp_recipientId ON NmsPropositionRcp (iRecipientId)
GO
```

