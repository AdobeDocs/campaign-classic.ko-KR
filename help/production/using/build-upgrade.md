---
product: campaign
title: 빌드 업그레이드 시작
description: 새 빌드로 업그레이드하는 주요 단계 알아보기
feature: Monitoring, Upgrade
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용됩니다."
badge-v7-prem: label="온-프레미스 및 하이브리드" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: c5a9c99a-4078-45d8-847b-6df9047a2fe2
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '2380'
ht-degree: 3%

---

# 빌드 업그레이드 수행{#performing-a-build-upgrade}



이 섹션에서는 업그레이드 프로세스와 충돌을 식별하고 해결하는 단계에 대해 자세히 설명합니다.

빌드 업그레이드는 신중하게 수행되어야 하며, 그 영향은 사전에 충분히 고려되어야 하고 높은 수준의 규율로 절차가 완료되어야 한다. 업그레이드를 성공적으로 수행하려면 전문가 사용자만 아래에 설명된 단계를 수행해야 합니다. 또한 다음 링크를 통해 문의하는 것이 좋습니다. [Adobe 고객 지원 센터](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 업그레이드를 시작하기 전에

다음 전제 조건이 필요합니다.

* Campaign 아키텍처에 대한 이해
* 시스템 및 서버측 지식
* 관리 권한 및 권한

자세한 내용은 다음 섹션에서 확인할 수 있습니다. [Adobe Campaign 업데이트 중](../../production/using/upgrading.md), [새 버전으로 마이그레이션](../../migration/using/about-migration.md).

호스팅 및 하이브리드 인스턴스의 경우 Adobe 기술 운영 팀에 빌드 업그레이드를 요청해야 합니다. 자세한 내용은 이 페이지의 맨 아래에 있는 FAQ 섹션을 참조하십시오. 다음 항목도 참조하십시오. [빌드 업그레이드 FAQ](../../platform/using/faq-build-upgrade.md).

## 업그레이드 준비

![](assets/do-not-localize/icon_planification.png)

빌드 업그레이드를 시작하기 전에 아래 설명된 대로 전체 준비를 수행해야 합니다.
시스템을 업그레이드할 준비가 되면 빌드 업그레이드가 필요합니다 **최소** 2시간.

빌드 업그레이드 프로세스에는 다음 리소스가 필요합니다.

* Adobe 설계자 - 데이터베이스 구조(기본 제공 스키마 및 추가된 모든 추가 스키마, 캠페인 디자인 및 특정 순서로 시작하고 테스트해야 하는 모든 중요한 경로 기능)를 이해할 수 있습니다.
* 프로젝트 관리자 - 빌드 업그레이드에 여러 다른 인스턴스(프로덕션, 스테이징, 테스트)와 기타 타사 서버 및 애플리케이션(데이터베이스, SFTP 사이트, 메시징 서비스 공급자)이 포함되는 경우 모든 테스트를 조정할 프로젝트 관리자를 갖는 것이 모범 사례로 간주됩니다.
* Adobe Campaign 관리자 - 관리자는 보안, 폴더 레이아웃, 보고 및 가져오기\내보내기 요구 사항을 포함하되 이에 국한되지 않는 서버 구성을 알고 있습니다. 관리자 없이 빌드 업그레이드를 수행하지 마십시오.
* Adobe Campaign 운영자(마케팅 사용자) - 성공적인 업그레이드는 일별 작업을 성공적으로 수행하는 사용자의 기능에 의존합니다. 이러한 이유로 업그레이드된 서버 테스트에 항상 일일 연산자 중 하나 이상을 포함하십시오.

### 계획 수립

빌드 업그레이드를 계획하는 방법에 대한 주요 사항은 다음과 같습니다.

1. 업그레이드를 위해 최소 2시간을 예약하십시오.
1. Adobe 및 고객 담당자를 위한 연락처 세부 정보를 배포합니다.
1. 호스팅된 인스턴스의 경우: Adobe 및 고객 담당자는 업그레이드 시간 및 실행 담당자를 조정합니다.
1. 온프레미스 인스턴스의 경우: 고객 직원이 전체 프로세스를 관리합니다. 맞춤화된 워크플로우 및 게재 논리를 테스트하는 데 도움이 필요한 경우 컨설팅 서비스를 가져와야 합니다.
1. 업그레이드할 Adobe Campaign 버전 확인 - 다음을 참조하십시오. [Adobe Campaign Classic 릴리스 노트](../../rn/using/rn-overview.md).
1. 업그레이드 실행 파일을 보유하고 있는지 확인합니다.

### 주요 사용자

빌드 업그레이드 프로세스를 진행하려면 다음 인력이 참여해야 합니다.

* Adobe 설계자: 호스팅 또는 하이브리드 아키텍처의 경우 설계자는 Adobe Campaign Client Care와 협력해야 합니다.

* 프로젝트 관리자:
   * 온프레미스 설치의 경우: 고객의 내부 프로젝트 리더가 업그레이드를 이끌고 라이프사이클 테스트를 관리합니다.

   * 호스팅 설치의 경우 호스팅 팀은 Adobe Campaign Client Care 팀 및 고객과 파트너 관계를 맺어 모든 인스턴스에 대한 업그레이드 타임라인을 조정합니다.

* Adobe Campaign 관리자:
   * 온프레미스 설치의 경우: 관리자가 업그레이드를 수행합니다.

   * 호스팅된 설치의 경우: 호스팅 팀이 업그레이드를 수행합니다.

* Adobe Campaign 운영자\마케팅 사용자: 운영자는 개발, 테스트 및 프로덕션 인스턴스에 대한 테스트를 실행합니다.

### 빌드 업그레이드 준비

빌드 업그레이드를 시작하기 전에 온-프레미스 고객은 다음 준비를 수행해야 합니다.

1. 업그레이드 전에 모든 개발 작업을 내보내고 패키지로 내보냅니다.

1. 소스 및 타겟 환경의 모든 인스턴스에 대해 데이터베이스의 전체 백업을 수행합니다.

1. 의 최신 버전 가져오기 [서버 구성 파일](../../installation/using/the-server-configuration-file.md).

1. [최신 빌드 다운로드](https://experience.adobe.com/#/downloads/content/software-distribution/ko/campaign.html). [자세히 알아보기](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=ko)

또한 다음을 모두 알아야 합니다. [유용한 명령줄](../../installation/using/command-lines.md) 빌드 업그레이드를 시작하기 전에:

* **nlserver 덤프**: 실행 중인 프로세스를 나열합니다.
* **nlserver pdump -who**: 활성 클라이언트 세션을 나열합니다.
* **nlserver 모니터 -missing**: 누락된 속성을 나열합니다.
* **nlserver 시작 process@instance-name**: 프로세스를 시작합니다.
* **nlserver 중지 process@instance-name**: 프로세스를 중지합니다.
* **nlserver 다시 시작 process@instance-name**: 프로세스 다시 시작
* **nlserver 종료**: 모든 Campaign 프로세스를 중지합니다
* **nlserver watchdog -svc**: 감시장치 시작(UNIX만 해당)

## 업그레이드 수행

![](assets/do-not-localize/icon_process.png)

아래 절차는 다음 대상에서만 수행됩니다. **온-프레미스** 고객. 호스팅된 고객의 경우 호스팅 팀에서 관리합니다. Adobe Campaign을 새 빌드로 업데이트하려면 아래 자세한 절차를 설명합니다.

### 환경 복제

다음은 소스 환경을 타겟 환경으로 복원하기 위해 Adobe Campaign 환경을 복제하여 두 개의 동일한 작업 환경을 만드는 방법입니다.

이렇게 하려면 아래 단계를 수행합니다:

1. 소스 환경의 모든 인스턴스에 데이터베이스 복사본을 만듭니다.

1. 타겟 환경의 모든 인스턴스에서 이러한 복사본을 복원합니다.

1. 실행 **nms:freezeInstance.js** 시작하기 전에 대상 환경에 대한 소작술 스크립트. 이렇게 하면 로그, 추적, 게재, 캠페인 워크플로 등 외부와 상호 작용하는 모든 프로세스가 중지됩니다.

   ```
   nlserverjavacsriptnms:freezeInstance.js–instance:<dev> -arg:run
   ```

1. 다음과 같이 소작술을 확인합니다.

   * 유일한 게재 부분이 ID가 설정된 부분인지 확인합니다. **0**:

     ```
     SELECT * FROM neolane.nmsdeliverypart;
     ```

   * 게재 상태 업데이트가 올바른지 확인합니다.

     ```
     SELECT iSate, count(*) FROM neolane.nmsdeliveryGroup By iProd;
     ```

   * 워크플로우 상태 업데이트가 올바른지 확인합니다.

     ```
     SELECT iState, count (*) FROM neolane.xtkworkflowGROUP BY iState;
     SELECT iStatus, count (*) FROM neolane.xtkworkflowGROUP BY iStatus;
     ```

### 서비스 종료

모든 파일을 새 버전으로 바꾸려면 nlserverservice의 모든 인스턴스를 종료해야 합니다.

1. 다음 서비스를 종료합니다.

   * 웹 서비스(IIS): **iisreset /stop**
   * Adobe Campaign 서비스: **net stop nlserver6**

   >[!NOTE]
   >
   >IIS에서 사용하는 nlsrvmod.dll 파일을 새 버전으로 바꿀 수 있도록 리디렉션 서버(webmdl)가 중지되었는지 확인하십시오.
   >

1. 를 실행하여 활성화된 작업이 없는지 확인 **nlserver 덤프** 명령입니다. 작업이 없는 경우 출력은 다음과 유사해야 합니다.

   ```
   C:\<installation path>\bin>nlserverpdump HH:MM:SS > Application Server for Adobe Campaign version x.x (build xxx) dated xx/xx/xxxx No tasks
   ```

1. Windows 작업 관리자에서 모든 프로세스가 중지되었는지 확인합니다.

### Adobe Campaign 서버 애플리케이션 업그레이드

1. 실행 **Setup.exe** 파일. 이 파일을 다운로드해야 하는 경우 [다운로드 센터](https://experience.adobe.com/#/downloads/content/software-distribution/ko/campaign.html).

1. 설치 모드를 선택합니다. **업데이트** 또는 **복구**.

1. 클릭 **다음**.

1. 클릭 **완료**: 설치 프로그램이 새 파일을 복사합니다.

1. 작업이 완료되면 다음을 클릭합니다. **완료**.

### 리소스 동기화

1. 명령줄을 엽니다.

1. 실행 **nlserver 구성 -업그레이드 후 -allinstances** 다음을 수행하십시오.

   * 리소스 동기화
   * 스키마 업데이트
   * 데이터베이스 업데이트

   >[!NOTE]
   >
   >이 작업은 nlserverweb 응용 프로그램 서버에서 한 번만 수행해야 합니다.
   >

   한 데이터베이스만 동기화하려면 다음 명령을 실행합니다.

   ```
   nlserver config -postupgrade -instance: <instance_name>
   ```

1. 동기화에서 오류 또는 경고가 생성되었는지 확인합니다.

### 서비스 다시 시작

다음 서비스를 다시 시작해야 합니다.

* 웹 서비스(IIS): **issreset /start**
* Adobe Campaign 서비스: **net start nlserver6**

### 클라이언트 콘솔 업데이트

클라이언트 콘솔은 서버 인스턴스와 동일한 빌드에 있어야 합니다.

Adobe Campaign 애플리케이션 서버가 설치된 컴퓨터(nlserverweb)에서 파일을 다운로드하여 복사합니다.

```
Setup-client-7.xxxx.exe in [path of the application]\datakit\nl\en\jsp
```

다음 번에 클라이언트 콘솔이 연결되면 새 업데이트의 사용 가능 여부를 사용자에게 알리고 다운로드 및 설치 가능성을 제공합니다.

### 특정 추가 작업

일부 구성에서 새 빌드로 업데이트하려면 특정 추가 작업이 필요합니다.

#### 트랜잭션 메시지

Campaign 인스턴스에서 트랜잭션 메시지(메시지 센터)를 사용하도록 설정한 경우 다음 추가 단계를 수행하여 업그레이드해야 합니다.

1. 메시지 센터 프로덕션 서버를 선택한 버전으로 업데이트합니다.
1. 업그레이드 후 스크립트를 실행합니다.
1. 테스트를 실행하고 메시지 센터 프로덕션 인스턴스를 통해 이메일을 성공적으로 수신하는지 확인합니다.
1. 클라이언트를 업그레이드하고 캐시를 지웁니다.
1. 패키지 내보내기:
   * 클라이언트 패키지 내보내기 도구를 사용하여 패키지 내보내기
   * 스키마 패키지 가져오기
   * 클라이언트 연결 끊기 및 다시 연결
   * 데이터베이스 업데이트
   * 연결 끊고 다시 연결
   * 관리 패키지 가져오기
   * 콘텐츠 패키지 가져오기
   * 콘텐츠 관리 패키지 가져오기
   * 연결 끊고 다시 연결
   * 워크플로우의 신속한 온전성 검사 수행

1. 메시지 센터 템플릿을 게시하여 서버와 메시지 센터 인스턴스 간의 인터페이스가 작동하는지 확인합니다.
1. 테스트를 실행하여 메시지 센터 프로덕션 인스턴스를 통해 이메일이 성공적으로 수신되는지 확인합니다.
1. 프로덕션에서 워크플로우 테스트를 실행하여 게재가 수신되는지 확인합니다.

#### 중간 소싱

중간 소싱 환경의 컨텍스트에서 다음 추가 단계를 수행하여 업그레이드해야 합니다.

1. 연락처 [Adobe 고객 지원 센터](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 중간 소싱 서버의 업그레이드를 조정합니다.
1. 테스트 링크를 실행하여 버전이 업데이트되었는지 확인합니다. 예제:

   ```
   http://[InsertServerURL]/r/test
   ```

>[!NOTE]
>
>중간 소싱 서버는 항상 마케팅 서버와 동일한 버전(또는 최신 버전)을 실행해야 합니다.
>

## 충돌의 경우

### 충돌 확인

동기화 결과를 확인해야 합니다. 이 절차는 온프레미스 고객만 수행합니다. 호스팅된 고객의 경우 호스팅 팀에서 관리합니다. 동기화 결과를 보는 방법에는 두 가지가 있습니다.

명령줄 인터페이스에서는 트리플 V자 &#39;>>&#39;에 의해 오류가 발생하고 동기화가 자동으로 중지됩니다. 경고는 이중 V자형 화살표 &#39;>>&#39;에 의해 구체화되며 동기화가 완료되면 해결해야 합니다. 업그레이드 후 요약이 명령 프롬프트에 표시됩니다. 다음과 같이 표시될 수 있습니다.

```
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log =========Summary of the update==========
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView‘ and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
```

경고가 리소스 충돌과 관련된 경우 이를 해결하기 위해 사용자의 주의가 필요합니다.

다음 **postupgrade_ServerVersionNumber_TimeOfPostupgrade.log** 파일에 동기화 결과가 포함되어 있습니다. 기본적으로 다음 디렉터리에서 사용할 수 있습니다. **installationDirectory/var/`<instance-name>`/postupgrade**. 오류 및 경고는 오류 및 경고 속성으로 표시됩니다.

### 충돌 분석

**충돌이 어떻게 발견됩니까?**

충돌은 해당 서버의 postupgrade.log 또는 Campaign 클라이언트 인터페이스(관리 > 구성 > 패키지 관리 > 충돌 편집)에서 찾을 수 있습니다.

식별자가 &#39;stockOverview&#39;이고 유형이 &#39;nms:webApp&#39;인 문서가 새 버전과 충돌합니다.

충돌이 발견되면 다음 조건이 일치하는지 확인하십시오.

* 고객이 개체를 수정했거나 사용자 지정했습니까?
* 제품에서 개체가 변경되었습니까?

이 두 가지 조건 중 어느 것도 적용되지 않는다면 이는 긍정 오류(false positive)입니다. 이 두 조건이 모두 적용된다면 실제 충돌이 발견된 것이다.

**고객이 객체를 수정했습니까?**

1. 충돌하는 개체를 식별합니다.
1. 고객이 개체를 수정했는지 질문합니다.
1. 물건에 특이한 점이 있나요?
1. 개체 코드에서 마지막으로 수정한 날짜가 설정됩니까?
1. 충돌에서 &quot;_conflict&quot; 속성을 검사한 XML 코드를 확인합니다. 맞춤화 처럼 보이나요?

**개체가 새 빌드에서 변경되었습니까?**

1. &quot;보통 용의자&quot;는? 기본 제공 웹 애플리케이션 또는 보고서(예: &#39;deliveryValidation&#39;, &#39;deliveryOverview&#39;, &#39;budget&#39;).
1. 변경 로그에서 업데이트를 검사합니다.
1. Adobe Campaign 전문가에게 문의하십시오.
1. 코드에서 &quot;diff&quot;를 수행합니다.

### 충돌 해결

충돌을 해결하려면 다음 프로세스를 적용합니다.

1. Adobe Campaign 탐색기에서 **관리 > 구성 > 패키지 관리 > 충돌 편집**.

1. 목록에서 해결할 충돌을 선택합니다.
충돌을 해결하는 세 가지 옵션이 있습니다. **새 버전 수락**, **현재 버전 유지**, **코드를 병합하고 해결된 것으로 선언합니다.**, **충돌 무시(권장되지 않음)**.

**새 버전은 언제 받을 수 있습니까?**

* 표준 기능을 원하는 경우
* 맞춤화가 없는 경우(모든 맞춤화가 제거됨)

**현재 버전은 언제 유지할 수 있습니까?**

* 맞춤화가 있는 경우
* 병합하지 않으려면
* 업그레이드에서 충돌하는 오브젝트에 대한 수정이 필요하지 않은 경우

**병합을 수행할 때**

* 양식, 보고서 및 웹 응용 프로그램만 병합할 수 있습니다.
* 일부 사소한 병합은 코드를 이해하지 않고도 해결할 수 있습니다.
* 보다 복잡한 병합은 적절한 기술과 능력을 갖춘 사람이 수행해야 한다.
* 다음을 참조하십시오 [병합 수행](#perform-a-merge).

**갈등을 무시하면 어쩌지?**

* 그 분쟁은 계속될 것이다
* 개체가 업그레이드되지 않습니다.
* 장기적 영향: 버전이 호환되지 않으므로 고객은 버그 수정을 이용할 수 없습니다.

>[!IMPORTANT]
>충돌을 해결하는 것이 좋습니다.
>

### 병합 수행{#perform-a-merge}

다양한 유형의 병합이 있습니다.

1. 간편한 병합: 사용자 지정 및 새 요소는 작고 관련이 없으며 코딩이 필요하지 않습니다.
1. 변경 내용 없음: 새 버전을 승인하고 마지막 업데이트 날짜만 변경하며 주석, 탭, 공백 또는 새 행만 허용합니다. 예: 실수로 저장합니다.
1. 사소한 변경: 한 줄만 변경되었습니다. 예: xpathToLoad
1. 복합 병합: 코딩이 필요한 경우. 개발 기술이 필요합니다. 다음을 참조하십시오 [복잡한 병합](#complex-merges).

#### 병합하는 방법

1. 원본 버전, 새 버전 및 사용자 지정 버전의 세 가지 버전을 모두 가져옵니다.
1. 원래 버전과 새 버전 간의 &quot;차이점&quot;을 실행합니다.
1. 변경 내용을 분리합니다.
1. 변경 사항이 없는 경우 현재 버전을 유지하여 해결합니다.

#### 코드를 찾을 수 있는 위치

1. 기본 제공 코드는 datakit 폴더의 XML 파일에 저장됩니다. 충돌하는 개체와 일치하는 XML 파일을 찾습니다. 예: installationDirectory\datakit\nms\fra\form\recipient.xml
1. 원본 버전 검색: 를 통해 [다운로드 센터](https://experience.adobe.com/#/downloads/content/software-distribution/ko/campaign.html) 또는 업그레이드되지 않은 다른 제품 설치.
1. 새 버전 검색: 를 통해 [다운로드 센터](https://experience.adobe.com/#/downloads/content/software-distribution/ko/campaign.html) 또는 고객이 설치한 파일.
1. 사용자 지정 버전 검색: Campaign 클라이언트 내에서 개체의 소스 코드를 검색합니다.

### 차이를 만드는 방법

1. 텍스트 또는 병합 편집기(예: 메모장 ++, AraxisMerge, WinMerge)를 설치합니다.
1. 편집기에서 원본 파일과 새 파일을 엽니다.
1. 차이를 실행합니다(두 파일 비교).
1. 차이점을 식별합니다.

### 병합하는 방법

1. 사용자 지정 버전에서 시작합니다.
1. 변경 사항을 적용합니다.
1. 해결됨으로 선언하여 충돌을 해결합니다.
1. 회귀가 아닌지 확인합니다.

충돌을 수동으로 해결하도록 선택하는 경우 다음과 같이 진행합니다.

1. 창의 아래쪽에서 **_conflict_string_** 를 클릭하여 충돌이 있는 엔티티를 찾습니다. 새 버전으로 설치된 엔터티에는 새 인수가 들어 있고 이전 버전과 일치하는 엔터티에는 사용자 지정 인수가 들어 있습니다.
1. 보관하지 않을 버전을 삭제합니다. 삭제 **_conflict_인수_** 유지할 엔터티의 문자열입니다.
1. 해결한 충돌로 이동합니다. 다음을 클릭합니다. **작업** 아이콘 및 선택 **해결됨으로 선언**.
1. 변경 내용을 저장합니다. 이제 충돌이 해결되었습니다.

#### 복잡한 병합{#complex-merges}

1. 변경 사항의 역할 이해: 변경 사항을 리버스 엔지니어링하고, 변경 로그를 검사하고, Adobe Campaign 전문가와 후속 작업을 수행합니다.
1. 변경 사항을 어떻게 할지 결정하십시오.
1. 맞춤화의 기능 이해: 변경 내용을 리버스 엔지니어링합니다.

복잡한 병합을 수행하는 단계는 다음과 같습니다.

1. 변경 집합에서 코드 비트 복사
1. 사용자 지정된 버전에 붙여넣기
1. 사용자 지정 회귀 안 함 테스트
1. 변경 기능 테스트
1. 사용자 승인 테스트 수행
1. 테스트 환경에서 수행


>[!IMPORTANT]
>복잡한 병합을 수행하기 위해서는 개발 기술이 필요하다.
>

**관련 항목**

* [빌드 업그레이드 FAQ](../../platform/using/faq-build-upgrade.md)
* [Campaign Classic 릴리스 노트](../../rn/using/rn-overview.md)
* [Campaign Classic에 대한 도움말 및 지원 옵션](../../support.md)
* [Campaign 연간 업그레이드 프로그램](../../rn/using/rn-overview.md)
