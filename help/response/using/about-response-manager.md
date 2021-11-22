---
product: campaign
title: 반응 관리자 기본 정보
description: 반응 관리자 기본 정보
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: b5c0e960-2afe-4a98-b82c-d47a74659703
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 5%

---

# 캠페인 응답 관리자 시작{#about-response-manager}

![](../../assets/v7-only.svg)

Adobe Campaign은 마케팅 캠페인의 성공 및 수익성을 측정하거나 커뮤니케이션 채널 간에 제안을 제공할 수 있는 응답 관리 추가 기능을 제공합니다. 이메일, 모바일, DM 등

## 가설 {#hypothesis-concept}

게재를 받은 후 타깃팅된 보고서의 동작을 추론하기 위해 연락 날짜로부터 주어진 기간 동안 가설을 구성할 수 있습니다. 이러한 가설은 **트랜잭션** 구매 및 이러한 구매의 세부 사항을 저장하는 표입니다.

가설이 제시간에 제한되어 있고 대상 모집단과 비교되도록 컨트롤 그룹에 적용할 수 있습니다. 가설 결과는 **지표** 계산이 완료되면 자동으로 업데이트됩니다. 가식에 연결된 ROI는 캠페인 보고서에서 고려됩니다.

또한, **보고서** 응답 관리자 가 제공되면 이직률 증가, 마진 계산 및 게재나 오퍼의 ROI에 연결된 정보를 요약할 수 있습니다.

또한 구매 세부 사항 라인 덕분에 가설을 지정하여 예를 들어 한 특정 제품에만 집중할 수 있습니다.

예를 들어 품목을 홍보하는 게재 후에 생성된 매출을 평가하려고 합니다. 게재 트리거 이후 달에 하나 이상의 항목을 구매한 모든 수신자가 이 작업에 반응했다는 가설을 적용합니다. 응답 관리는 이 가설을 기반으로 구매 요청 라인을 지정해야 하는 것을 결정합니다. 그런 다음 이를 기반으로 결과 매출을 이러한 라인의 합계로 결정할 수 있습니다.

>[!CAUTION]
>
>응답 관리자는 **[!UICONTROL Campaign]** 선택 사항입니다. 사용권 계약을 확인하십시오.

게재 또는 오퍼를 받은 수신자의 전체 가구에 대한 모든 반응을 계산할 수도 있습니다.

각 가설은 단일 트랜잭션 테이블에 연결됩니다. 하나의 게재 또는 오퍼를 여러 가식에 연결할 수 있습니다.

## 구현 단계 {#method}

응답 관리자 사용을 시작하기 전에 [구성](configuration.md) 필요한 구성을 수행합니다.

게재 또는 오퍼에 대한 가설을 시작하려면 만들어지는 각 가설에 사용할 템플릿에 해당 컨텍스트를 정의해야 합니다.

측정 가설을 정의하고 생성하려면 다음 프로세스를 적용합니다.

1. 가설 모델을 정의합니다. [자세히 알아보기](hypothesis-templates.md#creating-a-hypothesis-model)
1. 기존 게재에 대해 하나 이상의 가설을 만듭니다. [자세히 알아보기](creating-hypotheses.md#referencing-a-hypothesis-in-a-campaign-delivery)

   또는

   오퍼에 대해 하나 이상의 가설을 만듭니다. [자세히 알아보기](creating-hypotheses.md#creating-a-hypothesis-on-an-offer)

1. 가설 결과를 확인합니다. [자세히 알아보기](hypothesis-tracking.md)
1. 필요한 경우 가설을 다시 시작합니다. [자세히 알아보기](creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)
