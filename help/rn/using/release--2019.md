---
product: campaign
title: Campaign Classic 2019 릴리스
description: 'Campaign Classic 2019 릴리스에 대해 자세히 알아보기 '
exl-id: 8a36a542-e095-4208-b624-e59845592863
source-git-commit: 0f31ee570ba6e763f48902e91c5d823ac297fc24
workflow-type: tm+mt
source-wordcount: '4843'
ht-degree: 24%

---

# 2019년 릴리스{#release-2019}

![](../../assets/v7-only.svg)

## 릴리스 19.2{#release-19-2}

### ![](assets/do-not-localize/limited_2.png) 릴리스 19.2.4 - 빌드 9082 {#release-19-2-4-build-9082}

_2021년 4월 15일_

* IMS 연결 화면에서 지속적인 오류 메시지를 발생시킨 클라이언트 콘솔 회귀 문제를 수정했습니다. (NEO-34821)

**콘솔 업그레이드는 필수 사항입니다. 서버를 업그레이드할 필요가 없습니다.**

>[!NOTE]
>
> [Adobe 소프트웨어 배포](https://experience.adobe.com/#/downloads/content/software-distribution/ko/campaign.html)에 연결하여 새 버전을 다운로드합니다. [이 페이지에서](../../installation/using/client-console-availability-for-windows.md) 모든 최종 사용자에게 콘솔 업데이트를 제안하는 방법을 알아봅니다.

_2021년 3월 22일_

* 게재의 날짜 선택 및 이미지 관리와 같이 콘솔의 일부 구성 요소를 사용할 수 없는 회귀 문제를 해결했습니다. (NEO-31453, NEO-31454)

**콘솔 업그레이드는 필수 사항입니다. 서버를 업그레이드할 필요가 없습니다.**

>[!NOTE]
>
> [Adobe 소프트웨어 배포](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)에 연결하여 새 버전을 다운로드합니다. [이 페이지에서](../../installation/using/client-console-availability-for-windows.md) 모든 최종 사용자에게 콘솔 업데이트를 제안하는 방법을 알아봅니다.

_2020년 12월 23일_

>[!CAUTION]
>
> * 이 릴리스는 새 연결 프로토콜과 함께 제공됩니다. Adobe IMS(ID 관리 서비스)를 통해 Campaign에 연결할 경우, **2021년 6월 30일** 이후부터 Campaign 서버 및 클라이언트 콘솔은 Campaign에 연결할 수 있도록 업그레이드를 해야 합니다. [자세히 알아보기](../../technotes/using/ims-updates.md)
>
> * 이 릴리스는 [보안 픽스](https://helpx.adobe.com/kr/security/products/campaign/apsb21-04.html)와 함께 제공됩니다. 환경 보안을 강화하려면 업그레이드가 필요합니다.



* 연결 프로토콜은 새 IMS 인증 메커니즘을 따르도록 업데이트되었습니다.
* SSRF(Server Side Request Forgery) 공격으로부터 보호를 강화하기 위해 보안 문제를 해결했습니다. (NEO-27777)

### ![](assets/do-not-localize/red_2.png) 릴리스 19.2.3 - 빌드 9081 {#release-19-2-3-build-9081}

_2020년 2월 7일_

**개선 사항**

* Windows 서버에서 사용자 연결이 실패하는 SSL 인증 구현으로 인한 회귀 문제를 해결했습니다. (NEO-20629)
* 에서 잘못된 버전 태그 번호가 표시되는 문제를 해결했습니다. **정보** 메뉴 아래의 제품에서 사용할 수 있습니다.


### ![](assets/do-not-localize/red_2.png) 릴리스 19.2 - 빌드 9080 {#release-19-2-build-9080}

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
      <li>액세스 권한 및 삭제 권한: adobe는 GDPR에 추가된 기능을 활용하고 있습니다. <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#righttoaccess">자세히 보기</a></li>
      <li>소비자가 개인 정보 판매를 옵트아웃했는지 여부를 추적할 수 있습니다. 이를 위해 프로필 테이블을 확장하고 다음을 추가해야 합니다 <strong>CCPA용 옵트아웃</strong> 필드. <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#ccpa">자세히 보기</a></li></td> 
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
   <p>자세한 내용은 <a href="../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status">세부 설명서</a>를 참조하세요.</p></td> 
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
<td> <p>Adobe Campaign을 사용하면 새로운 대화형 기능을 사용해 볼 수 있습니다 <a href="https://amp.dev/about/email/">이메일용 AMP</a> 포맷. 마케터는 메시지 내에 AMP 구성 요소를 포함시켜 메시지 자체에서 직접 실행 가능한 풍부하고 동적인 대화형 컨텐츠로 이메일 경험을 향상시킬 수 있습니다.</p>
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
<td> <p>보안 SMS는 이제 확장된 일반 SMPP 커넥터를 통해 지원됩니다. 이를 통해 공급자에 암호화된 연결을 허용할 수 있습니다.</p> <p><strong>경고</strong> 이 기능을 사용하려면 모든 서버에 최신 인증서가 필요합니다. 인증서가 잘못되었거나, 해지되었거나, 만료된 경우 전체 SMS 전송 기능에 영향을 주는 오류가 발생합니다.</p><p>자세한 내용은 <a href="https://helpx.adobe.com/kr/campaign/kb/sms-connector-protocol-and-settings.html">세부 설명서</a>를 참조하세요. </p> </td> 
  </tr> 
 </tbody> 
</table>

**향상된 보안 기능**

* Campaign 인터페이스의 저장된 교차 사이트 스크립팅 취약점 - 입력 데이터 유효성 검사 및 출력 인코딩이 수정되었습니다. (NEO-16810)
* 로그인 제한 정책을 강화하여 권한이 없는 데이터에 액세스할 수 있는 프로필 권한 부여에 대한 보안 문제를 수정했습니다. (NEO-14445)

**개선 사항**

* 푸시 알림에 대한 메모리 사용량 최적화.
* 성능 및 스토리지 최적화를 위해 **logins.log** 파일이 향상되었습니다. 이제 파일은 여러 파일로 분할되어 매일 한 개씩 최대 365개의 파일이 유지됩니다. [자세히 보기](../../production/using/log-files.md)
* 이제 Microsoft Dynamics CRM 외부 계정을 암호 자격 증명(암호 + 사용자 이름) 또는 인증서(개인 키)를 사용하여 구성할 수 있습니다. [자세히 보기](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account)
* 안정성을 개선하기 위해 Hadoop FDA 커넥터에 몇 가지 개선 사항이 추가되었습니다
* 서버에 공개 리소스를 업로드하기 전에 디스크 공간을 확인하기 위해 특정 보호 기능이 추가되었습니다.
* 새로 만들기 [캠페인 옵션](../../installation/using/configuring-campaign-options.md) 가 추가되었습니다.
   * 다음 **WdbcKillSessionPolicy** 구성 옵션을 사용하면 **무조건 정지** 모든 워크플로우 및 PostgreSQL 데이터베이스 쿼리에 대한 동작입니다.
   * 다음 **NmsOperation_DeliveryPreparationWindow** 옵션을 사용하면 불일치 상태의 게재가 실행 중인 게재 수에서 제외되는 일 수를 정의할 수 있습니다.
   * 다음 **WdbcOptions_TempDbName** 옵션을 사용하면 Microsoft SQL Server에서 작업 테이블에 대해 별도의 데이터베이스를 구성할 수 있습니다. 백업 및 복제를 최적화합니다. [자세히 보기](../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server)
   * 다음 **XtkCleanup_NoStats** 데이터베이스 정리 워크플로우의 저장 최적화 단계의 동작을 더 잘 제어할 수 있도록 PostgreSQL에 대한 옵션이 향상되었습니다. [자세히 보기](../../production/using/database-cleanup-workflow.md#statistics-update)
* 계정 잠금 메커니즘이 **logon()** API. 지정된 기간 내에서 일정 수의 연속적인 로그인 시도 실패 후 추가적인 로그인 시도를 방지합니다.
* 새로운 **최대 개인화 실행 시간** 게재 속성의 옵션을 사용하면 개인화 단계가 너무 오랫동안 실행되지 않도록 개인화 실행 시간에 대한 시간 초과 기간을 정의할 수 있습니다. [자세히 보기](../../delivery/using/personalization-fields.md#timing-out-personalization)
* 다음 **ftp 프로토콜** SFTP 연결에 대해 프록시 구성을 사용할 수 있도록 옵션이 추가되었습니다. [자세히 보기](../../installation/using/file-res-management.md)
* 온-프레미스 환경을 위한 SFTP 외부 서버에 대한 프록시 액세스에 대한 새로운 지원.
* Campaign 인스턴스와 호환되지 않는 패키지를 설치하지 않도록 특정 보호 기능이 추가되었습니다. [자세히 보기](../../installation/using/installing-campaign-standard-packages.md)

_사용되지 않는 시스템_

이제 다음 시스템이 [사용되지 않음](deprecated-features.md) Campaign Classic 구현의 경우:
* Apache 2.2
* Centos 6

최신 Campaign 호환성 매트릭스에 나열된 모든 시스템의 지원 버전을 사용하고 있는지 확인하십시오. [자세히 보기](https://helpx.adobe.com/kr/campaign/kb/compatibility-matrix.html)

_Campaign Mobile SDK_

이제 iOS SDK의 빌드 1.0.26을 사용할 수 있습니다. 이 새 빌드에서 iOS 13의 지원을 추가했습니다. 이제 이 새 버전에서 iOS 13 푸시 알림에 대한 알림 우선 순위 및 새 등록 토큰 관리 프로세스를 지원합니다. 이전 버전의 SDK에서 애플리케이션을 실행하는 경우 새 SDK를 사용하여 애플리케이션을 다시 컴파일해야 합니다. SDK를 얻으려면 [고객 지원 Adobe](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**패치**

* 다음 상황에서 **연결된 테이블 추가** 필드에 비어 있습니다. **데이터 로드(RDBMS)** 워크플로우 활동. (NEO-12213)
* 중간 소싱 서버에서 특정 메시지가 처리되지 않는 문제를 수정했습니다. (NEO-12395)
* teradata에서 쿼리 브랜딩 옵션을 사용할 때 데이터베이스 정리 워크플로우의 문제를 해결했습니다. (NEO-12399)
* ne.jp 도메인을 포함하는 유형화 규칙을 사용하여 게재 분석에 영향을 주는 문제를 해결했습니다. (NEO-12609)
* 더 제한적인 인증서 정책으로 암시된 TLS 업데이트를 통한 SMS 관련 문제를 수정했습니다. 이러한 업데이트로 인해 최신 인증서가 아닌 경우 마케팅과 중간 소싱 서버 간에 연결이 실패할 수 있습니다. (NEO-17698)
* 를 사용할 때 발생하는 문제를 수정했습니다 **연결 테스트** 중간 소싱 환경에서 저장소 인증이 있는 외부 계정에 대한 단추. (NEO-12722)
* FDA Hadoop 연결과 함께 날짜 함수를 사용하는 쿼리에 대한 문제를 수정했습니다. (NEO-12847)
* 이메일 편집기에서 이미지를 바꿀 때 발생하는 문제를 수정했습니다. (NEO-13098)
* 삭제되었거나 다른 위치로 이동한 폴더에 대해 업그레이드 후 오류가 발생할 수 있는 문제를 해결했습니다. (NEO-13118)
* 를 사용할 때 이미지 표시에 문제가 해결되었습니다. **장치 화면 크기별 이미지 정의** LINE 메시지의 옵션입니다. (NEO-13228)
* 다음 상황에서 **배달 중 중복 주소 제외** 옵션을 선택하지 않았습니다. (NEO-13240)
* 을 사용할 때 워크플로우에서 발생하는 문제를 수정했습니다 **파일 전송** 활동을 사용하여 파일을 다운로드합니다. **전송 후 소스 파일 삭제** 옵션, 공백 문자를 포함하는 이름 (NEO-13411)
* 메모리 문제로 이어질 수 있는 Tomcat 캐시 정리 문제를 수정했습니다. (NEO-13456)
* 을 설치할 때 발생하는 문제를 해결했습니다 **실행 인스턴스를 사용하여 오퍼 엔진 제어** Microsoft SQL 2017에서 실행 중인 기존 제어 인스턴스에 내장된 패키지 (NEO-13539)
* 이메일에서 추적된 URL을 선택 취소할 때 발생할 수 있는 콘솔 충돌 문제를 수정했습니다. **텍스트 컨텐츠** 초기화되지 않은 변수로 인한 탭 (NEO-13545)
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
* 에서 임의 샘플링에 영향을 주는 문제를 해결했습니다 **분할** hadoop FDA 데이터베이스를 사용한 워크플로우 활동. (NEO-16636)
* 업그레이드 후 일부 함수가 유효하지 않은 것으로 간주되는 Oracle의 회귀 문제를 해결했습니다. (NEO-12759)


## 릴리스 19.1{#release-19-1}

### ![](assets/do-not-localize/limited_2.png) 릴리스 19.1.8 - 빌드 9039 {#release-19-1-8-build-9039}

_2021년 4월 15일_

* IMS 연결 화면에서 지속적인 오류 메시지를 발생시킨 클라이언트 콘솔 회귀 문제를 수정했습니다. (NEO-34821)
* FDA 데이터베이스(Teradata, Snowflake)으로 워크플로우 데이터 내보내기를 차단할 수 있는 회귀 문제를 해결했습니다.

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

_2020년 12월 16일_

>[!CAUTION]
>
> * 이 릴리스는 새 연결 프로토콜과 함께 제공됩니다. Adobe IMS(ID 관리 서비스)를 통해 Campaign에 연결할 경우, **2021년 6월 30일** 이후부터 Campaign 서버 및 클라이언트 콘솔은 Campaign에 연결할 수 있도록 업그레이드를 해야 합니다. [자세히 알아보기](../../technotes/using/ims-updates.md)
> * 이 릴리스는 [보안 픽스](https://helpx.adobe.com/security/products/campaign/apsb21-04.html)와 함께 제공됩니다. 환경 보안을 강화하려면 업그레이드가 필요합니다.
> * oAuth 인증을 통해 Experience Cloud 트리거 통합을 사용할 경우 [이 페이지에서](../../integrations/using/configuring-adobe-io.md) 설명한 대로 Adobe I/O로 이동해야 합니다. Campaign의 [레거시 oAuth 인증 모드는](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411?profile.language=ko) **2021년 9월**&#x200B;부로 사용이 중단되었습니다. 호스팅 환경의 경우 **2022년 2월 23일**&#x200B;까지 연장 사용할 수 있습니다. 온-프레미스 또는 하이브리드 고객은 Adobe 고객 지원 센터에 문의하여 2022년 2월로 지원을 연장하십시오. Adobe에 [OAuth 애플리케이션](../../integrations/using/configuring-pipeline.md?lang=en#step-optional)의 AppID를 제공해야 합니다.



**개선 사항**

* 연결 프로토콜은 새 IMS 인증 메커니즘을 따르도록 업데이트되었습니다.
* 기존 oAUTH 인증 설정을 기반으로 파이프라인에 액세스하는 트리거 통합 인증이 변경되었으며 Adobe I/O으로 이동되었습니다. [추가 정보](../../integrations/using/configuring-adobe-io.md)
* iOS APNs 레거시 이진 프로토콜에 대한 지원이 종료됨에 따라 업그레이드 후 이 프로토콜을 사용하는 모든 인스턴스는 HTTP/2 프로토콜로 업데이트됩니다.
* SSRF(Server Side Request Forgery) 공격으로부터 보호를 강화하기 위해 보안 문제를 해결했습니다. (NEO-27777)
* 연결 오류 후 SMPP 커넥터가 비활성화되어 다른 SMS 게재가 전송되지 않고 성능 문제가 발생하는 문제를 해결했습니다.
* 워크플로우 활동을 통해 설명 보고서를 생성할 때 잘못된 백분율을 표시하는 문제를 수정했습니다. (NEO-14314)
* 다음 상황에서 **배달 중 중복 주소 제외** 옵션을 선택하지 않았습니다. (NEO-13240)
* **보강** 활동을 실행할 때 워크플로우가 실패할 수 있는 문제를 해결했습니다. (NEO-17338)
* 외부 데이터베이스에서 레코드를 가져와 캠페인 데이터베이스에 삽입할 때의 워크플로우 문제를 해결했습니다. (NEO-26359)
* 식 구문 분석기를 지울 때 메모리 손상을 방지하여 서버 충돌 문제를 해결했습니다.
* Adobe Analytics 도구에서 **NoNull** 빌드 9032로 업그레이드한 후 Oracle 데이터베이스에서 작업할 때 사용됩니다. (NEO-26488)
* 캠페인 템플릿 설명을 편집 시 기호(예: 일본어 문자)를 복사 및 붙여넣을 때 **저장** 단추가 표시되지 않는 문제를 해결했습니다. (NEO-27071)
* **저장** 단추를 클릭하기 전에 창 외부를 클릭할 때 캠페인 또는 캠페인 템플릿의 설명이 저장되지 않는 문제를 해결했습니다. (NEO-27449)
* 최신 Windows 10 업데이트 후 Adobe Campaign에 로그인할 수 없는 프록시 구성 수준의 문제를 해결했습니다. (NEO-27813)
* MTA 프로세스 동작에 오류가 발생하고 게재 전송에서 성능이 저하되는 로그 파일의 빈 줄 관리와 관련된 문제를 수정했습니다.

**기술 진화**

Tomcat이 버전 7(7.0.103)에서 버전 8(8.5.57)로 업데이트되었습니다. `tomcat-7` 디렉터리가 `tomcat-8` 디렉터리로 대체됩니다. Windows의 경우 _iis_neolane_setup.vbs_ 및 _apache_neolane.conf_&#x200B;가 `conf` 디렉터리(기존 `tomcat-7/conf` 디렉터리 대신)에 설치됩니다. linux의 경우 _apache_neolane.conf_&#x200B;가 이제 `conf` 디렉터리에 설치됩니다.

Linux에서 nlserver 서비스 시작은 이제 /etc/init.d/nlserver6 스크립트 대신 시스템 단위를 사용합니다. 새 시작 구성표로 마이그레이션은 19.1.8 패키지를 설치할 때 자동으로 수행됩니다. /etc/init.d/nlserver6는 여전히 제공되지만 nlserver 서비스(시작, 다시 시작, 중지 등)와 상호 작용하기 위해 systemctl 명령을 직접 사용하는 것이 좋습니다.


### ![](assets/do-not-localize/red_2.png) 릴리스 19.1.7 - 빌드 9036 {#release-19-1-7-build-9036}

_2020년 9월 15일_

**개선 사항**

* nlsrvmod 충돌을 수정하기 위해 Apache 2.4 스레드 사용에 대한 nlsrvmod가 개선되었습니다.
* Azure 외부 계정 및 SSL 암호화와 함께 파일 전송 활동을 사용할 때 발생하는 문제를 해결했습니다. 연결이 HTTPS 대신 HTTP를 통해 수행되었습니다. (NEO-26720)
* 레이블 또는 카테고리를 검색하지 못한 URL 캐시 메커니즘 문제를 해결했습니다.
* 부적절한 ASCII 문자 제어로 인해 이메일 게재에서 미러 페이지 URL이 잘못 정의되는 문제를 해결했습니다. (NEO-26084)
* 더 이상 사용되지 않은 jar 파일에 대한 참조(iOS 알림)를 제거하도록 catalina.properties의 jarToSkip 목록이 업데이트되었습니다.
* 업그레이드 후 게시 작업을 하지 못했던 회귀 문제를 해결했습니다.
* PDF으로 내보낼 때 잘림으로 표시되는 기본 제공 게재 보고서의 회귀 문제를 해결했습니다. (NEO-25757)
* 추적 URL에서 리디렉션할 때 인코딩 매개 변수 값을 삭제한 문제를 해결했습니다(일본어 문자에 영향을 미침). (NEO-25637)
* 개인화된 도메인에서 서명되지 않은 링크가 허용되어야 할 때 차단되는 문제를 해결했습니다. (NEO-25210)
* 워크플로우의 실패를 야기하는 워크플로우 내 계산된 필드에 영향을 주는 회귀 문제를 해결했습니다. (NEO-25194)
* 일부 API 호출이 실행되지 않도록 하는 Microsoft Dynamics(버전 8.2)와의 호환성 문제를 해결했습니다(RetrieveAllEntities). (NEO-24528)
* ACS 커넥터 기능을 사용할 때 Campaign Standard 인스턴스에 연결할 수 없는 회귀 문제를 해결했습니다(FOH/FOH2 연결의 잘못된 관리). (NEO-23433)
* 데이터베이스 인코딩 문제로 웹 서버가 지속적으로 다시 시작되는 데이터베이스 연결의 회귀 문제를 해결했습니다. 이는 과소비를 야기할 수 있습니다. (NEO-23264)
* 관리되지 않는 데이터 소스로 인해 실패할 수 있는 데이터베이스 정리 워크플로우 문제를 해결했습니다. (NEO-23160, NEO-23364)
* 이제 정리 워크플로우는 만료된 목록을 하나씩 제거하는 대신 100개씩 일괄처리합니다.
* [새 시퀀스 ID 메커니즘](https://helpx.adobe.com/kr/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)으로 전환에 따라서 수신자 테이블을 업데이트하는 모든 웹 애플리케이션은 업그레이드 후 다시 게시됩니다.
* HTML 콘텐츠 태그 외부에 Javascript 코드가 있을 때 이메일이 전송되지 않는 문제를 수정했습니다. (NEO-18628)
* 트랜잭션 메시지 추적 표시기가 추적 워크플로우에 의해 업데이트되지 않는 문제를 해결했습니다. (NEO-17770)
* 응답 시간을 최적화하기 위해 데이터베이스 업데이트 마법사의 성능을 개선하여 SQL 문을 줄일 수 있습니다.
* 이메일에서 추적된 URL을 선택 취소할 때 발생할 수 있는 콘솔 충돌 문제를 수정했습니다. **텍스트 컨텐츠** 초기화되지 않은 변수로 인한 탭 (NEO-13545)
* 초기화되지 않은 변수(m_pCurlReader)로 인해 Azure Blob 저장소 외부 계정을 사용하여 파일 전송 활동에 파일을 업로드할 수 없는 문제를 해결했습니다. (NEO-13717)
* 웹 애플리케이션을 다시 게시하기 전에 Apache와 웹 서버가 꺼지는 업그레이드 후 문제를 해결했습니다. (NEO-27155)
* 에서 시간을 설정할 때 잘못된 시간대가 선택되는 회귀 문제를 해결했습니다. **스케줄러** 워크플로우 활동.


### ![](assets/do-not-localize/red_2.png) 릴리스 19.1.6 - 빌드 9035 {#release-19-1-6-build-9035}

>[!CAUTION]
>
>이 빌드는 온-프레미스 설치용입니다. 하이브리드 배포의 경우 호스팅된 인스턴스가 9032 빌드를 계속 실행합니다. 9032와 호환되지 않으므로 마케팅 인스턴스를 9035 빌드로 업그레이드하지 마십시오.

_2019년 10월 3일_

**개선 사항**

* Salesforce용 CRM 커넥터를 사용하는 경우 발생하는 문제를 해결했습니다. (NEO-17712)
* 트랜잭션 메시지를 보낼 때 성능 문제가 발생할 수 있는 인덱스 문제를 해결했습니다.
* 메시지를 보낼 때 발생하는 성능 문제를 해결했습니다. (NEO-17558)
* 중간 소싱 서버에서 특정 메시지가 처리되지 않는 문제를 수정했습니다. (NEO-12395)
* SQL 데이터 관리 활동을 완전히 사용할 수 없는 문제를 해결했습니다(오른쪽 이라는 &quot;SQL 데이터 관리&quot;가 누락됨).

### ![](assets/do-not-localize/red_2.png) 릴리스 19.1.5 - 빌드 9033{#release-19-1-5-build-9033}

_2019년 8월 13일_

**개선 사항**

* 데이터 관리 작업에서 데이터 추출 중에 FDA 데이터베이스가 아닌 기본 데이터베이스에서 실행된 SQL 문 &#39;SELECT COUNT&#39; 문제를 수정했습니다.
* 고객 인프라 기능을 개선하기 위해 이제 서버 구성 파일에서 SFTP 프록시 선언을 사용할 수 있습니다.
* 다음 상황에서 **연결된 테이블 추가** 필드에 비어 있습니다. **데이터 로드(RDBMS)** 워크플로우 활동. (NEO-12213)
* 명령줄에서 midEmitter 패키지 설치 문제를 해결했습니다.
* Microsoft Dynamics를 사용하는 AC 커넥터 내에서 OAuth 자격 증명을 지원하도록 새 인증 옵션이 추가되었습니다. (NEO-11982)
* Hive FDA에서 쿼리 및 데이터 로드 워크플로우 활동이 실패하는 UUID(고유 범용 식별자) 관리 문제를 수정했습니다.
* 업그레이드 후 일부 함수가 유효하지 않은 것으로 간주되는 Oracle의 회귀 문제를 해결했습니다. (NEO-12759)
* 예약 워크플로우 활동에서 시간을 설정할 때 잘못된 시간대가 선택되는 회귀 문제를 해결했습니다.

### ![](assets/do-not-localize/green_2.png) 릴리스 19.1.4 - 빌드 9032{#release-19-1-4-build-9032}


>[!NOTE]
>
>19.1.4 [!DNL Gold Standard] 릴리스는 다음 항목에 나열되어 있습니다. [페이지](../../rn/using/gold-standard.md).


### ![](assets/do-not-localize/red_2.png) 릴리스 19.1.2 - 빌드 9029{#release-19-1-2-build-9029}

_2019년 6월 21일_

**향상된 보안 기능**

* 보안을 최적화하기 위해 Java 라이브러리(Network)가 최신 버전(4.1.34)으로 업데이트되었습니다. (NEO-12788)

**개선 사항**

* 특정 구성에서 전자 메일이 전송되지 않도록 하는 도메인 열 관리에 연결된 회귀 문제를 해결했습니다.
* 성능을 개선하기 위해 _operation=&quot;none&quot; 속성이 rtEvent SOAP 호출에 추가되어 &quot;SELECT FOR UPDATE&quot; 요청을 방지했습니다.
* 테스트 활동 후 아웃바운드 전환 관련 워크플로우 표시 문제를 수정했습니다. (NEO-12727)
* 이제 가져오기 작업 과정 중에 Microsoft Dynamics에서 만든 더미 레코드를 삭제할 수 있습니다.
* 내부 계정을 사용할 때 보안 영역 패키지를 실행하는 권한이 개선되었습니다.


### ![](assets/do-not-localize/red_2.png) 릴리스 19.1 - 빌드 9026{#release-19-1-build-9026}

_2019년 5월 30일_

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
   <td> Campaign 컨트롤 패널<br /> </td> 
   <td> <p>관리자로서 작업의 효율성을 높이려면 저장소 모니터링을 통해 SFTP 서버의 설정을 관리하고, 저장소에 IP 주소허용 목록에 추가하다를 추가하고, 각 인스턴스에 대해 SSH 키를 설치하도록 합니다. 현재 Campaign 컨트롤 패널은 AWS에서 호스팅되는 고객에게만 제공됩니다(<a href="https://experiencecloud.adobe.com/campaign/controlpanel/">오늘 Experience Cloud을 통해 로그인</a>).</p> <p>자세한 내용은 <a href="https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=ko">세부 설명서</a> 및 <a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/control-panel/control-panel-overview.html?lang=ko">방법 비디오</a>를 참조하십시오. </p><p>참고: Campaign 컨트롤 패널에 액세스하려면 최신 Campaign 빌드로 업그레이드할 필요가 없습니다.</p> </td> 
  </tr> 
    <tr> 
   <td> 감사 추적<br /> </td> 
   <td> <p>관리자는 Adobe Campaign Classic 인스턴스 내에서 수행된 변경 사항을 모니터링하고 관리하여 생산성을 높입니다. 감사 추적에서는 소스 스키마, 워크플로우 및 옵션에서 수행한 작업을 기록합니다. 요소의 생성, 수정 또는 삭제 여부를 빠르게 확인할 수 있습니다.</p><p>자세한 내용은 <a href="../../production/using/audit-trail.md">세부 설명서</a> 및 <a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/monitoring/audit-trail.html">방법 비디오</a>.</p></td> 
  </tr> 
  <tr> 
   <td> 보호, 견고성 및 확장성<br /> </td> 
   <td> 일련의 향상된 기능이 Campaign Classic에 추가되었습니다. 보호, 견고성 및 확장성 개선사항은 아래에 나와 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 호환성 매트릭스 업데이트<br /> </td> 
   <td> 이 새 버전에서 Adobe Campaign은 이제 다음 데이터베이스 시스템을 지원합니다. 자세한 내용은 <a href="https://helpx.adobe.com/campaign/kb/compatibility-matrix.html">호환성 매트릭스</a>.<br /> 
    <ul> 
     <li> <p>Oracle 18c</p> </li> 
     <li> <p>MySQL 5.7 (FDA)</p> </li> 
     <li> <p>SQL Server 2017</p> </li> 
     <li> <p>Teradata 16 (FDA)</p> </li> 
     <li> <p>PostgreSQL 11</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**향상된 보안 기능**

* 보안상의 이유로 **[!UICONTROL Pre-process the file]** 옵션 **[!UICONTROL Data loading (file)]** 워크플로우 활동. 이제 3가지 옵션 중에서 선택할 수 있는 드롭다운 목록을 사용할 수 있습니다. **[!UICONTROL None]**, **[!UICONTROL Decompression]** (zcat) 또는 **[!UICONTROL Decrypt]** (gpg). XtkSecurity_Disable_Preproc 보안 플래그가 추가되었습니다. 새 고객의 경우 이 옵션이 0으로 설정됩니다. 기존 고객의 경우 이 옵션은 이전 동작을 유지하기 위해 업그레이드 후 가 1로 설정됩니다. 다음을 참조하십시오 [섹션](../../workflow/using/data-loading--file-.md).
* 표준 시간대가 설정되지 않은 FDA 외부 계정의 연결을 테스트할 때 발생하는 암호 가시성 문제를 해결했습니다.
* PDFBox 라이브러리가 제거되었습니다.
* Tomcat이 버전 7.0.93으로 업데이트되었습니다.
* 보안 토큰이 유효하지 않을 때 발생하는 토큰 가시성 문제를 해결했습니다.
* WSDL JSP(schemawsdl.jsp)의 잠재적 XTK 주입 문제가 수정되었습니다.
* 응용 프로그램의 소스 코드 및 메모리의 자격 증명 및 암호 저장소가 최적화되었습니다.
* PII 보기 제한이 최적화되었습니다. (NEO-12339, NEO-12396, NEO-12398, NEO-12339, NEO-12667)
* 비밀 키 관리의 불일치 문제가 해결되었습니다.
* 이제 유효한 사용자 이름 또는 잘못된 사용자 이름으로 실패한 로그인 시도에 대해 동일한 일반 오류가 표시됩니다.
* 업로드된 파일의 이름이 개선되었습니다.
* setEnv 및 getEnv 함수의 사용을 차단하기 위해 새로운 XtkSecurity_Disable_GetSetEnv 옵션이 추가되었습니다.
* 이제 응용 프로그램 스택 추적에 중요한 정보가 숨겨집니다.

**보호, 견고성 및 확장성 개선 사항**

* 수명 - XtkNewId 시퀀스 사용 최적화: 가장 많이 사용하는 테이블이 xtkNewId 시퀀스에서 전용 시퀀스로 이동되었습니다. [자세히 보기](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)
* HTTP v2를 통한 FDA: HTTP를 통한 FDA 프로토콜은 Hybrid 배포, 특히 broadLog 검색 및 게재 준비에 널리 사용됩니다. 데이터 검색 또는 푸싱과 같은 네트워크 문제와 가능한 오류를 방지하기 위해 견고성 기능이 향상되었습니다. 이렇게 하려면 연결의 양쪽 끝에서 빌드가 최신 상태여야 하며 그렇지 않으면 이전 프로토콜은 계속 사용됩니다.
* 추적 워크플로우: 추적 워크플로우 견고성이 향상되었습니다. 추적 로그 삽입/업데이트 및 URL 추적 사용자 지정과 관련된 몇 가지 문제가 수정되었습니다. 또한 이제 추적 워크플로우에서 오류로 인해 워크플로우를 중지할 수 있는 추적 로그 문제를 감지합니다. 이제 이러한 문제가 삭제되고 처리되지 않습니다.
* 정리 워크플로우: 잠재적인 오류 및 중지를 방지하기 위해 정리 워크플로우가 개선되었습니다. 데이터베이스 크기와 성능을 최적화합니다.
* 트랜잭션 메시지에 포함된 이미지: 가능한 충돌 또는 누락된 이미지를 방지하기 위해 트랜잭션 메시지에 포함된 이미지에 대한 전체 지원을 추가했습니다.
* 데이터베이스 크기 - XtkJobLog: 이 테이블에 제거 메커니즘이 추가되었습니다. 이는 데이터베이스 크기에 긍정적인 영향을 줍니다.
* 숨은 참조 보관: 숨은 참조 보관에 대한 기본 매개 변수가 보관 속도를 증가하도록 변경되었습니다. [자세히 보기](../../installation/using/email-archiving.md#parameters)
* 데이터베이스 구조 업데이트: 데이터베이스 구조 업데이트 마법사에서 생성한 SQL 요청이 개선되어 실행 속도가 빨라졌습니다.
* 운영자 작업에 대한 보호 기능: 연산자가 플랫폼의 무결성에 영향을 줄 수 있는 작업을 수행하지 못하도록 몇 가지 보안 기능이 구현되었습니다. 기본 제공 스키마는 더 이상 인터페이스를 통해 삭제할 수 없습니다. 또한 관리자가 아닌 사용자는 워크플로우 소스 XML을 더 이상 편집할 수 없습니다.
* 두 가지 새로운 옵션을 사용할 수 있습니다. **XtkSecurity_Restrict_EditXML** (게재 버전의 XML 코드를 비활성화할 수 있음) 및 **NmsOperation_OperationMgtDebug** (operationMgt 기술 워크플로우 실행을 모니터링할 수 있습니다.) [자세히 표시](../../installation/using/configuring-campaign-options.md)

**기타 변경 사항**

* 푸시 알림: 이제 iOS 푸시에 대한 스레드 ID 옵션이 지원됩니다.
* 업그레이드 후 문제를 일으킬 수 있는 긴 이름 인덱스 관리를 개선했습니다.
* 이제 디메일 게재를 분석하는 동안 게시 모드가 **[!UICONTROL None]** 배포 마법사에서 오류가 기록되고 분석이 중지됩니다. &quot;게시 모드가 &#39;없음&#39;으로 설정되어 있습니다. 이미지를 포함할 수 없습니다. 기능 휴대폰에는 이미지가 표시되지 않습니다.&quot; (NEO-12208)
* 트랜잭션 메시징을 위해 브로드로그 관리가 개선되었습니다. 브로드로그가 실행 인스턴스에서 제어 인스턴스로 동기화되면 @lastModified 필드가 시스템의 현재 날짜로 업데이트됩니다. 제어 인스턴스에 대해 MC_Update_BlLastModified 옵션이 추가되었습니다. True는 컨트롤 인스턴스(기본 동작)에서 현재 날짜가 사용됨을 의미합니다. False는 실행 인스턴스 브로드로그의 @lastModified 날짜를 사용함을 의미합니다. (NEO-12579)
* 게재 전송을 최적화하기 위해 쿠폰 임시 테이블에 인덱스가 추가되었습니다. (NEO-12437)
* Analytics 통합에서 이제 % 문자로 AAM 세그먼트 데이터를 검색할 수 있습니다. (NEO-12025)
* 누락된 데이터 문제를 해결하기 위해 워크플로우 Heatmap에서 10,000개의 레코드 제한을 제거했습니다. (NEO-12329)
* Open Office는 지원되지 않으며 이제 응용 프로그램에서 완전히 제거됩니다. 계속 사용 중인 경우 19.1부터 더 이상 작동하지 않으므로 Libre Office로 이동합니다.
* 이제 sysfilter 속성을 사용하여 워크플로우에서 데이터 업데이트 활동에 대한 쓰기 액세스를 제한할 수 있습니다. [자세히 보기](../../configuration/using/filtering-schemas.md)

**패치**

* iOS 모바일 푸시 알림에 대해 인증서가 업로드되지 않는 문제를 해결했습니다.
* 트랜잭션 푸시 알림에 대한 잠재적 재귀 서버 충돌을 해결했습니다. 다른 충돌 문제가 해결되었습니다.
* 열려 있는 게재 지표에 대한 사용자 활동과 추적 보고서 간의 불일치를 보고하도록 하는 문제를 해결했습니다. (NEO-11742)
* IMS 로그인 문제를 해결했습니다.
* 라이브러리에서 이미지를 추가할 때 게재에서 이미지가 누락될 수 있는 문제를 수정했습니다. (NEO-11900)
* DM 게재에서 오퍼 세부 사항을 추출할 때 발생할 수 있는 문제를 수정했습니다. (NEO-11700)
* SMS 트랜잭션 메시지 성능에 영향을 줄 수 있는 문제를 해결했습니다. (NEO-9812)
* 게재의 기본 대상에 대해 외부 파일에서 정의 옵션을 사용할 때 발생할 수 있는 콘솔 충돌을 수정했습니다. (NEO-12349)
* 일본어(.JP) 도메인의 수신자를 타겟팅하는 메시지를 분석할 때 발생하는 문제를 해결했습니다. (NEO-12246)
* 1:N 링크에서 값 분포를 사용할 때 발생하는 표시 문제를 수정했습니다. (NEO-12212, NEO-11820)
* 업그레이드 후 MTA 로그에서 NmsMxDomain 오류가 발생할 수 있는 문제를 수정했습니다. (NEO-12752)
* 데이터 보강 워크플로우 활동에서 &quot;기본 세트에서 추가 데이터를 모두 유지&quot; 옵션을 사용할 때 발생하는 문제를 해결했습니다. (NEO-13291)
* HTTP2를 사용하여 푸시 알림을 전송할 때 발생하는 Tomcat 충돌 문제를 해결했습니다. (NEO-12701)
* 모든 콜백이 완료될 때까지 기다리지 않는 HTTPRequest API 관련 문제를 해결했습니다. (NEO-12628)
* 트랜잭션 메시지에 대한 지표 추적 컴퓨팅 프로세스의 문제를 수정했습니다. (NEO-12529)
* 오퍼 관리에서 테마를 사용하는 문제가 해결되었습니다. (NEO-11804)
* 푸시 알림을 전송할 때 발생하는 성능 문제를 해결했습니다. (NEO-11787)
* DM 전달을 위해 오퍼 관리에서 아웃바운드 XML 또는 CSV 파일을 미리 볼 때 발생하는 문제를 수정했습니다. (NEO-11290)
* 을 설치할 때 발생하는 문제를 해결했습니다 **소셜 네트워크 관리** (소셜 마케팅) 패키지 (NEO-12081)
* 올바른 액세스 권한이 있어도 웹 애플리케이션을 삭제할 수 없는 문제를 수정했습니다. (NEO-12072)
* XML을 통해 개체를 내보내고 가져올 때 일부 값을 덮어쓰는 문제가 해결되었습니다. XtkExport_IncludeDefaultValues 옵션이 추가되었습니다. True(기본 동작)로 설정하면 모든 값이 내보내집니다. False로 설정하면 수정 사항이 기본값으로 덮어쓰여집니다. (NEO-11979)
* Adobe Social이 사용자 지정 브랜드 도메인을 인식하지 못하는 원인이 되는 **[!UICONTROL Alert]** 쿼리 후에 데이터 보강 활동을 추가한 경우 워크플로우 활동이 실패합니다. (NEO-12132)
* 데이터베이스에서 파이프라인(트리거) 오프셋이 성공적으로 검색되지 않아 중복 항목이 발생하는 Oracle 설정 문제를 수정했습니다. (NEO-12121)
* Analytics 통합을 사용할 때 피벗 테이블에 표시 오류가 발생하는 문제를 해결했습니다(NEO-12103).
* 설명 분석 보고서 관련 문제를 수정했습니다. (NEO-11414)
* 원격 테이블에 이름에 밑줄이 있는 필드가 포함된 경우 CRM 커넥터 문제를 해결했습니다.
* 가설 보고서에서 통화 기호에 대한 표시 문제를 일으킬 수 있는 문제를 수정했습니다. (NEO-11634)
* 추적 링크에서 특정 문자를 사용할 때 리디렉션 및 추적 문제를 해결했습니다.
* 오퍼 미리 보기가 제대로 작동하지 않는 문제를 수정했습니다.
* 주소 테이블에서 소프트 바운스가 제거되지 않는 문제를 해결했습니다.
* 바코드를 사용할 때 발생하는 JAVA 오류를 수정했습니다.
* 웹 애플리케이션에서 번역 문제가 수정되었습니다(NEO-12460).
* s3 파일 전송 워크플로우 활동 문제를 해결했습니다. (NEO-12473)
* 웹 애플리케이션의 날짜 필드 문제를 수정했습니다. (NEO-12496)
* 게재에서 시드 주소를 사용할 때 발생하는 ID 소모 문제를 수정했습니다. (NEO-11842)
* phantomjs 및 Debian 9 호환성 문제가 해결되었습니다.
* 증명 컨텐츠를 승인할 때 발생하는 오류를 수정했습니다. (NEO-12725)
* 모집단에서 이 하위 집합 제외 워크플로우 기능 문제를 수정했습니다. (NEO-12441)
* 모든 콜백이 완료될 때까지 기다리지 않는 HTTPRequest-wait API 관련 문제를 해결했습니다. (NEO-12628)
* 분할 활동에서 &quot;공유 대상 업데이트&quot; 작업 문제를 수정했습니다. (NEO-11562)
* 웹 서버 충돌 문제가 해결되었습니다. (NEO-12904)
* 트랜잭션 템플릿의 특성 매개 변수 문제를 수정했습니다. (NEO-12334)
* 추적된 URL을 이메일 텍스트 편집기에서 표시할 때 콘솔 충돌 문제를 수정했습니다. (NEO-13122)
* Audience Manager에서 대상자를 가져올 때 파일 분할 활동 문제를 해결했습니다. (NEO-11550)
* 핫 클릭 보고서에 오류가 발생하는 문제를 수정했습니다. (NEO-11459)
* 오퍼 렌더링 문제를 수정했습니다. (NEO-11565)
* Audience Manager에서 대상을 가져올 때 목록 업데이트 활동 문제를 해결했습니다. (NEO-11226)
* 예약 활동 및 시간대 구성 문제를 해결했습니다. (NEO-11662)
* 잘못된 형식의 URL의 경우 추적 워크플로우가 실패하는 문제를 해결했습니다.
* 모바일 애플리케이션 패키지를 가져온 후 외부 계정 문제를 해결했습니다.
* 연산자에 시간대를 할당할 때 발생하는 문제를 수정했습니다. (NEO-12464)
* 일치하는 필드 로그에 오류가 발생할 수 있는 문제를 수정했습니다. (NEO-11539, NEO-8978)
* 저장된 보고서에서 내역 아이콘을 클릭할 때 발생하는 문제를 수정했습니다. (NEO-11620)
* 보고서에서 피벗 테이블을 편집할 때 발생하는 문제를 해결했습니다. (NEO-12068)
