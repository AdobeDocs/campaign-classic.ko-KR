---
solution: Campaign Classic
product: campaign
title: 웹 양식 게시
description: 웹 양식 게시
audience: web
content-type: reference
topic-tags: web-forms
translation-type: tm+mt
source-git-commit: 21219f4a85a0caec4531acda33ab8bba5c7605d6
workflow-type: tm+mt
source-wordcount: '995'
ht-degree: 2%

---


# 웹 양식 게시{#publishing-a-web-form}

## 양식 데이터 {#pre-loading-the-form-data} 사전 로드

웹 양식을 통해 데이터베이스에 저장된 프로파일을 업데이트하려면 미리 로드 상자를 사용할 수 있습니다. 사전 로드 상자에서는 데이터베이스에서 업데이트할 레코드를 찾는 방법을 표시할 수 있습니다.

다음과 같은 식별 방법이 가능합니다.

* **[!UICONTROL Adobe Campaign Encryption]**

   이 암호화 방법은 암호화된 Adobe Campaign 식별자(ID)를 사용합니다. 이 방법은 Adobe Campaign 객체에만 적용되며 암호화된 ID는 Adobe Campaign 플랫폼에서만 생성할 수 있습니다.

   이 방법을 사용할 때는 **`<%=escapeUrl(recipient.cryptedId) %>`** 매개 변수를 추가하여 양식의 URL을 조정하여 이메일 주소로 전달해야 합니다. 자세한 내용은 [이메일을 통해 양식 제공](#delivering-a-form-via-email)을 참조하십시오.

* **[!UICONTROL DES encryption]**

   ![](assets/s_ncs_admin_survey_preload_methods_001.png)

   이 암호화 메서드는 외부에서 제공된 식별자(ID)를 사용하여 Adobe Campaign 및 외부 공급자가 공유하는 키에 연결합니다. **[!UICONTROL Des key]** 필드에서 이 암호화 키를 입력할 수 있습니다.

* **[!UICONTROL List of fields]**

   이 옵션을 사용하면 양식의 현재 컨텍스트에 있는 필드, 데이터베이스에서 해당 프로파일을 찾는 데 사용할 필드 중에서 선택할 수 있습니다.

   ![](assets/s_ncs_admin_survey_preload_methods_002.png)

   **[!UICONTROL Parameters]** 탭을 통해 양식 속성에 필드를 추가할 수 있습니다([매개 변수 추가](../../web/using/defining-web-forms-properties.md#adding-parameters) 참조). 양식 URL 또는 입력 영역에 배치됩니다.

   >[!CAUTION]
   >
   >선택한 필드의 데이터가 암호화되지 않았습니다. **[!UICONTROL Field list]** 옵션이 선택되어 있으면 Adobe Campaign에서 암호를 해독할 수 없으므로 암호화된 형식으로 제공해서는 안 됩니다.

   다음 예에서 프로필 미리 로드는 이메일 주소를 기반으로 합니다.

   이 URL에는 암호화되지 않은 이메일 주소가 포함될 수 있으며 이 경우 사용자가 자신과 관련된 페이지에 직접 액세스할 수 있습니다.

   ![](assets/s_ncs_admin_survey_preload_methods_003.png)

   그렇지 않으면 암호를 묻는 메시지가 나타납니다.

   ![](assets/s_ncs_admin_survey_preload_methods_004.png)

   >[!CAUTION]
   >
   >목록에 여러 필드를 지정한 경우 프로파일을 업데이트하려면 **ALL FIELDS**&#x200B;의 데이터가 데이터베이스에 저장된 데이터와 일치해야 합니다. 그렇지 않으면 새 프로필이 만들어집니다.
   > 
   >이 함수는 웹 응용 프로그램에 특히 유용하지만 공개 양식에는 권장되지 않습니다. 선택한 액세스 제어 옵션은 &quot;액세스 제어 사용&quot;이어야 합니다.

프로필을 업데이트하지 않으려면 **[!UICONTROL Skip preloading if no ID]** 옵션을 선택해야 합니다. 이 경우 입력된 각 프로필은 양식의 승인 후 데이터베이스에 추가됩니다. 이 옵션은 예를 들어 양식이 웹 사이트에 게시될 때 사용됩니다.

**[!UICONTROL Auto-load data referenced in the form]** 옵션을 사용하면 양식에서 입력 및 병합 필드와 일치하는 데이터를 자동으로 미리 로드할 수 있습니다. 그러나 **[!UICONTROL Script]** 및 **[!UICONTROL Test]** 활동에서 참조된 데이터는 관련이 없습니다. 이 옵션을 선택하지 않으면 **[!UICONTROL Load additional data]** 옵션을 사용하여 필드를 정의해야 합니다.

**[!UICONTROL Load additional data]** 옵션을 사용하면 양식의 페이지에 사용되지 않지만 미리 로드되는 정보를 추가할 수 있습니다.

예를 들어 수신자 성별을 미리 로드하고 테스트 상자를 통해 해당 페이지로 자동으로 안내할 수 있습니다.

![](assets/s_ncs_admin_survey_preload_ex.png)

## 웹 양식 배달 관리 및 추적 {#managing-web-forms-delivery-and-tracking}

양식을 만들고 구성하고 게시하면 양식을 제공하고 사용자 응답을 추적할 수 있습니다.

### 양식 {#life-cycle-of-a-form} 라이프사이클

양식의 라이프 사이클에는 3개의 단계가 있습니다.

1. **편집 중인 양식**

   이것이 초기 디자인 단계입니다. 새 양식이 만들어지면 편집 단계에 있습니다. 양식에 액세스하려면 테스트 목적으로만 해당 URL에 **[!UICONTROL __uuid]** 매개 변수를 사용해야 합니다. 이 URL은 **[!UICONTROL Preview]** 하위 탭에서 액세스할 수 있습니다. [양식 URL 매개 변수](../../web/using/defining-web-forms-properties.md#form-url-parameters)를 참조하십시오.

   >[!CAUTION]
   >
   >양식을 편집하는 동안 액세스 URL은 특수 URL입니다.

1. **Form Online**

   디자인 단계가 완료되면 양식을 전달할 수 있습니다. 우선, 그것은 게시되어야 합니다. 자세한 내용은 [양식](#publishing-a-form) 게시를 참조하십시오.

   이 양식은 만료될 때까지 **[!UICONTROL Live]**&#x200B;입니다.

   >[!CAUTION]
   >
   >배달하려면 설문 조사의 URL에 **[!UICONTROL __uuid]** 매개 변수가 포함되지 않아야 합니다.

1. **양식을 사용할 수 없음**

   양식이 닫히면 배달 단계가 종료되고 양식을 사용할 수 없게 됩니다.더 이상 사용자가 액세스할 수 없습니다.

   만료 날짜는 양식 속성 창에서 정의할 수 있습니다. 자세한 내용은 [온라인 양식 만들기](#making-a-form-available-online)를 참조하십시오.

양식의 게시 상태가 양식 목록에 표시됩니다.

![](assets/s_ncs_admin_survey_status.png)

### 양식 {#publishing-a-form} 게시

양식의 상태를 변경하려면 양식을 게시해야 합니다. 이렇게 하려면 웹 양식 목록 위의 **[!UICONTROL Publication]** 단추를 클릭하고 드롭다운 상자에서 상태를 선택합니다.

![](assets/webapp_publish_webform.png)

### 온라인 양식 만들기 {#making-a-form-available-online}

사용자가 양식에 액세스하려면 양식이 생산 단계여야 하며, 즉 유효 기간 내에 시작해야 합니다. 유효 날짜는 양식의 **[!UICONTROL Properties]** 링크를 통해 입력됩니다.

* **[!UICONTROL Project]** 섹션의 필드를 사용하여 양식의 시작 날짜와 종료 날짜를 입력합니다.

   ![](assets/webapp_availability_date.png)

* 사용자가 유효하지 않은 상태에서 양식에 액세스하려고 하면 표시할 오류 메시지를 정의하려면 **[!UICONTROL Personalize the message displayed if the form is closed...]** 링크를 클릭합니다.

   [양식](../../web/using/defining-web-forms-properties.md#accessibility-of-the-form)의 액세스 가능성을 참조하십시오.

### 이메일 {#delivering-a-form-via-email}을(를) 통해 양식 제공

이메일을 통해 초대장을 전달할 때 데이터 조정을 위해 **[!UICONTROL Adobe Campaign Encryption]** 옵션을 사용할 수 있습니다. 이렇게 하려면 전달 마법사로 이동하여 다음 매개 변수를 추가하여 양식에 대한 링크를 변경합니다.

```
<a href="https://server/webApp/APP264?&id=<%=escapeUrl(recipient.cryptedId) %>">
```

이 경우 데이터 저장소의 조정 키는 받는 사람의 암호화된 식별자여야 합니다. 자세한 내용은 [양식 데이터 사전 로드](#pre-loading-the-form-data)를 참조하십시오.

이 경우 레코드 상자에서 **[!UICONTROL Update the preloaded record]** 옵션을 선택해야 합니다. 자세한 내용은 [웹 양식 답변 저장](../../web/using/web-forms-answers.md#saving-web-forms-answers)을 참조하십시오.

![](assets/s_ncs_admin_survey_save_box_option.png)

### 응답 기록 {#log-responses}

응답 추적은 전용 탭에서 활성화하여 웹 양식의 영향을 모니터링할 수 있습니다. 이렇게 하려면 양식 속성 창에서 **[!UICONTROL Advanced parameters...]** 링크를 클릭하고 **[!UICONTROL Log responses]** 옵션을 선택합니다.

![](assets/s_ncs_admin_survey_trace.png)

응답자 ID를 볼 수 있는 **[!UICONTROL Responses]** 탭이 나타납니다.

![](assets/s_ncs_admin_survey_trace_tab.png)

수신자를 선택하고 **[!UICONTROL Detail...]** 단추를 클릭하여 제공된 응답을 봅니다.

![](assets/s_ncs_admin_survey_trace_edit.png)

예를 들어, 미리 알림을 전송할 때 응답자가 아닌 사람만을 대상으로 하거나 응답자에게 특정 커뮤니케이션을 제공하는 것과 같이 쿼리에 제공된 응답 로그를 처리할 수 있습니다.

>[!NOTE]
>
>제공된 응답에 대한 전체 추적을 수행하려면 응답을 내보내고 전용 보고서를 보거나 만드십시오(선택 사항 **Survey** 모듈 사용). 이 작업에 대한 자세한 정보는 [이 섹션](../../web/using/about-surveys.md)을 참조하십시오.

