---
product: campaign
title: 메시지 게재 최적화
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
exl-id: 24b2ee47-bec7-43ce-81b3-0b2d1a5cebae
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '729'
ht-degree: 8%

---

# 게재 최적화 {#optimize-delivery}

![](../../assets/common.svg)

게재 만들기를 시작하기 전에 몇 가지 작업을 수행하여 전송 프로세스 업스트림을 보호하고 최적화할 수 있습니다.

다음 섹션에서는 Adobe Campaign의 최적 구성을 위한 우수 사례 및 권장 절차에 대해 설명합니다. 이러한 방법을 따르면 다운스트림에 발생할 수 있는 문제를 최소화합니다.

## 플랫폼 성능

몇 가지 요소가 서버 성능에 직접 영향을 주고 플랫폼의 속도를 저하할 수 있습니다.

* 개인화 요소의 수 및 유형: 이메일의 개인화는 각 수신자에 대한 데이터베이스에서 데이터를 가져옵니다. 개인화 요소가 많으면 게재를 준비하는 데 필요한 데이터 양이 증가합니다.  [이 섹션](about-personalization.md)에서 개인화에 대해 자세히 알아보십시오

* 서버 로드: 마케팅 서버가 동시에 많은 다른 작업을 처리할 때 성능이 저하될 수 있습니다. 마케팅 서버는 데이터가 올바르고 제시간에 맞게 모든 게재에 대해 수신 및 발신 데이터를 모두 조정해야 합니다.

   **팁**  - 이를 방지하려면 팀 내 다른 구성원과 게재 일정을 조정하여 최상의 성능을 보장합니다.

* 워크플로우 실행: 플랫폼 성능 문제를 방지하려면 워크플로우를 모니터링해야 합니다. 이 문서](../../workflow/using/workflow-best-practices.md#execution-and-performance)에 나열된 지침을 따르십시오.[

* 자격이 있는 경우 [Campaign 컨트롤 패널 기능](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=ko)을 활용하여 [성능 모니터링](https://experienceleague.adobe.com/docs/control-panel/using/performance-monitoring/about-performance-monitoring.html) 기능을 사용하여 플랫폼을 모니터링할 수 있습니다.

## 네트워크 구성을 확인하는 중 {#network-config}

대용량 볼륨의 이메일을 처리할 때 게재를 최적화하고 스팸으로 오인되지 않도록 서버 ID를 숨기려 하지 않는 올바른 네트워크 구성이 있는지 확인하십시오.

**팁**: 브랜드 웹 사이트에 해당하는 투명한 발신자 주소를 사용하십시오. 예를 들어, 여행사 회사는 발렌티노 호텔 체인을 관리한다. 이 회사는 웹 사이트에 대한 발렌티노.com 도메인을 소유하고 있습니다. 파리에 있는 발렌티노 호텔을 홍보하기 위해서, 그것은 paris.valentino.com 하위 도메인을 사용합니다. 따라서 관련 발신자 주소는 hotel@paris.valentino.com일 수 있습니다.

## 전달성 관리 {#deliverability-management}

스팸으로 표시되거나 출력되지 않고 수신자의 받은 편지함에 도달하려면 메시지 게재 능력을 향상해야 합니다.

* 전달성의 정의?

   * 수신자 서버가 수락할 수 있는 기능을 결정하는 이메일의 요소를 참조합니다. ISP(인터넷 서비스 공급자)는 스팸으로 식별하는 이메일을 필터링하거나 이미지를 다운로드하지 못하도록 차단합니다. 특정 도메인이 너무 많은 이메일을 보내는 것으로 확인되면 해당 발신자로부터 받을 이메일 수에 제한을 설정합니다.

   * 게재 기능을 위해 이메일을 확인할 때 네 가지 주요 카테고리에 중점을 두려고 합니다. 데이터 품질, 메시지 및 컨텐츠, 전송 인프라, 평판. 이 항목에 대한 자세한 내용은 [이 섹션](about-deliverability.md)을 참조하십시오.

* 이 문서](about-deliverability.md)에 자세히 설명된 권장 사항을 적용합니다.[

* 도움이 필요하면 Adobe 담당자에게 문의하십시오.

## 격리 관리 {#quarantine-management}

우수한 격리 관리 프로세스를 유지하는 것이 귀하의 최대 관심사입니다.

새 플랫폼에서 전자 메일 보내기를 시작할 때 정규화된 주소가 아닌 주소 목록을 사용할 수 있습니다. 잘못된 주소 또는 허니포트 주소(스팸 메일함을 조작하기 위해 만든 사서함)로 보내는 경우 이로 인해 플랫폼의 명성은 낮아집니다. 양호한 격리 관리 프로세스는 다음과 같은 이점을 제공합니다. 주소 품질 유지, 인터넷 액세스 제공업체차단 목록의 방지, 오류 속도 감소, 게재 및 처리량 향상

**팁**

* 잘못된 주소 목록이 있는 경우 Adobe은 **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Non deliverables and addresses]**&#x200B;을 통해 격리 테이블로 가져오는 것을 권장합니다.

* 주소가 격리된 수신자는 기본적으로 게재 분석 중에 제외됩니다. 타겟팅되지 않았습니다. 이를 통해 게재 속도를 높일 수 있습니다. 오류율은 게재 속도에 상당한 영향을 미치기 때문입니다. 받은 편지함이 가득 찼거나 주소가 없는 경우 등 전자 메일 주소를 격리할 수 있습니다. [자세히 알아보기](#identifying-quarantined-addresses-for-a-delivery)

* Adobe Campaign은 반환된 오류 유형에 따라 잘못된 주소를 관리합니다. 이 작업에 대한 자세한 정보는 [이 섹션](understanding-quarantine-management.md)을 참조하십시오.


* 일부 인터넷 액세스 제공 업체는 잘못된 주소의 비율이 너무 높은 경우 이메일을 자동으로 스팸으로 간주합니다. 따라서 격리 를 사용하면 이러한 제공 업체에 의해 차단 목록에 추가되지 않습니다.

* 격리 관리는 잘못된 전화번호를 게재에서 제외하면 SMS를 보내는 비용을 줄이는 데 도움이 됩니다.

## 이중 옵트인 메커니즘 {#double-opt-in}

잘못된 주소로 메시지를 보내지 않고, 부적절한 통신을 제한하며, 발신자의 평판을 향상시키기 위해 Adobe은 구독 후 확인을 위해 이중 옵트인 메커니즘을 구현하는 것을 권장합니다. 이렇게 하면 수신자가 의도적으로 구독했는지 확인하는 데 도움이 됩니다.

이 메커니즘을 구현하는 자세한 내용은 [이 섹션](../../web/using/use-cases--web-forms.md)에 설명되어 있습니다.
