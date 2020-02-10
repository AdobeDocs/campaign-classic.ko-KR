---
title: 마이그레이션 테스트
seo-title: 마이그레이션 테스트
description: 마이그레이션 테스트
seo-description: null
page-status-flag: never-activated
uuid: 3ee6a10b-dea2-41c6-9aef-ee3ac922b459
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migration-procedure
discoiquuid: 30e3082f-a367-4c3b-bff2-208ccf97acd4
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4f8a13e3788b99ff4214e00dec1f88fdef0cb964

---


# 마이그레이션 테스트{#testing-the-migration}

## 일반 절차 {#general-procedure}

구성에 따라 마이그레이션 테스트를 수행하는 방법에는 여러 가지가 있습니다.

마이그레이션 테스트를 수행하려면 테스트/개발 환경이 있어야 합니다. 개발 환경은 다음 라이선스의 대상이 됩니다.라이선스 계약서를 확인하거나 Adobe Campaign의 세일즈 서비스에 문의하십시오.

1. 진행 중인 모든 개발 작업을 중단하고 생산 환경에 전달할 수 있습니다.
1. 개발 환경 데이터베이스를 백업합니다.
1. 개발 인스턴스에서 모든 Adobe Campaign 프로세스를 중지합니다.
1. 프로덕션 환경 데이터베이스를 백업하고 개발 환경으로 복원합니다.
1. Adobe Campaign 서비스를 시작하기 전에 **백업을 시작할 때 실행 중인 개체의 데이터베이스를 지울 수** 있는 freezeInstance.js 자막 스크립트를 실행하십시오.

   ```
   nlserver javascript nms:freezeInstance.js -instance:<instance> -arg:<run|dry>
   ```

   >[!NOTE]
   >
   >명령은 기본적으로 **드라이** 모드에서 실행되며, 명령을 실행하지 않고 해당 명령으로 실행된 모든 요청을 나열합니다. 자궁 요청을 실행하려면 명령에서 **run** 을 사용합니다.

1. 백업을 복원하여 백업이 올바른지 확인하십시오. 데이터베이스, 테이블, 데이터 등에 액세스할 수 있는지 확인합니다.
1. 개발 환경에서 마이그레이션 절차를 테스트합니다.

   전체 절차는 Adobe Campaign 7 [로 마이그레이션하기 위한 사전 요구 사항 섹션에](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) 설명되어 있습니다.

1. 개발 환경의 마이그레이션이 성공하면 프로덕션 환경을 마이그레이션할 수 있습니다.

>[!CAUTION]
>
>데이터 구조의 변경 사항으로 인해 v5 플랫폼과 v7 플랫폼 간에는 데이터 패키지를 가져오거나 내보낼 수 없습니다.

>[!NOTE]
>
>Adobe Campaign 업데이트 명령(**업그레이드**&#x200B;후)을 사용하면 리소스를 동기화하고 스키마 및 데이터베이스를 업데이트할 수 있습니다. 이 작업은 응용 프로그램 서버에서만 한 번만 수행할 수 있습니다. 리소스를 동기화한 후 **업그레이드** 후 명령을 사용하면 동기화가 오류나 경고를 생성하는지 감지할 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

다양한 옵션을 사용하여 마이그레이션의 영향을 측정하고 잠재적인 문제를 식별할 수 있습니다. 다음 옵션을 실행합니다.

* config **명령에서** 다음을 수행합니다.

   ```
   nlserver.exe config <option> -instance:<instanceName>
   ```

* 또는 업그레이드 후:

   ```
   nlserver.exe config -postupgrade <option> -instance:<instanceName>
   ```

>[!NOTE]
>
>**다음`<instanceame>`**인스턴스를 사용해야 합니다.옵션을 선택합니다. 모든 인스턴스**&#x200B;옵션을 사용하는 것은&#x200B;**권장되지 않습니다.

### -showCustomEntities 및 -showDeletedEntities 옵션 {#showcustomentities-and--showdeletedentities-options}

* showCustomEntities **옵션은** 비표준 개체의 목록을 표시합니다.

   ```
   nlserver.exe config -showCustomEntities -instance:<instanceName>
   ```

   보낸 메시지의 예:

   ```
   xtk_migration:opsecurity2 xtk:entity
   ```

* showDeletedEntities **** 옵션은 데이터베이스나 파일 시스템에 없는 모든 표준 개체의 목록을 표시합니다. 누락된 각 개체에 대해 경로가 지정됩니다.

   ```
   nlserver.exe config -showDeletedEntities -instance:<instanceName>
   ```

   보낸 메시지의 예:

   ```
   Out of the box object 'nms:deliveryCustomizationMdl' belonging to the 'xtk:srcSchema' schema has not been found in the file system.
   ```

### 확인 프로세스 {#verification-process}

업그레이드 후 명령에 표준으로 통합된 이 프로세스를 통해 마이그레이션 실패를 초래할 수 있는 경고 및 오류를 표시할 수 있습니다. **오류가 표시되면 마이그레이션이 실행되지 않았습니다.** 이러한 경우 모든 오류를 수정한 다음 사후 업그레이드를 다시 시작합니다.

다음 명령을 사용하여 자체(마이그레이션 없이) 확인 프로세스를 시작할 수 있습니다.

```
nlserver.exe config -postupgrade -check -instance:<instanceName>
```

>[!NOTE]
>
>JST-310040 코드가 있는 모든 경고 및 오류를 무시하십시오.

다음 표현식은 검색됩니다(대/소문자 구분).

<table> 
 <thead> 
  <tr> 
   <th> 표현식<br /> </th> 
   <th> 오류 코드<br /> </th> 
   <th> 로그 유형<br /> </th> 
   <th> 댓글<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> .@<br /> </td> 
   <td> PU-0001<br /> </td> 
   <td> 경고<br /> </td> 
   <td> 이러한 유형의 구문은 더 이상 제공 개인화에서 지원되지 않습니다. JavaScript를 <a href="../../migration/using/general-configurations.md#javascript" target="_blank">참조하십시오</a>. 그렇지 않으면 값 유형이 올바른지 확인하십시오.<br /> </td> 
  </tr> 
  <tr> 
   <td> common.js<br /> </td> 
   <td> PU-0002<br /> </td> 
   <td> 경고<br /> </td> 
   <td> 이 라이브러리는 사용할 수 없습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> logon(<br /> </td> 
   <td> PU-0003<br /> </td> 
   <td> 경고<br /> </td> 
   <td> 이 연결 메서드는 더 이상 사용할 수 없습니다. 식별된 <a href="../../migration/using/general-configurations.md#identified-web-applications" target="_blank">웹 애플리케이션을</a>참조하십시오.<br /> </td> 
  </tr> 
  <tr> 
   <td> new SoapMethodCall(<br /> </td> 
   <td> PU-0004<br /> </td> 
   <td> 경고<br /> </td> 
   <td> 이 함수는 sessionTokenOnly <strong>모드에 있는 보안 영역에서 실행되는 JavaScript 코드에서 사용되는 경우에만 지원됩니다</strong> .<br /> </td> 
  </tr> 
  <tr> 
   <td> sql=<br /> </td> 
   <td> PU-0005<br /> </td> 
   <td> 오류<br /> </td> 
   <td> 이 유형의 오류로 인해 마이그레이션 오류가 발생합니다. SQLData를 <a href="../../migration/using/general-configurations.md#sqldata" target="_blank">참조하십시오</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> SQLDATA<br /> </td> 
   <td> PU-0006<br /> </td> 
   <td> 오류<br /> </td> 
   <td> 이 유형의 오류로 인해 마이그레이션 오류가 발생합니다. SQLData를 <a href="../../migration/using/general-configurations.md#sqldata" target="_blank">참조하십시오</a>. 개요 유형 웹 애플리케이션 오류 로그(v6.02에서 마이그레이션)가 표시되면 웹 <a href="../../migration/using/specific-configurations-in-v6-02.md#web-applications" target="_blank">애플리케이션을</a>참조하십시오.<br /> </td> 
  </tr> 
 </tbody> 
</table>

데이터베이스 및 스키마 일관성 확인도 수행됩니다.

### 복원 옵션 {#restoration-option}

이 옵션을 사용하면 즉시 사용 가능한 개체를 수정한 경우 복원할 수 있습니다. 복원된 각 개체에 대해 변경 내용의 백업이 선택한 폴더에 저장됩니다.

```
nlserver.exe config -postupgrade -restoreFactory:<backupfolder> -instance:<instanceName>
```

>[!NOTE]
>
>절대 폴더 경로를 사용하고 폴더 트리 구조를 유지하는 것이 좋습니다. 예:backupFolder\nms\srcSchema\billing.xml.

### 마이그레이션 재개 {#resuming-migration}

마이그레이션 실패 후 PostUpgrade를 다시 시작하면 중단된 위치에서 다시 시작됩니다.
