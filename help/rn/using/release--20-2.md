---
product: campaign
title: 릴리스 20.2
description: 릴리스 20.2
feature: 개요
role: User
level: Beginner
exl-id: fcaab1aa-c8f9-4606-b0d8-eb481a38f588
source-git-commit: 601cc3883d7fa8abaa86161365c4230cbe30765c
workflow-type: tm+mt
source-wordcount: '2979'
ht-degree: 87%

---

# 릴리스 20.2{#release-20-2}

## ![](assets/do-not-localize/limited_2.png) 릴리스 20.2.5 - 빌드 9188 {#release-20-2-5-build-9188}

_2021년 4월 15일_

* IMS 연결 화면에서 지속적인 오류 메시지를 발생시킨 클라이언트 콘솔 회귀 문제를 수정했습니다. (NEO-34821)

**콘솔 업그레이드는 필수 사항입니다. 서버를 업그레이드할 필요가 없습니다.**

>[!NOTE]
>
> [Adobe 소프트웨어 배포](https://experience.adobe.com/#/downloads/content/software-distribution/ko/campaign.html)에 연결하여 새 버전을 다운로드합니다. [이 페이지에서](../../installation/using/client-console-availability-for-windows.md) 모든 최종 사용자에게 콘솔 업데이트를 제안하는 방법을 알아봅니다.

_2021년 3월 31일_

**개선 사항**

* 잘못된 soap 호출에서 충돌을 방지하기 위해 기능이 향상되었습니다. 이로 인해 특정 복잡한 쿼리를 실행하려고 할 때 인스턴스 작동이 중지될 수 있습니다. (NEO-28796, NEO-30553)
* 호스트 이름 확인으로 인해 TLS가 있는 SMS 게재가 전송되지 않는 회귀 문제를 해결했습니다. (NEO-29581)
* 일부 이메일 클라이언트에서 서명된 추적 링크가 작동하지 않는 문제를 수정했습니다. (NEO-28414, NEO-29615)
* webApp 추적 태그를 사용할 때 중복 ID와 충돌할 수 있는 추적 ID 시퀀스를 수정했습니다. (NEO-27931)
* 일별 wfserver 다시 시작으로 인해 실행 중인 워크플로우가 중지되는 문제를 해결했습니다. (NEO-30047)
* Adobe Experience Manager 템플릿을 동기화하려고 할 때 관리자가 아닌 사용자가 API 호출을 사용하는 보안 문제를 해결했습니다. (NEO-32389, NEO-23487)
* 템플릿으로 만든 게재에서 게재 대화 상자를 닫을 때 콘솔이 충돌하는 문제를 해결했습니다. (NEO-31547)
* 캠페인의 **타깃팅 및 워크플로우** 탭 내에서 게재를 만들고 저장할 때 발생하는 문제를 해결했습니다. 다음 오류가 발생하여 미리 보기가 실패합니다. (NEO-29440)
* 트랜잭션 메시지 로그에 오류가 발생하는 잘못된 답변을 보내는 Tomcat 8.5 문제를 수정했습니다. (NEO-30858)
* 외부 스레드 관리의 메모리 손상을 야기하고 성능에 영향을 주는 회귀 문제를 해결했습니다.
* 사용자 지정 대상 매핑을 사용할 때 청구 워크플로우가 실패할 수 있는 문제를 수정했습니다. 사용자 지정 스키마의 기본 키는 허용되는 정수 값만 사용하는 &#39;sourceId&#39; 열에 저장됩니다. 이제 문자열 값과 정수를 사용할 수 있습니다. (NEO-25914, NEO-28146)
* 게재의 날짜 선택 및 이미지 관리와 같이 콘솔의 일부 구성 요소를 사용할 수 없는 회귀 문제를 해결했습니다. (NEO-31453)

## ![](assets/do-not-localize/red_2.png) 릴리스 20.2.4 - 빌드 9187 {#release-20-2-4-build-9187}

_2021년 4월 15일_

* IMS 연결 화면에서 지속적인 오류 메시지를 발생시킨 클라이언트 콘솔 회귀 문제를 수정했습니다. (NEO-34821)
* 게재의 날짜 선택 및 이미지 관리와 같이 콘솔의 일부 구성 요소를 사용할 수 없는 회귀 문제를 해결했습니다. (NEO-31453, NEO-31454)

**콘솔 업그레이드는 필수 사항입니다. 서버를 업그레이드할 필요가 없습니다.**

>[!NOTE]
>
> [Adobe 소프트웨어 배포](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)에 연결하여 새 버전을 다운로드합니다. [이 페이지에서](../../installation/using/client-console-availability-for-windows.md) 모든 최종 사용자에게 콘솔 업데이트를 제안하는 방법을 알아봅니다.

_2020년 12월 22일_

>[!CAUTION]
>
> * 이 릴리스는 새 연결 프로토콜과 함께 제공됩니다. Adobe IMS(ID 관리 서비스)를 통해 Campaign에 연결할 경우, **2021년 6월 30일** 이후부터 Campaign 서버 및 클라이언트 콘솔은 Campaign에 연결할 수 있도록 업그레이드를 해야 합니다.  [자세히 알아보기](../../technotes/ims-updates.md)
> * 이 릴리스는 [보안 픽스](https://helpx.adobe.com/kr/security/products/campaign/apsb21-04.html)와 함께 제공됩니다. 환경 보안을 강화하려면 업그레이드가 필요합니다.
> * oAuth 인증을 통해 Experience Cloud 트리거 통합을 사용할 경우 [이 페이지에서](../../integrations/using/configuring-adobe-io.md) 설명한 대로 Adobe I/O로 이동해야 합니다. Campaign이 있는 기존 oAuth 인증 모드는 하이브리드 및 온-프레미스 환경의 경우 **8월 18일, 호스팅된 환경의 경우** 2021년 11월 30일&#x200B;**에서 사용이 중단됩니다.**


**개선 사항**

* 연결 프로토콜은 새 IMS 인증 메커니즘을 따르도록 업데이트되었습니다.
* 기존 oAUTH 인증 설정을 기반으로 파이프라인에 액세스하는 트리거 통합 인증이 변경되었으며 Adobe I/O으로 이동되었습니다. [자세히 알아보기](../../integrations/using/configuring-adobe-io.md)
* [iOS APNs 레거시 이진 프로토콜에 대한 지원 종료](https://developer.apple.com/kr/news/?id=c88acm2b)에 따라 업그레이드 이후 이 프로토콜을 사용하는 모든 인스턴스는 HTTP/2 프로토콜로 업데이트됩니다.
* SSRF(Server Side Request Forgery) 공격으로부터 보호를 강화하기 위해 보안 문제를 해결했습니다. (NEO-27777)
* 연결 오류 후 SMPP 커넥터가 비활성화되어 다른 SMS 게재가 전송되지 않고 성능 문제가 발생하는 문제를 해결했습니다. (NEO-28609)
* 식 구문 분석기를 지울 때 메모리 손상을 방지하여 서버 충돌 문제를 해결했습니다. (NEO-26856)
* 워크플로우에서 **분할** 작업 중 나머지 부분의 타겟 데이터를 표시할 때 서버가 충돌하는 문제를 해결했습니다.
* **수신자**(nms:recipient)가 아닌 다른 스키마에서 쿼리 후에 SMS 메시지를 미리 볼 때 오류 메시지를 표시하는 문제를 해결했습니다. (NEO-27517)
* 호스트 이름에 명시적으로 정의된 포트 번호로 HTTPS 연결 요청을 만들 때 인증서 오류로 인해 호출이 실패하던 문제를 수정했습니다. (NEO-29146)
* 마케팅 인스턴스에서 큰 코어 덤프 파일을 생성한 POSIX 스레드 관리 문제를 수정했습니다. (NEO-28117, NEO-29281)
* 게재를 준비하거나 되풀이하는 게재 미리 보기를 사용할 때 웹 프로세스가 충돌할 수 있는 문제를 해결했습니다. (NEO-27790, NEO-27517)
* 관리자가 아닌 연산자에 의해 트리거될 때 게재 또는 증명 전송이 실패하는 문제를 해결했습니다. (NEO-28597)

![](assets/do-not-localize/cp-icon.png) CNAME과 새로운 데이터베이스 모니터링 기능을 사용하는 도메인 구성이 포함된 **새로운 10월 Campaign 컨트롤 패널 릴리스**. [자세히 알아보기](https://experienceleague.adobe.com/docs/control-panel/using/release-notes.html?lang=ko)

## ![](assets/do-not-localize/red_2.png) 릴리스 20.2.3 - 빌드 9182 {#release-20-2-3-build-9182}

_2020년 9월 11일_

* 게재 부분의 잘못된 기능 하나 때문에 메모리 과부하가 발생하여 게재 준비의 차단을 야기하는 회귀 문제를 해결했습니다. (NEO-27346)
* 웹 애플리케이션을 다시 게시하기 전에 Apache와 웹 서버가 꺼지는 업그레이드 후 문제를 해결했습니다. (NEO-27155)
* 탭의 잘못된 해석으로 인해 URL 추적이 표시되는 HTML 템플릿 관리에서의 회귀 문제를 해결했습니다. (NEO-25909)
* 관리되지 않는 데이터 소스로 인해 실패할 수 있는 데이터베이스 정리 워크플로우 문제를 해결했습니다. (NEO-23160, NEO-23364)
* 이제 정리 워크플로우는 만료된 목록을 하나씩 제거하는 대신 100개씩 일괄처리합니다.
* 외부 계정의 내부 이름을 수정할 수 없는 회귀 문제를 해결했습니다. (NEO-27323)
* nlserver(오류 로그)의 잘못된 시작을 야기하는 업그레이드 후 회기를 해결합니다.
* 공유 메모리에 대한 업데이트 관리가 개선되었습니다. 20.2에서 필요한 추가 단계는 더 이상 필요하지 않습니다.

## ![](assets/do-not-localize/red_2.png) 릴리스 20.2.2 - 빌드 9180 {#release-20-2-2-build-9180}

_2020년 7월 22일_

* 서명 기능이 비활성화되었을 때 추적을 수행할 수 없는 문제를 해결했습니다. (NEO-26411)
* 개인화된 도메인에서 서명되지 않은 링크가 허용되어야 할 때 차단되는 문제를 해결했습니다. (NEO-25210)
* 특정 이전 버전의 Outlook을 사용할 때 추적 URL을 열거나 클릭하지 못하는 문제를 해결했습니다. (NEO-25688)
* 부적절한 ASCII 문자 제어로 인해 이메일 게재에서 미러 페이지 URL이 잘못 정의되는 문제를 해결했습니다. (NEO-26084)
* 피싱 방지 서비스에서 인코딩 URL 관리 문제를 해결했습니다. (NEO-25283)
* 개인화 매개 변수의 조각을 사용하여 URL을 추적할 수 없는 문제(파운드 기호가 있는 앵커 태그)를 해결했습니다. (NEO-25774)
* 특정 사용자 지정 추적 공식을 사용할 때의 추적 문제를 해결했습니다. (NEO-25277)
* &quot;알림 클릭&quot; 추적이 작동하지 않는 문제를 해결했습니다(iOS 및 Android 푸시 알림). (NEO-25965)
* 워크플로우의 실패를 야기하는 워크플로우 내 계산된 필드에 영향을 주는 회귀 문제를 해결했습니다. (NEO-25194)
* 웹 추적 URL 즉시 만들기가 작동하지 못하게 하는 회귀 문제를 해결했습니다. (NEO-20999)
* PDF로 내보낼 때 잘림으로 표시되는 기본 제공 게재 보고서의 회귀 문제를 해결했습니다. (NEO-25757)
* 배포 마법사의 충돌 문제를 해결했습니다.
* 업그레이드 후 오퍼 알림 워크플로우가 제대로 작동하지 않는 문제를 해결했습니다.
* iOS HTTP2 커넥터가 개선되었습니다(타사 업데이트 및 오류 관리). (NEO-25904, NEO-25903)
* 더 이상 사용되지 않은 jar 파일에 대한 참조(iOS 알림)를 제거하도록 catalina.properties의 jarToSkip 목록이 업데이트되었습니다.
* 업그레이드 후 게재 준비를 차단하는 문제를 해결했습니다.
* [새 시퀀스 ID 메커니즘](https://helpx.adobe.com/kr/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)으로 전환에 따라서 수신자 테이블을 업데이트하는 모든 웹 애플리케이션은 업그레이드 후 다시 게시됩니다.
* 게재 콘텐츠의 잠재적 XSS 취약성 문제를 해결했습니다. (NEO-17987, NEO-26073)

![](assets/do-not-localize/cp-icon.png) 활성 프로필 모니터링, 하위 도메인 게재 기능 감사 및 GPG 키 관리가 포함된 **새로운 제어판 6월 릴리스** . [자세히 알아보기](https://experienceleague.adobe.com/docs/control-panel/using/release-notes.html)

## ![](assets/do-not-localize/red_2.png) 릴리스 20.2.1 - 빌드 9178 {#release-20-2-1-build-9178}

_2020년 6월 8일_

**새로운 기능**

<table> 
 <thead> 
  <tr> 
   <th> <strong>이모티콘 지원</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Campaign에서 메시지를 디자인할 때 이제 전용 단추를 사용하여 메시지 본문에 이모티콘을 쉽게 삽입할 수 있습니다. 전자 메일 제목 줄에도 추가할 수 있습니다. 인터페이스에서 사용 가능한 이모티콘 목록을 사용자 지정할 수 있습니다.</p>
    <p>이모티콘 추가에 대한 자세한 내용은 <a href="../../delivery/using/defining-the-email-content.md#inserting-emoticons">세부 설명서</a>를 참조하십시오. <a href="../../delivery/using/customizing-emoticon-list.md">이 섹션</a>에서 이모티콘 목록 을 사용자 지정하는 방법을 배웁니다.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Azure Synapse FDA 커넥터</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>이제 캠페인 인스턴스를 Azure Synapse 외부 데이터베이스에 연결할 수 있습니다. 이 연결은 새 외부 계정을 통해 관리됩니다.</p>
    <p>Azure Synapse는 하이브리드 및 온-프레미스 환경에서만 사용할 수 있습니다. 자세한 내용은 <a href="../../installation/using/configure-fda-synapse.md">세부 설명서</a>를 참조하십시오.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>태국 및 브라질 개인 정보 보호 법</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>태국 개인 정보 보호법(PDPA)은 태국에 대한 데이터 보호 요구 사항을 통합하고 현대화한 새로운 개인 정보 보호법입니다. </p>
   <p>브라질의 Lei Geral de Proteção de Dados(LGPD)는 2021년 초부터 브라질에서 개인 데이터를 수집하거나 처리하는 모든 회사에 효력을 발휘합니다.</p>
   <p>이러한 규정은 해당 국가에 있는 데이터 주체의 데이터를 보유하고 있는 Adobe Campaign 고객에게 적용됩니다. Adobe는 Adobe Campaign에서는 이미 사용 가능한 개인 정보 보호 기능(동의 관리, 데이터 보존 설정 및 사용자 역할 포함) 이외에도 다음과 같은 추가 기능을 추가하여 PDPA 및 LGPD에 대한 준비를 도울 수 있습니다.</p>
   <ul> 
     <li><p>액세스 권한 및 삭제 권한: GDPR 및 CCPA에 추가된 기능을 활용하고 있습니다. <a href="https://helpx.adobe.com/kr/campaign/kb/acc-privacy.html">자세한 내용</a></p></li> 
     <li> <p>이제 Campaign 인터페이스 또는 API를 사용하여 개인 정보 요청을 만들 때 PDPA, LGPD, GDPR, CCPA와 같은 <strong>규정</strong> 유형을 선택합니다. <a href="https://helpx.adobe.com/kr/campaign/kb/acc-privacy.html#ManagingPrivacyRequests">자세한 내용</a></p></li>
    </ul>
   </td> 
  </tr> 
 </tbody> 
</table>

**향상된 보안 기능**

* 전자 메일 링크 추적에 대한 개선된 보안 기능이 모든 고객에 대해 기본적으로 활성화되어 있습니다. 고객 지원 센터에 연락하여 활성화할 수 있는 향상된 추가 보안 기능을 사용할 수 있습니다. 호스팅되지 않은 고객이 이 기능을 사용하도록 설정하는 기능 및 단계에 대한 자세한 내용은 [보안 및 개인 정보 보호 체크리스트](https://helpx.adobe.com/kr/campaign/kb/acc-security.html)에서 확인할 수 있습니다. (NEO-24232)

* 보안을 최적화하기 위해 파일 이름을 생성하는 데 사용되는 MD5 해싱 알고리즘이 공개 파일 업로드를 위해 sha256으로 보강되었습니다. (NEO-17044)

* XSS 공격에 대한 보안을 강화하기 위해 미러 페이지를 실행할 때 클라이언트측 스크립트가 비활성화됩니다. (NEO-17987)

* **개인 정보 보호 요청 파일 정리** 기술 워크플로우가 조정 데이터를 삭제하지 못하는 문제를 해결했습니다. (NEO-25168, NEO-21004)

* SFTP 키 기반 인증이 Debian 9에서 작동하지 않는 **파일 전송** 활동 문제를 해결했습니다. (NEO-23183)

**향상된 호환성**

이제 다음 시스템이 Campaign에서 지원됩니다.
* 운영 체제: Debian 10
* RDBMS: Oracle 18c 및 Oracle 19c
* FDA: Azure Synapse Analytics

자세한 내용은 [Campaign 호환성 매트릭스](https://helpx.adobe.com/kr/campaign/kb/compatibility-matrix.html)를 참조하십시오.

**개선 사항**

* 트랜잭션 메시지 기능이 개선되어 사용자 경험이 향상되었습니다. 이제 실행 인스턴스에서 삭제되는 트랜잭션 메시지 템플릿을 게시 취소할 수 있습니다. [자세히 알아보기](../../message-center/using/publishing-message-templates.md#template-unpublication)

* 이미지나 첨부 파일이 포함된 전자 메일을 보낼 때 제한을 설정하는 새로운 옵션을 사용할 수 있습니다. 이러한 경고는 성능 문제를 방지할 수 있으며 이는 트랜잭션 메시징에서 특히 유용합니다. [자세한 내용](../../installation/using/configuring-campaign-options.md#delivery)

* 새로운 **데이터베이스 게재 부분 준비** 옵션을 사용하면 데이터베이스 내에서 직접 게재 준비를 수행할 수 있으므로 분석 시간을 크게 단축할 수 있습니다. 이 옵션은 특정 구성에만 사용할 수 있습니다. [자세히 알아보기](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis) (NEO-23886)

* Microsoft Dynamics용 [CRM 커넥터 작업](../../workflow/using/crm-connector.md) 성능이 개선되었습니다. (NEO-13303, NEO-12710)

* 공유 메모리 버전이 증가했습니다.

   >[!WARNING]
   >
   >이 개선 사항은 업그레이드를 수행한 후 추가 단계가 필요합니다. 아래의 **기술 진화** 섹션을 참조하십시오.

* 정리 워크플로우가 향상되었습니다. 이제 삭제된 모든 워크플로우의 분리된 작업 테이블도 정리 워크플로우에 의해 자동으로 삭제됩니다. [자세히 알아보기](../../production/using/database-cleanup-workflow.md#cleanup-of-workflow-instances)

* 이제 푸시 알림을 전송하기 전에 iOS HTTP2 커넥터를 사용하는 iOS 모바일 애플리케이션에 대한 인증서의 유효성을 검사하여 인증서 만료로 인해 게재의 실패를 방지합니다.

* HTTP 프록시 연결 관리가 개선되었습니다. [자세히 알아보기](../../installation/using/file-res-management.md)

* 제한 후 실행을 중지하는 **[!UICONTROL Javascript Code]** 및 **[!UICONTROL Advanced Javascript Code]** 워크플로우 활동의 새 옵션입니다. 기본값은 1시간입니다. [자세히 알아보기](../../workflow/using/sql-code-and-javascript-code.md#javascript-code)

**기타 변경 사항**

* 레거시 SMS 커넥터는 이제 사용되지 않습니다. [사용되지 않는 기능 페이지](../../rn/using/deprecated-features.md)를 참조하십시오.

* 더 이상 자체 리트머스 계정을 사용하여 Adobe Campaign에서 받은 편지함 렌더링을 프로비저닝하고 사용할 수 없습니다. [자세히 알아보기](../../delivery/using/inbox-rendering.md)

* 뷰를 폴더와 구분하기 위해 뷰 이름의 색상이 짙은 파란색에서 어두운 녹청색으로 변경되었습니다. [자세한 내용](../../platform/using/access-management-folders.md)

* 이제 Campaign Classic을 영국, 인도 및 캐나다 지역에서 호스팅되는 Microsoft Dynamics CRM 계정에 연결할 수 있습니다. 이는 Office 365 및 온-프레미스(Dynamics 2015) 배포 유형에 적용됩니다.

* 이제 Campaign에서 TLS 확인을 수행하여 서버의 호스트 이름이 제공된 인증서의 호스트 이름과 일치하는지 확인합니다.

* 이제 게재 및 추적 통계 표에는 게재 수신자당 하나의 항목이 아니라 SMS 채널에 대해 게재당 하나의 항목이 표시됩니다.

* 다운로드한 파일이 디스크 공간보다 클 때 사용자에게 경고하기 위해 로그 파일에 오류 메시지가 추가되었습니다.

* 이제 Snowflake 커넥터에 다음 기능을 사용할 수 있습니다. MonthsAgo, DaysAgoInt, ToDateTime, YearsAgo.

**기술 진화**

이 새로운 빌드는 공유 메모리를 업데이트하며 업그레이드를 수행하는 추가 단계가 필요합니다. Campaign 관리자는 메모리 세그먼트를 제거해야 합니다. 이전 세그먼트로 인해 nlserver/nlsrvmod가 시작되지 않게 되므로 이러한 단계는 필수입니다.

Windows에서는 시스템을 다시 시작해야 합니다.

Debian/CentOs에서 공유 메모리 삭제가 필요합니다. 다음은 단계입니다.

업그레이드 전에 다음 단계를 수행해야 합니다.

1. 실행 중인 경우 apache2(CentOS의 http2) 서비스를 중지합니다.
1. 실행 중인 경우 nlserver(이전 빌드의 경우 nlserver6) 서비스를 중지합니다.

업그레이드 후:

1. 버전이 현재 버전보다 오래된 경우 **ipcrm** 명령을 사용하여 공유 메모리를 제거합니다.
1. 실행 중인 경우 nlserver 서비스를 시작합니다.
1. 실행 중인 경우 Apache2서비스를 시작합니다.

다음은 Debian의 명령줄입니다.

```
/etc/init.d/nlserver* stop
/etc/init.d/apache2 stop

for i in `ipcs -s | awk '/www-data/
{print $2}'`; do (ipcrm -s $i); done

for i in `ipcs -m | awk '/www-data/ {print $2}
'`; do (ipcrm shm $i); done

for i in `ipcs -m | awk '/neolane/
{print $2}'`; do (ipcrm shm $i); done

for i in `ipcs -s | awk '/neolane/ {print $2}
'`; do (ipcrm -s $i); done

/etc/init.d/apache2 restart
/etc/init.d/nlserver* start
```

Linux의 예는 이 [페이지](../../configuration/using/additional-parameters.md#redirection-server-configuration)에서 확인할 수 있습니다.

**패치**

* 정리 워크플로우 로그에서 사소한 회귀 문제를 해결했습니다.
* WSDL 파일을 구문 분석할 때 워크플로우 **로딩(SOAP)** 활동의 문제를 해결했습니다.
* 많은 수의 워크플로우를 효율적으로 처리하기 위해 **설문 조사** 활동을 사용하여 많은 워크플로우를 업그레이드할 때 오류가 발생하는 문제를 해결했습니다.
* 향상된 MTA에서 inMail 메시지를 처리하는 동안 일시적인 연결 문제를 해결했습니다. (NEO-20380)
* HTML에서 이미지가 100% 폭으로 표시될 때 핫 클릭 비율이 제대로 표시되지 않는 문제를 해결했습니다. (NEO-23203)
* 게재 조건부 콘텐츠가 핫 클릭 보고서에 완전히 표시되지 않는 문제를 해결했습니다. (NEO-18729)
* 반복 게재를 보내는 워크플로우를 다시 시작할 때 대상 승인 단계를 건너뛰던 문제를 해결했습니다. (NEO-18166)
* 워크플로우에서 오류를 수정한 후 **메시지 다시 시작 준비** 단추가 게재를 다시 시작하지 못하는 문제를 해결했습니다. (NEO-13488)
* 대상이 일본어 전자 메일 형식에 수신자를 포함하는 램프 업 단계 중에 중간 소싱 모드에서 게재가 실패할 수 있는 문제를 해결했습니다. (NEO-23846)
* Snowflake 커넥터의 표준 시간대 변환 문제를 해결했습니다.(NEO-20105).
* SSL을 통해 FTP를 사용하는 외부 계정 문제를 해결했습니다. (NEO-20498)
* 라인 게재에서 이미지가 표시되지 않는 문제를 해결했습니다. (NEO-23207)
* 오퍼를 게시할 때 오류가 발생하던 문제를 해결했습니다. (NEO-23312)
* 인증서가 만료된 경우에도 모바일 애플리케이션에서 테스트 연결이 작동되도록 허용하는 푸시 알림 문제를 해결했습니다. (NEO-22991)
* 높은 빈도로 전송할 때 푸시 알림에 영향을 줄 수 있는 문제를 해결했습니다. (NEO-20516)
* 추적 로그가 기록하지 않았음에도 불구하고 추적 데이터에 중복 항목이 포함되는 문제를 해결했습니다. (NEO-20040)
* 추적 서버 통신 오류가 해결된 후 중복 트랜잭션 전자 메일이 전송되던 문제를 해결했습니다. (NEO-23640)
* 추적 URL에서 리디렉션할 때 인코딩 매개 변수 값을 삭제한 문제를 해결했습니다(일본어 문자에 영향을 미침). (NEO-25637)
* 부동 소수를 비교할 때 쿼리가 작동하지 않던 문제를 해결했습니다. (NEO-23243)
* 워크플로우를 다시 시작한 후 **수정한 사람** 열 콘텐츠가 표시되지 않는 문제를 해결했습니다. (NEO-23035)
* 두 번째 컨테이너에서 로그를 다운로드할 때 추적 기술 워크플로우가 실패하는 문제를 해결했습니다. (NEO-23159)
* **보강** 활동을 실행할 때 워크플로우가 실패할 수 있는 문제를 해결했습니다. (NEO-17338)
* null 또는 음수 값을 입력할 수 없도록 **중복 제거** 워크플로우 활동 내 **Double 유지** 필드에 확인이 추가되었습니다.
* 시간 및 분이 언급되지 않도록 반복 캠페인에서 **스케줄러 마법사**&#x200B;를 제거했습니다. 날짜만 고려합니다.
* **스크립트** 워크플로우 활동의 **스크립트로 계산됨 옵션**&#x200B;을 통해 게재를 만들 때 추가 스토리지 필드의 문제를 해결했습니다. (NEO-20609)
* 데이터베이스 정리 작업 내에서 유령 워크플로우가 삭제되지 않는 문제를 해결했습니다.
* **청구(활성 프로필)** 기술 워크플로우가 실패하는 문제를 해결했습니다. (NEO-19777)
* ACS 커넥터 기능을 사용할 때 Campaign Standard 인스턴스에 연결할 수 없는 회귀 문제를 해결했습니다(FOH/FOH2 연결의 잘못된 관리). (NEO-23433)
* Hadoop 테이블이 있는 열이 여러 개인 기본 키에 스키마 확장을 만들 수 없는 문제를 해결했습니다. (NEO-17390)
* WSDL 파일이 URL에서 로드되지 않도록 하는 **로딩 (SOAP)** 활동의 문제를 해결했습니다. (NEO-16924)
* 여러 활성 워크플로우 서버가 부하 분산을 했을 때 콘솔을 통해 **무조건적 정지**&#x200B;를 수행하지 못하는 문제를 해결했습니다. (NEO-19556)
* 정리 워크플로우가 충돌하는 회귀 문제를 해결했습니다.
* 실행 인스턴스에 템플릿을 게시할 때 발생할 수 있는 문제를 해결했습니다.
* collectPrivacyRequests 기술 워크플로우가 실행되지 않는 문제를 해결했습니다. (NEO-20513, NEO-25169)
* 빌드 9080로 업그레이드한 후 Audience Manager에 연결하려고 할 때 발생하는 문제를 해결했습니다. (NEO-20511, NEO-25167)
* 보고서를 PDF 또는 XLS 형식으로 내보낼 때 발생하는 문제를 해결했습니다. (NEO-20982, NEO-23493, NEO-23348)
* 전송 후 게재 목록에 게재를 두 번 표시할 수 있는 문제를 해결했습니다.
* 중간 소싱을 통해 게재를 전송하도록 라우팅 구성을 설정할 때 발생할 수 있는 게재 준비 문제를 해결했습니다.
* 라인 메시지 내에서 웹 애플리케이션 링크를 클릭할 때 오류 메시지가 표시되는 문제를 해결했습니다.
* 정리 워크플로우를 실행한 후 **증분 쿼리** 활동 내역을 삭제하는 문제를 해결했습니다.
* 중간 소싱 외부 계정을 만들 때 NmsMidSourcing_LastBroadLog_&lt;InternalName> 옵션이 누락되는 문제를 해결했습니다..
* 데이터베이스 인코딩 문제로 웹 서버가 지속적으로 다시 시작되는 데이터베이스 연결의 회귀 문제를 해결했습니다. 이는 과소비를 야기할 수 있습니다. (NEO-23264)
