---
product: campaign
title: 업그레이드 시작
description: Campaign Classic 업그레이드에 대한 자세한 내용
feature: Overview
role: User
level: Beginner
exl-id: 7a05fdff-8f9d-4e8d-812e-0f1509db5499
source-git-commit: 1cc1568fe77cc5bbde88092b0e9108792e10fd71
workflow-type: ht
source-wordcount: '934'
ht-degree: 100%

---

# 릴리스 업데이트{#rn-overview}

![](../../assets/v7-only.svg)

Adobe Campaign Classic은 새로운 기능, 버그 수정으로 성능, 보안 및 유용성을 향상시키는 제품 업데이트를 정기적으로 릴리스합니다. 이러한 업데이트는 **제품 빌드**&#x200B;로 릴리스됩니다. 각 새 빌드에 대한 자세한 내용은 [릴리스 정보](latest-release.md)에서 확인할 수 있습니다.

## 릴리스 상태{#rn-statuses}

모든 새 빌드는 [릴리스 정보](latest-release.md)에서 색상으로 식별되는 상태를 제공합니다.

![](assets/do-not-localize/green3.png) GA(**General Availability**) - 안정적인 최신 빌드로 프로덕션에서 검증되었으며 Adobe에서 권장합니다.

![](assets/do-not-localize/limited3.png) LA(**Limited Availability**) - 주문형 배포만 가능합니다.

![](assets/do-not-localize/blue3.png) RC(**Release Candidate**) - 새로운 기능이 포함된 최신 빌드입니다.

![](assets/do-not-localize/orange3.png) **더 이상 사용할 수 없음** - 배포가 없습니다. 버그 해결이 없습니다. 최신 빌드로 업데이트하는 것이 좋습니다.

![](assets/do-not-localize/red3.png) **사용되지 않음** - 배포가 없습니다. 버그 해결이 없습니다. 기존 구현을 업그레이드해야 합니다.

## 릴리스 주기{#rn-cycle}

Adobe Campaign은 정기적으로 업데이트됩니다. 이렇게 정기적으로 업데이트를 제공하는 이유는 사용자가 최신 기능을 바로 사용할 수 있도록 하고 사용자의 환경을 안전하게 지키며 Adobe 제품 관련 경험을 개선하겠다는 목표를 위해서입니다.

따라서 Adobe Campaign의 **가장 안정적인 최신 빌드를 실행**&#x200B;하는 것이 매우 중요합니다. 또한 최신 빌드에서는 보통 문제를 식별, 재현, 해결하는 과정이 훨씬 빨라져 지원 경험이 향상됩니다. 이에 더해 최신 빌드에서는 사용자가 접할 수 있는 다양한 문제를 해결합니다.

호스팅된 고객은 별도의 조치 없이 안정적인 최신 빌드의 업그레이드를 자동으로 사용할 수 있습니다. 자세한 내용은 [연간 업그레이드 섹션](#yearly-upgrade)을 참조하십시오. 이전 빌드에서 마이그레이션하는 경우 먼저 이 빌드로 업그레이드하는 것이 좋습니다.

## 권장 사항{#recommendations}

Adobe는 안정적인 구성을 위해 동일한 클라이언트 구성에서 실행하는 모든 서버에 **동일한 빌드**&#x200B;를 설치하기를 권장합니다.

또한 [릴리스 정보](latest-release.md)에서 별도로 언급되지 않는 한, 클라이언트 콘솔은 서버 인스턴스와 **동일한 빌드**&#x200B;여야 합니다.

구현을 최신 상태로 유지하려면 각 새로운 릴리스에 포함된 [사용되지 않거나 제거된 기능](../../rn/using/deprecated-features.md) 및 [호환성 매트릭스](../../rn/using/compatibility-matrix.md) 페이지를 참조하세요.

## 업그레이드 프로세스{#process-upgrade}

호스팅 고객(Managed Service 또는 Hybrid)의 경우 환경을 업그레이드하려면 고객 지원 팀에 문의해 주세요.

온-프레미스 사용자는 업그레이드를 수행할 수 있습니다. 이를 위해서는 [안정적인 최신 빌드(GA)를 다운로드](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)하고 모든 환경을 업그레이드합니다.

[업데이트 프로세스](../../production/using/build-upgrade.md)와 [빌드 업그레이드 FAQ](../../platform/using/faq-build-upgrade.md)에 대해 자세히 알아보십시오.

## 연간 업그레이드 {#yearly-upgrade}

Adobe는 Adobe 소프트웨어 솔루션을 통해 최상의 경험과 가치를 제공하기 위해 최선을 다합니다. Adobe는 Adobe 솔루션이 작업 수행에 활용하는 관련 기술의 최신 버전에 사용자가 액세스할 수 있도록 최선을 다합니다.

Adobe Campaign Classic은 특히 다양한 기술을 사용하여 가치를 전달하고 있습니다. 이렇게 다양한 기술의 조합을 사용하므로, 최신 버전을 통해 뛰어난 보안, 안정성, 성능을 제공할 수 있도록 사용자가 정기적으로 Campaign Classic 인스턴스를 업그레이드해야 합니다.

호스팅된 사용자는 아무런 조치 없이 최신 GA 빌드로 자동 업그레이드 혜택을 받을 수 있습니다. 자세한 내용은 아래 FAQ를 참조하세요.

### 내 조직에 이 업그레이드가 필요한 이유는 무엇인가요?

호스팅된 고객으로서, Campaign Classic과 관련된 기술 중 하나 이상을 업그레이드하고 인프라를 현재 빌드(예: v7.2.1에서 v7.3.3으로) 및/또는 버전(v7에서 v8로)으로 업그레이드해야 하는 것으로 계정이 확인되면 Adobe은 직접 사용자에게 알림을 보냅니다.

이전 빌드를 사용하는 온-프레미스 또는 하이브리드 고객의 경우 Adobe는 안정적인 최신 빌드(GA)로 전환할 것을 권장합니다.

이렇게 하면 업데이트된 성능 관련 기술을 활용할 수 있을 뿐만 아니라 취약점으로부터 계정을 안전하게 보호할 수 있습니다. 또한 이 업그레이드에서는 사용자의 계정에 보다 간단한 정기적 업그레이드를 적용하여 번거롭게 직접 작업할 필요가 줄어듭니다.

### 이 업그레이드의 과정과 일정은 어떻게 되나요?

Adobe 팀이 사용자의 조직에 업그레이드 여정을 안내해 드리겠습니다.

전담 고객 지원 담당자, 제품 관리자, 엔지니어 및 TechOps 전문가, 제품 컨설턴트로 이루어진 팀이 사용자를 지원하여 원활한 고객 경험을 제공합니다.

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
    <li>고객 지원 볼륨이 감소하여 신속한 해결이 가능하며 업그레이드와 관련이 없는 다른 문제에 더욱 집중할 수 있습니다.</li>
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
    <li>Campaign Classic을 구동하는 기술 스택 개선은 조직의 마케팅 팀과 IT 팀 모두 체감할 수 있습니다.</li>
    </ul>
  </td>

<td>
      <img alt="빌드 업그레이드" src="assets/do-not-localize/upgrades.png" />
    <div>
    <strong>간편한 업그레이드</strong>
    </a>
    </div>
    <ul>
    <li>Campaign Classic의 두 버전 간 거리(v6 --&gt; v7)에 따라 사용하는 Campaign Classic 인스턴스를 업그레이드할 때 들어가는 노력과 복잡도가 올라갑니다.</li>
    <li>조직에서 업그레이드 전 대기하는 기간이 길어질수록 업그레이드가 더욱 복잡해지고, 더 많은 취약점에 노출될 수 있습니다.</li>
    <li>정기 업데이트를 통해 업그레이드에 따른 가동 중지 시간과 회귀 문제가 발생할 위험을 줄일 수 있습니다.</li>
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
