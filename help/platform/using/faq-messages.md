---
solution: Campaign Classic
product: campaign
title: 테스트 및 보내기 FAQ
description: Campaign Classic FAQ
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '735'
ht-degree: 100%

---


# 메시지 확인, 보내기 및 추적 {#validate-send-track}

## 테스트 및 유효성 검사 {#test-and-validate-before-sending}

Adobe Campaign 내에서 메시지를 보내기 전에 테스트 및 유효성 검사 단계를 수행하는 방법을 배웁니다.

### 게재 분석이란 무엇입니까? {#what-is-the-delivery-analysis-}

게재 분석은 대상 모집단을 계산하고 게재 콘텐츠가 준비되는 단계입니다. 완료되면 게재를 보낼 수 있습니다. 모든 것이 올바른지 확인하려면 로그를 참조하십시오.

[자세한 내용을 보려면 여기를 클릭하십시오](../../delivery/using/steps-validating-the-delivery.md).

### 증명을 만들어야 하는 이유는 무엇입니까? {#why-should-i-create-proofs-}

Adobe에서는 주요 대상으로 보내기 전에 승인 그룹에서 전달을 테스트하기 위하여 증명 메시지를 만드는 것을 강력히 권장합니다. 그런 다음 메시지 콘텐츠, 개인화 및 게재 매개 변수의 유효성을 검사할 수 있습니다.

[자세한 내용을 보려면 여기를 클릭하십시오](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### Adobe Campaign에서 시드 주소를 사용하는 방법 {#how-to-use-seed-addresses-in-adobe-campaign-}

시드 주소는 정의된 대상 기준과 일치하지 않는 수신자를 타겟팅 하는 데 사용됩니다. 이러한 수신자는 전달 또는 캠페인에서 직접 가져오거나 만들 수 있는 대상에 추가됩니다. 직접 메일 게재의 경우 추출 중에 추가되고 출력 문서에 혼합됩니다.

다음과 같은 이점이 있습니다.

* 수신자 프로필의 데이터로 필드를 임의로 대체: 이 기능을 사용하면 시드 주소 섹션과 같은 전자 메일 주소만 입력할 수 있습니다.
* 데이터 관리 기능으로 워크플로우를 사용하는 경우 게재에서 처리된 추가 데이터를 시드 주소 수준에서 입력하여 값을 강제 적용할 수 있습니다. 이는 무작위 값 대체를 회피합니다.

[시드 주소에 대한 자세한 내용을 보려면 여기를 클릭하십시오](../../delivery/using/about-seed-addresses.md).

### 메시지를 보내기 전에 승인 프로세스를 설정하려면 어떻게 해야 합니까? {#how-can-i-set-up-an-approval-process-before-sending-messages-}

메시지 구성에서 발생할 수 있는 오류를 탐지하기 위해 Adobe에서는 게재 유효성 검사 주기를 설정할 것을 강력히 권장합니다. 필요한 만큼 자주 테스트 내용을 수신자에게 보내서 콘텐츠가 승인되었는지 확인합니다. 콘텐츠를 승인하려면 변경 사항이 있을 때마다 증명을 보내야 합니다.

[자세한 내용을 보려면 여기를 클릭하십시오](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### 유형화 규칙이란 무엇입니까? {#what-is-a-typology-rule-}

캠페인 간의 충돌을 방지하기 위해 Adobe Campaign은 특정 제한 조건을 적용하여 다양한 조합을 테스트할 수 있습니다. 따라서 전송된 메시지는 회사 커뮤니케이션 정책을 준수하면서 고객의 요구 사항과 기대치에 가장 적합한 메시지를 제공합니다.

[자세한 내용을 보려면 여기를 클릭하십시오](../../campaign/using/about-campaign-typologies.md).

## 메시지 보내기 {#send-your-messages}

Adobe Campaign을 사용하여 다양한 채널에서 메시지를 보내는 방법을 배웁니다.

### 전자 메일을 웨이브로 보내려면 어떻게 해야 합니까?? {#how-can-i-send-emails-in-waves-}

게재를 큰 모집단으로 보내기 전에 [웨이브를 구성](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves)하여 여러 개의 배치로 메시지를 나누어 부하의 균형을 맞출 수 있습니다.

### Campaign에서 전자 메일을 만드는 주요 단계는 무엇입니까? {#which-are-the-key-steps-to-create-an-email-in-campaign-}

전자 메일 게재가 만들어지고 유효성이 확인되면 해당 전자 메일을 보낼 수 있습니다. 전자 메일을 주요 대상으로 즉시 보내거나 나중에 게재되도록 예약할 수 있습니다. 필요한 경우 그 전에 대상 모집단을 예측할 수도 있습니다.

[자세한 내용을 보려면 여기를 클릭하십시오](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### 게재를 예약하는 방법 {#how-to-schedule-a-delivery-}

게재 예약이나 판매 압력을 관리하고 모집단을 지나치게 모집하지 않기 위해 메시지 게재를 연기할 수 있습니다.

[자세한 내용을 보려면 여기를 클릭하십시오](../../delivery/using/steps-sending-the-delivery.md#scheduling-the-delivery-sending).

### 전자 메일에 첨부 파일을 추가할 수 있습니까? {#can-i-add-an-attachment-to-emails-}

Campaign Classic을 통해 개인화된 첨부 파일을 전자 메일에 추가할 수 있습니다.

[전자 메일 첨부 파일에 대한 자세한 내용을 보려면 여기를 클릭하십시오](../../delivery/using/attaching-files.md).

## 메시지 추적 및 효과 측정 {#track-your-messages-and-measure-their-impact}

메시지가 전송되고 나면 Adobe Campaign을 통해 영향력을 추적하고 측정하는 방법을 배웁니다.

### 전자 메일 게재에서 추적된 링크를 구성하려면 어떻게 해야 합니까? {#how-can-i-configure-tracked-links-in-an-email-delivery-}

각 게재에 대해 메시지 수신 및 메시지 콘텐츠에 삽입된 링크의 활성화를 추적할 수 있습니다. 이렇게 하면 수신자가 타겟팅된 게재 작업 이후 수신자의 동작을 추적할 수 있습니다.

메시지의 각 URL에 대해 추적을 활성화할지 여부를 선택하고, 링크 레이블을 변경하고, 보고용 범주로 링크를 그룹화할 수 있습니다.

Campaign Classic에서 메시지를 추적하는 방법을 [자세히 알아보려면 여기를 클릭하십시오](../../delivery/using/about-message-tracking.md).

### 게재 및 추적 로그는 어디에서 액세스할 수 있습니까? {#where-can-i-access-delivery-and-tracking-logs-}

[이 페이지](../../delivery/using/monitoring-a-delivery.md)에서 게재 정보를 추적하고 수신자의 동작을 이해하는 방법을 배웁니다.

### 게재 보고서는 어디에서 얻을 수 있습니까? {#where-can-i-get-delivery-reports-}

Adobe Campaign에는 게재를 모니터링하고 메시지를 추적하는 보고서 세트가 포함되어 있습니다.

[기본 제공 보고서에 대한 자세한 내용을 보려면 여기를 클릭하십시오](../../reporting/using/delivery-reports.md).

### Adobe Campaign은 격리 주소를 어떻게 분류하고 관리합니까? {#how-does-adobe-campaign-qualify-and-manage-quarantine-addresses-}

Adobe Campaign은 격리된 주소 목록을 관리합니다. 주소가 격리된 수신자는 기본적으로 게재 분석 중에 제외되며 타겟팅되지 않습니다. 예를 들어, 사서함이 가득 찼거나 주소가 없는 경우 전자 메일 주소를 격리할 수 있습니다.

[격리 관리에 대한 자세한 내용을 보려면 여기를 클릭하십시오](../../delivery/using/understanding-quarantine-management.md).
