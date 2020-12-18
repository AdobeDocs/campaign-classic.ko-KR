---
solution: Campaign Classic
product: campaign
title: Campaign의 제공 정보
description: 전달 가능성 모범 사례 학습
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---


# 게재 기능 기본 정보{#about-deliverability}

**제공** 은 바운싱 또는 스팸으로 표시되지 않고 수신자의 받은 편지함에 도달하는 캠페인의 성공을 측정하는 데 포함됩니다.

Adobe Campaign은 플랫폼의 제공 성능을 추적할 수 있는 다양한 툴을 제공합니다. 또한 이 섹션에서는 전달 능력을 관리 및 최적화할 때 고려해야 하는 주요 원칙을 강조 표시합니다.

## 구성 {#configuration}

이 기능은 Adobe Campaign의 전용 패키지를 통해 사용할 수 있습니다. 이 패키지를 사용하려면 이 패키지를 설치해야 합니다. 작업이 완료되면 패키지를 고려하여 서버를 다시 시작합니다.
* 호스팅된 클라이언트와 하이브리드 클라이언트의 경우, **수신 가능성 모니터링**&#x200B;은 Adobe 기술 지원 및 컨설턴트가 사용자 인스턴스에 구성합니다. 자세한 내용은 Adobe 계정 담당자에게 문의하십시오.

* 온-프레미스 설치의 경우 **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** 메뉴를 통해 **[!UICONTROL Deliverability monitoring (Email Deliverability)]** 패키지를 설치해야 합니다. 자세한 내용은 [Campaign Classic 표준 패키지 설치](../../installation/using/installing-campaign-standard-packages.md)를 참조하십시오.

Adobe Campaign Classic에서 **배달 가능 모니터링**&#x200B;은 **[!UICONTROL Refresh for deliverability]** 작업 과정에서 관리됩니다. 기본적으로 모든 인스턴스에 설치되며 바운스 메일 자격 규칙 목록, 도메인 목록 및 MX 목록을 초기화할 수 있습니다. **[!UICONTROL Deliverability monitoring (Email Deliverability)]** 패키지가 설치되면 이 워크플로우는 매일 밤 실행되어 규칙 목록을 정기적으로 업데이트하고 플랫폼 제공 기능을 능동적으로 관리할 수 있습니다.

## 배경 {#background}

이메일 전달 기능은 마케터에게 수 천 건의 메시지를 전송하든 수 십억 건의 메시지를 전송하든 중요한 문제를 제시합니다. 메시지 5개 중 1개는 받은 편지함이나 받는 사람에게 도달하지 않습니다.

한때 IT 부서에 &quot;기술적 문제&quot;로 언급되었던 이메일 전달 능력이 마케팅 안건에 대해 높은 수준으로 계속해서 증가하고 있습니다. 이는 지능적인 마케터가 많은 요소가 본질적으로 기술적인 요소이지만, 배달성은 궁극적으로 엄청난 매출 의미를 갖는 비즈니스 문제라고 인식하기 때문입니다.

이메일 마케팅 단계를 고려합니다. 제공 기능은 수신한 메시지 수를 결정하며, 이 수는 차례로 단계의 각 후속 단계에 영향을 줍니다. 수신한 이메일이 적을수록 열람이 줄고 클릭 수가 적으며 전환율도 적습니다. **대규모 데이터베이스를 보유한 기업에게, 평균 및 뛰어난 배달 능력의 차이는 말 그대로 수십만 달러에서 수백만 달러의 매출을 의미할 수 있습니다.**

![](assets/deliverability_overview_1.png)

마케터는 평균(80%) 제공 여부를 계산하여 상당한 전환율 및 달러(달러)를 책정하고 있습니다.

이메일 배달은 정확히 무엇입니까? 마케터가 어떻게 고객 경로를 손쉽게 파악하고 이메일 캠페인을 통해 더 많은 결과를 얻을 수 있습니까?

이메일 전달 능력은 메시지 전달 능력을 판별하는 일련의 특성을 의미하며, 컨텐트와 포맷에 있어서 예상되는 품질과 함께, 개인 이메일 주소를 통해 목적지에 도달할 수 있는 능력을 결정합니다. 이러한 특성은 4가지 주요 카테고리로 분류됩니다.데이터 품질, 메시지 및 컨텐츠, 전송 인프라 및 명성을 높일 수 있습니다. 성공적인 이메일 제공 프로그램의 기반이 됩니다. 이 개요는 이메일 전달 성공의 4가지 기본 사항을 간략히 설명하고 이메일 마케팅 프로그램의 수익을 높이고 받은 편지함에 도달하기 위한 모범 사례를 제공합니다.

<!--![](assets/deliverability_overview_2.png)-->
