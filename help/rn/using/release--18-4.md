---
title: 릴리스 18.4
seo-title: 릴리스 18.4
description: 릴리스 18.4
seo-description: null
page-status-flag: never-activated
uuid: d132570e-20e6-4550-95bd-176701f43b19
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rn
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 4dc87ff3-eb6a-40ac-97ee-00b64cd7718d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 14690ab1435f291679e643ee4240ae9df7e86356

---


# 릴리스 18.4{#release-18-4}

## 릴리스 18.4.5 - 빌드 8937{#release-18-4-5-build-8937}

2018년 11월 21일

**향상된 기능**

* FDA에서 MySQL을 사용하여 워크플로우를 실행할 때 발생하는 다양한 문제가 해결되었습니다. (NEO 파섹
* 특정 경우 배달 모집단 중 일부가 보류 중 상태로 유지되는 문제를 수정했습니다. (NEO 파섹)
* SMS 자동 응답에 대한 간헐적인 문제가 수정되었습니다. (NEO 파섹
* 배달에서 시드 주소를 사용할 때 ID 소모 문제가 해결되었습니다. (NEO 파섹
* 추가 워크플로우 활동에서 정렬을 수행할 때 구문 오류를 해결했습니다. (NEO 파섹)
* IIS 파섹 (NEO 파섹)
* 빌드 업그레이드(FDA - SQL) 후 추적 워크플로우가 실패하던 문제를 수정했습니다. (NEO 파섹
* 워크플로우 목록 데이터가 손실될 수 있는 문제를 수정했습니다. (NEO 파섹)
* 푸시 알림을 전송할 때 성능 문제가 해결되었습니다. (NEO 파섹)
* &quot;com.au&quot; 도메인에서 웹 추적이 작동하지 않는 문제를 해결했습니다(NEO 파섹 4385).
* 복잡한 워크플로우를 사용할 때 발생할 수 있는 클라이언트 고정 문제를 해결했습니다. (NEO 파섹)
* 특정 스키마의 요소를 선택한 후 새 배달을 저장할 때 발생하는 Oracle 오류를 수정했습니다(NEO-11682).
* 악센트 부호가 있는 문자(FDA/Teradata)가 들어 있는 필드를 쿼리할 때 발생하는 문제가 해결되었습니다. 이제 외부 계정을 사용하여 Teradata 드라이버와 통신하는 데 사용되는 인코딩을 변경할 수 있습니다. (NEO 파섹)
* 푸시 알림의 추가 변수에서 URL을 전달할 때 모바일 애플리케이션에서 받은 형식이 잘못되었거나 잘못된 데이터로 이어질 수 있는 추적 문제를 수정했습니다. (NEO 파섹 11468, NEO-11960)
* 1:N 링크와 함께 값 배포를 사용할 때 표시 문제를 초래했던 문제를 수정했습니다. (NEO 파섹)
* Teradata 16에서 벌크 로드가 작동하지 않는 문제를 해결했습니다.
* 15.10 드라이버의 바인딩 문제를 방지하기 위해 Teradata의 타임스탬프 버퍼 크기를 늘렸습니다.
* 업그레이드 후 문제를 야기할 수 있는 긴 이름 인덱스의 관리를 개선했습니다.
* MTA(Children dead Processing) 중 사용 가능한 공유 메모리 시간이 개선되었습니다.
* Apache(추적)의 잠재적 교착 상태를 수정했습니다.

## 릴리스 18.4.4 - 빌드 8936{#release-18-4-4-build-8936}

2018년 8월 1일

**향상된 기능**

* 이메일 보관 로그가 향상되어, BCC 보관을 통해 성공적으로 배달되었거나 실패한 이메일을 보다 쉽고 명확하게 확인할 수 있습니다. (NEO 파섹)
* 추적 브로드로그에서 고객 IP 대신 부하 균형 조정기 IP가 표시되는 문제를 해결했습니다. (NEO 파섹)
* PostgreSQL 데이터베이스에 FDA 연결을 사용할 때 LATIN1 인코딩 오류가 수정되었습니다. (NEO 파섹)
* 배달 옵션을 사용할 때 발생하는 문제를 **[!UICONTROL Prepare the personalization data with a workflow]** 수정했습니다. (NEO-11047, NEO-11301)
* 배달 속성이 잘못 덮어쓰여지는 무작위 문제를 수정했습니다. (NEO 파섹)
* 워크플로우 활동에서 계산된 필드를 사용할 때 발생하는 문제를 **[!UICONTROL Survey answers]** 수정했습니다. (NEO 파섹
* 워크플로우 활동에서 XML에 저장된 데이터를 사용할 때 발생하는 문제를 **[!UICONTROL Survey answers]** 수정했습니다. (NEO 파섹)
* 빌드 8935로 서버 업그레이드를 수행할 때 발생하는 문제가 해결되었습니다.
* 워크플로 활동이 완전히 구성되지 않았을 때 업그레이드 후 로그에 불필요한 오류가 표시되던 문제를 **[!UICONTROL Survey answers]** 수정했습니다.
* FDA Teradata:sql 테이블에서 자동으로 증가하는 필드 및 색인에 대한 문제를 수정했습니다.

## 릴리스 18.4.3 - 빌드 8935{#release-18-4-3-build-8935}

2018년 6월 22일

**향상된 기능**

* Microsoft Edge 및 Internet Explorer의 추적 인코딩 문제를 수정했습니다. (NEO 파섹)
* LINE 게재에서 이미지 링크 개인화 문제를 수정했습니다. (NEO 파섹)
* ID 시퀀스 생성 메커니즘이 제대로 작동하지 않는 문제를 해결했습니다. (NEO 파섹)
* 정수 유형 조정 키가 있는 사용자 지정 네임스페이스를 사용할 때 개인 정보(GDPR) 요청이 작동하지 않는 문제를 해결했습니다. (NEO 파섹
* 워크플로우 활동에서 **[!UICONTROL Distribution of values]** 옵션을 사용할 때 발생할 수 있는 오류를 **[!UICONTROL Query]** 수정했습니다. (NEO 파섹)
* 마케팅 인스턴스에서 상호 작용 인스턴스로 오퍼 공간을 동기화할 때 발생하는 문제를 수정했습니다. (NEO 파섹)
* 업그레이드 후 동안 긴 이름 인덱스 관리 개선

## 릴리스 18.4.2 - 빌드 8932{#release-18-4-2-build-8932}

2018년 5월 22일

**향상된 기능**

* Windows Server 업데이트가 제대로 작동하지 않는 문제를 해결했습니다.
* XML에 저장된 데이터를 사용할 때의 **[!UICONTROL Survey Result]** 활동 문제가 해결되었습니다. 보고서가 잘못 표시되었습니다. (NEO 파섹)
* 바운스 메일 서버를 사용할 때 inMail 프로세스에서 발생할 수 있는 성능 문제를 수정했습니다. (NEO 파섹)
* 1,000개 이상의 스키마를 업그레이드할 때 발생할 수 있는 데이터베이스 업그레이드 문제를 해결했습니다.

## 릴리스 18.4 - 빌드 8931{#release-18-4-build-8931}

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
   <td> EU 개인 정보 보호 규정(GDPR)<br /> </td> 
   <td> <p>GDPR은 2018년 5월 25일부터 적용되는 데이터 보호 요건을 통합하고 현대화한 유럽 연합의 새로운 개인 정보 보호 법입니다. GDPR은 EU에 거주하는 데이터 주체의 데이터를 보유하고 있는 Adobe Campaign 고객에게 적용됩니다.</p> <p> Adobe Campaign에서 이미 사용 가능한 개인 정보 보호 기능(동의 관리, 데이터 유지 설정 및 사용자 역할 포함) 외에도, Adobe는 데이터 프로세서로서의 기능을 추가로 제공하여 특정 GDPR 요청에 대해 데이터 컨트롤러로서의 준비를 용이하게 하기 위해 다음과 같은 기회를 제공하고 있습니다.</p> 
    <ul> 
     <li> <p>액세스 권한:데이터 주체가 Adobe Campaign에 저장된 데이터를 포함하여 데이터 관리자가 캡처한 개인 데이터의 사본을 수신할 수 있도록 허용합니다.</p> </li> 
     <li> <p>삭제할 권한:데이터 주체가 데이터 관리자에 의해 캡처한 개인 데이터를 삭제하도록 권한을 부여하며, 여기에는 Adobe Campaign에 저장된 데이터가 포함됩니다.</p> </li> 
    </ul> 자세한 내용은 <a href="https://docs.campaign.adobe.com/doc/AC/getting_started/EN/ACC_GDPR.html">자세한 설명서를</a>참조하십시오.<br /> </td> 
  </tr> 
  <tr> 
   <td> 활성 프로필<br /> </td> 
   <td> <p>이제 Adobe Campaign은 전용 워크플로우를 통해 매월 업데이트되는 활성 프로파일 목록을 제공합니다.</p> <p>자세한 내용은 <a href="../../platform/using/about-profiles.md#active-profiles">자세한 설명서를</a>참조하십시오.</p> </td> 
  </tr> 
  <tr> 
   <td> 향상된 Android 푸시 커넥터<br /> </td> 
   <td> <p>Android 커넥터는 높은 처리량을 지원하도록 향상되었습니다. </p> <p>자세한 내용은 <a href="../../delivery/using/setting-up-mobile-app-channel.md#android-connectors">자세한 설명서를</a>참조하십시오.</p> </td> 
  </tr> 
 </tbody> 
</table>

**향상된 보안 기능**

* 이제 인증되지 않은 사용자의 잠재적 공격을 방지하기 위해 외부 개체 확장을 사용할 수 없습니다. (NEO 파섹)
* 표준 사용자가 응용 프로그램 액세스 URL, LDAP 설정 등과 같은 인스턴스 구성 매개 변수를 변경하지 못하도록 하는 권한 강화 (NEO 파섹)
* 스택 추적을 통해 민감한 정보를 표시할 수 있는 문제를 해결했습니다. 이제 외부 네트워크에서 액세스할 수 없는 위치에 대한 오류 세부 사항이 백엔드에 기록됩니다. (NEO 파섹)
* 표준 사용자가 관리자의 업로드된 문서 및/또는 내보낸 패키지를 볼 수 없도록 하는 권한 강화 (NEO 파섹)

**향상된 기능**

* **LINE 채널 - 향상된 아키텍처**:Adobe Campaign의 다른 모든 채널과 마찬가지로 LINE 채널도 이제 모든 배포 유형에서 지원됩니다.호스팅, 하이브리드 및 온-프레미스
* **시퀀스 자동 생성**:ID 생성 메커니즘은 대량의 개체가 있는 Campaign 인스턴스의 수명을 늘리도록 개선되었습니다. 자세한 내용은 이 [기술 문서를 참조하십시오](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html).

**기타 변경 사항**

* 명령줄을 사용하여 패키지를 가져올 때 새로운 모드를 사용할 수 있으므로 순환 종속성을 허용할 수 있습니다(큰 패키지에는 권장되지 않음). 자세한 내용은 &#39;기술 발전&#39; 섹션을 참조하십시오. (NEO 파섹)
* Teradata에서 대량의 데이터 로딩에 대한 성능이 개선되었으며 로그에서 처리된 데이터의 올바른 값을 표시하지 못하는 문제를 해결했습니다. (NEO 파섹)
* 이제 Audience Manager에서 대상을 가져오는 작업이 분할 파일에서 작동합니다. 이전에는 importSharedAudience 기술 워크플로우에서 세그먼트의 마지막 파일만 가져왔습니다. (NEO 파섹)
* Windows에서 캠페인 서버의 기본 설치 경로가 변경되었습니다. 64비트 버전 설정을 시작할 때 기본 설치 경로는 다음과 같습니다.C: **Program FilesAdobeAdobe Campaign Classic v7** 대신 **C:Program Files (x86)AdobeAdobe Campaign Classic v7**
* 기본 MX 규칙이 더 많은 도메인을 포함하고 처리량을 최적화하도록 개선되었습니다.
* 배포 마법사 SOAP 호출에 대한 액세스 제한 사항을 적용했습니다(xtk:serverOptions#SaveOptions).
* weka.jar 오래된 라이브러리가 제거되었고 보안 최적화를 위해 OpenSSL 라이브러리가 업데이트되었습니다.
* 인스턴스 성능 보안을 위해 결제 기술 워크플로우를 개선했습니다.
* 모든 연산자의 암호를 설정하거나 재설정할 수 있는 관리자가 복원되었습니다. 이렇게 하려면 연산자를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Actions]** > **[!UICONTROL Reset password]** 을 선택하고 연산자의 새 암호를 설정합니다. 운영자가 처음 다시 연결할 때 암호를 변경하는 것이 좋습니다. 자세한 내용은 [자세한 설명서를](../../production/using/lost-password.md)참조하십시오.
* 이제 Adobe Target의 새로운 멀티테넌트 기능을 지원하기 위해 Target과의 통합을 위해 옵션 및 외부 계정을 구성할 때 새로운 &quot;at_property&quot; 매개 변수를 URL에 추가할 수 있습니다. 이 매개 변수에 사용할 값은 Adobe Target에서 찾을 수 있으며 Target 호출을 수행할 때 Campaign에서 사용됩니다. 자세한 내용은 [자세한 설명서를](../../integrations/using/inserting-a-dynamic-image.md)참조하십시오.
* 이제 Adobe Target에서 제공하는 이미지를 클릭할 때 열 기본 랜딩 페이지를 지정할 수 있습니다. 이전에는 해당 이미지를 클릭하면 이메일을 만들 때 기본 이미지 세트로 이동했습니다. 자세한 내용은 [자세한 설명서를](../../integrations/using/inserting-a-dynamic-image.md)참조하십시오.
* 추적 **출력을 강제 적용하기 위해 외부 계정에 SMPP 추적** 활성화 확인란을 추가했습니다. 자세한 내용은 [자세한 설명서를](../../delivery/using/sms-channel.md#creating-an-smpp-external-account)참조하십시오.

**기술 발전**

queryDef

queryDef가 &quot;orderBy&quot; 절에 대해 수정되었습니다. 변경 전에 쿼리된 테이블의 기본 키는 &quot;orderBy&quot; 절에 암시적으로 추가됩니다. 일부 데이터베이스 엔진에서는(최소 postgresql) 인덱스를 사용할 수 없습니다(orderBy 절의 모든 필드는 동일한 인덱스로 간주해야 함). 이 동작에 종속되어 있는 경우 &quot;orderBy&quot; 절에 기본 키를 명시적으로 추가해야 합니다.

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

(18.4가 변경되기 전에) 암시적으로 전달됩니다.

```
<queryDef operation="select" schema="xtk:job" startPath="/" xtkschema="xtk:queryDef">
  <select>
     <node expr="@id"/>
   </select>
   <orderBy>
      <node expr="@logDate"/>
      <node expr="@id"/> <!-- implicitely added before 18.4, you can add it manually on your query, if you relied on this implicit order clauses --!>
   </orderBy>
</queryDef>
```

urlEncode 함수

&#39;urlEncode&#39; JavaScript 함수가 ASCII가 아닌 문자에 대해 제대로 작동하지 않았습니다. 수정되었으며 이제 모든 유니코드 문자(일본어 문자 포함)에서 작동해야 합니다. 비 ASCII 문자에 대해 &#39;urlEncode&#39; 비헤이비어를 사용하는 경우 코드를 수정해야 합니다.

패키지 가져오기 새 모드

명령줄을 사용하여 패키지를 가져올 때 새로운 모드를 사용할 수 있으므로 순환 종속성을 허용할 수 있습니다(큰 패키지에는 권장되지 않음). 기존 기능은 그대로 유지됩니다. 순환 종속성이 있는 이러한 패키지의 경우 새 플래그 **사용** 코드가 명령줄 패키지 가져오기에 추가되었습니다. 실행되면 인터페이스에서 패키지 가져오기가 수행되는 경우와 같이 JSEngine을 사용합니다.

```
nlserver package -instance:fresh -import:sup-packInstallTest.xml -verbose -usejs
```

**패치**

* Adobe Campaign Standard에서 Adobe Campaign Classic으로 게재 및 추적 로그를 복제할 때 발생하는 동기화 문제를 수정했습니다. (NEO 파섹)
* 빠른 로드 작업 실패 후 ETL 워크플로우가 다시 시작될 때 Teradata에서 오류 및 로그 테이블 처리 문제를 해결했습니다. 이제 워크플로우가 다시 시작될 때마다 오류 및 로그 테이블이 제대로 삭제됩니다. (NEO 파섹)
* FDA 패키지가 설치된 경우 Hadoop에 필요한 하이브 패키지를 자동으로 설치하는 업그레이드 후 문제를 해결했습니다. (NEO 파섹)
* 잘못된 도메인을 정의되지 않음 **오류로 처리하던** 오류를 수정했습니다. (NEO 파섹)
* Android 푸시 배달을 전송할 때 deliveryLogStats 테이블에 중복된 로그가 표시되는 문제를 해결했습니다. (NEO 파섹)
* 바코드 스캐너에서 특정 바코드 형식을 읽을 수 없는 문제를 해결했습니다. (NEO 파섹)
* 비 ASCII 문자를 사용할 때 &#39;urlEncode&#39; JavaScript 함수 문제를 해결했습니다. 자세한 내용은 &#39;기술 발전&#39; 섹션을 참조하십시오. (NEO 파섹)
* Teradata 데이터베이스에서 sha256 함수를 포함하는 쿼리를 실행할 때 발생하는 문제를 수정했습니다. (NEO 파섹)
* 매우 큰 SalesForce 테이블을 사용할 때 SalesForce 활동에서 발생할 수 있는 워크플로우 메모리 오류를 수정했습니다. (NEO 파섹)
* FDA를 사용할 **때 워크플로우 활동을 타깃팅할 때 보완** 생성 옵션 문제가 해결되었습니다. (NEO 파섹)
* mid-sourcing 사용 시 **마케팅** 인스턴스에서 처리 및 성공 **지표가** 업데이트되지 않는 문제를 해결했습니다. (NEO 파섹)
* 플랫폼에서 총 10,000개 이상의 오퍼가 총 1만 개 이상인 경우 상호 작용 비제안 규칙을 수정했습니다(NEO 파섹-9352).
* XML 외부 파일을 사용할 때 배달 대상을 지정하지 못했던 문제를 수정했습니다. (NEO 파섹)
* 오퍼에 대한 가설을 실행하고 제안 상태를 업데이트할 때 워크플로우 오류가 발생할 수 있는 문제를 수정했습니다. (NEO 파섹)
* Android 배달 매핑의 속성을 기반으로 압력 규칙을 사용할 때 배달 분석 중에 발생하는 오류를 수정했습니다. (NEO 파섹)
* 수신자 목록에서 열을 정렬하면 성능 문제가 발생할 수 있는 문제를 해결했습니다. queryDef 수정에 대한 자세한 내용은 아래의 &#39;기술 발전&#39; 섹션을 참조하십시오. (NEO 파섹)
* 특히 Federated ID 로그인 유형을 사용하는 경우 승인 이메일의 링크가 잘못된 로그인 URL을 가리킬 수 있는 문제를 해결했습니다. (NEO 파섹)
* 특정 시간대의 보고서 날짜 선택기에 잘못된 날짜가 표시되는 문제를 해결했습니다. (NEO 파섹)
* FDA SQL 데이터베이스를 사용할 때 아웃바운드 대상을 볼 수 없는 문제를 해결했습니다. (NEO 파섹)
* MS Dynamics CRM 커넥터에서 월의 첫 7일 동안 데이터를 가져올 수 없는 문제를 해결했습니다. (NEO 파섹)
* 사용자가 국제 문자를 포함하지 못하게 하는 Analytics 통합 오류가 수정되었습니다. (NEO 파섹)
* 적절한 권한 없이 워크플로우 편집을 활성화할 수 있는 문제를 수정했습니다. (NEO 파섹)
* 하이브리드 아키텍처에서 메시지 센터를 사용할 때 HTTP를 통한 FDA의 연결 끊김 또는 연결 끊김(시간 초과) 문제가 해결되었습니다. (NEO 파섹)
* 네거티브 ID에 대한 증분 쿼리 활동에서 발생하는 워크플로우 오류를 수정했습니다. (NEO 파섹)
* 특정 화면에서 이중 스크롤 막대를 표시할 수 있는 문제를 수정했습니다. (NEO 파섹)
* 데이터베이스 구조 업데이트 마법사를 실행할 때 오류 메시지가 표시되는 문제를 해결했습니다. PostUpgrade는 이름이 30보다 긴 인덱스의 이름을 실행합니다. 큰 표의 경우 색인 교체에는 시간이 걸립니다. (NEO 파섹)
* 추적 로그가 메시지 센터 실행 인스턴스에서 인스턴스를 제어하기 위해 올바르게 동기화되지 않는 문제를 수정했습니다. (NEO 파섹)
* 오퍼 강화 활동과 관련된 성능 문제를 수정했습니다. (NEO 파섹)
* FDA 파섹 (NEO 파섹)
* 데이터 관리의 회귀 현상을 수정했습니다. 이 과정에서 데이터 중복 작업 시 색인이 생성되지 않던 문제를 수정했습니다.
* 제목 @id로 외부 리소스를 만들 때 발생할 수 있는 문제가 해결되었습니다.
* FTP 서버를 통해 zip 파일을 업로드하거나 파일 이름에 와일드카드가 있는 파일을 업로드할 때 발생하는 문제를 수정했습니다.
* Campaign Standard로 만든 외부 사용자 지정 리소스의 긴 기본 유형 열거형 문제를 수정했습니다.
* 공급자와의 연결이 실패하여 SMS 손실이 발생해도 SMS가 전송되도록 하는 문제를 해결했습니다.
* SMTP 연결이 무기한으로 중단되는 오류를 수정했습니다.
* LINE 매핑을 사용할 때 또는 필터링 및 타깃팅 스키마가 다를 때 메시지 준비 중에 압력 유형 규칙 문제를 해결했습니다.
