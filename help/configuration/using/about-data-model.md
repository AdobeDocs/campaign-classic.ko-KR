---
solution: Campaign Classic
product: campaign
title: Campaign Classic 데이터 모델 시작하기
description: Campaign 데이터 모델을 확장하거나 스키마를 편집하고 API를 사용하는 방법을 알아보십시오
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 6%

---


# Campaign 데이터 모델 시작{#about-data-model}

Adobe Campaign 데이터베이스의 개념적 데이터 모델은 내장된 테이블과 상호 작용으로 구성됩니다. 이 페이지에는 기본 테이블과 개념이 나열됩니다.

## 개요 {#data-model-overview}

Adobe Campaign은 서로 연결된 테이블을 포함하는 관계형 데이터베이스에 의존합니다. Adobe Campaign 데이터 모델의 기본 구조는 다음과 같이 설명될 수 있습니다.

### 수신자 테이블 {#recipient-table}

데이터 모델은 기본적으로 받는 사람 테이블(NmsRecipient)인 기본 테이블을&#x200B;**사용합니다**. 이 표를 사용하면 모든 마케팅 프로필을 저장할 수 있습니다.

수신자 테이블에 대한 자세한 내용은 [이 섹션을 참조하십시오](#default-recipient-table).

### 배달 표 {#delivery-table}

또한 데이터 모델에는 모든 마케팅 활동을 저장하기 위한 전용 부품이 포함되어 있습니다. 일반적으로 배달 테이블(NmsDelivery **)입니다**. 이 테이블의 각 레코드는 배달 작업 또는 배달 템플릿을 나타냅니다. 여기에는 타겟, 컨텐츠 등과 같은 전달 수행에 필요한 모든 매개 변수가 포함되어 있습니다.

### 테이블 로그 {#log-tables}

데이터 모델의 다른 부분에서 캠페인 실행과 관련된 모든 로그를 일시적으로 저장할 수 있습니다.

배달 로그는 모든 채널에서 받는 사람 또는 장치로 전송되는 모든 메시지입니다. 기본 배달 로그 테이블(**NmsBroadLog**)에는 모든 받는 사람의 배달 로그가 포함되어 있습니다.
주 추적 로그 테이블(**NmsTrackingLog**)은 모든 받는 사람의 추적 로그를 저장합니다. 추적 로그는 이메일 열기 및 클릭 수와 같은 수신자의 반응을 나타냅니다. 각 반응은 추적 로그에 해당합니다.
배달 로그와 추적 로그는 특정 기간 후에 삭제되며, Adobe Campaign에 지정되어 수정될 수 있습니다. 따라서 로그를 정기적으로 내보내는 것이 좋습니다.

### 기술 표 {#technical-tables}

마지막으로, 데이터 모델의 일부는 연산자 및 사용자 권한(**NmsGroup**), 폴더(XtkFolder **)를 비롯하여 애플리케이션 프로세스에 사용되는 기술 데이터로**&#x200B;구성됩니다.

## 기본 수신자 테이블 사용 {#default-recipient-table}

Adobe Campaign의 바로 사용 가능한 수신자 테이블은 데이터 모델을 구축하기 위한 좋은 시작점을 제공합니다. 미리 정의된 필드 및 표 링크가 많이 있으며, 이를 손쉽게 확장할 수 있습니다. 이 기능은 간단한 수신자 중심의 데이터 모델에 적합하므로 수신자를 주로 타깃팅하는 경우에 특히 유용합니다.

표준 수신자 테이블을 사용하면 다음과 같은 이점이 있습니다.

* 구독, 시드 목록, 설문 조사, 소셜 등과 같은 기능을 사용하여 간편하게 작업할 수 있습니다.
* 수신자 중심의 데이터 모델을 마케팅 데이터베이스에 제공
* 더욱 빨라진 구현
* 지원 및 파트너의 간편한 유지 관리

그러나 테이블의 필드나 링크 수는 줄이지 않고 수신자 테이블을 확장할 수는 있습니다.

>[!IMPORTANT]
>
>기본 제공 모듈에서 오류가 발생할 수 있으므로 수신자 테이블에서 필드를 삭제하지 않는 것이 좋습니다(쓸모 없는 경우에도).

또한 수신자 테이블이 제품의 일부이므로 제품이 변경될 때 테이블과 관련 양식이 모두 진화합니다. 따라서 업그레이드 시 모든 익스텐션이 여전히 유효한지 확인하기 위해 추가 유지 관리가 필요합니다.

## 데이터 모델 확장 {#extending-data-model}

Adobe Campaign을 시작할 때 기본 데이터 모델을 평가하여 마케팅 데이터를 저장하는 데 가장 적합한 테이블을 확인해야 합니다.

관련 있는 경우, [이 섹션에 설명된 것과 같이 기본 수신자 테이블을 기본적으로 사용할 수 있습니다](#default-recipient-table).

필요한 경우 두 가지 메커니즘으로 확장할 수 있습니다.

* 새 필드를 사용하여 기존 테이블을 확장합니다. 예를 들어 새 &quot;충성도&quot; 필드를 수신자 테이블에 추가할 수 있습니다.
* 데이터베이스의 각 프로파일에서 모든 구매를 나열하는 &quot;구매&quot; 테이블과 같은 새 테이블을 만들고 이를 수신자 테이블에 연결합니다.

개념 데이터 모델을 확장하도록 확장 스키마를 구성하는 방법에 대한 자세한 내용은 스키마 버전 [정보를 참조하십시오](../../configuration/using/about-schema-edition.md).

>[!IMPORTANT]
>
>데이터 모델 확장은 고급 사용자를 위해 예약되어 있습니다.

## Using a custom recipient table {#custom-recipient-table}

Adobe Campaign 데이터 모델을 디자인할 때 [바로 사용할 수 있는 수신자 테이블을](#default-recipient-table)사용하거나 [사용자 지정 수신자 테이블](../../configuration/using/about-custom-recipient-table.md) 테이블을 만들어 마케팅 프로필을 저장할 수 있습니다.

실제로 데이터 모델이 수신자 중심 구조에 맞지 않으면 다른 테이블을 Adobe Campaign 내의 타깃팅 차원으로 설정할 수 있습니다. 예를 들어 단순히 수신자가 아닌 가계, 계정(예: 휴대폰) 및 회사/사이트를 대상으로 해야 하는 경우 이 문제가 관련이 있을 수 있습니다.

>[!NOTE]
>
>이 경우 새 [대상 매핑을 만들어야 합니다](../../configuration/using/target-mapping.md).

사용자 지정 수신자 테이블을 사용할 때 필요한 모든 원칙과 단계는 [이 섹션에 자세히 설명되어 있습니다](../../configuration/using/about-custom-recipient-table.md).

사용자 지정 수신자 테이블을 사용하면 다음과 같은 이점이 있습니다.

* **유연한 데이터 모델** - 수신자 테이블 필드 대부분이 필요하지 않거나 데이터 모델이 수신자 중심의 것이 아닌 경우 즉시 사용할 수 있는 수신자 테이블은 무용지물입니다.

* **확장성** - 용량이 큰 경우 효율적인 디자인을 위해 필드가 거의 없는 간소화된 테이블이 필요합니다. 곧바로 사용할 수 있는 수신자 테이블에는 불필요한 필드가 너무 많아 성능에 영향을 주고 효율성이 저하될 수 있습니다.

* **데이터 위치** - 데이터가 외부 기존 마케팅 데이터베이스에 있을 경우 즉시 사용 가능한 수신자 테이블을 사용하는 데 너무 많은 노력이 필요할 수 있습니다. 기존 구조를 바탕으로 새 건물을 만드는 작업이 훨씬 수월합니다.

* **간편한 마이그레이션** - 업그레이드 시 모든 익스텐션이 여전히 유효한지 확인하기 위해 유지 관리가 필요하지 않습니다.

>[!IMPORTANT]
>
>사용자 지정 수신자 테이블 사용은 고급 사용자를 위해 예약되어 있으며 일부 제한 사항이 적용됩니다. 자세한 내용은 [이 섹션](../../configuration/using/about-custom-recipient-table.md)을 참조하십시오.

## 관련 항목

다음 섹션에서 캠페인 데이터 모델에 대해 자세히 알아보십시오.

* **기본 테이블** 설명 - 기본 Campaign Classic 데이터 모델 설명에 대한 자세한 내용은 [이 섹션을 참조하십시오](../../configuration/using/data-model-description.md).

* **각 테이블에 대한 전체 설명** - 각 테이블에 대한 전체 설명에 액세스하려면 목록에서 리소스 **[!UICONTROL Admin > Configuration > Data schemas]**&#x200B;를 선택하고 **[!UICONTROL Documentation]** 탭을 클릭합니다.

   ![](assets/data-model_documentation-tab.png)


* **캠페인 스키마** - 응용 프로그램에 포함된 데이터의 물리적 및 논리적 구조는 XML에 설명되어 있습니다. 스키마라고 하는 Adobe Campaign에 특정된 문법을 따릅니다. For more on Adobe Campaign schemas, read out [this section](../../configuration/using/about-schema-reference.md).

* **데이터 모델 모범 사례** - 이 섹션에서 캠페인 데이터 모델 아키텍처 및 관련 모범 사례 [를 살펴볼 수 있습니다](../../configuration/using/data-model-best-practices.md#data-model-architecture).
