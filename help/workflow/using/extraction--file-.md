---
title: 데이터 추출(파일)
description: 데이터 추출(파일) 워크플로우 활동에 대한 자세한 내용을 살펴보십시오.
page-status-flag: never-activated
uuid: c1e3fde3-183c-4602-9cef-760e4648fcf7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: fe4e6f64-eb0a-44bc-8221-6c9bfb99871f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5eb82bb5dae589cb18d42695565b25dad36006bd

---


# 데이터 추출(파일){#extraction-file}

외부 파일의 워크플로우 테이블에서 **[!UICONTROL Data extraction (file)]** 활동을 사용하여 데이터를 추출할 수 있습니다.

>[!CAUTION]
>
>이 활동에는 항상 추출할 데이터가 포함된 인바운드 전환이 있어야 합니다.

데이터 추출을 구성하려면 다음 단계를 수행하십시오.

1. 출력 파일의 이름을 지정합니다.이 이름에는 필드 오른쪽의 개인화 단추를 통해 삽입된 변수가 포함될 수 있습니다.
1. 을 **[!UICONTROL Edit the file format...]** 클릭하여 추출할 데이터를 선택합니다.

   ![](assets/s_advuser_extract_file_param.png)

   이 **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** 옵션은 합산된 최종 결과를 필터링하는 추가 단계를 추가합니다(예: 지정된 구매 발주 유형, 10회 이상 주문 고객 등).

1. 필요한 경우 컴퓨팅 또는 처리 결과와 같은 새 열을 출력 파일에 추가할 수 있습니다. 이렇게 하려면 **[!UICONTROL Add]** 아이콘을 클릭합니다

   ![](assets/s_advuser_extract_file_add_col.png)

   추가 행에서 아이콘을 클릭하여 새 열의 컨텐츠를 정의합니다. **[!UICONTROL Edit expression]**

   ![](assets/s_advuser_extract_file_add_exp.png)

   그런 다음 선택 창에 액세스합니다. 데이터에 적용할 프로세스를 **[!UICONTROL Advanced selection]** 선택하려면 을 클릭합니다.

   ![](assets/s_advuser_extract_file_advanced_selection.png)

   목록에서 원하는 공식을 선택합니다.

   ![](assets/s_advuser_extract_file_agregate_values.png)

## 집계 함수 목록 {#list-of-aggregate-functions}

다음은 사용 가능한 집계 함수 목록입니다.

* **[!UICONTROL Count]** to count all non-null values of the field to be aggreged, including duplicated values (of the aggregated field),

   **[!UICONTROL Distinct]** 을 클릭하여 합산할 필드의 서로 다른 값과 null이 아닌 값의 총 수를 계산합니다(중복 값은 계산 전에 제외됨).

* **[!UICONTROL Sum]** 숫자 필드의 값 합계를 계산하려면
* **[!UICONTROL Minimum value]** 필드의 최소 값(숫자 또는 기타)을 계산하려면
* **[!UICONTROL Maximum value]** 필드의 최대값(숫자 또는 기타)을 계산하려면
* **[!UICONTROL Average]** 를 사용하여 숫자 필드의 값 평균을 계산합니다.

