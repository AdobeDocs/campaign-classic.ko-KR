---
title: 복제 환경
seo-title: 복제 환경
description: 복제 환경
seo-description: null
page-status-flag: never-activated
uuid: b8fb8083-e3ec-4b1c-9449-73ac03508d89
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: data-processing
discoiquuid: 9f7118f4-aef0-469c-bbe1-b62bed674faa
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 779d9162b7296339a796512838612ede1186ddcc

---


# 복제 환경{#duplicating-environments}

## 소개 {#introduction}

### 개요 {#overview}

>[!CAUTION]
>
>서버 및 데이터베이스(호스팅 환경)에 대한 액세스 권한이 없는 경우 아래 설명된 절차를 수행할 수 없습니다. Adobe에 문의하십시오.

Adobe Campaign을 사용하려면 하나 이상의 환경을 설치하고 구성해야 합니다.개발, 테스트, 프리 프로덕션, 프로덕션 등

각 환경에는 Adobe Campaign 인스턴스가 포함되어 있으며 각 Adobe Campaign 인스턴스는 하나 이상의 데이터베이스에 연결됩니다. 응용 프로그램 서버는 하나 이상의 프로세스를 실행할 수 있습니다.거의 모든 애플리케이션이 인스턴스 데이터베이스에 직접 액세스할 수 있습니다.

이 섹션에서는 소스 환경을 대상 환경으로 복원하여 두 개의 동일한 작업 환경을 만드는 등 Adobe Campaign 환경을 복제하는 데 적용할 프로세스에 대해 자세히 설명합니다.

이렇게 하려면 다음 단계를 적용합니다.

1. 소스 환경의 모든 인스턴스에 데이터베이스 복사본을 만듭니다.
1. 대상 환경의 모든 인스턴스에서 이러한 복사본을 복원합니다.
1. 시작하기 전에 **대상 환경에서 nms:freezeInstance.js** 자막 스크립트를 실행합니다.

   이 프로세스는 서버와 해당 구성에 영향을 주지 않습니다.

   >[!NOTE]
   >
   >Adobe Campaign의 컨텍스트에서 **자국은** 외부와의 모든 프로세스를 중지할 수 있는 작업을 결합합니다.로그, 추적, 게재, 캠페인 워크플로우 등\
   >이 단계는 여러 번(명목상 환경에서 한 번, 중복된 환경에서 한 번) 메시지를 전달하는 것을 방지하기 위해 필요합니다.

   >[!CAUTION]
   >
   >하나의 환경에 여러 인스턴스가 포함될 수 있습니다. 각 Adobe Campaign 인스턴스에는 라이선스 계약이 적용됩니다. 라이선스 계약서를 확인하여 몇 개의 환경을 보유할 수 있는지 확인하십시오.\
   >아래 절차를 통해 설치한 환경 및 인스턴스 수에 영향을 주지 않고 환경을 전송할 수 있습니다.

### 시작하기 전에 {#before-you-start}

>[!CAUTION]
>
>전송 프로세스를 시작하기 전에 소스 및 대상 환경의 모든 인스턴스에 대해 데이터베이스의 전체 백업을 실행하는 것이 좋습니다. 이 방법으로 문제가 발생하면 백업을 복원하고 초기 구성으로 돌아갈 수 있습니다.

이 프로세스가 작동하려면 소스 및 대상 환경에 동일한 수의 인스턴스, 동일한 목적(마케팅 인스턴스, 전달 인스턴스) 및 유사한 구성이 있어야 합니다. 기술 구성은 소프트웨어 사전 요구 사항을 준수해야 합니다. 두 환경 모두에 동일한 구성 요소를 설치해야 합니다.

## 구현 {#implementation}

### 전송 절차 {#transfer-procedure}

이 섹션에서는 사례 연구를 통해 소스 환경을 타겟 환경으로 전송하는 데 필요한 단계를 이해하는 데 도움이 됩니다.여기서는 생산 환경(**prod** 인스턴스)을 개발 환경(**개발 인스턴스** )으로 복원하여 &#39;live&#39; 플랫폼과 가장 가까운 컨텍스트에서 작동하도록 하는 것이 목표입니다.

다음 단계는 매우 신중하게 수행해야 합니다.소스 환경 데이터베이스를 복사할 때 일부 프로세스가 계속 진행 중일 수 있습니다. 메시지 전송을 두 번 방지하고 데이터 일관성을 유지합니다.

>[!CAUTION]
>
>* 다음 절차는 PostgreSQL 언어로 유효합니다. SQL 언어가 다른 경우(예: Oracle) SQL 쿼리를 수정해야 합니다.
>* 아래 명령은 **prod** 인스턴스 및 PostgreSQL 아래의 **개발** 인스턴스 컨텍스트 내에 적용됩니다.
>



### 1단계 - 소스 환경(prod) 데이터의 백업 만들기 {#step-1---make-a-backup-of-the-source-environment--prod--data}

데이터베이스 복사

먼저 모든 소스 환경 데이터베이스를 복사합니다. 작업은 데이터베이스 엔진에 따라 다르며 데이터베이스 관리자의 책임입니다.

PostgreSQL 아래에서 명령은 다음과 같습니다.

```
pg_dump mydatabase > mydatabase.sql
```

### 2단계 - 대상 환경 구성 내보내기(개발) {#step-2---export-the-target-environment-configuration--dev-}

대부분의 구성 요소는 각 환경에 대해 다릅니다.외부 계정(mid-sourcing, 라우팅 등), 기술 옵션(플랫폼 이름, 데이터베이스 ID, 이메일 주소 및 기본 URL 등)

대상 데이터베이스에 소스 데이터베이스를 저장하기 전에 대상 환경(개발) 구성을 내보내야 합니다. 이렇게 하려면 다음 두 표의 컨텐츠를 내보냅니다.xtkoption **및** nmsextaccount ****.

이 내보내기를 사용하면 개발 구성을 유지하고 개발 데이터(워크플로우, 템플릿, 웹 애플리케이션, 수신자 등)만 새로 고칠 수 있습니다.

이렇게 하려면 다음 두 요소에 대해 패키지 내보내기를 수행합니다.

* 다음 내부 **이름을 가진 레코드 없이 xtk:option** 테이블을 &#39;options_dev.xml&#39; 파일로 내보냅니다.&#39;WdbcTimeZone&#39;, &#39;NmsServer_LastPostUpgrade&#39; 및 &#39;NmsBroadcast_RegexRules&#39;.
* &#39;extaccount_dev.xml&#39; 파일에서 ID가 0(@id &lt;> 0)이 아닌 모든 **레코드에** 대해 nms:extAccount 테이블을 내보냅니다.

내보낸 옵션/계정 수가 각 파일에서 내보낼 줄 수와 같은지 확인합니다.

>[!NOTE]
>
>패키지 내보내기에서 내보낼 줄 수는 1,000줄입니다. 옵션 또는 외부 계정 수가 1,000개를 초과하는 경우, 몇 개의 내보내기를 수행해야 합니다.
> 
>For more information, refer to [this section](../../platform/using/working-with-data-packages.md#exporting-packages).

### 3단계 - 타겟 환경 중지(개발) {#step-3---stop-the-target-environment--dev-}

모든 대상 환경 서버에서 Adobe Campaign 프로세스를 중지해야 합니다. 이 작업은 운영 체제에 따라 다릅니다.

모든 프로세스를 중지하거나 데이터베이스에 쓰는 프로세스만 중지할 수 있습니다.

모든 프로세스를 중지하려면 다음 명령을 사용합니다.

* Windows:

   ```
   net stop nlserver6
   ```

* Linux:

   ```
   /etc/init.d/nlserver6 stop
   ```

다음 명령을 사용하여 모든 프로세스가 중지되었는지 확인합니다.

```
nlserver pdump
```

>[!NOTE]
>
>Windows에서 **웹** 프로세스는 다른 작업에 영향을 주지 않고 여전히 활성 상태일 수 있습니다.

실행 중인 시스템 프로세스가 없는지 확인할 수도 있습니다.

이렇게 하려면 다음 프로세스를 사용하십시오.

* Windows:작업 **관리자를** 열고 **nlserver.exe** 프로세스가 없는지 확인합니다.
* Linux:ps **aux 실행| grep nlserver** 명령 및 nlserver **프로세스가 없는지** 확인합니다.

### 4단계 - 대상 환경에서 데이터베이스 복원(개발) {#step-4---restore-the-databases-in-the-target-environment--dev-}

대상 환경에서 소스 데이터베이스를 복원하려면 다음 명령을 사용합니다.

```
psql mydatabase < mydatabase.sql
```

### 5단계 - 대상 환경 재구성(개발) {#step-5---cauterize-the-target-environment--dev-}

잘못된 기능을 방지하려면 대상 환경이 활성화될 때 배달 전송 및 워크플로우 실행에 연결된 프로세스가 자동으로 실행되지 않아야 합니다.

이렇게 하려면 다음 명령을 실행합니다.

```
nlserver javascript nms:freezeInstance.js -instance:<dev> -arg:run
```

### 6단계 - 확인 {#step-6---check-cauterization}

1. ID가 0으로 설정된 유일한 배달부인지 확인하십시오.

   ```
   SELECT * FROM neolane.nmsdeliverypart;
   ```

1. 배달 상태 업데이트가 올바른지 확인하십시오.

   ```
   SELECT iState, count(*) FROM neolane.nmsdelivery GROUP BY iState;
   ```

1. 워크플로우 상태 업데이트가 올바른지 확인합니다.

   ```
   SELECT iState, count(*) FROM neolane.xtkworkflow GROUP BY iState;
   SELECT iStatus, count(*) FROM neolane.xtkworkflow GROUP BY iStatus;
   ```

### 7단계 - 대상 환경 다시 시작 웹 프로세스(개발) {#step-7---restart-the-target-environment-web-process--dev-}

타겟 환경에서 모든 서버에 대해 Adobe Campaign 프로세스를 다시 시작합니다.

>[!NOTE]
>
>개발 **환경에서 Adobe Campaign을** 다시 시작하기 전에 추가 안전 절차를 적용할 수 있습니다.웹 **모듈만** 시작합니다.
>  
>이렇게 하려면 인스턴스의 구성 파일(**config-dev.xml**)을 편집한 다음 각 모듈에 대한 autoStart=&quot;true&quot; 옵션 앞에 &quot;_&quot; 문자를 추가합니다(mta, stat 등).

다음 명령을 실행하여 웹 프로세스를 시작합니다.

```
nlserver start web
```

다음 명령을 사용하여 웹 프로세스만 시작되었는지 확인합니다.

```
nlserver pdump
```

클라이언트 콘솔 기능에 대한 액세스를 확인합니다.

### 8단계 - 옵션 및 외부 계정을 대상 환경으로 가져오기(개발) {#step-8---import-options-and-external-accounts-into-the-target-environment--dev-}

>[!CAUTION]
>
>이 단계에서는 웹 프로세스만 시작해야 합니다. 이 경우 계속하기 전에 실행 중인 다른 프로세스를 중지하십시오.

가져오기 전에 여러 줄의 파일 값을 확인합니다(예:옵션 테이블 및 외부 계정 테이블에 대한 배달 또는 중간 소싱 계정에 대한 &#39;NmsTracking_Pointer&#39;

대상 환경 데이터베이스(개발)에서 구성을 가져오려면 다음을 수행하십시오.

1. 데이터베이스의 관리 콘솔을 열고 ID가 0(@id &lt;> 0)이 아닌 외부 계정(테이블 nms:extAccount)을 제거합니다.
1. Adobe Campaign 콘솔에서 이전에 가져오기 패키지 기능을 통해 생성된 options_dev.xml 패키지를 가져옵니다.

   옵션이 **[!UICONTROL Administration > Platform > Options]** 노드에서 실제로 업데이트되었는지 확인합니다.

1. Adobe Campaign 콘솔에서 이전에 패키지 가져오기 기능을 통해 만든 extaccount_dev.xml을 가져옵니다

   외부 데이터베이스가 실제로 에서 가져왔는지 **[!UICONTROL Administration > Platform > External accounts]** 확인합니다.

### 9단계 - 모든 프로세스를 다시 시작하고 사용자 변경(개발) {#step-9---restart-all-processes-and-change-users--dev-}

Adobe Campaign 프로세스를 시작하려면 다음 명령을 사용합니다.

* Windows:

   ```
   net start nlserver6
   ```

* Linux:

   ```
   /etc/init.d/nlserver6 start
   ```

다음 명령을 사용하여 프로세스가 시작되었는지 확인합니다.

```
nlserver pdump
```

사용자를 변경하여 개발 플랫폼에 이미 존재하는 사용자를 찾습니다.
