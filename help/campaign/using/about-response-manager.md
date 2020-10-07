---
title: 반응 관리자 기본 정보
seo-title: 반응 관리자 기본 정보
description: 반응 관리자 기본 정보
seo-description: null
page-status-flag: never-activated
uuid: 3087a96d-50fb-488a-9b76-70eb5c67deed
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: response-manager
discoiquuid: a4669fee-4512-455f-b495-ebd5a0746b76
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 4%

---


# 반응 관리자 기본 정보{#about-response-manager}

## 목표 {#objectives}

Adobe Campaign은 마케팅 캠페인의 성공과 수익성을 측정하거나 모든 통신 채널(이메일, 모바일, 전화, 다이렉트 메일, 팩스, 에이전시 등)에 대한 제안을 제공할 수 있는 응답 관리 응용 프로그램(응답 관리자)을 제공합니다.

## 가설 개념 {#hypothesis-concept}

접수 후 타깃팅된 문서의 행동을 줄이기 위해 접촉 날짜로부터 지정된 기간 동안 가설을 구성할 수 있습니다. 이러한 가설들은 구매와 이러한 구매의 세부 사항을 저장하는 **거래** 테이블을 기반으로 합니다.

가설이 제시간에 한정되어 있고, 통제 그룹에 적용하여 목표 인구와 비교할 수 있습니다. 가설 결과는 계산이 완료되면 자동으로 업데이트되는 **지표로** 제공됩니다. 가설 관련 ROI는 캠페인 보고서에서 고려됩니다.

또한, 응답 관리자와 함께 제공된 **보고서를** 통해 매출 증가, 마진 계산, 전달 또는 오퍼의 ROI에 연결된 정보를 요약할 수 있습니다.

또한 구매 세부 정보 라인 덕분에 예를 들어 하나의 특정 제품에만 집중할 수 있도록 가설을 지정할 수 있습니다.

예를 들어 품목을 홍보하는 게재에 따라 생성된 매출을 평가하려고 합니다. 배송이 트리거된 다음 달에 하나 이상의 항목을 구매한 모든 수신자가 이 조치에 반응했다는 가설을 적용합니다. 응답 관리는 이러한 가설을 바탕으로 구매 요청 라인을 지정해야 하는 것을 결정합니다. 그런 다음 이를 기반으로 결과 매출을 이러한 라인의 합계로 결정할 수 있습니다.

>[!CAUTION]
>
>응답 관리자는 **[!UICONTROL Campaign]** 옵션입니다. 사용권 계약을 확인하십시오.

또한 배송 또는 오퍼를 받은 수신자의 전체 가정에 대한 모든 반응을 계산할 수 있습니다.

각 가설이 단일 트랜잭션 테이블에 연결됩니다. 하나의 전달 또는 오퍼를 여러 가설에 연결할 수 있습니다.

## 메서드 {#method}

응답 관리자를 사용하기 전에 구성을 [참조하여](../../campaign/using/configuration.md) 필요한 구성을 수행하십시오.

전달 또는 오퍼에 대한 가설을 실행하려면 작성한 각 가설에 사용할 템플릿의 컨텍스트를 정의해야 합니다.

가설을 정의하고 생성하려면 다음 절차를 수행하십시오.

1. 가설 모델을 정의합니다. 가설 모델 [만들기를 참조하십시오](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model).
1. 기존 전달에 대해 하나 이상의 가설을 만듭니다. 캠페인 전달 [의 가설 참조를 참조하십시오](../../campaign/using/creating-hypotheses.md#referencing-a-hypothesis-in-a-campaign-delivery).

   또는

   오퍼에 대해 하나 이상의 가설을 만듭니다. 오퍼에 [대한 가설 만들기를 참조하십시오](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-an-offer).

1. 가설 결과를 확인하십시오. 가설 [추적을 참조하십시오](../../campaign/using/hypothesis-tracking.md).
1. 필요한 경우 가설을 다시 실행합니다. 전달 [에 가설작성](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)참조

