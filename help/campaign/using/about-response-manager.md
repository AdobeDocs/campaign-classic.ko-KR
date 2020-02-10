---
title: 응답 관리자 정보
seo-title: 응답 관리자 정보
description: 응답 관리자 정보
seo-description: null
page-status-flag: never-activated
uuid: 3087a96d-50fb-488a-9b76-70eb5c67deed
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: response-manager
discoiquuid: a4669fee-4512-455f-b495-ebd5a0746b76
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 응답 관리자 정보{#about-response-manager}

## 목표 {#objectives}

Adobe Campaign은 마케팅 캠페인의 성공과 수익을 측정하거나 모든 커뮤니케이션 채널(이메일, 모바일, 전화, DM, 팩스, 에이전시 등)에 대한 제안을 제공할 수 있는 응답 관리 애플리케이션(응답 관리자)을 제공합니다.

## 가설 개념 {#hypothesis-concept}

접수 후 타깃팅된 가설을 접수 날짜로부터 지정된 기간 동안 구성할 수 있습니다. 이러한 가설은 구매와 이러한 구매의 세부 사항을 저장하는 **거래** 테이블을 기반으로 합니다.

가설이 제시간에 제한되며 목표 모집단과 비교하기 위해 제어 그룹에 적용될 수 있습니다. 가설 결과는 계산이 완료되면 자동으로 업데이트되는 **지표로** 제공됩니다. 가설을 연결하는 ROI는 캠페인 보고서에서 고려됩니다.

또한, 응답 관리자와 함께 제공되는 **보고서를** 사용하면 매출 증가, 마진 계산, 전달 또는 오퍼의 ROI에 연결된 정보를 요약할 수 있습니다.

또한 구매 세부 정보 라인 덕분에 예를 들어 특정 제품에 중점을 두도록 가설을 지정할 수 있습니다.

예를 들어, 품목을 홍보하는 배달을 수행한 후 생성된 매출을 평가하려고 합니다. Adobe는 배송이 트리거된 다음 달에 하나 이상의 항목을 구매한 수신자가 본 조치에 반응했다는 가설을 적용합니다. 응답 관리에서는 이 가설에 따라 어떤 구매 요청 라인을 지정해야 하는지를 결정합니다. 그런 다음, 이를 기반으로 결과 매출을 이러한 라인의 합계로 결정할 수 있습니다.

>[!CAUTION]
>
>응답 관리자는 **[!UICONTROL Campaign]** 옵션입니다. 사용권 계약을 확인하십시오.

전달 또는 오퍼를 받은 수신자의 전체 세대에 대한 모든 반응을 계산할 수도 있습니다.

각 가설이 단일 트랜잭션 테이블에 연결됩니다. 하나의 전달 또는 오퍼를 여러 가설에 연결할 수 있습니다.

## 메서드 {#method}

응답 관리자를 사용하기 전에 구성을 [참조하여](../../campaign/using/configuration.md) 필요한 구성을 수행하십시오.

게재 또는 오퍼에 대한 가설을 실행하려면, 작성한 각 가설을 위해 사용할 템플릿의 컨텍스트를 정의해야 합니다.

가설을 정의하고 생성하려면 다음 절차를 따르십시오.

1. 가설 모델을 정의합니다. 가설 [모델](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)만들기를 참조하십시오.
1. 기존 전달에 대해 가설을 하나 이상 만듭니다. 캠페인 [전달의](../../campaign/using/creating-hypotheses.md#referencing-a-hypothesis-in-a-campaign-delivery)가설 참조를 참조하십시오.

   or

   오퍼에 대해 하나 이상의 가설을 만듭니다. 오퍼에 [대한 가설 만들기를 참조하십시오](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-an-offer).

1. 가설 결과 확인 가설 [추적을](../../campaign/using/hypothesis-tracking.md)참조하십시오.
1. 필요한 경우 가설을 다시 시작합니다. 게재에서 [가설 만들기를](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)참조하십시오.

