---
product: campaign
title: 마케팅 캠페인 디자인 및 실행
description: 마케팅 캠페인을 정의, 최적화, 실행 및 분석할 수 있습니다.
role: User
feature: Campaigns
hide: true
hidefromtoc: true
exl-id: 4e0df18f-3623-4dfb-a2f8-ad293dbc4dd5
source-git-commit: 4f809011a8b4cb3803c4e8151e358e5fd73634e4
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 22%

---

# 마케팅 캠페인 디자인 및 실행{#designing-marketing-campaigns}


Adobe Campaign을 사용하면 커뮤니케이션 및 마케팅 캠페인을 정의, 최적화, 실행 및 분석할 수 있습니다. Adobe Campaign은 마케팅 전략을 위한 통합 주문 및 실행 센터 역할을 합니다. 자세한 내용은 [캠페인 액세스](../../distributed/using/accessing-campaigns.md) 및 [마케팅 캠페인 만들기](../../campaign/using/setting-up-marketing-campaigns.md)를 참조하세요.

또한 **마케팅 리소스 관리(MRM)** 모듈을 사용하면 관련된 작업, 예산 및 마케팅 리소스에 대한 완전한 관리 및 실시간 추적을 제공하여 공동 작업 모드에서 마케팅 작업을 제어할 수 있습니다. 마케팅 리소스 관리를 사용하면 내부 및 외부 프로세스, 리소스 및 마케팅 캠페인과 타사 관계(에이전시, 프린터 등)의 관리를 최적화하고 규제할 수 있습니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../mrm/using/about-marketing-resource-management.md)을 참조하십시오.

>[!NOTE]
>
>Adobe Campaign 핵심 기능에 대한 자세한 내용은 [이 섹션](../../platform/using/about-adobe-campaign-classic.md) 섹션을 참조하십시오.\
>다양한 채널에서 모집단 타겟팅, 메시지 개인화 및 메시지 배달과 관련된 기능은 [이 섹션](../../delivery/using/steps-about-delivery-creation-steps.md)에 자세히 설명되어 있습니다.

![](assets/do-not-localize/how-to-video.png) [비디오에서 마케팅 캠페인 키 개념 살펴보기](#video)

## 핵심 개념 {#core-concepts}

Campaign의 컨텍스트에서 다음 개념을 알고 있어야 합니다.

* **캠페인**

  캠페인은 게재, 타겟팅 규칙, 비용, 파일 내보내기, 관련 문서 등 마케팅 캠페인과 관련된 모든 요소를 중앙에서 관리합니다. 각 캠페인은 프로그램에 첨부됩니다.

  자세한 내용은 [캠페인 추가](../../campaign/using/setting-up-marketing-campaigns.md#adding-a-campaign)를 참조하세요.

* **프로그램**

  프로그램을 사용하여 일정 기간에 대해 론칭, 캔버스, 충성도 등 마케팅 작업을 정의할 수 있습니다. 각 프로그램에는 전체 보기를 제공하는 달력에 연결된 캠페인이 포함되어 있습니다.

* **계획**

  마케팅 계획에는 여러 프로그램이 포함될 수 있습니다. 일정 기간과 연결되며 예산이 할당되어 문서 및 목표에 연결할 수도 있습니다.

  자세한 내용은 [캠페인 일정](../../campaign/using/accessing-marketing-campaigns.md#campaign-calendar)을 참조하세요.

* **워크플로**

  캠페인 워크플로우에는 모든 워크플로우와 동일한 활동이 포함되지만 캠페인에만 해당됩니다. 이를 통해 사용 가능한 모든 채널에 대한 게재를 만들고 구성할 수 있습니다.

  이 작업에 대한 자세한 정보는 [이 섹션](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow)을 참조하십시오.

* **목표**

  캠페인, 프로그램 또는 계획 내에서 목표 목록을 명시할 수 있습니다. 도달할 수량화된 값입니다. 캠페인, 프로그램 또는 계획이 끝날 때 MRM 모듈을 사용하면 전용 보고서에서 목표와 결과를 비교할 수 있습니다.

* **게재 개요**

  게재 개요는 게재의 구조화된 설명입니다. 모든 게재는 관련 오퍼, 첨부할 문서 또는 저장소에 대한 링크 등이 포함된 게재 개요를 참조할 수 있습니다. 오퍼는 선택한 게재 개요에 따라 게재에서 참조할 수 있습니다.

  이 작업에 대한 자세한 정보는 [이 섹션](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline)을 참조하십시오.

## 튜토리얼 {#video}

이 비디오에서는 마케팅 캠페인의 주요 개념을 설명합니다.

>[!VIDEO](https://video.tv.adobe.com/v/326577?quality=12&captions=kor)

추가 Campaign Classic 방법 비디오는 [여기](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=ko)에서 시청할 수 있습니다.
