---
product: campaign
title: 적합한 대상자 정의
description: 대상을 선택할 때 모범 사례에 대해 배웁니다
feature: Audiences
exl-id: c0533148-b027-4158-9b95-8d2df769e963
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 3%

---

# 적합한 대상자 정의 {#define-the-right-audience}

![](../../assets/common.svg)

타겟팅된 모집단은 목록을 신중하게 작성하고, 인기 있는 이메일 클라이언트와 모바일 장치에서 이메일을 테스트하고, 이메일 목록이 최신 상태인지(알 수 없거나 오래된 주소 없음) 확인합니다. 또한 전체 유효성 검사 주기를 설정하는 데 도움이 되는 증명을 보낼 수도 있습니다.

대상 모집단에 대해 자세히 알아보기 [이 섹션](steps-defining-the-target-population.md)

## 적절한 대상 Target {#target-the-right-audience}

콘텐츠가 준비되면 메시지를 받을 사용자를 신중하게 정의해야 합니다.

성공적으로 게재하기 위해서는 가장 연관성이 높은 개인화된 콘텐츠를 적절한 수신자에게 전송해야 합니다. Adobe Campaign을 사용하면 가장 정확한 타겟 을 구축할 수 있습니다. 이전 게재에서 링크를 클릭한 경우, 나이, 로컬라이제이션, 구매한 항목, 이전 게재에서 링크를 클릭한 경우 등에 따라 수신자를 선택할 수 있습니다. Adobe Campaign을 사용하여 테스트 프로필, 컨트롤 그룹 및 시드 주소를 정의하여 타겟이 올바른지 확인할 수도 있습니다.

## Target 매핑 {#target-mappings}

Campaign Classic에서 기본적으로 게재 템플릿은 타겟 **수신자**. Adobe Campaign은 사용자의 요구 사항에 따라 변경할 수 있는 게재에 대한 다른 target 매핑을 제공합니다.

예를 들어 소셜 네트워크를 통해 프로필이 수집된 방문자 또는 정보 서비스를 구독한 방문자에게 콘텐츠를 전달할 수 있습니다.

이러한 매핑이 표시됩니다 [이 섹션](selecting-a-target-mapping.md).

사용자 지정된 대상 매핑을 생성하고 사용할 수도 있습니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../configuration/using/target-mapping.md)을 참조하십시오.

## 외부 수신자 {#external-recipients}

데이터베이스에 저장되지 않고 외부 파일에 저장된 수신자에게 전달할 수 있습니다. 추가 정보 [이 섹션](steps-defining-the-target-population.md#selecting-external-recipients).

## 구독자에게 보내기 {#send-to-subscribers}

뉴스레터 가입자에게 메시지를 보내기 위해 구독자를 해당 정보 서비스로 직접 타깃팅할 수 있습니다. 추가 정보 [이 섹션](managing-subscriptions.md#delivering-to-the-subscribers-of-a-service).


## 수신자 및 시드 주소 테스트 {#test-recipients-seed-addresses}

게재를 테스트하려면 주요 타겟에게 보내기 전에 증명을 사용합니다.

양식과 메시지의 내용의 유효성을 검사하므로 적절한 증명 수신자를 선택해야 합니다. 증명 수신자를 정의하는 단계가 표시됩니다 [이 섹션](steps-defining-the-target-population.md#selecting-the-proof-target).

시드 주소는 기본 타겟으로 보내기 전에 게재를 테스트하기 위해 정의된 대상 기준과 일치하지 않는 수신자를 타겟팅하는 데 사용됩니다. 이러한 항목이 제공됩니다 [이 섹션](about-seed-addresses.md).

## 주소 중복 제거 {#deduplicate-addresses}

이메일 주소가 중복되지 않도록 하는 것이 타겟에 영향을 줄 수 있으므로 중요합니다.

* 대상을 분할할 때 동일한 메시지를 두 번 이상 보낼 수 있습니다.

* 수신자가 메시지를 받은 후 구독을 취소하면 중복 프로필은 계속 향후 메시지를 수신하게 됩니다.

중복 제거 주소는 전송 평판을 보호하고 격리 관리를 잘 해줍니다.

**관련 항목:**

* [중복 제거 활동](../../workflow/using/deduplication.md).
* [사용 사례: 중복 제거 활동의 병합 기능 사용](../../workflow/using/deduplication-merge.md)

## 전자 메일 주소 인덱스 {#index-addresses}

응용 프로그램에 사용되는 SQL 쿼리의 성능을 최적화하기 위해 데이터 스키마의 기본 요소에서 인덱스를 선언할 수 있습니다.

전자 메일 주소에 색인을 추가하는 단계가 표시됩니다 [이 섹션](../../configuration/using/database-mapping.md#indexed-fields).
