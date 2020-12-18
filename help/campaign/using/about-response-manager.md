---
solution: Campaign Classic
product: campaign
title: 반응 관리자 기본 정보
description: 반응 관리자 기본 정보
audience: campaign
content-type: reference
topic-tags: response-manager
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 3%

---


# 반응 관리자 기본 정보{#about-response-manager}

## 목표 {#objectives}

Adobe Campaign은 마케팅 캠페인의 성공 및 수익성을 측정하거나 모든 통신 채널(이메일, 모바일, 전화, 다이렉트 메일, 팩스, 에이전시 등)에 대한 제안을 제공할 수 있는 응답 관리 애플리케이션(응답 관리자)을 제공합니다.

## 가설 개념 {#hypothesis-concept}

제공 후 타깃팅된 문서의 행동을 줄이기 위해 연락처 날짜로부터 지정된 기간 동안 가설을 구성할 수 있습니다. 이러한 가설은 구매 및 이러한 구매의 세부 사항을 저장하는 **transaction** 테이블을 기반으로 합니다.

가설이 제시간에 제한되고 목표 모집단과 비교되도록 제어 그룹에 적용될 수 있습니다. 가설 결과는 계산이 완료되면 자동으로 업데이트되는 **표시기**&#x200B;에 의해 제공됩니다. 가설을 포함한 ROI는 캠페인 보고서에서 고려됩니다.

또한 응답 관리자와 함께 제공되는 **보고서**&#x200B;를 사용하면 매출 증가, 마진 계산 및 전달 또는 오퍼의 ROI에 연결된 정보를 요약할 수 있습니다.

또한 구매 세부 정보 라인 덕분에 예를 들어 하나의 특정 제품에만 집중할 수 있도록 가설을 지정할 수 있습니다.

예를 들어 품목을 홍보하는 게재에 따라 생성된 매출을 평가하려고 합니다. 배달 트리거가 발생한 다음 달에 하나 이상의 항목을 구매한 모든 수신자가 이 작업에 반응했다는 가설을 적용합니다. 응답 관리에서는 이 가설을 바탕으로 구매 요청 라인을 지정해야 하는 것을 결정합니다. 그런 다음 이를 기반으로 결과 매출을 이러한 라인의 합계로 결정할 수 있습니다.

>[!CAUTION]
>
>응답 관리자는 **[!UICONTROL Campaign]** 옵션입니다. 사용권 계약을 확인하십시오.

전달 또는 오퍼를 받은 수신자의 전체 가정에 대한 모든 반응을 계산할 수도 있습니다.

각 가설이 단일 트랜잭션 테이블에 연결됩니다. 하나의 전달 또는 제안을 여러 가설을 연결할 수 있습니다.

## 메서드 {#method}

응답 관리자 사용을 시작하기 전에 [구성](../../campaign/using/configuration.md)을 참조하여 필요한 구성을 수행하십시오.

전달 또는 오퍼에 대한 가설을 시작하려면 만드는 각 가설을 위해 사용할 템플릿의 컨텍스트를 정의해야 합니다.

측정 가설을 정의하고 생성하려면 다음 프로세스를 수행합니다.

1. 가설 모델을 정의합니다. [가설 모델 만들기](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)를 참조하십시오.
1. 기존 전달에 대해 하나 이상의 가설을 만듭니다. 캠페인 전달[의 가설 참조를 참조하십시오.](../../campaign/using/creating-hypotheses.md#referencing-a-hypothesis-in-a-campaign-delivery)

   또는

   오퍼에 대해 하나 이상의 가설을 만듭니다. 오퍼[에 가설 만들기를 참조하십시오.](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-an-offer)

1. 가설 결과를 확인하십시오. [가설 추적](../../campaign/using/hypothesis-tracking.md)을 참조하십시오.
1. 필요한 경우 가설을 다시 시작합니다. [배달](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)에서 가설 만들기를 참조하십시오.

