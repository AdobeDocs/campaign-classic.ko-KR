---
product: campaign
title: Campaign Classic 데이터 모델 시작
description: Campaign 데이터 모델을 확장하거나 스키마를 편집하고 API를 사용하는 방법을 알아보십시오.
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Data Model
exl-id: 655b5928-b005-442f-b026-2f1b0c1abb99
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '980'
ht-degree: 6%

---

# Campaign 데이터 모델 시작{#about-data-model}

Adobe Campaign 데이터베이스의 개념적 데이터 모델은 내장된 테이블과 상호 작용으로 구성됩니다. 이 페이지에는 기본 테이블과 개념이 나열되어 있습니다.

## 개요 {#data-model-overview}

Adobe Campaign은 함께 연결된 테이블이 포함된 관계형 데이터베이스를 사용합니다. Adobe Campaign 데이터 모델의 기본 구조는 다음과 같이 설명할 수 있다.

### 수신자 테이블 {#recipient-table}

데이터 모델은 기본적으로 수신자 테이블( )인 기본 테이블을 사용합니다.**NmsRecipient**). 이 표에서 모든 마케팅 프로필을 저장할 수 있습니다.

수신자 테이블에 대한 자세한 내용은 [이 섹션](#default-recipient-table).

### 게재 테이블 {#delivery-table}

데이터 모델에는 모든 마케팅 활동을 저장하는 데 필요한 부품도 포함되어 있습니다. 일반적으로 게재 테이블(**NmsDelivery**). 이 테이블의 각 레코드는 게재 작업 또는 게재 템플릿을 나타냅니다. 여기에는 target, 콘텐츠 등 게재 수행에 필요한 모든 매개 변수가 포함되어 있습니다.

### 로그 테이블 {#log-tables}

데이터 모델의 또 다른 부분에서는 캠페인 실행과 관련된 모든 로그를 일시적으로 저장할 수 있습니다.

게재 로그는 모든 채널에서 수신자 또는 장치에 전송되는 모든 메시지를 의미합니다. 기본 게재 로그 표(**NmsBroadLog**)에는 모든 수신자에 대한 게재 로그가 포함됩니다.
기본 추적 로그 표(**NmsTrackingLog**)는 모든 수신자에 대한 추적 로그를 저장합니다. 추적 로그는 이메일 열기 및 클릭과 같은 수신자의 반응을 나타냅니다. 각 반응은 추적 로그에 해당합니다.
게재 로그 및 추적 로그는 Adobe Campaign에 지정되며 수정할 수 있는 특정 기간 후에 삭제됩니다. 따라서 정기적으로 로그를 내보내는 것이 좋습니다.

### 기술 표 {#technical-tables}

마지막으로 데이터 모델의 일부는 운영자 및 사용자 권한( )을 포함하여 애플리케이션 프로세스에 사용되는 기술 데이터로 구성됩니다.**Nms 그룹**), 폴더(**XtkFolder**).

## 기본 제공 수신자 테이블 사용 {#default-recipient-table}

Adobe Campaign의 기본 제공 수신자 테이블은 데이터 모델을 구축하기에 좋은 시작점을 제공합니다. 여기에는 쉽게 확장할 수 있는 사전 정의된 필드와 테이블 링크가 다수 포함되어 있습니다. 이 기능은 단순한 수신자 중심의 데이터 모델에 적합하기 때문에 주로 수신자를 타겟팅하는 경우 특히 유용합니다.

기본 제공 수신자 테이블을 사용하면 다음과 같은 이점이 있습니다.

* 구독, 시드 목록 등과 같은 기능이 내장된 작업
* 수신자 중심 데이터 모델을 사용하여 마케팅 데이터베이스 제공.
* 신속한 구현.
* 지원 및 파트너가 간편하게 유지 관리할 수 있습니다.

그러나 수신자 테이블을 확장할 수는 있지만 테이블의 필드 또는 링크 수는 줄일 수 없습니다.

>[!IMPORTANT]
>
>수신자 테이블의 필드는 기본 제공 모듈에 오류가 발생할 수 있으므로 유용하지 않더라도 삭제하지 않는 것이 좋습니다.

또한 수신자 테이블은 제품의 일부이므로 제품이 변함에 따라 테이블과 관련 양식이 모두 발전합니다. 따라서 업그레이드 시 모든 확장이 여전히 유효한지 확인하기 위해 추가 유지 관리가 필요합니다.

## 데이터 모델 확장 {#extending-data-model}

Adobe Campaign으로 시작할 때 기본 데이터 모델을 평가하여 마케팅 데이터를 저장하는 데 가장 적합한 테이블을 확인해야 합니다.

관련성이 있는 경우에서 설명한 것처럼 기본 수신자 테이블을 기본 제공 필드와 함께 사용할 수 있습니다 [이 섹션](#default-recipient-table).

필요한 경우 두 가지 메커니즘을 사용하여 확장할 수 있습니다.

* 새 필드로 기존 테이블을 확장합니다. 예를 들어 수신자 테이블에 새 &quot;충성도&quot; 필드를 추가할 수 있습니다.
* 데이터베이스의 각 프로필에서 수행한 모든 구매를 나열하는 &quot;구매&quot; 테이블과 같은 새 테이블을 만들고 수신자 테이블에 연결합니다.

개념 데이터 모델을 확장하도록 확장 스키마 구성에 대한 자세한 내용은 [스키마 편집 정보](../../configuration/using/about-schema-edition.md).

>[!IMPORTANT]
>
>데이터 모델 확장은 고급 사용자용으로 예약되어 있습니다.

## 사용자 지정 수신자 테이블 사용 {#custom-recipient-table}

Adobe Campaign 데이터 모델을 디자인할 때 [기본 제공 수신자 테이블](#default-recipient-table)또는 다음을 만들기로 결정 [사용자 지정 수신자 테이블](../../configuration/using/about-custom-recipient-table.md) 마케팅 프로필을 저장하는 테이블입니다.

실제로 데이터 모델이 수신자 중심 구조에 맞지 않으면 다른 테이블을 Adobe Campaign 내의 타겟팅 차원으로 설정할 수 있습니다. 예를 들어, 이는 단순히 수신자가 아닌 가구, 계정(휴대폰 등) 및 회사/사이트를 타겟팅해야 할 때 관련될 수 있습니다.

>[!NOTE]
>
>이 경우 새 을(를) 만들어야 합니다 [대상 매핑](../../configuration/using/target-mapping.md).

사용자 지정 수신자 테이블을 사용할 때 필요한 모든 원칙과 단계이에 자세히 설명되어 있습니다 [이 섹션](../../configuration/using/about-custom-recipient-table.md).

사용자 지정 수신자 테이블을 사용하면 다음과 같은 이점이 있습니다.

* **유연한 데이터 모델** - 기본 제공 수신자 테이블은 수신자 테이블 필드의 대부분이 필요하지 않거나 데이터 모델이 수신자 중심적이지 않은 경우 사용할 수 없습니다.

* **확장성** - 대용량 볼륨에는 효율적인 설계를 위해 적은 수의 필드를 포함하는 간소화된 테이블이 필요합니다. 기본 제공 수신자 테이블에는 쓸모없는 필드가 너무 많아 성능에 영향을 주고 효율성이 떨어질 수 있습니다.

* **데이터 위치** - 데이터가 기존의 외부 마케팅 데이터베이스에 있는 경우 기본 제공 수신자 테이블을 사용하는 데 많은 노력이 필요할 수 있습니다. 기존 구조를 기반으로 새 구조를 만드는 것이 더 간단합니다.

* **간편한 마이그레이션** - 업그레이드 시 모든 확장이 여전히 유효한지 확인하기 위해 유지 관리가 필요하지 않습니다.

>[!IMPORTANT]
>
>사용자 지정 수신자 테이블 사용은 고급 사용자용으로 예약되어 있으며 몇 가지 제한 사항이 적용됩니다. 자세한 내용은 [이 섹션](../../configuration/using/about-custom-recipient-table.md)을 참조하십시오.

## 관련 항목

다음 섹션에서 Campaign 데이터 모델에 대해 자세히 알아보세요.

* **기본 테이블에 대한 설명** - 기본 Campaign Classic 데이터 모델 설명에 대한 자세한 내용은 [이 섹션](../../configuration/using/data-model-description.md).

* **각 테이블에 대한 전체 설명** - 각 테이블에 대한 전체 설명에 액세스하려면 **[!UICONTROL Admin > Configuration > Data schemas]**&#x200B;목록에서 리소스를 선택하고 **[!UICONTROL Documentation]** 탭.

   ![](assets/data-model_documentation-tab.png)


* **Campaign 스키마** - 애플리케이션에 포함된 데이터의 물리적 및 논리적 구조는 XML에 설명되어 있습니다. 스키마라고 하는 Adobe Campaign에 특정된 문법을 따릅니다. Adobe Campaign 스키마에 대한 자세한 내용은 다음을 참조하십시오. [이 섹션](../../configuration/using/about-schema-reference.md).

* **데이터 모델 모범 사례** - Campaign 데이터 모델 아키텍처 및 관련 모범 사례에 대해 알아보기 [이 섹션](../../configuration/using/data-model-best-practices.md#data-model-architecture).
