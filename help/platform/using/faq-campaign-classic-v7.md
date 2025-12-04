---
product: campaign
title: Campaign Classic FAQ
description: Adobe Campaign Classic v7 아키텍처, 배포 및 기능과 관련된 질문
feature: Overview, Troubleshooting
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
source-git-commit: 295e3596d9291cbcc55e2d264309141526c3806b
workflow-type: tm+mt
source-wordcount: '1527'
ht-degree: 2%

---

# Campaign Classic v7 FAQ {#campaign-classic-v7-faq}

이 FAQ는 Adobe Campaign Classic v7 아키텍처, 배포 모델 및 v7 관련 기능과 관련된 질문을 해결합니다.

**일반적인 Campaign 질문에 대한 포괄적인 답변**(워크플로우, 게재, 대상, 보고, 개인화 등)은 주제별로 구성된 자세한 답변을 제공하는 [**Campaign v8 포괄적인 FAQ**](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html){target="_blank"}를 참조하십시오.

## Campaign Classic v7 아키텍처 및 배포 {#v7-architecture}

### Campaign Classic v7에서 사용할 수 있는 호스팅 모델은 무엇입니까? {#what-are-the-hosting-models-available-in-campaign-classic-v7}

Adobe Campaign Classic v7은 다음 세 가지 배포 모델을 제공합니다.

* **호스팅(Managed Services)** - Adobe 인프라의 Adobe에서 완전히 관리됨
* **온-프레미스** - 자체 인프라에 설치 및 관리됨
* **하이브리드** - 클라우드와 온-프레미스 구성 요소가 혼합된 중간 소싱 아키텍처

각 배포 모델에는 다양한 기능과 관리 책임이 있습니다. 모듈, 옵션 및 구성의 사용 가능 여부는 배포 유형에 따라 다릅니다.

호스팅 모델 및 차이점에 대해 [자세히 알아보려면 여기를 클릭하세요](../../installation/using/hosting-models.md).

**참고:** Campaign v8은 관리 클라우드 서비스로만 사용할 수 있습니다. [Campaign v8에 대해 알아봅니다](https://experienceleague.adobe.com/docs/campaign/campaign-v8/new/whats-new.html){target="_blank"}.

### 온프레미스 및 호스팅 환경에서 작업하는 경우의 차이점은 무엇입니까? {#what-are-the-differences-when-working-on-premise-vs-in-a-hosted-environment}

Adobe Campaign Classic v7에는 모듈 및 옵션 세트가 포함되어 있습니다. 이러한 모듈 및 구성 사용 가능 여부는 설치 [배포 유형](../../installation/using/hosting-models.md)에 따라 다릅니다. 호스팅(Managed Services), 하이브리드 또는 온-프레미스입니다.

주요 차이점:

* **온-프레미스** - 설치, 인프라 및 구성에 대한 모든 권한. 유지 관리, 업그레이드 및 보안을 위해 내부 IT 리소스가 필요합니다.
* **호스팅/Managed Services** - Adobe에서 관리하는 인프라 및 유지 관리. 자동 업그레이드 및 향상된 보안. 제한된 직접 서버 액세스.
* **하이브리드** - 두 모델의 이점을 결합합니다. Adobe에서 호스팅하는 마케팅 인스턴스, 실행/중간 소싱이 별도로 관리됩니다.

[전체 기능 매트릭스를 보려면 여기를 클릭하세요](../../installation/using/capability-matrix.md).

### 온-프레미스/하이브리드에서 Adobe Managed Services으로 마이그레이션하는 방법은 무엇입니까? {#how-do-i-migrate-from-on-premise-hybrid-to-adobe-managed-services}

Adobe Managed Services으로 마이그레이션하면 확장성, 보안이 향상되고 IT 오버헤드가 줄어듭니다. 이는 Campaign v8로 전환하기 전의 징검다리인 경우가 많습니다.

**주요 사항:**

* 사용 가능한 자동 마이그레이션 툴 없음 - 수동 계획 및 실행 필요
* Adobe Professional Services 지원이 적극 권장됨
* 클라우드 인프라, 자동 보안 패치, 전문가 지원, v8로 가는 쉬운 경로 등의 이점을 제공합니다
* 마이그레이션은 실사, 환경 감사, 데이터 정리, 스테이지 마이그레이션, 프로덕션 전환 등의 작업을 포함합니다.

**시작하기:** Adobe 담당자에게 문의하여 환경을 평가하고 Adobe Professional Services을 통한 자세한 마이그레이션 계획을 개발하십시오.

[Managed Services으로 마이그레이션](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-classic-blogs/migrate-your-adobe-campaign-v7-onprem-hybrid-environment-to/ba-p/681605){target="_blank"}에 대해 자세히 알아보세요.

## 빌드 업그레이드(Campaign Classic v7) {#build-upgrades-v7}

### Campaign Classic v7의 빌드 업그레이드란 무엇입니까? {#what-is-a-build-upgrade-v7}

빌드 업그레이드는 Adobe Campaign Classic v7 소프트웨어가 최신 보안 빌드 번호로 업데이트되지만 동일한 주/부 빌드 수준을 유지하는 것입니다. 예: Campaign Classic v7 빌드 9026에서 Campaign v7 빌드 9032.

Adobe Campaign은 정기적으로 업데이트됩니다. 일부 버전은 새로운 기능, 개선 사항 및 수정 사항이 포함되어 출시됩니다. 또한 누적 수정 사항만 있는 빌드는 주기적으로 릴리스됩니다.

자세한 내용은 [이 섹션](../../rn/using/rn-overview.md)을 참조하세요.

### Campaign Classic v7을 최신 버전으로 업그레이드하려면 어떻게 해야 합니까? {#how-can-i-upgrade-campaign-classic-v7}

Adobe Campaign Classic은 다양한 기술을 사용하여 가치를 제공합니다. 이러한 기술의 조합을 사용하면 Campaign Classic v7 인스턴스를 정기적으로 업그레이드하여 최신 버전을 통해 뛰어난 보안, 안정성 및 성능을 제공할 수 있습니다.

**호스팅된 고객의 경우:** 안정적인 최신 버전으로 Campaign 연간 업그레이드를 자동으로 사용할 수 있습니다. Adobe은 업그레이드 프로세스를 관리하고 시기를 조정합니다.

**온-프레미스/하이브리드 고객의 경우:** 업그레이드를 수행해야 합니다. Adobe은 매년 최소 한 번 업그레이드할 것을 강력히 권장합니다.

[이 섹션을 참조](../../production/using/build-upgrade.md)하여 환경을 업데이트하는 방법을 알아보고 이 특정 주제에 대한 자세한 질문을 보려면 [빌드 업그레이드 FAQ](../../platform/using/faq-build-upgrade.md)를 참조하십시오.

### Adobe Campaign Classic v7의 최신 버전은 무엇입니까? {#what-is-the-latest-version-v7}

새로운 기능 및 설명서를 포함한 최신 Campaign Classic v7 버전은 최신 [릴리스 정보](../../rn/using/latest-release.md)에 자세히 설명되어 있습니다.

### 실행 중인 Campaign Classic v7 버전을 어떻게 알 수 있습니까? {#how-do-i-know-which-version-v7}

Adobe Campaign 클라이언트 콘솔의 **[!UICONTROL Help > About...]** 메뉴에서 버전 및 빌드 번호를 확인하십시오. **[!UICONTROL About]** 상자에는 콘솔 및 서버 모두에서 실행 중인 버전 및 빌드에 대한 자세한 정보가 들어 있습니다.

자세한 내용은 [이 섹션](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)을 참조하세요.

### 빌드 업그레이드는 버전 업그레이드와 동일합니까? {#is-build-upgrade-same-as-version-upgrade}

아니요. 빌드 업그레이드는 주어진 주요 버전 내의 증분 업데이트이지만, 버전 업그레이드는 하나의 주요 버전에서 다른 주요 버전으로의 변경입니다. 빌드 업그레이드는 간단하며 일반적으로 아키텍처, 기술 또는 데이터 모델을 크게 변경하지 않습니다.

버전 업그레이드(예: v7에서 v8로)에는 일반적으로 중요한 기술 변경 사항이 수반되며 사용자 지정에 따라 구성을 변경하거나 일부 다시 구현해야 할 수 있습니다.

## Campaign Classic v7 구성 {#v7-configuration}

### Campaign Classic v7 인터페이스의 언어를 변경할 수 있습니까? {#can-i-change-language-v7}

인스턴스를 만들 때 Campaign Classic v7 언어가 선택됩니다. **나중에 변경할 수 없습니다.**

Adobe Campaign v7 사용자 인터페이스는 영어, 프랑스어, 독일어 및 일본어 4개 언어로 제공됩니다. 클라이언트 콘솔과 서버는 동일한 언어로 설정되어야 합니다. 각 Campaign Classic v7 인스턴스는 하나의 언어로만 실행할 수 있습니다.

Campaign v7을 설치할 때 미국 영어 또는 영국 영어 중 하나를 선택할 수 있습니다. 날짜 및 시간 형식이 다릅니다.

[이 섹션에서 자세히 알아보십시오](../../installation/using/creating-an-instance-and-logging-on.md).

**참고:** Campaign v8 Web UI를 통해 사용자는 인터페이스 언어를 개별적으로 변경할 수 있습니다. [자세히 알아보기](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/connect.html#language-pref){target="_blank"}

### Campaign Classic v7에서 보안 영역을 구성하려면 어떻게 해야 합니까? {#how-can-i-configure-security-zones-v7}

보안 영역 셀프 서비스 인터페이스는 Adobe Campaign Classic v7 배포의 VPN 보안 영역 구성의 항목을 관리하는 데 사용할 수 있습니다. 이는 주로 온-프레미스 및 하이브리드 배포와 관련이 있습니다.

Campaign v7의 보안 영역에 대한 자세한 내용은 [이 섹션](../../installation/using/security-zones.md)을 참조하세요.

보안 영역 셀프 서비스 UI에 대한 자세한 내용을 보려면 [여기를 클릭하세요](https://helpx.adobe.com/kr/campaign/kb/configuring-security-zones-self-service.html){target="_blank"}.

**참고:** 호스팅/Managed Services 고객은 Adobe에 문의하여 보안 영역을 구성해야 합니다.

### Adobe Campaign Classic v7을 LDAP와 통합할 수 있습니까? {#can-campaign-classic-integrate-with-ldap}

예. **온-프레미스/하이브리드 고객**&#x200B;의 경우 Campaign Classic v7을 LDAP 디렉터리와 통합하여 중앙 집중식 인증 및 사용자 관리를 수행할 수 있습니다.

이 통합을 통해 다음과 같은 작업을 수행할 수 있습니다.

* 회사 LDAP 디렉터리에 대해 인증할 사용자
* 중앙 집중식 사용자 및 권한 관리
* 사용자 그룹 및 권한의 자동 동기화
* Single Sign-On 기능

[Campaign Classic v7에서 LDAP 통합을 설정하는 방법을 알아보려면 여기를 클릭하세요](../../installation/using/connecting-through-ldap.md).

**참고:** LDAP 통합은 온-프레미스 및 하이브리드 배포에 사용할 수 있습니다. 호스팅된 고객은 인증에 Adobe IMS를 사용합니다.

### 온-프레미스 배포에 대한 보안 모범 사례는 무엇입니까? {#security-best-practices-on-premise}

온-프레미스 및 하이브리드 배포에서는 호스팅된 환경에 비해 추가적인 보안 구성 및 보안 강화가 필요합니다.

**주요 보안 영역:**

* 네트워크 보안 및 방화벽 구성
* 데이터베이스 액세스 및 보안
* 운영 체제 강화
* 파일 권한 및 액세스 제어
* 보안 영역 구성
* 암호화(저장 및 전송 중인 데이터)
* 사용자 액세스 관리
* 정기적인 보안 패치
* 감사 로깅 및 모니터링

[보안 구성 검사 목록](https://helpx.adobe.com/kr/campaign/kb/acc-security.html){target="_blank"}을 읽고 보안 구성 및 온-프레미스 배포에 대한 보안 구성 및 강화 기능을 확인할 주요 요소를 검색하세요.

### 클라이언트 콘솔 캐시를 지우려면 어떻게 합니까? {#how-do-i-clear-console-cache}

Campaign 클라이언트 콘솔 캐시를 지우면 많은 일반적인 표시 및 기능 문제가 해결됩니다. 캐시는 때때로 손상되거나 오래된 로컬 구성 파일을 저장합니다.

**캐시를 지우는 시기:**

* 새 브랜딩 요소가 올바르게 표시되지 않음
* 예기치 않게 내보내기/가져오기 기능 실패
* 구성 변경 후 인터페이스 요소가 업데이트되지 않음
* 성능 문제 또는 콘솔 응답 속도 저하
* 새 클라이언트 콘솔 버전으로 업그레이드 후

**캐시를 지우는 방법:**

1. **소프트 캐시 지우기(먼저 시도):**
   * Campaign 클라이언트 콘솔 열기
   * **[!UICONTROL File]** 메뉴로 이동
   * **[!UICONTROL Clear the local cache...]** 선택
   * 메시지가 표시되면 작업을 확인합니다
   * 클라이언트 콘솔 다시 시작

2. **하드 캐시 지우기(소프트 지우기로 문제가 해결되지 않는 경우):**
   * 먼저 소프트 캐시 지우기 수행
   * 클라이언트 콘솔을 로그아웃하고 완전히 닫습니다.
   * 다음으로 이동:
      * Windows 7/10: `C:\Users\<Username>\AppData\Roaming\Neolane\NL_5\`
      * Windows XP: `C:\Documents and Settings\<Username>\Application Data\Neolane\NL_5\`
   * 이름이 `nlclient-config-<alphanumerical value>.xml`인 모든 XML 파일과 관련 폴더 삭제
   * **중요:** `nlclient_cnx.xml` 파일을 삭제하지 않음
   * 클라이언트 콘솔 다시 시작

자세한 내용은 [Campaign 클라이언트 콘솔 설명서](../../platform/using/launching-adobe-campaign.md)를 참조하세요.

## 도움말 보기 {#getting-help}

### Campaign Classic v7에 대한 자세한 내용은 어디에서 찾을 수 있습니까? {#where-to-find-more-info-v7}

**설명서 및 리소스:**

* [Campaign Classic v7 설명서](https://experienceleague.adobe.com/docs/campaign-classic/using/campaign-classic-home.html?lang=ko){target="_blank"} - 전체 설명서
* [Campaign Classic v7 릴리스 노트](../../rn/using/latest-release.md) - 최신 릴리스 정보
* [Campaign Classic 호환성 매트릭스](../../rn/using/compatibility-matrix.md) - 지원되는 시스템 및 버전
* [Campaign Classic 자습서](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=ko){target="_blank"} - 비디오 자습서

**일반적인 캠페인 질문:**

다음에 대한 자세한 답변을 제공하는 [**Campaign v8 종합 FAQ**](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html){target="_blank"}를 참조하십시오.

* Campaign 시작
* 프로필 및 대상자
* 메시지 디자인 및 게재
* 워크플로우 및 자동화
* 보고 및 분석
* Campaign 설정 및 구성
* 개발자 리소스
* 개인 정보 및 규정 준수

**커뮤니티 및 지원:**

* [캠페인 커뮤니티 포럼](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-classic/ct-p/adobe-campaign-classic-community){target="_blank"}
* [Adobe 지원](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"}
* [Campaign 컨트롤 패널(호스팅된 고객)](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=ko){target="_blank"}

### Campaign Classic v7에서 Campaign v8로 마이그레이션해야 합니까? {#should-i-migrate-to-v8}

Campaign v8은 Adobe의 전략 플랫폼으로, 대용량 캠페인, 최신 웹 UI, 클라우드 기반의 이점 및 장기 지원이 필요한 조직에 적합합니다. Campaign Classic v7은 향후 지원 종료 시점에 도달합니다.

**다음 경우에 Campaign v8로 마이그레이션하는 것이 좋습니다.**

* 대용량 데이터 볼륨 또는 경험 성능 문제 처리
* IT 오버헤드와 인프라 관리(v8은 Managed Cloud Services만 해당) 절감
* 최신 UI 및 Adobe Experience Platform 통합 필요
* 자동 업데이트로 미래형 기술 필요
* 현재 호스팅/관리 서비스(간편한 마이그레이션 경로)에 있습니다.

**중요 고려 사항:**

* Campaign v8은 관리 클라우드 서비스로만 독점 제공됩니다(온-프레미스/하이브리드 옵션 없음)
* 맞춤화 및 통합 마이그레이션 계획 필요
* FFDA 아키텍처는 성능을 제공하지만 일부 워크플로우/API 조정이 필요합니다

**다음 단계:** Adobe 담당자에게 문의하여 마이그레이션 준비 상태를 평가하고 마이그레이션 도구에 액세스합니다.

자세히 알아보기:

* [Campaign v8 개요](https://experienceleague.adobe.com/docs/campaign/campaign-v8/new/whats-new.html){target="_blank"}
* [Campaign Classic v7에서 v8로 전환](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/v7-to-v8.html){target="_blank"}
* [Campaign v8 전체 FAQ](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html){target="_blank"}

**워크플로우, 게재, 대상자, 보고, 개인화 등에 대한 일반적인 Campaign 질문에 대한 자세한 답변을 보려면** Campaign v8 종합 FAQ[를 참조하세요.](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html){target="_blank"}
