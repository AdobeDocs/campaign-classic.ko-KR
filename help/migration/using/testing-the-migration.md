---
product: campaign
title: 마이그레이션 테스트
description: 마이그레이션 테스트
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: 228ee9e4-46a0-4d82-b8ba-b019bc0e7cac
source-git-commit: 59a2bc62b4c03ef0702cb57bd9dc808e7d0b444b
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 0%

---

# 마이그레이션 테스트{#testing-the-migration}

![](../../assets/v7-only.svg)

## 일반 절차 {#general-procedure}

구성에 따라 마이그레이션 테스트를 수행하는 방법에는 몇 가지가 있습니다.

마이그레이션 테스트를 수행하려면 테스트/개발 환경이 있어야 합니다. Adobe Campaign 환경에는 라이센스가 적용됩니다. 라이선스 계약을 확인하거나 Adobe 담당자에게 문의하십시오.

1. 진행 중인 모든 개발 작업을 중지하고 프로덕션 환경으로 이동하십시오.
1. 개발 환경 데이터베이스를 백업하십시오.
1. 개발 인스턴스의 모든 Adobe Campaign 프로세스를 중지합니다.
1. 운영 환경 데이터베이스를 백업하고 개발 환경으로 복원합니다.
1. Adobe Campaign 서비스를 시작하기 전에 **freezeInstance.js** 백업을 시작할 때 실행 중인 개체의 데이터베이스를 지울 수 있는 자작화 스크립트

   ```
   nlserver javascript nms:freezeInstance.js -instance:<instance> -arg:<run|dry>
   ```

   >[!NOTE]
   >
   >명령은 기본적으로 **건조하** 모드 및 는 명령을 실행하지 않고 해당 명령에 의해 실행된 모든 요청을 나열합니다. 소작화 요청을 실행하려면 **run** 를 입력합니다.

1. 백업을 복원하여 백업이 올바른지 확인합니다. 데이터베이스, 테이블, 데이터 등에 액세스할 수 있는지 확인합니다.
1. 개발 환경에서 마이그레이션 절차를 테스트합니다.
1. 개발 환경의 마이그레이션이 성공하면 프로덕션 환경을 마이그레이션할 수 있습니다.

>[!CAUTION]
>
>데이터 구조가 변경되므로 v5 플랫폼과 v7 플랫폼 간에 데이터 패키지를 가져오고 내보낼 수 없습니다.


## 마이그레이션 도구 {#migration-tools}

다양한 옵션을 사용하면 마이그레이션의 영향을 측정하고 잠재적인 문제를 식별할 수 있습니다. 다음 옵션을 실행할 수 있습니다.

* 에서 **config** 명령:

   ```
   nlserver.exe config <option> -instance:<instanceName>
   ```

* 또는 업그레이드 후:

   ```
   nlserver.exe config -postupgrade <option> -instance:<instanceName>
   ```

>[!NOTE]
>
>* 를 사용해야 합니다 **-instance:`<instanceame>`** 선택 사항입니다. 를 사용하지 않는 것이 좋습니다 **-allinstances** 선택 사항입니다.
>* Adobe Campaign 업데이트 명령(**postupgrade**)을 사용하면 리소스를 동기화하고 스키마와 데이터베이스를 업데이트할 수 있습니다. 이 작업은 응용 프로그램 서버에서 한 번만 수행할 수 있습니다. 리소스를 동기화한 후 **postupgrade** 명령을 사용하면 동기화가 오류나 경고를 생성하는지 여부를 감지할 수 있습니다.


### 비표준 또는 누락된 개체

* 다음 **-showCustomEntities** 옵션은 모든 비표준 객체 목록을 표시합니다.

   ```
   nlserver.exe config -showCustomEntities -instance:<instanceName>
   ```

   보낸 메시지의 예:

   ```
   xtk_migration:opsecurity2 xtk:entity
   ```

* 다음 **-showDeletedEntities** 옵션에는 데이터베이스 또는 파일 시스템에서 누락된 모든 표준 객체의 목록이 표시됩니다. 누락된 각 객체에 대해 경로가 지정됩니다.

   ```
   nlserver.exe config -showDeletedEntities -instance:<instanceName>
   ```

   보낸 메시지의 예:

   ```
   Out of the box object 'nms:deliveryCustomizationMdl' belonging to the 'xtk:srcSchema' schema has not been found in the file system.
   ```

### 확인 프로세스 {#verification-process}

업그레이드 후 명령에 표준으로 통합되는 이 프로세스를 사용하면 마이그레이션이 실패할 수 있는 경고 및 오류를 표시할 수 있습니다. **오류가 표시되면 마이그레이션이 실행되지 않은 것입니다.** 이 경우 모든 오류를 수정한 다음 업그레이드 후 다시 시작합니다.

다음 명령을 사용하여 자체(마이그레이션 없이) 확인 프로세스를 시작할 수 있습니다.

```
nlserver.exe config -postupgrade -check -instance:<instanceName>
```

>[!NOTE]
>
>JST-310040 코드에서 모든 경고 및 오류를 무시할 수 있습니다.

다음 식에 대해 검색할 수 있습니다(대/소문자 구분).

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
   <td> 이 유형의 구문은 더 이상 게재 개인화에서 지원되지 않습니다. 을(를) 참조하십시오. <a href="../../migration/using/general-configurations.md#javascript" target="_blank">JavaScript</a>. 그렇지 않으면 값 유형이 올바른지 확인합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> common.js<br /> </td> 
   <td> PU-0002<br /> </td> 
   <td> 경고<br /> </td> 
   <td> 이 라이브러리는 사용하지 않아야 합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> logon(<br /> </td> 
   <td> PU-0003<br /> </td> 
   <td> 경고<br /> </td> 
   <td> 이 연결 메서드는 더 이상 사용하지 않아야 합니다. 을(를) 참조하십시오. <a href="../../migration/using/general-configurations.md#identified-web-applications" target="_blank">식별된 웹 애플리케이션</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> 새 SoapMethodCall(<br /> </td> 
   <td> PU-0004<br /> </td> 
   <td> 경고<br /> </td> 
   <td> 이 함수는 의 보안 영역에서 실행된 JavaScript 코드에서 사용되는 경우에만 지원됩니다 <strong>sessionTokenOnly</strong> 모드.<br /> </td> 
  </tr> 
  <tr> 
   <td> sql=<br /> </td> 
   <td> PU-0005<br /> </td> 
   <td> 오류<br /> </td> 
   <td> 이러한 유형의 오류로 인해 마이그레이션 오류가 발생합니다. 을(를) 참조하십시오. <a href="../../migration/using/general-configurations.md#sqldata" target="_blank">SQLData</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> SQLDATA<br /> </td> 
   <td> PU-0006<br /> </td> 
   <td> 오류<br /> </td> 
   <td> 이러한 유형의 오류로 인해 마이그레이션 오류가 발생합니다. 을(를) 참조하십시오. <a href="../../migration/using/general-configurations.md#sqldata" target="_blank">SQLData</a>. 개요 유형 웹 애플리케이션 오류 로그(v6.02에서 마이그레이션)가 나타나면 다음을 참조하십시오 <a href="../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11" target="_blank">Campaign 구성</a>.<br /> </td> 
  </tr>
  <tr> 
   <td> crmDeploymentType="onpremise"<br /> </td> 
   <td> PU-0007<br /> </td> 
   <td> 오류<br /> </td> 
   <td> 이 유형의 배포는 더 이상 지원되지 않습니다. 이제 Office 365 및 온-프레미스 Microsoft CRM 커넥터 배포 유형이 더 이상 사용되지 않습니다. 
   </br>외부 계정에서 이러한 사용되지 않는 배포 유형 중 하나를 사용하는 경우 이 외부 계정을 삭제한 다음 <b>postupgrade</b> 명령. 
   </br>웹 API 배포로 변경하려면 <a href="../../platform/using/crm-ms-dynamics.md#configure-acc-for-microsoft" target="_blank">웹 애플리케이션</a>.<br /> </td>
  </tr> 
  <tr> 
   <td> CRM v1(mscrmWorkflow/sfdcWorkflow)<br /> </td> 
   <td> PU-0008<br /> </td> 
   <td> 오류<br /> </td> 
   <td> Microsoft CRM, Salesforce, Oracle CRM On Demand 작업 활동을 더 이상 사용할 수 없습니다. Adobe Campaign과 CRM 시스템 간의 데이터 동기화를 구성하려면 다음을 사용해야 합니다 <a href="../../workflow/using/crm-connector.md" target="_blank">CRM 커넥터</a> 타겟팅 활동.<br /> </td>
  </tr> 
 </tbody> 
</table>

데이터베이스 및 스키마 일관성 확인도 수행됩니다.

### 복원 옵션 {#restoration-option}

이 옵션을 사용하면 기본 제공 개체를 수정한 경우 복원할 수 있습니다. 복원된 각 객체에 대해 변경 사항 백업이 선택한 폴더에 저장됩니다.

```
nlserver.exe config -postupgrade -restoreFactory:<backupfolder> -instance:<instanceName>
```

>[!NOTE]
>
>절대 폴더 경로를 사용하고 폴더 트리 구조를 유지하는 것이 좋습니다. 예: backupFolder\nms\srcSchema\billing.xml

### 마이그레이션 다시 시작 {#resuming-migration}

마이그레이션 실패 후 업그레이드 후 다시 시작하면 중지된 동일한 위치에서 다시 시작됩니다.
