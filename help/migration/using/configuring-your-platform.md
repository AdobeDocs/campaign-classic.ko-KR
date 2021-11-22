---
product: campaign
title: 플랫폼 구성
description: 플랫폼 구성
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: ad71dead-c0ca-42d5-baa8-0f340979231a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '940'
ht-degree: 1%

---

# 플랫폼 구성{#configuring-your-platform}

![](../../assets/v7-only.svg)

Adobe Campaign v7의 특정 주요 변경 사항에는 효과적인 운영을 위해 구성이 필요합니다. 이러한 매개 변수는 마이그레이션 전이나 후에 필요할 수 있습니다. 관련 변경 사항 및 구성 모드가 이 섹션에 나와 있습니다.

마이그레이션 중에 **NmsRecipient** 테이블이 스키마 정의에서 다시 작성됩니다. Adobe Campaign 외부에 있는 이 테이블의 SQL 구조에 대한 모든 변경 사항은 손실됩니다.

확인할 요소 예:

* 열(또는 인덱스)을 **NmsRecipient** 그러나 스키마에 자세히 설명되어 있지 않으므로 저장되지 않습니다.
* 다음 **테이블스페이스** 속성은 기본적으로 해당 값을 되돌립니다(즉, 배포 마법사에 정의된 값).
* NmsRecipient 테이블에 참조 보기를 추가한 경우 마이그레이션하기 전에 삭제해야 합니다.

이 경고는 Oracle 사용자에게도 영향을 줍니다. 추가하신 경우 **usetimestamptz:1** 업그레이드 후 옵션( [시간대](../../migration/using/general-configurations.md#time-zones)). **날짜+시간** 필드가 다시 작성됩니다.

## 마이그레이션 전 {#before-the-migration}

Adobe Campaign v7로 마이그레이션할 때 다음 요소를 구성해야 합니다. 시작하기 전에 이러한 요소를 해결해야 합니다 **postupgrade**.

* 시간대

   v5.11 플랫폼에서 마이그레이션하는 동안 업그레이드 후 사용할 시간대를 지정해야 합니다.

   &quot;다중 시간대&quot; 모드를 사용하려면 다음을 참조하십시오 [시간대](../../migration/using/general-configurations.md#time-zones) 섹션을 참조하십시오.

   oracle을 데이터베이스로 사용하는 경우 Oracle 시간대 파일이 애플리케이션 서버와 데이터베이스 서버 간에 제대로 동기화되었는지 확인합니다. 자세한 내용은 [Oracle](../../migration/using/general-configurations.md#oracle) 섹션을 참조하십시오.

* 보안 영역

   보안상의 이유로 기본적으로 Adobe Campaign 플랫폼에 더 이상 액세스할 수 없습니다. 마이그레이션 전에 사용자 IP 주소를 수집해야 하는 보안 영역을 구성해야 합니다.

   자세한 내용은 [보안](../../migration/using/general-configurations.md#security) 섹션을 참조하십시오.

* 구문

   JavaScript의 특정 구문은 버전 5.11 및 6.02에서 허용될 수 있으며, 새 인터프리터를 사용하기 때문에 v7 버전에서 더 이상 허용되지 않습니다. 자세한 내용은 [JavaScript](../../migration/using/general-configurations.md#javascript) 섹션을 참조하십시오.

   마찬가지로 SQLData 기반 구문을 대체하기 위해 Adobe Campaign v7에 새로운 구문이 도입되었습니다. 이 구문과 함께 코드 요소를 사용하는 경우 이를 조정해야 합니다. 자세한 내용은 [SQLData](../../migration/using/general-configurations.md#sqldata) 섹션을 참조하십시오.

* 암호

   를 구성해야 합니다 **관리** 및 **내부** 암호. 자세한 내용은 [사용자 암호](../../migration/using/before-starting-migration.md#user-passwords) 섹션을 참조하십시오.

* 트리 구조

   v5.11 플랫폼에서 마이그레이션하는 경우 Adobe Campaign v6 규칙에 따라 트리 구조 폴더를 재구성해야 합니다. 자세한 내용은 [Adobe Campaign v7 트리 구조](../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure) 섹션을 참조하십시오.

* 상호 작용

   만약 **상호 작용** v7에 더 이상 존재하지 않는 6.02 스키마 참조를 모두 삭제해야 합니다. 자세한 내용은 [상호 작용](../../migration/using/general-configurations.md#interaction) 섹션을 참조하십시오.

## 마이그레이션 후 {#after-the-migration}

실행 후 **postupgrade**&#x200B;를 채울 때는 다음 요소와 해당 구성을 고려해야 합니다.

* 미러 페이지

   미러 페이지 개인화 블록이 v6.x에서 변경되었습니다. 이 새 버전은 이러한 페이지에 액세스할 때 보안을 개선합니다.

   메시지에서 v5 개인화 블록을 사용한 경우 미러 페이지 표시가 실패합니다. Adobe은 메시지에 미러 페이지를 삽입할 때 새로운 개인화 블록을 사용할 것을 권장합니다.

   그러나 임시 솔루션으로서(그리고 미러 페이지가 아직 라이브 상태일 때) 옵션을 변경하여 이 문제를 방지하려면 이전 개인화 블록으로 돌아갈 수 있습니다 **[!UICONTROL XtkAcceptOldPasswords]** 다음으로 설정 **[!UICONTROL 1]**. 이렇게 해도 새 v6.x 개인화 블록의 사용에는 영향을 주지 않습니다.

* 구문

   구문과 관련된 오류가 발생하면 업그레이드 후 일시적으로 를 활성화해야 합니다 **allowSQLInjection** 옵션 **serverConf.xml** 파일, 이렇게 하면 코드를 다시 작성할 수 있습니다. 코드가 적용되면 보안을 다시 활성화해야 합니다. 자세한 내용은 [SQLData](../../migration/using/general-configurations.md#sqldata) 섹션을 참조하십시오.

* 충돌

   마이그레이션은 업그레이드 후 수행되며 충돌이 보고서, 양식 또는 웹 애플리케이션에 표시될 수 있습니다. 콘솔에서 이러한 충돌을 해결할 수 있습니다.

   자세한 내용은 [충돌](../../migration/using/general-configurations.md#conflicts) 섹션을 참조하십시오.

* Tomcat

   설치 폴더를 사용자 지정한 경우 마이그레이션 후 올바르게 업데이트되었는지 확인합니다. 자세한 내용은 [Tomcat](../../migration/using/general-configurations.md#tomcat) 섹션을 참조하십시오.

* 보고서

   모든 기본 제공 보고서는 현재 v6.x 렌더링 엔진을 사용합니다. 보고서에 JavaScript 코드를 추가한 경우 일부 요소가 변경될 수 있습니다.

   자세한 내용은 [보고서](../../migration/using/general-configurations.md#reports) 섹션을 참조하십시오.

* 웹 애플리케이션

   업그레이드 후 식별된 웹 응용 프로그램에 연결하는 데 문제가 있으면 **allowUserPassword** 및 **sessionTokenOnly** 옵션 **serverConf.xml** 파일. 그런 다음 이 두 옵션을 비활성화해야 합니다. 자세한 내용은 [식별된 웹 애플리케이션](../../migration/using/general-configurations.md#identified-web-applications) 섹션을 참조하십시오.

   웹 응용 프로그램의 유형과 구성에 따라 해당 응용 프로그램이 제대로 작동하도록 추가 조작을 수행해야 합니다.

   자세한 내용은 [웹 애플리케이션](../../migration/using/general-configurations.md#web-applications) 섹션을 참조하십시오.

   v5.11 플랫폼에서 마이그레이션하는 경우 추가 구성을 수행해야 합니다. 자세한 내용은 [웹 애플리케이션](../../migration/using/specific-configurations-in-v5-11.md#web-applications) 섹션을 참조하십시오.

* 보안 영역.

   서버를 시작하기 전에 보안 영역을 구성해야 합니다. 자세한 내용은 [이 섹션](../../installation/using/security-zones.md) 그리고 [보안](../../migration/using/general-configurations.md#security) 섹션을 참조하십시오.

* 스키마

   Red Hat에서 특정 스키마를 편집할 때 오류가 발생할 수 있습니다. 자세한 내용은 [Red-Hat](../../migration/using/general-configurations.md#red-hat) 섹션을 참조하십시오.

* 워크플로우

   v5.11 플랫폼에서 마이그레이션하는 경우 워크플로우 런타임 디렉토리를 제어해야 합니다. 자세한 내용은 [워크플로우](../../migration/using/specific-configurations-in-v5-11.md#workflows) 섹션을 참조하십시오.

* 추적

   v5.11 플랫폼에서 마이그레이션하는 경우 추적 모드를 구성해야 합니다. 자세한 내용은 [추적](../../migration/using/specific-configurations-in-v5-11.md#tracking) 섹션을 참조하십시오.

* 홈페이지

   v6.02 플랫폼에서 마이그레이션하는 경우 이전 홈 페이지를 v6.02에서 유지하기 위해 추가 매개 변수를 정의할 수 있습니다. 자세한 내용은 [사용자 친화성: 홈 페이지 및 탐색](../../migration/using/specific-configurations-in-v6-02.md#user-friendliness--home-page-and-navigation) 섹션을 참조하십시오.

* 상호 작용

   만약 **상호 작용**, 마이그레이션 후에는 모든 매개 변수를 조정해야 합니다. 자세한 내용은 [상호 작용](../../migration/using/general-configurations.md#interaction) 섹션을 참조하십시오.
