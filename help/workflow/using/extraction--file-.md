---
product: campaign
title: 데이터 추출(파일)
description: 데이터 추출(파일) 워크플로우 활동에 대해 자세히 알아보십시오
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Data Management Activity
exl-id: 06eafedd-6386-498f-a80d-7f57ddcccad6
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 1%

---

# 데이터 추출(파일){#extraction-file}



를 사용하여 외부 파일의 워크플로우 테이블에서 데이터를 추출할 수 있습니다 **[!UICONTROL Data extraction (file)]** 활동.

>[!CAUTION]
>
>이 활동에는 항상 추출할 데이터가 포함된 인바운드 전환이 있어야 합니다.

데이터 추출을 구성하려면 다음 단계를 수행합니다.

1. 출력 파일의 이름을 지정합니다. 이 이름에는 필드 오른쪽의 개인화 단추를 통해 삽입되는 변수가 포함될 수 있습니다.
1. 클릭 **[!UICONTROL Edit the file format...]** 추출할 데이터를 선택합니다.

   ![](assets/s_advuser_extract_file_param.png)

   다음 **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** 선택 사항은 합계의 최종 결과를 필터링하는 추가 단계를 추가합니다. 예를 들어 주어진 구매 발주 유형, 10번 이상 주문한 고객 등이 있습니다.

1. 필요한 경우 출력 파일에 컴퓨팅 또는 처리 결과와 같은 새 열을 추가할 수 있습니다. 이렇게 하려면 **[!UICONTROL Add]** 아이콘.

   ![](assets/s_advuser_extract_file_add_col.png)

   추가 줄에서 **[!UICONTROL Edit expression]** 아이콘을 클릭하여 새 열의 컨텐츠를 정의합니다.

   ![](assets/s_advuser_extract_file_add_exp.png)

   그런 다음 선택 창에 액세스합니다. 클릭 **[!UICONTROL Advanced selection]** 를 눌러 데이터에 적용할 프로세스를 선택합니다.

   ![](assets/s_advuser_extract_file_advanced_selection.png)

   목록에서 원하는 공식을 선택합니다.

   ![](assets/s_advuser_extract_file_agregate_values.png)

데이터 추출 중에 실행할 사후 프로세스를 정의하여 파일을 압축하거나 암호화할 수 있습니다. 이를 수행하려면 원하는 명령을 **[!UICONTROL Script]** 활동의 탭.

자세한 정보는 다음 섹션을 참조하십시오. [파일 압축 또는 암호화](how-to-use-workflow-data.md#zipping-or-encrypting-a-file).

![](assets/postprocessing_dataextraction.png)

## 집계 함수 목록 {#list-of-aggregate-functions}

다음은 사용 가능한 집계 함수 목록입니다.

* **[!UICONTROL Count]** 중복 값(집계된 필드의 값)을 포함하여 집계할 필드의 null이 아닌 모든 값을 계산하려면,

   **[!UICONTROL Distinct]** 계산할 필드의 서로 다른 값과 null이 아닌 값의 총 개수를 계산하려면(중복 값이 계산 전에 제외됨),

* **[!UICONTROL Sum]** 숫자 필드의 값 합계를 계산하려면,
* **[!UICONTROL Minimum value]** 필드의 최소값(숫자 또는 기타 방법)을 계산하려면
* **[!UICONTROL Maximum value]** 필드의 최대값(숫자 또는 기타 값)을 계산하려면
* **[!UICONTROL Average]** 숫자 필드의 값의 평균을 계산하기 위해.
