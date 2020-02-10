---
title: 릴리스 18.10
seo-title: 릴리스 18.10
description: 릴리스 18.10
seo-description: null
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 12f4237c34560257901ae210d4e22a7d152a795d

---


# 릴리스 18.10{#release-18-10}

## 릴리스 18.10.6 - 빌드 8985{#release-18-10-6-build-8985}

2019년 7월 12일

**향상된 기능**

* 이제 가져오기 작업 과정 동안 Microsoft Dynamics에서 만든 더미 레코드를 삭제할 수 있습니다.
* 파일 액세스가 거부될 때 루프에 오류를 기록할 수 있는 파일 수집 워크플로우 작업 문제를 수정했습니다. (NEO 파섹)
* 열려 있는 배달 표시기에 대한 사용자 활동 및 추적 보고서 간에 보고가 불일치하는 문제를 해결했습니다. (NEO 파섹)
* 내부 계정을 사용할 때 보안 영역 패키지를 실행하기 위한 권한이 개선되었습니다.
* 일치 로그 오류를 발생시킬 수 있는 문제를 수정했습니다. (NEO 파섹)

## 릴리스 18.10.5 - 빌드 8984{#release-18-10-5-build-8984}

2019년 4월 23일

**향상된 기능**

* 동시 분석/전송(동시에 두 개의 배달이 분석된 경우)의 경우 배달 분석이 실패하는 SQL 교착 상태 문제를 해결했습니다. (NEO 파섹)
* Workflow Heatmap에서 누락된 데이터 문제를 해결하기 위해 10,000개의 레코드 제한을 제거했습니다. (NEO 파섹)
* 보충 워크플로우 활동에서 &quot;기본 세트에 추가 데이터 모두 유지&quot; 옵션을 사용할 때 발생하는 문제가 해결되었습니다. (NEO 파섹)

## 릴리스 18.10.4 - 빌드 8983{#release-18-10-4-build-8983}

2019년 4월 15일

**향상된 기능**

* 트랜잭션 메시지에 대한 추적 표시기의 컴퓨팅 프로세스 문제를 수정했습니다. (NEO 파섹 12529, NEO 파섹 12581)
* 일부 콜백이 완료될 때까지 기다리지 않았던 HTTPRequest API 관련 문제를 수정했습니다. (NEO 파섹)
* 배달 전송을 최적화하기 위해 쿠폰 임시 테이블에 인덱스가 추가되었습니다. (NEO 파섹)
* 일본어(.JP) 도메인에 대해 타깃팅된 받는 사람을 분석할 때 발생하는 문제를 수정했습니다. (NEO 파섹)
* 이제 Analytics 통합에서 % 문자를 포함하는 AAM 세그먼트 데이터를 검색할 수 있습니다. (NEO 파섹)
* HTTP2를 사용하여 푸시 알림을 전송할 때 발생하는 Tomcat 충돌 문제가 해결되었습니다. (NEO 파섹

## 릴리스 18.10.3 - 빌드 8981{#release-18-10-3-build-8981}

2019년 1월 29일

>[!CAUTION]
>
>이 건물은 회수되었습니다. 최신 빌드로 [업그레이드하거나](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) 기술 지원에 [](https://support.neolane.net/)문의하십시오.

**향상된 기능**

* s3 파일 전송 워크플로우 활동 문제를 수정했습니다. (NEO 파섹)
* 실패 시 추적 워크플로우의 문제를 수정했습니다. (NEO 파섹)
* IMS 로그인 문제를 수정했습니다.
* 큰 오퍼 ID를 사용할 때 트랜잭션 메시징의 미리 보기 및 컨텐츠 승인 문제가 해결되었습니다.
* 중간 소싱(배달 카운터) 워크플로우의 문제를 수정했습니다.
* NmsRecipient에서 새 인덱스를 삭제한 데이터베이스 구조 업데이트 문제를 수정했습니다.
* 전달의 기본 대상에 대해 외부 파일에 정의 옵션을 사용할 때 발생할 수 있는 콘솔 충돌을 수정했습니다. (NEO 파섹)
* 여러 InMail 충돌을 수정했습니다.
* 데이터 업데이트 워크플로우 활동을 사용하여 FDA Teradata 데이터베이스에 저장된 레코드를 삭제할 때 발생하는 문제를 수정했습니다.
* 비밀 키 관리의 불일치 문제가 해결되었습니다.
* 필드를 다음과 같이 입력할 때 추가 활동 문제가 해결되었습니다.xml=true 및 calculated=true
* 모바일 애플리케이션에서 푸시 알림을 전송할 때 문자 이스케이프 문제가 해결되었습니다.
* Mid-Sourcing 외부 계정에서 FDA에서 SOAP 동기화 방법으로 전환할 수 없는 문제를 해결했습니다.

## 릴리스 18.10.2 - 빌드 8978{#release-18-10-2-build-8978}

2018년 12월 6일

>[!CAUTION]
>
>이 건물은 회수되었습니다. 최신 빌드로 [업그레이드하거나](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) 기술 지원에 [](https://support.neolane.net/)문의하십시오.

**향상된 기능**

* FDA에서 MySQL을 사용하여 워크플로우를 실행할 때 발생하는 다양한 문제가 해결되었습니다. (NEO 파섹
* 푸시 알림을 전송할 때 성능 문제가 해결되었습니다. (NEO 파섹)
* 배달에서 시드 주소를 사용할 때 ID 소모 문제가 해결되었습니다. (NEO 파섹
* 복잡한 워크플로우를 사용할 때 발생할 수 있는 클라이언트 고정 문제를 해결했습니다. (NEO 파섹)
* 1:N 링크와 함께 값 배포를 사용할 때의 표시 문제를 수정했습니다. (NEO 파섹)
* 워크플로우 히트맵의 Oracle 오류를 수정했습니다.
* 농축 활동에 제안 사항을 추가할 때 문제가 해결되었습니다.
* SQL 데이터 관리 연결 문제를 수정했습니다.
* 음수 ID의 경우 임시 워크플로우 테이블 이름을 생성하는 문제를 수정했습니다.
* Workflow HeatMap의 워크플로우 지속 시간 계산 문제를 수정했습니다.


## 릴리스 18.10 - 빌드 8977{#release-18-10-build-8977}

2018년 11월 5일

>[!CAUTION]
>
>이 건물은 회수되었습니다. 최신 빌드로 [업그레이드하거나](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) 기술 지원에 [](https://support.neolane.net/)문의하십시오.

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
   <td> 향상된 푸시 알림<br /> </td> 
   <td> Adobe Campaign의 푸시 알림에 대해 많은 개선 사항이 구현되었습니다.<br /> 
    <ul> 
     <li> <p>iOS에서 자동 알림 추적 </p> </li> 
     <li> <p>iOS의 등록 호출에 대한 피드백 구현</p> </li> 
     <li> <p>iOS 전달 준비 속도 향상</p> </li> 
    </ul> <p>Google의 GCM 감가 상각의 일부로 Android V2 커넥터는 이제 FCM 서버에만 연결을 허용합니다.</p><p>자세한 내용은 <a href="../../delivery/using/setting-up-mobile-app-channel.md#integrating-campaign-sdk-into-the-mobile-application">자세한 설명서를</a>참조하십시오. FCM으로의 수동 업그레이드는 이 <a href="https://helpx.adobe.com/campaign/kb/migrate-to-fcm.html">문서에</a>자세히 설명되어 있습니다. </p> </td> 
  </tr> 
  <tr> 
   <td> SQL 데이터 관리 활동<br /> </td> 
   <td> <p>새로운 데이터 관리 워크플로우 활동이 추가되었습니다. SQL <strong>데이터 관리</strong> 활동을 사용하면 SQL 스크립트를 직접 작성하거나 복사하여 작업 테이블을 만들고 채울 수 있습니다(FDA에만 해당). </p> <p>자세한 내용은 <a href="../../workflow/using/sql-data-management.md">자세한 설명서를</a>참조하십시오.</p></td> 
  </tr> 
  <tr> 
   <td> 워크플로우 모니터링<br /> </td> 
   <td> <p>새로운 Adobe Campaign Workflow HeatMap을 사용하면 플랫폼 관리자는 모든 동시 작업 과정을 그래픽으로 빠르게 표시하여 인스턴스의 로드를 모니터링하고 그에 따라 워크플로우를 계획할 수 있습니다.</p> <p>자세한 내용은 <a href="../../workflow/using/heatmap.md">자세한 설명서를</a>참조하십시오.</p> <p>또한 Workflow HeatMap 패키지는 8977 이전 빌드(빌드 8700 시작)에 대한 요청 시 사용할 수 있습니다. 요청 및 설치에 대한 자세한 내용은 <a href="https://helpx.adobe.com/campaign/kb/install-workflow-heatmap-package.html">이 페이지를</a>참조하십시오.</p> </td> 
  </tr> 
 </tbody> 
</table>

**향상된 보안 기능**

* SSRF(Server Side Request 위조) 공격 및 DoS(서비스 거부) 공격에 취약할 수 있는 보안 문제를 수정했습니다. (NEO 파섹
* 컨텐츠(리디렉션, 미러 페이지, 설문 조사 등 추적) Adobe Campaign에서 X-Robots-Tag를 사용할 수 있습니다.캐시 헤더가 없습니다. 이렇게 하면 인터넷 검색 엔진으로 이 콘텐츠를 인덱싱할 수 없습니다. (NEO 파섹
* 구독 API의 XTK 삽입 문제를 수정했습니다(nms:subscription:Subscribe 및 nms:Subscription:Subscribe).
* 구독 취소 웹 응용 프로그램에서 XTK 삽입 문제를 해결했습니다.
* 일부 SMS 로그에 안전하게 표시된 암호를 제거했습니다.

**향상된 기능**

* 이제 [전용 페이지에서](https://docs.campaign.adobe.com/doc/AC/en/jsapi/index.html)Campaign Classic API를 사용할 수 있습니다. jsapi.chm 파일을 사용하는 경우 이제 새로운 온라인 버전을 참조하십시오.
* PostgreSQL 10, Debian 9 및 Teradata 16.20이 지원됩니다. 호환성 [매트릭스를](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)참조하십시오.
* 이제 SFTP 연결을 만들 때 프록시 인증을 사용할 수 있습니다. 자세한 내용은 [자세한 설명서를](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration) 참조하십시오(NEO-9868).
* 이제 **DM 배달 템플릿을 사용하여 단일 배달을 만들 때 배달 속성에서 날짜 계산 공식** 옵션을 사용할 수 있습니다. (NEO 파섹)
* 쿠키 추적 및 웹 응용 프로그램에 대한 도메인 이름 관리가 향상되었습니다. 자세한 내용은 아래의 &#39;기술 발전&#39; 섹션을 참조하십시오.
* 전달 또는 랜딩 페이지에서 Adobe Marketing Cloud 공유 에셋을 가져오는 기능이 보안 및 성능 측면에서 개선되었습니다.
* 모바일 채널 외부 계정에서 새로운 확인란을 사용하여 로그 파일에서 자세한 SMPP 추적을 활성화할 수 있으므로 이 출력을 Adobe Campaign 인터페이스에서 직접 액세스할 수 있습니다.
* 이제 브로드캐스트에는 최대 연결 수와 시간당 최대 메시지 수가 구분됩니다. When the limits are reached, it is possible to know why the throughput is limited. 이전에는 두 사례에 동일한 메시지(&#39;할당량 충족&#39;)가 적용되었습니다.
* 이제 풀에서 연결을 가져올 때 실행할 SQL 스크립트를 지정할 수 있습니다. 이 스크립트를 사용하여 기본 스키마를 설정할 수 있습니다. 이 스크립트는 쿼리 배너 후에 적용됩니다. (NEO 파섹
* Campaign SDK는 더 이상 PII 규정을 준수하기 위해 사용자 ID를 저장하지 않습니다. 이제 데이터가 해시로 저장됩니다.
* 패키지 내보내기 XML 파일을 가져올 때 이제 Campaign은 인코딩이 명시적으로 선언된 경우에도 파일에 BOM이 있는지 지원합니다.

**기술 발전**

클라이언트 및 서버 업그레이드

>[!CAUTION]
>
>18.10으로 업데이트된 서버가 있는 경우 서버에 액세스하려면 18.10 클라이언트를 사용해야 합니다. 18.10 클라이언트는 이전 서버 버전에 연결할 수 있습니다.

도메인 이름 관리

쿠키 추적 및 웹 응용 프로그램에 대한 도메인 이름 관리가 향상되었습니다.

이제 모든 두 글자의 두 번째 수준 도메인 이름이 기본적으로 지원됩니다(예: .aa.com). 보다 복잡한 도메인 이름(예: .com.au와 같은 세 글자 두 번째 수준 도메인)의 경우 serverConf의 **cookieDomains** 옵션(리디렉션 태그 아래)에 추가해야 합니다. 다음은 예입니다.

```
<redirection cookiedomain="http://toureiffel.paris">
```

향상된 색인

NmsRecipient에 대한 인덱스가 다시 수정되었습니다. 이렇게 하면 이 테이블을 사용하는 쿼리에 대한 성능이 향상됩니다. NmsRecipient의 확장을 수행한 경우 새 인덱스를 복제하는 인덱스가 없는지(데이터베이스 서버의 공간 사용을 최소화하기) 확인할 수 있습니다. (NEO 파섹)

UTF-8 데이터 정렬을 사용할 때 이제 &quot;LIKE &#39;string%&#39;(또는 &quot;다음으로 시작&quot;) 작업을 최적화하는 인덱스를 만들 수 있습니다. 같은 열에서 다른 작업을 수행하는 경우(예: 정렬 기준 또는 조인) 다른 표준 인덱스가 필요합니다. 스키마 측에서, 인덱스 정의에 indexOption=&quot;searchFromStart&quot;를 추가하면 됩니다(표준 트리 인덱스 대신 varchar_pattern_ops 인덱스를 생성합니다). 예(NmsRecipient):

```
<dbindex name="email2"> <!-- optimize order by/join (and startWith if not PostgreSql with an UTF-8 collation) operations -->
  <keyfield xpath="@email"/>
</dbindex>
<dbindex name="email3" indexOption="searchFromStart"><!-- optimize startsWith operation on PostgreSql when a UTF-8 collation is used; create no index in other cases-->
  <keyfield xpath="@email" />
</dbindex>
```

새 인덱스가 NmsRtEvent 및 NmsEventHisto(&quot;예약됨&quot; 열)에 추가되었으므로 해당 양식의 표시 시간이 개선됩니다(NEO-11738).

색인 변경 사항으로 인해 업그레이드 후 수행에 필요한 시간이 증가할 수 있습니다.

**패치**

* 웹 다운로드 워크플로우 **작업의 파일을** 다운로드할 수 없는 오류를 수정했습니다. (NEO 파섹
* 지표 및 캠페인 속성 **전송 워크플로우를** 실패함 상태로 가끔 남겨지는 오류를 수정했습니다(NEO-10820).
* 워크플로우에서 목록 업데이트 활동을 실행한 후 만든 수신자 목록을 삭제하는 문제를 해결했습니다. (NEO 파섹)
* 캠페인 달력(일본어 인스턴스)에서 한 달 전에 캠페인을 잘못 표시하던 문제를 수정했습니다. (NEO 파섹)
* Analytics 구성이 배달 속성의 웹 분석 탭에 표시되지 않던 문제를 수정했습니다. (NEO 파섹)
* nms:배달 입력 양식을 편집하고 저장하려고 할 때 표시되는 오류를 수정했습니다. (NEO 파섹)
* 파일 전송 활동이 포함된 워크플로우를 실행할 때 발생하는 외부 계정 구성 문제를 수정했습니다. (NEO 파섹
* zcat 함수를 사용하여 데이터 로드 작업에서 파일을 로드할 때 빈 줄을 반환하는 문제를 해결했습니다. (NEO 파섹
* 배달 분석 중에 중복된 확장 로그를 생성하는 문제를 수정했습니다. (NEO 파섹)
* 워크플로우에서 농축활동 실행 후 외부 링크 키가 누락되어 배달이 실패하는 문제를 해결했습니다. (NEO 파섹)
* 설치 경로에 특정 GB18030 중국어 문자가 포함되어 있을 때 Adobe Campaign의 제거 또는 복구를 제대로 수행하지 못했던 문제를 수정했습니다.
* 일부 추적 로그를 잘못된 배달에 연결하는 문제를 수정했습니다. (NEO 파섹)
* 배달 로그의 일부 부분이 예상보다 오래 대기 상태로 남아 있는 문제를 해결했습니다. (NEO 파섹)
* 쿼리를 편집하여 게시에 쿠폰을 추가하는 경우 발생하는 오류가 수정되었습니다. (NEO 파섹)
* 집계된 연산자가 선택된 것과 상관없이 차트가 항상 값의 합계를 계산하도록 하는 보고서의 문제를 수정했습니다. (NEO 파섹)
* &quot;request.scheme&quot; 함수는 더 이상 사용되지 않으므로 JSAPI 설명서에서 제거되었습니다. (NEO 파섹)
* 특정 시간대 구성을 가진 일부 사용자가 Adobe Campaign에 로그인하지 못했던 문제를 수정했습니다. (NEO 파섹)
* 확장 일반 SMPP 커넥터를 사용하여 모바일 채널 외부 계정을 설정할 때 발생하는 문제를 수정했습니다.수신기에 대해 다른 매개 변수를 사용하여 지정한 경우 송신기가 자체 매개 변수 대신 이러한 매개 변수를 잘못 사용하게 됩니다.
* 첫 번째 중재 후 배달이 계속 다시 계산되었기 때문에 압력 규칙에 대한 빈도를 설정할 때 예약 배달이 실패했던 문제를 수정했습니다. (NEO 파섹)
* 응용 프로그램 풀 재활용 프로세스(nlsrvmod.dll 라이브러리)에서 IIS 웹 서버가 충돌하는 문제를 해결했습니다. (NEO 파섹)
* 프로필 및 타겟 화면에서 수신자를 검색할 수 없는 **문제를** 수정했습니다. (NEO 파섹)
* 레코드 수가 많은 경우 이벤트 내역 폴더에 액세스할 때 시간 초과 오류가 발생하는 문제를 해결했습니다. (NEO 파섹)
* LINE 배달 수신자가 &quot;접근 불가&quot;로 잘못 반환될 수 있는 문제를 수정했습니다. (NEO 파섹)
* Oracle에서 추가 열이 있는 워크플로우 쿼리를 실행할 때 발생하는 문제를 수정했습니다. (NEO 파섹)
* 연결 풀에 닫힌 연결이 너무 오랫동안 유지되지 않도록 기능이 개선되었습니다. (NEO 파섹)
* 타깃팅 워크플로우 활동(쿼리, 데이터 로드(RDBMS) 등)을 사용할 때 발생하는 문제가 해결되었습니다. FDA를 통해 외부 Oracle 테이블에 연결됨(테이블 이름, 필드 이름 등) 또한 시스템에서 생성된 기본 제약 조건 이름의 기본 키 제약 조건을 포함합니다. (NEO 파섹)
* 배달의 HTML 콘텐츠를 삭제하지 못하는 문제를 해결했습니다. (NEO 파섹)
* 캠페인 실행 후 XML 및 CSV 파일을 DM으로 미리 보는 문제를 해결했습니다. (NEO 파섹)
* 강화된 워크플로우 활동에서 데이터를 정렬할 때 발생하는 문제를 수정했습니다. (NEO 파섹)
* 사용자 지정 보고서에서 데이터를 정렬할 때 발생하는 문제를 수정했습니다. (NEO 파섹)
* Teradata에서 useVault 설정을 사용할 때 오류가 발생하는 문제를 해결했습니다. (NEO 파섹)
* 여러 쿼리 행을 삭제할 때 Adobe Campaign 클라이언트 콘솔이 충돌하는 문제를 해결했습니다. (NEO 파섹)
* DM을 제공할 때 압력 규칙이 적용되지 않는 문제를 해결했습니다. (NEO 파섹)
* 데이터 로드 활동을 사용하여 데이터 유형이 &#39;시간&#39;인 열을 가져올 때 발생하는 문제를 수정했습니다.시간 구분 문자는 제거된 후에도 재설정됩니다. (NEO 파섹)
* 반복 배달을 편집할 때 배달 속성의 실행 폴더 목록에 배달 폴더가 표시되지 않는 문제를 해결했습니다. (NEO 파섹)
* 전체 보기 창에서 200개 이상의 레코드를 워크플로에서 쿼리 활동의 결과 대상으로 표시하지 않는 문제를 해결했습니다. (NEO 파섹)
* 1,000개 이상의 요소를 선택한 상태에서 DELETE 쿼리를 실행하지 못했던 Oracle 문제를 수정했습니다. (NEO 파섹
* Android 푸시 알림 전달의 추가 매개 변수에서 추적된 URL로 URL을 인코딩하는 문제를 해결했습니다. (NEO 파섹)
* 매개 변수를 &#39;하루 간격&#39; 및 &#39;열기&#39;로 설정할 때 사용자 활동 보고서에서 발생했던 스크립트 오류를 수정했습니다. (NEO 파섹
* 인증된 웹 프록시를 통해 중간 소싱 서버 또는 메시지 센터에 연결할 때 발생하는 문제를 수정했습니다. (NEO 파섹)
* SQL 뷰를 **기반으로 특정 스키마의 요소를 선택한 후 새 배달 컴포지션을 저장할 때 발생하는 Oracle 오류를 수정했습니다**. (NEO 파섹
* 압축 해제 옵션을 사용하여 .csv를 포함하는 압축 파일을 처리할 때 잘못된 위치 지정 파일이 생성되는 거부 파일로 이어지던 문제를 수정했습니다.
* xtkjoblog가 이제 정리 작업에 의해 삭제됩니다.

