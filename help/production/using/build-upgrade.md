---
solution: Campaign Classic
product: campaign
title: 빌드 업그레이드 시작하기
description: 새 빌드로 업그레이드하기 위한 주요 단계를 알아봅니다.
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
translation-type: tm+mt
source-git-commit: 5639f08ad709597d5f5c9e6bbd6932cffcbde40f
workflow-type: tm+mt
source-wordcount: '2368'
ht-degree: 0%

---


# 빌드 업그레이드 수행{#performing-a-build-upgrade}

이 섹션에서는 업그레이드 프로세스에 대한 자세한 설명 및 충돌 식별 및 해결 절차를 제공합니다.

빌드 업그레이드는 신중하게 수행해야 하며 그 영향을 사전에 완전히 고려해야 하며 절차는 높은 수준의 징계로 완료되어야 합니다. 성공적으로 업그레이드하려면 아래 설명된 단계를 전문가 사용자에게만 수행해야 합니다. 또한 업그레이드를 시작하기 전에 [Adobe 고객 지원 센터](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)에 문의하는 것이 좋습니다.

다음 전제 조건이 필요합니다.

* 캠페인 아키텍처 이해
* 시스템 및 서버측 지식
* 관리 권한

다음 섹션에서 자세한 내용을 확인할 수 있습니다.[Adobe Campaign](../../production/using/upgrading.md) 업데이트, [새 버전](../../migration/using/about-migration.md)으로 마이그레이션

호스팅된 인스턴스와 하이브리드 인스턴스의 경우 Adobe 기술 작업 팀에 대한 빌드 업그레이드를 요청해야 합니다. 이 페이지에 대한 자세한 내용은 이 페이지의 하단에 있는 FAQ 섹션을 참조하십시오. 또한 [업그레이드 FAQ](../../platform/using/faq-build-upgrade.md)를 참조하십시오.

## 업그레이드 준비

![](assets/do-not-localize/icon_planification.png)

빌드 업그레이드를 시작하기 전에 아래 설명된 대로 전체 준비를 수행해야 합니다.
시스템을 업그레이드할 준비가 되면 빌드 업그레이드는 **최소** 2시간이 소요됩니다.

빌드 업그레이드 프로세스에는 다음 리소스가 필요합니다.

* adobe 설계자 - 데이터베이스 구조(즉시 사용 가능한 스키마 및 추가된 추가 스키마, 캠페인 설계 및 특정 순서로 시작하고 테스트해야 하는 중요한 경로 기능)를 파악합니다.
* 프로젝트 관리자 - 빌드 업그레이드에 많은 다른 인스턴스(프로덕션, 스테이징, 테스트)와 기타 타사 서버 및 응용 프로그램(데이터베이스, SFTP 사이트, 메시징 서비스 공급자)이 포함되어 있는 경우 프로젝트 관리자가 모든 테스트를 조정하는 것이 가장 좋은 방법입니다.
* adobe campaign 관리자 - 관리자가 다음을 포함하나 이에 제한되지 않는 서버의 구성을 알고 있습니다.보안, 폴더 레이아웃, 보고 및 가져오기\내보내기 요구 사항. 관리자 없이는 빌드 업그레이드를 수행하지 마십시오.
* adobe campaign 운영자(마케팅 사용자) - 성공적인 업그레이드는 일상적인 작업을 성공적으로 수행할 수 있는 사용자의 능력에 의존합니다. 이러한 이유로, 항상 업그레이드된 서버를 테스트하는 데 일일 연산자 중 하나 이상을 포함합니다.

### 계획

빌드 업그레이드를 계획하는 방법은 다음과 같습니다.

1. 업그레이드를 위해 최소 2시간 예약합니다.
1. Adobe 및 고객 직원을 위한 연락처 세부 정보를 배포합니다.
1. 호스팅 인스턴스의 경우:Adobe과 고객 담당자는 업그레이드 시간과 적용 대상자를 조정할 수 있습니다.
1. 온-프레미스 인스턴스의 경우:고객 직원이 전체 프로세스를 관리합니다. 맞춤형 워크플로우 테스트와 전달 로직 테스트가 필요한 경우 컨설팅 서비스를 제공해야 합니다.
1. 업그레이드할 Adobe Campaign 버전을 확인하고 확인합니다. [Adobe Campaign Classic 릴리스 노트](../../rn/using/rn-overview.md)를 참조하십시오.
1. 업그레이드 실행 파일의 소유 여부를 확인합니다.

### 핵심 사용자

빌드 업그레이드 프로세스에는 다음 사람이 참여해야 합니다.

* Adobe 설계자:호스팅 또는 하이브리드 아키텍처의 경우 설계자는 Adobe Campaign Client Care와 협력해야 합니다.

* 프로젝트 관리자:
   * 온-프레미스 설치의 경우:고객의 내부 프로젝트 리더는 업그레이드를 주도하고 라이프사이클 테스트를 관리합니다.

   * 호스팅된 설치의 경우:호스팅 팀은 Adobe Campaign Client Care 팀과 고객 간의 협력을 통해 모든 인스턴스에 대한 업그레이드 타임라인을 조정할 것입니다.

* Adobe Campaign 관리자:
   * 온-프레미스 설치의 경우:관리자가 업그레이드를 수행합니다.

   * 호스팅 설치:호스팅 팀이 업그레이드를 수행합니다.

* Adobe Campaign 연산자\marketing 사용자:연산자는 개발, 테스트 및 프로덕션 인스턴스에 대해 테스트를 실행합니다.

### 빌드 업그레이드 준비

빌드 업그레이드를 시작하기 전에 온-프레미스 고객은 다음 준비를 수행해야 합니다.

1. 업그레이드 전에 개발 작업을 내보내고 패키지로 내보낼 수 있는지 확인합니다.

1. 소스 및 대상 환경의 모든 인스턴스에 대해 데이터베이스의 전체 백업을 수행합니다.

1. [서버 구성 파일](../../installation/using/the-server-configuration-file.md)의 최신 버전을 가져옵니다.

1. 최신 빌드를 다운로드합니다. [다운로드 센터에 대한 자세한 내용을 살펴보십시오](https://docs.adobe.com/content/help/en/experience-cloud/software-distribution/home.html).

빌드 업그레이드를 시작하기 전에 [유용한 명령줄](../../installation/using/command-lines.md)을 모두 알아야 합니다.

* **nlserver pdump**:실행 중인 프로세스 목록
* **nlserver pdump -who**:활성 클라이언트 세션 목록
* **nlserver monitor -missing**:누락된 속성 목록
* **nlserver 시작 process@instanceName**:프로세스 시작
* **nlserver 중지 process@instanceName**:프로세스를 중지합니다.
* **nlserver 다시 시작 process@instanceName**:프로세스 다시 시작
* **nlserver 종료**:모든 캠페인 프로세스를 중지합니다.
* **nlserver watchdog -svc**:감시기 시작(UNIX만 해당)

## 업그레이드 수행

![](assets/do-not-localize/icon_process.png)

아래 절차는 **온-프레미스** 고객만 수행합니다. 호스팅 고객의 경우 호스팅 팀이 관리합니다. Adobe Campaign을 새 빌드로 업데이트하려면 아래에 자세한 절차를 설명합니다.

### 환경 복제

소스 환경을 대상 환경으로 복원하여 두 개의 동일한 작업 환경을 만들기 위해 Adobe Campaign 환경을 복제하는 방법을 설명합니다.

이렇게 하려면 아래 단계를 수행합니다:

1. 소스 환경의 모든 인스턴스에 데이터베이스의 복사본을 만듭니다.

1. 대상 환경의 모든 인스턴스에서 이러한 복사본을 복원합니다.

1. 시작하기 전에 대상 환경에서 **nms:freezeInstance.js** 자막 스크립트를 실행합니다. 이렇게 하면 외부 상호 작용하는 모든 프로세스가 중지됩니다.로그, 추적, 배달, 캠페인 워크플로우 등

   ```
   nlserverjavacsriptnms:freezeInstance.js–instance:<dev> -arg:run
   ```

1. 다음과 같이 확인한다.

   * 배달 부품만 **0**&#x200B;으로 설정된 ID인지 확인하십시오.

      ```
      SELECT * FROM neolane.nmsdeliverypart;
      ```

   * 배달 상태 업데이트가 올바른지 확인합니다.

      ```
      SELECT iSate, count(*) FROM neolane.nmsdeliveryGroup By iProd;
      ```

   * 워크플로 상태 업데이트가 올바른지 확인:

      ```
      SELECT iState, count (*) FROM neolane.xtkworkflowGROUP BY iState;
      SELECT iStatus, count (*) FROM neolane.xtkworkflowGROUP BY iStatus;
      ```

### 서비스 종료

모든 파일을 새 버전으로 대체하려면 nlserverservice의 모든 인스턴스가 종료되어야 합니다.

1. 다음 서비스를 종료합니다.

   * 웹 서비스(IIS):**iesreset /stop**
   * Adobe Campaign 서비스:**net stop nlserver6**

   >[!NOTE]
   >
   >IIS에서 사용하는 nlsrvmod.dll 파일을 새 버전으로 바꿀 수 있도록 리디렉션 서버(webmdl)가 중지되었는지 확인하십시오.

1. **nlserver pdump** 명령을 실행하여 활성 작업이 없는지 확인합니다. 작업이 없는 경우 다음과 같이 출력합니다.

   ```
   C:\<installation path>\bin>nlserverpdump HH:MM:SS > Application Server for Adobe Campaign version x.x (build xxx) dated xx/xx/xxxx No tasks
   ```

1. 모든 프로세스가 중지되었는지 확인하려면 Windows 작업 관리자를 확인하십시오.

### Adobe Campaign Server 응용 프로그램 업그레이드

1. **Setup.exe** 파일을 실행합니다. 이 파일을 다운로드해야 하는 경우 [다운로드 센터](https://docs.adobe.com/content/help/en/experience-cloud/software-distribution/home.html)에 액세스하십시오.

1. 설치 모드를 선택합니다.**업데이트** 또는 **복구**.

1. **다음**&#x200B;을 클릭합니다.

1. **완료**&#x200B;를 클릭합니다.설치 프로그램은 새 파일을 복사합니다.

1. 작업이 완료되면 **완료**&#x200B;를 클릭합니다.

### 리소스 동기화

1. 명령줄을 엽니다.

1. **nlserver config -postupgrade -allinstances**&#x200B;을 실행하여 다음을 수행합니다.

   * 리소스 동기화
   * 스키마 업데이트
   * 데이터베이스 업데이트

   >[!NOTE]
   >
   >이 작업은 서버 웹 응용 프로그램 서버에서만 한 번만 수행해야 합니다.

   하나의 데이터베이스만 동기화하려면 다음 명령을 실행합니다.

   ```
   nlserver config -postupgrade -instance: <instance_name>
   ```

1. 동기화에서 오류 또는 경고가 생성되었는지 확인합니다.

### 서비스를 다시 시작합니다.

다음 서비스를 다시 시작해야 합니다.

* 웹 서비스(IIS):**isreset /start**
* Adobe Campaign 서비스:**net start nlserver6**

### 클라이언트 콘솔 업데이트

클라이언트 콘솔은 서버 인스턴스와 동일한 빌드에 있어야 합니다.

Adobe Campaign 응용 프로그램 서버가 설치된 컴퓨터(nlserverweb)에서 파일을 다운로드하고 복사합니다.

```
Setup-client-7.xxxx.exe in [path of the application]\datakit\nl\en\jsp
```

다음 번에 클라이언트 콘솔이 연결되면 사용자에게 새 업데이트가 사용 가능한지 알려 주고 다운로드 및 설치 가능성을 제공합니다.

### 특정 추가 작업

일부 구성에서는 새 빌드로 업데이트하기 위해 특정 추가 작업이 필요합니다.

#### 트랜잭션 메시지

캠페인 인스턴스에서 트랜잭션 메시지(메시지 센터)가 활성화된 경우 업그레이드하려면 다음과 같은 추가 단계를 수행해야 합니다.

1. 메시지 센터 프로덕션 서버를 선택한 버전으로 업데이트합니다.
1. 업그레이드 후 스크립트를 실행합니다.
1. 테스트를 실행하고 Message Center 프로덕션 인스턴스를 통해 이메일이 성공적으로 수신되었는지 확인합니다.
1. 클라이언트 업그레이드 및 캐시 지우기
1. 패키지 내보내기:
   * 클라이언트 패키지 내보내기 도구를 사용하여 패키지 내보내기
   * 스키마 패키지 가져오기
   * 클라이언트 연결 끊기 및 다시 연결
   * 데이터베이스 업데이트
   * 연결 끊기 및 다시 연결
   * 관리 패키지 가져오기
   * 콘텐츠 패키지 가져오기
   * 콘텐츠 관리 패키지 가져오기
   * 연결 끊기 및 다시 연결
   * 워크플로우의 상태를 신속하게 확인

1. 메시지 센터 템플릿을 게시하여 서버와 메시지 센터 인스턴스 간 인터페이스가 제대로 작동하는지 확인합니다.
1. 테스트를 실행하여 Message Center 프로덕션 인스턴스를 통해 이메일이 성공적으로 수신되었는지 확인합니다.
1. 프로덕션에서 워크플로우 테스트를 실행하여 배달을 수신합니다.

#### 중간 소싱

중간 소싱 환경 컨텍스트에서 업그레이드하려면 다음과 같은 추가 단계를 수행해야 합니다.

1. Mid-Sourcing 서버 업그레이드를 조정하려면 [Adobe 고객 지원 센터](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)에 문의하십시오.
1. 테스트 링크를 실행하여 버전이 업데이트되었는지 확인합니다. 예제:

   ```
   http://[InsertServerURL]/r/test
   ```

>[!NOTE]
>
>Mid-Sourcing 서버는 마케팅 서버에 대해 항상 동일한 버전(또는 보다 최신)을 실행해야 합니다.


## 충돌 시

### 충돌 식별

동기화 결과를 확인해야 합니다. 이 절차는 온-프레미스 고객만 수행합니다. 호스팅 고객의 경우 호스팅 팀이 관리합니다. 동기화 결과를 보는 방법에는 두 가지가 있습니다.

명령줄 인터페이스에서 3단계 V형 수장 &#39;>>>&#39;에 의해 오류가 발생하고 동기화가 자동으로 중지됩니다. 경고는 이중 V형 무늬 &#39;>&#39;에 의해 구현되며 동기화가 완료되면 확인되어야 합니다. 업그레이드 후 끝에 명령 프롬프트에 요약이 표시됩니다. 다음과 같이 표시됩니다.

```
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log =========Summary of the update==========
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView‘ and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
```

경고가 리소스의 충돌을 우려하면 이를 해결하기 위해 사용자의 주의가 필요합니다.

**postupgrade_ServerVersionNumber_TimeOfPostupgrade.log** 파일에는 동기화 결과가 포함되어 있습니다. 다음 디렉토리에서 기본적으로 사용할 수 있습니다.**installationDirectory/var/instanceName/postupgrade** 오류 및 경고는 오류 및 경고 속성으로 표시됩니다.

### 충돌 분석

**충돌이 어떻게 발견됩니까?**

충돌은 해당 서버의 postupgrade.log 또는 캠페인 클라이언트 인터페이스(관리 > 구성 > 패키지 관리 > 충돌 편집)에서 찾을 수 있습니다.

식별자가 &#39;stockOverview&#39;이고 &#39;nms:webApp&#39;인 문서가 새 버전과 충돌합니다.

충돌이 있는 경우 다음 조건이 일치하는지 확인하십시오.

* 고객이 개체를 수정하거나 사용자 지정했습니까?
* 제품에서 개체가 변경되었습니까?

이러한 조건 중 어느 것도 적용되지 않는 경우 이것은 잘못된 양수입니다. 이 두 가지 조건이 모두 적용되면 실제 충돌이 발견되었습니다.

**고객이 개체를 수정했습니까?**

1. 충돌하는 개체를 식별합니다.
1. 고객이 개체를 수정했는지 확인합니다.
1. 그 물건에는 특이한 점이 있나요?
1. 마지막으로 수정한 날짜가 개체 코드에 설정되어 있습니까?
1. 충돌의 XML 코드에서 &quot;_conflict&quot; 속성을 검사합니다. 맞춤화 기능처럼 보입니까?

**새 빌드에서 개체가 변경되었습니까?**

1. &quot;보통 용의자&quot;가 있나요? 내장된 웹 애플리케이션 또는 보고서(예:&#39;deliveryValidation&#39;, &#39;deliveryOverview&#39;, &#39;budget&#39;).
1. 변경 로그에서 업데이트를 확인합니다.
1. Adobe Campaign 전문가에게 문의하십시오.
1. 코드에 대해 &quot;diff&quot;를 수행합니다.

### 충돌 해결

충돌을 해결하려면 다음 프로세스를 적용합니다.

1. Adobe Campaign 탐색기에서 **관리 > 구성 > 패키지 관리 > 충돌 편집**&#x200B;으로 이동합니다.

1. 목록에서 해결할 충돌을 선택합니다.
충돌을 해결하는 3가지 옵션이 있습니다.**새 버전**, **현재 버전 유지**, **코드 병합(그리고 해결된 것으로 선언함)**, **충돌 무시(권장되지 않음)**

**새로운 버전은 언제 받을 수 있습니까?**

* 표준 기능을 원하신다면
* 사용자 정의가 없는 경우(모든 사용자 지정 설정이 제거됨)

**언제 현재 버전을 유지할 수 있습니까?**

* 사용자 정의된
* 병합하지 않으려면
* 업그레이드의 충돌 개체에 대한 수정 사항이 필요하지 않은 경우

**언제 병합을 수행해야 합니까?**

* 양식, 보고서 및 웹 애플리케이션만 병합할 수 있습니다.
* 일부 작은 병합은 코드를 이해하지 않고 해결할 수 있습니다.
* 보다 복잡한 합병은 적절한 기술과 능력을 가진 사람이 해야 한다.
* [병합 수행](#perform-a-merge)을 참조하십시오.

**충돌을 무시하면 어떻게 됩니까?**

* 갈등이 계속될 것이다
* 개체가 업그레이드되지 않습니다.
* 장기적인 효과:버전 호환하지 않는 경우, 고객은 버그 수정을 통해 혜택을 받을 수 없습니다.

>[!IMPORTANT]
>충돌을 해결하는 것이 좋습니다.


### 병합 수행{#perform-a-merge}

병합 유형은 서로 다릅니다.

1. 간편한 병합:사용자 정의 요소와 새로운 요소는 작고 관련이 없으며 코딩할 필요가 없습니다.
1. 변경 사항 없음:새 버전을 수락하고 마지막 업데이트 날짜만 변경했으며 주석, 탭, 공백 또는 새 줄만 수락합니다. 예:실수로 저장합니다.
1. 사소한 변경 사항:한 줄만 변경되었습니다. 예:xpathToLoad
1. 복잡한 병합:코딩이 필요한 경우 개발 기술이 필요합니다. [복잡한 병합](#complex-merges)을 참조하십시오.

#### 병합하는 방법

1. 3가지 버전 모두 다운로드:원본 버전, 새 버전 및 사용자 지정 버전.
1. 원본과 새 버전 간에 &quot;diff&quot;를 실행합니다.
1. 변경 사항을 격리합니다.
1. 변경 사항이 없는 경우 현재 버전을 유지하여 확인합니다.

#### 코드를 어디에서 찾을 수 있습니까?

1. 기본 제공 코드는 Datakit 폴더의 XML 파일에 저장됩니다. 충돌하는 객체와 일치하는 XML 파일을 찾습니다. 예:installationDirectory\datakit\nms\fra\form\recipient.xml
1. 원본 버전 검색:[다운로드 센터](https://docs.adobe.com/content/help/en/experience-cloud/software-distribution/home.html) 또는 업그레이드되지 않은 다른 제품 설치를 통해
1. 새 버전 검색:를 통해 [다운로드 센터](https://docs.adobe.com/content/help/en/experience-cloud/software-distribution/home.html) 또는 고객이 설치한 파일을 다운로드합니다.
1. 사용자 정의 버전 검색:캠페인 클라이언트 내에서 객체의 소스 코드를 검색합니다.

### 비교 방법

1. 텍스트 또는 병합 편집기(예: 메모장 ++, AraxisMerge, WinMerge)를 설치합니다.
1. 원본 파일과 새 파일을 편집기에서 엽니다.
1. 비교를 실행합니다(두 파일 비교).
1. 차이점 파악

### 병합하는 방법

1. 사용자 정의 버전에서 시작합니다.
1. 변경 사항을 적용합니다.
1. 충돌을 해결됨으로 선언하여 해결합니다.
1. 회귀 여부를 확인하십시오.

충돌을 수동으로 해결하도록 선택한 경우 다음과 같이 진행합니다.

1. 창의 아래쪽 섹션에서 **_conflict_string_**&#x200B;을 검색하여 충돌이 있는 엔티티를 찾습니다. 새 버전으로 설치된 엔터티에 새 인수가 포함되어 있으며 이전 버전과 일치하는 엔터티에 사용자 지정 인수가 포함되어 있습니다.
1. 유지하지 않을 버전을 삭제합니다. 보관하고 있는 엔티티의 **_conflict_argument_** 문자열을 삭제합니다.
1. 해결된 충돌로 이동합니다. **작업** 아이콘을 클릭하고 **확인됨으로 선언**&#x200B;을 선택합니다.
1. 변경 내용을 저장합니다.이제 충돌이 해결되었습니다.

#### 복잡한 병합{#complex-merges}

1. 변경 사항 이해:변경 사항을 리버스 엔지니어링하고 변경 로그를 검사한 다음 Adobe Campaign 전문가에게 문의하십시오.
1. 변경 내용을 어떻게 할지 결정합니다.
1. 사용자 정의 기능 이해:변경 내용 역설계

복잡한 병합을 수행하는 단계는 다음과 같습니다.

1. 변경 세트에서 코드 비트 복사
1. 사용자 지정된 버전에 붙여넣기
1. 사용자 정의 비회귀 테스트
1. 변경 기능 테스트
1. 사용자 수락 테스트 수행
1. 테스트 환경에서 수행


>[!IMPORTANT]
>복잡한 병합을 수행하려면 개발 기술이 필요합니다.


**관련 항목**

* [업그레이드 FAQ 구축](../../platform/using/faq-build-upgrade.md)
* [Campaign Classic 릴리스 노트](../../rn/using/rn-overview.md)
* [Campaign Classic 도움말 및 지원 옵션](https://helpx.adobe.com/campaign/kb/ac-support.html#acc-support-req)
* [Gold Standard 프로그램](https://helpx.adobe.com/kr/campaign/kb/gold-standard.html)