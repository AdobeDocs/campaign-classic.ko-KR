---
title: 게재 모니터링
seo-title: 게재 모니터링
description: 게재 모니터링
seo-description: null
page-status-flag: never-activated
uuid: 7cb409eb-a01c-4b4d-bb62-760e0bafdc8a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
discoiquuid: 3aab3d47-76fd-4c68-add4-9c14240c936e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: bc54cef4c44be4c694e062f56685dbb09d2fcf8e
workflow-type: tm+mt
source-wordcount: '2567'
ht-degree: 2%

---


# 게재 모니터링{#monitoring-a-delivery}

배달 **대시보드는** 메시지를 보내는 동안 발생하는 전달 및 최종 문제를 모니터링하기 위한 핵심입니다.

**관련 항목:**

* [게재 실패 이해](../../delivery/using/understanding-delivery-failures.md)
* [격리 관리 이해](../../delivery/using/understanding-quarantine-management.md)
* [전달 모범 사례](../../delivery/using/delivery-best-practices.md)
* [게재 기능 관리](../../delivery/using/about-deliverability.md)

## 배달 대시보드 {#delivery-dashboard}

게재에 대한 정보를 보려면 해당 정보를 편집하고 대시보드를 보고 사용 가능한 탭을 클릭합니다.

배달을 보낸 후에는 탭 내용을 더 이상 변경할 수 없습니다.

![](assets/s_ncs_user_del_details.png)

### 게재 요약 {#delivery-summary}

이 **[!UICONTROL Summary]** 탭에는 전달 특성이 포함되어 있습니다.배달 상태, 사용된 채널, 보낸 사람 정보, 제목, 실행에 관한 정보 자세한 내용은 보낸 [메시지 수를 참조하십시오](#number-of-messages-sent).

이 **[!UICONTROL reports]** 링크를 사용하면 배달 작업과 관련된 보고서 세트를 볼 수 있습니다.일반 전달 보고서, 세부 보고서, 전달 보고서, 실패한 메시지 배포, 시작 비율, 클릭 수 및 거래 등 이 탭의 내용은 사용자의 요구 사항에 따라 구성할 수 있습니다. 자세한 정보는 [이 섹션](../../reporting/using/delivery-reports.md)을 참조하십시오.

### 배달 로그 및 내역 {#delivery-logs-and-history}

이 **[!UICONTROL Delivery]** 탭에는 이 배달의 발생 내역이 표시됩니다. 여기에는 전송 로그(예: 전송된 메시지 목록 및 해당 상태 및 관련 메시지)가 포함됩니다.

배달의 경우(예: 배달 실패 또는 격리 주소가 있는 받는 사람만 표시)할 수 있습니다. 이렇게 하려면 **[!UICONTROL Filters]** 단추를 클릭하고 선택합니다 **[!UICONTROL By state]**. 그런 다음 드롭다운 목록에서 상태를 선택합니다.

![](assets/s_ncs_user_delivery_delivery_tab.png)

다양한 상태가 [이 페이지에 나열됩니다](#delivery-statuses).

>[!NOTE]
>
>이 **[!UICONTROL Display the mirror page for this message...]** 링크를 사용하면 새 창의 목록에서 선택한 배달 컨텐츠의 미러 페이지를 볼 수 있습니다. 미러 페이지는 HTML 컨텐츠가 정의된 게재에만 사용할 수 있습니다. 자세한 내용은 미러 페이지 [생성을 참조하십시오](../../delivery/using/sending-messages.md#generating-the-mirror-page).

### Tracking logs {#tracking-logs}

이 게재의 추적 내역이 **[!UICONTROL Tracking]** 탭에 나열됩니다. 이 탭에는 전송된 메시지(예: Adobe Campaign에 의한 추적이 적용되는 모든 URL)에 대한 추적 데이터가 표시됩니다. 추적 데이터는 시간별로 업데이트됩니다.

>[!NOTE]
>
>게재에 대한 추적이 활성화되지 않으면 이 탭이 표시되지 않습니다.

배달 마법사의 적절한 단계에서 추적 구성이 수행됩니다. 추적된 링크 [를 구성하는 방법을 참조하십시오](../../delivery/using/how-to-configure-tracked-links.md).

**[!UICONTROL Tracking]** 데이터는 배달 보고서에서 해석됩니다. [이 섹션](../../reporting/using/delivery-reports.md)을 참조하십시오.

![](assets/s_ncs_user_delivery_tracking_tab.png)

### 배달 감사 {#delivery-audit-}

이 **[!UICONTROL Audit]** 탭에는 배달 로그와 교정에 대한 모든 메시지가 포함되어 있습니다. 이 **[!UICONTROL Refresh]** 단추를 사용하면 데이터를 업데이트할 수 있습니다. 이 **[!UICONTROL Filters]** 단추를 사용하여 데이터에 대한 필터를 정의합니다.

특수 아이콘을 사용하여 오류 또는 경고를 식별할 수 있습니다. 전달 [분석을 참조하십시오](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).

하위 **[!UICONTROL Proofs]** 탭에서는 전송된 증명 목록을 볼 수 있습니다.

![](assets/s_ncs_user_delivery_log_tab.png)

표시할 열을 선택하여 이 창(및 탭 **[!UICONTROL Delivery]** 과 **[!UICONTROL Tracking]** 탭)에 표시되는 정보를 수정할 수 있습니다. 이렇게 하려면 오른쪽 아래에 있는 **[!UICONTROL Configure list]** 아이콘을 클릭합니다. 목록 표시 구성에 대한 자세한 내용은 [이 섹션을 참조하십시오](../../platform/using/adobe-campaign-workspace.md#configuring-lists).

### 배달 대시보드 동기화 {#delivery-dashboard-synchronization}

배달 대시보드에서 처리된 메시지 및 배달 로그를 확인하여 배달이 성공적으로 전송되었는지 확인합니다.

일부 지표 또는 상태는 정확하지 않거나 최신 상태가 아닐 수 있습니다. 이 문제는 다음 솔루션으로 해결될 수 있습니다.

* 배달 상태가 잘못된 경우, 이 배달에 필요한 모든 승인이 완료되었는지 또는 **[!UICONTROL operationMgt]** 및 워크플로우가 오류 없이 실행 중인지 **[!UICONTROL deliveryMgt]** 확인하십시오. 이것은 전송 인스턴스에서 구성되지 않은 친화성을 사용한 배달 때문일 수도 있습니다.
* 배달 지표가 여전히 0이고 중간 소싱 구성인 경우 **[!UICONTROL Mid-sourcing (delivery counters)]** 기술 워크플로우를 확인하십시오. 상태가 아닐 경우 시작합니다 **[!UICONTROL Started]**. 그런 다음 Adobe Campaign 탐색기에서 관련 배달을 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Actions]** > 을 선택하여 지표를 재계산할 수 있습니다 **[!UICONTROL Recompute delivery and tracking indicators]**. For more information on tracking indicators, refer to this [section](../../reporting/using/delivery-reports.md#tracking-indicators).
* 배달 카운터가 배달과 일치하지 않는 경우, Adobe Campaign 탐색기에서 관련 전달을 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Actions]** > 을 선택하여 다시 동기화하여 지표 **[!UICONTROL Recompute delivery and tracking indicators]** 를 재계산해 보십시오. For more information on tracking indicators, refer to this [section](../../reporting/using/delivery-reports.md#tracking-indicators).
* 중간 소싱 배포에 대한 배달 카운터가 최신 상태가 아닌 경우 **[!UICONTROL Mid-Sourcing (Delivery counters)]** 기술 워크플로우가 실행 중인지 확인하십시오. 자세한 정보는 이 [페이지](../../installation/using/mid-sourcing-deployment.md)를 참조하십시오.

배달 대시보드를 통해 다른 보고서로 배달 내용을 추적할 수도 있습니다. 자세한 정보는 이 [섹션](../../reporting/using/delivery-reports.md)을 참조하십시오.

## 성능 문제 {#performance-issues}

### 검사 목록 {#checklist-}

배달 실적이 나쁜 경우 다음을 확인할 수 있습니다.

* **배달**&#x200B;크기:큰 배달은 완료하는 데 더 오래 걸릴 수 있습니다. MTA 하위는 대부분의 인스턴스에서 작동하는 기본 배치 크기를 처리하도록 구성되지만 배달이 지속적으로 느려질 때 확인해야 합니다.
* **배달**&#x200B;대상:배달 성능 제한은 다시 시도 구성에 따라 처리되는 소프트 바운스 오류로 인해 영향을 받습니다. 오류 수가 많을수록 더 많은 재시도가 필요합니다.
* **전체 플랫폼 로드**:여러 개의 큰 배달이 전송되면 전체 플랫폼에 영향을 줄 수 있습니다. 또한 IP 명성과 전달 가능성 문제를 확인할 수 있습니다. 자세한 내용은 Adobe Campaign 전달 [가능성 우수 사례 가이드](../../delivery/using/deliverability-key-points.md) 및 [이 페이지를 참조하십시오](../../delivery/using/about-deliverability.md).

플랫폼 및 데이터베이스 유지 관리도 배달 전송 성능에 영향을 줄 수 있습니다. For more on this, refer to [this page](../../production/using/database-performances.md).

### 느린 전달 {#slow-deliveries}

이 **[!UICONTROL Send]** 단추를 클릭하면 배달이 평소보다 오래 걸리는 것 같습니다. 이 문제는 다음과 같은 여러 요소로 인해 발생할 수 있습니다.

* 일부 이메일 공급자가 사용자의 IP 주소를 차단 목록에 추가했을 수 있습니다. 이 경우 브로드로그를 확인하고 [이 섹션을 참조하십시오](../../delivery/using/about-deliverability.md).
* 배달이 너무 커서 빠르게 처리할 수 없을 수도 있고, 높은 JavaScript 개인화를 통해 또는 배달 무게가 60KB 이상인 경우 이러한 문제가 발생할 수 있습니다. 콘텐츠 가이드라인에 대한 자세한 내용은 Adobe Campaign [전달](../../delivery/using/delivery-best-practices.md) 모범 사례를 참조하십시오.
* Adobe Campaign MTA 내에서 조절이 발생했을 수 있습니다. 이 문제는 다음과 같습니다.

   * 보류 중인 메시지(**[!UICONTROL quotas met]** 메시지):Campaign에 정의된 선언적 MX 규칙으로 선언된 할당량이 충족되었습니다. 이 메시지에 대한 자세한 내용은 [이 페이지를 참조하십시오](../../delivery/using/deliverability-faq.md) . MX 규칙에 대한 자세한 내용은 [이 페이지를 참조하십시오](../../delivery/using/technical-recommendations.md#mx-rules).
   * 보류 중인 메시지(**[!UICONTROL dynamic flow control]** 메시지):캠페인 MTA가 지정된 ISP에 대한 메시지를 전달하려고 할 때 오류가 발생하여 오류 밀도가 너무 커 잠재적 차단 목록에 직면할 수 있습니다.

* 시스템 문제로 인해 서버가 서로 상호 작용할 수 없습니다.이렇게 하면 전송 프로세스가 느려질 수 있습니다. 예를 들어 개인화 데이터를 가져오는 과정에서 Campaign에 영향을 줄 수 있는 메모리 또는 리소스 문제가 없는지 서버를 확인하십시오.

### 성능 모범 사례 {#best-practices-performance}

* 임시 테이블을 유지하고 성능에 영향을 주므로 인스턴스에 배달을 실패한 상태로 유지하지 마십시오.

* 더 이상 필요하지 않은 배달을 제거합니다.

* 주소 품질을 유지하기 위해 최근 12개월 동안 비활성 수신자를 데이터베이스에서 제거해야 합니다.

* 큰 배달은 함께 예약하지 마십시오. 이 부하를 시스템에 균일하게 분산시키는 데에는 5-10분의 차이가 있다. 우수 성과를 확보하기 위해 팀의 다른 구성원과 배달 예약을 조정합니다. 마케팅 서버가 동시에 여러 가지 작업을 처리할 때 성능이 저하될 수 있습니다.

* 이메일 크기를 최대한 낮게 유지하십시오. 권장되는 최대 이메일 크기는 약 35KB입니다. 이메일 배달의 크기는 전송 서버에서 특정 양을 생성합니다.

* 100만 명 이상의 수신자에게 배달하는 것과 같은 큰 배달은 전송 대기열에 공간이 필요합니다. 이 자체만으로는 서버에 문제가 되지 않지만 수십 개의 다른 큰 배달과 함께 동시에 발송되는 경우 전송 지연을 유발할 수 있습니다.

* 이메일의 개인화는 각 수신자에 대한 데이터를 데이터베이스에서 가져옵니다. 개인화 요소가 많은 경우 전달을 준비하는 데 필요한 데이터의 양이 증가합니다.

* 색인 주소. 응용 프로그램에 사용되는 SQL 쿼리의 성능을 최적화하기 위해 데이터 스키마의 기본 요소에서 인덱스를 선언할 수 있습니다.

>[!NOTE]
>
>ISP는 비활성 기간 후 주소를 비활성화합니다. 바운스된 메시지는 이 새로운 상태에 대해 알려주기 위해 발신자에게 전송됩니다.

## 배달 상태 {#delivery-statuses}

배달을 보내는 동안 배달 대시보드에서 다음 상태가 될 수 있습니다.

<table> 
 <thead> 
  <tr> 
   <th> 상태<br /> </th> 
   <th> 정의 및 솔루션<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 해당 사항 없음<br /> </td> 
   <td> 배달은 서버(MTA)에서 고려했지만 처리되지 않았습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 무시됨<br /> </td> 
   <td> 주소가 잘못되어 배달이 받는 사람에게 전송되지 않았습니다. 차단 목록에 추가되었거나, 격리되었거나, 제공되지 않으며, 복제되었습니다. <br /> </td> 
  </tr> 
  <tr> 
   <td> 전송<br /> </td> 
   <td> 배달이 메시지 제공자에게 올바르게 전송되었지만 받는 사람이 메시지를 반드시 수신하지는 않았습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 실패<br /> </td> 
   <td> 잘못된 주소 또는 전체 받은 편지함으로 인해 배달이 받는 사람에게 도달할 수 없습니다. 또한 스키마를 배달 매핑과 일치하지 않을 때 오류를 생성할 수 있으므로 개인화 블록 문제를 연결할 수도 있습니다. 실패 <a href="#failed-status" target="_blank">상태 참조</a><br /> </td> 
  </tr> 
  <tr> 
   <td> 서비스 제공업체에서 고려<br /> </td> 
   <td> SMS 서비스 제공업체가 배달을 받았습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 모바일에서 수신<br /> </td> 
   <td> 수신자는 모바일 디바이스에서 SMS를 받았습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 보류 중<br /> </td> 
   <td> 배달을 보낼 준비가 되었으며 배달 서버(MTA)에서 처리할 예정입니다. 보류 <a href="#pending-status" target="_blank">상태를 참조하십시오</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> 배달이 취소되었습니다.<br /> </td> 
   <td> 교환원이 배달을 취소했다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 준비<br /> </td> 
   <td> 모바일 채널과 같은 외부 커넥터에만 사용되는 중간 상태입니다. '보류 중' 상태를 따르고 다음 상태를 결정하는 외부 커넥터입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 서비스 공급자에게 전송<br /> </td> 
   <td> 배달은 SMS 서비스 제공업체에 보내졌지만 아직 받지 못했습니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

Adobe Campaign 이메일의 전달 가능성을 최적화하는 방법에 대한 자세한 내용은 Adobe Campaign 전달 [가능성 우수 사례 가이드](../../delivery/using/deliverability-key-points.md) 및 [이 페이지를 참조하십시오](../../delivery/using/about-deliverability.md).

### 보류 중 상태 {#pending-status}

배달을 확인한 후 배달 상태를 확인할 수 있습니다 **[!UICONTROL Pending]**. 이 상태는 실행 프로세스가 일부 리소스의 가용성을 기다리고 있음을 의미합니다.

우선 **[!UICONTROL Pending]** 상태는 배달을 예약했으며 지정된 날짜까지 보류 중임을 의미합니다. For more on this, refer to the [Delivery scheduling](../../delivery/using/steps-sending-the-delivery.md#scheduling-the-delivery-sending) section.

배달이 전송되지 않고 해당 상태가 남아 있는 경우 **[!UICONTROL Pending]**&#x200B;는 다음 작업의 결과일 수 있습니다.

* 배달 서버에서 모듈 및 프로세스를 실행하고 이메일 전송을 관리하는 MTA(메시지 전송 에이전트)가 시작되지 않았거나 다시 시작해야 할 수 있습니다. 이 확인란을 선택하고 필요한 경우 모듈을 시작하려면 다음 단계를 수행하십시오.

   * MTA 서버에서 `mta@<instance>` 모듈이 시작되었는지 확인합니다.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (X.Y.Z YY.R build nnnn@SHA1) of DD/MM/YYYY
   [...]
   mta@<INSTANCENAME> (9268) - 23.0 Mb
   [...]
   ```

   * MTA가 목록에 없으면 다음 명령으로 시작하십시오.

   ```
   nlserver start mta@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >인스턴스 `<INSTANCENAME>` (프로덕션, 개발 등)의 이름으로 대체합니다. 인스턴스 이름은 구성 파일을 통해 식별됩니다. `[path of application]nl6/conf/config-<INSTANCENAME>.xml`

* 전송 서버에서 구성되지 않은 친화성을 사용할 수 있습니다. 이 경우 트래픽 관리(IP 친화성)의 구성을 확인하고 이 **[!UICONTROL Managing affinities with IP addresses]** 필드를 사용하여 관련성을 관리하는 MTA에 제공을 연결합니다. For more information on affinities, refer to [this section](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters).
* 게재 준비 보류 상태일 때 너무 많은 캠페인이 실행 중일 수 있으므로 게재의 상태 업데이트를 차단합니다. 이 문제를 해결하려면 로 이동하여 값 **[!UICONTROL Options]** 을 **[!UICONTROL NmsOperation_LimitConcurrency]** 높입니다(기본값은 10). 이 특정 옵션에 할당된 값보다 더 많은 캠페인을 실행하지 마십시오.

### 실패 상태 {#failed-status}

이메일 배달 상태가 개인화 블록 **[!UICONTROL Failed]**&#x200B;의 문제에 연결될 수 있습니다. 배급의 개인화 블록은 스키마가 배달 매핑과 일치하지 않을 때 오류를 생성할 수 있습니다.

배달 로그는 배달이 실패한 이유를 확인하는 데 중요합니다. 배달 로그에서 감지할 수 있는 오류는 다음과 같습니다.

* 받는 사람 메시지에 &quot;연결할 수 없음&quot; 오류가 표시되는 경우: **스크립트 &#39;content htmlContent&#39; 줄 X를 컴파일하는 동안 오류가 발생했습니다.`[table]`가 정의되지 않았습니다. JavaScript:스크립트 &#39;content htmlContent**&#39;를 평가하는 동안 오류가 발생했습니다. 이 문제의 원인은 업스트림 타깃팅 또는 게재 대상 매핑에서 정의되거나 매핑되지 않은 테이블이나 필드를 호출하려고 시도하는 HTML 내의 개인화입니다.

   이 문제를 해결하려면 워크플로우 및 전달 컨텐츠를 검토하여 특정 개인화가 해당 테이블을 호출하려고 시도하는 내용과 테이블을 매핑할 수 있는지 여부를 구체적으로 결정해야 합니다. 여기에서 HTML에서 이 테이블에 대한 호출을 제거하거나 배달에 대한 매핑을 수정하는 것이 해결 경로가 됩니다.

* 중간 소싱 배포 모델에서 다음 메시지가 배달 로그에 나타날 수 있습니다. **중간 소싱 서버에서 &#39;AppendDeliveryPart&#39; 메서드를 호출하는 동안 오류가 발생했습니다.&#39;서버에 통신 오류가 발생했습니다.제대로 구성되어 있는지 확인하십시오. 코드 HTTP 408 &#39;서비스를 일시적으로 사용할 수 없습니다&#39;**.

   원인은 성능 문제와 연결되어 있습니다. 즉, 마케팅 인스턴스가 데이터를 중간 소싱 서버로 보내기 전에 데이터 작성에 너무 많은 시간을 소비합니다.

   이 문제를 해결하려면 데이터베이스에 진공청소기를 다시 색인화하는 것이 좋습니다. For more information on database maintenance, refer to [this section](../../production/using/recommendations.md).

   또한 예약된 활동이 있는 모든 워크플로우와 실패한 상태의 모든 워크플로우도 다시 시작해야 합니다. [이 섹션](../../workflow/using/scheduler.md)을 참조하십시오.

* 배달이 실패하면 배달 로그에 다음 오류가 표시될 수 있습니다. **DLV-XXXX 준비된 메시지 수(123)가 보낼 메시지 수(111)보다 큽니다. 지원 센터에 문의하십시오.**

   일반적으로 이 오류는 이메일 내에 받는 사람에 대해 값이 두 개 이상인 개인화 필드 또는 블록이 있음을 의미합니다. 개인화 블록을 사용하고 있으며 특정 수신자에 대해 둘 이상의 레코드를 가져오는 중입니다.

   이 문제를 해결하려면 사용된 개인화 데이터를 확인한 다음 해당 필드에 대해 둘 이상의 항목이 있는 수신자의 대상을 확인하십시오. 배달 활동 전에 타깃팅 워크플로우에서 **[!UICONTROL Deduplication]** 활동을 사용하여 한 번에 하나의 개인화 필드만 있는지 확인할 수도 있습니다. For more information on deduplication, refer to [this page](../../workflow/using/deduplication.md).

* 일부 배달은 &quot;연결할 수 없음&quot; 오류로 실패할 수 있습니다.&quot;인바운드 이메일 바운스(규칙 &#39;자동 응답&#39;이 이 바운스와 일치함). 즉, 배달에 성공했지만 Adobe Campaign은 &#39;자동 회신&#39; 인바운드 이메일 규칙과 일치하는 수신자(&quot;부재 중&quot; 응답)로부터 자동 회신을 수신했습니다. 자동 회신 이메일은 Adobe Campaign에서 무시되며 수신자의 주소는 격리조치에 보내지 않습니다.

**관련 항목:**

* [배달 로그 및 내역](#delivery-logs-and-history)
* [게재 실패 이해](../../delivery/using/understanding-delivery-failures.md)
* [게재 실패 유형 및 이유](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)

## Number of messages sent {#number-of-messages-sent}

트리 노드를 통해 배달 목록에서 전달에 액세스할 수 **[!UICONTROL Campaign Management > Deliveries]** 있습니다.

기본적으로 배달 목록에는 선택한 노드에서 생성된 게재의 이름과 상태가 포함됩니다. 전송, 처리 및 전송될 메시지 수도 표시됩니다.

* 분석 후 및 전달 전 타깃팅된 수신자 수에 해당하는 **[!UICONTROL Messages to send]** 수입니다.
* 열의 메시지 수는 **[!UICONTROL Success]** 서버가 보내고 받는 메시지 수에 해당합니다.
* 메시지 수는 받은 메시지 수와 오류가 있는 메시지 수에 해당합니다. **[!UICONTROL Processed]**

배달 대시보드를 통해 보낸 메시지 수를 추적할 수 있습니다.

>[!NOTE]
>
>큰 배달의 경우 이러한 값을 업데이트할 수 있습니다. 이렇게 하려면 해당 배달을 선택한 다음 마우스 오른쪽 단추로 클릭합니다. 선택한 **[!UICONTROL Action > Recompute delivery and tracking indicators...]** 다음 마법사를 사용하여 이 정보를 업데이트합니다.

## 예약된 배달 {#scheduled-deliveries-}

게재가 정확한 예약된 날짜에 실행되지 않으면 서버 표준 시간대 간의 차이와 관련이 있을 수 있습니다. 중간 소싱 인스턴스와 프로덕션 인스턴스는 다른 시간대에 있을 수 있습니다.

예를 들어, 중간 소싱 인스턴스가 브리즈번 시간대와 생산 인스턴스가 다윈 시간대에만 있는 경우, 두 시간대는 서로 30분 정도 떨어져 있고 감사 기록에서 납품이 11:56에 생산될 예정이라면 중간으로 예정된 동일한 배달이 30분 차이가 있는 12:26이 될 것임을 분명히 알 수 있습니다.
