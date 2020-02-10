---
title: 테스트 및 보내기 FAQ
seo-title: 메시지 확인, 전송 및 추적
description: Campaign Classic FAQ
page-status-flag: never-activated
uuid: 3f719ac2-cc26-4fb0-adda-84666c8c38e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 16dbe423-018f-4666-9901-2120a8dc609a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 994ec35e37a1c26e83a8dd2ae31f6594cadd4c45

---


# 메시지 확인, 전송 및 추적 {#validate-send-track}

## 테스트 및 유효성 검사 {#test-and-validate-before-sending}

Adobe Campaign 내에서 메시지를 보내기 전에 테스트 및 유효성 검사 단계를 수행하는 방법을 알아봅니다.

### 배달 분석이란 무엇입니까? {#what-is-the-delivery-analysis-}

게재 분석은 대상 모집단이 계산되고 게재 컨텐츠가 준비된 단계입니다. 완료되면 배송이 가능합니다. 모든 것이 올바른지 확인하려면 로그를 참조하십시오.

[자세한](../../delivery/using/steps-validating-the-delivery.md)내용을 보려면 여기를 클릭하십시오.

### 교정본을 만들어야 하는 이유는 무엇입니까? {#why-should-i-create-proofs-}

Adobe에서는 기본 타겟으로 보내기 전에 승인 그룹에서 전달을 테스트하기 위한 증명 메시지를 만드는 것이 좋습니다. 그런 다음 메시지 컨텐츠, 개인화 및 전달 매개 변수의 유효성을 확인할 수 있습니다.

[자세한](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)내용을 보려면 여기를 클릭하십시오. 또한 [이 비디오를](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/getting-started/managing-seed-and-proofs.html)볼 수 있습니다.

### Adobe Campaign에서 시드 주소를 사용하는 방법 {#how-to-use-seed-addresses-in-adobe-campaign-}

시드 주소는 정의된 대상 기준과 일치하지 않는 수신자를 타깃팅하는 데 사용됩니다. 이러한 수신자는 대상에 추가됩니다.전달 또는 캠페인에서 직접 가져오거나 만들 수 있습니다. 직접 메일 배달의 경우 추출 중에 추가되고 출력 문서에 혼합됩니다.

다음과 같은 이점이 있습니다.

* 수신자 프로필의 데이터를 사용하여 필드를 임의 대체:이렇게 하면 이메일 주소만 입력할 수 있습니다(예: 시드 주소 섹션).
* 데이터 관리 기능과 함께 워크플로우를 사용할 때 게시에 처리된 추가 데이터를 시드 주소 수준에서 입력하여 값을 강제 적용할 수 있습니다.이 단계 무작위 값 대체를 수행합니다.

[시드 주소에](../../delivery/using/about-seed-addresses.md)대한 자세한 내용을 보려면 여기를 클릭하십시오.

### 메시지를 보내기 전에 승인 프로세스를 설정하려면 어떻게 해야 합니까? {#how-can-i-set-up-an-approval-process-before-sending-messages-}

메시지 구성에서 발생할 수 있는 오류를 검색하려면 배달 유효성 검사 주기를 설정하는 것이 좋습니다. 테스트 수신자에게 교정본을 전송하여 필요에 따라 자주 컨텐츠가 승인되었는지 확인합니다. 컨텐츠를 승인하려면 변경 사항이 있을 때마다 증명을 보내야 합니다.

[자세한](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)내용을 보려면 여기를 클릭하십시오.

### Typical 규칙이란 무엇입니까? {#what-is-a-typology-rule-}

캠페인 간의 충돌을 방지하기 위해 Adobe Campaign은 특정 제약 조건 규칙을 적용하여 다양한 조합을 테스트할 수 있습니다. 따라서 전송된 메시지는 회사 커뮤니케이션 정책에 따라 고객의 요구와 기대를 가장 잘 충족할 수 있습니다.

[자세한](../../campaign/using/about-campaign-typologies.md)내용을 보려면 여기를 클릭하십시오.

## 메시지 보내기 {#send-your-messages}

Adobe Campaign을 사용하여 다양한 채널에서 메시지를 전송하는 방법을 알아봅니다.

### 어떻게 이메일을 전파로 보낼 수 있습니까? {#how-can-i-send-emails-in-waves-}

배달을 큰 모집단으로 보내기 전에 여러 개의 배치로 메시지를 나누고 부하의 균형을 조정하기 위해 물결을 [](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves) 구성할 수 있습니다.

### Campaign에서 이메일을 만드는 주요 단계는 무엇입니까? {#which-are-the-key-steps-to-create-an-email-in-campaign-}

이메일 배달이 만들어지고 확인되면 전송할 수 있습니다. 이메일을 기본 타겟으로 즉시 전송하거나 나중에 배달할 날짜를 예약할 수 있습니다. 필요한 경우 그 전에 타겟 인구를 예측할 수도 있습니다.

[자세한](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)내용을 보려면 여기를 클릭하십시오.

### 배달을 예약하는 방법 {#how-to-schedule-a-delivery-}

메시지 전달을 연기하여 배달 일정을 잡거나 판매 압력을 관리하며 모집단을 과도한 모집하지 않을 수 있습니다.

[자세한](../../delivery/using/steps-sending-the-delivery.md#scheduling-the-delivery-sending)내용을 보려면 여기를 클릭하십시오.

### 이메일에 첨부 파일을 추가할 수 있습니까? {#can-i-add-an-attachment-to-emails-}

Campaign Classic을 사용하면 개인화된 첨부 파일을 이메일에 추가할 수 있습니다.

[이메일 첨부 파일에](../../delivery/using/attaching-files.md)대한 자세한 내용을 보려면 여기를 클릭하십시오.

## 메시지 추적 및 효과 측정 {#track-your-messages-and-measure-their-impact}

메시지가 전송되면 Adobe Campaign을 사용하여 영향력을 추적하고 측정하는 방법을 살펴볼 수 있습니다.

### 이메일 배달에서 추적된 링크를 어떻게 구성할 수 있습니까? {#how-can-i-configure-tracked-links-in-an-email-delivery-}

각 전달에 대해 메시지 수신과 메시지 컨텐츠에 삽입된 링크의 활성화를 추적할 수 있습니다. 이렇게 하면 받는 사람이 타깃팅된 전달 작업 이후 받는 사람의 동작을 추적할 수 있습니다.

메시지의 각 URL에 대해 추적을 활성화할지 여부를 선택하거나, 링크 레이블을 변경하고, 보고용 카테고리별로 링크를 그룹화할 수 있습니다.

[Campaign Classic에서 메시지를 추적하는 방법에 대한 자세한](../../delivery/using/about-message-tracking.md) 내용을 보려면 여기를 클릭하십시오.

### 배포 및 추적 로그는 어디에서 액세스할 수 있습니까? {#where-can-i-access-delivery-and-tracking-logs-}

이 [페이지에서](../../delivery/using/monitoring-a-delivery.md)배달을 추적하고 받는 사람의 행동을 이해하는 방법을 알아봅니다.

### 배달 보고서는 어디에서 얻을 수 있습니까? {#where-can-i-get-delivery-reports-}

Adobe Campaign에는 게재를 모니터링하고 메시지를 추적하는 보고서 세트가 포함되어 있습니다.

[내장된 보고서에](../../reporting/using/reports-on-deliveries.md#delivery-reports)대한 자세한 내용을 보려면 여기를 클릭하십시오.

### Adobe Campaign은 검역 주소를 어떻게 검증 및 관리합니까? {#how-does-adobe-campaign-qualify-and-manage-quarantine-addresses-}

Adobe Campaign에서 격리된 주소 목록을 관리합니다. 주소가 격리된 수신자는 배달 분석 중에 기본적으로 제외되며 타깃팅되지 않습니다. 예를 들어, 사서함이 가득 찼거나 주소가 없는 경우 이메일 주소를 격리할 수 있습니다.

[격리 관리에](../../delivery/using/understanding-quarantine-management.md)대한 자세한 내용을 보려면 여기를 클릭하십시오.
