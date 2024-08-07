---
product: campaign
title: ISP 중단 후 바운스 자격 업데이트
description: ISP 중단 후 바운스 자격을 업데이트하는 방법을 알아봅니다
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Deliverability
hide: true
hidefromtoc: true
exl-id: 7a9afe0a-0219-40f1-9fe2-6374db8d555c
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 3%

---

# ISP 중단 후 잘못된 하드 바운스 업데이트 {#update-bounces}



## 컨텍스트{#update-bounce-context}

ISP가 중단되는 경우 Campaign을 통해 보낸 이메일이 수신자에게 정상적으로 전달될 수 없습니다. 이러한 이메일은 바운스로 잘못 표시됩니다.

예를 들어 Apple 또는 Gmail의 전역 문제로 인해 유효한 Apple 또는 Gmail 이메일 주소로 전송된 일부 이메일 메시지가 바운스 다음 응답과 함께 ISP 서버에 의해 잘못된 이메일 주소로 잘못 하드 바운스될 수 있습니다.

* &quot;550 5.1.1 &#39;이메일 주소&#39;: 사용자 조회에 성공했지만 사용자 레코드를 찾을 수 없습니다.&quot;

* &quot;550명의 &#39;이메일 주소&#39; 수신자 거부됨&quot;

지연 바운스가 &quot;452 요청된 작업이 중단됨: 나중에 다시 시도&quot;라는 메시지와 함께 관찰되는 경우 자동으로 다시 시도되며 작업이 필요하지 않습니다. ISP가 전체 용량을 복구하므로 성능이 향상되어야 합니다.

>[!NOTE]
>
>[이 페이지](https://www.apple.com/support/systemstatus/){_blank}에서 Apple 시스템 상태 대시보드를 확인할 수 있습니다.
>
>[이 페이지](https://www.google.com/appsstatus#hl=en&amp;v=status){_blank}에서 Google Workspace 상태 대시보드를 확인할 수 있습니다.
>

## 영향{#update-bounce-impact}

ISP가 중단되는 경우 Campaign을 통해 보낸 이메일이 수신자에게 정상적으로 전달될 수 없습니다. 이러한 이메일은 바운스로 잘못 표시됩니다.

표준 바운스 처리 논리에 따라 Adobe Campaign은 **[!UICONTROL Status]** 설정이 **[!UICONTROL Quarantine]**&#x200B;인 격리 목록에 이 수신자를 자동으로 추가했습니다. 이 문제를 해결하려면 야간 정리 워크플로우에서 해당 수신자를 찾아 제거하거나 **[!UICONTROL Status]**&#x200B;을(를) **[!UICONTROL Valid]**(으)로 변경하여 Campaign에서 격리 테이블을 업데이트해야 합니다.

이 문제의 영향을 받는 수신자를 찾으려면 아래 지침을 참조하십시오.

## 업데이트할 프로세스{#update-bounce-update}

Apple 격리 테이블에서 쿼리를 실행하여 중단의 영향을 받을 수 있는 모든 수신자(예: @icloud.com, @me.com, @mac.com)를 포함한 주소)를 필터링해야 합니다. 이러한 수신자는 격리 목록에서 제거하고 향후 Campaign 이메일 게재에 포함할 수 있습니다.

인시던트의 일정 및 ISP를 기반으로 이 쿼리에 대한 권장 지침은 다음과 같습니다.

* 격리 목록의 **[!UICONTROL Error text]** 필드에 인바운드 전자 메일 규칙 정보가 있는 캠페인 환경의 경우:

   * **오류 텍스트(격리 텍스트)**&#x200B;에 &quot;Momen_Code10_InvalidRecipient&quot;가 포함되어 있습니다.
   * **전자 메일 도메인(@domain)**&#x200B;이 domain1.com과 같음 또는 **전자 메일 도메인(@domain)**&#x200B;이 domain2.com과 같음 또는 **전자 메일 도메인(@domain)**&#x200B;이 domain3.com과 같음
   * `MM/DD/YYYY HH:MM:SS AM` 또는 이후 **업데이트 상태(@lastModified)**
   * **업데이트 상태(@lastModified)**(`MM/DD/YYYY HH:MM:SS PM` 또는 이전)

* 격리 목록의 **[!UICONTROL Error text]** 필드에 SMTP 바운스 응답 정보가 있는 캠페인 환경의 경우:

   * **오류 텍스트(격리 텍스트)**&#x200B;에 &quot;550-5.1.1&quot;이 있고 **오류 텍스트(격리 텍스트)**&#x200B;에 &quot;support.ISP.com&quot;이 있습니다.

     예를 들어 &quot;support.ISP.com&quot;은 &quot;support.apple.com&quot; 또는 &quot;support.google.com&quot;일 수 있습니다.

   * `MM/DD/YYYY HH:MM:SS AM` 또는 이후 **업데이트 상태(@lastModified)**
   * **업데이트 상태(@lastModified)**(`MM/DD/YYYY HH:MM:SS PM` 또는 이전)


영향을 받는 받는 받는 받는 받는 사람 목록을 가지고 있으면 **[!UICONTROL Database cleanup]** 워크플로에 의해 격리 목록에서 제거될 수 있도록 해당 받는 사람을 **[!UICONTROL Valid]** 상태로 설정하거나 표에서 삭제할 수 있습니다.

**관련 항목:**
* [게재 실패 이해](understanding-delivery-failures.md)
* [반송 메일 조건](understanding-delivery-failures.md#bounce-mail-qualification)
