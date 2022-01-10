---
product: campaign
title: 업그레이드 시작
description: Campaign Classic 업그레이드에 대한 자세한 내용
feature: Overview
role: User
level: Beginner
exl-id: 7a05fdff-8f9d-4e8d-812e-0f1509db5499
source-git-commit: 87067a0cca1a4a7f8ea1137ece6d513d58fcdb42
workflow-type: tm+mt
source-wordcount: '913'
ht-degree: 81%

---

# 업그레이드 시작하기{#rn-overview}

![](../../assets/v7-only.svg)

## 릴리스 상태{#rn-statuses}

모든 새 빌드는 색상으로 구체화된 상태를 제공합니다.

![](assets/do-not-localize/green3.png) GA(**General Availability**) - 프로덕션에서 검증되었으며 Adobe에서 권장합니다.

![](assets/do-not-localize/limited3.png) LA(**Limited Availability**) - 주문형 배포만 가능.

![](assets/do-not-localize/blue3.png) RC(**Release Candidate**) - 새로운 기능이 포함된 최신 버전입니다.

![](assets/do-not-localize/orange3.png) **더 이상 사용할 수 없음** - 배포가 없습니다. 버그 해결이 없습니다. 최신 빌드로 업데이트하는 것이 좋습니다.

![](assets/do-not-localize/red3.png) **사용되지 않음** - 배포가 없습니다. 버그 해결이 없습니다. 기존 구현을 업그레이드해야 합니다.

## 릴리스 주기

Adobe Campaign은 정기적으로 업데이트됩니다. 이러한 정기 업데이트 빈도는 최신 업데이트를 직접 경험해 보고 환경을 안전하게 지키며 Adobe 제품을 통해 경험을 향상시키는 것을 목표로 합니다.

이것이 우리가 당신이 중요하다고 믿는 이유입니다 **가장 최근의 안정적인 버전 실행** Adobe Campaign 또한 최근 빌드에서 문제를 식별, 복제 및 수정이 일반적으로 훨씬 빨라져 지원 경험이 향상됩니다. 또한, 최근 빌드에서 발생한 다양한 문제를 해결합니다.

호스팅된 고객은 아무런 조치 없이 최신 안정된 버전의 업그레이드를 자동으로 활용할 수 있습니다. 자세한 내용은 [연간 업그레이드 섹션](#yearly-upgrade). 이전 빌드에서 마이그레이션하는 경우 먼저 이 버전으로 업그레이드하는 것이 좋습니다.

## 추천{#recommendations}

안정적인 구성을 위해서는 를 설치하는 것이 좋습니다 **같은 안정적인 빌드** 동일한 클라이언트 구성에서 실행 중인 모든 서버에서

또한 클라이언트 콘솔은 서버 인스턴스와 동일한 빌드에 있어야 합니다.

구현을 최신 상태로 유지하려면 각 새로운 릴리스에 포함된 [사용되지 않거나 제거된 기능](../../rn/using/deprecated-features.md) 및 [호환성 매트릭스](../../rn/using/compatibility-matrix.md) 페이지를 참조하세요.

## 업그레이드 프로세스{#process-upgrade}

호스팅 고객(Managed Service 또는 Hybrid)은 고객 지원 팀에 연락하여 환경을 업그레이드해야 합니다.

온-프레미스 사용자는 업그레이드를 수행할 수 있습니다. 이를 위해서는 [안정적인 최신 빌드를 다운로드](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)하고 모든 환경을 업그레이드해야 합니다. [업그레이드 프로세스](../../production/using/build-upgrade.md)에 대한 자세한 내용은 [빌드 업그레이드 FAQ](../../platform/using/faq-build-upgrade.md)를 참조하십시오.

## 연간 업그레이드 {#yearly-upgrade}

Adobe 및 Adobe Campaign은 Adobe 소프트웨어 솔루션을 통해 최상의 경험과 가치를 제공하기 위해 최선을 다합니다. Adobe는 Adobe 솔루션이 해당 작업을 수행하는 데 활용하는 최신 버전의 관련 기술을 액세스할 수 있도록 최선을 다합니다.

Adobe Campaign Classic은 특히 다양한 기술을 사용하여 가치를 전달하고 있습니다. 이러한 기술의 조합은 정기적인 Campaign Classic 인스턴스의 업그레이드를 요구하여 최신 버전이 뛰어난 보안, 안정성 및 성능을 제공하는 데 사용되도록 합니다.

호스팅된 사용자는 아무런 조치 없이 최신 안정적인 빌드로 업그레이드를 자동으로 활용할 수 있습니다. 자세한 내용은 아래 FAQ를 참조하십시오.

### 조직에 이 업그레이드가 필요한 이유는 무엇입니까?

호스팅 고객으로서, 귀하의 계정이 현재 빌드 및/또는 버전을 업데이트하면서 Campaign Classic과 관련된 기술 중 하나 이상을 업그레이드할 필요가 있다고 판단되면 Adobe에서 즉시 알려드립니다.

이전 버전에서 실행되는 온-프레미스 또는 하이브리드 고객으로서 Adobe은 최신 안정적인 빌드로 이동할 것을 권장합니다.

이렇게 하면 업데이트된 성능 기술을 활용할 수 있을 뿐만 아니라 취약점으로부터 계정을 안전하게 보호할 수 있습니다. 또한, 이 업그레이드는 수작업과 개입이 줄어들고 쉽게 주기적으로 업그레이드를 수행할 수 있도록 계정을 배치합니다.

### 이 업그레이드의 프로세스와 타임라인은 무엇입니까?

Adobe 팀이 이 여정을 안내해드리겠습니다.

Adobe는 원활한 고객 경험을 지원하고 제공하기 위해 전담 고객 지원 담당자, 제품 관리자, 엔지니어 및 TechOps 전문가, 제품 컨설턴트로 이루어진 팀을 구성했습니다.

Adobe는 귀하에게 관련 프로젝트 및 연락처 정보를 제공하기 위해 최선을 다하고 있습니다.

### 이점

<tr>
  <td>
      <img alt="보안" src="assets/do-not-localize/security.png"/>
    <div>
    <strong>향상된 보안</strong>
    </div>
    <ul>
    <li>Adobe Campaign Classic의 기능을 강화하는 데 사용되는 기술의 결합으로 가치를 제공합니다.</li>
    <li>보안을 유지하기 위해 모든 인스턴스를 업데이트해야 합니다.</li>
    <li>보안에는 지속적인 집중과 사전 예방적인 유지 관리가 필요합니다.</li>
    <li>보안 위험은 어디에나 존재하며 무시할 수 없습니다. Campaign Classic을 업그레이드할 때마다 보안이 향상됩니다.</li>
    </ul>
  </td>

<td>
      <img alt="지원" src="assets/do-not-localize/support.png" />
    <div>
    <strong>향상된 지원</strong>
    </div>
    <ul>
    <li>대부분의 중요한 문제는 실제로 업그레이드를 통해 해결되며 예방할 수 있습니다.</li>
    <li>주기적인 업그레이드는 이러한 문제를 예방하여 당면 과제를 줄이고 효율성을 높이는 데 도움이 됩니다.</li>
    <li>고객 지원 볼륨이 감소하여 신속한 해결 방법이 가능하며 업그레이드와 관련이 없는 문제에 더욱 집중할 수 있습니다.</li>
    </ul>
  </td>
</tr>

<tr>
  <td>
      <img alt="유지 관리" src="assets/do-not-localize/maintenance.png"/>
    <div>
    <strong>유지 관리 및 안정성 향상</strong>
    </div>
    <ul>
    <li>Adobe Campaign 팀은 시간이 지남에 따라 제품의 안정성과 성능을 향상시키고 알려진 문제를 수정하는 방법을 확인합니다.</li>
    <li>업그레이드를 통해 이러한 향상된 기능으로 인스턴스를 최신 상태로 유지할 수 있으며 Campaign Classic 인스턴스 내에서 급격한 증가 및/또는 복잡성을 겪고 있는 조직에서 경험하는 일반적인 문제를 예방할 수 있습니다.</li>
    <li>Campaign Classic을 향상시키는 기술 스택에 대한 향상된 기능은 마케팅 팀과 조직의 IT 팀 모두에서 확인할 수 있습니다.</li>
    </ul>
  </td>

<td>
      <img alt="빌드 업그레이드" src="assets/do-not-localize/upgrades.png" />
    <div>
    <strong>간편한 업그레이드</strong>
    </a>
    </div>
    <ul>
    <li>Campaign Classic 인스턴스 업그레이드의 노력과 복잡성은 2개 버전(v5 —&gt; v7) 간의 거리를 증가시킵니다.</li>
    <li>조직에서 대기할 시간이 길어질수록 업그레이드는 더욱 복잡해질 수 있습니다(그리고 더 많은 취약점이 노출됨).</li>
    <li>정기 업데이트를 통해 가동 중지 시간을 줄여 업그레이드하고 재발 위험을 줄일 수 있습니다.</li>
    </ul>
  </td>
</tr>
</table>

## 추가 리소스{#support}

* [Campaign 버전 찾기](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).
* [도움말 및 지원](../../support.md)
* [Campaign 컨트롤 패널 릴리스](https://experienceleague.adobe.com/docs/control-panel/using/release-notes.html?lang=ko)
* [최신 설명서 업데이트](../../rn/using/documentation-updates.md)
* [사용이 중단되거나 제거된 기능](../../rn/using/deprecated-features.md)
* [빌드 업그레이드 FAQ](../../platform/using/faq-build-upgrade.md)

새로운 Experience Cloud 솔루션 릴리스에 대한 정보를 받으려면 [Adobe Priority Product Update](https://www.adobe.com/kr/subscription/priority-product-update.html)를 구독하십시오.
