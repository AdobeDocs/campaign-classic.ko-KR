---
solution: Campaign Classic
product: campaign
title: 적합한 대상 정의
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 3%

---


# 적합한 대상 정의 {#define-the-right-audience}

타깃팅된 채우기가 핵심 요소입니다.목록을 주의 깊게 작성하고, 인기 있는 이메일 클라이언트 및 모바일 디바이스에서 이메일을 테스트하고, 이메일 목록이 최신 상태(알 수 없거나 오래된 주소 없음)인지 확인합니다. 또한 전체 확인 주기를 설정하는 데 도움이 되는 교정본을 보낼 수 있습니다.

이 섹션](../../delivery/using/steps-defining-the-target-population.md)에서 타겟 모집단 [에 대해 자세히 알아보십시오.

## 올바른 대상자 {#target-the-right-audience}

콘텐츠를 준비하면 메시지를 받을 사람을 신중하게 정의해야 합니다.

성공적으로 전달하려면 가장 연관성 높은 개인화된 컨텐츠를 적합한 수신자에게 전송해야 합니다. Adobe Campaign을 사용하면 가장 정확한 타겟을 구축할 수 있습니다.이전 배달에서 링크를 클릭한 경우 연령, 현지화, 구매자, 구매자 등에 따라 받는 사람을 선택할 수 있습니다. Adobe Campaign을 사용하면 테스트 프로필, 제어 그룹 및 시드 주소를 정의하여 대상이 올바른지 확인할 수도 있습니다.

## 대상 매핑 {#target-mappings}

Campaign Classic에서 기본적으로 배달 템플릿은 **수신자**&#x200B;를 대상으로 합니다. Adobe Campaign은 필요에 따라 변경할 수 있는 게재에 대한 다른 대상 매핑을 제공합니다.

예를 들어 소셜 네트워크를 통해 프로필이 수집된 방문자 또는 정보 서비스에 가입한 방문자에게 프로필을 전달할 수 있습니다.

이러한 매핑은 이 섹션](../../delivery/using/selecting-a-target-mapping.md)에 [표시됩니다.

사용자 지정된 대상 매핑을 만들고 사용할 수도 있습니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../configuration/using/target-mapping.md)을 참조하십시오.

## 외부 받는 사람 {#external-recipients}

데이터베이스에 저장되지 않고 외부 파일에 저장된 수신자에게 전달할 수 있습니다. 이 섹션](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients)에서 [에 대해 자세히 알아보십시오.

## 구독자에게 {#send-to-subscribers} 보내기

뉴스레터 가입자에게 메시지를 보내려면 해당 정보 서비스에 가입자를 직접 타깃팅할 수 있습니다. 이 섹션](../../delivery/using/managing-subscriptions.md#delivering-to-the-subscribers-of-a-service)에서 [에 대해 자세히 알아보십시오.


## 받는 사람 및 시드 주소 테스트 {#test-recipients-seed-addresses}

전달 내용을 테스트하려면 주 타겟으로 보내기 전에 교정본을 사용하십시오.

양식 및 메시지 내용의 유효성을 검사하므로 적절한 증명 수신자를 선택해야 합니다. 증명 받는 사람을 정의하는 단계는 이 섹션](../../delivery/using/steps-defining-the-target-population.md#selecting-the-proof-target)에 [표시됩니다.

시드 주소는 기본 타겟으로 보내기 전에 배달을 테스트하기 위해 정의된 대상 기준과 일치하지 않는 수신자를 타게팅하는 데 사용됩니다. 이 섹션](../../delivery/using/about-seed-addresses.md)에 [이 표시됩니다.

## 주소 중복 제거 {#deduplicate-addresses}

타겟에 영향을 줄 수 있으므로 중복된 이메일 주소를 사용하지 않는 것이 중요합니다.

* 대상이 분할될 때 동일한 메시지를 두 번 이상 보낼 수 있습니다.

* 메시지를 받은 수신자가 구독을 취소하는 경우 중복된 프로필은 여전히 향후 메시지를 수신하게 됩니다.

중복 제거 주소는 전송 명성을 보호하고 안전한 격리 관리를 보장합니다.

이 사용 사례](../../workflow/using/deduplication.md#example--identify-the-duplicates-before-a-delivery)에서 [에 대해 자세히 알아보십시오.

## 색인 이메일 주소 {#index-addresses}

응용 프로그램에 사용된 SQL 쿼리의 성능을 최적화하기 위해 데이터 스키마의 기본 요소에서 인덱스를 선언할 수 있습니다.

전자 메일 주소에 색인을 추가하는 단계는 이 섹션](../../configuration/using/database-mapping.md#indexed-fields)에 [으로 표시됩니다.
