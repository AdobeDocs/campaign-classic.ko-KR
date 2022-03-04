---
product: campaign
title: 게재 전송 문제 해결
description: 게재 성능 및 게재 모니터링과 관련된 문제를 해결하는 방법에 대해 자세히 알아봅니다
feature: Monitoring, Deliverability
exl-id: 37b1d7fb-7ceb-4647-9aac-c8a80495c5bf
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '791'
ht-degree: 1%

---

# 게재 전송 문제 해결 {#delivery-troubleshooting}

![](../../assets/common.svg)

이 섹션에는 게재를 보낼 때 발생할 수 있는 일반적인 문제와 이러한 문제를 해결하는 방법이 나와 있습니다.

또한 다음에 자세히 설명된 우수 사례 및 검사 목록을 따라야 합니다. [이 페이지](delivery-performances.md) 게재가 제대로 수행되도록 합니다.

**관련 항목:**

* [게재 상태](delivery-statuses.md)
* [게재 대시보드](delivery-dashboard.md)
* [게재 실패 이해](understanding-delivery-failures.md)

## 느린 게재 {#slow-deliveries}

을 클릭한 후 **[!UICONTROL Send]** 단추, 배달이 평소보다 오래 걸리는 것 같습니다. 이 문제는 다른 요소에 의해 발생할 수 있습니다.

* 일부 이메일 공급자가 사용자의 IP 주소를에 추가했을 수 차단 목록 있습니다. 이 경우 브로드로그를 확인하고 다음을 참조하십시오 [이 섹션](about-deliverability.md).

* 게재 크기가 너무 커서 빠르게 처리할 수 없거나, 높은 JavaScript 개인화와 함께 발생할 수 있으며, 게재 무게가 60KB 이상인 경우 발생할 수 있습니다. Adobe Campaign 를 참조하십시오 [게재 모범 사례](delivery-best-practices.md) 컨텐츠 지침에 대해 알아봅니다.

* Adobe Campaign MTA 내에서 전송률 조절이 발생했을 수 있습니다. 이 문제는 다음 원인으로 인해 발생합니다.

   * 보류 중인 메시지(**[!UICONTROL quotas met]** 메시지): Campaign에 정의된 선언적 MX 규칙으로 선언된 할당량이 충족되었습니다. 이 메시지에 대한 자세한 내용은 [이 페이지](deliverability-faq.md). MX 규칙에 대한 자세한 내용은 [이 섹션](../../installation/using/email-deliverability.md#about-mx-rules).

   * 보류 중인 메시지(**[!UICONTROL dynamic flow control]** 메시지): Campaign MTA가 주어진 ISP에 메시지를 전달하려고 할 때 오류가 발생하여 오류 밀도가 너무 커 잠재적이 발생하지 차단 목록 않습니다.

* 시스템 문제로 인해 서버가 서로 상호 작용할 수 없습니다. 이렇게 하면 전체 전송 프로세스가 느려질 수 있습니다. 예를 들어 개인화 데이터를 가져오는 과정에서 Campaign에 영향을 줄 수 있는 메모리 또는 리소스 문제가 없는지 서버를 확인합니다.

## 예약된 게재 {#scheduled-deliveries-}

게재가 정확히 예약된 날짜에 실행되지 않는 경우 서버 시간대 간의 차이와 관련이 있을 수 있습니다. 중간 소싱 인스턴스와 프로덕션 인스턴스는 서로 다른 시간대에 있을 수 있습니다.

예를 들어 중간 소싱 인스턴스가 브리즈번 시간대에 있고 프로덕션 인스턴스가 다윈의 시간대에 있는 경우 두 시간대가 30분 정도 떨어져 있는 경우 감사 로그에 게재가 11:56에 생산되도록 스케줄링된 경우 mid에 대해 스케줄링된 동일한 게재가 30분의 1 차이가 있는 12:26이 될 것임을 분명히 알 수 있습니다.

## 실패 상태 {#failed-status}

이메일 게재의 상태가 **[!UICONTROL Failed]**&#x200B;개인화 블록 문제에 연결할 수 있습니다. 예를 들어, 게재의 개인화 블록은 스키마가 게재 매핑과 일치하지 않을 때 오류를 생성할 수 있습니다.

게재 로그는 게재가 실패한 이유를 확인하는 키입니다. 게재 로그에서 감지할 수 있는 가능한 오류는 다음과 같습니다.

* 받는 사람 메시지가 &quot;연결할 수 없음&quot; 오류로 인해 실패했습니다.

   ```
   Error while compiling script 'content htmlContent' line X: `[table]` is not defined. JavaScript: error while evaluating script 'content htmlContent
   ```

   이 문제의 원인은 거의 항상 HTML 내에서 업스트림 타깃팅이나 게재 대상 매핑에서 정의되거나 매핑되지 않은 테이블이나 필드를 호출하려고 시도하는 개인화입니다.

   이를 수정하려면 워크플로우 및 게재 콘텐츠를 검토하여 해당 테이블을 호출하려고 하는 개인화와 테이블을 매핑할 수 있는지 여부를 결정해야 합니다. 거기에서 HTML에서 이 테이블에 대한 호출을 제거하거나 게재 매핑을 수정하는 것이 해결 방법입니다.

* 중간 소싱 배포 모델에서 게재 로그에 다음 메시지가 나타날 수 있습니다.

   ```
   Error during the call of method 'AppendDeliveryPart' on the mid sourcing server: 'Communication error with the server: please check this one is correctly configured. Code HTTP 408 'Service temporarily unavailable'.
   ```

   원인은 성능 문제와 연결되어 있습니다. 즉, 마케팅 인스턴스가 중간 소싱 서버로 데이터를 보내기 전에 데이터를 작성하는 데 너무 많은 시간이 소요됩니다.

   이를 해결하기 위해 데이터베이스에 대해 진공 및 재색인을 수행하는 것이 좋습니다. 데이터베이스 유지 관리에 대한 자세한 내용은 [이 섹션](../../production/using/recommendations.md).

   또한 예약된 활동과 실패한 상태의 모든 워크플로우를 다시 시작해야 합니다. [이 섹션](../../workflow/using/scheduler.md)을 참조하십시오.

* 게재가 실패하면 게재 로그에 다음 오류가 표시될 수 있습니다.

   ```
   DLV-XXXX The count of message prepared (123) is greater than the number of messages to send (111). Please contact support.
   ```

   일반적으로 이 오류는 이메일 내에 수신자에 대한 값이 두 개 이상 있는 개인화 필드 또는 블록이 있음을 의미합니다. 개인화 블록을 사용하고 있으며, 특정 수신자에 대해 두 개 이상의 레코드를 가져오고 있습니다.

   이를 해결하려면 사용된 개인화 데이터를 확인한 다음 해당 필드에 대해 둘 이상의 항목이 있는 수신자의 대상을 확인합니다. 를 사용할 수도 있습니다 **[!UICONTROL Deduplication]** 게재 활동 전에 타겟팅 워크플로우에서 한 번에 하나의 개인화 필드만 있는지 확인하는 활동. 중복 제거에 대한 자세한 내용은 [이 페이지](../../workflow/using/deduplication.md).

* 일부 게재는 &quot;접근 불가&quot; 오류로 실패할 수 있습니다.

   ```
   Inbound email bounce (rule 'Auto_replies' has matched this bounce).
   ```

   즉, 게재에 성공했지만 Adobe Campaign이 &#39;자동 회신&#39; 인바운드 전자 메일 규칙과 일치하는 수신자(예: &quot;부재 중&quot; 회신)로부터 자동 답장을 받았음을 의미합니다.

   자동 회신 이메일은 Adobe Campaign에서 무시하며 수신자의 주소는 격리로 전송되지 않습니다.
