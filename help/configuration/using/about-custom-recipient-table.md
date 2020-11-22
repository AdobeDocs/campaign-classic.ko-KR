---
solution: Campaign Classic
product: campaign
title: 사용자 지정 수신자 테이블 정보
description: 사용자 지정 수신자 테이블 정보
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '665'
ht-degree: 2%

---


# 사용자 지정 수신자 테이블 정보{#about-custom-recipient-table}

이 섹션에서는 비표준 수신자 테이블을 사용하기 위한 원칙에 대해 자세히 설명합니다.

기본적으로, Adobe Campaign은 즉시 사용 가능한 기능과 프로세스가 연결된 표준 수신자 테이블을 제공합니다. 표준 수신자 테이블에는 확장 테이블을 사용하여 쉽게 확장할 수 있는 사전 정의된 필드와 테이블이 많이 있습니다.

이 확장 방법이 표를 확장하는 데 상당한 유연성을 제공하는 경우 테이블의 필드나 링크 수를 줄일 수 없습니다. 표준이 아닌 표 또는 &#39;외부 수신자 테이블&#39;을 사용하면 유연성이 향상되지만 구현할 때는 특정 예방 조치가 필요합니다.

## 정확도 {#precisions}

이 기능을 통해 Adobe Campaign은 외부 데이터베이스의 데이터를 처리할 수 있습니다.이 데이터는 배달용 프로필 세트로 사용됩니다. 이 프로세스를 구현하려면 클라이언트의 요구 사항에 따라 관련이 있을 수 있는 몇 가지 정밀도가 수반됩니다. 예:

* Adobe Campaign 데이터베이스에 대한 업데이트 스트림이 없습니다.이 테이블의 데이터는 이 테이블을 호스팅하는 데이터베이스 엔진을 통해 직접 업데이트할 수 있습니다.
* 기존 데이터베이스에서 작동하는 프로세스에 변경 사항이 없습니다.
* 비표준 구조와 함께 프로필 데이터베이스 사용:단일 인스턴스를 사용하여 다양한 구조가 있는 다양한 표에 저장된 프로파일에 제공할 수 있습니다.
* Adobe Campaign 데이터베이스를 업데이트할 때 변경 또는 유지 관리가 필요하지 않습니다.
* 테이블 필드 대부분이 필요하지 않거나 데이터베이스 템플릿이 받는 사람 중심으로 되어 있지 않으면 표준 받는 사람 테이블이 무용지물입니다.
* 프로필의 수가 많을 경우 필드가 거의 없는 표를 사용하여 효율적으로 작업해야 합니다. 표준 받는 사람 테이블에 이 특정 사례에 비해 필드가 너무 많습니다.

이 섹션에서는 Adobe Campaign의 기존 테이블을 매핑할 수 있는 핵심 사항과, 테이블을 기준으로 배달 실행에 적용할 구성을 설명합니다. 마지막으로, 표준 수신자 테이블에서 사용할 수 있는 것과 같이 실용적인 인터페이스를 사용자에게 제공하는 방법을 설명합니다. 이 섹션에 나와 있는 자료를 이해하려면 화면 및 스키마 디자인의 원칙에 대한 충분한 지식이 있어야 합니다.

## Recommendations 및 제한 사항 {#recommendations-and-limitations}

외부 받는 사람 테이블을 사용하면 다음과 같은 제한 사항이 있습니다.

* Adobe Campaign은 여러 받는 사람 스키마를 지원하지 않습니다. 타깃팅 스키마로 알고, 동일한 브로드로그 및/또는 trackinglog 스키마에 연결되어 있습니다. 그렇지 않으면 이후 데이터 조정에서 예외 항목이 발생할 수 있습니다.

   아래 그래픽에서는 각 사용자 지정 수신자 스키마에 대해 필요한 관계형 구조에 대해 자세히 설명합니다.
   ![](assets/custom_recipient_limitation.png)

   권장 사항:

   * 간편하게 사용할 수 있도록 **[!UICONTROL nms:BroadLogRcp]** 및 **[!UICONTROL nms:TrackingLogRcp]** 스키마를 제공할 수 있습니다 **[!UICONTROL nms:Recipientschema]**. 이러한 두 개의 로그 테이블은 추가 사용자 지정 수신자 테이블에 링크되어서는 안 됩니다.
   * 새 사용자 지정 수신자 스키마에 대한 전용 사용자 지정 브로드캐스트 로그 및 추적 로그 스키마를 정의합니다. 대상 매핑을 설정할 때 이 작업을 자동으로 수행할 수 있습니다. [대상 매핑을 참조하십시오](../../configuration/using/target-mapping.md).

* 제품에서 **[!UICONTROL Services and Subscriptions]** 제공하는 표준은 사용할 수 없습니다.

   이는 [이 섹션에](../../delivery/using/managing-subscriptions.md) 설명된 전체 작업을 적용할 수 없음을 의미합니다.

* 표가 있는 **[!UICONTROL visitor]** 링크가 작동하지 않습니다.

   따라서 **[!UICONTROL Social Marketing]** 모듈을 사용하려면 올바른 테이블을 참조하도록 저장소 단계를 구성해야 합니다.

   마찬가지로 참조 기능을 사용할 때는 표준 초기 메시지 전송 템플릿을 조정해야 합니다.

* 목록에 프로필을 수동으로 추가할 수는 없습니다.

   따라서 추가 구성 없이 [이 섹션에](../../platform/using/creating-and-managing-lists.md) 설명된 절차는 적용되지 않습니다.

   >[!NOTE]
   >
   >워크플로우를 사용하여 수신자 목록을 만들 수도 있습니다. 자세한 내용은 워크플로우로 [프로필 목록 만들기를 참조하십시오](../../configuration/using/creating-a-profile-list-with-a-workflow.md).

또한 다음과 같은 다양한 기본 구성에 사용되는 기본값을 확인하는 것이 좋습니다.사용하는 기능에 따라 여러 가지 적응이 이루어져야 합니다.

예제:

* 특정 표준 보고서, 특히 **상호 작용** 및 **모바일 애플리케이션** 등은 재개발되어야 합니다. 보고서 [관리 섹션을](../../configuration/using/managing-reports.md) 참조하십시오.
* 특정 워크플로우 활동에 대한 기본 구성은 표준 수신자 테이블(**[!UICONTROL nms:recipient]**)을 참조합니다.이러한 구성은 외부 수신자 테이블에 사용될 때 변경해야 합니다. 워크플로우 [관리 섹션을](../../configuration/using/managing-workflows.md) 참조하십시오.
* 표준 **[!UICONTROL Unsubscription link]** 개인화 블록을 조정해야 합니다.
* 표준 배달 템플릿의 대상 매핑을 수정해야 합니다.
* V4 양식은 외부 받는 사람 테이블과 호환하지 않습니다.웹 응용 프로그램을 사용해야 합니다.

