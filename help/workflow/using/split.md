---
product: campaign
title: 분할
description: 분할 워크플로우 활동에 대해 자세히 알아보기
feature: Workflows, Targeting Activity
exl-id: 4204350a-c2d2-4033-9bdf-87b49d8211b9
source-git-commit: 13eb777e96602ddd3463f721c6b2a3e6b67cb329
workflow-type: tm+mt
source-wordcount: '1971'
ht-degree: 3%

---

# 분할{#split}

**분할** 유형의 활동을 사용하면 대상을 여러 하위 집합으로 분할할 수 있습니다. 타겟은 받은 모든 결과로 구성됩니다. 따라서 이 활동을 실행하려면 모든 이전 활동이 완료되어야 합니다.

이 활동은 인바운드 모집단의 결합을 트리거하지 않습니다. 여러 전환이 하나의 분할 활동에 랜딩되는 경우 앞에 **[!UICONTROL Union]** 활동을 삽입하는 것이 좋습니다.

>[!NOTE]
>
>소스가 다른 테이블에 대해서는 분할 작업을 수행할 수 없습니다. 이를 위해 **분할** 활동 전에 **데이터 보강** 활동을 추가해야 합니다.

* 사용 중인 분할 활동의 예를 보려면 [분할 활동을 사용하여 하위 집합 만들기](targeting-data.md#creating-subsets-using-the-split-activity)를 참조하십시오.
* 필터링 조건을 사용하여 Split 활동을 사용하여 대상을 다른 모집단으로 세분화하는 방법에 대한 예제는 [이 섹션](cross-channel-delivery-workflow.md)에 설명되어 있습니다.
* 분할 활동에서 인스턴스 변수를 사용하는 방법을 보여 주는 예는 [이 섹션](javascript-scripts-and-templates.md)에서 확인할 수 있습니다.

이 활동을 구성하려면 **[!UICONTROL Subsets]** 탭에서 하위 집합 콘텐츠와 레이블을 정의한 다음 **[!UICONTROL General]** 탭에서 대상 차원을 선택합니다.

## 하위 집합 만들기 {#creating-subsets}

하위 집합을 생성하려면 다음을 수행합니다.

1. 일치 필드에서 레이블을 클릭하고 적용할 필터를 선택합니다.
1. 인바운드 모집단을 필터링하려면 **[!UICONTROL Add a filtering condition]** 옵션을 선택하고 **[!UICONTROL Edit...]** 링크를 클릭하십시오.

   이 집합에 포함할 데이터에 적용할 필터 유형을 선택합니다.

   프로세스는 **쿼리** 유형 활동과 동일합니다.

   >[!NOTE]
   >
   >최대 2개의 외부 데이터베이스(FDA)에서 데이터를 필터링할 수 있습니다.

1. 대상에서 추출할 최대 레코드 수를 지정하여 하위 집합을 만들 수 있습니다. 이렇게 하려면 **[!UICONTROL Limit the selected records]** 옵션을 선택하고 **[!UICONTROL Edit...]** 링크를 클릭하십시오.

   마법사를 사용하여 이 하위 집합의 레코드에 대한 선택 모드를 선택할 수 있습니다. [하위 집합 레코드 수 제한](#limiting-the-number-of-subset-records)에서 단계를 찾을 수 있습니다.

   ![](assets/s_user_segmentation_partage4.png)

1. 원하는 경우 **[!UICONTROL Add]** 단추를 사용하여 **다른 하위 집합을 추가**&#x200B;할 수 있습니다.

   ![](assets/s_user_segmentation_partage_add.png)

   >[!NOTE]
   >
   >**[!UICONTROL Enable overlapping of output populations]** 옵션을 선택하지 않으면 탭 순서대로 하위 집합이 만들어집니다. 이 창의 오른쪽 상단에 있는 화살표를 사용하여 이동합니다. 예를 들어 첫 번째 하위 집합이 초기 모집단의 70%를 복구하는 경우 다음 하위 집합은 나머지 30%에만 선택 기준을 적용합니다.

   생성된 각 하위 세트에 대해 아웃바운드 전환이 분할 활동에 추가됩니다.

   ![](assets/s_user_segmentation_partage_add2.png)

   단일 아웃바운드 전환을 생성하도록 선택하고(예: 세그먼트 코드를 사용하여 집합 식별), 이렇게 하려면 **[!UICONTROL General]** 탭에서 **[!UICONTROL Generate subsets in the same table]** 옵션을 선택합니다.

   완료되면, 각 서브셋의 세그먼트 코드는 자동으로 추가 열에 저장된다. 이 열은 게재 수준의 개인화 필드에서 액세스할 수 있습니다.

## 하위 집합 레코드 수 제한 {#limiting-the-number-of-subset-records}

하위 집합에 포함된 전체 모집단을 사용하지 않으려면 포함될 레코드 수를 제한할 수 있습니다.

1. 하위 집합 편집 창에서 **[!UICONTROL Limit the selected records]** 옵션을 선택하고 **[!UICONTROL Edit...]** 링크를 클릭합니다.
1. 선택한 제한 유형을 선택합니다.

   * **[!UICONTROL Activate random sampling]**: 이 옵션은 임의 레코드 샘플을 가져옵니다. 적용되는 임의 샘플링 유형은 데이터베이스 엔진에 따라 다릅니다.
   * **[!UICONTROL Keep only the first records after sorting]**: 이 옵션을 사용하면 하나 이상의 정렬 순서에 따라 제한을 정의할 수 있습니다. **[!UICONTROL Age]** 필드를 정렬 기준으로 선택하고 100개를 제한으로 선택하면 가장 최신 받는 사람 100명만 유지됩니다.
   * **[!UICONTROL Keep the first ones after sorting (criteria, random)]**: 이 옵션은 앞의 두 옵션을 결합합니다. 하나 이상의 정렬 순서에 따라 제한을 정의한 다음, 일부 레코드가 정의된 기준과 동일한 값을 갖는 경우 첫 번째 레코드에 무작위 선택을 적용할 수 있습니다.

     예를 들어 **[!UICONTROL Age]** 필드를 정렬 기준으로 선택한 다음 제한을 100개로 정의한 경우 데이터베이스의 가장 최연소 수신자 2000명이 모두 18개이면 2000명 중 100명의 수신자가 임의로 선택됩니다.

   ![](assets/s_user_segmentation_partage_wz1.png)

1. 정렬 기준을 정의하려면 추가 단계를 통해 열과 정렬 순서를 정의할 수 있습니다.

   ![](assets/s_user_segmentation_partage_wz1.1.png)

1. 그런 다음 데이터 제한 방법을 선택합니다.

   ![](assets/s_user_segmentation_partage_wz2.png)

   다음과 같은 몇 가지 방법이 있습니다.

   * **[!UICONTROL Size (in %)]**: 레코드 비율입니다. 예를 들어 아래 구성은 전체 모집단의 10%를 추출합니다.

     백분율은 활동의 결과가 아닌 초기 모집단에 적용됩니다.

   * **[!UICONTROL Size (as a % of the segment)]**: 하위 집합에만 관련되고 초기 모집단과 관련되지 않은 레코드의 백분율입니다.
   * **[!UICONTROL Maximum size]**: 최대 레코드 수입니다.
   * **[!UICONTROL By data grouping]**: 인바운드 모집단의 지정된 필드에 있는 값에 따라 레코드 수에 대한 제한을 설정할 수 있습니다. 이 주제에 대한 자세한 내용은 [데이터 그룹화별로 하위 집합 레코드 수 제한](#limiting-the-number-of-subset-records-by-data-grouping)을 참조하세요.
   * **[!UICONTROL By data grouping (in %)]**: 백분율을 사용하여 인바운드 모집단의 지정된 필드에 있는 값에 따라 레코드 수에 대한 제한을 설정할 수 있습니다. 이 주제에 대한 자세한 내용은 [데이터 그룹화별로 하위 집합 레코드 수 제한](#limiting-the-number-of-subset-records-by-data-grouping)을 참조하세요.
   * **[!UICONTROL By data distribution]**: 그룹화 필드에 값이 너무 많거나 각 새 분할 활동에 대해 값을 다시 입력하지 않으려면 Adobe Campaign에서 **[!UICONTROL By data distribution]** 제한을 구성할 수 있습니다(선택적 분산 마케팅 모듈). 자세한 내용은 [데이터 배포당 하위 집합 레코드 수 제한](#limiting-the-number-of-subset-records-per-data-distribution)을 참조하세요.

1. 레코드 선택 조건을 승인하려면 **[!UICONTROL Finish]**&#x200B;을(를) 클릭하십시오. 그러면 정의된 구성이 편집기의 중간 창에 표시됩니다.

## 데이터 그룹화로 하위 집합 레코드 수 제한 {#limiting-the-number-of-subset-records-by-data-grouping}

데이터 그룹화별로 레코드 수를 제한할 수 있습니다. 이 제한은 고정된 값 또는 백분율을 사용하여 수행할 수 있습니다.

예를 들어 **[!UICONTROL Language]** 필드를 그룹 필드로 선택하는 경우 각 언어에 대한 레코드 목록을 정의할 수 있습니다.

1. 데이터 제한 값을 선택한 후 **[!UICONTROL By data grouping]** 또는 **[!UICONTROL By data grouping (as a %)]**&#x200B;을(를) 선택하고 **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다.

   ![](assets/s_user_segmentation_partage_wz3.png)

1. 그런 다음 그룹화 필드(인스턴스의 경우 **[!UICONTROL Language]** 필드)를 선택하고 **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다.

   ![](assets/s_user_segmentation_partage_wz4.png)

1. 마지막으로 데이터 그룹화 임계값을 지정합니다(이전에 선택한 그룹화 방법에 따라 고정된 값 또는 백분율을 사용). 각 언어에 대한 레코드 수를 10개로 설정하려면 **[!UICONTROL All data groupings are the same size]** 옵션을 선택하십시오. 모든 값에 대해 다른 제한을 설정하려면 **[!UICONTROL Limitations by grouping value]** 옵션을 선택하십시오. 이렇게 하면 영어, 프랑스어 등에 대한 다른 제한을 선택할 수 있습니다.

   ![](assets/s_user_segmentation_partage_wz5.png)

1. 제한을 승인하고 분할 활동 편집으로 돌아가려면 **[!UICONTROL Finish]**&#x200B;을(를) 클릭하십시오.

## 데이터 배포당 하위 집합 레코드 수 제한 {#limiting-the-number-of-subset-records-per-data-distribution}

그룹화 필드에 너무 많은 값이 포함되어 있거나 모든 새 분할 활동에 대해 값을 재설정하지 않으려는 경우 Adobe Campaign을 사용하여 데이터 분포별로 제한을 만들 수 있습니다. 데이터 제한 값을 선택할 때(이 주제에 대한 자세한 내용은 [하위 집합 만들기](#creating-subsets) 섹션 참조) **[!UICONTROL By data distribution]** 옵션을 선택하고 드롭다운 메뉴에서 템플릿을 선택합니다. 데이터 배포 템플릿 만들기는 아래에 나와 있습니다.

배포 템플릿을 사용하는 **[!UICONTROL Local approval]** 활동의 예를 보려면 [로컬 승인 활동 사용](using-the-local-approval-activity.md)을 참조하세요.

![](assets/s_user_segmentation_partage_wz6.png)

>[!IMPORTANT]
>
>이 기능을 사용하려면 Campaign 옵션인 분산 마케팅 모듈을 구매해야 합니다. 사용권 계약을 확인하십시오.

데이터 배포 템플릿을 사용하면 그룹화 값 목록을 사용하여 레코드 수를 제한할 수 있습니다. 데이터 배포 템플릿을 만들려면 다음 단계를 적용합니다.

1. 데이터 배포 템플릿을 만들려면 **[!UICONTROL Resources > Campaign management > Data distribution]** 노드로 이동하여 **[!UICONTROL New]**&#x200B;을(를) 클릭합니다.

   ![](assets/local_validation_data_distribution_1.png)

1. **[!UICONTROL General]** 탭에서 배포의 레이블 및 실행 컨텍스트(타깃팅 차원, 배포 필드)를 입력할 수 있습니다.

   ![](assets/local_validation_data_distribution_2.png)

   다음 필드를 입력해야 합니다.

   * **[!UICONTROL Label]**: 배포 템플릿에 대한 레이블입니다.
   * **[!UICONTROL Targeting dimension]**: 데이터 배포를 적용할 대상 차원을 입력하십시오(예: **[!UICONTROL Recipient]**). 이 스키마는 항상 타겟팅 워크플로우에서 사용되는 데이터와 호환되어야 합니다.
   * **[!UICONTROL Distribution field]**: 타겟팅 차원을 통해 필드를 선택합니다. 예를 들어 **[!UICONTROL Email domain]** 필드를 선택하면 수신자 목록이 도메인별로 분류됩니다.
   * **[!UICONTROL Distribution type]**: **[!UICONTROL Distribution]** 탭에서 대상의 제한 값을 분류하는 방법을 선택하십시오. **[!UICONTROL Percentage]** 또는 **[!UICONTROL Set]**.
   * **[!UICONTROL Assignment type]**: 데이터 배포 할당 유형을 선택하십시오. 그룹별 또는 연산자별 지정과 로컬 개체별 지정 중에서 선택할 수 있습니다. 로컬 엔터티별 할당은 **분산 마케팅**&#x200B;에서 사용됩니다. 자세한 정보는 이 [섹션](../../distributed/using/about-distributed-marketing.md)을 참조하세요.
   * **[!UICONTROL Approval storage]**: 타깃팅 워크플로우에서 **[!UICONTROL Local approval]** 활동을 사용하는 경우([로컬 승인](local-approval.md) 참조) 승인 결과가 저장될 스키마를 입력하십시오. 타깃팅 스키마당 하나의 저장소 스키마를 지정해야 합니다. **[!UICONTROL Recipients]** 대상 스키마를 사용하는 경우 기본 **[!UICONTROL Local approval of recipients]** 저장소 스키마를 입력하십시오.

     로컬 승인 없이 데이터 그룹화로 간단하게 제한하는 경우 **[!UICONTROL Approvals storage]** 필드를 입력할 필요가 없습니다.

1. **[!UICONTROL Local approval]** 활동을 사용하는 경우([로컬 승인](local-approval.md) 참조) 배포 템플릿에 대한 **[!UICONTROL Advanced settings]**&#x200B;을(를) 입력하십시오.

   ![](assets/local_validation_data_distribution_3.png)

   다음 필드를 입력해야 합니다.

   * **[!UICONTROL Approve targeted messages]**: 승인할 받는 사람 목록에서 모든 받는 사람을 미리 선택하려면 이 옵션을 선택하십시오. 이 옵션을 선택 취소하면 수신자를 미리 선택하지 않습니다.

     >[!NOTE]
     >
     >이 옵션은 기본적으로 선택되어 있습니다.

     ![](assets/local_validation_notification.png)

   * **[!UICONTROL Delivery label]**: 반환 알림에 게재 레이블을 표시하는 식을 정의할 수 있습니다. 기본 표현식은 게재의 표준 레이블(계산 문자열)에 대한 정보를 제공합니다. 이 표현식은 수정할 수 있습니다.

     ![](assets/local_validation_notification_3.png)

   * **[!UICONTROL Grouping field]**: 이 필드를 사용하면 승인 및 반송 알림에 수신자를 표시하는 데 사용되는 그룹화를 정의할 수 있습니다.

     ![](assets/local_validation_notification_4.png)

   * **[!UICONTROL Web Interface]**: 웹 응용 프로그램을 받는 사람 목록에 연결할 수 있습니다. 승인 및 반환 알림에서 각 수신자는 클릭할 수 있고 선택한 웹 애플리케이션에 연결됩니다. **[!UICONTROL Parameters]** 필드(예: **[!UICONTROL recipientId]**)를 사용하면 URL 및 웹 애플리케이션에서 사용할 추가 매개 변수를 구성할 수 있습니다.

     ![](assets/local_validation_notification_5.png)

1. **[!UICONTROL Breakdown]** 탭에서는 배포 값 목록을 정의할 수 있습니다.

   ![](assets/local_validation_data_distribution_4.png)

   * **[!UICONTROL Value]**: 배포 값을 입력하십시오.
   * **[!UICONTROL Percentage / Set]**: 각 값에 연결된 레코드 제한(고정 또는 백분율)을 입력하십시오.

     이 열은 **[!UICONTROL General]** 탭의 **[!UICONTROL Distribution type]** 필드에 의해 정의됩니다.

   * **[!UICONTROL Label]**: 각 값에 연결된 레이블을 입력합니다.
   * **[!UICONTROL Group or operator]**: **[!UICONTROL Local approval]** 활동을 사용하는 경우([로컬 승인](local-approval.md) 참조) 각 배포 값에 할당된 연산자 또는 연산자 그룹을 선택하십시오.

     로컬 승인 없이 데이터 그룹화로 간단하게 제한하는 경우 **[!UICONTROL Group or operator]** 필드를 입력할 필요가 없습니다.

     >[!IMPORTANT]
     >
     >운영자에게 적절한 권한이 할당되었는지 확인합니다.

   * **[!UICONTROL Local entity]**: 각 배포 값에 할당된 로컬 엔터티를 선택하십시오. 로컬 엔터티가 **분산 마케팅**&#x200B;에서 사용됩니다. 자세한 정보는 이 [섹션](../../distributed/using/about-distributed-marketing.md)을 참조하세요.

## 매개 변수 필터링 {#filtering-parameters}

**[!UICONTROL General]** 탭을 클릭하여 활동 레이블을 입력합니다. 이 분할에 대한 대상 및 필터 차원을 선택합니다. 필요한 경우 주어진 하위 집합에 대해 이러한 차원을 변경할 수 있습니다.

![](assets/s_user_segmentation_partage_general.png)

나머지 모집단을 활용하려면 **[!UICONTROL Generate complement]** 옵션을 선택하십시오. 보수는 인바운드 대상에서 하위 집합의 결합을 뺀 것입니다. 그러면 다음과 같이 추가 아웃바운드 전환이 활동에 추가됩니다.

![](assets/s_user_segmentation_partage_compl.png)

이 옵션이 제대로 작동하려면 인바운드 데이터에 기본 키가 있어야 합니다.

예를 들어, **[!UICONTROL Data loading (RDBMS)]** 활동을 통해 Netezza(인덱스 개념을 지원하지 않음)과 같은 외부 데이터베이스에서 직접 데이터를 읽으면 **[!UICONTROL Split]** 활동으로 생성된 보조 데이터가 올바르지 않습니다.

이를 방지하기 위해 **[!UICONTROL Enrichment]** 활동을 **[!UICONTROL Split]** 활동 바로 앞에 끌어다 놓을 수 있습니다. **[!UICONTROL Enrichment]** 활동에서 **[!UICONTROL Keep all additional data from the main set]**&#x200B;을(를) 확인하고 추가 데이터에 **[!UICONTROL Split]** 활동의 필터를 구성하는 데 사용할 열을 지정합니다. 그런 다음 **[!UICONTROL Split]** 활동의 인바운드 전환에서 가져온 데이터가 Adobe Campaign 서버의 임시 테이블에 로컬로 저장되고 보조 항목을 올바르게 생성할 수 있습니다.

**[!UICONTROL Enable overlapping of output populations]** 옵션을 사용하면 여러 하위 집합에 속하는 모집단을 관리할 수 있습니다.

* 확인란을 선택하지 않으면 분할 활동은 수신자가 여러 하위 집합의 기준을 충족하더라도 여러 출력 전환에 표시되지 않습니다. 첫 번째 탭의 타겟에서 기준이 일치합니다.
* 확인란을 선택하면 필터 기준을 충족하는 경우 여러 하위 집합에서 수신자를 찾을 수 있습니다. Adobe Campaign에서는 전용 기준을 사용할 것을 권장합니다.

## 입력 매개 변수 {#input-parameters}

* tableName
* 스키마

각 인바운드 이벤트는 이러한 매개 변수로 정의된 대상을 지정해야 합니다.

## 출력 매개 변수 {#output-parameters}

* tableName
* 스키마
* recCount

이 세 값 세트는 제외로 인한 대상을 식별합니다. **[!UICONTROL tableName]**&#x200B;은(는) 대상 식별자를 기록하는 테이블의 이름이고, **[!UICONTROL schema]**&#x200B;은(는) 모집단의 스키마(일반적으로 nms:recipient)이며, **[!UICONTROL recCount]**&#x200B;은(는) 테이블의 요소 수입니다.

보체와 관련된 전환은 동일한 매개 변수를 갖는다.
