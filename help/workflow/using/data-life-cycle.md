---
solution: Campaign Classic
product: campaign
title: 데이터 수명 주기
description: 워크플로우의 데이터 라이프사이클에 대한 자세한 내용
audience: workflow
content-type: reference
topic-tags: -general-operation
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 4%

---


# 데이터 수명 주기 {#data-life-cycle}

## 작업 테이블 {#work-table}

워크플로우에서 한 활동에서 다른 활동으로 전송된 데이터는 임시 작업 테이블에 저장됩니다.

해당 전환을 마우스 오른쪽 단추로 클릭하여 이 데이터를 표시하고 분석할 수 있습니다.

![](assets/wf-right-click-analyze.png)

이렇게 하려면 관련 메뉴를 선택합니다.

* 대상 표시

   이 메뉴는 대상 모집단뿐만 아니라 작업 테이블 구조(**[!UICONTROL Schema]** 탭)에 사용 가능한 데이터를 표시합니다.

   ![](assets/wf-right-click-display.png)

   자세한 내용은 작업 테이블 및 [워크플로우 스키마를 참조하십시오](../../workflow/using/monitoring-workflow-execution.md#worktables-and-workflow-schema).

* 대상 분석

   이 메뉴를 사용하면 전환 데이터에 대한 통계 및 보고서를 생성할 수 있는 설명 분석 마법사에 액세스할 수 있습니다.

   자세한 정보는 이 [섹션](../../reporting/using/using-the-descriptive-analysis-wizard.md)을 참조하십시오.

워크플로우가 실행되면 대상 데이터가 삭제됩니다. 마지막 작업 테이블만 액세스할 수 있습니다. 모든 작업 테이블에 액세스할 수 있도록 워크플로우를 구성할 수 있습니다.워크플로우 속성에서 **[!UICONTROL Keep the result of interim populations between two executions]** 옵션을 선택합니다.

하지만 대량의 데이터가 있을 경우 이 옵션을 활성화하지 않는 것이 좋습니다.

![](assets/wf-purge-data-option.png)

## Target 데이터 {#target-data}

워크플로우의 작업 테이블에 저장된 데이터는 개인화 필드에서 액세스할 수 있습니다.

이렇게 하면 목록을 통해 수집한 데이터 또는 배달에서 설문 조사에 대한 답변을 기반으로 데이터를 사용할 수 있습니다. 이렇게 하려면 다음 구문을 사용하십시오.

```
%= targetData.FIELD %
```

**[!UICONTROL Target extension]** (targetData) 유형 개인화 요소는 타깃팅 워크플로우에서 사용할 수 없습니다. 전달 타겟은 워크플로우에서 구축되어야 하며 게재 인바운드 전환에서 지정해야 합니다.

전달 증명 자료를 만들려면 개인화 데이터를 입력할 수 있도록 **[!UICONTROL Address substitution]** 모드를 기반으로 증명 대상을 만들어야 합니다. 자세한 정보는 이 [섹션](../../delivery/using/steps-defining-the-target-population.md#using-address-substitution-in-proof)을 참조하십시오.

다음 예에서는 고객에 대한 정보 목록을 수집하여 개인화된 이메일에 사용할 것입니다.

다음 단계를 적용합니다.

1. 워크플로우를 만들어 정보를 수집하고, 데이터베이스에 있는 데이터와 대사한 다음 배달을 시작합니다.

   ![](assets/wf-targetdata-sample-1.png)

   이 예에서는 파일 컨텐츠가 다음과 같습니다.

   ```
   Music,First name,Last name,Account,CD/DVD,Card
   Pop,David,BLAIR,4323,CD,0
   Rock,Daniel,ARCARI,3222,DVD,1
   Disco,Uma,ALTON,0488,DVD,0
   Jazz,Paul,BOLES,6475,CD,1
   Jazz,David,BOUKHARI,0841,DVD,1
   [...]
   ```

   파일을 로드하려면 다음 단계를 적용합니다.

   ![](assets/wf-targetdata-sample-2.png)

1. 수집된 데이터를 이미 Adobe Campaign 데이터베이스에 있는 데이터와 대사하도록 **[!UICONTROL Enrichment]** 유형 활동을 구성합니다.

   여기에서 조정 키는 계정 번호입니다.

   ![](assets/wf-targetdata-sample-3.png)

1. 그런 다음 다음을 **[!UICONTROL Delivery]**&#x200B;구성합니다.템플릿은 템플릿을 기반으로 생성되며 수신자는 인바운드 전환으로 지정됩니다.

   ![](assets/wf-targetdata-sample-4.png)

   >[!CAUTION]
   >
   >전환 시 포함된 데이터만 전달을 개인화하는 데 사용할 수 있습니다. **targetData** 유형 개인화 필드는 활동의 인바운드 모집단에만 사용할 수 **[!UICONTROL Delivery]** 있습니다.

1. 배달 템플릿에서 수집한 필드를 사용합니다.

   이렇게 하려면 **[!UICONTROL Target extension]** 유형 개인화 필드를 삽입합니다.

   ![](assets/wf-targetdata-sample-5.png)

   워크플로우에서 수집한 파일에 명시된 대로 고객이 가장 좋아하는 음악 장르와 미디어 유형(CD 또는 DVD)을 삽입하려고 합니다.

   게다가, 우리는 &#39;카드&#39; 값이 1인 수신자를 위한 충성도 카드 소지자를 위한 쿠폰을 추가할 예정입니다.

   ![](assets/wf-targetdata-sample-6.png)

   **[!UICONTROL Target extension]** (targetData) 유형 데이터는 모든 개인화 필드와 동일한 특성을 사용하여 게재에 삽입됩니다. 제목, 링크 레이블 또는 링크 자체에서도 사용할 수 있습니다.

   수집된 수신자에게 전송되는 메시지에는 다음 데이터가 포함됩니다.

   ![](assets/wf-targetdata-sample-7.png)
