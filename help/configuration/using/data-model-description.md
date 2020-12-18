---
solution: Campaign Classic
product: campaign
title: Adobe Campaign Classic 데이터 모델 설명
description: 이 문서에서는 Adobe Campaign Classic 데이터 모델에 대해 설명합니다.
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 6d5dbc16ed6c6e5a2e62ceb522e2ccd64b142825
workflow-type: tm+mt
source-wordcount: '2375'
ht-degree: 1%

---


# 캠페인 데이터 모델 설명{#data-model-description}

Adobe Campaign은 사전 정의된 데이터 모델을 제공합니다. 이 섹션에서는 Adobe Campaign 데이터 모델의 내장 테이블과 상호 작용에 대한 세부 사항을 제공합니다.

각 테이블의 설명에 액세스하려면 **[!UICONTROL Admin > Configuration > Data schemas]**&#x200B;으로 이동하여 목록에서 리소스를 선택하고 **[!UICONTROL Documentation]** 탭을 클릭합니다.

![](assets/data-model_documentation-tab.png)

>[!NOTE]
>
>애플리케이션에 포함된 데이터의 물리적 및 논리적 구조는 XML에 설명되어 있습니다. 스키마라고 하는 Adobe Campaign에 특정된 문법을 따릅니다. Adobe Campaign 스키마에 대한 자세한 내용은 [이 섹션](../../configuration/using/about-schema-reference.md)을 읽어 보십시오.

## 기본 테이블 {#description-main-tables} 설명

Adobe Campaign은 서로 연결된 테이블을 포함하는 관계형 데이터베이스를 사용합니다.

다음 다이어그램은 Adobe Campaign 데이터 모델의 기본 비즈니스 테이블 간 연결과 각 필드에 대한 기본 필드를 보여줍니다.

<!--![](assets/data-model_diagram.png)-->

![](assets/data-model_simplified-diagram.png)

사전 정의된 Adobe Campaign 데이터 모델에는 아래에 나열된 기본 테이블이 포함되어 있습니다.

### NmsRecipient {#NmsRecipient}

이 표는 **nms:recipient** 스키마와 일치합니다.

배달&#x200B;**의**&#x200B;수신자에게 사용되는 기본 테이블입니다. 따라서 다양한 채널을 통해 배달하는 데 필요한 정보가 포함됩니다.

* 이메일:이메일 주소입니다.
* iEmailFormat:이메일에 대한 기본 형식(텍스트의 경우 1, HTML의 경우 2, 정의되지 않은 경우 0)입니다.
* sAddress1, sAddress2, sAddress3, sAddress4, sZipCode, sCity는 우편 주소를 작성하는 데 사용됩니다(1997년 5월 XPZ 10-011 AFNOR 표준과 함께 사용).
* sPhone, sMobilePhone, sFax에는 각각 전화, 휴대폰 및 팩스 번호가 들어 있습니다.
* iBlackList는 프로파일에 사용되는 기본 옵트아웃 플래그입니다(1은 &quot;가입되지 않음&quot;, 0은 그렇지 않음).

iFolderId 필드는 수신자를 해당 실행 폴더로 연결하는 외래 키입니다. 자세한 내용은 [XtkFolder](#XtkFolder)를 참조하십시오.

sCountryCode 필드는 수신자와 관련된 국가의 3166-1 Alpha 2 ISO 코드(2자)입니다. 이 필드는 국가 레이블 및 기타 국가 코드 데이터를 포함하는 국가 참조 테이블(NmsCountry)의 외래 키입니다. 국가가 채워지지 않으면 &#39;XX&#39; 값이 저장됩니다(그리고 이 값은 0의 ID 레코드 대신 사용됩니다).

수신자 테이블에 대한 자세한 내용은 [이 섹션](../../configuration/using/about-data-model.md#default-recipient-table)을 참조하십시오.

### NmsGroup {#NmsGroup}

이 표는 **nms:group** 스키마와 일치합니다.

이 기능을 사용하면 **수신자의 동적 그룹을 만들 수 있습니다**. 받는 사람과 그룹 간에는 다대다 관계가 있습니다. 예를 들어 한 수신자는 여러 그룹에 속할 수 있고 한 그룹은 여러 수신자를 포함할 수 있습니다. 그룹은 가져오기 또는 배달 타깃팅을 통해 수동으로 만들 수 있습니다. 그룹은 종종 배달 타겟으로 사용됩니다. 필드에 sName 그룹의 내부 이름을 나타내는 고유한 인덱스가 있습니다. 그룹이 폴더에 연결되어 있습니다(키는 iFolderId입니다.) 자세한 내용은 [XtkFolder](#XtkFolder))를 참조하십시오.

### NmsRcpGrpRel {#NmsRcpGrpRel}

NmsRcpGrpRel 관계 표에는 iRecipientId 및 iGroupId 연결 테이블의 식별자에 해당하는 두 개의 필드만 포함됩니다.

### NmsService {#NmsService}

이 표는 **nms:service** 스키마와 일치합니다.

Adobe Campaign에서 정보 서비스(항목) 가입을 만들고 관리할 수 있습니다. NmsService 테이블에는 수신자에게 가입하도록 제공하는 정보 서비스(주제)의 정의(예: 뉴스레터)가 저장됩니다.

서비스는 더 많은 정보를 배포하고 양식을 통해 구독 및 가입을 간편하게 관리할 수 있다는 점을 제외하면 그룹(정적 수신자 그룹)과 유사한 개체입니다.

sName 서비스의 내부 이름을 나타내는 고유한 인덱스가 필드에 있습니다. 서비스가 폴더에 연결되어 있습니다(키는 iFolderId입니다. 자세한 내용은 [XtkFolder](#XtkFolder))를 참조하십시오. 마지막으로 iType 필드는 이 서비스의 배달 채널(이메일의 경우 0, SMS의 경우 1, 전화의 경우 2, DM의 경우 3, 팩스의 경우 4)을 지정합니다.

### NmsSubscription {#NmsSubscription}

이 표는 **nms:subscription** 스키마와 일치합니다.

정보 서비스에 대한 수신자 가입을 관리할 수 있습니다.

### NmsSubHisto {#NmsSubHisto}

이 표는 **nms:subHisto** 스키마와 일치합니다.

구독이 웹 양식 또는 응용 프로그램의 인터페이스를 사용하여 관리되는 경우 모든 구독 및 구독 취소는 NmsSubHisto 테이블에 저장됩니다. iAction 필드는 tsDate 필드에 저장된 날짜에 수행되는 작업(가입 해제는 0, 가입은 1)을 지정합니다.

### NmsDelivery {#NmsDelivery}

이 표는 **nms:delivery** 스키마와 일치합니다.

이 테이블의 각 레코드는 **배달 작업** 또는 **배달 템플릿**&#x200B;을 나타냅니다. 여기에는 배달 수행에 필요한 모든 매개 변수(대상, 컨텐츠 등)가 포함되어 있습니다. 분석 단계 동안 배달(브로드캐스트) 로그(NmsBroadLog) 및 관련 추적 URL(NmsTrackingUrl)이 만들어집니다(이 표 모두에 대한 자세한 내용은 아래 참조).

sInternalName 배달 또는 시나리오의 내부 이름을 나타내는 고유한 인덱스가 필드에 있습니다. 배달이 실행 폴더에 연결됩니다(외래 키는 iFolderProcessId입니다.) 자세한 내용은 [XtkFolder](#XtkFolder))를 참조하십시오.

### XtkFolder {#XtkFolder}

여기에는 **트리의 모든 폴더**&#x200B;이 콘솔의 **내비게이션** 탭에 표시됩니다.

폴더 유형은 다음과 같습니다.sModel 필드의 값은 폴더에 포함할 수 있는 데이터 유형을 지정합니다. 또한 이 필드를 사용하면 클라이언트 콘솔에서 해당 양식을 사용하여 데이터를 올바르게 표시할 수 있습니다. 이 필드의 가능한 값은 navTree에 정의됩니다.

트리는 iParentId 및 iChildCount 필드에 의해 관리됩니다. sFullName 필드는 트리에 있는 폴더의 전체 경로를 제공합니다. 마지막으로, 필드에 sName 폴더의 내부 이름을 나타내는 고유한 인덱스가 있습니다.

## 배달 및 추적 {#delivery-and-tracking}

이 테이블 집합은 **배달** 모듈에 연결되어 있으므로 메시지가 전송될 때 발생하는 전달 및 최종 문제를 모니터링할 수 있습니다. 자세한 내용은 [배달 모니터링](../../delivery/using/about-delivery-monitoring.md)을 참조하십시오. 추적에 대한 자세한 내용은 [추적 메시지](../../delivery/using/about-message-tracking.md)를 참조하십시오.

![](assets/data-model_delivery.png)

**NmsBroadLogMsg**:이 테이블은 nms: **broadLogMsgschema** 와 일치합니다. 배달 로그 테이블의 확장입니다.

## 캠페인 관리 {#campaign-management}

이 테이블 세트는 통신 및 마케팅 캠페인을 정의, 최적화, 실행 및 분석할 수 있는 **마케팅 캠페인** 모듈과 연결됩니다. 자세한 내용은 [마케팅 캠페인 정보](../../campaign/using/designing-marketing-campaigns.md)를 참조하십시오.

![](assets/data-model_campaign.png)

* **NmsOperation**:이 테이블은 nms: **operationschema** 와 일치합니다. 여기에는 마케팅 캠페인의 데이터가 포함됩니다.
* **NmsDeliveryOutline**:이 테이블은 nms: **deliveryOutlineschema** 와 일치합니다. 배달의 확장 속성(배달 개요)이 포함되어 있습니다.
* **NmsDlvOutlineItem**:이 테이블은  **nms:dlvOutlineItemschema** 와 일치합니다. 배달 개요의 아티클이 포함되어 있습니다.
* **NmsDeliveryCustomization**:이 테이블은 nms: **deliveryCustomizationschema** 와 일치합니다. 게재의 개인화 필드를 포함합니다.
* **Nms예산**:이 테이블은 nms: **budgetischema와** 일치합니다. 여기에는 캠페인, 계획, 프로그램, 작업 및/또는 게재에 대한 예산 데이터가 포함됩니다.
* **NmsDocument**:이 테이블은 nms: **documentschema와** 일치합니다. 캠페인 마케팅 문서를 파일 형식(이미지, excel 또는 word 파일 등)으로 포함합니다.
* **XtkWorkflow**:이 테이블은 xtk: **workflowschema와** 일치합니다. 여기에는 캠페인 타깃팅이 포함됩니다.
* **NmsTask**:이 테이블은 nms: **taskschema와** 일치합니다. 여기에는 마케팅 작업의 정의가 포함됩니다.
* **NmsAsset**:이 테이블은 nms: **assetschema** 와 일치합니다. 마케팅 리소스의 정의를 포함합니다.

## 통신 일관성 {#communication-consistency}

이 테이블 세트는 배달 전송을 제어, 필터링 및 모니터링할 수 있는 **캠페인 최적화** 모듈에 연결됩니다. 이에 대한 자세한 내용은 [캠페인 유형 지정 정보](../../campaign/using/about-campaign-typologies.md)를 참조하십시오.

![](assets/data-model_typology.png)

* **NmsTypicalRule**:이 테이블은 nms: **Typelics** Ruleschema와 일치합니다. 유형 분류에 따라 배달에 적용되는 규칙을 포함합니다.
* **NmsTypical**:이 테이블은 nms: **Typolgyschema** 와 일치합니다. 여기에는 유형 유형과 일치하는 게재에 적용할 규칙 세트가 포함되어 있습니다.
* **NmsTypesologyRuleRel**:이 테이블은 nms: **TypolicsRuleReschema** 와 일치합니다. 그것은 유형 유형과 규칙 사이의 관계를 포함한다.
* **NmsVolumeLine**:이 테이블은 nms: **volumeLineschema와** 일치합니다. 용량 규칙의 가용성 라인 세트가 포함되어 있습니다.
* **NmsVolumeUsed**:이 테이블은 nms: **volumeConsomedschema** 와 일치합니다. 용량 규칙의 모든 소비 라인을 포함합니다.

## 응답 관리 {#response-management}

이 테이블 세트는 마케팅 캠페인의 성공과 수익성을 측정하거나 모든 통신 채널에 대한 제안을 제공할 수 있는 **응답 관리자** 모듈과 연결됩니다. 자세한 내용은 [응답 관리자 ](../../campaign/using/about-response-manager.md)를 참조하십시오.

![](assets/data-model_response.png)

### NmsRema가설 {#NmsRemaHypothesis}

이 표는 **nms:rema가설** 스키마와 일치합니다. 측정 가설의 정의가 포함되어 있습니다.

이 표에는 XML에 저장되는 다음과 같은 중요한 정보가 포함되어 있습니다.

**실행 컨텍스트(XML에 저장된 정보)**

실행 컨텍스트는 측정 계산을 위해 고려할 테이블과 필드를 채웁니다. 즉,
* nms:remaMatchRcp 반응 로그 저장소 스키마입니다.
* 트랜잭션 테이블 스키마(예: 구매).
* 가설 조건의 시작 테이블을 정의할 수 있는 쿼리 스키마.
* 쿼리 스키마를 기반으로 개인을 식별할 수 있는 개인 링크입니다.
* 거래 일자. 이 필드는 필수는 아니지만 계산 경계를 제한하는 데 사용하는 것이 좋습니다.
* 거래 금액:매출 지표를 자동으로 계산하는 선택적 필드입니다.

**가설 경계(XML에 저장된 정보)**

가설 경계는 쿼리 스키마 테이블을 기반으로 가설을 필터링하는 데 포함됩니다.

**가설 오버로드 스크립트(XML에 저장된 정보)**

가설 오버로드 스크립트는 실행하는 동안 가설 컨텐츠를 오버로드하도록 하는 JavaScript 코드입니다.

**측정 지표**

가설을 실행하는 동안 다음 표시기가 자동으로 업데이트됩니다.

* 반응 수:**iTransaction**. 응답 로그 테이블의 줄 수입니다.
* 연락 횟수:**iContactResponcaced**. 가설을 통해 타깃팅된 연락처의 수를 구별합니다.
* 제어 그룹 수:**iProofResponsephed**. 가설을 통해 타깃팅된 제어 그룹 연락처가 구분되는 개수입니다.
* 연결된 응답률:**dContactResponcacedRate**. 가설을 통해 타깃팅된 연락처의 응답률입니다.
* 제어 그룹의 응답률:**dProofResponsiveRate**. 가설 제어 그룹의 응답률입니다.
* 연결된 인구의 총 매출액:**dContactResponcacedTotalAmount** 가설을 통해 타깃팅된 연락처의 총 매출액.
* 제어 그룹의 평균 매출:**dContactResponcacedAvgAmount** 가설을 통해 타깃팅된 제어 그룹 연락처의 평균 매출입니다.
* 제어 그룹의 총 매출:**dProofReaccessedTotalAmount** 가설 제어 그룹의 총 매출액.
* 제어 그룹의 평균 매출:**dProofResponsephedAvgAmount** 가설 제어 그룹의 평균 매출액.
* 연락처당 총 여백:**dContactResponcacedTotalMargin**. 가설을 대상으로 하는 접촉당 총 마진 수입니다.
* 연락처당 평균 마진:**dContactResponcacedAvgMargin**. 가설을 대상으로 하는 접촉당 평균 마진.
* 제어 그룹의 총 여백:**dProofReaccessedTotalMargin**. 가설을 대상으로 하는 제어 그룹의 전체 여백입니다.
* 제어 그룹의 평균 여백:**dProofResponsephedAvgMargin**. 가설을 대상으로 하는 제어 그룹의 평균 여백입니다.
* 추가 매출액:**AdditionalAmount** (접촉 평균 매출 - 제어 그룹의 평균 매출) * 접촉 수입니다.
* 추가 여백:**AdditionalMargin**. (접촉의 평균 여백 - 제어 그룹의 평균 여백)/접촉된 항목 수입니다.
* 연락처당 평균 비용(SQL 표현식). 배달의 계산된 비용/접촉 수입니다.
* ROI(SQL 표현식). 배달의 계산된 비용/총 접촉 마진.
* 효과적인 ROI(SQL 표현식) 배달의 계산된 비용/추가 마진.
* 중요도:**중요성**(SQL 표현식) 캠페인의 중요도에 따라 0부터 3까지의 값을 포함합니다.

### NmsRemaMatchRcp {#NmsRemaMatchRcp}

이 표는 **nms:remaMatchRcp** 스키마와 일치합니다.

이것은 주어진 가설에 대한 개인의 반응을 나타내는 기록을 포함합니다. 이러한 기록들은 가설 실행 중에 만들어졌다.

## 시뮬레이션 및 배달 {#simulation-and-delivery}

이 테이블 세트는 **시뮬레이션** 모듈에 연결되어 있으므로 수신자에게 제안을 보내기 전에 카테고리 또는 환경에 속하는 오퍼의 배포를 테스트할 수 있습니다. 자세한 내용은 [오퍼 시뮬레이션 정보](../../interaction/using/about-offers-simulation.md)를 참조하십시오.

![](assets/data-model_simulation.png)

* **NmsSimulation**:이 테이블은 nms: **simulationschema** 와 일치합니다. 주어진 모집단에서 전달 또는 오퍼의 세트에 대한 시뮬레이션을 나타냅니다.
* **NmsDlvSimulationRel**:이 테이블은  **nms:dlvSimulationReschema** 와 일치합니다. 시뮬레이션에서 고려된 배달 목록이 포함되어 있습니다. 시뮬레이션의 범위는 XML에 저장됩니다.
* **NmsOfferSimulationRel**:이 테이블은 nms: **offerSimulationReschema** 와 일치합니다. 오퍼와 시뮬레이션을 연결할 수 있습니다.

## 상호 작용 모듈 {#interaction-module}

이 테이블 집합은 **상호 작용** 모듈과 연결되어 있으므로 지정된 담당자와 상호 작용하는 동안 해당 테이블을 하나 또는 여러 개의 수정된 오퍼로 만들어 실시간으로 응답할 수 있습니다. 이에 대한 자세한 내용은 [상호 작용 및 오퍼 관리](../../interaction/using/interaction-and-offer-management.md)를 참조하십시오.

* **NmsOffer**:이 테이블은 nms: **offerschema와** 일치합니다. 여기에는 각 마케팅 오퍼의 정의가 포함됩니다.
* **NmsProvisionRcp**:이 테이블은 nms: **provisionRcpschema** 와 일치합니다. 여기에는 각 개인에게 전송된 마케팅 프로필의 크로스 채널 로그가 포함되어 있습니다. 기록은 제안을 준비하거나 효과적으로 개인에게 제출될 때 생성됩니다.
* **NmsOfferSpace**:이 테이블은 nms: **offerSpaceschema** 와 일치합니다. 여기에는 proposition이 작성되는 위치의 정의가 포함됩니다.
* **NmsOfferContext**:이 테이블은 nms: **offerContextschema** 와 일치합니다. 이것은 무게 계산 공식의 정의와 함께 제안의 적용 가능성에 대한 추가적인 기준을 포함합니다.
* **NmsOfferView**:이 테이블은 nms:offerView **와 일치합니다**. 여기에는 오퍼 표현이 포함되어 있습니다.
* **NmsOfferCategory**:이 테이블은 nms:offerCategory **와 일치합니다**. 여기에는 오퍼 카테고리가 포함됩니다.
* **NmsOfferEnv**:이 테이블은  **nms:offerEnv와 일치합니다**. 오퍼 환경이 포함되어 있습니다.

## 메시지 센터 모듈 {#message-center-module}

다음 표 집합은 사용자에게 전송되고 정보 시스템에서 트리거된 이벤트에서 생성된 개별 및 고유 통신을 관리할 수 있는 **트랜잭션 메시지**(메시지 센터) 모듈에 연결되어 있습니다. 자세한 내용은 [트랜잭션 메시지 정보](../../message-center/using/about-transactional-messaging.md)를 참조하십시오.

### NmsRtEvent {#NmsRtEvent}

![](assets/data-model_message-center_rt.png)

이 표는 **nms:rtEvent** 스키마와 일치합니다. 여기에는 실시간 이벤트의 정의가 포함되어 있습니다.

### NmsBatchEvent {#NmsBatchEvent}

![](assets/data-model_message-center_batch.png)

이 표는 **nms:batchEvent** 스키마와 일치합니다. 여기에는 일괄 처리별 이벤트 정의가 포함됩니다.

<!--## Microsites Module {#microsites-module}

This set of tables is linked to the **Web applications** functionality, which allows to create and publish dynamic and interactive web applications with data from the database and content adapted to the rights of the connected user. For more on this, see [About web applications](../../web/using/about-web-applications.md).

![](assets/data-model_microsites.png)

* **NmsTrackingUrl**: This table matches the **nms:trackingUrl** schema.

* **NmsPurl**: This table matches the **nms:purl** schema.-->

## NMAC 모듈 {#nmac-module}

이 표 세트는 앱을 통해 iOS 및 Android 터미널에 개인화된 알림을 보낼 수 있는 **모바일 앱 채널**&#x200B;에 연결되어 있습니다. 자세한 내용은 [모바일 앱 채널](../../delivery/using/about-mobile-app-channel.md)을 참조하십시오.

* **NmsMobileApp**:이 표는 nms: **mobileAppschema와** 일치합니다. 여기에는 Adobe Campaign에 정의된 모바일 애플리케이션이 포함되어 있습니다.
* **NmsAppSubscription**:이 표는 nms: **appSubscriptionschema** 와 일치합니다. 하나 이상의 응용 프로그램에 대한 구독자 정보가 포함되어 있습니다.
* **NmsAppSubscriptionRcp**:이 테이블은 nms: **appSubscriptionRcpschema** 와 일치합니다. 애플리케이션을 구독한 방문자를 수신자 테이블과 연결할 수 있습니다.
* **NmsExcludeLogAppSubRcp**:이 테이블은 nms: **excludeLogAppSubRcpschema** 와 일치합니다.
* **NmsTrackingLogAppSubRcp**:이 테이블은 nms: **trackingLogAppSubRcpschema** 와 일치합니다.
* **NmsBroadLogAppSubRcp**:이 테이블은 nms: **broadLogAppSubRcpschema** 와 일치합니다.

## 소셜 마케팅 모듈 {#social-marketing-module}

이 테이블 세트는 Facebook 및 Twitter를 통해 고객 및 잠재 고객과 상호 작용할 수 있는 **소셜 네트워크 관리** 모듈과 연결되어 있습니다. 자세한 내용은 [소셜 마케팅 정보](../../social/using/about-social-marketing.md)를 참조하십시오.

![](assets/data-model_social.png)

* **Nms방문자**:이 테이블은  **nms:visitorschema** 와 일치합니다. 방문자에 대한 정보가 포함되어 있습니다.
* **NmsVisitorSub**:이 테이블은 nms: **visitorSubschema와** 일치합니다. 방문자를 가입한 서비스(Twitter 또는 Facebook)에 연결할 수 있습니다.
* **NmsFriendShipRel**:이 테이블은 nms: **friendshipReschema와** 일치합니다. Facebook 서비스 컨텍스트 내에서 방문자를 친구와 연결할 수 있습니다.
* **NmsVisitorInterestRel**:이 테이블은 nms: **visitorInterestReschema** 와 일치합니다. 방문자와 이들의 관심사를 연결할 수 있습니다.
* **NmsInterest**:이 테이블은 nms: **interest 스키마** 와 일치합니다. 여기에는 각 방문자에 대한 관심 목록이 포함되어 있습니다.