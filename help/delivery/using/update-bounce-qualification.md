---
product: campaign
title: Apple 2021 중단 후 바운스 자격 업데이트
description: Apple 2021 중단 후 바운스 자격을 업데이트하는 방법을 알아봅니다
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Deliverability
exl-id: 34be23f7-17fa-475e-9663-2e353d76b172
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 1%

---

# Apple 중단 후 잘못된 하드 바운스 업데이트 {#update-bounce-qualification.md}

## 컨텍스트

2021년 4월 26일에 Apple의 글로벌 문제로 인해 유효한 Apple 이메일 주소로 전송된 일부 이메일 메시지가 바운스 다음 응답과 함께 Apple 서버에서 잘못된 이메일 주소로 잘못 하드 바운스되었습니다. &quot;550 5.1.1 &#39;이메일 주소&#39;: 사용자 조회 성공했지만 사용자 레코드를 찾을 수 없음.&quot;

이 문제는 4월 26일에 발생했으며, 오전 7시~오후 1시(EST) 사이에 지속되었습니다.

>[!NOTE]
>
>에서 Apple 시스템 상태 대시보드를 확인할 수 있습니다. [이 페이지](https://www.apple.com/support/systemstatus/).

ISP가 중단되는 경우 Campaign을 통해 보낸 이메일이 수신자에게 정상적으로 전달될 수 없습니다. 이러한 이메일은 바운스로 잘못 표시됩니다.

표준 바운스 처리 논리에 따라 Adobe Campaign은 다음과 같이 격리 목록에 이러한 수신자를 자동으로 추가했습니다. **[!UICONTROL Status]** 설정 **[!UICONTROL Quarantine]**. 이 문제를 해결하려면 이러한 수신자를 찾아 제거하거나 수신자를 변경하여 Campaign에서 격리 테이블을 업데이트해야 합니다 **[!UICONTROL Status]** 끝 **[!UICONTROL Valid]** 따라서 야간 정리 워크플로우에서 제거됩니다.

이 문제의 영향을 받은 수신자를 찾으려면 또는 다른 ISP에서 이 문제가 다시 발생하는 경우 아래 지침을 참조하십시오.

## 업데이트할 프로세스

격리 테이블에서 쿼리를 실행하여 중단의 영향을 받을 수 있는 모든 Apple 수신자(예: @icloud.com, @me.com, @mac.com)를 필터링해야 격리 목록에서 제거할 수 있으며 향후 Campaign 이메일 게재에 포함될 수 있습니다.

인시던트의 일정에 따라, 아래는 이 쿼리에 대한 권장 지침입니다.

>[!IMPORTANT]
>
>이 날짜/시간은 동부 표준 시간대(EST)를 기반으로 합니다. 인스턴스의 시간대를 조정하십시오.

* 에 SMTP 바운스 응답 정보가 있는 캠페인 인스턴스 **[!UICONTROL Error text]** 격리 목록의 필드:

   * **오류 텍스트(격리 텍스트)** 에는 &quot;사용자 조회 성공했지만 사용자 레코드를 찾을 수 없음&quot;이 포함되어 있고 **오류 텍스트(격리 텍스트)** &quot;support.apple.com&quot;을 포함합니다.
   * **업데이트 상태(@lastModified)** 2021년 4월 26일 또는 그 이후 07:00:오전 00
   * **업데이트 상태(@lastModified)** 2021년 4월 26일 또는 이전 01:00:오후

* 에 인바운드 이메일 규칙 정보가 있는 캠페인 인스턴스 **[!UICONTROL Error text]** 격리 목록의 필드:

   * **오류 텍스트(격리 텍스트)** 에는 &quot;Momen_Code10_InvalidRecipient&quot;가 포함되어 있습니다.
   * **이메일 도메인(@domain)** icloud.com과 같음 또는 **이메일 도메인(@domain)** me.com과 같음 또는 **이메일 도메인(@domain)** mac.com과 같음
   * **업데이트 상태(@lastModified)** 2021년 4월 26일 또는 그 이후 07:00:오전 00
   * **업데이트 상태(@lastModified)** 2021년 4월 26일 또는 이전 01:00:오후

영향을 받는 수신자 목록이 있으면 다음 상태로 설정할 수 있습니다. **[!UICONTROL Valid]** 따라서 다음을 통해 격리 목록에서 제거됩니다. **[!UICONTROL Database cleanup]** 워크플로우 또는 테이블에서 삭제하기만 하면 됩니다.

**관련 항목:**
* [게재 실패 이해](understanding-delivery-failures.md)
* [반송 메일 조건](understanding-delivery-failures.md#bounce-mail-qualification)
