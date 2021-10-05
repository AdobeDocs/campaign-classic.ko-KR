---
product: campaign
title: ISP 중단 후 바운스 자격 업데이트
description: ISP 중단 후 반송 조건을 업데이트하는 방법을 알아봅니다.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
exl-id: 34be23f7-17fa-475e-9663-2e353d76b172
source-git-commit: cee019432c64eaaefac86a27b731355242fd1555
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 3%

---

# Apple 중단 후 잘못된 하드 바운스 업데이트 {#update-bounce-qualification.md}

![](../../assets/common.svg)

## 컨텍스트

2021년 4월 26일, Apple의 글로벌 문제로 인해 유효한 Apple 이메일 주소로 전송된 일부 이메일 메시지가 바운스 다음 응답이 있는 Apple 서버의 잘못된 이메일 주소로 잘못 바운스되었습니다.  &quot;550 5.1.1 &#39;이메일 주소&#39;: 사용자 조회 성공했지만 사용자 레코드가 없습니다.&quot;

이 문제는 4/26 오전 7시 - 오후 1시에 발생했습니다.

>[!NOTE]
>
>[이 페이지에서 Apple 시스템 상태 대시보드를 확인할 수 있습니다](https://www.apple.com/support/systemstatus/).

ISP가 중단되는 경우, Campaign을 통해 전송된 이메일을 수신자에게 전달할 수 없습니다. 이 이메일은 반송 행위로 잘못 표시될 것입니다.

표준 바운스 처리 논리에 따라 Adobe Campaign은 **[!UICONTROL Quarantine]** 의 **[!UICONTROL Status]** 설정을 사용하여 이러한 수신자를 격리 목록에 자동으로 추가했습니다. 이 문제를 해결하려면 야간 정리 워크플로우가 제거할 수 있도록 이러한 수신자를 찾아 제거하거나 **[!UICONTROL Status]** 을 **[!UICONTROL Valid]**(으)로 변경하여 Campaign에서 격리 테이블을 업데이트해야 합니다.

이 문제의 영향을 받은 수신자를 찾거나 다른 ISP에서 이 문제가 다시 발생하는 경우 아래 지침을 참조하십시오.

## 업데이트할 프로세스

격리 테이블에서 쿼리를 실행하여 중단의 영향을 받을 수 있는 모든 Apple 수신자(@icloud.com, @me.com, @mac.com)를 필터링함으로써 격리 목록에서 제거하고 향후 Campaign 이메일 게재에 포함할 수 있습니다.

사고 기간에 따라 이 쿼리에 대한 권장 지침은 아래에 나와 있습니다.

>[!IMPORTANT]
>
>이 날짜/시간은 동부 표준 시간대(EST)를 기반으로 합니다. 인스턴스의 시간대에 맞게 조정하십시오.

* 격리 목록의 **[!UICONTROL Error text]** 필드에 SMTP 바운스 응답 정보가 있는 Campaign 인스턴스의 경우:

   * **오류 텍스트(격리 텍스트)** 에 &quot;사용자 조회 성공했지만 사용자 레코드를 찾을 수 없음&quot;이 포함되어 있으며,  **오류 텍스트(격리 텍스트)** 에 &quot;support.apple.com&quot;이 포함되어 있습니다
   * **4/26/2021 07** 오전 :00:00시 또는 그 이후의 업데이트 상태(@lastModified)
   * **4/26/2021 01** 일 또는 그 전:00: 오후 업데이트 상태(@lastModified)

* 격리 목록의 **[!UICONTROL Error text]** 필드에 인바운드 전자 메일 규칙 정보가 있는 Campaign 인스턴스의 경우:

   * **오류 텍스트(격리 텍스트)** 에 &quot;Momen_Code10_InvalidRecipient&quot;가 포함되어 있습니다.
   * **이메일 도메인(@domain)** icloud.com 또는  **이메일 도메인(@domain)** me.com 또는  **이메일 도메인(@domain)** 과 mac.com과 같음
   * **4/26/2021 07** 오전 :00:00시 또는 그 이후의 업데이트 상태(@lastModified)
   * **4/26/2021 01** 일 또는 그 전:00: 오후 업데이트 상태(@lastModified)

영향을 받는 수신자 목록이 있으면 **[!UICONTROL Valid]** 상태로 설정하여 **[!UICONTROL Database cleanup]** 워크플로에 의해 격리 목록에서 제거하거나 테이블에서 삭제할 수 있습니다.

**관련 항목:**
* [게재 실패 이해](understanding-delivery-failures.md)
* [반송 메일 조건](understanding-delivery-failures.md#bounce-mail-qualification)
