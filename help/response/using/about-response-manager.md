---
product: campaign
title: 응답 관리자 기본 정보
description: 응답 관리자 기본 정보
feature: Campaigns
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
exl-id: b5c0e960-2afe-4a98-b82c-d47a74659703
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 4%

---

# 캠페인 반응 관리자 시작{#about-response-manager}



Adobe Campaign에서는 마케팅 캠페인의 성공 및 수익성을 측정하거나 커뮤니케이션 채널 간에 제안을 제공하는 응답 관리 추가 기능을 제공합니다.

## 가설 {#hypothesis-concept}

게재를 받은 후 타겟팅한 사람들의 행동을 추론하기 위해 연락 날짜로부터 주어진 기간 동안 가설을 구성할 수 있습니다. 이러한 가설은 구매 내역 및 구매 내역을 저장하는 **transaction** 테이블을 기반으로 합니다.

가설은 시간이 제한되어 있으며, 대상 모집단과 비교할 대조군에 적용될 수 있다. 계산이 완료되면 자동으로 업데이트되는 **지표**&#x200B;에서 가설 결과를 제공합니다. 가설에 연결된 ROI는 캠페인 보고서에서 고려됩니다.

또한 응답 관리자와 함께 제공된 **보고서**&#x200B;를 통해 매출액 증가, 이익 계산과 연계된 정보와 게재 또는 오퍼의 ROI를 요약할 수 있습니다.

또한 구매 세부 사항 라인 덕분에 예를 들어 한 가지 특정 제품에만 집중하도록 가설을 지정할 수 있습니다.

예를 들어 게재를 통해 항목을 홍보한 후 생성된 수익을 평가하려고 합니다. 게재가 트리거된 다음 달에 하나 이상의 항목을 구매한 수신자가 이 작업에 반응했다는 가설을 적용합니다. 응답 관리는 이 가설을 기반으로 어떤 구매 요청 라인을 할당해야 하는지 결정합니다. 그러면 이를 바탕으로 그 결과 수익을 이들 라인의 합계로 결정할 수 있을 것이다.

>[!CAUTION]
>
>응답 관리자는 **[!UICONTROL Campaign]** 옵션입니다. 사용권 계약을 확인하십시오.

게재나 오퍼를 받은 수신자 전체 가구에 대한 모든 반응을 계산할 수도 있다.

각 가설은 단일 거래 테이블에 연결되어 있습니다. 하나의 게재 또는 오퍼가 여러 가설에 연결될 수 있습니다.

## 구현 단계 {#method}

응답 관리자를 사용하기 전에 [구성](configuration.md)을(를) 참조하여 필요한 구성을 수행하십시오.

게재 또는 오퍼에 대한 가설을 시작하려면 만드는 각 가설에 사용될 템플릿에서 그 컨텍스트를 정의해야 합니다.

측정 가설을 정의하고 생성하려면 다음 프로세스를 적용합니다.

1. 가설 모델을 정의합니다. [자세히 알아보기](hypothesis-templates.md#creating-a-hypothesis-model)
1. 기존 게재에 대해 하나 이상의 가설을 만듭니다. [자세히 알아보기](creating-hypotheses.md#referencing-a-hypothesis-in-a-campaign-delivery)

   또는

   오퍼에 대해 하나 이상의 가설을 만듭니다. [자세히 알아보기](creating-hypotheses.md#creating-a-hypothesis-on-an-offer)

1. 가설 결과를 확인합니다. [자세히 알아보기](hypothesis-tracking.md)
1. 필요한 경우 가설을 다시 실행합니다. [자세히 알아보기](creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)
