---
title: 캠페인 전달 모범 사례
seo-title: 전달 모범 사례
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f599bc5483779ae62dd4d5eb1936cbc2760639b5
workflow-type: tm+mt
source-wordcount: '4348'
ht-degree: 3%

---


# 전달 모범 사례 {#delivery-best-practices}

## 전달 최적화 {#optimize-delivery}

게재 생성을 시작하기 전에 여러 작업을 수행하여 전송 프로세스를 보호하고 최적화할 수 있습니다.

다음 섹션에서는 Adobe Campaign의 최적 구성을 위한 모범 사례와 권장 절차에 대해 설명합니다. 이러한 관행을 따르면 다운스트림에 직면할 수 있는 문제를 최소화할 수 있습니다.

### 플랫폼 성능

몇 가지 요소는 서버 성능에 직접적인 영향을 주고 플랫폼을 느리게 할 수 있습니다.

* 개인화 요소의 수 및 유형: 이메일의 개인화는 각 수신자에 대한 데이터를 데이터베이스에서 가져옵니다. 개인화 요소가 많은 경우 전달을 준비하는 데 필요한 데이터의 양이 증가합니다.  이 섹션에서 개인화에 대한 자세한 [내용](../../delivery/using/about-personalization.md)

* 서버 로드: 마케팅 서버가 동시에 여러 가지 작업을 처리할 때 성능이 저하될 수 있습니다. 마케팅 서버는 데이터가 정확하고 정시에 맞는지 확인하기 위해 모든 게재에 대해 수신 및 발신 데이터를 모두 조정해야 합니다.

   **팁** - 이를 방지하려면 팀 내 다른 구성원과 배달 예약을 조정하여 최상의 성능을 보장합니다.

* 워크플로우 실행: 플랫폼 성능 문제를 방지하려면 워크플로우 모니터링이 필요합니다. 이 문서 [에 나와 있는 지침을 따르십시오](../../workflow/using/workflow-best-practices.md#execution-and-performance).

* 호스팅 고객인 경우 [캠페인 제어 패널 기능을](https://docs.adobe.com/content/help/en/control-panel/using/discover-control-panel/key-features.html) 활용하여 [성능 모니터링](https://docs.adobe.com/content/help/en/control-panel/using/performance-monitoring/about-performance-monitoring.html) 기능을 사용하여 플랫폼을 모니터링할 수 있습니다.

### 네트워크 구성 확인 {#network-config}

대량의 이메일을 처리할 때 배달을 최적화하고 스패머로 오인되지 않도록 하려면 서버의 ID를 숨기려고 하지 않는 적절한 네트워크 구성이 있는지 확인하십시오.

**팁**:  브랜드의 웹 사이트에 해당하는 투명한 보낸 사람 주소를 사용합니다. 예를 들어, 여행사 회사는 발렌티노 호텔 체인을 관리합니다. 자체 웹사이트에 발렌티노.com 도메인을 보유하고 있다. 파리 발렌티노 호텔을 홍보하기 위해 파리.발렌티노.com 하위 도메인을 사용한다. 따라서 관련 보낸 사람 주소는 hotel@paris.valentino.com일 수 있습니다.

### 전달 능력 관리 {#deliverability-management}

수신자의 받은 편지함에 도달하기 위해 메시지 전달 비율을 향상시켜야 합니다.

* 배달능력이란?

   * 받는 사람의 서버에서 받을 수 있는 기능을 결정하는 이메일의 요인을 나타냅니다. ISP(Internet Service Providers)는 스팸으로 식별하는 이메일을 필터링하거나 이미지를 다운로드하지 못하도록 차단합니다. 특정 도메인이 너무 많은 이메일을 보내는 것으로 판단되면 해당 보낸 사람으로부터 받을 이메일 수에 제한을 설정합니다.

   * 이메일 수신 여부를 확인할 때 다음 네 가지 주요 카테고리에 주력해야 합니다. 데이터 품질, 메시지 및 컨텐츠, 전송 인프라 및 명성을 높일 수 있습니다. 이 주제에 대한 자세한 내용은 [이 섹션을 참조하십시오](../../delivery/using/about-deliverability.md).

* 이 문서 [에 설명된 권장 사항을 적용합니다](../../delivery/using/deliverability-key-points.md).

* 도움이 필요하면 Adobe 담당자에게 문의하십시오.

### 검역 관리 {#quarantine-management}

우수한 검역 관리 과정을 유지하는 것이 귀하의 관심에 달려 있습니다.

새 플랫폼에서 이메일을 전송하기 시작하면 자격이 충분히 되지 않은 주소 목록을 사용할 수 있습니다. 잘못된 주소 또는 허니포트 주소(스패머를 조작하기 위해 만든 메일함)로 보내는 경우 플랫폼의 명성은 낮아집니다. 탁월한 격리 관리 프로세스 주소 품질 유지, 인터넷 액세스 제공업체별 차단 목록 방지, 오류 속도 감소, 전달 및 처리량 속도 향상

**팁**

* 잘못된 주소 목록이 있는 경우, Adobe은 **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Non deliverables and addresses]**&#x200B;를 통해 격리 테이블로 가져오는 것이 좋습니다.

* 주소가 격리된 수신자는 배달 분석 중에 기본적으로 제외됩니다. 타깃팅되지 않습니다. 이를 통해 게재 속도를 높일 수 있습니다. 오류율은 게재 속도에 상당한 영향을 미치기 때문입니다. 받은 편지함이 가득 찼거나 주소가 없는 경우 이메일 주소를 격리할 수 있습니다. [자세히 알아보기](#identifying-quarantined-addresses-for-a-delivery)

* Adobe Campaign은 반환된 오류 유형에 따라 잘못된 주소를 관리합니다. 자세한 정보는 [이 섹션](../../delivery/using/understanding-quarantine-management.md)을 참조하십시오.


* 일부 인터넷 액세스 제공 업체는 잘못된 주소의 비율이 너무 높은 경우 이메일을 자동으로 스팸으로 간주합니다. 따라서 격리 기능을 사용하면 이러한 공급자가 차단 목록에 추가하지 않을 수 있습니다.

* 검역관리 역시 잘못된 전화 번호를 배달에서 제외함으로써 SMS를 보내는 비용을 줄이는 데 도움이 될 것이다.

### 이중 옵트인 메커니즘 {#double-opt-in}

잘못된 주소로 메시지를 보내지 않고, 부적절한 통신을 제한하며, 발신자의 명성을 높이려면, Adobe은 구독 후 확인을 위해 이중 옵트인 메커니즘을 구현할 것을 권장합니다. 이렇게 하면 수신자가 의도적으로 구독할 수 있습니다.

이 메커니즘을 구현하기 위한 자세한 내용은 [이 섹션에 요약되어 있습니다](../../web/using/use-cases--web-forms.md).

## 템플릿 사용 {#use-templates}

전달 템플릿을 사용하면 대부분의 일반적인 유형의 활동에 대해 미리 만들어진 시나리오를 제공하여 효율성을 높일 수 있습니다. 템플릿을 사용하면 마케터는 짧은 시간에 맞춤화를 최소화하면서 새로운 캠페인을 배포할 수 있습니다.

이 섹션에서 배달 템플릿에 대한 자세한 내용 [을 살펴보십시오](../../delivery/using/creating-a-delivery-template.md).

### 전달 템플릿 시작하기 {#gs-templates}

배달 템플릿을 [사용하면](../../delivery/using/creating-a-delivery-template.md) 사용자의 요구 사항에 부합하고 향후 게재에 재사용할 수 있는 기술 및 기능 속성 세트를 한 번 정의할 수 있습니다. 그런 다음 시간을 절약하고 필요에 따라 배달을 표준화할 수 있습니다.

Adobe Campaign에서 여러 브랜드를 관리하는 경우, Adobe은 브랜드당 하나의 하위 도메인을 가질 것을 권장합니다. 예를 들어 은행은 각 지역 기관에 해당하는 여러 하위 도메인을 가질 수 있습니다. 은행이 bluebank.com 도메인을 보유하고 있는 경우 해당 하위 도메인은 @ny.bluebank.com, @ma.bluebank.com, @ca.bluebank.com 등이 될 수 있습니다. 하위 도메인당 하나의 배달 템플릿을 사용하면 항상 각 브랜드에 대해 사전 구성된 올바른 매개 변수를 사용할 수 있으므로 오류를 방지하고 시간을 절약할 수 있습니다.

**팁**:  Campaign Standard에서 구성 오류를 방지하려면 새 템플릿을 만드는 대신 기본 템플릿을 복제하고 해당 속성을 변경하는 것이 좋습니다.

**주소 구성**

* 보낸 사람의 주소는 이메일을 보낼 수 있도록 허용해야 합니다.

* 일부 ISP(Internet Service Providers)는 메시지를 수락하기 전에 발신자 주소의 유효성을 확인합니다.

* 형식이 잘못되면 수신 서버에서 주소가 거부될 수 있습니다. 정확한 주소를 입력해야 합니다.

* 주소는 발신자를 명시적으로 식별해야 합니다. 도메인은 발신자가 소유해야 하며 발신자에게 등록되어 있어야 합니다.

* Adobe은 배달 및 답글에 대해 지정된 주소에 해당하는 이메일 계정을 만드는 것을 권장합니다. 메시징 시스템 관리자에게 문의하십시오.

캠페인 인터페이스에서 주소를 구성하려면 아래 단계를 따르십시오.

1. 배달 [템플릿에서](../../delivery/using/creating-a-delivery-template.md)링크를 클릭합니다 **[!UICONTROL From]** . 창에서 **[!UICONTROL Email header parameters]** 다음 필드를 입력합니다.

   ![](assets/d_best_practices_email_header.png)

1. 필드에서 **[!UICONTROL Sender address]** 주소 도메인이 Adobe에 위임한 하위 도메인과 같은지 확인합니다. &#39;@&#39; 앞의 부분은 변경할 수 있지만 도메인 주소는 변경할 수 없습니다.

1. 이 **[!UICONTROL From]** 필드에서 브랜드 이름과 같은 수신자가 쉽게 식별할 수 있는 이름을 사용하여 배송 시작 비율을 높입니다. 수신자의 경험을 더 개선하기 위해 &quot;Emma from Megasstore&quot;와 같은 이름을 추가할 수 있습니다.

1. 필드에서 **[!UICONTROL Reply address text]** 발신자의 주소는 답글에 기본적으로 사용됩니다. 그러나 Adobe은 브랜드의 고객 지원 센터와 같은 기존 실제 주소를 사용하는 것이 좋습니다. 이 경우 수신자가 응답을 보낼 경우 고객 지원 센터에서 이 응답을 처리할 수 있습니다.

**컨트롤 그룹 설정**

배달을 전송하면 제외된 받는 사람의 동작을 배달을 받은 받는 사람과 비교할 수 있습니다. 그런 다음 캠페인의 효율성을 측정할 수 있습니다. 제어 그룹에 대해 자세히 [알아보십시오](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

제어 그룹을 설정하려면 **[!UICONTROL To]** 링크를 클릭합니다. 창에서 **[!UICONTROL Select target]** 탭을 **[!UICONTROL Control group]** 선택합니다. 예를 들어 5% 임의 샘플과 같이 대상의 일부를 추출할 수 있습니다.

![](assets/d_best_practices_control_group.png)

**필터 또는 컨트롤 규칙을 적용하려면 유형 지정 기능을 사용하십시오.**

유형학 유형에는 메시지를 보내기 전에 분석 단계 동안 적용되는 확인 규칙이 포함됩니다.

템플릿 속성의 **[!UICONTROL Typology]** 탭에서 필요에 따라 기본 유형을 변경합니다.

예를 들어 아웃바운드 트래픽을 보다 잘 제어하기 위해 하위 도메인당 하나의 관련성을 정의하고 선호도 당 하나의 유형을 만들어 사용할 수 있는 IP 주소를 정의할 수 있습니다. 인스턴스의 구성 파일에 친화성이 정의됩니다. Adobe Campaign 관리자에게 문의하십시오.

For more on typologies, refer to [this section](../../campaign/using/about-campaign-typologies.md).

## 디자인 및 개인화 {#design-and-personalize}

메시지 내용을 디자인할 때 배달 실행을 방지할 수 있는 일반적인 문제를 방지하십시오. 대부분의 경우 [개인화](../../delivery/using/about-personalization.md), 서식 [및](../../delivery/using/defining-the-email-content.md#message-content) 이미지 [와 관련된 오류가 발생할 수 있습니다](../../delivery/using/defining-the-email-content.md#adding-images).

### 개인화 최적화 {#optimize-personalization}

메시지 전달을 실행하지 못하도록 하고 받는 사람의 경험을 향상시킬 수 있는 일반적인 문제를 방지하기 위해 Adobe Campaign을 사용하면 메시지를 개인화할 수 있습니다.

Adobe Campaign 데이터베이스에 저장된 수신자 데이터를 사용하거나 추적, 랜딩 페이지, 구독 등을 통해 수집할 수 있습니다.
개인화 기본 사항은 [이 섹션에 나와 있습니다](../../delivery/using/personalization-fields.md).

메시지 컨텐츠가 개인화와 관련된 오류를 방지하도록 제대로 설계되었는지 확인하십시오.

**팁**: 타사 공급업체에서 제공한 외부 파일에서 나오는 개인화 필드에서 외부 HTML 콘텐츠가 잘못될 수 있습니다. 이를 방지하려면 구문, 태그, 문자 등의 사용을 확인하십시오. 예를 들어 Adobe Campaign 개인화 태그에는 항상 다음 양식이 있습니다. &lt;%=table.field%>. 자세한 내용은 [이 섹션](../../delivery/using/about-personalization.md)을 참조하십시오.

개인화 블록에서 매개 변수가 잘못 사용될 수 있습니다. 예를 들어 JavaScript의 변수는 다음과 같이 사용해야 합니다.

    &lt;%
    
    var brand = &quot;xxx&quot;
    
    %>

개인화 블록에 대한 자세한 내용은 [이 섹션을 참조하십시오](../../delivery/using/personalization-blocks.md).

워크플로우에서 개인화 데이터를 준비하여 전달 준비 분석을 향상시킬 수 있습니다. 개인화 데이터가 FDA(Federated Data Access)를 통해 외부 테이블에서 가져오는 경우 특별히 사용해야 합니다. 이 옵션은 [이 섹션에 설명되어 있습니다.](../../delivery/using/personalization-fields.md#optimizing-personalization)

### 최적화된 콘텐츠 제작 {#optimize-content}

이메일을 작성할 때 아래의 일반적인 모범 사례를 염두에 두십시오.

* 디자인 간소화

* 모바일 사용자를 염두에 두십시오

* 이미지 기반의 이메일 수신 방지

* 이메일 안전 글꼴 사용

* 특수 문자 인코딩

**제목 라인** - [제목](../../delivery/using/defining-the-email-content.md#message-content) 라인에서 작업하여 열률을 향상시킵니다.

* 너무 긴 과목은 피하세요. 최대 50자를 사용할 수 있습니다

* 스팸으로 간주될 수 있는 &quot;무료&quot; 또는 &quot;오퍼&quot;와 같은 반복적인 단어를 사용하지 마십시오

* 대문자 및 &quot;!&quot;, &quot; 저녁&quot;, &quot;\&quot;, &quot;$&quot;와 같은 특수 문자를 사용하지 마십시오.

**미러 페이지** - 항상 미러 페이지 링크를 포함합니다. 이메일의 맨 위에 기본 위치가 있습니다. [자세히 알아보기](../../delivery/using/sending-messages.md#generating-the-mirror-page)

**구독 취소 링크** - 구독 취소 링크는 필수입니다. 반드시 표시되고 유효해야 하며, 양식이 제대로 작동하는지 확인해야 합니다. 기본적으로 메시지를 분석하면 분류 규칙 [이 옵트아웃 링크](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies) 포함 여부를 확인하고 누락된 경우 경고를 생성합니다.

**팁**: 사용자 오류는 항상 가능하므로 전송 때마다 옵트아웃 링크가 제대로 작동하는지 확인합니다. 예를 들어 증거를 보낼 때 링크가 유효한지, 양식이 온라인인지, 이 수신자에게 더 이상 연락하지 않음 필드가 예로 변경되었는지 확인하십시오.

이 섹션 [에 옵트아웃 링크를 삽입하는 방법을 알아봅니다](../../delivery/using/personalization-blocks.md#personalization-blocks-example).

**이메일 크기** - 성능이나 전달 가능성 문제를 방지하기 위해 권장되는 최대 이메일 크기는 **35KB입니다**. 메시지 크기를 확인하려면 **[!UICONTROL Preview]** 탭으로 이동하여 테스트 프로필을 선택합니다. 메시지 크기가 생성되면 오른쪽 상단 모서리에 표시됩니다.

이메일을 제한된 범위 내에서 유지하려면 다음을 고려하십시오.

* 중복 또는 사용하지 않는 스타일 제거

* 이메일 콘텐츠 중 일부를 랜딩 페이지로 이동

* 코드 축소

최종 전송 전에 변경 사항을 테스트하십시오

**SMS 길이**

기본적으로 SMS의 글자 수는 GSM(이동통신 글로벌 시스템) 표준을 충족합니다. GSM 인코딩을 사용하는 SMS 메시지는 SMS당 160자, 또는 여러 부분으로 나누어 전송되는 메시지의 경우 153자로 제한됩니다.

변환은 GSM 표준에서 고려하지 않는 SMS 문자를 다른 문자로 바꾸는 작업입니다. SMS 메시지의 컨텐츠에 개인화 필드를 삽입하면 GSM 인코딩에 의해 고려되지 않는 문자가 도입될 수 있습니다. 해당 채널의 SMPP 채널 설정 탭에서 해당 상자를 선택하여 문자 교환을 인증할 수 있습니다 **[!UICONTROL External account]**.
이 섹션 [에서 자세히 알아보십시오](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

**팁**:

* SMS 메시지의 모든 문자를 그대로 유지하려면 적절한 이름을 바꾸지 마십시오. 음역을 활성화하지 마십시오.

* 그러나 GSM 표준으로 간주되지 않는 많은 문자가 SMS 메시지에 포함되어 있는 경우, 교역을 활성화하여 메시지 전송 비용을 제한합니다.

이 섹션 [에서 자세히 알아보십시오](../../delivery/using/sms-channel.md#about-character-transliteration).

### 서식에 대한 작업 {#formatting}

일반적인 서식 오류를 방지하려면 다음 요소를 확인하십시오.

* 올바른 **날짜 서식**: Adobe Campaign은 JavaScript 템플릿 및 XSL 스타일시트에 날짜 서식 기능을 제공합니다. [자세히 알아보기](../../delivery/using/formatting.md#date-display)

* 이메일에서 **인증된 문자** 사용: 이메일 주소의 유효한 문자 목록은 &quot;XtkEmail_Characters&quot; 옵션에 정의되어 있습니다. 이 섹션에서 캠페인 옵션 [에 액세스하는 방법을 알아봅니다](../../installation/using/configuring-campaign-options.md). 특수 문자를 올바로 처리하려면 유니코드로 Adobe Campaign을 설치해야 합니다.

* 이메일 **인증 구성**: 이메일 헤더에 DKIM 서명이 포함되어 있는지 확인합니다. DKIM(Domain Keys Identified Mail) 인증을 통해 수신 이메일 서버는 메시지를 보낸 것이라고 주장하는 사람 또는 엔티티가 메시지를 실제로 보냈는지, 메시지 컨텐츠가 처음 전송된 시간(및 DKIM &quot;signed&quot;) 및 수신한 시간 사이에 변경되었는지 여부를 확인할 수 있습니다. 이 표준은 일반적으로 보낸 사람 헤더의 도메인을 사용합니다. 자세한 정보는 [이 섹션](../../delivery/using/technical-recommendations.md#dkim)을 참조하십시오.

* **반응형 이메일 디자인을** 사용하면 이메일이 열려 있는 장치에 최적화된 방식으로 렌더링됩니다.

   * 웹 HTML이 아닌 반응형 이메일 HTML을 사용하십시오.

   * 미리 보기 모드를 사용하여 가능한 한 많은 디바이스에서 렌더링을 테스트할 수 있습니다.

   * Adobe Campaign Classic DCE(Digital Content Editor) 모듈에는 **[!UICONTROL Resources]** > **[!UICONTROL Templates]** 를 통해 사용할 수 있는 모바일용 반응형 디자인 형식 템플릿이 포함되어 있습니다 **[!UICONTROL Content templates]**. 이 문서 [에서 자세히 알아보십시오](https://theblog.adobe.com/responsive-email-design-101/).



### 이미지 관리 {#manage-images}

이미지 사용에 대해서는 아래 지침을 따르십시오.

* **이미지 차단** 방지 - 일부 이메일 클라이언트는 기본적으로 이미지를 차단하며 일부 사용자는 데이터 사용을 위해 이미지를 차단하도록 설정을 변경합니다. 따라서 이미지를 다운로드하지 않으면 전체 메시지가 손실될 수 있습니다. 이를 방지하려면

   * 콘텐츠와 이미지 및 텍스트의 균형을 맞출 수 있습니다. 이미지 기반의 이메일 전달

   * 이미지에 텍스트를 포함해야 하는 경우 대체 및 제목 텍스트를 사용하여 메시지가 제대로 전달되는지 확인하십시오. 대체/제목 텍스트에 스타일을 지정하여 모양을 향상시킬 수 있습니다.

   * 일부 이메일 클라이언트에서 지원하지 않는 배경 이미지는 사용하지 마십시오.

* **반응형** 이미지 제작 - 반응형 이미지를 만들고 크기를 조절할 수 있습니다. 이렇게 하면 구축하는 데 시간이 더 걸리기 때문에 비용 측면에서 영향을 줄 수 있습니다.

* **절대 이미지 참조** 사용 - 외부에서 액세스할 수 있으려면 캠페인에 연결된 이메일 및 공개 리소스에 사용된 이미지가 외부에서 액세스 가능한 서버에 있어야 합니다.

   * 인스턴스 구성이 공개 리소스 관리를 활성화하는지 확인할 수 있습니다. [자세히 알아보기](../../installation/using/deploying-an-instance.md#managing-public-resources)

   * 배달 마법사에서 이미지가 포함된 HTML 페이지를 가져오거나 아이콘을 통해 HTML 편집기를 사용하여 직접 이미지를 삽입할 수 **[!UICONTROL Image]** 있습니다. [자세히 알아보기](../../delivery/using/defining-the-email-content.md#adding-images)

   * 이미지가 표시되지 않으면 서버에서 이미지를 사용할 수 있는지 확인하십시오. 이렇게 하려면 게재에서 소스 탭을 클릭합니다. 이미지를 찾아 웹 브라우저에서 각 이미지의 URL을 복사하여 붙여넣습니다. 이미지가 표시되지 않으면 IT 관리자나 배달 내용을 제공하는 타사 공급업체에 문의하십시오.

### 메시지 미리 보기 {#preview-msg}

Adobe은 메시지를 미리 보고 개인화와 수신자가 전달을 어떻게 볼 수 있는지 확인하는 것이 좋습니다.

* 전달 창에서 **[!UICONTROL Preview]** 하위 탭을 사용하여 수신자의 각 컨텐츠 렌더링을 볼 수 있습니다. 개인화 필드 및 컨텐츠 조건부 요소는 선택한 프로필에 대한 해당 정보로 대체됩니다. [자세히 알아보기](../../delivery/using/defining-the-email-content.md#message-content)

* 각 미리 보기 중에 스팸 방지 자동 검사가 수행됩니다. 하위 **[!UICONTROL Preview]** 탭에서 SpamAsser [스팸 점수](../../delivery/using/spamassassin.md) 지정을 확인합니다.  경고 **[!UICONTROL More...]** 에 대한 자세한 내용을 보려면 을 클릭합니다.  SpamAsser가 Adobe Campaign 응용 프로그램 서버에 올바르게 설치 및 구성되어 있는지 확인하십시오. [자세히 알아보기](../../installation/using/configuring-spamassassin.md)

## 올바른 타겟 정의 {#define-the-right-target}

타깃팅된 모집단: 목록을 주의 깊게 만들고, 인기 있는 이메일 클라이언트 및 모바일 디바이스에서 이메일을 테스트하고, 이메일 목록이 최신(알 수 없거나 오래된 주소 없음)인지 확인합니다. 또한 전체 인증 주기를 설정하는 데 도움이 되는 교정을 전송할 수 있습니다.

이 섹션 [에서 타겟 모집단에 대한 자세한 내용](../../delivery/using/steps-defining-the-target-population.md)

### Target {#target-the-right-audience}

콘텐츠를 준비하면 메시지를 받을 사람을 신중하게 정의해야 합니다.

최적의 콘텐츠를 수신자에게 전달하면 Adobe Campaign을 사용하면 가장 정확한 타겟을 구축할 수 있습니다. 이전 배달에서 링크를 클릭한 경우 연령, 로컬라이제이션, 구매한 항목, 구매한 항목 등에 따라 수신자를 선택할 수 있습니다. 또한 Adobe Campaign을 사용하여 테스트 프로필, 제어 그룹 및 시드 주소를 정의하여 타겟이 올바른지 확인할 수 있습니다.

### 대상 매핑 {#target-mappings}

Campaign Classic에서 기본적으로 배달 템플릿은 수신자를 **타깃팅합니다**. Adobe Campaign은 필요에 따라 변경할 수 있는 게재에 대한 다른 대상 매핑을 제공합니다.

예를 들어 소셜 네트워크를 통해 프로필이 수집된 방문자 또는 정보 서비스에 가입한 방문자에게 전달할 수 있습니다.

이러한 매핑은 이 섹션 [에 표시됩니다](../../delivery/using/selecting-a-target-mapping.md).

사용자 지정된 대상 매핑을 만들고 사용할 수도 있습니다. 자세한 정보는 [이 섹션](../../configuration/using/target-mapping.md)을 참조하십시오.

### 외부 수신자 {#external-recipients}

데이터베이스에 저장되지 않고 외부 파일에 저장된 수신자에게 전달할 수 있습니다. 이 섹션 [에서 자세히 알아보십시오](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients).

### 구독자에게 보내기 {#send-to-subscribers}

뉴스레터의 가입자에게 메시지를 전송하려면 해당 정보 서비스에 가입자를 직접 타깃팅할 수 있습니다. 이 섹션 [에서 자세히 알아보십시오](../../delivery/using/managing-subscriptions.md#delivering-to-the-subscribers-of-a-service).


### 수신자 및 시드 주소 테스트 {#test-recipients-seed-addresses}

전달 내용을 테스트하려면 주 타겟으로 보내기 전에 교정본을 사용하십시오.

양식 및 메시지 내용의 유효성을 검사하므로 적절한 증명 수신자를 선택해야 합니다. 증명 받는 사람을 정의하는 단계는 이 섹션 [에 나와 있습니다](../../delivery/using/steps-defining-the-target-population.md#selecting-the-proof-target).

시드 주소는 기본 타겟으로 보내기 전에 배달을 테스트하기 위해 정의된 대상 기준과 일치하지 않는 수신자를 타게팅하는 데 사용됩니다. 이 섹션 [에 나와 있습니다](../../delivery/using/about-seed-addresses.md).

### 중복 주소 제거 {#deduplicate-addresses}

중복된 이메일 주소는 타겟에 영향을 줄 수 있으므로 피하는 것이 중요합니다.

* 대상이 분할될 때 동일한 메시지를 두 번 이상 보낼 수 있습니다.

* 수신자가 메시지를 받은 후 구독을 취소하는 경우 중복된 프로필은 여전히 향후 메시지를 수신하게 됩니다.

중복 제거 주소는 전송 명성을 보호하고 안전한 격리 관리를 보장합니다.

이 사례 [에 대한 자세한 내용을 살펴보십시오](../../workflow/using/deduplication.md#example--identify-the-duplicates-before-a-delivery).


### 색인 이메일 주소 {#index-addresses}

응용 프로그램에 사용되는 SQL 쿼리의 성능을 최적화하기 위해 데이터 스키마의 기본 요소에서 인덱스를 선언할 수 있습니다.

이메일 주소에 색인을 추가하는 단계는 이 섹션 [에 나와 있습니다](../../configuration/using/database-mapping.md#indexed-fields).

## 보내기 전에 모든 확인 수행 {#perform-all-checks}

메시지가 준비되면, 모든 장치에서 해당 컨텐츠가 올바르게 표시되는지 확인하고, 개인화나 깨진 링크 등의 오류를 포함하지 마십시오.

메시지를 보내기 전에 매개 변수 및 구성이 전달과 일치하는지 확인하십시오.

### 유효성 검사가 핵심 {#validation-is-key}

배달을 보내기 전에 받는 사람이 실제로 보내려는 메시지를 받게 해야 합니다. 이렇게 하려면 메시지 내용 및 배달 매개 변수의 유효성을 확인해야 합니다.

이 단계를 통해 가능한 오류를 감지하여 주 타겟으로 전달하기 전에 수정할 수 있습니다.

배달을 확인하는 단계는 이 섹션 [에 나와 있습니다](../../delivery/using/steps-validating-the-delivery.md).

### 받은 편지함 렌더링 {#inbox-and-email-rendering}

받은 편지함 렌더링을 사용하면 주요 이메일 클라이언트에서 메시지를 미리 보고, 컨텐츠와 명성을 스캔하고, 수신자가 어떻게 메시지를 읽고 있는지 파악할 수 있습니다.

**팁**:

* 수신될 수 있는 다른 컨텍스트에서 보낸 메시지를 볼 수 있습니다. 웹메일, 메시지 서비스, 모바일 등

* 받은 편지함 렌더링 기능은 이메일 캠페인이 주요 ISP(Internet Service Providers)와 웹 메일 서비스의 필터를 성공적으로 통과하는지 여부를 식별하기 위해 중요합니다. 이러한 도구는 이메일의 시험판 사본을 테스트 받은 편지함의 네트워크로 전송하므로, 이러한 서비스에서 메시지가 어떻게 표시되거나 렌더링되는지 확인할 수 있습니다. 또한 보고서 및 코드 교정 옵션을 포함하여 빠르게 식별하고 전달을 개선하는 수정 사항을 만들 수 있습니다.

이 섹션 [에서 자세히 알아보십시오](../../delivery/using/inbox-rendering.md).

### 증명 메시지 {#proof-messages}

교정본을 전송하면 옵트아웃 링크, 미러 페이지 및 기타 링크를 확인하고, 메시지를 확인하고, 이미지가 표시되는지 확인하고, 가능한 오류 감지 등을 수행할 수 있습니다. 또한 다양한 디바이스에서 디자인과 렌더링을 확인할 수 있습니다.

이 섹션 [에서 자세히 알아보십시오](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### A/B 테스트 배달 설정 {#a-b-testing-deliveries}

이메일 전달에 필요한 컨텐츠가 여러 개 있는 경우 A/B 테스트를 사용하여 타깃팅된 모집단에게 가장 큰 영향을 미치는 버전을 확인할 수 있습니다.

**팁**:

* 수신자의 일부에게 다른 버전 보내기

* 성공률이 가장 높은 타겟을 선택하고 나머지 타겟으로 보냅니다.

이 섹션 [에서 자세히 알아보십시오](../../workflow/using/a-b-testing.md).

### 메시지가 전달되었는지 확인 {#make-sure-your-message-is-delivered}

마지막 단계로 Adobe Campaign Classic의 역량을 최대한 발휘하여 관련 수신자에게 메시지를 전달할 수 있습니다.

**유효성 검사 프로세스** 진행 - Adobe Campaign 연산자와 그룹이 포함된 전체 유효성 검사 프로세스를 정의하여 대상 및 메시지 컨텐츠의 유효성을 모두 확인할 수 있습니다. 이렇게 하면 캠페인의 다양한 프로세스를 완전히 모니터링하고 제어할 수 있습니다. 타깃팅, 컨텐츠, 예산, 추출 및 증명 전송 사용 권한에 따라 사용자에게 알림 메시지를 전송하고 증거 기록을 수신하며 메시지의 유효성을 검사하거나 거부할 수 있습니다. 이 섹션 [에서 자세히 알아보십시오](../../campaign/using/marketing-campaign-approval.md#approval-process).

**파도** 사용 - 파동을 사용하여 보낸 양을 점진적으로 늘릴 수 있습니다. 이렇게 하면 메시지가 스팸으로 표시되거나 일별 메시지 수를 제한하려는 경우 피됩니다. 파도를 사용하면 대량의 메시지를 동시에 보내지 않고 여러 개의 배치로 배달을 나눌 수 있습니다. 이 섹션 [에서 자세히 알아보십시오](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).

**메시지** 우선 순위 - 우선순위 수준을 표시하여 게재에 대한 전송 순서를 설정할 수 있습니다. 방법은 다음과 같습니다.

1. 배달 속성을 편집하고 **[!UICONTROL Delivery]** 탭을 선택합니다.

1. 배달에 대한 우선 순위 레벨을 척도에서 **[!UICONTROL Very low]** 로 정의합니다 **[!UICONTROL Very high]**.

>[!NOTE]
>
>배달 내에서 메시지를 보내는 순서를 정의할 수 없습니다.

**IP 친화성** 설정 - 아웃바운드 SMTP 트래픽을 더 잘 제어하려면 각 관련성에 사용할 수 있는 특정 IP 주소를 정의하여 친화성을 관리할 수 있습니다. 이를 통해 시스템이나 출력 주소로 특정 게재에 대한 이메일 수를 제한할 수 있습니다. 예를 들어 국가 또는 하위 도메인마다 하나의 관련성을 사용할 수 있습니다. 그런 다음 국가별로 하나의 유형을 만들고 각 관련성을 해당 유형에 연결할 수 있습니다.

다음을 수행할 수 있습니다.

* serverConf.xml 구성 파일에서 IP 기능을 정의합니다. [자세히 알아보기](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)

* 각 IPAfferity 요소에 대해 사용할 수 있는 IP 주소를 선언합니다. [자세히 알아보기](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

* 선택한 [유형](../../campaign/using/about-campaign-typologies.md) 에서 **[!UICONTROL Managing affinities with IP addresses]** 필드를 사용하여 해당 관련성을 관리하는 배달 서버(MTA)에 배달을 연결합니다. [자세히 알아보기](../../campaign/using/applying-rules.md#control-outgoing-smtp-traffic).

* 이메일이 전송되면 헤더를 확인하여 배달을 보낸 IP 주소를 확인합니다. 이메일 관리자가 헤더 정보를 가져오는 데 도움이 됩니다.

>[!NOTE]
>
>이러한 대부분의 단계는 전문가 사용자만이 수행할 수 있습니다.

**유형 지정** 사용 - 유형 분류 규칙을 사용하여 특정 기준을 기반으로 대상의 일부를 제외할 수 있습니다. 따라서 전송된 메시지는 회사 커뮤니케이션 정책을 준수하면서 고객의 요구 사항과 기대치에 가장 적합한 메시지를 제공합니다. 예를 들어 뉴스레터의 대상에서 미성년자인 수신자를 필터링할 수 있습니다. 이 예제 [에서 자세히 알아보십시오](../../campaign/using/filtering-rules.md).

**첨부 파일** 방지 - 첨부 파일은 맬웨어 확산을 위한 가장 일반적인 벡터 중 하나로 남아 있으며, 특히 대량으로 전송될 때 더욱 그렇습니다. 문서를 첨부하지 않고 문서에 대한 보안 링크를 포함합니다. 이로 인해 의도하지 않은 재배포를 방지할 수 있는 추가 보안 레이어가 보장되고 메시지 크기나 보안상의 이유로 인바운드 이메일 게이트웨이에 메시지가 거부될 가능성이 크게 줄어듭니다.

## 추적 및 모니터 {#track-and-monitor}

전송 버튼을 클릭했습니까? 어떻게 되는지 봅시다. 배달이 전송되면 Adobe Campaign을 통해 보낸 메시지를 추적하고 수신자가 전달에 어떻게 반응하는지 알 수 있습니다. 이를 통해 향후 전송을 개선하고 다음 캠페인을 최적화할 수 있습니다.

### 배달 모니터링 {#monitoring-deliveries}

캠페인을 제어하려면 메시지를 받는 사람에게 실제로 전달했는지 확인해야 합니다.

캠페인 배달 대시보드에서 처리된 메시지와 배달 감사 로그를 확인할 수 있습니다.
배달 로그에 있는 메시지의 상태를 제어할 수도 있습니다. [자세히 알아보기](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard).

배송이 전송되지 않고 상태가 보류 **중으로 유지되면 어떻게 됩니까**?

* 일부 리소스가 사용 가능한 상태에서 실행 프로세스가 대기 중입니다. MTA가 시작되지 않았을 수 있습니다.
mta@instance 모듈이 MTA 서버에서 시작되었는지 확인하고 필요한 경우 MTA 모듈을 시작합니다. [자세히 알아보기](../../production/using/administration.md).

* 배달은 전송 인스턴스에서 구성되지 않은 친화성을 사용할 수 있습니다.
팁: 트래픽 관리(IP 친화성) 구성을 확인합니다. 자세한 내용은 나가는 SMTP 트래픽 제어를 참조하십시오.

>[!NOTE]
>
>이러한 단계는 전문가 사용자만 수행할 수 있습니다.

### 추적 {#tracking-deliveries}

수신자의 행동을 보다 정확하게 파악하려면 수신자가 전달에 어떻게 반응하는지 추적할 수 있습니다. 수신, 열기, 링크 클릭, 구독 취소 등 Campaign Classic에서 이 정보는 게재의 대상이 되는 수신자의 추적 탭 및 게재의 추적 탭에 표시됩니다. Campaign Standard에서 게재의 추적 로그 탭에 표시됩니다.

**팁**: 메시지 추적은 기본적으로 활성화되어 있습니다. URL을 구성하려면 배달 마법사의 아래 섹션에서 URL 표시 옵션을 선택합니다. 메시지의 각 URL에 대해 추적을 활성화할지 여부를 선택할 수 있습니다.

자세한 내용은 추적 [구성](../../delivery/using/how-to-configure-tracked-links.md) 섹션 및 [추적 지표](../../reporting/using/delivery-reports.md#tracking-indicators) 설명을 참조하십시오.

### 전달 성능 {#delivery-performances}

To measure the speed at the messages are delivered, you can control the delivery throughput. 기준은 시간당 전송된 메시지 수와 메시지 크기(초당 비트 수)입니다. For more on this, see [Delivery throughput](../../reporting/using/global-reports.md#delivery-throughput).

**팁**:

* 임시 테이블을 유지하고 성능에 영향을 주므로 인스턴스에 배달을 실패한 상태로 유지하지 마십시오.

* 더 이상 필요하지 않은 게재와 비활성 수신자를 데이터베이스에서 제거하여 주소 품질을 유지합니다.

* 큰 배달은 함께 예약하지 마십시오. 시스템에 로드를 균일하게 분산하는 데 5~10분이 걸릴 수 있습니다.

## 배달 문제 해결 {#delivery-troubleshooting}

배달과 관련된 문제가 발생할 때 특정 작업을 수행할 수 있습니다.

* [전달 가능성 문제](../../production/using/performance-and-throughput-issues.md#deliverability_issues)

* [이미지 표시 문제](../../production/using/image-display-issues.md)

* [전달 성능 문제](../../delivery/using/monitoring-a-delivery.md#performance_issues)

* [임시 파일 문제](../../production/using/temporary-files.md) - *온-프레미스 고객만 해당*
