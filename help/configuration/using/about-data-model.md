---
product: campaign
title: Campaign Classic 데이터 모델 시작
description: Campaign 데이터 모델을 확장하거나 스키마를 편집하고 API를 사용하는 방법을 알아보십시오
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 655b5928-b005-442f-b026-2f1b0c1abb99
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '980'
ht-degree: 6%

---

# Campaign 데이터 모델 시작{#about-data-model}

![](../../assets/v7-only.svg)

Adobe Campaign 데이터베이스의 개념적 데이터 모델은 내장된 테이블과 상호 작용으로 구성됩니다. 이 페이지에는 기본 테이블 및 개념이 나열됩니다.

## 개요 {#data-model-overview}

Adobe Campaign은 함께 연결된 테이블이 들어 있는 관계형 데이터베이스를 사용합니다. Adobe Campaign 데이터 모델의 기본 구조는 다음과 같이 설명될 수 있습니다.

### 수신자 테이블 {#recipient-table}

데이터 모델은 기본적으로 수신자 테이블(**NmsRecipient**)인 기본 테이블을 사용합니다. 이 테이블을 사용하면 모든 마케팅 프로필을 저장할 수 있습니다.

수신자 테이블에 대한 자세한 내용은 [이 섹션](#default-recipient-table)을 참조하십시오.

### 게재 테이블 {#delivery-table}

데이터 모델에는 모든 마케팅 활동을 저장하도록 구성된 파트도 포함되어 있습니다. 일반적으로 배달 테이블(**NmsDelivery**)입니다. 이 테이블의 각 레코드는 게재 작업 또는 게재 템플릿을 나타냅니다. 여기에는 Target, 콘텐츠 등과 같은 게재를 수행하는 데 필요한 모든 매개 변수가 포함되어 있습니다.

### 로그 테이블 {#log-tables}

데이터 모델의 다른 부분에서 캠페인 실행과 연관된 모든 로그를 일시적으로 저장할 수 있습니다.

게재 로그는 모든 채널에서 수신자 또는 장치로 전송되는 모든 메시지입니다. 기본 게재 로그 테이블(**NmsBroadLog**)에는 모든 수신자에 대한 게재 로그가 포함되어 있습니다.
기본 추적 로그 테이블(**NmsTrackingLog**)은 모든 수신자에 대한 추적 로그를 저장합니다. 추적 로그는 이메일 열기 및 클릭과 같이 수신자의 반응을 나타냅니다. 각 반응은 추적 로그에 해당합니다.
게재 로그 및 추적 로그는 Adobe Campaign에 지정되며 수정할 수 있는 특정 기간 후에 삭제됩니다. 따라서 정기적으로 로그를 내보내는 것이 좋습니다.

### 기술 테이블 {#technical-tables}

마지막으로, 데이터 모델의 일부는 연산자 및 사용자 권한(**NmsGroup**), 폴더(**XtkFolder**)를 포함하여 응용 프로그램 프로세스에 사용되는 기술 데이터에 포함되어 있습니다.

## 기본 제공 수신자 테이블 사용 {#default-recipient-table}

Adobe Campaign의 기본 제공 수신자 테이블은 데이터 모델을 구축하는 데 적합한 시작점을 제공합니다. 미리 정의된 필드 및 테이블 링크를 많이 포함하며 쉽게 확장할 수 있습니다. 이 기능은 간단한 수신자 중심 데이터 모델에 적합하므로 주로 수신자를 타겟팅하는 경우에 특히 유용합니다.

기본 제공 수신자 테이블을 사용하면 다음과 같은 이점이 있습니다.

* 구독, 시드 목록 등과 같은 기능을 기본으로 사용하여 작업하는 방법
* 수신자 중심 데이터 모델을 마케팅 데이터베이스에 제공합니다.
* 더욱 신속한 구현.
* 지원 및 파트너의 간편한 유지 관리

하지만 수신자 테이블을 확장할 수는 있지만 테이블의 필드나 링크 수를 줄일 수는 없습니다.

>[!IMPORTANT]
>
>기본 제공 모듈에서 오류가 발생할 수 있으므로 수신자 테이블에서 필드를 삭제하지 않는 것이 좋습니다(없는 경우에도).

또한 수신자 테이블은 제품의 일부이므로 제품과 연관된 양식은 모두 제품이 변경될 때 발전합니다. 따라서 업그레이드 시 모든 확장이 계속 유효한지 확인하려면 추가 유지 관리가 필요합니다.

## 데이터 모델 확장 {#extending-data-model}

Adobe Campaign을 시작할 때 기본 데이터 모델을 평가하여 마케팅 데이터를 저장하는 데 가장 적합한 테이블을 확인해야 합니다.

해당하는 경우 [이 섹션](#default-recipient-table)에 설명된 것과 같이 기본적으로 제공되는 필드와 함께 기본 수신자 테이블을 사용할 수 있습니다.

필요한 경우 두 가지 메커니즘으로 확장할 수 있습니다.

* 기존 테이블을 새 필드로 확장합니다. 예를 들어 수신자 테이블에 새 &quot;충성도&quot; 필드를 추가할 수 있습니다.
* 데이터베이스의 각 프로필에서 수행한 모든 구매를 나열하는 &quot;구매&quot; 테이블 등의 새 테이블을 만들고 이를 수신자 테이블에 연결합니다.

개념 데이터 모델을 확장하도록 확장 스키마를 구성하는 방법에 대한 자세한 내용은 [스키마 에디션 정보](../../configuration/using/about-schema-edition.md)를 참조하십시오.

>[!IMPORTANT]
>
>데이터 모델 확장은 고급 사용자를 위해 예약되어 있습니다.

## 사용자 지정 수신자 테이블 사용 {#custom-recipient-table}

Adobe Campaign 데이터 모델을 디자인할 때 [즉시 사용 가능한 수신자 테이블](#default-recipient-table)을 사용하거나 [사용자 지정 수신자 테이블](../../configuration/using/about-custom-recipient-table.md) 테이블을 만들어 마케팅 프로필을 저장할 수 있습니다.

실제로 데이터 모델이 수신자 중심 구조에 맞지 않는 경우 Adobe Campaign 내에서 다른 테이블을 타겟팅 차원으로 설정할 수 있습니다. 예를 들어 단순히 수신자를 타겟팅하지 않고 가구, 계정(예: 휴대폰) 및 회사/사이트를 타겟팅해야 하는 경우에 해당될 수 있습니다.

>[!NOTE]
>
>이 경우 새 [대상 매핑](../../configuration/using/target-mapping.md)을 만들어야 합니다.

사용자 지정 수신자 테이블을 사용할 때 필요한 모든 원칙과 단계는 [이 섹션](../../configuration/using/about-custom-recipient-table.md)에 자세히 설명되어 있습니다.

사용자 지정 수신자 테이블을 사용하면 다음과 같은 이점이 있습니다.

* **유연한 데이터 모델**  - 수신자 테이블 필드가 대부분 필요하지 않거나 데이터 모델이 수신자 중심적이지 않은 경우 바로 사용할 수 있는 수신자 테이블은 무용지물입니다.

* **확장성**  - 큰 볼륨에는 효율적인 설계를 위해 필드가 적은 간소화된 테이블이 필요합니다. 즉시 사용 가능한 수신자 테이블에는 불필요한 필드가 너무 많아 성능에 영향을 줄 수 있고 효율성이 저하될 수 있습니다.

* **데이터 위치**  - 데이터가 외부 기존 마케팅 데이터베이스에 있는 경우 기본 제공 수신자 테이블을 사용하기 위해 너무 많은 노력이 필요할 수 있습니다. 기존 구조를 바탕으로 새로운 구조를 만드는 것이 더 쉽습니다.

* **쉬운 마이그레이션**  - 업그레이드 시 모든 확장이 계속 유효한지 확인하려면 유지 관리가 필요하지 않습니다.

>[!IMPORTANT]
>
>사용자 지정 수신자 테이블 사용은 고급 사용자를 위해 예약되며 일부 제한 사항이 적용됩니다. 자세한 내용은 [이 섹션](../../configuration/using/about-custom-recipient-table.md)을 참조하십시오.

## 관련 항목

다음 섹션에서 Campaign 데이터 모델에 대해 자세히 알아보십시오.

* **기본 테이블에 대한 설명**  - 기본 Campaign Classic 데이터 모델 설명에 대한 자세한 내용은  [이 섹션](../../configuration/using/data-model-description.md)을 참조하십시오.

* **각 테이블에 대한 전체 설명**  - 각 테이블의 전체 설명에 액세스하려면  **[!UICONTROL Admin > Configuration > Data schemas]**&#x200B;로 이동하여 목록에서 리소스를 선택한 다음 탭을  **[!UICONTROL Documentation]** 클릭합니다.

   ![](assets/data-model_documentation-tab.png)


* **Campaign 스키마**  - 애플리케이션에 포함된 데이터의 물리적 및 논리적 구조는 XML에 설명되어 있습니다. 스키마라고 하는 Adobe Campaign에 특정된 문법을 따릅니다. Adobe Campaign 스키마에 대한 자세한 내용은 [이 섹션을 참조하십시오](../../configuration/using/about-schema-reference.md).

* **데이터 모델 모범 사례**  -  [이 섹션](../../configuration/using/data-model-best-practices.md#data-model-architecture)에서 Campaign 데이터 모델 아키텍처 및 관련 모범 사례를 알아봅니다.
