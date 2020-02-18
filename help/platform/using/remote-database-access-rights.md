---
title: 외부 데이터베이스 액세스
seo-title: 외부 데이터베이스 액세스
description: 외부 데이터베이스 액세스
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d2758b5e81d1720a4f01a610e51c4a33995d88d1

---


# 원격 데이터베이스 액세스 권한 {#remote-database-access-rights}

먼저 사용자가 FDA를 통해 외부 데이터베이스에서 작업을 수행할 수 있도록 Adobe Campaign에서 특정 이름이 지정되어 있어야 합니다.

1. Adobe Campaign **[!UICONTROL Administration > Access Management > Named Rights]** 탐색기에서 노드를 선택합니다.
1. 선택한 레이블을 지정하여 새 권한을 만듭니다.
1. 이 **[!UICONTROL Name]** 필드에는 다음 형식 **사용자가 있어야 합니다.base@server**. 여기서 :

   * **사용자는** 외부 데이터베이스의 사용자 이름과 일치합니다.
   * **base** 는 외부 데이터베이스 이름과 일치합니다.
   * **서버는** 외부 데이터베이스 서버의 이름과 일치합니다.

      >[!NOTE]
      >
      >Oracle에서 **:base** 부분은 선택 사항입니다.

1. 이름을 마우스 오른쪽 단추로 저장한 다음 Adobe Campaign 탐색기의 **[!UICONTROL Administration > Access Management > Operators]** 노드에서 선택한 사용자에게 연결합니다.

그런 다음 외부 데이터베이스에 포함된 데이터를 처리하려면 Adobe Campaign 사용자가 작업 테이블을 만들 수 있도록 데이터베이스에 대해 &#39;쓰기&#39; 권한이 있어야 합니다. Adobe Campaign에서 자동으로 삭제됩니다.

일반적으로 다음과 같은 권한이 필요합니다.

* **연결**:원격 데이터베이스에 대한 연결,
* **데이터 읽기**:고객 데이터가 포함된 테이블에 대한 읽기 전용 액세스,
* **&#39;MetaData&#39;**&#x200B;보기:서버 데이터 카탈로그에 액세스하여 테이블 구조를 가져옵니다.
* **로드**:작업 테이블에서 대량 로드(컬렉션 및 조인 작업 시 필수),
* **테이블/인덱스** / **프로시저/함수 만들기/삭제**,
* **설명** (권장):문제가 있을 경우 공연을 모니터링하기 위해
* **WRITE 데이터** (통합 시나리오에 따라 다름).

>[!NOTE]
>
>데이터베이스 관리자는 이러한 권한을 각 데이터베이스 엔진과 관련된 권한과 일치시켜야 합니다. 자세한 내용은 RDBMS [특정 권한을](https://docs.campaign.adobe.com/doc/AC6.1/en/technicalResources/technicalResources.html)참조하십시오.