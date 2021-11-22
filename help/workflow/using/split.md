---
product: campaign
title: 분할
description: 분할 워크플로우 활동에 대해 자세히 알아보기
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: 4204350a-c2d2-4033-9bdf-87b49d8211b9
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1935'
ht-degree: 0%

---

# 분할{#split}

![](../../assets/common.svg)

A **분할**-type 활동을 통해 대상을 여러 하위 집합으로 분할할 수 있습니다. 대상이 수신된 모든 결과로 구성됩니다. 따라서 이 활동을 실행하려면 모든 이전 활동이 완료되었어야 합니다.

이 활동은 인바운드 모집단의 결합을 트리거하지 않습니다. 여러 전환이 하나의 분할 활동에 도달하는 경우 **[!UICONTROL Union]** 활동 앞에 표시하십시오.

사용 중인 분할 활동의 예는 를 참조하십시오 [분할 활동을 사용하여 하위 집합 만들기](targeting-data.md#creating-subsets-using-the-split-activity).

분할 활동을 사용하여 필터링 조건을 사용하여 대상을 다른 모집단으로 세그먼트화하는 방법을 설명하는 예가 나와 있습니다. [이 섹션](cross-channel-delivery-workflow.md).

분할 활동에서 인스턴스 변수를 사용하는 방법을 보여주는 예는 를 사용할 수 있습니다. [이 섹션](javascript-scripts-and-templates.md).

이 활동을 구성하려면 의 하위 집합 콘텐츠 및 레이블을 정의합니다 **[!UICONTROL Subsets]** 탭을 클릭한 다음, **[!UICONTROL General]** 탭.

## 하위 집합 만들기 {#creating-subsets}

하위 집합을 생성하려면

1. 일치하는 필드에서 레이블을 클릭하고 적용할 필터를 선택합니다.
1. 인바운드 모집단을 필터링하려면 **[!UICONTROL Add a filtering condition]** 옵션을 선택하고 **[!UICONTROL Edit...]** 링크를 클릭합니다.

   이 세트에 포함할 데이터에 적용할 필터 유형을 선택합니다.

   프로세스는 와 동일합니다 **쿼리**-type activity.

   >[!NOTE]
   >
   >최대 두 개의 외부 데이터베이스(FDA)로 데이터를 필터링할 수 있습니다.

1. 대상에서 추출할 최대 레코드 수를 지정하여 하위 집합을 만들 수 있습니다. 이렇게 하려면 **[!UICONTROL Limit the selected records]** 옵션을 선택하고 **[!UICONTROL Edit...]** 링크를 클릭합니다.

   마법사를 사용하여 이 하위 집합의 레코드에 대한 선택 모드를 선택할 수 있습니다. 단계는 [하위 집합 레코드 수 제한](#limiting-the-number-of-subset-records).

   ![](assets/s_user_segmentation_partage4.png)

1. 원한다면 **다른 하위 집합 추가** 사용 **[!UICONTROL Add]** 버튼을 클릭합니다.

   ![](assets/s_user_segmentation_partage_add.png)

   >[!NOTE]
   >
   >만약 **[!UICONTROL Enable overlapping of output populations]** 옵션을 선택하지 않으면 탭의 순서로 하위 세트가 생성됩니다. 이 창의 오른쪽 위 섹션에 있는 화살표를 사용하여 이동합니다. 첫 번째 하위 집합에서 초기 모집단의 70%를 복구하는 경우, 예를 들어 다음 하위 집합에서는 나머지 30%에만 선택 기준을 적용합니다.

   만들어진 각 하위 세트에 대해 아웃바운드 전환이 분할 활동에 추가됩니다.

   ![](assets/s_user_segmentation_partage_add2.png)

   단일 아웃바운드 전환을 생성하고 세그먼트 코드를 사용하여 세트를 식별하도록 선택할 수 있습니다(예: ). 이렇게 하려면 을(를) 선택합니다 **[!UICONTROL Generate subsets in the same table]** 옵션 **[!UICONTROL General]** 탭.

   완료되면 각 하위 세트의 세그먼트 코드가 추가 열에 자동으로 저장됩니다. 이 열은 배달 수준의 개인화 필드에서 액세스할 수 있습니다.

## 하위 집합 레코드 수 제한 {#limiting-the-number-of-subset-records}

하위 집합에 포함된 전체 모집단을 사용하지 않으려면 포함할 레코드 수를 제한할 수 있습니다.

1. 하위 집합 편집 창에서 **[!UICONTROL Limit the selected records]** 옵션을 선택하고 **[!UICONTROL Edit...]** 링크를 클릭합니다.
1. 선택한 제한 유형을 선택합니다.

   * **[!UICONTROL Activate random sampling]**: 이 옵션은 임의의 레코드 샘플을 사용합니다. 적용된 임의 샘플링 유형은 데이터베이스 엔진에 따라 다릅니다.
   * **[!UICONTROL Keep only the first records after sorting]**: 이 옵션을 사용하면 하나 이상의 정렬 명령을 기준으로 제한을 정의할 수 있습니다. 을(를) 선택하는 경우 **[!UICONTROL Age]** 필드를 정렬 기준으로 사용하고 100을 제한으로 사용할 경우 가장 어린 100명의 수신자만 유지됩니다.
   * **[!UICONTROL Keep the first ones after sorting (criteria, random)]**: 이 옵션은 앞의 두 옵션을 결합합니다. 이를 통해 하나 이상의 정렬 명령을 기준으로 제한을 정의한 다음, 일부 레코드가 정의된 기준과 동일한 값을 갖는 경우 첫 번째 레코드에 임의 선택을 적용할 수 있습니다.

      예를 들어 **[!UICONTROL Age]** 필드를 정렬 기준으로 정의하고 제한을 100으로 정의하지만 데이터베이스에 있는 2000명의 가장 젊은 수신자는 모두 18명이고 그 다음 100명의 수신자는 이 2000명 중에서 임의로 선택됩니다.
   ![](assets/s_user_segmentation_partage_wz1.png)

1. 정렬 기준을 정의하려면 추가 단계를 사용하여 열과 정렬 순서를 정의할 수 있습니다.

   ![](assets/s_user_segmentation_partage_wz1.1.png)

1. 그런 다음 데이터 제한 방법을 선택합니다.

   ![](assets/s_user_segmentation_partage_wz2.png)

   다음과 같은 여러 가지 방법으로 데이터를 수집할 수 있습니다.

   * **[!UICONTROL Size (in %)]**: 레코드 백분율입니다. 예를 들어 아래 구성은 전체 모집단의 10%를 추출합니다.

      백분율은 활동 결과가 아니라 초기 모집단에 적용됩니다.

   * **[!UICONTROL Size (as a % of the segment)]**: 초기 모집단과 관련이 없고 하위 세트에만 관련된 레코드의 백분율입니다.
   * **[!UICONTROL Maximum size]**: 최대 레코드 수입니다.
   * **[!UICONTROL By data grouping]**: 인바운드 모집단의 지정된 필드에 있는 값에 따라 레코드 수에 대한 제한을 설정할 수 있습니다. 이 주제에 대한 자세한 내용은 [데이터 그룹별로 하위 집합 레코드 수를 제한합니다.](#limiting-the-number-of-subset-records-by-data-grouping).
   * **[!UICONTROL By data grouping (in %)]**: 백분율을 사용하여 인바운드 모집단의 지정된 필드에 있는 값에 따라 레코드 수에 대한 제한을 설정할 수 있습니다. 이 주제에 대한 자세한 내용은 [데이터 그룹별로 하위 집합 레코드 수를 제한합니다.](#limiting-the-number-of-subset-records-by-data-grouping).
   * **[!UICONTROL By data distribution]**: 그룹화 필드에 값이 너무 많거나 새로운 분할 활동에 대해 값을 다시 입력하지 않으려면 Adobe Campaign을 사용하여 **[!UICONTROL By data distribution]** 제한 사항(선택적 분산 마케팅 모듈). 자세한 내용은 [데이터 배포당 하위 집합 레코드 수 제한](#limiting-the-number-of-subset-records-per-data-distribution).

1. 클릭 **[!UICONTROL Finish]** 레코드 선택 기준을 승인하려면 다음을 수행하십시오. 그러면 정의된 구성이 편집기의 가운데 창에 표시됩니다.

## 데이터 그룹별로 하위 집합 레코드 수를 제한합니다. {#limiting-the-number-of-subset-records-by-data-grouping}

데이터 그룹별로 레코드 수를 제한할 수 있습니다. 이 제한은 고정 값 또는 백분율을 사용하여 수행할 수 있습니다.

예를 들어, **[!UICONTROL Language]** 필드를 그룹 필드로 사용하여 각 언어의 레코드 목록을 정의할 수 있습니다.

1. 데이터 제한 값을 선택한 후 **[!UICONTROL By data grouping]** 또는 **[!UICONTROL By data grouping (as a %)]** 을(를) 클릭합니다. **[!UICONTROL Next]**.

   ![](assets/s_user_segmentation_partage_wz3.png)

1. 그런 다음 그룹화 필드( **[!UICONTROL Language]** 예를 들어 필드를 클릭한 다음 **[!UICONTROL Next]**.

   ![](assets/s_user_segmentation_partage_wz4.png)

1. 마지막으로, 이전에 선택한 그룹화 방법에 따라 고정 값이나 백분율을 사용하여 데이터 그룹화 임계값을 지정합니다. 모든 값에 대해 동일한 임계값을 설정하려면(예: 각 언어에 대한 레코드 수를 10으로 설정하려면) **[!UICONTROL All data groupings are the same size]** 선택 사항입니다. 모든 값에 대해 다른 제한을 설정하려면 **[!UICONTROL Limitations by grouping value]** 선택 사항입니다. 이를 통해 영어, 프랑스어 등에 대해 다른 제한을 선택할 수 있습니다.

   ![](assets/s_user_segmentation_partage_wz5.png)

1. 클릭 **[!UICONTROL Finish]** 제한을 승인하고 분할 활동 편집으로 돌아가려면 을 클릭합니다.

## 데이터 배포당 하위 집합 레코드 수 제한 {#limiting-the-number-of-subset-records-per-data-distribution}

그룹화 필드에 값이 너무 많거나 새로운 분할 활동에 대한 값 재설정을 방지하려면 Adobe Campaign에서 데이터 배포당 제한을 만들 수 있습니다. 데이터 제한 값을 선택할 때(이 주제에 대한 자세한 내용은 [하위 집합 만들기](#creating-subsets) 섹션)에서 **[!UICONTROL By data distribution]** 옵션을 선택하고 드롭다운 메뉴에서 템플릿을 선택합니다. 데이터 배포 템플릿을 만드는 방법은 아래에 나와 있습니다.

예 **[!UICONTROL Local approval]** 배포 템플릿을 사용하는 활동은 [로컬 승인 활동 사용](using-the-local-approval-activity.md).

![](assets/s_user_segmentation_partage_wz6.png)

>[!IMPORTANT]
>
>이 기능을 사용하려면 캠페인 옵션인 분산 마케팅 모듈을 구매해야 합니다. 사용권 계약을 확인하십시오.

데이터 배포 템플릿을 사용하면 그룹화 값 목록을 사용하여 레코드 수를 제한할 수 있습니다. 데이터 배포 템플릿을 만들려면 다음 단계를 적용합니다.

1. 데이터 배포 템플릿을 만들려면 다음 위치로 이동합니다. **[!UICONTROL Resources > Campaign management > Data distribution]** 노드 및 **[!UICONTROL New]**.

   ![](assets/local_validation_data_distribution_1.png)

1. 다음 **[!UICONTROL General]** 탭에서는 분포의 레이블 및 실행 컨텍스트(타겟팅 차원, 배포 필드)를 입력할 수 있습니다.

   ![](assets/local_validation_data_distribution_2.png)

   다음 필드를 입력해야 합니다.

   * **[!UICONTROL Label]**: 배포 템플릿에 대한 레이블입니다.
   * **[!UICONTROL Targeting dimension]**: 데이터 배포를 적용할 타겟팅 차원을 입력합니다. **[!UICONTROL Recipient]** 예를 들어, 이 스키마는 항상 타겟팅 워크플로우에 사용되는 데이터와 호환되어야 합니다.
   * **[!UICONTROL Distribution field]**: 타겟팅 차원을 통해 필드를 선택합니다. 예를 들어, **[!UICONTROL Email domain]** 필드에서는 수신자 목록이 도메인별로 분류됩니다.
   * **[!UICONTROL Distribution type]**: 대상에서 제한 값이 **[!UICONTROL Distribution]** 탭: **[!UICONTROL Percentage]** 또는 **[!UICONTROL Set]**.
   * **[!UICONTROL Assignment type]**: 데이터 분배 지정 유형을 선택합니다. 그룹별 지정 또는 연산자별 지정 또는 로컬 엔티티별 지정 중에서 선택할 수 있습니다. 로컬 엔티티별 할당은 **분산 마케팅**. 자세한 내용은 다음을 참조하십시오 [섹션](../../distributed/using/about-distributed-marketing.md).
   * **[!UICONTROL Approval storage]**: 만약 **[!UICONTROL Local approval]** 타겟팅 워크플로우에서 활동( [로컬 승인](local-approval.md))에서 승인 결과를 저장할 스키마를 입력합니다. 대상 스키마당 하나의 저장소 스키마를 지정해야 합니다. 를 사용하는 경우 **[!UICONTROL Recipients]** 타겟팅 스키마, 기본 입력 **[!UICONTROL Local approval of recipients]** 저장소 스키마.

      로컬 승인 없이 데이터 그룹화로 간단하게 제한되는 경우 **[!UICONTROL Approvals storage]** 필드.

1. 를 사용 중인 경우 **[!UICONTROL Local approval]** 활동(참조) [로컬 승인](local-approval.md)), 을 입력합니다. **[!UICONTROL Advanced settings]** 배포 템플릿의 경우:

   ![](assets/local_validation_data_distribution_3.png)

   다음 필드를 입력해야 합니다.

   * **[!UICONTROL Approve targeted messages]**: 모든 수신자를 수신자 목록에서 미리 선택하여 승인하려면 이 옵션을 선택합니다. 이 옵션을 선택 취소하면 수신자가 미리 선택되지 않습니다.

      >[!NOTE]
      >
      >이 옵션은 기본적으로 선택되어 있습니다.

      ![](assets/local_validation_notification.png)

   * **[!UICONTROL Delivery label]**: 반환 알림에 게재 레이블을 표시할 표현식을 정의할 수 있습니다. 기본 표현식은 게재의 표준 레이블(계산 문자열)에 대한 정보를 제공합니다. 이 표현식을 수정할 수 있습니다.

      ![](assets/local_validation_notification_3.png)

   * **[!UICONTROL Grouping field]**: 이 필드에서는 승인 및 반환 알림에 수신자를 표시하는 데 사용되는 그룹을 정의할 수 있습니다.

      ![](assets/local_validation_notification_4.png)

   * **[!UICONTROL Web Interface]**: 웹 애플리케이션을 수신자 목록에 연결할 수 있습니다. 승인 및 반환 알림에서 각 수신자를 클릭할 수 있으며 선택한 웹 애플리케이션에 연결됩니다. 다음 **[!UICONTROL Parameters]** 필드(예 **[!UICONTROL recipientId]**)을 사용하면 URL 및 웹 애플리케이션에서 사용할 추가 매개 변수를 구성할 수 있습니다.

      ![](assets/local_validation_notification_5.png)

1. 다음 **[!UICONTROL Breakdown]** 탭에서는 배포 값 목록을 정의할 수 있습니다.

   ![](assets/local_validation_data_distribution_4.png)

   * **[!UICONTROL Value]**: 분배 값을 입력합니다.
   * **[!UICONTROL Percentage / Set]**: 각 값에 연결된 레코드 한도(고정 또는 백분율)를 입력합니다.

      이 열은 **[!UICONTROL Distribution type]** 내 필드 **[!UICONTROL General]** 탭.

   * **[!UICONTROL Label]**: 각 값에 연결된 레이블을 입력합니다.
   * **[!UICONTROL Group or operator]**: 사용 중인 **[!UICONTROL Local approval]** 활동(참조) [로컬 승인](local-approval.md))을 클릭하여 각 배포 값에 할당된 연산자 또는 연산자 그룹을 선택합니다.

      로컬 승인 없이 데이터 그룹화로 간단하게 제한되는 경우 **[!UICONTROL Group or operator]** 필드.

      >[!IMPORTANT]
      >
      >연산자에게 적절한 권한이 할당되었는지 확인합니다.

   * **[!UICONTROL Local entity]**: 각 분배 값에 지정된 로컬 엔티티를 선택합니다. 로컬 엔티티는 **분산 마케팅**. 자세한 내용은 다음을 참조하십시오 [섹션](../../distributed/using/about-distributed-marketing.md).

## 매개 변수 필터링 {#filtering-parameters}

을(를) 클릭합니다. **[!UICONTROL General]** 탭하여 활동 레이블을 입력합니다. 이 분할에 대한 대상 및 필터 차원을 선택합니다. 필요한 경우 지정된 하위 세트에 대해 이러한 차원을 변경할 수 있습니다.

![](assets/s_user_segmentation_partage_general.png)

을(를) 확인합니다. **[!UICONTROL Generate complement]** 나머지 모집단을 활용하려는 경우 선택합니다. 보수는 인바운드 타겟에서 하위 세트의 결합을 뺀 것입니다. 그런 다음 다음과 같이 활동에 추가 아웃바운드 전환이 추가됩니다.

![](assets/s_user_segmentation_partage_compl.png)

이 옵션이 올바르게 작동하려면 인바운드 데이터에 기본 키가 있어야 합니다.

예를 들어, Netezza(인덱스 개념을 지원하지 않음)와 같은 외부 데이터베이스에서 직접 데이터를 읽는 경우 **[!UICONTROL Data loading (RDBMS)]** 활동, 에서 생성한 보완 **[!UICONTROL Split]** 활동이 올바르지 않습니다.

이를 방지하기 위해 **[!UICONTROL Enrichment]** 활동 바로 전 **[!UICONTROL Split]** 활동. 에서 **[!UICONTROL Enrichment]** 활동을 확인하고 **[!UICONTROL Keep all additional data from the main set]** 추가 데이터에서 필터 구성에 사용할 열을 지정합니다 **[!UICONTROL Split]** 활동. 의 인바운드 전환에서 수집한 데이터 **[!UICONTROL Split]** 그러면 활동이 Adobe Campaign 서버의 임시 테이블에 로컬로 저장되며 보정을 올바르게 생성할 수 있습니다.

다음 **[!UICONTROL Enable overlapping of output populations]** 옵션을 사용하면 여러 하위 세트에 속하는 모집단을 관리할 수 있습니다.

* 상자를 선택하지 않으면 분할 활동은 수신자가 여러 하위 세트의 기준을 충족하더라도 여러 출력 전환에 있을 수 없도록 합니다. 기준은 일치하는 첫 번째 탭의 대상에 포함됩니다.
* 이 확인란을 선택하면 수신자가 필터 기준을 충족하면 여러 하위 세트에서 찾을 수 있습니다. Adobe Campaign에서는 제외 기준을 사용하는 것이 좋습니다.

## 입력 매개 변수 {#input-parameters}

* tableName
* 스키마

각 인바운드 이벤트는 이러한 매개 변수로 정의된 대상을 지정해야 합니다.

## 출력 매개 변수 {#output-parameters}

* tableName
* 스키마
* recCount

이 세 값 집합은 제외로 인한 대상을 식별합니다. **[!UICONTROL tableName]** 는 대상 식별자를 기록하는 테이블의 이름입니다. **[!UICONTROL schema]** 는 모집단의 스키마(일반적으로 nms:recipient)이며 **[!UICONTROL recCount]** 는 테이블에 있는 요소의 수입니다.

보어와 연관된 전환에는 동일한 매개 변수가 있습니다.
