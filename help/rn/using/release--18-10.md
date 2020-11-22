---
solution: Campaign Classic
product: campaign
title: 릴리스 18.10
description: 릴리스 18.10
audience: rns
content-type: reference
topic-tags: latest-release-notes
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '2366'
ht-degree: 7%

---


# 릴리스 18.10{#release-18-10}

## 릴리스 18.10.6 - 빌드 8985{#release-18-10-6-build-8985}

2019년 7월 12일

**개선 사항**

* 이제 가져오기 작업 과정 동안 Microsoft Dynamics에서 만든 더미 레코드를 삭제할 수 있습니다.
* 파일 액세스가 거부되었을 때 루프에서 오류를 기록할 수 있는 파일 수집 워크플로우 작업의 문제를 수정했습니다. (NEO-12085)
* 열려 있는 배달 표시기에 대한 사용자 활동과 추적 보고서 간의 보고가 불일치하는 문제를 해결했습니다. (NEO-11742)
* 내부 계정을 사용할 때 보안 영역 패키지를 실행하기 위한 권한이 개선되었습니다.
* 집계 로그에 오류가 발생하던 문제를 수정했습니다. (NEO-8978)

## 릴리스 18.10.5 - 빌드 8984{#release-18-10-5-build-8984}

2019년 4월 23일

**개선 사항**

* 동시 분석/전송(동시에 두 개의 배달이 분석된 경우)에 배달 분석이 실패하는 SQL 교착 상태 문제를 해결했습니다. (NEO-13026)
* 누락된 데이터 문제를 해결하기 위해 워크플로우 히트맵에서 10,000개의 레코드 제한을 제거했습니다. (NEO-12329)
* 강화된 워크플로우 활동에서 &quot;기본 세트에 모든 추가 데이터 유지&quot; 옵션을 사용할 때 발생하는 문제가 해결되었습니다. (NEO-13291)

## 릴리스 18.10.4 - 빌드 8983{#release-18-10-4-build-8983}

2019년 4월 15일

**개선 사항**

* 트랜잭션 메시지에 대한 지표 추적 프로세스의 문제를 수정했습니다. (NEO-12529, NEO-12581)
* 일부 콜백이 완료될 때까지 기다리지 않던 HTTPRequest API 관련 문제를 수정했습니다. (NEO-12628)
* 배달 전송을 최적화하기 위해 쿠폰 임시 테이블에 인덱스가 추가되었습니다. (NEO-12437)
* 일본어(.JP) 도메인에서 받는 사람을 대상으로 하는 메시지를 분석할 때 발생하는 문제를 수정했습니다. (NEO-12246)
* 이제 Analytics 통합에서 % 문자가 있는 AAM 세그먼트 데이터를 검색할 수 있습니다. (NEO-12025)
* HTTP2를 사용하여 푸시 알림을 전송할 때 발생하는 Tomcat 충돌 문제가 해결되었습니다. (NEO-12701)

## 릴리스 18.10.3 - 빌드 8981{#release-18-10-3-build-8981}

2019년 1월 29일

>[!CAUTION]
>
>이 건물은 회수되었다. 최신 빌드 [로](../../production/using/build-upgrade.md) 업그레이드하거나 [Adobe 고객 지원 센터에 문의하십시오](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**개선 사항**

* s3 파일 전송 워크플로우 활동 문제를 수정했습니다. (NEO-12473)
* 실패 시 발생할 수 있는 추적 워크플로우 문제를 해결했습니다. (NEO-12520)
* IMS 로그인 문제가 해결되었습니다.
* 큰 오퍼 ID를 사용할 때 트랜잭션 메시징에서 미리 보기 및 컨텐츠 승인 문제가 해결되었습니다.
* 중간 소싱(배달 카운터) 워크플로우의 문제를 수정했습니다.
* NmsRecipient에서 새 색인을 삭제한 데이터베이스 구조 업데이트 문제를 수정했습니다.
* 게재의 기본 대상에 대해 외부 파일에서 정의 옵션을 사용할 때 발생할 수 있는 콘솔 충돌을 해결했습니다. (NEO-12349)
* 여러 InMail 충돌을 수정했습니다.
* 데이터 업데이트 워크플로우 활동을 사용하여 FDA Teradata 데이터베이스에 저장된 레코드를 삭제할 때 발생하는 문제를 수정했습니다.
* 비밀 키 관리의 불일치 문제가 해결되었습니다.
* 필드를 다음과 같이 입력할 때 데이터 연계 강화 활동 문제가 해결되었습니다.xml=true 및 calculated=true
* 모바일 애플리케이션에서 푸시 알림을 전송할 때 발생하는 문자 이스케이프 문제가 해결되었습니다.
* 중간 소싱 외부 계정에서 FDA에서 SOAP 동기화 방법으로 전환할 수 없는 문제를 해결했습니다.

## 릴리스 18.10.2 - 빌드 8978{#release-18-10-2-build-8978}

2018년 12월 6일

>[!CAUTION]
>
>이 건물은 회수되었다. 최신 빌드 [로](../../production/using/build-upgrade.md) 업그레이드하거나 [Adobe 고객 지원 센터에 문의하십시오](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**개선 사항**

* FDA에서 MySQL을 사용하여 워크플로우를 실행할 때 발생하는 다양한 문제가 해결되었습니다. (NEO-11652)
* 푸시 알림을 전송할 때 발생하는 성능 문제가 해결되었습니다. (NEO-11787)
* 배달에서 시드 주소를 사용할 때 발생하는 ID 소모 문제가 해결되었습니다. (NEO-11842)
* 복잡한 워크플로우를 사용할 때 발생할 수 있는 클라이언트 고정 문제를 해결했습니다. (NEO-11847)
* 1:N 링크로 값 배포를 사용할 때의 표시 문제를 수정했습니다. (NEO-11820)
* 워크플로우 히트맵의 Oracle 오류를 수정했습니다.
* 농축 활동에 제안 사항을 추가할 때 문제가 해결되었습니다.
* SQL 데이터 관리 연결 문제를 수정했습니다.
* 네거티브 ID의 경우 임시 워크플로우 테이블 이름을 생성하는 문제를 수정했습니다.
* 워크플로우 HeatMap에서 워크플로우 지속 시간 계산 문제를 수정했습니다.


## 릴리스 18.10 - 빌드 8977{#release-18-10-build-8977}

2018년 11월 5일

>[!CAUTION]
>
>이 건물은 회수되었다. 최신 빌드 [로](../../production/using/build-upgrade.md) 업그레이드하거나 [Adobe 고객 지원 센터에 문의하십시오](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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
   <td> Push notification improvements<br /> </td> 
   <td> Adobe Campaign에서 푸시 알림에 대해 많은 개선 사항이 구현되었습니다.<br /> 
    <ul> 
     <li> <p>iOS에서 자동 알림 추적 </p> </li> 
     <li> <p>iOS의 등록 호출에 대한 피드백 구현</p> </li> 
     <li> <p>iOS 전달 준비 속도 개선</p> </li> 
    </ul> <p>Google의 GCM 감가 상각의 일부로 Android V2 커넥터는 이제 FCM 서버에만 연결을 허용합니다.</p><p>자세한 내용은 <a href="../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md">세부 설명서</a>를 참조하십시오. FCM으로 업그레이드하는 방법은 이 <a href="https://helpx.adobe.com/kr/campaign/kb/migrate-to-fcm.html">문서에 자세히 설명되어 있습니다</a>. </p> </td> 
  </tr> 
  <tr> 
   <td> SQL 데이터 관리 활동<br /> </td> 
   <td> <p>새로운 데이터 관리 워크플로우 활동이 추가되었습니다. SQL <strong>데이터 관리</strong> 활동을 사용하면 자체 SQL 스크립트를 작성하거나 복사하여 작업 테이블을 만들고 채울 수 있습니다(FDA에만 해당). </p> <p>자세한 내용은 <a href="../../workflow/using/sql-data-management.md">세부 설명서</a>를 참조하십시오.</p></td> 
  </tr> 
  <tr> 
   <td> 워크플로우 모니터링<br /> </td> 
   <td> <p>새로운 Adobe Campaign 워크플로우 HeatMap을 통해 플랫폼 관리자는 모든 동시 워크플로우를 그래픽으로 표현하므로 인스턴스의 로드를 모니터링하고 워크플로우를 적절하게 계획할 수 있습니다.</p> <p>자세한 내용은 <a href="../../workflow/using/heatmap.md">세부 설명서</a>를 참조하십시오.</p> <p>Workflow HeatMap 패키지는 8977 이전(빌드 8700 시작) 빌드에 대해서도 On-Demand 방식으로 사용할 수 있습니다. 요청 및 설치에 대한 자세한 내용은 <a href="https://helpx.adobe.com/campaign/kb/install-workflow-heatmap-package.html">이 페이지를 참조하십시오</a>.</p> </td> 
  </tr> 
 </tbody> 
</table>

**향상된 보안 기능**

* SSRF(Server Side Request 위조) 공격 및 DoS(서비스 거부) 공격에 취약할 수 있는 보안 문제를 수정했습니다. (NEO-11453)
* 컨텐츠(리디렉션, 미러 페이지, 설문 조사 등 추적) 이제 X-Robots-Tag가 있는 Campaign에서 제공됩니다.캐시 헤더가 없습니다. 이렇게 하면 인터넷 검색 엔진별로 이 콘텐츠를 인덱싱할 수 없습니다. (NEO-11101)
* 구독 API의 XTK 삽입 문제를 수정했습니다(nms:subscription:Unsubscribe 및 nms:subscription:Subscribe).
* 구독 취소 웹 응용 프로그램의 XTK 삽입 문제를 해결했습니다.
* 일부 SMS 로그에 안전하게 표시되는 암호를 제거했습니다.

**개선 사항**

* 이제 [전용 페이지](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html)에서 Campaign Classic API를 사용할 수 있습니다. jsapi.chm 파일을 사용하는 경우 이제 새로운 온라인 버전을 참조해야 합니다.
* 이제 PostgreSQL 10, Debian 9 및 Teradata 16.20이 지원됩니다. [호환성 매트릭스](https://helpx.adobe.com/kr/campaign/kb/compatibility-matrix.html)를 참조하십시오.
* 이제 SFTP 연결을 만들 때 프록시 인증을 사용할 수 있습니다. For more information, refer to the [detailed documentation](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration) (NEO-9868)
* 이제 **DM 배달 템플릿을 사용하여 단일 배달을 만들 때 배달 속성에서 날짜 계산 공식** 옵션을 사용할 수 있습니다. (NEO-9792)
* 쿠키 추적 및 웹 응용 프로그램에 대한 도메인 이름 관리가 개선되었습니다. 자세한 내용은 아래의 &#39;기술 발전&#39; 섹션을 참조하십시오.
* 전달 또는 랜딩 페이지에서 Adobe Marketing Cloud 공유 에셋 가져오기가 보안 및 성능 측면에서 개선되었습니다.
* 모바일 채널 외부 계정에서 자세한 SMPP 추적이 로그 파일에서 활성화되도록 새 확인란을 사용할 수 있으므로 이 출력에 Adobe Campaign 인터페이스에서 직접 액세스할 수 있습니다.
* 이제 브로드캐스팅에는 최대 연결 수와 시간당 최대 메시지 수 사이에 차이가 있습니다. When the limits are reached, it is possible to know why the throughput is limited. 이전에는, 동일한 메시지(&#39;할당량 충족&#39;)가 두 경우 모두에 적용되었습니다.
* 이제 풀에서 연결을 가져올 때 실행할 SQL 스크립트를 지정할 수 있습니다. 이 스크립트를 사용하여 기본 스키마를 설정할 수 있습니다. 이 스크립트는 쿼리 배너 후에 적용됩니다. (NEO-11256)
* Campaign SDK는 더 이상 PII 규정을 준수하기 위해 사용자 ID를 저장하지 않습니다. 이제 데이터가 해시로 저장됩니다.
* 패키지 내보내기 XML 파일을 가져올 때 이제 Campaign은 인코딩이 파일에서 명시적으로 선언된 경우에도 파일에 BOM이 있음을 지원합니다.

**기술 진화**

클라이언트 및 서버 업그레이드

>[!CAUTION]
>
>18.10으로 업데이트된 서버가 있는 경우 서버에 액세스하려면 18.10 클라이언트를 사용해야 합니다. 18.10 클라이언트는 이전 서버 버전에 연결할 수 있습니다.

도메인 이름 관리

쿠키 추적 및 웹 응용 프로그램에 대한 도메인 이름 관리가 개선되었습니다.

이제 모든 두 글자의 두 번째 수준 도메인 이름이 기본적으로 지원됩니다(예: .aa.com). 보다 복잡한 도메인 이름(예: .com.au와 같은 3자 두 번째 수준 도메인)의 경우 리디렉션 태그 아래의 serverConf의 **cookieDomains** 옵션(선택 태그)에 추가해야 합니다. 다음은 한 예입니다.

```
<redirection cookiedomain="http://toureiffel.paris">
```

향상된 색인

NmsRecipient의 인덱스가 다시 수정되었습니다. 이 표를 사용하는 쿼리의 성능이 향상되어야 합니다. NmsRecipient의 확장을 수행한 경우 새 색인을 복제하는 인덱스가 없는지(데이터베이스 서버의 공간 사용을 최소화하기) 확인할 수 있습니다. (NEO-8228)

UTF-8 데이터 정렬을 사용할 때 이제 &quot;LIKE &#39;string%&#39;(또는 &quot;다음으로 시작&quot;) 작업을 최적화하는 인덱스를 만들 수 있습니다. 동일한 열에서 다른 작업을 수행하는 경우(예: 정렬 기준 또는 조인) 다른 표준 인덱스가 필요합니다. 스키마 쪽에서는 인덱스 정의에 indexOption=&quot;searchFromStart&quot;를 추가하여 이 작업을 수행합니다(표준 트리 인덱스 대신 varchar_pattern_ops 인덱스를 생성합니다). 예(NmsRecipient):

```
<dbindex name="email2"> <!-- optimize order by/join (and startWith if not PostgreSql with an UTF-8 collation) operations -->
  <keyfield xpath="@email"/>
</dbindex>
<dbindex name="email3" indexOption="searchFromStart"><!-- optimize startsWith operation on PostgreSql when a UTF-8 collation is used; create no index in other cases-->
  <keyfield xpath="@email" />
</dbindex>
```

새 인덱스가 NmsRtEvent 및 NmsEventHisto(&quot;예약됨&quot; 열)에 추가되었으므로 해당 양식의 표시 시간이 개선됩니다(NEO-11738).

이러한 색인 변경 사항으로 인해 업그레이드 후 수행에 필요한 시간이 늘어날 수 있습니다.

**패치**

* 웹 다운로드 **워크플로우 활동** 파일의 다운로드를 방해하던 오류를 수정했습니다. (NEO-11105)
* 지표 및 캠페인 속성 **의 전송 작업 과정을 실패 상태(NEO-10820)로** 가끔 남겨 두는 오류를 수정했습니다.
* 워크플로우에서 목록 업데이트 활동을 실행한 후 만든 수신자 목록을 삭제하는 문제를 해결했습니다. (NEO-11696)
* 캠페인 달력(일본어 인스턴스)에서 한 달 전에 캠페인을 잘못 표시하던 문제를 수정했습니다. (NEO-11445)
* 배달 속성의 웹 분석 탭에 Analytics 구성이 표시되지 않던 문제를 수정했습니다. (NEO-11619)
* nms:배달 입력 양식을 편집하고 저장할 때 표시되는 오류를 수정했습니다. (NEO-10973)
* 파일 전송 활동이 포함된 워크플로우를 실행할 때 발생하는 외부 계정 구성 문제를 수정했습니다. (NEO-11012)
* zcat 함수를 사용하여 데이터 로드 활동에서 파일을 로드할 때 빈 줄을 반환하는 문제를 해결했습니다. (NEO-11273)
* 배달 분석 중에 중복된 확장 로그를 생성하는 문제를 수정했습니다. (NEO-11360)
* 워크플로우에서 농축활동 실행 후 외부 링크 키가 누락되어 배달이 실패하는 문제를 해결했습니다. (NEO-11537)
* 설치 경로에 특정 GB18030 중국어 문자가 포함되어 있을 때 Adobe Campaign을 제거하거나 복구할 수 없는 문제를 해결했습니다.
* 일부 추적 로그를 잘못된 배달에 연결하는 문제를 수정했습니다. (NEO-11412)
* 배달 로그의 일부가 예상보다 오래 대기 중인 상태로 남아 있는 문제를 해결했습니다. (NEO-11336)
* 게시에 쿠폰을 추가하기 위해 쿼리를 편집할 때 발생하는 오류가 수정되었습니다. (NEO-11037)
* 집계된 연산자를 선택한 것과 상관없이 차트가 항상 값의 합계를 계산하도록 하는 보고서의 문제를 해결했습니다. (NEO-10913)
* &quot;request.scheme&quot; 함수는 더 이상 사용되지 않으므로 JSAPI 설명서에서 제거되었습니다. (NEO-10828)
* 특정 시간대 구성을 가진 일부 사용자가 Adobe Campaign에 로그인하지 못했던 문제를 수정했습니다. (NEO-10712)
* 확장 일반 SMPP 커넥터를 사용하여 모바일 채널 외부 계정을 설정할 때 발생하는 문제가 해결되었습니다.수신기에 대해 다른 매개 변수를 사용하여 지정한 경우 송신기는 자체 매개 변수 대신 이러한 매개 변수를 잘못 사용하게 됩니다.
* 첫 번째 중재 후 배달이 계속 다시 계산되었기 때문에 압력 규칙에 대한 빈도를 설정할 때 예약된 배달이 실패했던 문제를 수정했습니다. (NEO-10016)
* 응용 프로그램 풀 재활용 프로세스(nlsrvmod.dll 라이브러리) 중에 IIS 웹 서버가 충돌하는 문제를 해결했습니다. (NEO-10862)
* 프로필 및 Target **** 화면에서 수신자를 검색하지 못하는 문제를 해결했습니다. (NEO-8228)
* 레코드 수가 많은 경우 이벤트 내역 폴더에 액세스할 때 시간 초과 오류가 발생하는 문제를 해결했습니다. (NEO-11738)
* LINE 배달 수신자가 &quot;접근 불가&quot;로 잘못 반환될 수 있는 문제가 해결되었습니다. (NEO-10833)
* oracle에서 추가 열이 있는 워크플로우 쿼리를 실행할 때 발생하는 문제가 해결되었습니다. (NEO-11615)
* 연결 풀에 닫힌 연결이 너무 오랫동안 유지되지 않도록 개선되었습니다. (NEO-11392)
* 타깃팅 워크플로우 활동(쿼리, 데이터 로드(RDBMS) 등)을 사용할 때 발생하는 문제가 해결되었습니다. UTF8 문자가 포함된 외부 Oracle 테이블에 FDA를 통해 연결(표 이름, 필드 이름 등) 또한 시스템에서 생성된 기본 제약 조건 이름의 기본 키 제약 조건을 포함합니다. (NEO-10714)
* 게재의 HTML 콘텐츠를 삭제하지 못하는 문제를 해결했습니다. (NEO-11327)
* 캠페인 실행 후 XML 및 CSV 파일을 DM으로 미리 보는 문제가 해결되었습니다. (NEO-11290)
* 데이터 연계 강화 워크플로우 활동에서 데이터를 정렬할 때 발생하는 문제가 해결되었습니다. (NEO-11394)
* 사용자 지정 보고서에서 데이터를 정렬할 때 발생하는 문제를 수정했습니다. (NEO-10896)
* teradata에서 useVault 설정을 사용할 때 오류가 발생하던 문제를 수정했습니다. (NEO-11399)
* 여러 쿼리 행을 삭제할 때 Adobe Campaign 클라이언트 콘솔이 중단되던 문제를 수정했습니다. (NEO-10744)
* 다이렉트 메일을 전달할 때 일부 경우 압력 규칙이 적용되지 않는 문제를 해결했습니다. (NEO-9004)
* 데이터 로드 활동을 사용하여 데이터 유형이 &#39;time&#39;인 열을 가져올 때 발생하는 문제를 수정했습니다.시간 구분 문자는 제거한 후에도 재설정됩니다. (NEO-10743)
* 반복 배달을 편집할 때 배달 속성의 실행 폴더 목록에 배달 폴더가 표시되지 않던 문제를 수정했습니다. (NEO-11094)
* 워크플로우에서 쿼리 활동의 결과 대상으로 200개 이상의 레코드를 표시하는 데 장애가 발생하던 문제를 수정했습니다. (NEO-11195)
* 1,000개 이상의 요소를 선택한 상태로 DELETE 쿼리를 실행하지 못했던 Oracle 문제가 해결되었습니다. (NEO-11171)
* Android 푸시 알림 전달의 추가 매개 변수에서 추적된 URL로 URL을 인코딩하는 문제를 해결했습니다. (NEO-11468)
* 매개 변수를 &#39;하루 간격&#39; 및 &#39;열기&#39;로 설정할 때 사용자 활동 보고서에서 발생하는 스크립트 오류가 수정되었습니다. (NEO-11655)
* 인증된 웹 프록시를 통해 중간 소싱 서버 또는 메시지 센터에 연결할 때 발생하던 문제를 수정했습니다. (NEO-11309)
* SQL 보기에 **따라 특정 스키마의 요소를 선택한 후 새 배달 컴포지션이 저장되었을 때 발생하는 Oracle 오류가 수정되었습니다**. (NEO-11682)
* 압축 해제 옵션을 사용하여 .csv를 포함하는 zip 파일을 처리할 때 잘못된 양수가 포함된 파일이 생성되던 문제를 수정했습니다.
* xtkjoblog가 이제 정리 중에 삭제됩니다.

