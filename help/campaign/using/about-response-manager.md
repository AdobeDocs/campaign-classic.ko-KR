---
product: campaign
title: 반응 관리자 기본 정보
description: 반응 관리자 기본 정보
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: b5c0e960-2afe-4a98-b82c-d47a74659703
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 3%

---

# 캠페인 응답 관리자 시작{#about-response-manager}

Adobe Campaign은 마케팅 캠페인의 성공 및 수익성을 측정하거나 커뮤니케이션 채널 간에 제안을 제공할 수 있는 응답 관리 추가 기능을 제공합니다.이메일, 모바일, DM 등

## 가설 {#hypothesis-concept}

게재를 받은 후 타깃팅된 보고서의 동작을 추론하기 위해 연락 날짜로부터 주어진 기간 동안 가설을 구성할 수 있습니다. 이러한 가설은 구매 및 이러한 구매의 세부 사항을 저장하는 **transaction** 표를 기반으로 합니다.

가설이 제시간에 제한되어 있고 대상 모집단과 비교되도록 컨트롤 그룹에 적용할 수 있습니다. 가설 결과는 계산이 완료되면 자동으로 업데이트되는 **지표**&#x200B;에서 제공합니다. 가식에 연결된 ROI는 캠페인 보고서에서 고려됩니다.

또한 응답 관리자 가 제공된 **보고서**&#x200B;를 사용하면 이직률 증가, 마진 계산 및 게재 또는 오퍼의 ROI에 연결된 정보를 요약할 수 있습니다.

또한 구매 세부 사항 라인 덕분에 가설을 지정하여 예를 들어 한 특정 제품에만 집중할 수 있습니다.

예를 들어 품목을 홍보하는 게재 후에 생성된 매출을 평가하려고 합니다. 게재 트리거 이후 달에 하나 이상의 항목을 구매한 모든 수신자가 이 작업에 반응했다는 가설을 적용합니다. 응답 관리는 이 가설을 기반으로 구매 요청 라인을 지정해야 하는 것을 결정합니다. 그런 다음 이를 기반으로 결과 매출을 이러한 라인의 합계로 결정할 수 있습니다.

>[!CAUTION]
>
>응답 관리자는 **[!UICONTROL Campaign]** 옵션입니다. 사용권 계약을 확인하십시오.

게재 또는 오퍼를 받은 수신자의 전체 가구에 대한 모든 반응을 계산할 수도 있습니다.

각 가설은 단일 트랜잭션 테이블에 연결됩니다. 하나의 게재 또는 오퍼를 여러 가식에 연결할 수 있습니다.

## 구현 단계 {#method}

응답 관리자 사용을 시작하기 전에 [구성](../../campaign/using/configuration.md)을 참조하여 필요한 구성을 수행하십시오.

게재 또는 오퍼에 대한 가설을 시작하려면 만들어지는 각 가설에 사용할 템플릿에 해당 컨텍스트를 정의해야 합니다.

측정 가설을 정의하고 생성하려면 다음 프로세스를 적용합니다.

1. 가설 모델을 정의합니다. [가설 모델 만들기](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)를 참조하십시오.
1. 기존 게재에 대해 하나 이상의 가설을 만듭니다. 캠페인 게재에서 가설 참조](../../campaign/using/creating-hypotheses.md#referencing-a-hypothesis-in-a-campaign-delivery)를 참조하십시오.[

   또는

   오퍼에 대해 하나 이상의 가설을 만듭니다. [오퍼](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-an-offer)에 가설 만들기를 참조하십시오.

1. 가설 결과를 확인합니다. [가설 추적](../../campaign/using/hypothesis-tracking.md)을 참조하십시오.
1. 필요한 경우 가설을 다시 시작합니다. [게재 시 즉시 가설 만들기](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)를 참조하십시오.
