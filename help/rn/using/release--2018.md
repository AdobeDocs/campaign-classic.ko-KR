---
product: campaign
title: Campaign Classic 2018 릴리스
description: 'Campaign Classic 2018 릴리스에 대해 자세히 알아보기 '
exl-id: f70fceba-4bbf-4f33-8746-e4405a1cdae6
source-git-commit: f4513834cf721f6d962c7c02c6c64b2171059352
workflow-type: tm+mt
source-wordcount: '5385'
ht-degree: 7%

---

# 2018년 릴리스{#release-2018}

![](../../assets/v7-only.svg)

## 릴리스 18.10

### 릴리스 18.10.6 - 빌드 8985{#release-18-10-6-build-8985}

2019년 7월 12일

**개선 사항**

* 이제 가져오기 작업 과정 중에 Microsoft Dynamics에서 만든 더미 레코드를 삭제할 수 있습니다.
* 파일 액세스가 거부될 때 루프에서 오류를 기록할 수 있는 파일 수집기 워크플로우 활동 문제를 해결했습니다. (NEO-12085)
* 열려 있는 게재 지표에 대한 사용자 활동과 추적 보고서 간의 불일치를 보고하도록 하는 문제를 해결했습니다. (NEO-11742)
* 내부 계정을 사용할 때 보안 영역 패키지를 실행하는 권한이 개선되었습니다.
* 일치하는 필드 로그에 오류가 발생할 수 있는 문제를 수정했습니다. (NEO-8978)

### 릴리스 18.10.5 - 빌드 8984{#release-18-10-5-build-8984}

2019년 4월 23일

**개선 사항**

* 동시 분석/전송(동시에 두 개의 게재를 분석했을 때)의 경우 게재 분석이 실패하는 SQL 교착 상태 문제를 해결했습니다. (NEO-13026)
* 누락된 데이터 문제를 해결하기 위해 워크플로우 Heatmap에서 10,000개의 레코드 제한을 제거했습니다. (NEO-12329)
* 데이터 보강 워크플로우 활동에서 &quot;기본 세트에서 추가 데이터를 모두 유지&quot; 옵션을 사용할 때 발생하는 문제를 해결했습니다. (NEO-13291)

### 릴리스 18.10.4 - 빌드 8983{#release-18-10-4-build-8983}

2019년 4월 15일

**개선 사항**

* 트랜잭션 메시지에 대한 지표 추적 컴퓨팅 프로세스의 문제를 수정했습니다. (NEO-12529, NEO-12581)
* 모든 콜백이 완료될 때까지 기다리지 않는 HTTPRequest API 관련 문제를 해결했습니다. (NEO-12628)
* 게재 전송을 최적화하기 위해 쿠폰 임시 테이블에 인덱스가 추가되었습니다. (NEO-12437)
* 일본어(.JP) 도메인의 수신자를 타겟팅하는 메시지를 분석할 때 발생하는 문제를 해결했습니다. (NEO-12246)
* Analytics 통합에서 이제 % 문자로 AAM 세그먼트 데이터를 검색할 수 있습니다. (NEO-12025)
* HTTP2를 사용하여 푸시 알림을 전송할 때 발생하는 Tomcat 충돌 문제를 해결했습니다. (NEO-12701)

### 릴리스 18.10.3 - 빌드 8981{#release-18-10-3-build-8981}

2019년 1월 29일

>[!CAUTION]
>
>이 빌드는 리콜되었습니다. 제발 [최신 빌드로 업그레이드](../../production/using/build-upgrade.md)  또는 연락처 [고객 지원 Adobe](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**개선 사항**

* s3 파일 전송 워크플로우 활동 문제를 해결했습니다. (NEO-12473)
* 추적 워크플로우가 실패할 수 있는 문제를 해결했습니다. (NEO-12520)
* IMS 로그인 문제를 해결했습니다.
* 큰 오퍼 ID를 사용할 때 트랜잭션 메시지에서 미리 보기 및 콘텐츠 승인 문제를 해결했습니다.
* 중간 소싱(게재 카운터) 워크플로우 문제를 해결했습니다.
* NmsRecipient에서 새 인덱스를 삭제하는 데이터베이스 구조 업데이트 문제를 해결했습니다.
* 게재의 기본 대상에 대해 외부 파일에서 정의 옵션을 사용할 때 발생할 수 있는 콘솔 충돌을 수정했습니다. (NEO-12349)
* 여러 InMail 충돌이 수정되었습니다.
* 데이터 업데이트 워크플로우 활동을 사용하여 FDA Teradata 데이터베이스에 저장된 레코드를 삭제할 때 발생하는 문제를 수정했습니다.
* 비밀 키 관리의 불일치 문제가 해결되었습니다.
* 필드를 다음과 같이 입력할 때 데이터 보강 활동 문제를 해결했습니다. xml=true 및 calculated=true
* 모바일 애플리케이션에서 푸시 알림을 전송할 때 발생하는 문자 이스케이프 문제를 해결했습니다.
* 중간 소싱 외부 계정에서 FDA에서 SOAP 동기화 방법으로 전환할 수 없는 문제를 해결했습니다.

### 릴리스 18.10.2 - 빌드 8978{#release-18-10-2-build-8978}

2018년 12월 6일

>[!CAUTION]
>
>이 빌드는 리콜되었습니다. 제발 [최신 빌드로 업그레이드](../../production/using/build-upgrade.md) 또는 연락처 [고객 지원 Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**개선 사항**

* FDA에서 MySQL을 사용하여 워크플로우를 실행할 때 발생하는 다양한 문제를 해결했습니다. (NEO-11652)
* 푸시 알림을 전송할 때 발생하는 성능 문제를 해결했습니다. (NEO-11787)
* 게재에서 시드 주소를 사용할 때 발생하는 ID 소모 문제를 수정했습니다. (NEO-11842)
* 복잡한 워크플로우를 사용할 때 발생할 수 있는 클라이언트 고정 문제를 해결했습니다. (NEO-11847)
* 1:N 링크에서 값 분포를 사용할 때 발생하는 표시 문제를 수정했습니다. (NEO-11820)
* 워크플로우 Heatmap에서 Oracle 오류를 수정했습니다.
* 데이터 보강 활동에서 오퍼 제안을 추가할 때 발생하는 올바른 문제를 수정했습니다.
* SQL 데이터 관리 연결 문제를 해결했습니다.
* 음수 ID의 경우 임시 워크플로우 테이블 이름을 생성하는 문제를 수정했습니다.
* 워크플로우 HeatMap에서 워크플로우 지속 시간 계산 문제를 수정했습니다.


### 릴리스 18.10.1 - 빌드 8977{#release-18-10-build-8977}

2018년 11월 5일

>[!CAUTION]
>
>이 빌드는 리콜되었습니다. 제발 [최신 빌드로 업그레이드](../../production/using/build-upgrade.md) 또는 연락처 [고객 지원 Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**새로운 기능**

<table> 
 <thead> 
  <tr> 
   <th> 기능<br /> </th> 
   <th> 설명<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 푸시 알림 개선<br /> </td> 
   <td> Adobe Campaign에서 푸시 알림에 대한 많은 개선 사항이 구현되었습니다.<br /> 
    <ul> 
     <li> <p>iOS에서 자동 알림 추적 </p> </li> 
     <li> <p>iOS의 등록 호출에 대한 피드백 구현</p> </li> 
     <li> <p>iOS 게재 준비 속도 개선</p> </li> 
    </ul> <p>Google에서 GCM 감가상각의 일부로, 이제 Android V2 커넥터에서 FCM 서버에만 연결을 허용합니다.</p><p>자세한 내용은 <a href="../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md">세부 설명서</a>를 참조하세요.</p> </td> 
  </tr> 
  <tr> 
   <td> SQL 데이터 관리 활동<br /> </td> 
   <td> <p>새로운 데이터 관리 워크플로우 활동을 추가했습니다. 다음 <strong>SQL 데이터 관리</strong> 활동을 통해 고유한 SQL 스크립트를 작성하거나 복사하여 붙여넣기를 사용하여 작업 테이블(FDA 전용)을 만들고 채울 수 있습니다. </p> <p>자세한 내용은 <a href="../../workflow/using/sql-data-management.md">세부 설명서</a>를 참조하세요.</p></td> 
  </tr> 
  <tr> 
   <td> 워크플로우 모니터링<br /> </td> 
   <td> <p>새로운 Adobe Campaign Workflow HeatMap을 사용하면 플랫폼 관리자가 모든 동시 실행 워크플로우를 빠른 그래픽으로 표시하여 인스턴스의 로드를 모니터링하고 그에 따라 워크플로우를 계획할 수 있습니다.</p> <p>자세한 내용은 <a href="../../workflow/using/heatmap.md">세부 설명서</a>를 참조하세요.</p> <p>Workflow HeatMap 패키지는 8977(빌드 8700 시작) 이전 빌드에 대한 수요에서도 사용할 수 있습니다. 요청 및 설치에 대한 자세한 내용은 <a href="https://helpx.adobe.com/campaign/kb/install-workflow-heatmap-package.html">이 페이지</a>.</p> </td> 
  </tr> 
 </tbody> 
</table>

**향상된 보안 기능**

* SSRF(Server Side Request Forgery) 공격 및 서비스 거부(DoS) 공격에 취약할 수 있는 보안 문제를 해결했습니다. (NEO-11453)
* 컨텐츠(리디렉션, 미러 페이지, 설문 조사 등) 이제 X-Robots-Tag가 포함된 Campaign에서 을(를) 제공합니다. 캐시 헤더가 없습니다. 따라서 인터넷 검색 엔진별로 이 콘텐츠를 인덱싱할 수 없습니다. (NEO-11101)
* 구독 API(nms)에서 XTK 주입 문제가 해결되었습니다.:subscription:구독 취소 및 nms:subscription:구독).
* 구독 취소 웹 애플리케이션에서 XTK 주입 문제가 수정되었습니다.
* 일부 SMS 로그에 안전하게 표시된 암호를 제거했습니다.

**개선 사항**

* 이제 [전용 페이지](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=ko)에서 Campaign Classic API를 사용할 수 있습니다. jsapi.chm 파일을 사용하는 경우 이제 새로운 온라인 버전을 참조해야 합니다.
* 이제 PostgreSQL 10, Debian 9 및 Teradata 16.20이 지원됩니다. [호환성 매트릭스](https://helpx.adobe.com/kr/campaign/kb/compatibility-matrix.html)를 참조하십시오.
* 이제 SFTP 연결을 만들 때 프록시 인증을 사용할 수 있습니다. 자세한 내용은 [세부 설명서](../../installation/using/file-res-management.md) (NEO-9868)
* 다음 **날짜 계산 공식** 이제 dm 게재 템플릿을 사용하여 단일 게재를 만들 때 게재 속성에서 옵션을 사용할 수 있습니다. (NEO-9792)
* 쿠키 추적 및 웹 애플리케이션을 위해 도메인 이름 관리가 개선되었습니다. 자세한 내용은 아래의 &#39;기술 진화&#39; 섹션을 참조하십시오.
* 게재 또는 랜딩 페이지에서 Adobe Marketing Cloud 공유 자산의 가져오기가 보안 및 성능 측면에서 개선되었습니다.
* 모바일 채널 외부 계정에서 새로운 확인란을 사용하여 로그 파일에서 자세한 SMPP 추적을 활성화하면 Adobe Campaign 인터페이스에서 직접 이 출력에 액세스할 수 있습니다.
* 이제 브로드로그에는 최대 연결 수와 시간당 최대 메시지 수가 구분됩니다. 제한에 도달하면 처리량이 제한되는 이유를 알 수 있습니다. 이전에는 두 사례에 동일한 메시지(&#39;quota met&#39;)가 적용되었습니다.
* 이제 풀에서 연결을 가져올 때 실행할 SQL 스크립트를 지정할 수 있습니다. 이 스크립트를 사용하여 기본 스키마를 설정할 수 있습니다. 이 스크립트는 쿼리 브랜딩 후에 적용됩니다. (NEO-11256)
* Campaign SDK는 PII 규정을 준수하도록 더 이상 사용자 ID를 저장하지 않습니다. 이제 데이터가 해시로 저장됩니다.
* 패키지 내보내기 XML 파일을 가져올 때 Campaign에서는 인코딩이 파일에서 명시적으로 선언된 경우에도 파일에 BOM이 있는 것을 지원합니다.

**기술 진화**

클라이언트 및 서버 업그레이드

>[!CAUTION]
>
>18.10으로 업데이트된 서버가 있는 경우 서버에 액세스하려면 18.10 클라이언트를 사용해야 합니다. 18.10 클라이언트는 이전 서버 버전에 연결할 수 있습니다.

도메인 이름 관리

쿠키 추적 및 웹 애플리케이션을 위해 도메인 이름 관리가 개선되었습니다.

이제 기본적으로 두 글자로 된 두 번째 수준 도메인 이름이 모두 지원됩니다(예: .aa.com). 보다 복잡한 도메인 이름(예: .com.au와 같은 세 글자로 된 두 번째 수준 도메인)의 경우, **cookieDomains** serverConf 옵션(리디렉션 태그 아래)입니다. 다음은 한 예입니다.

```
<redirection cookiedomain="http://toureiffel.paris">
```

색인 개선 사항

NmsRecipient에 대한 인덱스가 다시 작성되었습니다. 이렇게 하면 이 테이블을 사용하는 쿼리에 대한 성능이 향상됩니다. NmsRecipient의 확장을 수행한 경우 새 인덱스를 복제하는 인덱스가 없는지 확인할 수 있습니다(데이터베이스 서버의 공간 사용을 최소화함). (NEO-8228)

UTF-8 데이터 정렬을 사용할 때 이제 &quot;LIKE &#39;string%&#39;(또는 &quot;다음으로 시작&quot;) 작업을 최적화하는 인덱스를 만들 수 있습니다. 동일한 열에서 다른 작업을 수행하는 경우(예: 정렬 기준 또는 조인) 다른 표준 인덱스가 필요합니다. 스키마 측에서 이 작업은 인덱스 정의에 indexOption=&quot;searchFromStart&quot;를 추가하여 수행합니다(표준 트리 인덱스 대신 varchar_pattern_ops 인덱스를 생성). 예(NmsRecipient에서):

```
<dbindex name="email2"> <!-- optimize order by/join (and startWith if not PostgreSql with an UTF-8 collation) operations -->
  <keyfield xpath="@email"/>
</dbindex>
<dbindex name="email3" indexOption="searchFromStart"><!-- optimize startsWith operation on PostgreSql when a UTF-8 collation is used; create no index in other cases-->
  <keyfield xpath="@email" />
</dbindex>
```

새 인덱스가 NmsRtEvent 및 NmsEventHisto(&quot;예약된&quot; 열에서)에 추가되었으므로 해당 양식의 표시 시간이 개선됩니다(NEO-11738).

이러한 인덱스 변경으로 인해 업그레이드 후 수행 시간이 늘어날 수 있습니다.

**패치**

* 에서 파일을 사용할 수 없는 오류를 수정했습니다. **웹 다운로드** 워크플로우 활동 다운로드 중. (NEO-11105)
* 가끔 **지표 및 캠페인 속성 보내기** 워크플로우 실패 상태(NEO-10820).
* 워크플로우에서 목록 업데이트 활동을 실행한 후 생성된 수신자 목록을 삭제하는 문제를 해결했습니다. (NEO-11696)
* 캠페인 달력(일본어 인스턴스에서)에서 한 달 전에 캠페인을 잘못 표시하는 문제를 수정했습니다. (NEO-11445)
* 게재 속성의 웹 분석 탭에 Analytics 구성이 표시되지 않는 문제를 수정했습니다. (NEO-11619)
* nms:delivery 입력 양식을 편집하고 저장하려고 할 때 표시되는 오류를 수정했습니다. (NEO-10973)
* 파일 전송 활동이 포함된 워크플로우를 실행할 때 발생하는 외부 계정 구성 문제를 해결했습니다. (NEO-11012)
* zcat 함수를 사용하여 데이터 로드 활동에서 파일을 로드할 때 빈 줄을 반환하던 문제를 수정했습니다. (NEO-11273)
* 게재를 분석하는 동안 중복되는 광범위한 로그를 생성하는 문제를 수정했습니다. (NEO-11360)
* 워크플로우에서 데이터 보강 활동을 실행한 후 외부 링크 키가 누락되어 게재가 실패하는 문제를 해결했습니다. (NEO-11537)
* 설치 경로에 중국어 문자가 포함되어 있을 때 Adobe Campaign을 제거하거나 복구할 수 없는 GB18030 문제를 해결했습니다.
* 일부 추적 로그를 잘못된 게재에 연결하는 문제를 수정했습니다. (NEO-11412)
* 게재 로그 중 일부 부분이 예상 보다 오래 보류 중인 상태로 유지될 수 있는 문제를 해결했습니다. (NEO-11336)
* 게재 시 쿠폰을 추가하기 위해 쿼리를 편집할 때 발생하는 오류를 수정했습니다. (NEO-11037)
* 집계된 연산자가 선택된 경우에도 차트가 항상 값의 합계를 계산하도록 하는 보고서의 문제를 수정했습니다. (NEO-10913)
* &quot;request.scheme&quot; 함수는 더 이상 사용되지 않으므로 JSAPI 설명서에서 제거되었습니다. (NEO-10828)
* 특정 시간대 구성을 가진 일부 사용자가 Adobe Campaign에 로그인하지 못하는 문제를 해결했습니다. (NEO-10712)
* 확장 일반 SMPP 커넥터를 사용하여 Mobile 채널 외부 계정을 설정할 때 발생하는 문제를 해결했습니다. 수신기에 대해 다른 매개 변수를 사용하여 지정한 경우 송신기가 자체 매개 변수 대신 이러한 매개 변수를 잘못 사용하게 됩니다.
* 첫 번째 중재 후 게재가 지속적으로 다시 계산되었기 때문에 압력 규칙에 대한 빈도를 설정할 때 예약된 게재가 실패하던 문제를 해결했습니다. (NEO-10016)
* nlsrvmod.dll 라이브러리의 응용 프로그램 풀 재활용 프로세스 중에 IIS 웹 서버가 충돌하는 문제를 해결했습니다. (NEO-10862)
* 에서 수신자를 검색할 수 없는 문제를 해결했습니다 **프로필 및 Target** 화면. (NEO-8228)
* 레코드 수가 많은 경우 이벤트 내역 폴더에 액세스할 때 시간 초과 오류가 발생하는 문제를 수정했습니다. (NEO-11738)
* LINE 게재 수신자가 &quot;접근 불가&quot;로 잘못 반환되는 문제를 해결했습니다. (NEO-10833)
* oracle 시 추가 열이 있는 워크플로우 쿼리를 실행할 때 발생하는 문제를 해결했습니다. (NEO-11615)
* 연결 풀에 닫힌 연결이 너무 오랫동안 유지되지 않도록 기능이 개선되었습니다. (NEO-11392)
* 타겟팅 워크플로우 활동(쿼리, 데이터 로드(RDBMS) 등)을 사용할 때 발생하는 문제를 해결했습니다. UTF8 문자(테이블 이름, 필드 이름 등)가 포함된 외부 Oracle 테이블에 FDA를 통해 연결 또한 시스템 생성 기본 제약 조건 이름이 있는 기본 키 제약 조건이 포함됩니다. (NEO-10714)
* 게재의 HTML 콘텐츠를 삭제하지 못하는 문제를 해결했습니다. (NEO-11327)
* 캠페인 실행 후 DM에서 XML 및 CSV 파일 미리 보기 문제를 수정했습니다. (NEO-11290)
* 데이터 보강 워크플로우 활동에서 데이터를 정렬할 때 발생하는 문제를 해결했습니다. (NEO-11394)
* 사용자 지정 보고서에서 데이터를 정렬할 때 발생하는 문제를 해결했습니다. (NEO-10896)
* teradata에서 useVault 설정을 사용할 때 오류가 발생하는 문제를 수정했습니다. (NEO-11399)
* 여러 쿼리 라인을 삭제할 때 Adobe Campaign 클라이언트 콘솔이 충돌하는 문제를 해결했습니다. (NEO-10744)
* DM을 제공할 때 일부 경우에 압력 규칙이 적용되지 않는 문제를 수정했습니다. (NEO-9004)
* 데이터 로드 활동을 사용하여 데이터 유형이 &#39;시간&#39;인 열을 가져올 때 발생하는 문제를 해결했습니다. 시간 구분자는 제거한 후에도 재설정됩니다. (NEO-10743)
* 반복 게재를 편집할 때 게재 속성의 실행 폴더 목록에 게재 폴더가 표시되지 않는 문제를 수정했습니다. (NEO-11094)
* 모집단 보기 창에서 200개가 넘는 레코드를 워크플로우에서 쿼리 활동의 결과 대상으로 표시할 수 없는 문제를 수정했습니다. (NEO-11195)
* 1000개 이상의 요소를 선택한 상태로 DELETE 쿼리를 실행할 수 없는 Oracle 문제를 해결했습니다. (NEO-11171)
* Android 푸시 알림 게재의 추가 매개 변수에서 추적된 URL로 URL을 인코딩하는 문제가 해결되었습니다. (NEO-11468)
* 매개 변수를 &#39;1일 간격&#39; 및 &#39;열기&#39;로 설정할 때 사용자 활동 보고서에서 발생하는 스크립트 오류를 수정했습니다. (NEO-11655)
* 인증된 웹 프록시를 통해 중간 소싱 서버 또는 메시지 센터에 연결할 때 발생하는 문제를 해결했습니다. (NEO-11309)
* 특정 스키마의 요소를 선택한 후 새 게재 컴포지션을 저장할 때 발생하는 Oracle 오류를 수정했습니다 **SQL 보기 기반**. (NEO-11682)
* 압축 해제 옵션을 사용하여 파일 로드 활동을 통해 .csv 가 포함된 zip 파일을 처리할 때 긍정 오류(false positive)가 포함된 거부 파일이 생성되던 문제를 수정했습니다.
* xtchjoblog가 이제 정리 작업에 의해 제거됩니다.

## 릴리스 18.6

### 릴리스 18.6.2 - 빌드 8949{#release-18-6-3-build-8949}

2018년 8월 22일

>[!CAUTION]
>
>이 빌드는 리콜되었습니다. 제발 [최신 빌드로 업그레이드](../../production/using/build-upgrade.md) 또는 연락처 [고객 지원 Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**새로운 기능**

<table> 
 <thead> 
  <tr> 
   <th> 기능<br /> </th> 
   <th> 설명<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 쿼리 밴딩<br /> </td> 
   <td> <p>여러 Campaign 사용자가 동일한 FDA Teradata 외부 계정에 연결하면 이제 각 사용자별 쿼리 대역(키/값 쌍)을 전달할 수 있습니다. Campaign 사용자가 Teradata 데이터베이스에서 쿼리를 수행할 때마다 Adobe Campaign은 이제 사용자에게 연결된 메타 데이터를 전송할 수 있습니다. 키 및 값 목록으로 구성된 이러한 데이터는 Teradata 관리자가 감사 목적으로 사용하거나 액세스 권한을 관리하는 등의 목적으로 사용할 수 있습니다.</p><p>자세한 내용은 <a href="../../installation/using/external-accounts.md">세부 설명서</a>를 참조하세요.</p> </td>
  </tr> 
 </tbody> 
</table>

**개선 사항**

* 전자 메일 보관 로그가 개선되어 BCC 보관을 통해 성공적으로 배달되었거나 실패한 전자 메일을 보다 쉽고 정확하게 확인할 수 있습니다. (NEO-10675)
* 추적 브로드로그에서 고객 IP 대신 로드 밸런서 IP가 표시되는 문제를 해결했습니다. (NEO-11295)
* 게재 속성을 잘못 덮어쓰는 무작위 문제가 수정되었습니다. (NEO-11015)
* 데이터 보강 활동 결과를 정렬할 때 구문 오류를 수정했습니다. (NEO-11394)
* 에서 계산된 필드를 사용할 때 발생하는 문제를 수정했습니다 **[!UICONTROL Survey answers]** 워크플로우 활동. (NEO-11382)
* Tomcat이 취약점 착취를 방지하기 위해 업데이트되었습니다. (NEO-11503)
* PostgreSQL 데이터베이스에 FDA 연결을 사용할 때 LATIN1 인코딩 오류가 수정되었습니다. (NEO-11299)
* 를 사용할 때 발생하는 문제를 수정했습니다 **[!UICONTROL Prepare the personalization data with a workflow]** 배달 옵션. (NEO-11047)
* 확장 커넥터를 사용할 때 SMS 전송을 방해하는 업그레이드 후 문제를 해결했습니다.
* 패키지 가져오기/내보내기 개선(인터페이스에 로그 및 영역이 추가됨).
* 업그레이드 후 로그에 **[!UICONTROL Survey answers]** 워크플로우 활동이 완전히 구성되지 않았습니다.

**기술 진화**

쿼리 밴딩

특정 키(PROXYUSER 또는 PROXYROLE)는 Teradata 사용자 또는 역할을 Campaign 사용자에게 연결하는 데 사용됩니다. 이 프록시 사용자/역할을 사용하기 위해 새 권한이 추가되었습니다. 데이터베이스 계정(Teradata 외부 계정에 정의된 계정)에 GRANT CONNECT THROUGH 액세스 권한을 추가해야 합니다.

teradata 외부 계정에 새 탭이 추가되었습니다. 다음 **[!UICONTROL Query banding]** 탭에는 다음 옵션이 포함되어 있습니다.

* **[!UICONTROL Active]**: 이 확인란을 선택하여 기능을 활성화합니다.
* **[!UICONTROL Default]**: 사용자에게 연관된 쿼리 밴딩이 없는 경우 사용할 기본 쿼리 밴딩을 입력합니다. 정의된 기본 쿼리 밴딩이 없는 경우 연결된 쿼리 밴딩이 없는 사용자는 Teradata을 사용할 수 없습니다.
* **[!UICONTROL Users]**: 각 사용자에 대해 쿼리 밴딩을 지정합니다. 필요한 만큼 키/값 쌍을 추가할 수 있습니다. 예: &#39;priority=1;workload=high;&#39;

쿼리 밴딩에 대한 자세한 내용은 다음 문서를 참조하십시오.

* [https://docs.teradata.com/reader/cY5B~oeEUFWjgN2kBnH3Vw/a5G1iz~ve68yTMa24kVjVw](https://docs.teradata.com/reader/cY5B%7EoeEUFWjgN2kBnH3Vw/a5G1iz%7Eve68yTMa24kVjVw)
* [https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ)

### 릴리스 18.6.1 - 빌드 8947{#release-18-6-build-8947}

2018년 6월 25일

>[!CAUTION]
>
>이 빌드는 리콜되었습니다. 제발 [최신 빌드로 업그레이드](../../production/using/build-upgrade.md) 또는 연락처 [기술 지원](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**새로운 기능**

<table> 
 <thead> 
  <tr> 
   <th> 기능<br /> </th> 
   <th> 설명<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 보안 개선 사항<br /> </td> 
   <td> 일련의 보안 개선 사항이 Campaign Classic에 추가되었습니다. 개선 사항 및 수정 사항이 아래에 나열되어 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> Windows Server 2016 지원<br /> </td> 
   <td> Adobe Campaign은 이제 Windows Server 2016와 호환됩니다. 을(를) 참조하십시오. <a href="https://helpx.adobe.com/campaign/kb/compatibility-matrix.html">Campaign Classic 호환성 매트릭스</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

**향상된 보안 기능**

decryptString

다음 **decryptString** 함수는 더 이상 사용되지 않습니다. 자세한 내용은 [사용이 중단되거나 제거된 기능](deprecated-features.md) 문서.

새 고객의 경우 이제 이 함수는 랜딩 페이지에서 수신자의 암호화된 ID를 해독하는 데만 사용됩니다. 외부 계정에 저장된 암호를 해독하려면 새 **decryptPassword** 함수 위에 있어야 합니다.

기존 고객의 경우 이 기능의 동작은 변경되지 않지만, **decryptPassword** 대신 **decryptString**. 다음 **XtkSecurity_Unsafe_DecryptString** 호환성 옵션이 업그레이드 후 추가되고 기본적으로 활성화되므로 함수를 계속 사용할 수 있습니다. 비활성화하려면 **decryptString**&#x200B;을 비활성화하십시오.

decryptPassword

다음 **decryptPassword** 함수가 추가되었습니다. 외부 계정에 저장된 암호를 해독할 수 있습니다. 자세한 내용은 [JSAPI](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) 설명서 를 참조하십시오.

파일 API

새로 설치하는 경우 파일 API를 통한 폴더 액세스는 다음으로 제한됩니다 **var**, **sftp** 및 Adobe Campaign의 임시 폴더.

기존 고객의 경우 파일 API가 더 이상 **conf** Adobe Campaign 폴더. 다음 **XtkSecurity_Disable_JSFileSandboxing** 호환성 옵션이 업그레이드 후 추가되고 기본적으로 활성화되므로 다른 폴더에 계속 액세스할 수 있습니다. 액세스 권한을 **var**, **sftp** Adobe Campaign의 임시 폴더에서 옵션을 비활성화합니다.

**Patch**

* SMS 트랜잭션 메시지 성능에 영향을 줄 수 있는 문제를 해결했습니다. (NEO-9812)

## 릴리스 18.4

### 릴리스 18.4.5 - 빌드 8937{#release-18-4-5-build-8937}

2018년 11월 21일

**개선 사항**

* FDA에서 MySQL을 사용하여 워크플로우를 실행할 때 발생하는 다양한 문제를 해결했습니다. (NEO-11652)
* 특정 경우에 게재 모집단의 일부가 보류 중 상태로 유지되던 문제를 수정했습니다. (NEO-11336)
* SMS 자동 응답에서 간헐적인 문제를 해결했습니다. (NEO-11811)
* 게재에서 시드 주소를 사용할 때 발생하는 ID 소모 문제를 수정했습니다. (NEO-11842)
* 데이터 보강 워크플로우 활동에서 정렬을 수행할 때 구문 오류를 수정했습니다. (NEO-11394)
* IIS를 다시 시작할 때 웹 서버 충돌을 일으킬 수 있는 문제를 해결했습니다. (NEO-10862)
* 빌드 업그레이드(FDA - SQL) 후 추적 워크플로우가 실패할 수 있는 문제를 해결했습니다. (NEO-11635)
* 워크플로우 목록 데이터가 손실될 수 있는 문제를 해결했습니다. (NEO-11696)
* 푸시 알림을 전송할 때 발생하는 성능 문제를 해결했습니다. (NEO-11787)
* &quot;com.au&quot; 도메인에 대해 웹 추적이 작동하지 않는 문제를 해결했습니다(NEO-4385).
* 복잡한 워크플로우를 사용할 때 발생할 수 있는 클라이언트 고정 문제를 해결했습니다. (NEO-11847)
* 특정 스키마의 요소를 선택한 후 새 게재를 저장할 때 발생하는 Oracle 오류를 수정했습니다(NEO-11682).
* 강조가 있는 문자가 포함된 필드를 쿼리할 때 발생하는 문제를 해결했습니다(FDA/Teradata). 이제 외부 계정을 통해 Teradata 드라이버과 통신하는 데 사용되는 인코딩을 변경할 수 있습니다. (NEO-11818).
* 푸시 알림의 추가 변수에 URL을 전달할 때 모바일 애플리케이션에서 받은 잘못된 형식 또는 잘못된 데이터를 초래할 수 있는 추적 문제를 해결했습니다. (NEO-11468, NEO-11960)
* 1:N 링크에서 값 분포를 사용할 때 디스플레이 문제가 발생하는 문제를 수정했습니다. (NEO-11820)
* 벌크 로드가 Teradata 16에서 작동하지 않는 문제를 해결했습니다.
* 15.10 드라이버의 바인딩 문제를 방지하기 위해 Teradata에서 타임스탬프의 버퍼 크기를 늘렸습니다.
* 업그레이드 후 문제를 일으킬 수 있는 긴 이름 인덱스 관리를 개선했습니다.
* MTA(자식 데드 처리) 중 사용 가능한 공유 메모리 시간이 개선되었습니다.
* Apache(추적)의 잠재적 교착 상태가 해결되었습니다.


### 릴리스 18.4.4 - 빌드 8936{#release-18-4-4-build-8936}

2018년 8월 1일

**개선 사항**

* 전자 메일 보관 로그가 개선되어 BCC 보관을 통해 성공적으로 배달되었거나 실패한 전자 메일을 보다 쉽고 정확하게 확인할 수 있습니다. (NEO-10675)
* 추적 브로드로그에서 고객 IP 대신 로드 밸런서 IP가 표시되는 문제를 해결했습니다. (NEO-11295)
* PostgreSQL 데이터베이스에 FDA 연결을 사용할 때 LATIN1 인코딩 오류가 수정되었습니다. (NEO-11299)
* 를 사용할 때 발생하는 문제를 수정했습니다 **[!UICONTROL Prepare the personalization data with a workflow]** 배달 옵션. (NEO-11047, NEO-11301)
* 게재 속성을 잘못 덮어쓰는 무작위 문제가 수정되었습니다. (NEO-11015)
* 에서 계산된 필드를 사용할 때 발생하는 문제를 수정했습니다 **[!UICONTROL Survey answers]** 워크플로우 활동. (NEO-11382)
* XML에 저장된 데이터를 **[!UICONTROL Survey answers]** 워크플로우 활동. (NEO-10816)
* 빌드 8935로 서버 업그레이드를 수행할 때 발생하는 문제를 해결했습니다.
* 업그레이드 후 로그에 **[!UICONTROL Survey answers]** 워크플로우 활동이 완전히 구성되지 않았습니다.
* FDA Teradata: SQL 테이블의 자동 증분 필드 및 색인 문제를 해결했습니다.

### 릴리스 18.4.3 - 빌드 8935{#release-18-4-3-build-8935}

2018년 6월 22일

**개선 사항**

* Microsoft Edge 및 Internet Explorer의 추적 인코딩 문제를 수정했습니다. (NEO-11257)
* LINE 게재에서 이미지 링크 개인화 문제를 해결했습니다. (NEO-11077)
* ID 시퀀스 생성 메커니즘이 제대로 작동하지 않는 문제를 수정했습니다. (NEO-11115)
* 정수 유형 조정 키와 함께 사용자 지정 네임스페이스를 사용할 때 개인 정보 보호(GDPR) 요청이 작동하지 않는 문제를 해결했습니다. (NEO-11123)
* 를 사용할 때 발생할 수 있는 오류를 수정했습니다. **[!UICONTROL Distribution of values]** 옵션 **[!UICONTROL Query]** 워크플로우 활동. (NEO-10958)
* 마케팅 인스턴스에서 상호 작용 인스턴스로 오퍼 공간을 동기화할 때 발생하는 문제를 수정했습니다. (NEO-11162)
* 업그레이드 후 긴 이름 인덱스 관리 개선

### 릴리스 18.4.2 - 빌드 8932{#release-18-4-2-build-8932}

2018년 5월 22일

**개선 사항**

* Windows Server 업데이트가 제대로 작동하지 않는 문제를 해결했습니다.
* 에서 문제가 해결되었습니다. **[!UICONTROL Survey Result]** XML에 저장된 데이터를 사용할 때 활동을 클릭합니다. 보고서가 잘못 표시되었습니다. (NEO-10816)
* 바운스 메일 서버를 사용할 때 inMail 프로세스에서 발생할 수 있는 성능 문제를 수정했습니다. (NEO-10641)
* 1000개 이상의 스키마를 업그레이드할 때 발생할 수 있는 데이터베이스 업그레이드 문제를 해결했습니다.

### 릴리스 18.4.1 - 빌드 8931{#release-18-4-build-8931}

2018년 4월 24일

**새로운 기능**

<table> 
 <thead> 
  <tr> 
   <th> 기능<br /> </th> 
   <th> 설명<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 유럽 연합 개인 정보 보호 규정(GDPR)<br /> </td> 
   <td> <p>GDPR은 2018년 5월 25일부터 시행된 데이터 보호 요구 사항을 통합하고 현대화한 유럽 연합의 새로운 개인 정보 보호법입니다. GDPR은 유럽 연합에 거주하는 데이터 주체의 데이터를 보유하고 있는 Adobe Campaign 고객에게 적용됩니다.</p> <p>Adobe Campaign에서 이미 사용 가능한 개인 정보 보호 기능(동의 관리, 데이터 보존 설정 및 사용자 역할 포함) 외에도 Adobe는 데이터 프로세서로서의 Adobe의 역할을 통해 특정 GDPR 요청에 대해 데이터 컨트롤러로서의 준비를 용이하게 하기 위해 추가 기능을 포함하고 있습니다.</p> 
    <ul> 
     <li> <p>액세스 권한: 데이터 주체는 Adobe Campaign에 저장된 데이터를 포함하여 데이터 통제자가 캡처하는 개인 데이터의 사본을 받을 수 있도록 허용합니다.</p> </li> 
     <li> <p>삭제 권한: 데이터 주체는 데이터 통제자가 개인 데이터를 캡처하여 삭제하도록 할 수 있으며, 이는 잠재적으로 Adobe Campaign에 저장된 데이터를 포함할 수 있습니다.</p> </li> 
    </ul> 자세한 내용은 <a href="https://helpx.adobe.com/kr/campaign/kb/acc-privacy.html">세부 설명서</a>를 참조하세요.<br /> </td> 
  </tr> 
  <tr> 
   <td> 활성 프로필<br /> </td> 
   <td> <p>이제 Adobe Campaign은 전용 워크플로우를 통해 매월 업데이트되는 활성 프로필 목록을 제공합니다.</p> <p>자세한 내용은 <a href="../../platform/using/about-profiles.md#active-profiles">세부 설명서</a>를 참조하세요.</p> </td> 
  </tr> 
  <tr> 
   <td> Android 푸시 커넥터 개선 사항<br /> </td> 
   <td> <p>Android 커넥터가 향상된 처리량을 지원합니다. </p> <p>자세한 내용은 <a href="../../delivery/using/configuring-the-mobile-application.md">세부 설명서</a>를 참조하세요.</p> </td> 
  </tr> 
 </tbody> 
</table>

**향상된 보안 기능**

* 이제 인증되지 않은 사용자의 잠재적 공격을 방지하기 위해 외부 엔터티 확장이 비활성화되었습니다. (NEO-10173)
* 표준 사용자가 애플리케이션 액세스 URL, LDAP 설정 등과 같은 인스턴스 구성 매개 변수를 변경하지 못하도록 하기 위해 권한이 강화되었습니다. (NEO-10171)
* 스택 추적을 통해 중요한 정보를 표시할 수 있는 문제를 해결했습니다. 이제 오류 세부 사항이 외부 네트워크에서 액세스할 수 없는 위치로 백 엔드에 기록됩니다. (NEO-10176)
* 표준 사용자가 관리자의 업로드된 문서 및/또는 내보낸 패키지를 볼 수 없도록 하는 권한이 강화되었습니다. (NEO-10170)

**개선 사항**

* **LINE 채널 - 아키텍처 향상**: Adobe Campaign의 다른 모든 채널과 마찬가지로, 이제 모든 배포 유형에서 LINE 채널이 지원됩니다. 호스팅, 하이브리드 및 온-프레미스.
* **시퀀스 자동 생성**: 대량의 개체가 있는 Campaign 인스턴스의 수명을 늘리기 위해 ID 생성 메커니즘이 개선되었습니다.

**기타 변경 사항**

* 명령줄을 사용하여 패키지를 가져올 때 새 모드를 사용할 수 있으므로 순환 종속성이 가능합니다(큰 패키지에는 권장되지 않음). 자세한 내용은 &#39;기술 진화&#39; 섹션을 참조하십시오. (NEO-8979)
* teradata에서 많은 양의 데이터 로드를 위한 성능이 개선되고 로그에서 처리된 데이터의 올바른 값이 표시되지 않는 문제가 해결되었습니다. (NEO-10429)
* 이제 Audience Manager에서 대상을 가져오는 작업이 분할 파일에서 작동합니다. 이전에는 importSharedAudience 기술 워크플로우에서 세그먼트의 마지막 파일만 가져왔습니다. (NEO-10156)
* Windows에서 Campaign 서버의 기본 설치 경로가 변경되었습니다. 64비트 버전 설정을 시작할 때 기본 설치 경로는 다음과 같습니다. **C:\Program Files\Adobe\Adobe Campaign Classic v7** 대신 **C:\Program Files (x86)\Adobe\Adobe Campaign Classic v7**
* 더 많은 도메인을 포함하고 처리량을 최적화하도록 기본 MX 규칙이 향상되었습니다.
* 배포 마법사 SOAP 호출에 대한 액세스 제한 적용(xtk:serverOptions#SaveOptions).
* weka.jar 오래된 라이브러리가 제거되고 보안 최적화를 위해 OpenSSL 라이브러리가 업데이트되었습니다.
* 인스턴스 성능을 보호하기 위해 청구 기술 워크플로우가 개선되었습니다.
* 관리자가 모든 연산자의 암호를 설정하거나 재설정할 수 있는 기능이 복원되었습니다. 이렇게 하려면 연산자를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Actions]** > **[!UICONTROL Reset password]** 연산자의 새 암호를 설정합니다. 운영자가 처음 다시 연결할 때 암호를 변경하는 것이 좋습니다. 자세한 내용은 [세부 설명서](../../production/using/lost-password.md)를 참조하세요.
* Adobe Target의 새로운 멀티 테넌트 기능을 지원하기 위해 이제 Target과 통합을 위한 옵션 및 외부 계정을 구성할 때 새로운 &quot;at_property&quot; 매개 변수를 URL에 추가할 수 있습니다. 이 매개 변수에 사용할 값은 Adobe Target에서 찾을 수 있으며, Target 호출을 수행할 때 Campaign에서 사용합니다. 자세한 내용은 [세부 설명서](../../integrations/using/inserting-a-dynamic-image.md)를 참조하세요.
* 이제 Adobe Target에서 제공하는 이미지를 클릭하면 열 기본 랜딩 페이지를 지정할 수 있습니다. 이전에는 해당 이미지를 클릭하면 대신 이메일을 만들 때 기본 이미지 세트가 표시되었습니다. 자세한 내용은 [세부 설명서](../../integrations/using/inserting-a-dynamic-image.md)를 참조하세요.
* 추가됨 **SMPP 추적 사용** 추적 출력을 강제 적용하기 위한 외부 계정의 확인란 자세한 내용은 [세부 설명서](../../delivery/using/sms-set-up.md#creating-an-smpp-external-account)를 참조하세요.

**기술 진화**

queryDef

&quot;orderBy&quot; 절에 대해 queryDef가 수정되었습니다. 변경 전에 쿼리된 테이블의 기본 키가 &quot;orderBy&quot; 절에 암시적으로 추가됩니다. 일부 데이터베이스 엔진에서(최소한 postgresql) 인덱스를 사용할 수 없습니다(orderBy 절의 모든 필드는 동일한 인덱스로 적용되어야 함). 이 동작에 종속되어 있는 경우 &quot;orderBy&quot; 절에 기본 키를 명시적으로 추가해야 합니다.

예를 들어 다음 쿼리가 있는 경우

```
<queryDef operation="select" schema="xtk:job" startPath="/" xtkschema="xtk:queryDef">
  <select>
     <node expr="@id"/>
   </select>
   <orderBy>
     <node expr="@logDate"/>
   </orderBy>
</queryDef>`
```

(18.4 변경 전)으로 암시적으로 전달됩니다.

```
<queryDef operation="select" schema="xtk:job" startPath="/" xtkschema="xtk:queryDef">
  <select>
     <node expr="@id"/>
   </select>
   <orderBy>
      <node expr="@logDate"/>
      <node expr="@id"/> <!-- implicitly added before 18.4, you can add it manually on your query, if you relied on this implicit order clauses --!>
   </orderBy>
</queryDef>
```

urlEncode 함수

&#39;urlEncode&#39; JavaScript 함수가 ASCII가 아닌 문자에 대해 제대로 작동하지 않았습니다. 수정된 내용이 적용되었으며 이제 모든 유니코드 문자(일본어 문자 포함)와 함께 작동해야 합니다. 비 ASCII 문자로 &#39;urlEncode&#39; 동작을 사용하는 경우 코드를 조정해야 합니다.

패키지 가져오기 새 모드

명령줄을 사용하여 패키지를 가져올 때 새 모드를 사용할 수 있으므로 순환 종속성이 가능합니다(큰 패키지에는 권장되지 않음). 기존 기능은 그대로 유지됩니다. 순환 종속성이 있는 패키지의 경우 새 플래그 **-usejs** 이(가) 명령줄 패키지 가져오기에 추가되었습니다. 실행되면 인터페이스에서 패키지 가져오기를 수행할 때와 마찬가지로 JSEngine을 사용합니다.

```
nlserver package -instance:fresh -import:sup-packInstallTest.xml -verbose -usejs
```

**패치**

* 게재 및 추적 로그를 Adobe Campaign Standard에서 Adobe Campaign Classic으로 복제할 때 발생하는 동기화 문제를 수정했습니다. (NEO-10023)
* 빠른 로드 작업 실패 후 ETL 워크플로우가 다시 시작되는 경우 Teradata의 오류 및 로그 테이블 처리 문제가 해결되었습니다. 이제 워크플로우가 다시 시작될 때마다 오류 및 로그 테이블이 제대로 삭제됩니다. (NEO-10672)
* FDA 패키지가 설치된 경우 Hive 패키지(Hadoop에 필요)를 자동으로 설치하도록 업그레이드 후 문제를 해결했습니다. (NEO-10592)
* 잘못된 도메인을 **정의되지 않음** 오류가 발생했습니다. (NEO-10248)
* Android 푸시 게재를 전송할 때 deliveryLogStats 표에 중복 로그가 발생하는 문제를 해결했습니다. (NEO-10234)
* 바코드 스캐너에서 특정 바코드 형식을 읽을 수 없는 문제를 해결했습니다. (NEO-10125)
* 비 ASCII 문자를 사용할 때 &#39;urlEncode&#39; JavaScript 함수 문제를 해결했습니다. 자세한 내용은 &#39;기술 진화&#39; 섹션을 참조하십시오. (NEO-10123)
* teradata 데이터베이스에서 sha256 함수를 포함하는 쿼리를 실행할 때 발생하는 문제가 해결되었습니다. (NEO-10119)
* 매우 큰 SalesForce 테이블을 사용할 때 SalesForce 활동에서 발생할 수 있는 워크플로우 메모리 오류를 수정했습니다. (NEO-9900)
* Adobe Analytics 도구에서 **보완 생성** FDA를 사용할 때 워크플로우 활동 타깃팅의 옵션을 선택합니다. (NEO-9878)
* 로 이어질 수 있는 문제를 수정했습니다. **처리됨** 및 **성공** 중간 소싱을 사용할 때 마케팅 인스턴스에서 지표가 업데이트되지 않습니다. (NEO-9454)
* 플랫폼에서 총 1만 개 이상의 오퍼가 총 10만 개 이상인 경우 상호 작용 비제안 규칙이 수정되었습니다(NEO-9352).
* XML 외부 파일을 사용할 때 게재 대상을 지정할 수 없는 문제를 해결했습니다. (NEO-9312)
* 오퍼에서 가설을 실행하고 제안 상태를 업데이트할 때 워크플로우 오류가 발생하는 문제를 수정했습니다. (NEO-9304)
* Android 게재 매핑의 속성을 기반으로 압력 규칙을 사용할 때 게재 분석 중에 발생하는 오류를 수정했습니다. (NEO-9202)
* 수신자 목록의 열을 정렬할 때 성능 문제가 발생하는 문제를 해결했습니다. queryDef 수정에 대한 자세한 내용은 아래의 &#39;기술 진화&#39; 섹션을 참조하십시오. (NEO-9042)
* 특히 Federated ID 로그인 유형을 사용하는 경우 승인 이메일의 링크가 잘못된 로그인 URL을 가리킬 수 있는 문제를 수정했습니다. (NEO-9011)
* 특정 시간대에 대한 보고서의 날짜 선택기에 잘못된 날짜가 표시되는 문제를 해결했습니다. (NEO-9007)
* FDA SQL 데이터베이스를 사용할 때 아웃바운드 타겟을 볼 수 없는 문제를 수정했습니다. (NEO-8924)
* MS Dynamics CRM 커넥터에서 첫 7일 동안 데이터를 가져오지 못하는 문제를 해결했습니다. (NEO-8803)
* 사용자가 국제 문자를 포함하지 못하게 하는 Analytics 통합 오류를 수정했습니다. (NEO-8719)
* 적절한 권한 없이 워크플로우 편집을 활성화할 수 있는 문제를 해결했습니다. (NEO-8708)
* 하이브리드 아키텍처에서 메시지 센터를 사용하여 연결 감소 또는 연결 손실(시간 초과)을 초래할 수 있는 HTTP를 통한 FDA 문제를 수정했습니다. (NEO-8438)
* 음수 ID에 대한 증분 쿼리 활동에서 발생하는 워크플로우 오류를 수정했습니다. (NEO-8229)
* 특정 화면에서 이중 스크롤 막대를 표시할 수 있는 문제를 수정했습니다. (NEO-8208)
* 데이터베이스 구조 업데이트 마법사를 실행할 때 오류 메시지가 표시되는 문제를 해결했습니다. PostUpgrade는 이름이 30보다 긴 인덱스의 이름 변경을 실행합니다. 큰 테이블의 경우 색인 교체에는 시간이 소요됩니다. (NEO-7983)
* 추적 로그가 메시지 센터 실행 인스턴스에서 제어 인스턴스로 올바르게 동기화되지 않는 문제를 수정했습니다. (NEO-7286)
* 오퍼 보강 활동의 성능 문제를 수정했습니다. (NEO-7263)
* FDA를 통해 Redshift 데이터베이스를 쿼리할 때 DaysAgo 함수를 사용할 수 없는 문제를 해결했습니다. (NEO-7099)
* 데이터 보강 유사 워크플로우 활동에서 색인 생성을 방지하는 데이터 관리의 회귀 문제를 해결했습니다.
* 제목과 함께 외부 리소스를 만들 때 발생할 수 있는 문제를 @id
* FTP 서버를 통해 Zip 파일을 업로드하거나 파일 이름에 와일드카드가 있는 파일을 업로드할 때 발생할 수 있는 문제를 수정했습니다.
* Campaign Standard으로 생성된 외부 사용자 지정 리소스의 긴 기본 유형 열거형 문제를 해결했습니다.
* 공급자와의 연결에 실패하여 SMS 손실이 발생하는 경우에도 SMS가 전송될 수 있는 문제를 해결했습니다.
* SMTP 연결이 무기한으로 중단되는 오류가 해결되었습니다.
* LINE 매핑을 사용할 때 또는 필터링 및 타깃팅 스키마가 다를 때 메시지를 준비하는 동안 압력 유형 분류 규칙 문제를 해결했습니다.
