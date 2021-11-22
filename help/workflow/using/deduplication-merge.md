---
title: 중복 제거 활동의 병합 기능 사용
description: 중복 제거 작업의 병합 기능을 사용하는 방법을 알아봅니다.
page-status-flag: never-activated
uuid: 8887574e-447b-48a5-afc6-95783ffa7fb3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 4113c3fe-a279-4fe1-be89-ea43c96edc34
index: y
internal: n
snippet: y
exl-id: a6b10585-7bf9-4fef-b886-db081b6d3acc
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 5%

---

# 중복 제거 활동의 병합 기능 사용 {#deduplication-merge}

![](../../assets/common.svg)

## 이 활용 사례 정보 {#about-this-use-case}

이 사용 사례에서는 **[!UICONTROL Merge]** 기능 **[!UICONTROL Deduplication]** 활동.

이 기능에 대한 자세한 내용은 [이 섹션](deduplication.md#merging-fields-into-single-record).

다음 **[!UICONTROL Deduplication]** 활동은 데이터 세트에서 중복 행을 제거하는 데 사용됩니다. 이 사용 사례에서는 아래에 표시된 데이터가 이메일 필드를 기반으로 복제됩니다.

| 마지막 수정 날짜 | 이름 | 성 | 이메일 | 휴대폰 | 전화 |
|-----|------------|-----------|-------|--------------|------|
| 5/19/2020 | 로버트 | 티너 | bob@mycompany.com | 444-444-444 | 777-777-7777 |
| 7/22/2020 | 바비 | 티너 | bob@mycompany.com |  | 777-777-7777 |
| 10/03/2020 | Bob |  | bob@mycompany.com |  | 888-888-8888 |

중복 제거 활동 사용 **[!UICONTROL Merge]** 또는 데이터 중복 제거에 대한 규칙 세트를 구성하여 하나의 결과 데이터 레코드에 병합할 필드 그룹을 정의할 수 있습니다. 예를 들어 중복 레코드 세트를 사용하여 가장 오래된 전화 번호 또는 가장 최근 이름을 유지하도록 선택할 수 있습니다.

## 병합 기능 활성화 {#activating-merge}


병합 기능을 활성화하려면 먼저 **[!UICONTROL Deduplication]** 활동. 이렇게 하려면 다음 단계를 수행합니다.

1. 활동을 열고 **[구성 편집]** 링크를 클릭합니다.

1. 중복 제거에 사용할 조정 필드를 선택한 다음 을(를) 클릭합니다 **[!UICONTROL Next]**. 이 예제에서는 이메일 필드를 기반으로 중복을 제거하려고 합니다.

   ![](assets/uc_merge_edit.png)

1. 을(를) 클릭합니다. **[!UICONTROL Advanced parameters]** 링크를 클릭한 다음 를 활성화합니다 **[!UICONTROL Merge records]** 및 **[!UICONTROL Use several record merging criteria]** 옵션.

   ![](assets/uc_merge_advanced_parameters.png)

1. 다음 **[!UICONTROL Merge]** 탭이 **[!UICONTROL Deduplication]** 구성 화면. 중복 제거를 수행할 때 이 탭을 사용하여 병합할 데이터를 지정합니다.

## 병합할 필드 구성 {#configuring-rules}

데이터를 단일 레코드로 병합하는 데 사용할 규칙은 다음과 같습니다.

* 가장 최근 이름(이름 및 성 필드)을 유지합니다.
* 최신 휴대폰은 그대로 두고
* 가장 오래된 전화 번호를 보관하세요
* 최종 레코드에 적격하려면 그룹의 모든 필드가 null이 아니어야 합니다.

이러한 규칙을 구성하려면 다음 단계를 수행합니다.

1. 를 엽니다. **[!UICONTROL Merge]** 탭을 클릭한 다음 **[!UICONTROL Add]** 버튼을 클릭합니다.

   ![](assets/uc_merge_add.png)

1. 병합할 필드 그룹의 식별자 및 레이블을 지정합니다.

   ![](assets/uc_merge_identifier.png)

1. 고려할 레코드를 선택하는 조건을 지정합니다.

   ![](assets/uc_merge_filter.png)

1. 가장 최근 이름을 선택하려면 마지막 수정 날짜를 정렬합니다.

   ![](assets/uc_merge_sort.png)

1. 병합할 필드를 선택합니다. 이 예제에서는 이름과 성 필드를 유지하려고 합니다.

   ![](assets/uc_merge_keep.png)

1. 필드는 병합할 데이터 세트에 추가되고 새 요소가 워크플로우 스키마에 추가됩니다.

   휴대폰 및 전화 필드를 구성하려면 다음 단계를 반복합니다.

   ![](assets/dedup8.png)

   ![](assets/dedup9.png)

## 결과 {#results}

이러한 규칙을 구성한 후 **[!UICONTROL Deduplication]** 활동.

| 수정 날짜 | 이름 | 성 | 이메일 | 휴대폰 | 전화 |
|-----|------------|-----------|-------|--------------|------|
| 5/19/2020 | 로버트 | 티너 | bob@mycompany.com | 444-444-444 | 777-777-7777 |
| 7/22/2020 | 바비 | 티너 | bob@mycompany.com |  | 777-777-7777 |
| 10/03/2020 | Bob |  | bob@mycompany.com |  | 888-888-8888 |

결과는 이전에 구성된 규칙에 따라 세 개의 레코드에서 병합됩니다. 비교 후, 가장 최근의 이름과 휴대전화가 원래 전화 번호와 함께 사용되었다고 결론지었어요.

| 이름 | 성 | 이메일 | 휴대폰 | 전화 |
|------------|-----------|-------|--------------|------|
| 바비 | 티너 | bob@mycompany.com | 444-444-4444 | 888-888-8888 |

>[!NOTE]
>
> 이름 및 마지막 필드를 모두 사용하여 &quot;이름&quot; 규칙을 구성했으므로 병합된 이름은 &quot;Bobby&quot;입니다.
>
>따라서 연결된 성 필드가 비어 있으므로 &quot;Bob&quot;(가장 최근 이름)을 고려할 수 없습니다. 가장 최근의 이름과 성 조합이 최종 레코드에 병합되었습니다.
