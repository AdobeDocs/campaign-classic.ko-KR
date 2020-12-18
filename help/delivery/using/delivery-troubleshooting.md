---
solution: Campaign Classic
product: campaign
title: 문제 해결
description: 배달 성과에 대한 자세한 내용과 배달 모니터링과 관련된 문제를 해결하는 방법에 대해 알아보십시오.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
translation-type: tm+mt
source-git-commit: f3ba836bbb5a5f82d6a7868dcb15edc8e61b9a5b
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 1%

---


# 전송 문제 해결 {#delivery-troubleshooting}

이 섹션에는 게재를 전송할 때 발생할 수 있는 일반적인 문제와 이러한 문제를 해결하는 방법이 나와 있습니다.

또한 [이 페이지](../../delivery/using/delivery-performances.md)에 자세히 설명된 우수 사례 및 확인 목록을 따라 배달이 제대로 수행되는지 확인하십시오.

**관련 항목:**

* [배달 상태](../../delivery/using/delivery-statuses.md)
* [배달 대시보드](../../delivery/using/delivery-dashboard.md)
* [게재 실패 이해](../../delivery/using/understanding-delivery-failures.md)

## 느리게 배달 {#slow-deliveries}

**[!UICONTROL Send]** 단추를 클릭하면 배달이 평소보다 오래 걸리는 것 같습니다. 이것은 다른 요소로 인해 발생할 수 있습니다.

* 일부 이메일 공급자가 사용자의 IP 주소를에 추가했을 수 차단 목록 있습니다. 이 경우 브로드로그를 확인하고 [이 섹션](../../delivery/using/about-deliverability.md)을 참조하십시오.

* 배달이 너무 커서 신속하게 처리할 수 없을 수도 있고, JavaScript 개인화가 높거나 배달 크기가 60KB 이상인 경우 발생할 수 있습니다. 콘텐츠 가이드라인에 대한 자세한 내용은 Adobe Campaign [배달 모범 사례](../../delivery/using/delivery-best-practices.md)를 참조하십시오.

* Adobe Campaign MTA 내에서 조절이 발생했을 수 있습니다. 이 문제는 다음 경우에 발생합니다.

   * 보류 중인 메시지(**[!UICONTROL quotas met]** 메시지):Campaign에 정의된 선언적 MX 규칙으로 선언된 할당량이 충족되었습니다. 이 메시지에 대한 자세한 내용은 [이 페이지](../../delivery/using/deliverability-faq.md)를 참조하십시오. MX 규칙에 대한 자세한 내용은 [이 페이지](../../delivery/using/technical-recommendations.md#mx-rules)를 참조하십시오.

   * 보류 중인 메시지(**[!UICONTROL dynamic flow control]** 메시지):캠페인 MTA가 오류 농도가 너무 커서 잠재적인에 부딪치는 등 둔화를 초래하는 지정된 ISP의 메시지를 전달하려고 할 때 오류가 차단 목록 발생했습니다.

* 시스템 문제로 인해 서버가 서로 상호 작용할 수 없습니다.이렇게 하면 전체 전송 프로세스가 느려질 수 있습니다. 예를 들어 개인화 데이터를 가져오는 과정에서 Campaign에 영향을 줄 수 있는 메모리 또는 리소스 문제가 없는지 서버를 확인합니다.

## 예약된 배달 {#scheduled-deliveries-}

게재가 정확한 예약된 날짜에 실행되지 않으면 서버 표준 시간대 간의 차이와 관련이 있을 수 있습니다. 중간 소싱 인스턴스와 생산 인스턴스는 다른 시간대에 있을 수 있습니다.

예를 들어 중간 소싱 인스턴스가 브리즈번 시간대와 생산 인스턴스가 다윈 시간대에만 있는 경우, 두 시간대는 서로 30분 거리에 있습니다. 감사 기록에는 배달이 11:56에 생산되도록 예정되어 있는 경우 중간으로 예약된 동일한 배달이 30분 차이가 있는 12:26에 있음을 분명히 알 수 있습니다.

## 실패한 상태 {#failed-status}

이메일 배달 상태가 **[!UICONTROL Failed]**&#x200B;인 경우 개인화 블록 문제에 연결할 수 있습니다. 예를 들어 배급의 개인화 블록은 스키마가 배달 매핑과 일치하지 않을 때 오류를 생성할 수 있습니다.

배달 로그는 배달이 실패한 이유를 확인하는 데 중요합니다. 배달 로그에서 감지할 수 있는 오류는 다음과 같습니다.

* 받는 사람 메시지에 &quot;연결할 수 없습니다&quot; 오류가 발생하여 다음 내용이 표시되지 않습니다.

   ```
   Error while compiling script 'content htmlContent' line X: `[table]` is not defined. JavaScript: error while evaluating script 'content htmlContent
   ```

   이 문제의 원인은 업스트림 타깃팅 또는 게재 대상 매핑에서 정의되거나 매핑되지 않은 테이블이나 필드를 호출하려고 시도하는 HTML 내의 개인화입니다.

   이 문제를 해결하려면 워크플로우 및 전달 컨텐츠를 검토하여 특정 개인화를 통해 해당 테이블을 호출하려고 시도하는 요소와 테이블을 매핑할 수 있는지 여부를 명확하게 결정해야 합니다. 여기에서 HTML에서 이 테이블에 대한 호출을 제거하거나 배달에 대한 매핑을 수정하는 것이 해결 경로가 됩니다.

* 중간 소싱 배포 모델에서 다음 메시지가 배달 로그에 나타날 수 있습니다.

   ```
   Error during the call of method 'AppendDeliveryPart' on the mid sourcing server: 'Communication error with the server: please check this one is correctly configured. Code HTTP 408 'Service temporarily unavailable'.
   ```

   원인은 성능 문제와 연결되어 있습니다. 즉, 마케팅 인스턴스는 데이터를 중간 소싱 서버로 보내기 전에 데이터를 작성하는 데 너무 많은 시간을 할애합니다.

   이 문제를 해결하려면 데이터베이스에 대해 진공청소기를 다시 색인화하는 것이 좋습니다. 데이터베이스 유지 관리에 대한 자세한 내용은 [이 섹션](../../production/using/recommendations.md)을 참조하십시오.

   또한 예약된 활동이 있는 모든 워크플로우와 실패한 상태의 모든 워크플로우도 다시 시작해야 합니다. [이 섹션](../../workflow/using/scheduler.md)을 참조하십시오.

* 배달이 실패하면 배달 로그에 다음 오류가 나타날 수 있습니다.

   ```
   DLV-XXXX The count of message prepared (123) is greater than the number of messages to send (111). Please contact support.
   ```

   일반적으로 이 오류는 이메일 내에 수신자에 대해 값이 두 개 이상인 개인화 필드나 블록이 있음을 의미합니다. 개인화 블록을 사용하고 있으며 특정 수신자에 대해 둘 이상의 레코드를 가져오는 중입니다.

   이 문제를 해결하려면 사용된 개인화 데이터를 확인한 다음 해당 필드에 대해 둘 이상의 항목이 있는 수신자의 대상을 확인합니다. 배달 활동 전에 타깃팅 워크플로우에서 **[!UICONTROL Deduplication]** 활동을 사용하여 한 번에 하나의 개인화 필드만 있는지 확인할 수도 있습니다. 데이터 중복 제거에 대한 자세한 내용은 [이 페이지](../../workflow/using/deduplication.md)를 참조하십시오.

* 다음 내용이 포함된 &quot;연결할 수 없음&quot; 오류로 인해 일부 배달이 실패할 수 있습니다.

   ```
   Inbound email bounce (rule 'Auto_replies' has matched this bounce).
   ```

   즉, 배달에 성공했지만 Adobe Campaign은 &#39;자동 응답&#39; 인바운드 이메일 규칙과 일치하는 수신자(&quot;부재 중&quot; 응답)로부터 자동 회신을 수신했음을 의미합니다.

   자동 응답 이메일은 Adobe Campaign에서 무시되며 받는 사람의 주소는 검역소에 전달되지 않습니다.
