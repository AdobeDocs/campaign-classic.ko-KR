---
product: campaign
title: 업그레이드 시작
description: Campaign Classic 업그레이드에 대한 자세한 내용
feature: Overview
role: User
level: Beginner
exl-id: 7a05fdff-8f9d-4e8d-812e-0f1509db5499
source-git-commit: 29e56d6bf2817eeb863cbe33f99233a8241f2bf5
workflow-type: tm+mt
source-wordcount: '881'
ht-degree: 53%

---

# 업그레이드 시작하기{#rn-overview}

![](../../assets/v7-only.svg)

## 릴리스 상태{#rn-statuses}

모든 새 빌드는 색상으로 상태가 표시됩니다.

![](assets/do-not-localize/green3.png) **일반 공급** (GA) - 최신 안정적인 빌드, 프로덕션에서 유효성 검사되고 Adobe에서 권장됩니다.

![](assets/do-not-localize/limited3.png) LA(**Limited Availability**) - 주문형 배포만 가능.

![](assets/do-not-localize/blue3.png) RC(**Release Candidate**) - 새로운 기능이 포함된 최신 버전입니다.

![](assets/do-not-localize/orange3.png) **더 이상 사용할 수 없음** - 배포가 없습니다. 버그 해결이 없습니다. 최신 빌드로 업데이트하는 것이 좋습니다.

![](assets/do-not-localize/red3.png) **사용되지 않음** - 배포가 없습니다. 버그 해결이 없습니다. 기존 구현을 업그레이드해야 합니다.

## 릴리스 주기{#rn-cycle}

Adobe Campaign은 정기적으로 업데이트됩니다. 이렇게 정기적으로 업데이트를 제공하는 이유는 사용자가 최신 기능을 바로 사용할 수 있도록 하고 사용자의 환경을 안전하게 지키며 Adobe 제품 관련 경험을 개선하겠다는 목표를 위해서입니다.

이것이 바로 여러분이 매우 중요한 이유입니다 **가장 최근의 안정적인 버전 실행** Adobe Campaign 또한 최근 빌드에서 문제를 식별, 복제 및 수정이 일반적으로 훨씬 빨라져 지원 경험이 향상됩니다. 또한, 최근 빌드에서 발생한 다양한 문제를 해결합니다.

호스팅된 사용자는 별도의 조치 없이 안정적인 최신 버전의 업그레이드를 자동으로 사용할 수 있습니다. 자세한 내용은 [연간 업그레이드 섹션](#yearly-upgrade)을 참조하세요. 이전 빌드에서 마이그레이션하는 경우 먼저 이 버전으로 업그레이드하는 것이 좋습니다.

## 권장 사항{#recommendations}

안정적인 구성을 위해서는 를 설치하는 것이 좋습니다 **동일한 빌드** 동일한 클라이언트 구성에서 실행 중인 모든 서버에서

또한 릴리스 노트에서 별도로 언급된 경우를 제외하고 클라이언트 콘솔이 켜져 있어야 합니다 **동일한 빌드** 를 서버 인스턴스로 설정합니다.

구현을 최신 상태로 유지하려면 각 새로운 릴리스에 포함된 [사용되지 않거나 제거된 기능](../../rn/using/deprecated-features.md) 및 [호환성 매트릭스](../../rn/using/compatibility-matrix.md) 페이지를 참조하세요.

## 업그레이드 프로세스{#process-upgrade}

호스팅된 고객(Managed Service 또는 Hybrid)으로서 고객 지원 팀에 연락하여 환경을 업그레이드하십시오.

온-프레미스 사용자는 업그레이드를 수행할 수 있습니다. 이렇게 하려면 [최신 안정적인 빌드 (GA) 다운로드](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) 모든 환경을 업그레이드합니다. [업그레이드 프로세스](../../production/using/build-upgrade.md)에 대한 자세한 내용은 [빌드 업그레이드 FAQ](../../platform/using/faq-build-upgrade.md)를 참조하십시오.

## 연간 업그레이드 {#yearly-upgrade}

Adobe은 Adobe의 소프트웨어 솔루션을 통해 최상의 경험과 가치를 제공하기 위해 노력하고 있습니다. 조직은 Adobe 솔루션이 해당 작업을 수행하는 데 사용하는 최신 버전의 관련 기술에 액세스할 수 있도록 하기 위해 최선을 다하고 있습니다.

Adobe Campaign Classic은 특히 다양한 기술을 사용하여 가치를 전달하고 있습니다. 이러한 기술의 조합은 정기적인 Campaign Classic 인스턴스의 업그레이드를 요구하여 최신 버전이 뛰어난 보안, 안정성 및 성능을 제공하는 데 사용되도록 합니다.

호스팅된 사용자는 아무런 조치 없이 최신 GA 빌드로 업그레이드를 자동으로 활용할 수 있습니다. 자세한 내용은 아래 FAQ를 참조하세요.

### 조직에 이 업그레이드가 필요한 이유는 무엇입니까?

호스팅된 고객의 경우 계정이 Campaign Classic과 관련된 기술 중 하나 이상을 업그레이드하고 현재 빌드 및/또는 버전을 업데이트할 필요가 있다고 확인된 경우 Adobe은 사용자에게 직접 알려줍니다.

이전 버전을 사용하는 온-프레미스 또는 하이브리드 고객의 경우 Adobe는 안정적인 최신 빌드(GA)로 전환할 것을 권장합니다.

이렇게 하면 업데이트된 성능 기술을 사용할 뿐만 아니라 취약성에서도 계정이 보호됩니다. 또한 이 업그레이드는 수작업 및 개입이 덜 필요한 보다 쉽고 정기적으로 업그레이드할 수 있도록 계정을 포지셔닝합니다.

### 이 업그레이드의 프로세스와 타임라인은 무엇입니까?

Adobe 팀이 이 여정을 통해 조직을 이끌고 가이드합니다.

전담 고객 지원 담당자, 제품 관리자, 엔지니어 및 TechOps 전문가, 제품 컨설턴트 팀이 고객 지원 및 원활한 경험을 제공합니다.

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
    <li>고객 지원 센터 볼륨이 감소하여 문제를 보다 빠르게 해결하고 업그레이드와 관련이 없는 문제에 더 많은 관심을 기울일 수 있습니다.</li>
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
    <li>Campaign Classic을 지원하는 기술 스택에 대한 개선 사항은 조직의 마케팅 팀과 IT 팀 모두에 적용됩니다.</li>
    </ul>
  </td>

<td>
      <img alt="빌드 업그레이드" src="assets/do-not-localize/upgrades.png" />
    <div>
    <strong>간편한 업그레이드</strong>
    </a>
    </div>
    <ul>
    <li>Campaign Classic 인스턴스를 업그레이드하는 노력과 복잡성은 두 버전(v5 —&gt; v7) 간의 거리에 따라 증가합니다.</li>
    <li>조직에서 대기할 시간이 길어질수록 업그레이드는 더욱 복잡해질 수 있습니다(그리고 더 많은 취약점이 노출됨).</li>
    <li>정기적인 업데이트로 업그레이드에 대한 다운타임과 회귀 위험이 줄어듭니다.</li>
    </ul>
  </td>
</tr>
</table>

## 추가 리소스{#support}

* [Campaign 버전을 확인합니다](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).
* [도움말 및 지원](../../support.md)
* [Campaign 컨트롤 패널 릴리스](https://experienceleague.adobe.com/docs/control-panel/using/release-notes.html?lang=ko)
* [최신 설명서 업데이트](../../rn/using/documentation-updates.md)
* [사용이 중단되거나 제거된 기능](../../rn/using/deprecated-features.md)
* [빌드 업그레이드 FAQ](../../platform/using/faq-build-upgrade.md)

새로운 Experience Cloud 솔루션 릴리스에 대한 정보를 받으려면 [Adobe 주요 제품 업데이트](https://www.adobe.com/kr/subscription/priority-product-update.html)를 구독하세요.
