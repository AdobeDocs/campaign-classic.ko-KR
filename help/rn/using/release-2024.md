---
product: campaign
title: Campaign Classic 2024 릴리스
description: 'Campaign Classic 2024 릴리스에 대해 자세히 알아보기 '
feature: Release Notes
role: User
level: Beginner
exl-id: 8e20391d-3628-4d0c-b413-c34e046ae810
source-git-commit: bf45c8bcdd41e614f9be09bc0fd6385707159841
workflow-type: ht
source-wordcount: '387'
ht-degree: 100%

---

# 2024년 릴리스{#release-2024}

## 릴리스 7.4.1 - 빌드 9383 {#release-7-4-1}

[!BADGE 일반 공급]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=ko#rn-statuses" tooltip="일반 공급"}

_2024년 6월 18일 수요일_

### 변경 및 개선 사항 {#release-7-4-1-changes}

* Adobe의 서비스 계정(JWT) 자격 증명 사용 종료에 따라 Adobe 솔루션 및 앱과 Campaign 아웃바운드 통합이 이제 OAuth 서버 간 자격 증명을 사용합니다. Campaign-Analytics 통합 또는 Experience Cloud 트리거 통합과 같은 아웃바운드 통합을 구현한 경우 2025년 1월 27일 이전에 Campaign 환경을 v7.4.1로 업그레이드하고 기술 계정을 oAuth로 마이그레이션해야 합니다. [자세히 알아보기](../../integrations/using/oauth-technical-account.md)

* [Campaign 기술 운영자를 Developer Console로 마이그레이션](../../technotes/using/ims-migration.md)하고 [최종 사용자 인증 방식을 IMS로 전환](../../technotes/using/migrate-users-to-ims.md)한 뒤에는 사용자 인터페이스 및 API 제한을 활성화하여 기본 인증과 관련된 옵션 및 기능을 제거할 수 있습니다. [자세히 알아보기](../../technotes/using/impact-ims-migration.md)


### 호환성 업데이트 {#release-7-4-1-compat}

[Adobe Campaign 호환성 매트릭스](compatibility-matrix.md)에 이번 새로운 릴리스와 함께 제공되는 변경 사항을 업데이트했습니다. 아래에서 목록을 확인할 수 있습니다.

* Adobe Campaign이 이제 **Microsoft Server 2022** 운영 체제와 호환됩니다.
* Adobe Campaign이 이제 **RHEL 9** 운영 체제와 호환됩니다.

  >[!CAUTION]
  >
  >RHEL 9를 사용하는 온-프레미스 고객이 DKIM(Domain Keys Identified Mail) 인증을 사용하려면 [이 섹션](../../installation/using/installing-packages-with-linux.md#rhel-9-update)에서 설명하는 대로 시스템 설정을 업데이트해야 합니다.


* Adobe Campaign이 이제 **Microsoft SQL Server 2022** 및 **Oracle 23c** 관계형 데이터베이스 관리 시스템과 호환되며, FDA(Federated Data Access)에서 사용할 수 있습니다.

* 이제 Adobe Campaign에 JDK(Java Development Kit) 11 이상이 필요합니다. Windows에서는 [이 섹션](../../installation/using/application-server.md#jdk)의 설명대로 JRE를 사용할 수 있어야 합니다.

* 모바일 애플리케이션용 Campaign(Neolane) SDK의 사용이 종료되었습니다. 이제 Adobe Experience Platform SDK로 전환해야 합니다. [자세히 알아보기](deprecated-features.md).

  한편 서비스 연속성을 보장하기 위해 Campaign v7.4에는 다음이 포함되어 있습니다.

   * 새로운 iOS용 Campaign SDK 1.0.27(iOS 16 및 17 호환) 및 최신 [Apple iOS 개인 정보 요청 요구 사항](https://developer.apple.com/news/?id=r1henawx){target="_blank"}.
   * 새로운 Android 14용 Campaign SDK.

### 기타 변경 사항 {#release-7-4-1-other}

v7.4.1부터 RPM Linux용 XML 라이브러리는 더 이상 Campaign에 포함되지 않습니다. 온-프레미스 또는 하이브리드 고객의 경우 관리자가 해당 라이브러리를 설치해야 합니다. [자세히 알아보기](../../installation/using/installing-packages-with-linux.md)

### 패치 {#release-7-4-1-patches}

이 릴리스에서는 다음 수정 사항이 제공됩니다.

NEO-74754, NEO-73174, NEO-72504, NEO-71534, NEO-71473, NEO-70195, NEO-69663, NEO-69651, NEO-67620, NEO-67235, NEO-66797, NEO-64680, NEO-63706, NEO-63657, NEO-62964, NEO-62575, NEO-58734, NEO-40531, NEO-36189, NEO-29592


