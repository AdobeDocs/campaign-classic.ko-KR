---
product: campaign
title: 데이터 수명 주기
description: 워크플로우의 데이터 수명 주기에 대해 자세히 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Data Management
exl-id: 366acc1e-d769-4053-9fa1-f47182627c07
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 5%

---

# 데이터 수명 주기 {#data-life-cycle}



## 작업 테이블 {#work-table}

워크플로우에서 한 활동에서 다른 활동으로 전송된 데이터는 임시 작업 표에 저장됩니다.

해당 전환을 마우스 오른쪽 버튼으로 클릭하여 이 데이터를 표시하고 분석할 수 있습니다.

![](assets/wf-right-click-analyze.png)

이렇게 하려면 관련 메뉴를 선택합니다.

* 대상 표시

   이 메뉴에는 대상 모집단에서 사용 가능한 데이터와 작업 테이블(**[!UICONTROL Schema]** 탭).

   ![](assets/wf-right-click-display.png)

   자세한 내용은 다음을 참조하십시오. [작업 테이블 및 워크플로 스키마](monitoring-workflow-execution.md#worktables-and-workflow-schema).

* 대상 분석

   이 메뉴를 사용하여 전환 데이터에 대한 통계 및 보고서를 작성할 수 있는 설명 분석 마법사에 액세스할 수 있습니다.

   자세한 정보는 이 [섹션](../../reporting/using/using-the-descriptive-analysis-wizard.md)을 참조하십시오.

워크플로우가 실행되면 대상 데이터가 제거됩니다. 마지막 작업 테이블만 액세스할 수 있습니다. 모든 작업 테이블에 액세스할 수 있도록 워크플로를 구성할 수 있습니다. 다음을 확인하십시오. **[!UICONTROL Keep the result of interim populations between two executions]** 옵션을 선택합니다.

그러나 대량의 데이터가 있는 경우에는 이 옵션을 활성화하지 않는 것이 좋습니다.

![](assets/wf-purge-data-option.png)

## 타겟 데이터 {#target-data}

워크플로우의 작업 테이블에 저장된 데이터는 개인화 필드에서 액세스할 수 있습니다.

이렇게 하면 목록을 통해 또는 게재의 설문 조사에 대한 답변을 기반으로 수집된 데이터를 사용할 수 있습니다. 이렇게 하려면 다음 구문을 사용합니다.

```
%= targetData.FIELD %
```

**[!UICONTROL Target extension]** (targetData) 유형 개인화 요소는 타깃팅 워크플로우에 사용할 수 없습니다. 게재 대상은 워크플로우에 빌드되고 게재의 인바운드 전환에서 지정되어야 합니다.

게재 증명을 만들려면 다음을 기반으로 증명 대상을 빌드해야 합니다. **[!UICONTROL Address substitution]** 을 입력하여 개인화 데이터를 입력할 수 있습니다. 자세한 정보는 이 [섹션](../../delivery/using/steps-defining-the-target-population.md#using-address-substitution-in-proof)을 참조하십시오.

다음 예제에서는 개인화된 전자 메일에 사용할 고객에 대한 정보 목록을 수집하려고 합니다.

다음 단계를 적용합니다.

1. 정보를 수집할 워크플로우를 만들고 데이터베이스에 이미 있는 데이터와 조정한 다음 게재를 시작합니다.

   ![](assets/wf-targetdata-sample-1.png)

   이 예제에서 파일 콘텐츠는 다음과 같습니다.

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

1. 구성 **[!UICONTROL Enrichment]** activity를 입력하여 수집된 데이터를 Adobe Campaign 데이터베이스에 이미 있는 데이터와 조정합니다.

   여기서 조정 키는 계정 번호입니다.

   ![](assets/wf-targetdata-sample-3.png)

1. 그런 다음 을(를) 구성합니다 **[!UICONTROL Delivery]**: 템플릿을 기반으로 생성되며 수신자는 인바운드 전환에 의해 지정됩니다.

   ![](assets/wf-targetdata-sample-4.png)

   >[!CAUTION]
   >
   >전환에 포함된 데이터만 게재를 개인화하는 데 사용할 수 있습니다. **targetData** 유형 개인화 필드는 의 인바운드 모집단에만 사용할 수 있습니다. **[!UICONTROL Delivery]** 활동.

1. 게재 템플릿에서 워크플로우에서 수집된 필드를 사용합니다.

   이렇게 하려면 를 삽입합니다. **[!UICONTROL Target extension]** 개인화 필드를 입력합니다.

   ![](assets/wf-targetdata-sample-5.png)

   여기에서는 워크플로우에서 수집한 파일에 명시된 대로 고객이 좋아하는 음악 장르와 미디어 유형(CD 또는 DVD)을 삽입하려고 합니다.

   추가로, 우리는 충성도 카드 소지자, 즉 &#39;카드&#39; 값이 1인 수신자를 위한 쿠폰을 추가할 것입니다.

   ![](assets/wf-targetdata-sample-6.png)

   **[!UICONTROL Target extension]** (targetData) 유형 데이터는 모든 개인화 필드와 동일한 특성을 사용하여 게재에 삽입됩니다. 제목, 링크 레이블 또는 링크 자체에서도 사용할 수 있습니다.

   수집된 수신자에게 보내는 메시지에는 다음 데이터가 포함됩니다.

   ![](assets/wf-targetdata-sample-7.png)
