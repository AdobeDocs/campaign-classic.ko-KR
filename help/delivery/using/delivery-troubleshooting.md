---
product: campaign
title: 게재 전송 문제 해결
description: 게재 성능 및 게재 모니터링과 관련된 문제를 해결하는 방법에 대해 자세히 알아보기
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Monitoring, Deliverability
exl-id: 37b1d7fb-7ceb-4647-9aac-c8a80495c5bf
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '791'
ht-degree: 1%

---

# 게재 전송 문제 해결 {#delivery-troubleshooting}



이 섹션에서는 게재를 보낼 때 발생할 수 있는 일반적인 문제와 해결 방법을 나열합니다.

또한 다음에 설명된 모범 사례 및 검사 목록을 따라야 합니다. [이 페이지](delivery-performances.md) 게재 성능을 확인합니다.

**관련 항목:**

* [게재 상태](delivery-statuses.md)
* [게재 대시보드](delivery-dashboard.md)
* [게재 실패 이해](understanding-delivery-failures.md)

## 느린 게재 {#slow-deliveries}

을(를) 클릭한 후 **[!UICONTROL Send]** 버튼입니다, 배송이 평소보다 오래 걸리는 것 같습니다. 이 문제는 서로 다른 요소로 인해 발생할 수 있습니다.

* 일부 이메일 공급자가 IP 주소를 차단 목록에 추가했을 수 있습니다. 이 경우 브로드로그를 확인하고 다음을 참조하십시오 [이 섹션](about-deliverability.md).

* 게재가 너무 커서 빠르게 처리할 수 없습니다. 이 문제는 높은 JavaScript 개인화를 통해 발생하거나 게재 무게가 60kbyte를 초과하는 경우 발생할 수 있습니다. Adobe Campaign 참조 [게재 모범 사례](delivery-best-practices.md) 콘텐츠 지침에 대해 알아봅니다.

* Adobe Campaign MTA 내에서 제한이 발생했을 수 있습니다. 이 문제는 다음으로 인해 발생합니다.

   * 보류된 메시지(**[!UICONTROL quotas met]** message): Campaign에 정의된 선언적 MX 규칙으로 선언된 할당량이 충족되었습니다. 이 메시지에 대한 자세한 내용은 [이 페이지](deliverability-faq.md). MX 규칙에 대한 자세한 내용은 [이 섹션](../../installation/using/email-deliverability.md#about-mx-rules).

   * 보류된 메시지(**[!UICONTROL dynamic flow control]** message): 지정된 ISP에 대해 메시지를 전달하려고 할 때 Campaign MTA에 오류가 발생했습니다. 이로 인해 지연 시간으로 인해 오류 밀도가 너무 높아져 잠재적 차단 목록이 발생할 수 있습니다.

* 시스템 문제로 인해 서버가 서로 상호 작용하지 못할 수 있습니다. 이렇게 하면 전체 전송 프로세스가 느려질 수 있습니다. 예를 들어 개인화 데이터를 가져오는 과정에서 Campaign에 영향을 줄 수 있는 메모리 또는 리소스 문제가 없는지 서버를 확인합니다.

## 예약된 게재 {#scheduled-deliveries-}

게재가 정확한 예약된 날짜에 실행되지 않는 경우 서버 시간대 간의 차이와 관련될 수 있습니다. 중간 소싱 인스턴스와 프로덕션 인스턴스는 다른 시간대에 있을 수 있습니다.

예를 들어 중간 소싱 인스턴스가 브리즈번 시간대에 있고 프로덕션 인스턴스가 다윈 시간대에 있는 경우 두 시간대가 서로 30분 정도 떨어져 있으며, 감사 로그에서 게재를 11:56에 프로덕션으로 예약한 경우 mid로 예약한 동일한 게재가 12:26에 30분 정도 차이가 난다는 것을 명확하게 확인할 수 있습니다.

## 실패 상태 {#failed-status}

이메일 게재 상태가 다음과 같은 경우 **[!UICONTROL Failed]**, 개인화 블록의 문제와 연결할 수 있습니다. 게재의 개인화 블록은 예를 들어 스키마가 게재 매핑과 일치하지 않을 때 오류를 생성할 수 있습니다.

게재 로그는 게재가 실패한 이유를 알아보는 중요한 요소입니다. 게재 로그에서 감지할 수 있는 가능한 오류는 다음과 같습니다.

* 수신자 메시지가 다음 내용을 포함하는 &quot;연결할 수 없음&quot; 오류로 인해 실패:

   ```
   Error while compiling script 'content htmlContent' line X: `[table]` is not defined. JavaScript: error while evaluating script 'content htmlContent
   ```

   이 문제의 원인은 거의 항상 업스트림 타겟팅 또는 게재 대상 매핑에서 정의되거나 매핑되지 않은 테이블 또는 필드를 호출하려는 HTML 내의 개인화입니다.

   이 문제를 해결하려면 워크플로우 및 게재 콘텐츠를 검토하여 해당 테이블을 호출하려고 하는 개인화와 테이블을 매핑할 수 있는지 여부를 구체적으로 결정해야 합니다. 여기에서 HTML에서 이 테이블에 대한 호출을 제거하거나 매핑을 게재에 수정하면 문제 해결 경로가 됩니다.

* 중간 소싱 배포 모델에서 게재 로그에 다음 메시지가 표시될 수 있습니다.

   ```
   Error during the call of method 'AppendDeliveryPart' on the mid sourcing server: 'Communication error with the server: please check this one is correctly configured. Code HTTP 408 'Service temporarily unavailable'.
   ```

   원인은 성능 문제와 관련이 있습니다. 즉, 마케팅 인스턴스가 데이터를 중간 소싱 서버에 보내기 전에 데이터를 작성하는 데 너무 많은 시간이 소요됩니다.

   이 문제를 해결하려면 진공을 수행하고 데이터베이스를 다시 인덱싱하는 것이 좋습니다. 데이터베이스 유지 관리에 대한 자세한 내용은 [이 섹션](../../production/using/recommendations.md).

   또한 예약된 활동이 있는 모든 워크플로우와 실패 상태에 있는 모든 워크플로우를 다시 시작해야 합니다. [이 섹션](../../workflow/using/scheduler.md)을 참조하십시오.

* 게재가 실패하면 게재 로그에 다음 오류가 표시될 수 있습니다.

   ```
   DLV-XXXX The count of message prepared (123) is greater than the number of messages to send (111). Please contact support.
   ```

   일반적으로 이 오류는 이메일 내에 수신자에 대한 값이 두 개 이상 있는 개인화 필드 또는 블록이 있음을 의미합니다. 개인화 블록을 사용 중이며 특정 수신자에 대해 두 개 이상의 레코드를 가져오고 있습니다.

   이를 해결하려면 사용된 개인화 데이터를 확인한 다음 해당 필드에 둘 이상의 항목이 있는 수신자의 타겟을 확인합니다. 다음을 사용할 수도 있습니다. **[!UICONTROL Deduplication]** 확인할 게재 활동 이전에 타기팅 워크플로우의 활동은 한 번에 하나의 개인화 필드만 있습니다. 중복 제거에 대한 자세한 내용은 [이 페이지](../../workflow/using/deduplication.md).

* 일부 게재가 실패하고 다음과 같은 &quot;연결할 수 없음&quot; 오류가 표시될 수 있습니다.

   ```
   Inbound email bounce (rule 'Auto_replies' has matched this bounce).
   ```

   즉, 게재는 성공했지만 Adobe Campaign이 &#39;Auto_replies&#39; 인바운드 이메일 규칙과 일치하는 수신자로부터 자동 회신(예: &quot;부재 중&quot; 회신)을 받았습니다.

   자동 회신 이메일은 Adobe Campaign에서 무시되며 수신자 주소는 격리에 전송되지 않습니다.
