---
solution: Campaign Classic
product: campaign
title: ISP 중단 후 바운스 자격 업데이트
description: ISP 중단 후 바운스 자격 조건을 업데이트하는 방법을 알아봅니다.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
hidefromtoc: true
exl-id: 34be23f7-17fa-475e-9663-2e353d76b172
translation-type: tm+mt
source-git-commit: ad7f0725a5ce1dea9b5b3ab236c839a816b29382
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 4%

---

# ISP 중단 후 바운스 자격 업데이트 {#update-bounce-qualification.md}

## 컨텍스트

ISP가 중단되는 경우, Campaign을 통해 전송된 이메일은 수신자에게 성공적으로 배달될 수 없습니다.이러한 이메일은 바운스로 잘못 표시됩니다.

2021년 4월 26일, Apple의 글로벌 문제로 인해 올바른 Apple 이메일 주소로 전송되는 일부 이메일 메시지가 바운스 다음 응답을 포함한 Apple 서버의 잘못된 이메일 주소로 반송되면서 잘못 반송되었습니다.*&quot;550 5.1.1 <email address>:사용자 조회 성공했지만 사용자 레코드를 찾을 수 없습니다.&quot;*이 문제는 4월 26일에 발생했으며 7시 - 동부 시간 오후 1시까지입니다.

>[!NOTE]
>
>[이 페이지](https://www.apple.com/support/systemstatus/)에서 Apple 시스템 상태 대시보드를 확인할 수 있습니다.

표준 바운스 처리 로직마다 Adobe Campaign은 **[!UICONTROL Quarantine]**&#x200B;의 **[!UICONTROL Status]** 설정으로 이러한 받는 사람을 격리 목록에 자동으로 추가했습니다. 이 문제를 해결하려면 이러한 받는 사람을 찾아 제거하거나 해당 수신자의 **[!UICONTROL Status]**&#x200B;을 **[!UICONTROL Valid]**&#x200B;으로 변경하여 야간 정리 워크플로우가 해당 수신자를 제거하도록 Campaign에서 격리 테이블을 업데이트해야 합니다.

이 문제로 영향을 받은 수신자를 찾거나 다른 ISP에서 이 문제가 다시 발생하는 경우 아래 지침을 참조하십시오.

## 업데이트 프로세스

격리 테이블에서 쿼리를 실행하여 서비스 중단에 영향을 받을 수 있는 모든 Apple 받는 사람(@icloud.com, @me.com, @mac.com 포함)을 필터링하면 격리 목록에서 제거되고 향후 캠페인 이메일 전달에 포함될 수 있습니다.

사고 기간에 따라 이 쿼리에 대한 권장 지침은 아래에 있습니다.

>[!IMPORTANT]
>
>이러한 날짜/시간은 동부 표준 시간대(EST)를 기반으로 합니다. 인스턴스의 표준 시간대를 조정하십시오.

* 격리 목록의 **[!UICONTROL Error text]** 필드에 SMTP 바운스 응답 정보가 있는 캠페인 인스턴스의 경우:

   * **오류 텍스트(격리 텍스트)** 에 &quot;사용자 조회 성공했지만 사용자 레코드를 찾을 수 없음&quot; 및  **오류 텍스트(격리 텍스트)** 에 &quot;support.apple.com&quot; **
   * **4/26/2021 AM** 의 업데이트 상태(@lastModified)
   * **4/26/2021 PM** 에 또는 그 전에 상태 업데이트(@lastModified)

* 격리 목록의 **[!UICONTROL Error text]** 필드에 인바운드 이메일 규칙 정보가 있는 캠페인 인스턴스의 경우:

   * **오류 텍스트(격리 텍스트)** 에 &quot;Momain_Code10_InvalidRecipient&quot;가 포함되어 있습니다.
   * **이메일 도메인(@domain)** 이 icloud.com&quot; OR 이메일 도메인(@domain)이 me.com&quot; OR 이메일 도메인(@domain)과 mac.com과 같습니다.&quot;
   * **4/26/2021 AM** 의 업데이트 상태(@lastModified)
   * **4/26/2021 PM** 에 또는 그 전에 상태 업데이트(@lastModified)

영향을 받는 받는 받는 받는 받는 사람 목록이 있는 경우 **[!UICONTROL Valid]** 상태로 설정하여 **[!UICONTROL Database cleanup]** 작업 과정에 의해 격리 목록에서 제거하거나 표에서 해당 받는 사람 목록을 삭제합니다.

**관련 항목:**
* [배달 오류 이해](../../delivery/using/understanding-delivery-failures.md)
* [반송 메일 조건](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification)
