---
title: 웹 양식에 필드 추가
seo-title: 웹 양식에 필드 추가
description: 웹 양식에 필드 추가
seo-description: null
page-status-flag: never-activated
uuid: 33c6ab85-b021-422a-a224-c9eff27e6fc0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: d63892b3-260d-45e8-b99a-1e7c78353395
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 963aaa81971a8883b944bfcf4d1a00d729627916

---


# 웹 양식에 필드 추가{#adding-fields-to-a-web-form}

웹 양식에서 필드를 사용하면 정보를 입력하고 옵션을 선택할 수 있습니다. 웹 양식은 입력 필드, 선택 필드, 정적 및 고급 컨텐츠(캡션, 구독 등)를 제공할 수 있습니다.

마법사를 사용하여 필드를 추가하면 선택한 필드나 저장소 변수에 따라 필드 유형이 자동으로 검색됩니다. 탭의 **[!UICONTROL Type]** 드롭다운 상자를 사용하여 편집할 수 **[!UICONTROL General]** 있습니다.

![](assets/s_ncs_admin_webform_change_type.png)

도구 모음에서 단추를 사용할 때 추가할 필드 유형을 선택합니다.

다음 유형의 필드를 사용할 수 있습니다.

* 텍스트/번호 입력. 입력 [필드](#adding-input-fields)추가를 참조하십시오.
* 드롭다운 목록 선택. 드롭다운 [목록](#adding-drop-down-lists)추가를 참조하십시오.
* 확인란을 통해 다양한 선택 확인란 [추가를 참조하십시오](#adding-checkboxes).
* 라디오 단추를 통한 전용 선택 라디오 [단추](#adding-radio-buttons)추가를 참조하십시오.
* 옵션 격자에서 투표 격자 [추가를](#adding-grids)참조하십시오.
* 숫자 및 날짜 날짜 [및 번호](#adding-dates-and-numbers)추가를 참조하십시오.
* 정보 서비스 구독/구독 취소. 구독 [확인란을](#subscription-checkboxes)참조하십시오.
* Captcha 유효성 검사. captcha [삽입을 참조하십시오](#inserting-a-captcha).
* 다운로드 단추. [파일](#uploading-a-file)업로드
* 숨겨진 상수입니다. 숨겨진 [상수](#inserting-a-hidden-constant)삽입을 참조하십시오.

응답 저장소 모드를 지정하십시오.데이터베이스의 필드를 업데이트하거나(저장된 마지막 값만 저장) 변수에 저장합니다(대답은 저장되지 않음). 자세한 내용은 응답 [스토리지 필드를](../../web/using/web-forms-answers.md#response-storage-fields)참조하십시오.

>[!NOTE]
>
>기본적으로 필드는 현재 트리의 아래쪽에 삽입됩니다. 도구 모음의 화살표를 사용하여 위 또는 아래로 이동합니다.

## 필드 만들기 마법사 {#field-creation-wizard}

양식의 각 페이지에 대해 도구 모음의 첫 번째 단추를 통해 필드를 추가할 수 있습니다. 이렇게 하려면 **[!UICONTROL Add using the wizard]** 메뉴에서

![](assets/s_ncs_admin_survey_add_field_menu.png)

만들려는 필드 유형을 선택합니다.데이터베이스에 필드, 변수 또는 다른 형식으로 만들어 컨테이너에서 수집한 필드 그룹을 가져오도록 선택할 수 있습니다.

스토리지 필드 또는 변수 또는 가져올 컨테이너를 **[!UICONTROL Next]** 클릭하여 선택합니다.

![](assets/s_ncs_admin_webform_wz_confirm_db.png)

을 **[!UICONTROL Finish]** 클릭하여 선택한 필드를 페이지에 삽입합니다.

![](assets/s_ncs_admin_webform_wz_insert_field.png)

## 입력 필드 추가 {#adding-input-fields}

입력 필드를 추가하려면 **[!UICONTROL Input control]** 단추를 클릭하고 추가할 필드 유형을 선택합니다.

![](assets/s_ncs_admin_webform_select_field.png)

### 입력 필드 유형 {#types-of-input-fields}

양식 페이지에 삽입할 수 있는 5가지 유형의 텍스트 필드:

* **텍스트**:한 줄에 텍스트를 입력할 수 있습니다.

   ![](assets/s_ncs_admin_survey_txt_ex.png)

* **번호**:한 줄에 숫자를 입력할 수 있습니다. 자세한 내용은 숫자 [추가를 참조하십시오](#adding-numbers).

   페이지가 승인되면 필드 컨텐츠가 확인되어 입력된 값이 필드와 호환되는지 확인합니다. 자세한 내용은 컨트롤 [설정](../../web/using/form-rendering.md#defining-control-settings)정의를 참조하십시오.

* **암호**:한 줄에 텍스트를 입력할 수 있습니다. 텍스트 입력 시 문자가 점으로 바뀝니다.

   ![](assets/s_ncs_admin_survey_passwd_ex.png)

   >[!CAUTION]
   >
   >암호는 암호화되지 않은 상태로 데이터베이스에 저장됩니다.

* **여러 줄 텍스트**:여러 줄에 텍스트를 입력할 수 있습니다.

   ![](assets/s_ncs_admin_survey_txtmulti_ex.png)

   >[!CAUTION]
   >
   >여러 줄 텍스트 필드는 캐리지 리턴을 포함할 수 있는 특정 필드입니다. 저장소 공간은 XML 특성이 아닌 XML 요소에 매핑된 필드와 연결해야 합니다. 스키마의 데이터 유형에 대한 자세한 내용은 [이 섹션의](../../configuration/using/about-schema-reference.md)&quot;스키마 참조&quot; 장을 참조하십시오.
   >   
   >설문 조사 모듈을 사용하는 **경우** 이 유형의 필드를 보관된 필드에 저장할 수 있으며, 이 필드는 형식에 자동으로 적용됩니다. For more on this, refer to [this section](../../web/using/about-surveys.md).

* **풍부해진 여러 줄 텍스트**:HTML 형식으로 저장되는 레이아웃으로 텍스트를 입력할 수 있습니다.

   ![](assets/s_ncs_admin_survey_txthtmli_ex.png)

   사용자에게 제공되는 편집기 유형을 선택할 수 있습니다. 이렇게 하려면 탭의 **[!UICONTROL HTML editor]** 필드 드롭다운 상자를 **[!UICONTROL Advanced]** 사용합니다.

   ![](assets/webapp_enrich_text_type.png)

   표시되는 아이콘 수는 편집기 유형에 따라 다릅니다. 편집기의 경우 렌더링은 다음과 **[!UICONTROL Advanced]** 같습니다.

   ![](assets/webapp_enrich_text_max.png)

### 입력 필드 구성 {#configure-input-fields}

입력 필드는 모두 다음 옵션을 사용하여 동일한 모드를 기반으로 구성됩니다.

![](assets/s_ncs_admin_survey_txt_param.png)

이 **[!UICONTROL General]** 탭에서는 필드 이름을 입력하고 필요한 경우 기본값을 지정할 수 있습니다.

응답 저장 모드는 **[!UICONTROL Edit storage...]** 링크를 통해 변경할 수 있습니다. 값은 데이터베이스의 기존 필드에 저장할 수 있습니다.또는 데이터베이스에 정보를 저장하지 않도록 선택할 수 있습니다(로컬 변수 사용).

>[!NOTE]
>
>스토리지 모드는 응답 스토리지 [필드에 자세히 설명되어 있습니다.](../../web/using/web-forms-answers.md#response-storage-fields)

이 **[!UICONTROL Advanced]** 탭에서는 필드의 표시 매개 변수(레이블 위치, 정렬 등)를 정의할 수 있습니다. 웹 [양식 레이아웃](../../web/using/defining-web-forms-layout.md)정의를 참조하십시오.

## 드롭다운 목록 추가 {#adding-drop-down-lists}

설문 조사 페이지에 드롭다운 목록을 삽입할 수 있습니다. 이렇게 하면 사용자가 드롭다운 메뉴의 오퍼에서 값을 선택할 수 있습니다.

![](assets/s_ncs_admin_survey_dropdown_sample.png)

양식 페이지에 드롭다운 상자를 추가하려면 페이지 편집기의 도구 모음에서 **[!UICONTROL Selection controls > Drop-down list]** 단추를 클릭합니다.

![](assets/s_ncs_admin_survey_create_dropdown.png)

응답 저장 모드를 선택하고 선택을 확인합니다.

탭의 하단 섹션에서 목록의 레이블 및 값을 **[!UICONTROL General]** 정의합니다. 정보가 데이터베이스의 기존 필드에 저장되고 열거형 필드인 경우, 아래와 같이 **[!UICONTROL Initialize the list of values from the database]** 을 클릭하여 값을 자동으로 입력할 수 있습니다.

![](assets/s_ncs_admin_survey_database_values.png)

>[!NOTE]
>
>값 목록 오른쪽에 있는 화살표를 사용하여 순서를 변경합니다.

데이터가 연결된 테이블에 저장되어 있는 경우 목록에 제시될 값이 저장되는 필드를 선택할 수 있습니다. 예를 들어 국가 테이블을 선택한 경우 을 클릭하고 원하는 필드를 **[!UICONTROL Initialize the list of values from the database...]** 선택합니다.

![](assets/s_ncs_admin_survey_preload_values.png)

그런 다음 **[!UICONTROL Load]** 링크를 클릭하여 값을 검색합니다.

![](assets/s_ncs_admin_survey_load_button.png)

>[!CAUTION]
>
>목록이 업데이트될 때마다 이 작업을 반복하여 오퍼의 값을 새로 고칩니다.

## 확인란 추가 {#adding-checkboxes}

사용자가 옵션을 선택하려면 확인란을 사용해야 합니다.

![](assets/s_ncs_admin_survey_check_box.png)

양식에 확인란을 추가하려면 페이지 편집기의 도구 모음에서 **[!UICONTROL Selection controls > Checkbox...]** 아이콘을 클릭합니다.

응답 저장 모드를 선택하고 선택을 확인합니다.

탭의 **[!UICONTROL Label]** 필드에 상자의 레이블을 **[!UICONTROL General]** 입력합니다.

![](assets/s_ncs_admin_survey_check_box_edit.png)

확인란을 선택하면 확인란을 선택했는지 여부에 따라 저장소 필드(또는 값)에 값을 지정할 수 있습니다. 이 **[!UICONTROL Values]** 섹션에서는 상자가 선택된 경우(필드에서) 할당할 값을 입력하고, 상자가 선택되지 않은 경우 할당할 값( **[!UICONTROL Value]** **[!UICONTROL Empty value]** 필드에서)을 입력할 수 있습니다. 이러한 값은 데이터 저장소 형식에 따라 다릅니다.

저장소 필드(또는 변수)가 부울이면, 상자를 선택하지 않으면 할당할 값을 자동으로 추론합니다. 이 경우 아래와 같이 **[!UICONTROL Value if checked]** 필드만 제공됩니다.

![](assets/s_ncs_admin_survey_check_box_enum.png)

## 예:상자를 선택하는 경우 필드에 값 할당 {#example--assign-a-value-to-a-field-if-a-box-is-checked}

아래와 같이 유지 관리 요청을 보내기 위한 확인란을 양식에 삽입하려고 합니다.

![](assets/s_ncs_admin_survey_check_box_ex.png)

정보는 데이터베이스와 기존 필드(이 경우 **[!UICONTROL Comment]** 필드)에 업로드됩니다.

![](assets/s_ncs_admin_survey_check_box_ex_list.png)

&quot;유지 관리 필요&quot; 상자를 선택하면 **[!UICONTROL Comment]** 열에 &quot;유지 관리 필요&quot;가 포함됩니다. 상자를 선택하지 않으면 열에 &quot;유지 관리가 필요하지 않음&quot;이 표시됩니다. 이 결과를 얻으려면 양식 페이지의 확인란에 다음 구성을 적용합니다.

![](assets/s_ncs_admin_survey_check_box_ex_edit.png)

## 라디오 단추 추가 {#adding-radio-buttons}

라디오 단추를 사용하면 사용자에게 선택할 수 있는 일련의 전용 옵션을 제공할 수 있습니다. 동일한 필드에 대한 값이 다릅니다.

![](assets/s_ncs_admin_survey_radio_button.png)

라디오 단추를 개별적으로(단위 단추) 또는 객관식 목록을 통해 만들 수 있지만 라디오 단추 포인트는 한 옵션 또는 다른 옵션을 선택하는 것이기 때문에 라디오 단추 쌍을 항상 만들지 않고 한 개 이상의 라디오 단추를 만듭니다.

>[!CAUTION]
>
>선택 사항을 필수 항목으로 만들려면 객관식 목록을 만들어야 합니다.

### 단일 단추 추가 {#add-single-buttons}

양식 페이지에 라디오 단추를 추가하려면 페이지 편집기의 도구 모음에 있는 **[!UICONTROL Selection controls > Radio button]** 메뉴로 이동하여 저장소 모드를 선택합니다.

![](assets/s_ncs_admin_survey_radio_button_sample.png)

라디오 단추는 확인란과 유사한 방법으로 구성됩니다(확인란 [추가 참조](#adding-checkboxes)). 그러나 옵션을 선택하지 않으면 값이 할당되지 않습니다. 여러 개의 단추가 상호 종속되도록 하려면, 즉 하나를 선택하면 다른 단추가 자동으로 선택 취소되고 동일한 필드에 저장되어야 합니다. 데이터베이스에 저장되지 않은 경우, 임시 저장소에 동일한 로컬 변수를 사용해야 합니다. 응답 [저장소 필드를](../../web/using/web-forms-answers.md#response-storage-fields)참조하십시오.

### 단추 목록 추가 {#add-a-list-of-buttons}

목록을 통해 라디오 단추를 추가하려면 페이지 편집기의 도구 모음에 있는 **[!UICONTROL Selection controls>Multiple choice]** 메뉴로 이동합니다.

![](assets/s_ncs_admin_survey_radio_button_sample2.png)

레이블만큼 라디오 단추를 추가합니다. 이 기능의 장점은 기존 필드(항목별 필드의 경우)에서 값을 가져와서 사용자가 하나의 옵션을 선택할 수 있도록 하는 것입니다. 그러나 단추 레이아웃은 유연하지 않습니다.

>[!NOTE]
>
>웹 양식은 여러 값 선택을 인증하지 않습니다. 설문 조사 형식 양식에만 다중 선택을 활성화할 **수** 있습니다. For more on this, refer to [this section](../../web/using/about-surveys.md).\
>그러나 웹 애플리케이션에 **[!UICONTROL Multiple choice]** 문자 필드를 삽입할 수는 있습니다.하지만 여러 값을 선택할 수 있는 권한을 부여하지 않은 경우:제공되는 옵션은 라디오 단추를 사용하여 선택할 수 있습니다.

## 격자 추가 {#adding-grids}

격자는 웹 애플리케이션에서 투표 페이지를 디자인하는 데 사용됩니다. 이렇게 하면 아래 표시된 대로 설문 조사 또는 평가 유형 웹 양식에 응답할 라디오 단추 목록을 제공할 수 있습니다.

![](assets/s_ncs_admin_survey_vote_param.png)

양식에서 이 유형의 요소를 사용하려면 간단한 그리드를 만들고 평가할 각 요소에 대한 라인을 추가합니다.

![](assets/s_ncs_admin_survey_vote_sample.png)

격자의 각 행에 있는 라디오 단추 수는 단순 격자에 정의된 값의 수와 일치합니다.

![](assets/s_ncs_admin_survey_vote_ex.png)

격자 선당 하나의 옵션만 선택할 수 있습니다.

>[!NOTE]
>
>이 예제에서는 격자의 레이블이 숨겨집니다. 이렇게 하려면 **[!UICONTROL Advanced]** 탭으로 이동하면 **[!UICONTROL Label position]** 표시가 로 정의됩니다 **[!UICONTROL Hidden]** . 레이블 [위치 정의를 참조하십시오](../../web/using/defining-web-forms-layout.md#defining-the-position-of-labels).

## 날짜 및 번호 추가 {#adding-dates-and-numbers}

양식 필드의 내용은 데이터베이스에 저장된 데이터와 일치하거나 특정 요구 사항을 충족하기 위해 형식을 지정할 수 있습니다. 숫자 및 날짜 입력에 적합한 필드를 만들 수 있습니다.

### 날짜 추가 {#adding-dates}

![](assets/s_ncs_admin_survey_date_calendar.png)

사용자가 양식 페이지에 날짜를 입력할 수 있도록 하려면 도구 모음 또는 페이지 편집기에서 **[!UICONTROL Add input field > Date...]** 을 선택합니다.

필드의 레이블을 입력하고 데이터 저장소 모드를 구성합니다.

![](assets/s_ncs_admin_survey_date_edit.png)

창의 하단 섹션에서는 이 필드에 저장된 값의 날짜 및 시간 형식을 선택할 수 있습니다.

![](assets/s_ncs_admin_survey_date_edit_values.png)

날짜(또는 시간)를 표시하지 않도록 선택할 수도 있습니다.

날짜는 달력 또는 드롭다운 상자를 통해 선택할 수 있습니다. 필드에 직접 입력할 수도 있지만 위의 화면에 지정된 형식과 일치해야 합니다.

>[!NOTE]
>
>기본적으로 양식에 사용된 날짜는 달력을 통해 입력됩니다. 다국어 양식은 사용된 모든 언어로 달력이 제공되는지 확인하십시오. 웹 [양식](../../web/using/translating-a-web-form.md)변환을 참조하십시오.

그러나 경우에 따라(생년월일 입력 등) 드롭다운 목록을 사용하는 것이 더 쉽습니다.

![](assets/s_ncs_admin_survey_date_list_select.png)

이렇게 하려면 **[!UICONTROL Advanced]** 탭을 클릭하고 를 사용하여 입력 모드를 선택합니다 **[!UICONTROL Drop-down lists]**.

![](assets/s_ncs_admin_survey_date_selection.png)

그런 다음 목록에 제공되는 값에 제한을 설정할 수 있습니다.

![](assets/s_ncs_admin_survey_date_first_last_y.png)

### 숫자 추가 {#adding-numbers}

숫자 입력에 적합한 필드를 만들 수 있습니다.

![](assets/s_ncs_admin_survey_number.png)

숫자 필드에 숫자만 입력할 수 있습니다. 페이지가 승인되면 시작 컨트롤이 자동으로 적용됩니다.

데이터베이스에 데이터가 저장되는 필드에 따라 특수 서식 또는 특정 제한이 적용될 수 있습니다. 최대값과 최소값을 지정할 수도 있습니다. 이 유형의 필드는 다음과 같이 구성됩니다.

![](assets/s_ncs_admin_survey_number_edit.png)

기본값은 양식이 게시될 때 필드에 표시되는 값입니다. 사용자가 수정할 수 있습니다.

아래와 같이 **[!UICONTROL Advanced]** 탭을 통해 숫자 필드에 접두사 및/또는 접미사를 추가할 수 있습니다.

![](assets/s_ncs_admin_survey_number_ex_conf.png)

양식에서 렌더링은 다음과 같습니다.

![](assets/s_ncs_admin_survey_number_ex.png)

## 구독 확인란 {#subscription-checkboxes}

사용자가 하나 이상의 정보 서비스(뉴스레터, 경고, 실시간 알림 등)에 가입하거나 가입을 해지할 수 있는 컨트롤을 추가할 수 있습니다. 가입하려면 해당 서비스를 확인합니다.

구독 확인란을 만들려면 을 클릭합니다 **[!UICONTROL Advanced controls>Subscription]**.

![](assets/s_ncs_admin_survey_subscription_edit.png)

확인란 레이블을 지정하고 **[!UICONTROL Service]** 드롭다운 상자를 사용하여 관련 정보 서비스를 선택합니다.

>[!NOTE]
>
>정보 서비스는 [이 페이지에](../../delivery/using/managing-subscriptions.md)자세히 설명되어 있습니다.

사용자는 관련 옵션을 선택하여 서비스에 가입합니다.

![](assets/s_ncs_admin_survey_subscribe.png)

>[!CAUTION]
>
>사용자가 정보 서비스에 이미 가입되어 있고 양식을 승인할 때 이 서비스에 연결된 상자가 선택되지 않은 경우 해당 사용자는 구독을 취소하게 됩니다.

구독 및 레퍼러의 예는 [이 섹션에](../../web/using/about-surveys.md)있습니다.

## captcha 삽입 {#inserting-a-captcha}

captcha **테스트의** 목적은 웹 양식의 부정 사용을 방지하는 것입니다.

>[!CAUTION]
>
>양식에 여러 페이지가 포함되어 있는 경우 보안 조치를 피할 수 있도록 항상 저장소 상자 바로 앞에 마지막 페이지에 Captcha를 배치해야 합니다.

양식에 Captcha를 삽입하려면 도구 모음에서 첫 번째 단추를 클릭하고 선택을 **[!UICONTROL Advanced controls>Captcha]**&#x200B;클릭합니다.

![](assets/s_ncs_admin_survey_add_captcha.png)

필드의 레이블을 입력합니다. 이 레이블은 Captcha 표시 영역 앞에 표시됩니다. 이 레이블의 위치는 **[!UICONTROL Advanced]** 탭에서 변경할 수 있습니다.

![](assets/s_ncs_admin_survey_captcha_adv.png)

>[!NOTE]
>
>유형 컨트롤의 **[!UICONTROL captcha]** 경우 저장소 필드나 변수를 표시할 필요가 없습니다.

Captcha는 시각적 아래에 입력 필드를 배치하여 페이지에 삽입됩니다. 이러한 두 요소는 분리할 수 없으며 페이지 레이아웃 용도로 단일 항목으로 간주됩니다(단일 셀을 차지함).

![](assets/s_ncs_admin_survey_captcha_sample.png)

페이지가 확인되면 Captcha의 컨텐츠가 올바르게 입력되지 않은 경우 입력 필드가 빨간색으로 표시됩니다.

![](assets/s_ncs_admin_survey_captcha_error.png)

표시할 오류 메시지를 만들 수 있습니다. 이렇게 하려면 **[!UICONTROL Personalize the message]** **[!UICONTROL General]** 탭의 링크를 사용하십시오.

![](assets/s_ncs_admin_survey_captcha_error_msg.png)

>[!NOTE]
>
>캡처는 항상 8자입니다. 이 값은 수정할 수 없습니다.

## 파일 업로드 {#uploading-a-file}

페이지에 업로드 필드를 추가할 수 있습니다. 이 기능은 인트라넷 파일 공유에 유용합니다.

![](assets/s_ncs_admin_survey_download_file.png)

양식 페이지에 업로드 필드를 삽입하려면 페이지 편집기의 도구 모음에서 **[!UICONTROL Advanced controls > File...]** 메뉴를 선택합니다.

기본적으로 업로드된 파일은 **[!UICONTROL Resources > Online > Public resources]** 메뉴를 통해 액세스할 수 있는 리소스 파일에 저장됩니다. 스크립트를 사용하여 이 동작을 변경할 수 있습니다. 이 스크립트는 파일 조작과 관련된 기능을 [포함하여 Campaign JSAPI 문서에](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html)정의된 함수를 사용할 수 있습니다.

이러한 파일에 대한 링크를 로컬 변수 또는 데이터베이스 필드에 저장할 수 있습니다. 예를 들어 수신자 스키마를 확장하여 파일 기반 리소스에 대한 링크를 추가할 수 있습니다.

>[!CAUTION]
>
>* 이 유형의 파일은 보안 액세스(자격 증명 사용)가 있는 양식에 대해 예약해야 합니다.
>* Adobe Campaign은 업로드된 리소스의 크기 또는 유형을 제어하지 않습니다.따라서 안전한 형식 인트라넷 사이트에만 업로드 필드를 사용하는 것이 좋습니다.
>* 여러 서버가 인스턴스에 연결된 경우(로드 밸런싱 아키텍처) 웹 양식 호출이 동일한 서버에 도달하는지 확인해야 합니다.
>* 이러한 구현은 Adobe Campaign 컨설팅 팀의 지원이 필요합니다.
>



## 숨겨진 상수 삽입 {#inserting-a-hidden-constant}

사용자가 양식의 페이지 중 하나를 지날 때 필드를 강조 표시할 수 있습니다. 이렇게 하려면 페이지에 상수를 배치하고 값과 저장소 위치를 지정합니다.

이 필드는 사용자가 볼 수 없지만 사용자 프로필의 데이터를 보완하는 데 사용할 수 있습니다.

다음 예에서는 사용자가 이 페이지를 승인할 때마다 수신자 프로필의 **원본** 파일이 자동으로 채워집니다. 페이지에 상수가 표시되지 않습니다.

![](assets/s_ncs_admin_survey_constante.png)

