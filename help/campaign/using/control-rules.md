---
solution: Campaign Classic
product: campaign
title: 제어 규칙
description: 제어 규칙
audience: campaign
content-type: reference
topic-tags: campaign-optimization
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 1%

---


# 제어 규칙{#control-rules}

## 분석 및 중재 제어 규칙 {#analysis-and-arbitration-control-rules}

제어 규칙을 사용하면 전달 전에 메시지의 유효성과 품질을 보장할 수 있습니다.문자 표시, SMS 크기, 주소 형식 등

특별한 규칙을 설정하여 일반적인 검사를 수행할 수 있습니다. 다음 검사(인터페이스에 굵게 표시됨)는 다음과 같습니다.

* **[!UICONTROL Object approval]** (이메일):보낸 사람 개체 및 주소에 특정 메일 에이전트에 문제를 일으킬 수 있는 특수 문자가 포함되어 있지 않은지 확인합니다.
* **[!UICONTROL URL label approval]** (이메일):각 추적 URL에 레이블이 있는지 확인합니다.
* **[!UICONTROL URL approval]** (이메일):추적 URL(&quot;&amp;&quot; 문자 존재)을 확인합니다.
* **[!UICONTROL Message size approval]** (모바일):SMS 메시지 크기를 확인합니다.
* **[!UICONTROL Validity period check]** (이메일):배달의 유효 기간이 모든 메시지를 보낼 만큼 길은지 확인합니다.
* **[!UICONTROL Proof size check]** (모든 채널):증명 대상 모집단에서 수신자가 100명을 초과하는 경우 오류 메시지가 생성됩니다.
* **[!UICONTROL Wave scheduling check]** (이메일):배달이 여러 파도로 분류된 경우 유효 기간이 끝나기 전에 마지막 전달 흐름이 시작되도록 예약되었는지 확인합니다.
* **[!UICONTROL Unsubscription link approval]** (이메일):각 컨텐츠에 하나 이상의 구독 취소(옵트아웃) URL이 있는지 확인합니다(HTML 및 텍스트).

## Creating a control rule {#creating-a-control-rule}

필요에 맞게 새로운 제어 규칙을 만들 수 있습니다. 이렇게 하려면 유형 **[!UICONTROL Control]** 규칙을 만들고 SQL에 컨트롤 공식을 **[!UICONTROL Code]** 입력합니다.

**예제:**

다음 예에서는 100명 이상의 수신자에게 SMS 오퍼가 전송되지 않도록 하는 규칙을 만듭니다. 이 규칙은 캠페인 유형 분석에 연결된 다음, 관련 오퍼를 사용할 수 있는 SMS 게재에 연결됩니다.

다음 단계를 적용합니다.

1. 분류 규칙을 **[!UICONTROL Control]** 만듭니다. 경고 수준을 **[!UICONTROL Warning]** 선택합니다.

   ![](assets/campaign_opt_create_control_01.png)

1. 아래 **[!UICONTROL Code]** 와 같이 탭에서 원하는 임계값을 적용할 스크립트를 입력합니다.

   ![](assets/campaign_opt_create_control_02.png)

   배달 대상이 다음 연락처가 100명을 초과하는 경우 이 스크립트는 경고를 트리거합니다.

   ```
   if( delivery.FCP == false && delivery.properties.toDeliver > 100 ) { logWarning("Significant number of SMS to deliver (" + delivery.properties.toDeliver + "). Please make sure the target is correct.") return false; } return true
   ```

1. 이 규칙을 캠페인 유형 분석에 연결하고 관련 SMS 전달의 유형을 참조합니다.

   ![](assets/campaign_opt_create_control_03.png)

1. 배달 분석 중에 규칙이 적용되며 해당되는 경우 경고가 생성됩니다.

   ![](assets/campaign_opt_create_control_04.png)

   그러나 배송은 여전히 보낼 준비가 될 것입니다.

   경고 수준을 높이면 배달이 시작되지 않습니다.

   ![](assets/campaign_opt_create_control_05.png)

   분석 종료 시 단추를 사용할 수 **[!UICONTROL Confirm delivery]** 없습니다.

   ![](assets/campaign_opt_create_control_06.png)

