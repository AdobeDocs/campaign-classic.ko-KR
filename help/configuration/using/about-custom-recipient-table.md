---
product: campaign
title: 사용자 정의 수신자 테이블 정보
description: 사용자 정의 수신자 테이블 정보
feature: Configuration, Custom Resources
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
exl-id: d8cea496-b3f3-420a-bf6e-b7cbb321b30d
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '679'
ht-degree: 2%

---

# 사용자 정의 수신자 테이블 사용{#about-custom-recipient-table}



이 섹션에서는 사용자 지정(또는 외부) 수신자 테이블 사용에 대한 원칙을 자세히 설명합니다.

기본적으로 Adobe Campaign은 기본 제공 함수 및 프로세스가 연결된 기본 제공 수신자 테이블을 제공합니다. 기본 제공 수신자 표에는 확장 테이블을 사용하여 쉽게 확장할 수 있는 사전 정의된 필드와 표가 있습니다.

이 확장 방법이 테이블을 확장할 수 있는 유연성을 제공하는 경우 테이블 내 필드나 링크의 수를 줄일 수 없습니다. 비표준 테이블 또는 &#39;외부 수신자 테이블&#39;을 사용하면 보다 유연하게 사용할 수 있지만 구현 시 특정 주의 사항이 필요합니다.

이 기능을 사용하면 Adobe Campaign에서 외부 데이터베이스의 데이터를 처리할 수 있습니다. 이 데이터는 게재에 대한 프로필 세트로 사용됩니다. 이 프로세스를 구현하려면 클라이언트의 요구 사항에 따라 관련될 수 있는 몇 가지 정밀도가 필요합니다. 예:

* Adobe Campaign 데이터베이스에 대한 업데이트 스트림 없음: 이 테이블의 데이터는 이를 호스팅하는 데이터베이스 엔진을 통해 직접 업데이트할 수 있습니다.
* 기존 데이터베이스에서 작동하는 프로세스에 변경 사항이 없습니다.
* 비표준 구조의 프로필 데이터베이스 사용: 단일 인스턴스를 사용하여 다양한 구조의 다양한 테이블에 저장된 프로필에 전달할 수 있습니다.
* Adobe Campaign 데이터베이스를 업데이트할 때 변경 또는 유지 관리가 필요하지 않습니다.
* 기본 제공 수신자 테이블은 대부분의 테이블 필드가 필요하지 않거나 데이터베이스 템플릿이 수신자에 중점을 두지 않은 경우 사용할 수 없습니다.
* 프로필의 수가 많은 경우 효율적이 되도록 필드가 적은 표가 필요합니다. 기본 제공 수신자 테이블에는 이 특정 사례에 사용할 수 있는 필드가 너무 많습니다.

이 섹션에서는 Adobe Campaign의 기존 테이블을 매핑할 수 있는 주요 사항과 테이블을 기반으로 게재를 실행하는 데 적용할 구성에 대해 설명합니다. 마지막으로, 기본 제공 수신자 테이블에서 사용할 수 있는 것과 같은 실용적인 쿼리 인터페이스를 사용자에게 제공하는 방법을 설명합니다. 이 절에서 제시하는 자료를 이해하기 위해서는 화면과 스키마 디자인의 원리에 대한 숙지가 필요하다.

## Recommendations 및 제한 사항 {#recommendations-and-limitations}

사용자 지정 수신자 테이블을 사용하는 데에는 다음과 같은 제한 사항이 있습니다.

* Adobe Campaign은 동일한 broadlog 및/또는 trackinglog 스키마에 연결된 타겟팅 스키마라고 하는 여러 수신자 스키마를 지원하지 않습니다. 그렇지 않으면 이후 데이터 조정에 예외 항목이 발생할 수 있습니다.

  아래 그래픽에서는 각 사용자 지정 수신자 스키마에 대한 필수 관계 구조를 자세히 설명합니다.
  ![](assets/custom_recipient_limitation.png)

  권장 사항:

   * 전용 **[!UICONTROL nms:BroadLogRcp]** 및 **[!UICONTROL nms:TrackingLogRcp]** 스키마를 기본 제공 **[!UICONTROL nms:Recipientschema]**. 이러한 두 로그 테이블은 추가 사용자 지정 수신자 테이블에 연결하면 안 됩니다.
   * 각 새 사용자 정의 수신자 스키마에 대한 전용 사용자 정의 브로드로그 및 추적 로그 스키마를 정의합니다. 대상 매핑을 설정할 때 자동으로 수행할 수 있습니다. 다음을 참조하십시오. [대상 매핑](../../configuration/using/target-mapping.md).

* 표준을 사용할 수 없습니다. **[!UICONTROL Services and Subscriptions]** 제품에 제공됩니다.

  이는 다음에 자세히 설명된 전체 작업을 의미합니다. [이 섹션](../../delivery/using/managing-subscriptions.md) 은(는) 적용할 수 없습니다.

* 링크 대상: **[!UICONTROL visitor]** 테이블이 작동하지 않습니다.

  따라서 **[!UICONTROL Social Marketing]** 모듈 올바른 테이블을 참조하도록 스토리지 단계를 구성해야 합니다.

  마찬가지로 참조 함수를 사용할 때는 표준 초기 메시지 전송 템플릿을 조정해야 합니다.

* 목록에 프로필을 수동으로 추가할 수 없습니다.

  따라서 다음에 자세히 설명된 절차 [이 섹션](../../platform/using/creating-and-managing-lists.md) 는 추가 구성 없이 적용할 수 없습니다.

  >[!NOTE]
  >
  >워크플로우를 사용하여 수신자 목록을 만들 수 있습니다. 자세한 내용은 다음을 참조하십시오. [워크플로우를 사용하여 프로필 목록 만들기](../../configuration/using/creating-a-profile-list-with-a-workflow.md).

또한 다양한 기본 구성에서 사용되는 기본값을 확인하는 것이 좋습니다. 사용되는 기능에 따라 몇 가지 수정을 수행해야 합니다.

예제:

* 특정 표준 보고서, 특히 제공 **상호 작용** 및 **모바일 애플리케이션** 다시 개발해야 합니다. 다음을 참조하십시오. [보고서 관리](../../configuration/using/managing-reports.md) 섹션.
* 특정 워크플로우 활동에 대한 기본 구성은 표준 수신자 테이블(**[!UICONTROL nms:recipient]**): 외부 수신자 테이블에 사용할 때 이러한 구성을 변경해야 합니다. 다음을 참조하십시오. [워크플로우 관리](../../configuration/using/managing-workflows.md) 섹션.
* 표준 **[!UICONTROL Unsubscription link]** 개인화 블록을 조정해야 합니다.
* 표준 게재 템플릿의 대상 매핑을 수정해야 합니다.
* V4 양식은 외부 수신자 테이블과 함께 사용할 수 없습니다. 웹 응용 프로그램을 사용해야 합니다.
