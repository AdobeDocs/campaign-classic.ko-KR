---
solution: Campaign Classic
product: campaign
title: 규칙 적용
description: 규칙 적용
audience: campaign
content-type: reference
topic-tags: campaign-optimization
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '977'
ht-degree: 9%

---


# 규칙 적용{#applying-rules}

## 배달 {#applying-a-typology-to-a-delivery}에 유형 분류 적용

귀하가 만든 유형 분류 규칙을 적용하려면, 유형을 분류법에 연결한 다음 이 유형 유형을 전달에서 참조해야 합니다. 방법은 다음과 같습니다.

1. 캠페인 유형을 만듭니다.

   유형 분류는 **[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]** 노드를 통해 액세스합니다.

1. **[!UICONTROL Rules]** 탭으로 이동하여 **[!UICONTROL Add]** 버튼을 클릭하고 이 Typical에 적용할 규칙을 선택합니다.

   ![](assets/campaign_opt_pressure_sample_1_6.png)

1. 다음과 같은 유형을 저장합니다.가 기존 유형 유형 목록에 추가됩니다.
1. 규칙을 적용할 배달을 엽니다.
1. 배달 속성을 열고 **[!UICONTROL Typology]** 탭에 액세스합니다.
1. 드롭다운 목록에서 유형을 선택합니다.

   ![](assets/campaign_opt_pressure_sample_1_7.png)

   >[!NOTE]
   >
   >이 템플릿을 사용하여 만든 모든 게재에 자동으로 적용되도록 게재 템플릿에서 유형화를 정의할 수 있습니다.

## 응용 프로그램 조건 정의 {#defining-application-conditions}

필요에 따라(제어 규칙 제외) 규칙의 응용 프로그램 필드를 제한할 수 있습니다.

분류 규칙 유형을 구성하여 Type Rules가 연결되어 있는 특정 게재나 전달 대상 중 특정 받는 사람만 관련되도록 할 수 있습니다.

규칙의 응용 프로그램 조건을 정의하려면 **[!UICONTROL General]** 탭에서 **[!UICONTROL Edit the rule application conditions...]** 링크를 클릭합니다.

그런 다음 쿼리 편집기를 사용하여 필터링 조건을 정의합니다. 다음 예에서, 용량 규칙은 2013년 4월 1일 이전에 생성된 레이블이나 배달에서 &#39;offer&#39;라는 단어가 포함된 배달에만 적용됩니다.

![](assets/campaign_opt_create_capacity_criterion.png)

>[!NOTE]
>
>필터링 규칙의 경우 필터링 기준의 응용 프로그램 조건을 선택할 수 있습니다.배달이나 배달 방법에 따라 달라질 수 있습니다. 자세한 내용은 [필터링 규칙](../../campaign/using/filtering-rules.md#conditioning-a-filtering-rule)을 참조하십시오.

## 계산 주기 조정 중 {#adjusting-calculation-frequency}

데이터베이스 정리 워크플로우를 통해 중재는 매일 밤 자동으로 재실행됩니다. 하지만 이 기간을 초과하여 값을 저장할 수 있습니다.

실제로 일부 계산에서는 매일 변경되지 않는 값을 사용합니다. 따라서 매일 데이터를 다시 계산하고 아무 것도 없이 데이터베이스를 과부화하는 것은 상관없습니다. 예를 들어 프로세스가 고객 성향 점수와 매주 구매 정보를 통해 마케팅 데이터베이스를 향상시키는 경우 이러한 값에 기반한 데이터를 매일 다시 계산하지 않아도 됩니다.

이렇게 하려면 **[!UICONTROL General]** 탭의 **[!UICONTROL Frequency]** 필드를 사용하여 타깃팅이 저장되는 동안 최대 기간을 정의할 수 있습니다. 기본적으로 값 **0**&#x200B;은 일일 재조정을 다음 번 실행할 때까지 계산이 유효함을 나타냅니다.

이 기간 이후의 결과를 저장하려면 **[!UICONTROL Frequency]** 필드에 12보다 큰 값을 입력합니다.이 기간이 만료되면 모든 규칙이 다시 적용됩니다.

**[!UICONTROL Re-apply the rule at the start of personalization]** 옵션을 사용하면 **[!UICONTROL Frequency]** 필드에 명시된 기간이 여전히 유효한 경우를 포함하여 개인화 단계 동안 규칙을 자동으로 적용할 수 있습니다.

## 규칙 응용 프로그램 단계 선택 {#selecting-the-rule-application-phase}

분류 규칙은 관심 있는 게재의 타깃팅, 분석 및 개인화 단계에서 특정 시퀀스에 적용됩니다.

### 실행 순서 {#execution-order}

표준 작업 모드에서는 규칙은 다음 순서로 적용됩니다.

1. 타겟팅 시작 시 적용되는 경우에는 규칙을 제어합니다.
1. 필터링 규칙:

   * 주소 자격에 대한 기본 응용 프로그램 규칙:/격리된 주소/주소 차단 목록 품질에 정의된 주소/검증되지 않은 주소/주소
   * 사용자가 정의한 필터링 규칙.
   * 주소 또는 식별자에 대한 데이터 중복 제거 규칙(필요한 경우 적용).

1. 압력 규칙.
1. 용량 규칙.
1. 타겟팅 끝에 적용되는 경우에는 규칙을 제어합니다.
1. 규칙이 개인화 시작 시 적용되는 경우 규칙을 제어합니다. 사용자 규칙(필터링/압력/용량)이 만료되어 다시 계산해야 하는 경우 이 단계 동안 적용됩니다.
1. 규칙이 개인화 종료 시 적용되는 경우

>[!NOTE]
>
>캠페인 상호 작용 모듈로 작업하는 경우 오퍼 자격 규칙은 오퍼 엔진에 대한 호출 동안 필터링 규칙(제공 아웃라인에 있는 오퍼에 대해 제공)이나 개인화 단계 도중 동시에 적용됩니다.

규칙의 **[!UICONTROL General]** 탭에서 적절한 필드를 사용하여 동일한 유형의 규칙의 실행 순서를 조정할 수 있습니다. 동일한 메시지 처리 단계 동안 여러 개의 규칙이 실행되면 **[!UICONTROL Execution sequence]** 필드에서 실행 시퀀스를 구성할 수 있습니다.

예를 들어 실행 순서가 20인 압력 규칙은 실행 순서가 30인 압력 규칙 전에 실행됩니다.

### 제어 규칙 {#control-rules}

**[!UICONTROL Control]** 규칙의 경우, 배포 라이프사이클의 어느 지점을 결정하면(타깃팅 전 또는 후에, 개인화가 시작될 때, 분석 끝에) 규칙이 적용됩니다. **[!UICONTROL Phase]** 필드의 드롭다운 목록에서 Typical 규칙의 **[!UICONTROL General]** 탭에서 적용할 값을 선택합니다.

![](assets/campaign_opt_define_control_phase.png)

가능한 값은 다음과 같습니다.

* **[!UICONTROL At the start of targeting]**

   오류가 발생하는 경우 개인화 단계가 실행되지 않도록 하려면 여기에서 제어 규칙을 적용할 수 있습니다.

* **[!UICONTROL After targeting]**

   제어 규칙을 적용하려면 대상의 볼륨을 알아야 하는 경우 이 단계를 선택하십시오.

   예를 들어 각 타깃팅 단계 다음에 **[!UICONTROL Check proof size]** 제어 규칙이 적용됩니다.이 규칙은 증명 받는 사람이 너무 많을 경우 메시지 개인화를 방지합니다.

* **[!UICONTROL At the start of personalization]**

   컨트롤이 메시지 개인화 승인에 관련된 경우 이 단계를 선택해야 합니다. 분석 단계 동안 메시지 개인화가 수행됩니다.

* **[!UICONTROL At the end of the analysis]**

   검사를 완료하기 위해 메시지 개인화를 완료해야 하는 경우 이 단계를 선택하십시오.

## 추가 구성 {#additional-configurations}

### 나가는 SMTP 트래픽 {#control-outgoing-smtp-traffic} 제어

옵션으로 **[!UICONTROL Managing affinities with IP addresses]** 필드를 사용하여 이 관련성을 MTA(배달 서버)에 배달을 연결할 수 있습니다. 이를 통해 특정 게재에 대한 이메일 수를 기계나 출력 주소로 제한할 수 있습니다.

![](assets/campaign_opt_select_ip_affinity.png)

>[!NOTE]
>
>선호도 관리는 **[!UICONTROL Filtering]** 유형 유형에는 적용되지 않습니다.\
>친화성은 Adobe Campaign 서버의 인스턴스 구성 파일에 정의됩니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../installation/using/about-initial-configuration.md)을 참조하십시오.

### 캠페인 최적화 및 분산 마케팅 {#campaign-optimization-and-distributed-marketing}

**[!UICONTROL Distributed Marketing]** 탭에서는 공유 캠페인이 순서가 지정되거나 예약될 때 적용되는 유형 및/또는 규칙의 다시 매핑을 정의할 수 있습니다. 중앙 엔터티에 대해 정의된 엔터티에 연결된 로컬 엔티티에 대해 정의된 유형/규칙이 중앙 엔티티에 연결된 규칙/유형 유형을 대체합니다. 다시 매핑을 사용하면 중앙 개체 규칙을 캠페인을 순서를 지정한 로컬 개체에 적용할 수 있습니다.

![](assets/simu_campaign_opti_distrib_mkg.png)

>[!NOTE]
>
>라이센스에 다음 옵션이 포함된 경우, 유형 및 유형 분류 규칙에서 **[!UICONTROL Distributed Marketing]** 탭이 추가됩니다.사용권 계약을 확인하십시오.\
>분산 마케팅에 대한 자세한 내용은 [분산 마케팅 정보](../../campaign/using/about-distributed-marketing.md)를 참조하십시오.

