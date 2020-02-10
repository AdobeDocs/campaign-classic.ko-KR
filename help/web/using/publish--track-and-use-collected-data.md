---
title: 수집된 데이터 게시, 추적 및 사용
seo-title: 수집된 데이터 게시, 추적 및 사용
description: 수집된 데이터 게시, 추적 및 사용
seo-description: null
page-status-flag: never-activated
uuid: eac16f2c-0423-4727-a2da-3af1d6c616ec
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: online-surveys
discoiquuid: 434a4bda-0907-42a7-8a75-2db658bba046
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 수집된 데이터 게시, 추적 및 사용{#publish-track-and-use-collected-data}

양식을 만들고 구성하며 게시했으면 사용자와 링크를 공유하고 응답을 추적할 수 있습니다.

>[!NOTE]
>
>Adobe Campaign의 설문 조사 라이프사이클과 게시 및 배달 모드는 웹 양식의 라이프사이클 및 비슷합니다.이러한 내용은 [이 섹션에](../../web/using/about-web-forms.md)자세히 설명되어 있습니다.

## 설문 조사 대시보드 {#survey-dashboard}

각 설문 조사에는 상태, 설명, 공개 URL 및 가용성 일정을 볼 수 있는 자체 대시보드가 있습니다. 사용 가능한 보고서를 볼 수도 있습니다. 자세한 내용은 설문 조사에 [대한](#reports-on-surveys)보고서를 참조하십시오.

설문 조사의 공개 URL은 대시보드에 표시됩니다.

![](assets/survey_public_url.png)

## 응답 추적 {#response-tracking}

로그 및 보고서에서 설문 조사에 대한 응답을 추적할 수 있습니다.

### 설문 조사 로그 {#survey-logs}

전달된 각 설문 조사에 대해 **[!UICONTROL Logs]** 탭에서 응답을 추적할 수 있습니다. 이 탭에는 설문 조사를 완료한 사용자 목록과 원본 목록이 표시됩니다.

![](assets/s_ncs_admin_survey_logs.png)

라인을 두 번 클릭하여 응답자가 입력한 대로 설문 조사 양식을 표시합니다. 설문 조사를 전체적으로 검색하고 답변에 완전히 액세스할 수 있습니다. 외부 파일로 내보낼 수 있습니다. 자세한 내용은 답변 내보내기를 [참조하십시오](#exporting-answers).

원본 문자는 다음 문자를 추가하여 설문 조사 URL에 표시됩니다.

```
?origin=xxx
```

설문 조사를 편집하는 동안 설문 조사 URL에 매개 변수가 포함되어 **[!UICONTROL __uuid]**&#x200B;있습니다. 이 매개 변수는 테스트 단계이며 아직 온라인 상태가 아님을 나타냅니다. 이 URL 파섹 원점은 값으로 **[!UICONTROL Adobe Campaign]**&#x200B;지정됩니다.

URL 매개 변수에 대한 자세한 내용은 [이 페이지를](../../web/using/defining-web-forms-properties.md#form-url-parameters)참조하십시오.

### 설문 조사에 대한 보고서 {#reports-on-surveys}

대시보드 탭에서는 설문 조사 보고서에 액세스할 수 있습니다. 보고서 이름을 클릭하여 봅니다.

![](assets/s_ncs_admin_survey_report_doc.png)

설문 조사 구조는 **[!UICONTROL Documentation]** 보고서에 표시됩니다.

웹 설문 조사에 대한 다른 두 보고서는 설문 조사의 **[!UICONTROL Reports]** 탭에서 사용할 수 있습니다. **[!UICONTROL General]** 및 **[!UICONTROL Breakdown of responses]** Adobe

* 일반

   이 보고서에는 설문 조사에 대한 일반 정보가 포함되어 있습니다.시간의 경과에 따라 응답 수가 변경되는 방식 및 출처 및 언어별 배포.

   일반 보고서의 예:

   ![](assets/s_ncs_admin_survey_report_0.png)

* 응답 분류

   이 보고서는 각 질문에 대한 응답 분류를 보여줍니다. 이 분류는 **[!UICONTROL Question]** 유형 컨테이너에 저장된 필드에 지정된 응답에만 사용할 수 있습니다. 선택 컨트롤(예: 텍스트 필드의 분류 없음)에만 사용할 수 있습니다.

   ![](assets/s_ncs_admin_survey_report_2.png)

## 대답 내보내기 {#exporting-answers}

설문 조사에 대한 답변을 외부 파일로 내보내 나중에 처리할 수 있습니다. 다음 두 가지 방법으로 이 작업을 수행할 수 있습니다.

1. 보고서 데이터 내보내기

   보고서 데이터를 내보내려면 **[!UICONTROL Export]** 단추를 클릭하고 내보내기 형식을 선택합니다.

   보고서 데이터 내보내기에 대한 자세한 내용은 [이 섹션을](../../reporting/using/about-reports-creation-in-campaign.md)참조하십시오.

1. 대답 내보내기

   답변을 내보내려면 설문 조사의 **[!UICONTROL Responses]** 탭을 클릭하고 마우스 오른쪽 단추를 클릭합니다. 을 **[!UICONTROL Export...]**&#x200B;선택합니다.

   ![](assets/s_ncs_admin_survey_logs_export_menu.png)

   그런 다음 내보낼 정보와 저장소 파일을 입력합니다.

   내보내기 마법사에서 출력 파일의 내용과 형식을 구성할 수 있습니다.

   이를 통해 다음을 수행할 수 있습니다.

   * 출력 파일에 열을 추가하고 수신자 정보(데이터베이스에 저장됨)를 복구합니다.
   * 내보낸 데이터의 형식 지정,
   * 파일의 정보에 대한 인코딩 형식을 선택합니다.
   내보내려는 설문 조사에 여러 **[!UICONTROL Multi-line text]** 개 또는 **[!UICONTROL HTML text]** 필드가 포함되어 있으면 **[!UICONTROL XML]** 형식을 내보내야 합니다. 이렇게 하려면 아래 표시된 대로 **[!UICONTROL Output format]** 필드의 드롭다운 목록에서 이 형식을 선택합니다.

   ![](assets/s_ncs_admin_survey_logs_export_xml.png)

   을 **[!UICONTROL Start]** 클릭하여 내보내기를 실행합니다.

   >[!NOTE]
   >
   >데이터 내보내기 및 구성 단계는 [이 섹션에](../../platform/using/generic-imports-and-exports.md)자세히 설명되어 있습니다.

## 수집된 데이터 사용 {#using-the-collected-data}

온라인 설문 조사를 통해 수집된 정보는 타깃팅 워크플로우의 프레임워크 내에서 복구할 수 있습니다. 이렇게 하려면 **[!UICONTROL Survey responses]** 상자를 사용합니다.

다음 예에서는 최소 2명의 자녀와 온라인 설문 조사에서 가장 높은 점수를 받은 5명의 받는 사람을 위해 특별히 웹 오퍼를 만듭니다. 이 설문 조사에 대한 대답은 다음과 같습니다.

![](assets/s_ncs_admin_survey_responses_wf_box_4.png)

타깃팅 워크플로우에서는 다음과 같이 **[!UICONTROL Survey responses]** 구성됩니다.

![](assets/s_ncs_admin_survey_responses_wf_box_1.png)

먼저 관련 설문 조사를 선택한 다음 창의 중앙 섹션에서 추출할 데이터를 선택합니다. 이 경우 5개의 가장 높은 점수를 복구하려면 분할 상자에 점수가 사용되므로 점수 열을 적어도 추출해야 합니다.

링크를 클릭하여 응답에 대한 필터링 조건을 **[!UICONTROL Edit query...]** 지정합니다.

![](assets/s_ncs_admin_survey_responses_wf_box_2.png)

타깃팅 워크플로우를 시작합니다. 쿼리는 8명의 수신자를 복구합니다.

![](assets/s_ncs_admin_survey_responses_wf_box_5.png)

컬렉션 상자의 출력 전환을 마우스 오른쪽 단추로 클릭하여 표시합니다.

![](assets/s_ncs_admin_survey_responses_wf_box_6.png)

그런 다음 워크플로우에 분할 상자를 배치하여 가장 높은 점수를 받은 5명의 수신자를 복구합니다.

분할 상자를 편집하여 구성합니다.

* 탭에서 적절한 스키마를 선택한 다음 **[!UICONTROL General]** 하위 세트를 구성합니다.

   ![](assets/s_ncs_admin_survey_responses_wf_box_6b.png)

* 탭으로 **[!UICONTROL Sub-sets]** 이동하여 **[!UICONTROL Limit the selected records]** 옵션을 선택한 다음 **[!UICONTROL Edit...]** 링크를 클릭합니다.

   ![](assets/s_ncs_admin_survey_responses_wf_box_7.png)

* 옵션을 **[!UICONTROL Keep only the first records after sorting]** 선택하고 정렬 열을 선택합니다. 옵션을 **[!UICONTROL Descending sort]** 선택합니다.

   ![](assets/s_ncs_admin_survey_responses_wf_box_8.png)

* 단추를 클릭하고 레코드 수를 5로 제한합니다. **[!UICONTROL Next]**

   ![](assets/s_ncs_admin_survey_responses_wf_box_9.png)

* 아이콘을 **[!UICONTROL Finish]** 클릭한 다음 워크플로우를 다시 시작하여 타깃팅을 승인합니다.

## 데이터 표준화 {#standardizing-data}

별칭을 사용하여 수집한 데이터에 대해 Adobe Campaign에서 표준화 프로세스를 설정할 수 있습니다. 이렇게 하면 데이터베이스에 저장된 데이터를 표준화할 수 있습니다.이렇게 하려면 관련 정보가 포함된 항목별 목록에 별칭을 정의합니다.

For more on this, refer to [this page](../../platform/using/managing-enumerations.md#about-enumerations).
