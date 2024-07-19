---
product: campaign
title: Apple 2021 중단 후 바운스 자격 업데이트
description: Apple 2021 중단 후 바운스 자격을 업데이트하는 방법을 알아봅니다
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Deliverability
exl-id: 34be23f7-17fa-475e-9663-2e353d76b172
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# Apple 중단 후 잘못된 하드 바운스 업데이트 {#update-bounce-qualification.md}

## 컨텍스트

2021년 4월 26일에 Apple의 글로벌 문제로 인해 유효한 Apple 이메일 주소로 전송된 일부 이메일 메시지가 바운스 다음 응답과 함께 Apple 서버에서 잘못된 이메일 주소로 잘못 하드 바운스되었습니다. &quot;550 5.1.1 &#39;이메일 주소&#39;: 사용자 조회 성공했지만 사용자 레코드를 찾을 수 없음.&quot;

이 문제는 4월 26일에 발생했으며, 오전 7시~오후 1시(EST) 사이에 지속되었습니다.

>[!NOTE]
>
>[이 페이지](https://www.apple.com/support/systemstatus/)에서 Apple 시스템 상태 대시보드를 확인할 수 있습니다.

ISP가 중단되는 경우 Campaign을 통해 보낸 이메일이 수신자에게 정상적으로 전달될 수 없습니다. 이러한 이메일은 바운스로 잘못 표시됩니다.

표준 바운스 처리 논리에 따라 Adobe Campaign은 **[!UICONTROL Status]** 설정이 **[!UICONTROL Quarantine]**&#x200B;인 격리 목록에 이 수신자를 자동으로 추가했습니다. 이 문제를 해결하려면 야간 정리 워크플로우에서 해당 수신자를 찾아 제거하거나 **[!UICONTROL Status]**&#x200B;을(를) **[!UICONTROL Valid]**(으)로 변경하여 Campaign에서 격리 테이블을 업데이트해야 합니다.

이 문제의 영향을 받은 수신자를 찾으려면 또는 다른 ISP에서 이 문제가 다시 발생하는 경우 아래 지침을 참조하십시오.

## 업데이트할 프로세스

격리 테이블에서 쿼리를 실행하여 중단의 영향을 받을 수 있는 모든 Apple 수신자(예: @icloud.com, @me.com, @mac.com)를 필터링해야 격리 목록에서 제거할 수 있으며 향후 Campaign 이메일 게재에 포함될 수 있습니다.

인시던트의 일정에 따라, 아래는 이 쿼리에 대한 권장 지침입니다.

>[!IMPORTANT]
>
>이 날짜/시간은 동부 표준 시간대(EST)를 기반으로 합니다. 인스턴스의 시간대를 조정하십시오.

* 격리 목록의 **[!UICONTROL Error text]** 필드에 SMTP 바운스 응답 정보가 있는 캠페인 인스턴스의 경우:

   * **오류 텍스트(격리 텍스트)**&#x200B;에 &quot;사용자 조회 성공했지만 사용자 레코드를 찾을 수 없음&quot;이 포함되고 **오류 텍스트(격리 텍스트)**&#x200B;에 &quot;support.apple.com&quot;이 포함됩니다.
   * **업데이트 상태(@lastModified)**(2021년 4월 26일 오전 또는 이후):00:00
   * **업데이트 상태(@lastModified)** 2021년 4월 26일 또는 그 이전:00:

* 격리 목록의 **[!UICONTROL Error text]** 필드에 인바운드 전자 메일 규칙 정보가 있는 캠페인 인스턴스의 경우:

   * **오류 텍스트(격리 텍스트)**&#x200B;에 &quot;Momen_Code10_InvalidRecipient&quot;가 포함되어 있습니다.
   * **전자 메일 도메인(@domain)**&#x200B;이 icloud.com과 같음 또는 **전자 메일 도메인(@domain)**&#x200B;이 me.com과 같음 또는 **전자 메일 도메인(@domain)**&#x200B;이 mac.com과 같음
   * **업데이트 상태(@lastModified)**(2021년 4월 26일 오전 또는 이후):00:00
   * **업데이트 상태(@lastModified)** 2021년 4월 26일 또는 그 이전:00:

영향을 받는 받는 받는 받는 받는 사람 목록을 가지고 있으면 **[!UICONTROL Database cleanup]** 워크플로에 의해 격리 목록에서 제거될 수 있도록 해당 받는 사람을 **[!UICONTROL Valid]** 상태로 설정하거나 표에서 삭제할 수 있습니다.

**관련 항목:**
* [게재 실패 이해](understanding-delivery-failures.md)
* [반송 메일 조건](understanding-delivery-failures.md#bounce-mail-qualification)
