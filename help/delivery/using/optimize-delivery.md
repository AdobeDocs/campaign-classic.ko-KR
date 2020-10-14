---
title: 메시지 전달 최적화
seo-title: 메시지 전달 최적화
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
translation-type: tm+mt
source-git-commit: 75cbb8d697a95f4cc07768e6cf3585e4e079e171
workflow-type: tm+mt
source-wordcount: '736'
ht-degree: 6%

---


# 전달 최적화 {#optimize-delivery}

게재 생성을 시작하기 전에 여러 작업을 수행하여 전송 프로세스를 보호하고 최적화할 수 있습니다.

다음 섹션에서는 Adobe Campaign의 최적 구성을 위한 모범 사례와 권장 절차에 대해 설명합니다. 이러한 관행을 따르면 다운스트림에 직면할 수 있는 문제를 최소화할 수 있습니다.

## 플랫폼 성능

몇 가지 요소는 서버 성능에 직접적인 영향을 주고 플랫폼을 느리게 할 수 있습니다.

* 개인화 요소의 수 및 유형:이메일의 개인화는 각 수신자에 대한 데이터를 데이터베이스에서 가져옵니다. 개인화 요소가 많은 경우 전달을 준비하는 데 필요한 데이터의 양이 증가합니다.  이 섹션에서 개인화에 대한 자세한 [내용](../../delivery/using/about-personalization.md)

* 서버 로드:마케팅 서버가 동시에 여러 가지 작업을 처리할 때 성능이 저하될 수 있습니다. 마케팅 서버는 데이터가 정확하고 정시에 맞는지 확인하기 위해 모든 게재에 대해 수신 및 발신 데이터를 모두 조정해야 합니다.

   **팁** - 이를 방지하려면 팀 내 다른 구성원과 배달 예약을 조정하여 최상의 성능을 보장합니다.

* 워크플로우 실행:플랫폼 성능 문제를 방지하려면 워크플로우 모니터링이 필요합니다. 이 문서 [에 나와 있는 지침을 따르십시오](../../workflow/using/workflow-best-practices.md#execution-and-performance).

* 호스팅 고객인 경우 [캠페인 제어 패널 기능을](https://docs.adobe.com/content/help/en/control-panel/using/discover-control-panel/key-features.html) 활용하여 [성능 모니터링](https://docs.adobe.com/content/help/en/control-panel/using/performance-monitoring/about-performance-monitoring.html) 기능을 사용하여 플랫폼을 모니터링할 수 있습니다.

## 네트워크 구성 확인 {#network-config}

대량의 이메일을 처리할 때 배달을 최적화하고 스패머로 오인되지 않도록 하려면 서버의 ID를 숨기려고 하지 않는 적절한 네트워크 구성이 있는지 확인하십시오.

**팁**: 브랜드의 웹 사이트에 해당하는 투명한 보낸 사람 주소를 사용합니다. 예를 들어, 여행사 회사는 발렌티노 호텔 체인을 관리합니다. 자체 웹사이트에 발렌티노.com 도메인을 보유하고 있다. 파리 발렌티노 호텔을 홍보하기 위해 파리.발렌티노.com 하위 도메인을 사용한다. 따라서 관련 보낸 사람 주소는 hotel@paris.valentino.com일 수 있습니다.

## 게재 기능 관리 {#deliverability-management}

수신자의 받은 편지함에 도달하기 위해 메시지 전달 비율을 향상시켜야 합니다.

* 배달능력이란?

   * 받는 사람의 서버에서 받을 수 있는 기능을 결정하는 이메일의 요인을 나타냅니다. ISP(Internet Service Providers)는 스팸으로 식별하는 이메일을 필터링하거나 이미지를 다운로드하지 못하도록 차단합니다. 특정 도메인이 너무 많은 이메일을 보내는 것으로 판단되면 해당 보낸 사람으로부터 받을 이메일 수에 제한을 설정합니다.

   * 이메일 수신 여부를 확인할 때 다음 네 가지 주요 카테고리에 주력해야 합니다.데이터 품질, 메시지 및 컨텐츠, 전송 인프라 및 명성을 높일 수 있습니다. 이 주제에 대한 자세한 내용은 [이 섹션을 참조하십시오](../../delivery/using/about-deliverability.md).

* 이 문서 [에 설명된 권장 사항을 적용합니다](../../delivery/using/deliverability-key-points.md).

* 도움이 필요하면 Adobe 담당자에게 문의하십시오.

## 검역 관리 {#quarantine-management}

우수한 검역 관리 과정을 유지하는 것이 귀하의 관심에 달려 있습니다.

새 플랫폼에서 이메일을 전송하기 시작하면 자격이 충분히 되지 않은 주소 목록을 사용할 수 있습니다. 잘못된 주소 또는 허니포트 주소(스패머를 조작하기 위해 만든 메일함)로 보내는 경우 플랫폼의 명성은 낮아집니다. 탁월한 격리 관리 프로세스주소 품질 유지, 인터넷 액세스 제공업체별 차단 목록 방지, 오류 속도 감소, 전달 및 처리량 속도 향상

**팁**

* 잘못된 주소 목록이 있는 경우, Adobe은 **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Non deliverables and addresses]**&#x200B;를 통해 격리 테이블로 가져오는 것이 좋습니다.

* 주소가 격리된 수신자는 배달 분석 중에 기본적으로 제외됩니다.타깃팅되지 않습니다. 이를 통해 게재 속도를 높일 수 있습니다. 오류율은 게재 속도에 상당한 영향을 미치기 때문입니다. 받은 편지함이 가득 찼거나 주소가 없는 경우 이메일 주소를 격리할 수 있습니다. [자세히 알아보기](#identifying-quarantined-addresses-for-a-delivery)

* Adobe Campaign은 반환된 오류 유형에 따라 잘못된 주소를 관리합니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../delivery/using/understanding-quarantine-management.md)을 참조하십시오.


* 일부 인터넷 액세스 제공 업체는 잘못된 주소의 비율이 너무 높은 경우 이메일을 자동으로 스팸으로 간주합니다. 따라서 격리 기능을 사용하면 이러한 제공자가에 추가하는 것을 차단 목록 방지할 수 있습니다.

* 검역관리 역시 잘못된 전화 번호를 배달에서 제외함으로써 SMS를 보내는 비용을 줄이는 데 도움이 될 것이다.

## 이중 옵트인 메커니즘 {#double-opt-in}

잘못된 주소로 메시지를 보내지 않고, 부적절한 통신을 제한하며, 발신자의 명성을 높이려면, Adobe은 구독 후 확인을 위해 이중 옵트인 메커니즘을 구현할 것을 권장합니다. 이렇게 하면 수신자가 의도적으로 구독할 수 있습니다.

이 메커니즘을 구현하기 위한 자세한 내용은 [이 섹션에 요약되어 있습니다](../../web/using/use-cases--web-forms.md).
