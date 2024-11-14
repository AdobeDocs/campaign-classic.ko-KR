---
product: campaign
title: 감사 추적
description: Campaign 감사 추적을 사용하여 인스턴스를 모니터링하는 방법 알아보기
feature: Audit Trail, Monitoring, Workflows
exl-id: 8508d879-fb38-4b1f-9f55-0341bb8d0c67
source-git-commit: 3d1ed85dcafc5afc4088db98c09d78fb7e9c0a39
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 2%

---

# 감사 추적{#audit-trail}

>[!INFO]
>
>[Adobe Campaign v8 설명서](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/audit-trail)에서 감사 추적 기능에 대해 자세히 알아보세요.

Adobe Campaign에서 **[!UICONTROL Audit trail]**&#x200B;을(를) 사용하면 인스턴스 내에서 수행한 변경 내용의 전체 기록에 액세스할 수 있습니다.

**[!UICONTROL Audit trail]**&#x200B;에서는 Adobe Campaign 인스턴스 내에서 발생하는 작업 및 이벤트의 포괄적인 목록을 실시간으로 캡처합니다. 여기에는 워크플로우에 발생한 사항, 워크플로우를 마지막으로 업데이트한 사람 또는 사용자가 인스턴스에서 수행한 작업 등의 질문에 답변하는 데 도움이 되는 데이터 기록에 액세스하는 셀프서비스 방법이 포함되어 있습니다.

>[!NOTE]
>
>Adobe Campaign은 사용자 권한, 템플릿, 개인화 또는 캠페인 내에서 수행된 변경 사항을 감사하지 않습니다.\
>감사 추적은 인스턴스 관리자만 관리할 수 있습니다.

![](assets/audit_trail_2.png)

+++ 감사 추적 사용 가능한 엔터티에 대해 자세히 알아보기

* **스키마 감사 추적**: 스키마에 대한 변경 내용을 살펴보고 수정한 사람과 수정한 시기를 식별할 수 있습니다.

  스키마에 대한 자세한 내용은 이 [페이지](../../configuration/using/data-schemas.md)를 참조하세요.

* **워크플로 감사 추적**&#x200B;은(는) 다음을 포함하여 워크플로와 관련된 모든 작업을 추적합니다.

   * 시작
   * 일시 정지
   * 정지
   * 다시 시작
   * 정리 - 작업 삭제 내역에 해당합니다.
   * 시뮬레이션 모드에서 시작 작업과 동일한 시뮬레이션
   * 지금 대기 중인 작업 실행 작업과 동일한 절전 모드 해제
   * 무조건 정지

  워크플로우에 대한 자세한 내용은 이 [페이지](../../workflow/using/about-workflows.md)를 참조하세요.

  워크플로우를 모니터링하는 방법에 대한 자세한 내용은 [전용 섹션](../../workflow/using/monitoring-workflow-execution.md)을 참조하세요.

* **옵션 감사 추적**&#x200B;을 통해 활동 및 옵션에 대한 마지막 수정 사항을 확인할 수 있습니다.

  옵션에 대한 자세한 내용은 이 [페이지](../../installation/using/configuring-campaign-options.md)를 참조하세요.

* **게재 감사 추적**&#x200B;을 통해 활동 및 게재에 대한 마지막 수정 사항을 확인할 수 있습니다.

  게재에 대한 자세한 내용은 이 [페이지](../../delivery/using/communication-channels.md)를 참조하세요.

* **외부 계정**&#x200B;을(를) 사용하면 기술 워크플로우 또는 캠페인 워크플로우와 같은 기술 프로세스에서 사용하는 외부 계정에 대한 수정 사항을 확인할 수 있습니다.

  외부 계정에 대한 자세한 내용은 이 [페이지](../../installation/using/external-accounts.md)를 참조하세요.

* **게재 매핑**&#x200B;을(를) 사용하면 활동 및 게재 매핑에 대한 최근 수정 사항을 모니터링할 수 있습니다.

  게재 매핑에 대한 자세한 내용은 이 [페이지](../../configuration/using/target-mapping.md)를 참조하세요.

* **웹 응용 프로그램**&#x200B;을(를) 사용하면 입력 및 선택 필드가 있는 페이지를 만드는 데 사용되는 Campaign V8의 웹 폼에 대한 수정 사항을 확인할 수 있으며, 여기에는 데이터베이스의 데이터가 포함될 수 있습니다.

  웹 응용 프로그램에 대한 자세한 내용은 이 [페이지](../../web/using/about-web-applications.md)를 참조하세요.

* **오퍼**&#x200B;를 사용하면 활동 및 오퍼에 대한 마지막 수정 사항을 확인할 수 있습니다.

  오퍼에 대한 자세한 내용은 이 [페이지](../../interaction/using/interaction-and-offer-management.md)를 참조하세요.

* **연산자**&#x200B;을(를) 사용하면 연산자의 활동 및 최근 수정 사항을 모니터링할 수 있습니다.

  연산자에 대한 자세한 내용은 이 [페이지](../../platform/using/access-management-operators.md)를 참조하세요.

+++
