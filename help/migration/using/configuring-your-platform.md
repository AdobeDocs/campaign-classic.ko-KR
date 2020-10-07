---
title: 플랫폼 구성
seo-title: 플랫폼 구성
description: 플랫폼 구성
seo-description: null
page-status-flag: never-activated
uuid: e6255e4b-c9c8-4ac9-9ee3-aaa4dc9e5ecf
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migration-procedure
discoiquuid: 4d2e765b-750b-457f-ad55-8bd6faaa86af
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '943'
ht-degree: 2%

---


# 플랫폼 구성{#configuring-your-platform}

Adobe Campaign v7의 특정 주요 변경 사항은 효과적인 작업을 위해 구성이 필요합니다. 이러한 매개 변수는 마이그레이션 전이나 후에 필요할 수 있습니다. 관련 변경 사항 및 해당 구성 모드가 이 섹션에 표시됩니다.

마이그레이션하는 동안 NmsRecipient **테이블이** 스키마 정의에서 다시 빌드됩니다. Adobe Campaign 외부에 있는 이 테이블의 SQL 구조에 대한 모든 변경 사항은 손실됩니다.

확인할 요소 예:

* 열(또는 인덱스)을 **NmsRecipient** 테이블에 추가했지만 스키마에 구체적으로 설명된 것은 아니므로 저장되지 않습니다.
* 테이블스페이스 **** 속성은 기본적으로 해당 값을 되돌립니다(즉, 배포 마법사에 정의된 값).
* NmsRecipient 테이블에 참조 뷰를 추가한 경우 마이그레이션하기 전에 이를 삭제해야 합니다.

이 경고는 Oracle 사용자에게도 영향을 줍니다.업그레이드 후 중에 usetimestamptz:1 **** 옵션을 추가한 경우( [시간대](../../migration/using/general-configurations.md#time-zones)참조) 최소 한 개 이상의 **date+time** 필드를 포함하는 모든 테이블이다시만들어집니다.

## 마이그레이션 전 {#before-the-migration}

Adobe Campaign v7으로 마이그레이션할 때 다음 요소를 구성해야 합니다. 업그레이드 후 작업을 시작하기 전에 이러한 요소를 **해결해야 합니다**.

* 시간대

   v5.11 플랫폼에서 마이그레이션하는 동안 업그레이드 후 사용할 시간대를 지정해야 합니다.

   &quot;다중 시간대&quot; 모드를 사용하려면 [시간대](../../migration/using/general-configurations.md#time-zones) 섹션을 참조하십시오.

   Oracle을 데이터베이스로 사용하는 경우 Oracle 표준 시간대 파일이 응용 프로그램 서버와 데이터베이스 서버 간에 제대로 동기화되었는지 확인합니다. For more on this, refer to the [Oracle](../../migration/using/general-configurations.md#oracle) section.

* 보안 영역

   보안상의 이유로, 기본적으로 Adobe Campaign 플랫폼에 더 이상 액세스할 수 없습니다.마이그레이션 전에 사용자 IP 주소를 수집해야 하는 보안 영역을 구성해야 합니다.

   For more information, refer to the [Security](../../migration/using/general-configurations.md#security) section.

* 구문

   JavaScript의 특정 구문은 버전 5.11 및 6.02에서 사용할 수 있으며, 새 인터프리터의 사용으로 인해 v7 버전에서 더 이상 사용할 수 없습니다. For more information, refer to the [JavaScript](../../migration/using/general-configurations.md#javascript) section.

   마찬가지로, SQLData 기반 구문을 바꾸기 위해 Adobe Campaign v7에 새로운 구문이 도입됩니다. 이 구문과 함께 코드 요소를 사용하는 경우 이를 조정해야 합니다. For more information, refer to the [SQLData](../../migration/using/general-configurations.md#sqldata) section.

* 암호

   관리자 및 **내부** 암호를 **구성해야** 합니다. For more information, refer to the [User passwords](../../migration/using/before-starting-migration.md#user-passwords) section.

* 트리 구조

   v5.11 플랫폼에서 마이그레이션하는 경우 Adobe Campaign v6 규범에 따라 트리 구조 폴더를 다시 구성해야 합니다. 자세한 내용은 [Adobe Campaign v7 트리 구조](../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure) 섹션을 참조하십시오.

* 상호 작용

   상호 작용 **을**&#x200B;사용하는 경우 v7에 더 이상 존재하지 않는 모든 6.02 스키마 참조를 삭제해야 합니다. For more information, refer to the [Interaction](../../migration/using/general-configurations.md#interaction) section.

## 마이그레이션 후 {#after-the-migration}

업그레이드 **후**&#x200B;실행 후 다음 요소를 고려해야 하며 해당 구성을 수행해야 합니다.

* 페이지 미러

   v6.x에서 페이지 개인화 블록이 변경되었습니다.이 새 버전은 이러한 페이지에 액세스할 때 보안을 향상시킵니다.

   메시지에 v5 개인화 블록을 사용한 경우 미러 페이지 표시가 실패합니다. Adobe은 메시지에 미러 페이지를 삽입할 때 새로운 개인화 블록을 사용하는 것이 좋습니다.

   그러나 임시 솔루션으로서(미러 페이지가 여전히 활성 상태인 경우) 옵션을 변경하여 이 문제를 방지하려면 이전 개인화 블록 **[!UICONTROL XtkAcceptOldPasswords]** 으로 되돌릴 수 있습니다 **[!UICONTROL 1]**. 새로운 v6.x 개인화 블록 사용에는 영향을 주지 않습니다.

* 구문

   구문과 관련된 오류가 발생하면 업그레이드 후 진행되는 동안 **serverConf.xml** 파일에서 allowSQLInjection **** 옵션을 일시적으로 활성화해야 합니다. 이렇게 하면 코드를 다시 작성할 수 있습니다. 코드가 조정되면 보안을 다시 활성화하십시오. For more on this, refer to the [SQLData](../../migration/using/general-configurations.md#sqldata) section.

* 충돌

   마이그레이션은 업그레이드 후 수행되므로 보고서, 양식 또는 웹 응용 프로그램에 충돌이 발생할 수 있습니다. 콘솔에서 이러한 충돌을 해결할 수 있습니다.

   충돌 [섹션을](../../migration/using/general-configurations.md#conflicts) 참조하십시오.

* Tomcat

   설치 폴더를 사용자 지정한 경우 마이그레이션 후 올바르게 업데이트되었는지 확인하십시오. 자세한 내용은 [Tomcat](../../migration/using/general-configurations.md#tomcat) 섹션을 참조하십시오.

* 보고서

   모든 기본 보고서는 현재 v6.x 렌더링 엔진을 사용합니다. 보고서에 JavaScript 코드를 추가한 경우 일부 요소가 변경될 수 있습니다.

   보고서 [섹션을](../../migration/using/general-configurations.md#reports) 참조하십시오.

* 웹 애플리케이션

   업그레이드 후 식별된 웹 응용 프로그램에 연결하는 데 문제가 있는 경우 **serverConf.xml** 파일의 allowUserPassword **및** sessionTokenOnly **옵션을** 활성화해야합니다. 이 두 옵션을 비활성화해야 합니다. 자세한 내용은 식별된 [웹 애플리케이션](../../migration/using/general-configurations.md#identified-web-applications) 섹션을 참조하십시오.

   웹 응용 프로그램의 유형 및 구성에 따라 해당 응용 프로그램이 제대로 작동하는지 확인하려면 추가 작업을 수행해야 합니다.

   웹 [애플리케이션](../../migration/using/general-configurations.md#web-applications) 섹션을 참조하십시오.

   v5.11 플랫폼에서 마이그레이션하는 경우 추가 구성을 수행해야 합니다.자세한 내용은 [웹 애플리케이션](../../migration/using/specific-configurations-in-v5-11.md#web-applications) 섹션을 참조하십시오.

* 보안 구역

   서버를 시작하기 전에 보안 영역을 구성해야 합니다. 자세한 내용은 [이 섹션](../../installation/using/configuring-campaign-server.md#defining-security-zones) 및 [보안](../../migration/using/general-configurations.md#security) 섹션을 참조하십시오.

* 스키마

   Red Hat에서는 특정 스키마를 편집할 때 오류가 발생할 수 있습니다. For more on this, refer to the [Red-Hat](../../migration/using/general-configurations.md#red-hat) section.

* 워크플로우

   v5.11 플랫폼에서 마이그레이션하는 경우 워크플로우 런타임 디렉토리를 제어해야 합니다. For more on this, refer to the [Workflows](../../migration/using/specific-configurations-in-v5-11.md#workflows) section.

* 추적

   v5.11 플랫폼에서 마이그레이션하는 경우 추적 모드를 구성해야 합니다. For more on this, refer to the [Tracking](../../migration/using/specific-configurations-in-v5-11.md#tracking) section.

* 홈페이지

   v6.02 플랫폼에서 마이그레이션하는 경우, v6.02에서 이전 홈 페이지를 유지할 수 있도록 추가 매개 변수를 정의할 수 있습니다. 이에 대한 자세한 내용은 [사용자 친화성을 참조하십시오.홈 페이지 및 탐색](../../migration/using/specific-configurations-in-v6-02.md#user-friendliness--home-page-and-navigation) 섹션.

* 상호 작용

   상호 작용 **을**&#x200B;사용하는 경우 마이그레이션 후 모든 매개 변수를 조정해야 합니다. For more on this, refer to the [Interaction](../../migration/using/general-configurations.md#interaction) section.

