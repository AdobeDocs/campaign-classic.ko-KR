---
product: campaign
title: 릴리스 19.2
description: Campaign 19.2 릴리스 노트
feature: null
role: null
level: null
exl-id: 3c529e4e-8787-41d2-b85d-3feaa5432196
source-git-commit: 883ac681e0bf0e4ccf916c745924b7340a4d22f9
workflow-type: tm+mt
source-wordcount: '1542'
ht-degree: 21%

---

# 릴리스 19.2{#release-19-2}

## ![](assets/do-not-localize/limited_2.png) 릴리스 19.2.4 - 빌드 9082 {#release-19-2-4-build-9082}

_2021년 4월 15일_

* IMS 연결 화면에서 지속적인 오류 메시지를 발생시킨 클라이언트 콘솔 회귀 문제를 수정했습니다. (NEO-34821)

**콘솔 업그레이드는 필수 사항입니다. 서버를 업그레이드할 필요가 없습니다.**

>[!NOTE]
>
> [Adobe 소프트웨어 배포](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)에 연결하여 새 버전을 다운로드합니다. [이 페이지에서](../../installation/using/client-console-availability-for-windows.md) 모든 최종 사용자에게 콘솔 업데이트를 제안하는 방법을 알아봅니다.

_2021년 3월 22일_

* 게재의 날짜 선택 및 이미지 관리와 같이 콘솔의 일부 구성 요소를 사용할 수 없는 회귀 문제를 해결했습니다. (NEO-31453, NEO-31454)

**콘솔 업그레이드는 필수 사항입니다. 서버를 업그레이드할 필요가 없습니다.**

>[!NOTE]
>
> [Adobe 소프트웨어 배포](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)에 연결하여 새 버전을 다운로드합니다. [이 페이지에서](../../installation/using/client-console-availability-for-windows.md) 모든 최종 사용자에게 콘솔 업데이트를 제안하는 방법을 알아봅니다.

_2020년 12월 23일_

>[!CAUTION]
>
> * 이 릴리스는 새 연결 프로토콜과 함께 제공됩니다. Adobe IMS(ID 관리 서비스)를 통해 Campaign에 연결할 경우, **2021년 6월 30일** 이후부터 Campaign 서버 및 클라이언트 콘솔은 Campaign에 연결할 수 있도록 업그레이드를 해야 합니다. [자세히 알아보기](../../technotes/ims-updates.md)
   >
   > 
* 이 릴리스는 [보안 픽스](https://helpx.adobe.com/kr/security/products/campaign/apsb21-04.html)와 함께 제공됩니다. 환경 보안을 강화하려면 업그레이드가 필요합니다.



* 연결 프로토콜은 새 IMS 인증 메커니즘을 따르도록 업데이트되었습니다.
* SSRF(Server Side Request Forgery) 공격으로부터 보호를 강화하기 위해 보안 문제를 해결했습니다. (NEO-27777)

## ![](assets/do-not-localize/red_2.png) 릴리스 19.2.3 - 빌드 9081 {#release-19-2-3-build-9081}

_2020년 2월 7일_

**개선 사항**

* Windows 서버에서 사용자 연결이 실패하는 SSL 인증 구현으로 인한 회귀 문제를 해결했습니다. (NEO-20629)
* **정보** 메뉴에서 잘못된 버전 태그 번호를 표시하던 문제가 해결되었습니다.

## ![](assets/do-not-localize/red_2.png) 릴리스 19.2 - 빌드 9080 {#release-19-2-build-9080}

_2019년 12월 2일_

**새로운 기능**

<table> 
 <thead> 
  <tr> 
   <th> <strong>캘리포니아 소비자 개인 정보 보호법(CCPA)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>CCPA는 2020년 1월 1일부터 시행된 데이터 보호 요구 사항을 통합하고 현대화한 캘리포니아 주의 새로운 개인 정보 보호 법입니다. CCPA는 캘리포니아에 거주하는 데이터 주체의 데이터를 보유하고 있는 Adobe Campaign 고객에게 적용됩니다.</p>
    <p>Adobe Campaign은 이미 사용 가능한 개인 정보 보호 기능(동의 관리, 데이터 유지 설정 및 사용자 역할 포함) 외에도 CPA에 대한 준비를 용이하게 합니다.</p>
    <ul>
      <li>액세스 권한 및 삭제 권한:adobe는 GDPR에 추가된 기능을 활용하고 있습니다. <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#righttoaccess">자세히 알아보기</a></li>
      <li>소비자가 개인 정보 판매를 옵트아웃했는지 여부를 추적할 수 있습니다. 이를 위해 프로필 테이블을 확장하고 <strong>CCPA에 대한 옵트아웃</strong> 필드를 추가해야 합니다. <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#ccpa">자세히 알아보기</a></li></td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>워크플로우 라이브 모니터링</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>이제 사전 정의된 보기를 사용하여 인스턴스에 있는 모든 워크플로우의 실행 상태를 모니터링할 수 있습니다.</p>
   <p>자세한 내용은 <a href="../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status">세부 설명서</a>를 참조하십시오.</p></td> 
  </tr> 
 </tbody> 
</table>


<table> 
 <thead> 
  <tr> 
   <th> <strong>AMP를 사용한 대화형 콘텐츠</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
<td> <p>Adobe Campaign을 사용하면 새로운 대화형 <a href="https://amp.dev/about/email/">AMP for Email</a> 형식을 사용해 볼 수 있습니다. 이 이메일 형식을 통해 마케터는 메시지 내에 AMP 구성 요소를 포함시켜 메시지 자체에서 직접 실행 가능한 풍부하고 동적인 대화형 컨텐츠로 이메일 경험을 향상시킬 수 있습니다.</p>
   <p>이 기능은 공개 베타로 출시됩니다.</p>
   <p>자세한 내용은 <a href="../../delivery/using/defining-interactive-content.md">세부 설명서</a> 및 <a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/email-channel/defining-interactive-email-content-with-amp.html">튜토리얼 비디오</a>를 참조하십시오.</p><br /></td> 
  </tr> 
 </tbody> 
</table>


<table> 
 <thead> 
  <tr> 
   <th> <strong>TLS(보안 SMS 메시지)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
<td> <p>보안 SMS는 이제 확장된 일반 SMPP 커넥터를 통해 지원됩니다. 이를 통해 공급자에 암호화된 연결을 허용할 수 있습니다.</p> <p><strong></strong> 경고 이 기능을 사용하려면 모든 서버에 최신 인증서가 필요합니다. 인증서가 잘못되었거나, 해지되었거나, 만료된 경우 전체 SMS 전송 기능에 영향을 주는 오류가 발생합니다.</p><p>자세한 내용은 <a href="https://helpx.adobe.com/kr/campaign/kb/sms-connector-protocol-and-settings.html">세부 설명서</a>를 참조하십시오. </p> </td> 
  </tr> 
 </tbody> 
</table>

**향상된 보안 기능**

* Campaign 인터페이스의 저장된 교차 사이트 스크립팅 취약점 - 입력 데이터 유효성 검사 및 출력 인코딩이 수정되었습니다. (NEO-16810)
* 로그인 제한 정책을 강화하여 권한이 없는 데이터에 액세스할 수 있는 프로필 권한 부여에 대한 보안 문제를 수정했습니다. (NEO-14445)

**개선 사항**

* 푸시 알림에 대한 메모리 사용량 최적화.
* 성능 및 저장 공간 최적화를 위해 **logins.log** 파일의 처리가 향상되었습니다. 이제 파일은 여러 파일로 분할되어 매일 한 개씩 최대 365개의 파일이 유지됩니다. [자세히 알아보기](../../production/using/log-files.md)
* 이제 암호 자격 증명(암호 + 사용자 이름) 또는 인증서(개인 키)를 사용하여 Microsoft Dynamics CRM 외부 계정을 구성할 수 있습니다. [자세히 알아보기](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account)
* 안정성을 개선하기 위해 Hadoop FDA 커넥터에 몇 가지 개선 사항이 추가되었습니다
* 서버에 공개 리소스를 업로드하기 전에 디스크 공간을 확인하기 위해 특정 보호 기능이 추가되었습니다.
* 새 [캠페인 옵션](../../installation/using/configuring-campaign-options.md)이 추가되었습니다.
   * **WdbcKillSessionPolicy** 구성 옵션을 사용하면 모든 워크플로우 및 PostgreSQL 데이터베이스 쿼리에 대해 **무조건적 정지** 동작에 영향을 줄 수 있습니다.
   * **NmsOperation_DeliveryPreparationWindow** 옵션을 사용하면 실행 중인 게재 수에서 불일치 상태의 게재를 제외할 일 수를 정의할 수 있습니다.
   * **WdbcOptions_TempDbName** 옵션을 사용하면 Microsoft SQL Server에서 작업 테이블에 대해 별도의 데이터베이스를 구성할 수 있습니다. 백업 및 복제를 최적화합니다. [자세히 알아보기](../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server)
   * PostgreSQL에 대해 **XtkCleanup_NoStats** 옵션이 개선되어 데이터베이스 정리 워크플로우의 저장소 최적화 단계의 동작을 더 잘 제어할 수 있습니다. [자세히 알아보기](../../production/using/database-cleanup-workflow.md#statistics-update)
* 계정 잠금 메커니즘이 **logon()** API에 추가되었습니다. 지정된 기간 내에서 일정 수의 연속적인 로그인 시도 실패 후 추가적인 로그인 시도를 방지합니다.
* 게재 속성의 새로운 **최대 개인화 실행 시간** 옵션을 사용하면 개인화 단계가 너무 오랫동안 실행되지 않도록 하기 위해 개인화 실행 시간에 대한 시간 초과 기간을 정의할 수 있습니다. [자세히 알아보기](../../delivery/using/personalization-fields.md#timing-out-personalization)
* SFTP 연결에 프록시 구성을 사용할 수 있도록 **ftp 프로토콜** 옵션이 추가되었습니다. [자세히 알아보기](../../installation/using/file-res-management.md)
* 온-프레미스 환경을 위한 SFTP 외부 서버에 대한 프록시 액세스에 대한 새로운 지원.
* Campaign 인스턴스와 호환되지 않는 패키지를 설치하지 않도록 특정 보호 기능이 추가되었습니다. [자세히 알아보기](../../installation/using/installing-campaign-standard-packages.md)

_사용되지 않는 시스템_

이제 다음 시스템은 Campaign Classic 구현에 대해 [사용되지 않습니다](https://helpx.adobe.com/kr/campaign/kb/deprecated-and-removed-features.html).
* Apache 2.2
* Centos 6

최신 Campaign 호환성 매트릭스에 나열된 모든 시스템의 지원 버전을 사용하고 있는지 확인하십시오. [자세히 알아보기](https://helpx.adobe.com/kr/campaign/kb/compatibility-matrix.html)

_Campaign Mobile SDK_

이제 iOS SDK의 빌드 1.0.26을 사용할 수 있습니다. 이 새로운 빌드에서 iOS 13의 지원을 추가했습니다. 이제 이 새 버전에서 iOS 13 푸시 알림에 대한 알림 우선 순위 및 새 등록 토큰 관리 프로세스를 지원합니다. 이전 버전의 SDK에서 애플리케이션을 실행하는 경우 새 SDK를 사용하여 애플리케이션을 다시 컴파일해야 합니다. SDK를 얻으려면 [고객 지원 센터 Adobe](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)에 문의하십시오.

**패치**

* **데이터 로드(RDBMS)** 워크플로우 활동에서 **연결된 테이블 추가** 필드가 비어 있는 경우 발생하는 충돌 문제가 해결되었습니다. (NEO-12213)
* 중간 소싱 서버에서 특정 메시지가 처리되지 않는 문제를 수정했습니다. (NEO-12395)
* teradata에서 쿼리 브랜딩 옵션을 사용할 때 데이터베이스 정리 워크플로우의 문제를 해결했습니다. (NEO-12399)
* ne.jp 도메인을 포함하는 유형화 규칙을 사용하여 게재 분석에 영향을 주는 문제를 해결했습니다. (NEO-12609)
* 더 제한적인 인증서 정책으로 암시된 TLS 업데이트를 통한 SMS 관련 문제를 수정했습니다. 이러한 업데이트로 인해 최신 인증서가 아닌 경우 마케팅과 중간 소싱 서버 간에 연결이 실패할 수 있습니다. (NEO-17698)
* 중간 소싱 환경에서 자격 증명 모음 인증이 있는 외부 계정에서 **연결 테스트** 단추를 사용할 때 발생하는 문제를 해결했습니다. (NEO-12722)
* FDA Hadoop 연결과 함께 날짜 함수를 사용하는 쿼리에 대한 문제를 수정했습니다. (NEO-12847)
* 이메일 편집기에서 이미지를 바꿀 때 발생하는 문제를 수정했습니다. (NEO-13098)
* 삭제되었거나 다른 위치로 이동한 폴더에 대해 업그레이드 후 오류가 발생할 수 있는 문제를 해결했습니다. (NEO-13118)
* LINE 메시지에서 **장치 화면 크기당 이미지 정의** 옵션을 사용할 때 이미지 표시 문제를 해결했습니다. (NEO-13228)
* **배달 중 중복 주소 제외** 옵션이 선택되지 않은 경우 게재 준비 문제가 해결되었습니다. (NEO-13240)
* **파일 전송** 활동을 사용하여 **전송 후 소스 파일 삭제** 옵션을 사용하여 파일을 다운로드할 때 공백 문자가 포함된 이름으로 문제가 해결되었습니다. (NEO-13411)
* 메모리 문제로 이어질 수 있는 Tomcat 캐시 정리 문제를 수정했습니다. (NEO-13456)
* Microsoft SQL 2017에서 실행되는 기존 제어 인스턴스에 실행 인스턴스&#x200B;**내장 패키지를 사용하여 오퍼 엔진의**&#x200B;제어 패키지를 설치할 때 발생하는 문제를 해결했습니다. (NEO-13539)
* 초기화되지 않은 변수로 인해 **텍스트 콘텐츠** 탭에서 이메일의 추적된 URL을 선택 취소할 때 발생할 수 있는 콘솔 충돌 문제를 수정했습니다. (NEO-13545)
* 중국어 발신자 이름에 대한 인코딩 문제가 수정되었습니다. (NEO-13837)
* 탐색기에서 설문 조사 응답 데이터를 표시할 때 발생할 수 있는 오류를 수정했습니다. (NEO-14590)
* 게재 로그 분류와 격리 테이블 간에 불일치가 발생할 수 있는 문제를 수정했습니다. (NEO-16547)
* 전자 메일에 포함되지 않은 DKIM 키 문제를 해결했습니다. (NEO-16804)
* 이벤트를 트리거하기 위해 API 호출 컨텍스트에서 잘못된 세션 토큰이 사용된 경우 잘못된 오류 코드가 표시되는 문제를 해결했습니다. 오류 코드는 &#39;HTTP 403 금지됨&#39; 대신 &#39;HTTP 200 OK&#39;였습니다. (NEO-16826)
* 웹 액세스를 통해 게재 보고서를 표시할 때 발생하는 문제를 수정했습니다. (NEO-17015)
* Adobe Campaign에 로그인할 때 발생하는 IMS 인증 문제가 수정되었습니다. (NEO-17312)
* 격리된 이메일이 개인 정보 관리 프로세스에서 삭제되지 않는 문제를 수정했습니다. (NEO-17314)
* SQL 데이터베이스를 사용하여 9031로 업그레이드한 후 처리량 문제를 해결했습니다. (NEO-17558)
* Salesforce로 CRM 커넥터에 영향을 주는 문제를 해결했습니다. (NEO-17712)
* 외부 SFTP에서 데이터를 가져올 때 시간 초과 문제를 해결했습니다. (NEO-19723)
* 예측 모델에 액세스할 때 발생하는 문제를 수정했습니다. (NEO-19713)
* hadoop FDA 데이터베이스를 사용하는 **Split** 워크플로우 활동의 임의 샘플링에 영향을 주는 문제를 해결했습니다. (NEO-16636)
* 업그레이드 후 일부 함수가 유효하지 않은 것으로 간주되는 Oracle의 회귀 문제를 해결했습니다. (NEO-12759)
