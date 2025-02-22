---
product: campaign
title: 표준 시간대 관리
description: 표준 시간대 관리
feature: Installation, Instance Settings
badge-v7-prem: label="온-프레미스/하이브리드만" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: e5ed96cc-3fc7-4af4-a29e-5a4c81f4fe39
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '951'
ht-degree: 1%

---

# 표준 시간대 관리{#time-zone-management}



## 운영 원칙 {#operating-principle}

Adobe Campaign을 사용하면 날짜를 시간대의 함수로 표현할 수 있습니다. 이렇게 하면 국제 사용자가 다양한 시간대에서 전 세계에서 작업할 수 있습니다. 동일한 인스턴스를 사용하는 각 국가는 캠페인 실행, 추적, 보관 등을 관리할 수 있습니다. 현지 시간에 따라 다릅니다.

국제적 규모로 Adobe Campaign 플랫폼을 사용하려면 시스템에서 사용하는 모든 날짜를 시간대에 연결할 수 있어야 합니다. 시간대가 알려진 날짜는 시간대에 상관없이 다른 시간대로 가져올 수 있습니다.

Adobe Campaign을 사용하면 날짜/시간을 UTC(협정 세계시) 형식으로 저장할 수 있습니다. 데이터가 노출되면 연산자의 로컬 날짜/시간으로 변환됩니다. 데이터베이스가 UTC로 구성되면 자동으로 변환됩니다([구성](#configuration) 참조). 데이터베이스가 UTC로 구성되지 않은 경우 플랫폼 날짜의 시간대에 대한 정보가 옵션에 저장됩니다.

시간대 관리와 관련된 주요 플랫폼 기능은 데이터 가져오기/내보내기, 운영자 및 워크플로우 관리입니다. **상속 개념**&#x200B;은(는) 가져오기/내보내기 또는 워크플로에 사용할 수 있습니다. 기본적으로 데이터베이스 서버 시간대에 대해 구성되지만 워크플로우 및 단일 활동에 대해 새 시간대를 재정의할 수 있습니다.

**연산자**&#x200B;은(는) **게재 구성** 중에 시간대를 수정할 수 있으며 게재를 실행할 특정 시간대를 지정할 수 있습니다.

>[!IMPORTANT]
>
>데이터베이스가 여러 시간대를 관리하지 않는 경우 모든 데이터 필터링 작업의 경우 데이터베이스 서버의 시간대에서 SQL 쿼리를 실행해야 합니다.

각 Adobe Campaign 연산자는 시간대에 연결됩니다. 이 정보는 프로필에 구성됩니다. 자세한 정보는 [이 문서](../../platform/using/access-management.md)를 참조하세요.

Adobe Campaign 플랫폼에서 시간대 관리가 필요하지 않은 경우 특정 연결된 시간대를 사용하여 저장소 모드를 로컬 형식으로 유지할 수 있습니다.

## 추천 {#recommendations}

시간대는 여러 현실을 결합합니다. 표현식은 UTC 날짜와 함께 일정한 시차를 나타내거나 일년에 두 번 변경될 수 있는 지역의 시간(일광 절약 시간)을 나타낼 수 있습니다.

예를 들어, postgreSQL에서 **SET 시간대 &#39;Europe/Paris&#39;;** 명령은 여름 및 겨울 시간을 고려합니다. 날짜는 연중 시간에 따라 UTC+1 또는 UTC+2로 표현됩니다.

그러나 **SET TIME ZONE 0200;** 명령을 사용하는 경우 시간 지연은 항상 UTC+2가 됩니다.

## 구성 {#configuration}

데이터베이스를 만드는 동안 날짜 및 시간에 대한 저장소 모드를 선택했습니다([새 인스턴스 만들기](#creating-a-new-instance) 참조). 마이그레이션하는 경우 날짜에 연결된 시간이 로컬 날짜와 시간으로 변환됩니다([마이그레이션](#migration) 참조).

기술적인 관점에서 보면 데이터베이스에 **날짜+시간** 형식 정보를 저장하는 두 가지 방법이 있습니다.

1. 시간대 형식이 있는 타임스탬프: 데이터베이스 엔진이 날짜를 UTC로 저장합니다. 열린 각 세션에는 시간대가 있으며 그에 따라 날짜가 변환됩니다.
1. 로컬 형식 + 로컬 시간대: 모든 날짜는 로컬 형식(시간 지연 관리 없음)으로 저장되고 단일 시간대가 할당됩니다. 시간대는 Adobe Campaign 인스턴스의 **WdbcTimeZone** 옵션에 저장되며 트리의 **[!UICONTROL Administration > Platform > Options]** 메뉴를 통해 변경할 수 있습니다.

>[!IMPORTANT]
>
>이 수정으로 인해 데이터 일관성 및 동기화 문제가 발생할 수 있습니다.

### 새 인스턴스 만들기 {#creating-a-new-instance}

여러 명의 해외 사용자가 동일한 인스턴스에서 작업하려면 인스턴스를 만들 때 국가 간 시간대를 관리하도록 시간대를 구성해야 합니다. 인스턴스를 만드는 동안 데이터베이스 구성 단계의 **[!UICONTROL Time zone]** 섹션에서 날짜 및 시간 관리 모드를 선택하십시오.

날짜 및 시간이 포함된 모든 데이터를 UTC 형식(SQL 필드 및 XML 필드)으로 저장하려면 **[!UICONTROL UTC database (date fields with time zone)]** 옵션을 선택하십시오.

![](assets/install_wz_select_utc_option.png)

>[!IMPORTANT]
>
>**Oracle**&#x200B;을(를) 사용하는 경우 Oracle 클라이언트 레이어의 시간대 파일(.dat)이 서버에 설치된 시간대 파일과 호환되어야 합니다.

데이터베이스가 UTC가 아닌 경우 드롭다운 목록에서 제공된 시간대 중 하나를 선택할 수 있습니다. 서버의 시간대를 사용하거나 UTC(협정 세계시) 옵션을 선택할 수도 있습니다.

![](assets/install_wz_unselect_utc_option.png)

**[!UICONTROL UTC Database (date fields with time zone)]** 옵션을 선택하면 SQL 필드가 TIMESTAMP WITH TIMEZONE 형식으로 저장됩니다.

그렇지 않으면 로컬 형식으로 저장되며 데이터베이스에 적용할 시간대를 선택해야 합니다.

### 마이그레이션 {#migration}

시간대 관리 없이 이전 버전으로 마이그레이션할 때 데이터베이스에서 날짜 저장 영역 모드를 정의해야 합니다.

Adobe Campaign 데이터베이스에 액세스하는 외부 도구와의 호환성을 보장하기 위해 **Date+time** 유형 SQL 필드는 기본적으로 로컬 형식으로 저장됩니다.

날짜가 포함된 XML 필드는 이제 UTC로 저장됩니다. 로드하는 동안 UTC 형식이 아닌 필드는 서버의 시간대를 사용하여 자동으로 변환됩니다. 즉, 모든 XML 필드가 점진적으로 UTC 형식으로 변환됩니다.

기존 인스턴스를 사용하려면 **WdbcTimeZone** 옵션을 추가하고 인스턴스의 시간대를 입력하십시오.

>[!IMPORTANT]
>
>WdbcTimeZone 옵션에 대해 올바른 값이 구성되었는지 확인하십시오. 나중에 변경하면 일관성이 없을 수 있습니다.

가능한 값의 예:

* 유럽/파리,
* 유럽/런던
* 아메리카/뉴욕 등

  이 값은 tz(Olson) 데이터베이스에서 가져옵니다. 자세한 내용은 [https://en.wikipedia.org/wiki/List_of_tz_database_time_zones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)을(를) 참조하세요.

## Oracle 데이터베이스 및 서버 시간대

기본 데이터베이스의 경우 Campaign은 서버 시간대를 사용하여 데이터베이스 연결에서 세션 시간대를 설정합니다. &quot;WdbcTimeZone&quot; 옵션은 영향을 주지 않습니다. 따라서 서버 시간대는 Campaign에서 사용하는 기본 데이터베이스의 시간대와 일치해야 합니다. 서버 시간대를 변경할 수 없는 경우 customer.sh에서 TZ 환경 변수를 설정하여 Campaign에서 사용하는 시간대를 재정의할 수 있습니다.