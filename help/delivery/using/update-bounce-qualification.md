---
product: campaign
title: ISP 중단 후 바운스 자격 업데이트
description: ISP 중단 후 반송 조건을 업데이트하는 방법을 알아봅니다
exl-id: 34be23f7-17fa-475e-9663-2e353d76b172
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 3%

---

# Apple 중단 후 잘못된 하드 바운스 업데이트 {#update-bounce-qualification.md}

![](../../assets/common.svg)

## 컨텍스트

2021년 4월 26일, Apple의 글로벌 문제로 인해 유효한 Apple 이메일 주소에 보낸 일부 이메일 메시지가 바운스 다음 응답이 있는 Apple 서버에 의한 잘못된 이메일 주소로 잘못 바운스되었습니다. &quot;550 5.1.1 &#39;이메일 주소&#39;: 사용자 조회 성공했지만 사용자 레코드가 없습니다.&quot;

이 문제는 4/26 오전 7시 - 오후 1시에 발생했습니다.

>[!NOTE]
>
>에서 Apple 시스템 상태 대시보드를 확인할 수 있습니다. [이 페이지](https://www.apple.com/support/systemstatus/).

ISP가 중단되는 경우, Campaign을 통해 전송된 이메일을 수신자에게 전달할 수 없습니다. 이 이메일은 반송 행위로 잘못 표시될 것입니다.

표준 바운스 처리 논리에 따라 Adobe Campaign은 이러한 수신자를 **[!UICONTROL Status]** 설정 **[!UICONTROL Quarantine]**. 이 문제를 해결하려면 이러한 수신자를 찾아 제거하거나 수신자를 변경하여 Campaign에서 격리 테이블을 업데이트해야 합니다 **[!UICONTROL Status]** to **[!UICONTROL Valid]** 야간 정리 워크플로우가 해당 워크플로우가 제거합니다.

이 문제의 영향을 받은 수신자를 찾거나 다른 ISP에서 이 문제가 다시 발생하는 경우 아래 지침을 참조하십시오.

## 업데이트할 프로세스

격리 테이블에서 쿼리를 실행하여 중단의 영향을 받을 수 있는 모든 Apple 수신자(@icloud.com, @me.com, @mac.com)를 필터링함으로써 격리 목록에서 제거하고 향후 Campaign 이메일 게재에 포함할 수 있습니다.

사고 기간에 따라 이 쿼리에 대한 권장 지침은 아래에 나와 있습니다.

>[!IMPORTANT]
>
>이 날짜/시간은 동부 표준 시간대(EST)를 기반으로 합니다. 인스턴스의 시간대에 맞게 조정하십시오.

* 에서 SMTP 바운스 응답 정보가 있는 Campaign 인스턴스의 경우 **[!UICONTROL Error text]** 격리 목록 필드:

   * **오류 텍스트(격리 텍스트)** 에는 &quot;사용자 조회 성공했지만 사용자 레코드가 없음&quot;이 포함되어 있으며 **오류 텍스트(격리 텍스트)** contains &quot;support.apple.com&quot;
   * **업데이트 상태(@lastModified)** 4/26/2021 이후:00:오전 00시
   * **업데이트 상태(@lastModified)** 4/26/2021 또는 이전:00:오후 00시

* 에서 인바운드 전자 메일 규칙 정보가 있는 Campaign 인스턴스의 경우 **[!UICONTROL Error text]** 격리 목록 필드:

   * **오류 텍스트(격리 텍스트)** contains &quot;Momen_Code10_InvalidRecipient&quot;
   * **이메일 도메인(@domain)** icloud.com 또는 과 같음 **이메일 도메인(@domain)** me.com과 같음 또는 **이메일 도메인(@domain)** mac과 같음.com
   * **업데이트 상태(@lastModified)** 4/26/2021 이후:00:오전 00시
   * **업데이트 상태(@lastModified)** 4/26/2021 또는 이전:00:오후 00시

영향을 받는 수신자 목록이 있으면 해당 수신자를 다음 상태로 설정할 수 있습니다. **[!UICONTROL Valid]** 따라서 다음을 통해 격리 목록에서 제거됩니다 **[!UICONTROL Database cleanup]** 워크플로우나 테이블에서 삭제할 수도 있습니다.

**관련 항목:**
* [게재 실패 이해](understanding-delivery-failures.md)
* [반송 메일 조건](understanding-delivery-failures.md#bounce-mail-qualification)
