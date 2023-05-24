---
product: campaign
title: 적합한 대상자 정의
description: 대상자를 선택할 때의 모범 사례에 대해 알아봅니다.
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Audiences
exl-id: c0533148-b027-4158-9b95-8d2df769e963
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 4%

---

# 적합한 대상자 정의 {#define-the-right-audience}



타겟팅된 모집단은 중요합니다. 목록을 신중하게 작성하고, 인기 있는 이메일 클라이언트 및 모바일 디바이스에서 이메일을 테스트하고, 이메일 목록이 최신 상태인지 확인합니다(알 수 없거나 오래된 주소는 없음). 전체 유효성 검사 주기를 설정하는 데 도움이 되는 증명을 보낼 수도 있습니다.

대상 모집단에 대해 자세히 알아보기 [이 섹션에서](steps-defining-the-target-population.md)

## 적합한 대상 Target {#target-the-right-audience}

콘텐츠를 준비한 후에는 메시지를 받을 사용자를 신중하게 정의해야 합니다.

게재를 성공적으로 수행하려면 가장 관련성이 높은 개인화된 콘텐츠를 적절한 수신자에게 전송해야 합니다. Adobe Campaign을 사용하면 가장 정확한 대상을 작성할 수 있습니다. 이전 게재에서 링크를 클릭한 경우 나이, 현지화, 구입한 항목 등에 따라 수신자를 선택할 수 있습니다. Adobe Campaign을 사용하면 테스트 프로필, 컨트롤 그룹 및 시드 주소를 정의하여 타겟이 올바른지 확인할 수도 있습니다.

## 대상 매핑 {#target-mappings}

Campaign Classic에서 기본적으로 게재 템플릿은 타겟팅합니다 **수신자**. Adobe Campaign은 게재에 대한 다른 타겟 매핑을 제공하며, 필요에 따라 변경할 수 있습니다.

예를 들어 소셜 네트워크를 통해 프로필이 수집된 방문자 또는 정보 서비스를 구독한 방문자에게 를 제공할 수 있습니다.

이 매핑이 표시됩니다. [이 섹션에서](selecting-a-target-mapping.md).

사용자 지정된 대상 매핑을 만들고 사용할 수도 있습니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../configuration/using/target-mapping.md)을 참조하십시오.

## 외부 수신자 {#external-recipients}

데이터베이스에 저장되지 않고 외부 파일에 저장된 수신자에게 전달할 수 있습니다. 자세히 알아보기 [이 섹션에서](steps-defining-the-target-population.md#selecting-external-recipients).

## 구독자에게 보내기 {#send-to-subscribers}

뉴스레터 가입자에게 메시지를 보내려면 해당 정보 서비스의 가입자를 직접 타겟팅할 수 있습니다. 자세히 알아보기 [이 섹션에서](managing-subscriptions.md#delivering-to-the-subscribers-of-a-service).


## 수신자 및 시드 주소 테스트 {#test-recipients-seed-addresses}

게재를 테스트하려면 주요 타겟에게 보내기 전에 증명을 사용하십시오.

적절한 증명 수신자를 선택해야 합니다. 메시지 양식 및 내용의 유효성을 검사하기 때문입니다. 증명 수신자를 정의하는 단계가 표시됩니다 [이 섹션에서](steps-defining-the-target-population.md#selecting-the-proof-target).

시드 주소는 기본 대상으로 보내기 전에 게재를 테스트하기 위해 정의된 대상 기준과 일치하지 않는 수신자를 타겟팅하는 데 사용됩니다. 제공됩니다. [이 섹션에서](about-seed-addresses.md).

## 주소 중복 제거 {#deduplicate-addresses}

중복 이메일 주소는 타겟에 영향을 줄 수 있으므로 피하는 것이 중요합니다.

* 대상이 분할될 때 동일한 메시지를 두 번 이상 보낼 수 있습니다.

* 메시지를 받은 후 수신자가 구독을 취소해도 중복 프로필은 향후 메시지를 계속 수신합니다.

주소 중복을 제거하면 전송 평판이 보호되며 격리도 잘 관리됩니다.

**관련 항목:**

* [중복 제거 활동](../../workflow/using/deduplication.md).
* [사용 사례: 중복 제거 활동의 병합 기능 사용](../../workflow/using/deduplication-merge.md)

## 이메일 주소 색인 지정 {#index-addresses}

응용 프로그램에서 사용되는 SQL 쿼리의 성능을 최적화하기 위해 데이터 스키마의 주 요소에서 인덱스를 선언할 수 있습니다.

이메일 주소에 인덱스를 추가하는 단계가 표시됩니다 [이 섹션에서](../../configuration/using/database-mapping.md#indexed-fields).
