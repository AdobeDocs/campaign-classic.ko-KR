---
product: campaign
title: Adobe Campaign Classic 데이터 모델 설명
description: 이 문서에서는 Adobe Campaign 데이터 모델에 대해 설명합니다
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용"
feature: Data Model
role: Data Engineer, Developer
exl-id: fc0fd23c-f9ea-4e30-b47b-a84143d882ca
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '2381'
ht-degree: 2%

---

# Campaign 데이터 모델 설명{#data-model-description}


Adobe Campaign은 사전 정의된 데이터 모델을 제공합니다. 이 섹션에서는 Adobe Campaign 데이터 모델의 기본 제공 테이블과 상호 작용에 대한 몇 가지 세부 정보를 제공합니다.

각 테이블의 설명에 액세스하려면 **[!UICONTROL Admin > Configuration > Data schemas]**&#x200B;목록에서 리소스를 선택하고 **[!UICONTROL Documentation]** 탭.

![](assets/data-model_documentation-tab.png)

>[!NOTE]
>
>애플리케이션에 포함된 데이터의 물리적 및 논리적 구조는 XML에 설명되어 있습니다. 스키마라고 하는 Adobe Campaign에 특정된 문법을 따릅니다. Adobe Campaign 스키마에 대한 자세한 내용은 다음을 참조하십시오. [이 섹션](../../configuration/using/about-schema-reference.md).

## 기본 테이블에 대한 설명 {#description-main-tables}

Adobe Campaign은 함께 연결된 테이블이 포함된 관계형 데이터베이스를 사용합니다.

다음 다이어그램은 Adobe Campaign 데이터 모델의 기본 비즈니스 테이블과 각 테이블의 기본 필드 간의 조인을 보여 줍니다.

<!--![](assets/data-model_diagram.png)-->

![](assets/data-model_simplified-diagram.png)

사전 정의된 Adobe Campaign 데이터 모델에는 아래 나열된 기본 테이블이 포함됩니다.

### NmsRecipient {#NmsRecipient}

이 테이블은 **nms:recipient** 스키마.

에 사용되는 기본 테이블입니다. **게재 수신자**. 따라서 여기에는 다양한 채널을 통한 게재에 필요한 정보가 포함됩니다.

* sEmail: 이메일 주소.
* iEmailFormat: 이메일 기본 설정 형식(텍스트 1개, HTML 2개, 정의되지 않은 경우 0).
* sAddress1, sAddress2, sAddress3, sAddress4, sZipCode, sCity는 우편 주소를 작성하는 데 사용됩니다(1997년 5월부터 XPZ 10-011 AFNOR 표준을 유지).
* sPhone, sMobilePhone, sFax에는 각각 전화, 휴대폰 및 팩스 번호가 포함됩니다.
* iBlackList는 프로필에 사용되는 기본 옵트아웃 플래그입니다(1은 &quot;구독 취소됨&quot;을 의미하고, 그렇지 않은 경우 0임).

iFolderId 필드는 수신자를 해당 실행 폴더에 연결하는 외래 키입니다. 자세한 내용은 [XtkFolder](#XtkFolder).

sCountryCode 필드는 수신자와 연결된 국가의 3166-1 Alpha 2 ISO 코드(2자)입니다. 이 필드는 국가 레이블 및 기타 국가 코드 데이터를 포함하는 국가 참조 테이블(NmsCountry)의 외래 키입니다. 국가를 채우지 않으면 값 &#39;XX&#39;가 저장됩니다(0 ID 레코드 대신 사용됨).

수신자 테이블에 대한 자세한 내용은 [이 섹션](../../configuration/using/about-data-model.md#default-recipient-table).

### Nms 그룹 {#NmsGroup}

이 테이블은 **nms:group** 스키마.

이를 통해 다음을 만들 수 있습니다. **수신자의 통계 그룹**. 수신자와 그룹 사이에는 다대다 관계가 있습니다. 예를 들어 한 수신자가 여러 그룹에 속할 수 있고 한 그룹은 여러 수신자를 포함할 수 있습니다. 그룹은 가져오기 또는 게재 타깃팅을 통해 수동으로 만들 수 있습니다. 그룹은 종종 게재 대상으로 사용됩니다. 필드에는 sName 그룹의 내부 이름을 나타내는 고유한 색인이 있습니다. 그룹이 폴더에 연결되어 있습니다(키는 iFolderId임). 자세한 내용은 [XtkFolder](#XtkFolder)).

### NmsRcpGrpRel {#NmsRcpGrpRel}

NmsRcpGrpRel 관계 테이블에는 iRecipientId 및 iGroupId 연결 테이블의 식별자에 해당하는 두 필드만 포함됩니다.

### Nms서비스 {#NmsService}

이 테이블은 **nms:service** 스키마.

Adobe Campaign에서 정보 서비스(주제) 구독을 만들고 관리할 수 있습니다. NmsService 테이블에는 수신자에게 구독할 수 있도록 제공하는 정보 서비스(주제)에 대한 정의가 저장됩니다(예: 뉴스레터).

서비스는 더 많은 정보를 순환하고 양식을 통해 구독 및 구독 취소를 쉽게 관리한다는 점을 제외하고 그룹(정적 수신자 그룹)과 유사한 엔티티입니다.

필드에는 sName 서비스의 내부 이름을 나타내는 고유한 색인이 있습니다. 서비스가 폴더에 연결되어 있습니다(키는 iFolderId임). 자세한 내용은 [XtkFolder](#XtkFolder)). 마지막으로 iType 필드에는 이 서비스의 게재 채널이 지정됩니다(이메일 0, SMS 1, 전화 2, DM 3, 팩스 4).

### Nms구독 {#NmsSubscription}

이 테이블은 **nms:subscription** 스키마.

이를 통해 정보 서비스에 대한 수신자 구독을 관리할 수 있습니다.

### NmsSubHisto {#NmsSubHisto}

이 테이블은 **nms:subHisto** 스키마.

웹 양식이나 애플리케이션 인터페이스를 사용하여 구독을 관리하는 경우 모든 구독 및 구독 취소가 NmsSubHisto 표에 기록됩니다. iAction 필드는 tsDate 필드에 저장된 날짜에 수행되는 작업 (구독 취소의 경우 0, 구독의 경우 1)을 지정합니다.

### NmsDelivery {#NmsDelivery}

이 테이블은 **nms:delivery** 스키마.

이 테이블의 각 레코드는 **게재 작업** 또는 **게재 템플릿**. 여기에는 게재 수행에 필요한 모든 매개 변수(대상, 콘텐츠 등)가 포함됩니다. 게재(브로드캐스트) 로그(NmsBroadLog) 및 관련 추적 URL(NmsTrackingUrl)은 분석 단계 중에 만들어집니다(이 두 테이블에 대한 자세한 내용은 아래 참조).

sInternalName 게재 또는 시나리오의 내부 이름을 나타내는 고유 인덱스가 필드에 있습니다. 게재가 실행 폴더에 연결되어 있습니다(외래 키는 iFolderProcessId임). 자세한 내용은 [XtkFolder](#XtkFolder)).

### XtkFolder {#XtkFolder}

포함 사항 **트리의 모든 폴더** 다음에서 표시: **탐색** 콘솔의 탭.

폴더는 유형화됩니다. sModel 필드의 값은 폴더에 포함될 수 있는 데이터 유형을 지정합니다. 또한 이 필드를 사용하면 클라이언트 콘솔에서 해당 양식을 사용하여 데이터를 올바르게 표시할 수 있습니다. 이 필드에 사용할 수 있는 값은 navTree에 정의되어 있습니다.

트리는 iParentId 및 iChildCount 필드에서 관리합니다. sFullName 필드는 트리에 있는 폴더의 전체 경로를 제공합니다. 마지막으로, 필드에 sName 폴더의 내부 이름을 나타내는 고유한 색인이 있습니다.

## 게재 및 추적 {#delivery-and-tracking}

이 테이블 집합은 **게재** 모듈을 사용하여 메시지를 보낼 때 발생하는 게재 및 최종 문제를 모니터링할 수 있습니다. 자세한 내용은 [게재 모니터링](../../delivery/using/about-delivery-monitoring.md). 추적에 대한 자세한 내용은 [메시지 추적](../../delivery/using/about-message-tracking.md).

![](assets/data-model_delivery.png)

**NmsBroadLogMsg**: 이 테이블은 **nms:broadLogMsg** 스키마. 게재 로그 테이블의 확장입니다.

## 캠페인 관리 {#campaign-management}

이 테이블 집합은 **마케팅 캠페인** 모듈 을 사용하여 커뮤니케이션 및 마케팅 캠페인을 정의, 최적화, 실행 및 분석할 수 있습니다. 자세한 내용은 [마케팅 캠페인 기본 정보](../../campaign/using/designing-marketing-campaigns.md).

![](assets/data-model_campaign.png)

* **NmsOperation**: 이 테이블은 **nms:operation** 스키마. 여기에는 마케팅 캠페인의 데이터가 포함되어 있습니다.
* **NmsDeliveryOutline**: 이 테이블은 **nms:deliveryOutline** 스키마. 여기에는 게재의 확장된 속성(게재 개요)이 포함됩니다.
* **NmsDlvOutlineItem**: 이 테이블은 **nms:dlvOutlineItem** 스키마. 여기에는 게재 개요의 문서가 포함되어 있습니다.
* **NmsDeliveryCustomization**: 이 테이블은 **nms:deliveryCustomization** 스키마. 여기에는 게재의 개인화 필드가 포함됩니다.
* **NmsBudget**: 이 테이블은 **nms:budget** 스키마. 여기에는 캠페인, 계획, 프로그램, 작업 및/또는 게재에 대한 예산 데이터가 포함됩니다.
* **NmsDocument**: 이 테이블은 **nms:document** 스키마. 여기에는 캠페인의 마케팅 문서가 파일(이미지, Excel 또는 Word 파일 등) 형태로 포함되어 있습니다.
* **XtkWorkflow**: 이 테이블은 **xtk:workflow** 스키마. 여기에는 캠페인 타깃팅이 포함되어 있습니다.
* **NmsTask**: 이 테이블은 **nms:task** 스키마. 여기에는 마케팅 작업의 정의가 포함되어 있습니다.
* **NmsAsset**: 이 테이블은 **nms:asset** 스키마. 여기에는 마케팅 리소스의 정의가 포함되어 있습니다.

## 커뮤니케이션 일관성 {#communication-consistency}

이 테이블 집합은 **Campaign 최적화** 모듈: 게재 전송을 제어, 필터링 및 모니터링할 수 있습니다. 자세한 내용은 [캠페인 유형화 기본 정보](../../campaign-opt/using/about-campaign-typologies.md).

![](assets/data-model_typology.png)

* **NmsTypologyRule**: 이 테이블은 **nms:typologyRule** 스키마. 여기에는 유형화에 따라 게재에 적용되는 규칙이 포함됩니다.
* **Nms 유형화**: 이 테이블은 **nms:유형화** 스키마. 여기에는 유형화와 일치하는 게재에 적용할 규칙 세트가 포함되어 있습니다.
* **NmsTypologyRuleRel**: 이 테이블은 **nms:typologyRuleRel** 스키마. 여기에는 유형화와 해당 규칙 간의 관계가 포함되어 있습니다.
* **Nms볼륨 라인**: 이 테이블은 **nms:volumeLine** 스키마. 여기에는 능력 규칙의 가용성 라인 세트가 포함됩니다.
* **NmsVolumeSupplied**: 이 테이블은 **nms:volumeSumested** 스키마. 여기에는 능력 규칙의 모든 소비 라인이 포함됩니다.

## 응답 관리 {#response-management}

이 테이블 집합은 **반응 관리자** 모듈 을 사용하여 마케팅 캠페인의 성공 및 수익성을 측정하거나 모든 커뮤니케이션 채널에 대한 제안을 제공할 수 있습니다. 자세한 내용은 [응답 관리자 기본 정보](../../response/using/about-response-manager.md).

![](assets/data-model_response.png)

### NmsRemaHypothesis {#NmsRemaHypothesis}

이 테이블은 다음과 일치합니다. **nms:remaHypothesis** 스키마. 여기에는 측정 가설에 대한 정의가 포함되어 있다.

이 표에는 다음과 같은 XML에 저장된 중요한 정보가 포함되어 있습니다.

**실행 컨텍스트(XML에 저장된 정보)**

실행 컨텍스트는 측정 계산에 고려할 테이블 및 필드를 채웁니다. 즉,
* nms:remaMatchRcp 반응 로그 저장 스키마.
* 트랜잭션 테이블 스키마(예: 구매).
* 가설 조건의 시작 테이블을 정의할 수 있는 쿼리 스키마.
* 쿼리 스키마를 기반으로 개인을 식별할 수 있는 개인 링크.
* 트랜잭션 날짜. 이 필드는 필수는 아니지만 이 필드를 사용하여 계산 둘레를 제한하는 것이 좋습니다.
* 거래 금액: 수익 지표를 자동으로 계산하기 위한 선택적 필드입니다.

**가설 경계(XML에 저장된 정보)**

가설 경계는 쿼리 스키마 테이블을 기반으로 가설을 필터링하는 방식으로 구성됩니다.

**가설 오버로드 스크립트(XML에 저장된 정보)**

가설 오버로드 스크립트는 실행 중에 가설 콘텐츠를 오버로드할 수 있는 JavaScript 코드입니다.

**측정 지표**

다음 지표는 가설 실행 중에 자동으로 업데이트됩니다.

* 반응 수: **iTransaction**. 반응 로그 테이블의 라인 수.
* 연락 횟수: **iContactReactified**. 가설에 포함된 고유 타겟팅된 연락처 수.
* 컨트롤 그룹 수: **iProofReactified**. 가설에 포함된 타깃팅된 컨트롤 그룹 연락처의 고유 수입니다.
* 연락한 응답률: **dContactReactedRate**. 가설에 있는 타겟팅된 연락처의 응답률입니다.
* 컨트롤 그룹의 응답률: **dProofReactedRate**. 가설 컨트롤 그룹의 응답률입니다.
* 연락한 인구의 총 수익: **dContactReactedTotalAmount**. 가설에 있는 타겟팅된 연락처의 총 매출액.
* 컨트롤 그룹의 평균 수익: **dContactReactedAvgAmount**. 가설에 있는 타겟팅된 컨트롤 그룹 연락처의 평균 매출액.
* 컨트롤 그룹의 총 수익: **dProofReactedTotalAmount**. 가설 컨트롤 그룹의 총 수익.
* 컨트롤 그룹의 평균 수익: **dProofReactedAvgAmount**. 가설 컨트롤 그룹의 평균 매출입니다.
* 연락처당 총 이익: **dContactReactedTotalMargin**. 가설에서 타겟팅된 연락처당 총 이익.
* 연락처당 평균 이익: **dContactReactedAvgMargin**. 가설에 타겟팅된 연락처당 평균 이익.
* 컨트롤 그룹의 총 이익: **dProofReactedTotalMargin**. 가설에 타겟팅된 컨트롤 그룹의 총 이익.
* 컨트롤 그룹의 평균 이익: **dProofReactedAvgMargin**. 가설에 타겟팅된 통제집단의 평균 이익.
* 추가 수익: **dAdditionalAmount**. (연락한 평균 수익 - 컨트롤 그룹의 평균 수익) * 연락한 수.
* 추가 이익: **dAdditionalMargin**. (연락한 평균 이익 - 컨트롤 그룹의 평균 이익) / 연락한 수.
* 연락처당 평균 비용(SQL 표현식). 게재 비용 계산 / 연락 수.
* ROI(SQL 표현식). 게재 비용 계산 / 연락한 총 이익.
* 유효 ROI(SQL 표현식). 계산된 게재 비용 / 추가 이익.
* 중요도: **유의성** (SQL 표현식). 캠페인의 중요도에 따라 0~3 사이의 값을 포함합니다.

### NmsRemaMatchRcp {#NmsRemaMatchRcp}

이 테이블은 **nms:remaMatchRcp** 스키마.

주어진 가설에 대한 개인의 반응을 나타내는 기록을 포함하고 있다. 이러한 레코드는 가설 실행 중에 생성되었습니다.

## 시뮬레이션 및 게재 {#simulation-and-delivery}

이 테이블 집합은 **시뮬레이션** 모듈 : 수신자에게 제안을 보내기 전에 카테고리 또는 환경에 속한 오퍼의 배포를 테스트할 수 있습니다. 자세한 내용은 [오퍼 시뮬레이션 기본 정보](../../interaction/using/about-offers-simulation.md).

![](assets/data-model_simulation.png)

* **NmsSimulation**: 이 테이블은 **nms:simulation** 스키마. 주어진 모집단의 게재 또는 오퍼 세트에 대한 시뮬레이션을 나타냅니다.
* **NmsDlvSimulationRel**: 이 테이블은 **nms:dlvSimulationRel** 스키마. 여기에는 시뮬레이션에서 고려되는 게재 목록이 포함되어 있습니다. 시뮬레이션의 범위는 XML로 저장됩니다.
* **NmsOfferSimulationRel**: 이 테이블은 **nms:offerSimulationRel** 스키마. 시뮬레이션을 오퍼와 연결할 수 있습니다.

## 상호 작용 모듈 {#interaction-module}

이 테이블 집합은 **상호 작용** 모듈을 사용하면 지정된 연락처와 상호 작용 중에 단일 또는 여러 개의 조정된 오퍼로 만들어 실시간으로 응답할 수 있습니다. 자세한 내용은 [상호 작용 및 오퍼 관리](../../interaction/using/interaction-and-offer-management.md).

* **NmsOffer**: 이 테이블은 **nms:offer** 스키마. 여기에는 각 마케팅 오퍼의 정의가 포함되어 있습니다.
* **NmsPropositionRcp**: 이 테이블은 **nms:propositionRcp** 스키마. 여기에는 각 개인에게 전송된 마케팅 제안의 크로스 채널 로그가 포함됩니다. 기록은 제안이 개인에게 준비되거나 효과적으로 만들어질 때 만들어진다.
* **NmsOfferSpace**: 이 테이블은 **nms:offerSpace** 스키마. 여기에는 제안되는 위치에 대한 정의가 포함되어 있습니다.
* **NmsOfferContext**: 이 테이블은 **nms:offerContext** 스키마. 가중치 계산 공식의 정의 뿐만 아니라 명제의 적용 가능성에 대한 추가적인 기준을 포함하고 있다.
* **NmsOfferView**: 이 테이블은 **nms:offerView**. 여기에는 오퍼 표현이 포함됩니다.
* **NmsOfferCategory**: 이 테이블은 **nms:offer범주**. 오퍼 카테고리를 포함합니다.
* **NmsOfferEnv**: 이 테이블은 **nms:offer환경**. 오퍼 환경이 포함되어 있습니다.

## 메시지 센터 모듈 {#message-center-module}

다음 테이블 집합은 **트랜잭션 메시지** (메시지 센터) 모듈 - 사용자에게 전송되고 정보 시스템에서 트리거된 이벤트에서 생성된 개별적이고 고유한 통신을 관리할 수 있습니다. 자세한 내용은 [트랜잭션 메시지 기본 정보](../../message-center/using/about-transactional-messaging.md).

### NmsRtEvent {#NmsRtEvent}

![](assets/data-model_message-center_rt.png)

이 테이블은 **nms:rtEvent** 스키마. 여기에는 실시간 이벤트에 대한 정의가 포함되어 있습니다.

### NmsBatchEvent {#NmsBatchEvent}

![](assets/data-model_message-center_batch.png)

이 테이블은 **nms:batchEvent** 스키마. 여기에는 일괄 처리에 의한 이벤트의 정의가 포함되어 있습니다.

<!--## Microsites Module {#microsites-module}

This set of tables is linked to the **Web applications** functionality, which allows to create and publish dynamic and interactive web applications with data from the database and content adapted to the rights of the connected user. For more on this, see [About web applications](../../web/using/about-web-applications.md).

![](assets/data-model_microsites.png)

* **NmsTrackingUrl**: This table matches the **nms:trackingUrl** schema.

* **NmsPurl**: This table matches the **nms:purl** schema.-->

## NMAC 모듈 {#nmac-module}

이 테이블 집합은 **모바일 앱 채널**: 앱을 통해 iOS 및 Android 터미널에 개인화된 알림을 전송할 수 있습니다. 자세한 내용은 [모바일 앱 채널 기본 정보](../../delivery/using/about-mobile-app-channel.md).

* **NmsMobileApp**: 이 테이블은 **nms:mobileApp** 스키마. 여기에는 Adobe Campaign에 정의된 모바일 애플리케이션이 포함됩니다.
* **NmsAppSubscription**: 이 테이블은 **nms:appSubscription** 스키마. 여기에는 하나 이상의 애플리케이션에 대한 구독자 정보가 포함됩니다.
* **NmsAppSubscriptionRcp**: 이 테이블은 **nms:appSubscriptionRcp** 스키마. 애플리케이션을 구독한 방문자를 수신자 테이블과 연결할 수 있습니다.
* **NmsExcludeLogAppSubRcp**: 이 테이블은 **nms:excludeLogAppSubRcp** 스키마.
* **NmsTrackingLogAppSubRcp**: 이 테이블은 **nms:trackingLogAppSubRcp** 스키마.
* **NmsBroadLogAppSubRcp**: 이 테이블은 **nms:broadLogAppSubRcp** 스키마.

## 소셜 마케팅 모듈 {#social-marketing-module}

이 테이블 집합은 **소셜 네트워크 관리** facebook 및 Twitter을 통해 고객 및 잠재 고객과 상호 작용할 수 있는 모듈입니다. 자세한 내용은 [소셜 마케팅 정보](../../social/using/about-social-marketing.md).

![](assets/data-model_social.png)

* **NmsVisitor**: 이 테이블은 **nms:visitor** 스키마. 여기에는 방문자에 대한 정보가 포함되어 있습니다.
* **NmsVisitorSub**: 이 테이블은 **nms:visitorSub** 스키마. 방문자가 가입한 서비스(Twitter 또는 Facebook)에 방문자를 연결할 수 있습니다.
* **NmsFriendShipRel**: 이 테이블은 **nms:friendshipRel** 스키마. facebook 서비스의 컨텍스트 내에서 방문자를 친구와 연결할 수 있습니다.
* **NmsVisitorInterestRel**: 이 테이블은 **nms:visitorInterestRel** 스키마. 방문자와 방문자의 관심사를 연결할 수 있습니다.
* **NmsInterest**: 이 테이블은 **nms:interest** 스키마. 여기에는 각 방문자의 관심 목록이 포함되어 있습니다.
