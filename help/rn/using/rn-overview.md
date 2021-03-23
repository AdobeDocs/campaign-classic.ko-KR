---
solution: Campaign Classic
product: campaign
title: 업그레이드 시작
description: Campaign Classic 업그레이드에 대한 자세한 내용
feature: 개요
role: 비즈니스 전문가
level: 초급
translation-type: tm+mt
source-git-commit: b77a56a97e499f60c092fae45c7809f7bfd9f2ea
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 93%

---


# 업그레이드 시작{#rn-overview}

Adobe Campaign은 정기적으로 업데이트 됩니다. 새로운 기능, 개선 사항 및 수정 사항이 포함된 평균 2~3개의 부 버전이 매년 릴리스됩니다. 또한 누적 수정 사항만 있는 빌드를 주기적으로 릴리스합니다.

이러한 정기 업데이트 빈도는 최신 업데이트를 직접 경험해 보고 환경을 안전하게 지키며 Adobe 제품을 통해 경험을 향상시키는 것을 목표로 합니다.

Adobe Campaign의 최신 버전을 실행하는 것이 매우 중요하다고 생각하는 이유입니다. 또한 최근 빌드에서 문제를 식별, 복제 및 수정이 일반적으로 훨씬 빨라져 지원 경험이 향상됩니다. 또한, 최근 빌드에서 발생한 다양한 문제를 해결합니다.

## 릴리스 상태{#rn-statuses}

상태는 각 빌드에 연결됩니다. 아래에서 상태 목록 및 해석 방법을 확인할 수 있습니다.

![](assets/do-not-localize/green3.png) GA(**General Availability**) - 프로덕션에서 검증되었으며 Adobe에서 권장합니다.

마지막 **GA 빌드**&#x200B;는 [[!DNL Gold Standard]  11 릴리스](../../rn/using/gold-standard.md#gs-11) 및 [Campaign 20.2.4 릴리스](../../rn/using/release--20-2.md#release-20-2-4-build-9187)입니다.

![](assets/do-not-localize/limited3.png) LA(**Limited Availability**) - 주문형 배포만 가능.

![](assets/do-not-localize/blue3.png) RC(**Release Candidate**) - 새로운 기능이 포함된 최신 버전입니다.

**최신 RC 빌드**&#x200B;는 [Campaign Classic 21.1 릴리스](../../rn/using/latest-release.md)입니다.

![](assets/do-not-localize/red3.png) **사용되지 않음** - 배포가 없습니다. 기존 구현을 업그레이드해야 합니다.

## 추천{#recommendations}

안정적인 구성을 위해서는 동일한 클라이언트 구성에서 실행 중인 모든 서버에 동일한 안정적인 빌드를 설치하는 것이 좋습니다.

또한, 클라이언트 콘솔은 서버 인스턴스와 동일한 빌드에 있어야 합니다.

구현을 최신 상태로 유지하려면 각 새로운 릴리스에 포함된 [사용되지 않거나 제거된 기능](../../rn/using/deprecated-features.md) 및 [호환성 매트릭스](../../rn/using/compatibility-matrix.md) 페이지를 참조하십시오.

## 업그레이드 프로세스{#process-upgrade}

호스팅 고객(Managed Service 또는 Hybrid)은 고객 지원 팀에 연락하여 환경을 업그레이드해야 합니다.

온-프레미스 사용자는 업그레이드를 수행할 수 있습니다. 이를 위해서는 [안정적인 최신 빌드를 다운로드](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)하고 모든 환경을 업그레이드해야 합니다. [업그레이드 프로세스](../../production/using/build-upgrade.md)에 대한 자세한 내용은 [빌드 업그레이드 FAQ](../../platform/using/faq-build-upgrade.md)를 참조하십시오.

### [!DNL Gold Standard]{#upgrade-for-gold-standard-users}

호스팅된 [!DNL Gold Standard] 사용자는 아무런 작업 없이 [최신 GA [!DNL Gold Standard] build](../../rn/using/gold-standard.md#gs-11)로 [!DNL Gold Standard] 업그레이드 혜택을 자동으로 받게 됩니다. [자세히 알아보기](../../rn/using/gs-overview.md)

>[!NOTE]
>[!DNL Gold Standard]에 대한 호환성 매트릭스는 [GA 호환성 매트릭스](../../rn/using/compatibility-matrix-gs.md)에서 사용할 수 있습니다.

## 지원 및 기타 유용한 링크{#support}

* [도움말 및 지원](https://helpx.adobe.com/kr/campaign/kb/ac-support.html)
* [Campaign 컨트롤 패널 릴리스](https://docs.adobe.com/content/help/ko-KR/control-panel/using/release-notes.html)
* [최신 설명서 업데이트](../../rn/using/documentation-updates.md)
* [사용이 중단되거나 제거된 기능](../../rn/using/deprecated-features.md)

새로운 Experience Cloud 솔루션 릴리스에 대한 정보를 얻으려면 [Adobe Priority Product Update](https://www.adobe.com/subscription/priority-product-update.html)를 구독하십시오.
