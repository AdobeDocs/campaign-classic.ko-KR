---
title: 시간대 관리
seo-title: 시간대 관리
description: 시간대 관리
seo-description: null
page-status-flag: never-activated
uuid: b8926761-65e2-48fd-8689-2ae6b0596e72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: b9846eda-eeca-433e-b961-6dfc2aa2708b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 963aaa81971a8883b944bfcf4d1a00d729627916

---


# 시간대 관리{#time-zone-management}

## 운영 원칙 {#operating-principle}

Adobe Campaign을 사용하면 날짜를 시간대의 기능으로 표현할 수 있습니다.이를 통해 전세계 사용자는 다양한 시간대에서 작업할 수 있습니다. 동일한 인스턴스를 사용하는 각 국가는 캠페인 실행, 추적, 보관 등을 관리할 수 있습니다. 현지 시간에 따라 다릅니다.

Adobe Campaign 플랫폼을 국제적인 규모로 사용하려면 시스템에서 사용하는 모든 날짜를 표준 시간대에 연결할 수 있어야 합니다. 따라서 표준 시간대를 알 수 있는 날짜는 다른 표준 시간대 또는 표준 시간대와 상관없이 가져올 수 있습니다.

Adobe Campaign을 사용하면 날짜/시간을 UTC(협정 세계시) 형식으로 저장할 수 있습니다. 데이터가 노출되면 연산자의 로컬 날짜/시간으로 변환됩니다. 데이터베이스가 UTC에 구성되면 변환이 자동으로 수행됩니다(구성 [참조](#configuration)). 데이터베이스가 UTC에 구성되지 않은 경우 플랫폼의 날짜 표준 시간대에 대한 정보가 옵션으로 저장됩니다.

시간대 관리와 관련된 주요 플랫폼 기능은 다음과 같습니다.데이터 및 연산자 가져오기/내보내기 및 워크플로우 관리 상속 개념은 **** 가져오기/내보내기 또는 워크플로우에 사용할 수 있습니다. 기본적으로 데이터베이스 서버 표준 시간대로 구성되지만 워크플로우와 단일 활동에 대해 새 시간대를 재정의할 수 있습니다.

**연산자를** 사용하면 **배달 구성** 중에 시간대를 수정할 수 있고 배달을 실행할 특정 시간대를 지정할 수 있습니다.

>[!CAUTION]
>
>데이터베이스가 여러 시간대를 관리하지 않는 경우 모든 데이터 필터링 작업에 대해 데이터베이스 서버의 시간대에서 SQL 쿼리를 실행해야 합니다.

각 Adobe Campaign 운영자가 표준 시간대에 연결됩니다.이 정보는 프로필에 구성됩니다. For more on this, refer to [this document](../../platform/using/access-management.md).

Adobe Campaign 플랫폼에 표준 시간대 관리가 필요하지 않은 경우 특정 연결된 표준 시간대로 저장소 모드를 로컬 형식으로 유지할 수 있습니다.

## Recommendations {#recommendations}

시간대는 다음과 같은 여러 현실을 결합합니다.이 표현식은 UTC 날짜와의 일정한 시간 지연이나 일년에 두 번(일광 절약 시간) 시간을 변경할 수 있는 지역의 시간을 설명할 수 있습니다.

**예를 들어 postgreSQL에서 SET** TIME ZONE &#39;Europe/Paris&#39;;명령은 여름 및 겨울 시간을 고려합니다.날짜는 연도의 시간에 따라 UTC+1 또는 UTC+2로 표시됩니다.

**그러나 설정**&#x200B;표준 시간대 0200을 사용하는 경우command 키, 시간 지연은 항상 UTC+2입니다.

## 구성 {#configuration}

데이터베이스 생성 중에 날짜 및 시간에 대한 저장소 모드가 선택됩니다(새 [인스턴스](#creating-a-new-instance)만들기 참조). 마이그레이션의 경우 날짜에 연결된 시간이 로컬 날짜 및 시간으로 변환됩니다(마이그레이션 [참조](#migration)).

기술적인 관점에서 보면 데이터베이스에 Date+ **time** 유형 정보를 저장하는 두 가지 방법이 있습니다.

1. 표준 시간대 형식을 사용하는 타임스탬프:데이터베이스 엔진은 날짜를 UTC에 저장합니다. 열린 각 세션에는 시간대가 있으며, 날짜는 그에 따라 변환됩니다.
1. 로컬 형식 + 로컬 표준 시간대:모든 날짜는 로컬 형식(시간 지연 관리 없음)으로 저장되고 단일 표준 시간대가 할당됩니다. 표준 시간대는 Adobe Campaign **인스턴스의 WdbcTimeZone** 옵션에 저장되며 트리의 **[!UICONTROL Administration > Platform > Options]** 메뉴를 통해 변경할 수 있습니다.

>[!CAUTION]
>
>이 수정 사항으로 인해 데이터 일관성 및 동기화 문제가 발생할 수 있습니다.

### 새 인스턴스 만들기 {#creating-a-new-instance}

여러 국제 사용자가 동일한 인스턴스에서 작업하려면 국가 간 시간 지연을 관리할 인스턴스를 만들 때 시간대를 구성해야 합니다. 인스턴스를 생성하는 동안 데이터베이스 구성 단계의 **[!UICONTROL Time zone]** 섹션에서 날짜 및 시간 관리 모드를 선택합니다.

날짜 및 시간이 있는 모든 데이터를 UTC 형식(SQL 필드 및 XML 필드)으로 저장하려면 **[!UICONTROL UTC database (date fields with time zone)]** 옵션을 선택합니다.

![](assets/install_wz_select_utc_option.png)

>[!CAUTION]
>
>Oracle을 사용하는 **경우** Oracle 클라이언트 레이어의 시간대 파일(.dat)은 서버에 설치된 시간대 파일과 호환되어야 합니다.

데이터베이스가 UTC가 아닌 경우 드롭다운 목록에 제공되는 시간대 중 하나를 선택할 수 있습니다. 서버의 표준 시간대를 사용하거나 UTC(협정 세계시) 옵션을 선택할 수도 있습니다.

![](assets/install_wz_unselect_utc_option.png)

이 **[!UICONTROL UTC Database (date fields with time zone)]** 옵션을 선택하면 SQL 필드가 TIMEZONE 형식의 TIMESTAMP에 저장됩니다.

그렇지 않으면 로컬 형식으로 저장되므로 데이터베이스에 적용할 시간대를 선택해야 합니다.

### 마이그레이션 {#migration}

시간대 관리 없이 이전 버전으로 마이그레이션할 때 데이터베이스에서 날짜 저장소 모드를 정의해야 합니다.

Adobe Campaign 데이터베이스에 액세스하는 외부 도구와의 호환성을 보장하기 위해 **날짜+시간** 유형 SQL 필드는 기본적으로 로컬 형식으로 저장됩니다.

날짜가 포함된 XML 필드는 이제 UTC에 저장됩니다. 로드하는 동안 UTC 형식이 아닌 필드는 서버의 시간대를 사용하여 자동으로 변환됩니다. 즉, 모든 XML 필드가 점진적으로 UTC 형식으로 변환됩니다.

기존 인스턴스를 사용하려면 WdbcTimeZone **옵션을** 추가하고 인스턴스의 표준 시간대를 입력합니다.

>[!CAUTION]
>
>WdbcTimeZone 옵션에 대해 올바른 값이 구성되어 있는지 확인하십시오.나중에 수행된 변경 사항으로 인해 불일치가 발생할 수 있습니다.

가능한 값의 예:

* 유럽/파리,
* 유럽/런던,
* 미국/뉴욕 등

   이러한 값은 tz(Olson) 데이터베이스에서 가져옵니다. 자세한 내용은 https://en.wikipedia.org/wiki/List_of_tz_database_time_zones을 [참조하십시오](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).

