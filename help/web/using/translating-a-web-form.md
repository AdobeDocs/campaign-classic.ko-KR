---
solution: Campaign Classic
product: campaign
title: 웹 양식 번역
description: 웹 양식 번역
audience: web
content-type: reference
topic-tags: web-forms
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1565'
ht-degree: 1%

---


# 웹 양식 번역{#translating-a-web-form}

웹 애플리케이션을 여러 언어로 현지화할 수 있습니다.

Adobe Campaign 콘솔에서 직접 번역 수행(편집기에서 번역 [관리 참조](#managing-translations-in-the-editor))하거나, 문자열을 내보내거나 가져와 번역 외부화(번역 [의 외부화 참조](#externalizing-translation))할 수 있습니다.

기본적으로 사용할 수 있는 번역 언어 목록은 [양식 표시 언어 변경에 자세히 설명되어 있습니다](#changing-forms-display-language).

웹 응용 프로그램은 편집 언어로 디자인되었습니다.번역할 레이블 및 기타 컨텐츠를 입력하는 데 사용되는 참조 언어입니다.

기본 언어는 해당 액세스 URL에 언어 설정이 추가되지 않는 경우 웹 응용 프로그램이 표시되는 언어입니다.

>[!NOTE]
>
>기본적으로 편집 언어와 기본 언어는 콘솔 언어와 동일합니다.

## 언어 선택 {#choosing-languages}

하나 이상의 번역 언어를 정의하려면 웹 응용 프로그램의 **[!UICONTROL Properties]** 단추를 클릭한 다음 **[!UICONTROL Localization]** 탭을 클릭합니다. 단추를 클릭하여 웹 응용 프로그램의 새 번역 언어를 정의합니다. **[!UICONTROL Add]**

>[!NOTE]
>
>또한 이 창에서 기본 언어 및 편집 언어를 변경할 수 있습니다.

![](assets/s_ncs_admin_survey_add_lang.png)

웹 응용 프로그램에 대한 번역 언어를 추가할 때(또는 기본 언어와 편집 언어가 다른 경우) **[!UICONTROL Translation]** 하위 탭이 **[!UICONTROL Edit]** 탭에 추가되어 번역을 관리합니다.

Adobe Campaign에는 다중 언어 번역을 번역하고 관리하는 도구가 포함되어 있습니다. 이 편집기를 사용하면 번역하거나 승인할 문자열을 보고, 인터페이스에 직접 번역문을 입력하거나, 문자열을 가져오기/내보내어 번역문을 외부화할 수 있습니다.

## 편집기에서 번역 관리 {#managing-translations-in-the-editor}

### 문자열 수집 {#collecting-strings}

이 **[!UICONTROL Translations]** 탭에서는 웹 응용 프로그램을 구성하는 문자 문자열에 대한 번역을 입력할 수 있습니다.

이 탭을 처음 열면 데이터가 포함되지 않습니다. 웹 응용 프로그램의 문자열을 업데이트하려면 **[!UICONTROL Collect the strings to translate]** 링크를 클릭합니다.

Adobe Campaign은 모든 정적 요소의 탭에 정의된 필드 및 문자열 **[!UICONTROL Texts]** 의 레이블을 수집합니다.HTML 블록, Javascript 등 정적 요소는 웹 양식의 [정적 요소에 자세히 설명되어 있습니다](../../web/using/static-elements-in-a-web-form.md).

![](assets/s_ncs_admin_survey_trad_tab.png)

>[!CAUTION]
>
>이 프로세스는 처리할 데이터의 양에 따라 몇 분 정도 걸릴 수 있습니다.
> 
>시스템 사전에서 일부 번역이 누락되었다는 경고가 나타나면 시스템 문자열 [변환을 참조하십시오](#translating-the-system-strings).

문자열을 번역할 때마다 번역된 내용이 번역 사전에 추가됩니다.

컬렉션 프로세스에서 번역이 이미 존재함을 감지하면 이 번역이 문자열의 열에 **[!UICONTROL Text]** 표시됩니다. 문자열의 상태가 로 전환됩니다 **[!UICONTROL Translated]**.

번역되지 않은 문자열의 경우 **[!UICONTROL Text]** 필드는 비어 있고 상태는 **[!UICONTROL To translate]**&#x200B;입니다.

### 문자열 필터링 {#filtering-strings}

기본적으로 웹 애플리케이션의 각 번역 언어가 표시됩니다. 두 가지 기본 필터가 있습니다.언어 및 상태. 단추를 **[!UICONTROL Filters]** 클릭한 다음 을 클릭하여 **[!UICONTROL By language or status]** 일치하는 드롭다운 상자를 표시합니다. 고급 필터를 만들 수도 있습니다. 자세한 정보는 이 [페이지](../../platform/using/creating-filters.md#creating-an-advanced-filter)를 참조하십시오.

![](assets/s_ncs_admin_survey_trad_tab_en.png)

드롭다운 **[!UICONTROL Language]** 상자로 이동하여 번역 언어를 선택합니다.

번역되지 않은 문자열만 표시하려면 드롭다운 상자 **[!UICONTROL To translate]** 에서 **[!UICONTROL Status]** 선택합니다. 번역되거나 승인된 문자열만 표시할 수도 있습니다.

### 문자열 번역 {#translating-strings}

1. 단어를 번역하려면 문자열 목록에서 해당 줄을 두 번 클릭합니다.

   ![](assets/s_ncs_admin_survey_trad_tab_add_term.png)

   소스 문자열은 창의 위쪽 섹션에 표시됩니다.

1. 아래 섹션에 번역을 입력합니다. 승인하려면 옵션을 **[!UICONTROL Translation approved]** 선택합니다.

   >[!NOTE]
   >
   >번역 승인은 선택 사항이며 프로세스를 차단하지 않습니다.

   승인되지 않은 번역은 로 표시됩니다 **[!UICONTROL Translated]**. 승인된 번역은 로 표시됩니다 **[!UICONTROL Approved]**.

## 번역 외부화 {#externalizing-translation}

문자 문자열을 내보내거나 가져와 Adobe Campaign 이외의 도구로 변환할 수 있습니다.

>[!CAUTION]
>
>문자열을 내보낸 후에는 통합 도구를 사용하여 번역하지 마십시오. 따라서 번역을 다시 가져오면 충돌이 발생합니다.

### 파일 내보내기 {#exporting-files}

1. 가져올 문자열이 있는 웹 애플리케이션을 선택하고 마우스 오른쪽 버튼을 클릭한 다음 **[!UICONTROL Actions > Export strings for translation...]**

   ![](assets/s_ncs_admin_survey_trad_export.png)

1. 다음 중 하나를 **[!UICONTROL Export strategy]** 선택합니다.

   * **[!UICONTROL One file per language]**:내보내기 시 번역 언어당 하나의 파일이 생성됩니다. 각 파일은 선택한 모든 웹 응용 프로그램에 공통으로 사용됩니다.
   * **[!UICONTROL One file per Web application]**:내보내기를 수행하면 선택한 웹 응용 프로그램당 하나의 파일이 생성됩니다. 각 파일에는 모든 번역 언어가 포함됩니다.

      >[!NOTE]
      >
      >이 유형의 내보내기는 XLIFF 내보내기에 사용할 수 없습니다.

   * **[!UICONTROL One file per language and per Web application]**:내보내기로 여러 파일이 생성됩니다. 각 파일에는 웹 응용 프로그램당 하나의 번역 언어가 포함됩니다.
   * **[!UICONTROL One file for all]**:내보내기는 모든 웹 응용 프로그램에 대해 단일 다중 언어 파일을 생성합니다. 선택한 모든 웹 응용 프로그램에 대한 모든 번역 언어가 포함됩니다.

      >[!NOTE]
      >
      >이 유형의 내보내기는 XLIFF 내보내기에 사용할 수 없습니다.

1. 그런 다음 파일을 **[!UICONTROL Target folder]** 기록할 위치를 선택합니다.
1. 파일 형식( **[!UICONTROL CSV]** 또는 **[!UICONTROL XLIFF]** )을 선택하고 을 클릭합니다 **[!UICONTROL Start]**.

![](assets/s_ncs_admin_survey_trad_export_start.png)

>[!NOTE]
>
>내보내기 파일의 이름은 자동으로 생성됩니다. 동일한 내보내기를 여러 번 수행하면 기존 파일이 새 파일로 대체됩니다. 이전 파일을 유지해야 하는 경우 를 변경한 **[!UICONTROL Target folder]** 다음 다시 클릭하여 내보내기를 **[!UICONTROL Start]** 실행합니다.

파일을 **CSV 형식으로**&#x200B;내보낼 때 각 언어는 상태 및 승인 상태에 연결됩니다. 승인 **?** 열을 사용하면 번역을 승인할 수 있습니다. 이 열에는 **예** 또는 아니요 값이 **포함될 수 있습니다**. 통합 편집기의 경우(편집기에서 [번역](#managing-translations-in-the-editor)관리 참조), 변환 승인은 선택 사항이며 프로세스를 차단하지는 않습니다.

### 파일 가져오기 {#importing-files}

외부 변환이 완료되면 번역된 파일을 가져올 수 있습니다.

1. 웹 애플리케이션 목록으로 이동하여 마우스 오른쪽 버튼을 클릭한 다음 **[!UICONTROL Actions > Import translated strings...]**

   >[!NOTE]
   >
   >번역을 통해 관련 웹 애플리케이션을 선택할 필요가 없습니다. 웹 응용 프로그램 목록의 어디에나 커서를 놓습니다.

   ![](assets/s_ncs_admin_survey_trad_import.png)

1. 가져올 파일을 선택한 다음 을 클릭합니다 **[!UICONTROL Upload]**.

   ![](assets/s_ncs_admin_survey_trad_import_start.png)

>[!NOTE]
>
>외부 번역은 항상 내부 번역에 우선합니다. 충돌이 발생하는 경우 내부 번역문을 외부 번역으로 덮어씁니다.

## 양식 표시 언어 변경 {#changing-forms-display-language}

웹 양식은 웹 응용 프로그램 속성의 **[!UICONTROL Localization]** 탭에 지정된 기본 언어로 표시됩니다. 언어를 변경하려면 URL 끝에 다음 문자를 추가해야 합니다(여기서 **xx는** 언어의 기호임).

```
?lang=xx
```

if the language is the first or only parameter of the URL. 예: **https://myserver/webApp/APP34?lang=en**

```
&lang=xx
```

if there are other parameters before the language in the URL. 예: **https://myserver/webApp/APP34?status=1&amp;lang=en**

기본적으로 사용할 수 있는 번역 언어와 사전은 아래에 나와 있습니다.

**기본 시스템 사전**:일부 언어에는 시스템 문자열의 번역이 포함된 기본 사전이 포함되어 있습니다. 자세한 내용은 시스템 문자열 [변환을 참조하십시오](#translating-the-system-strings).

**달력 관리**:웹 응용 프로그램의 페이지에는 날짜를 입력하는 달력이 포함될 수 있습니다. 기본적으로 이 달력은 여러 언어(일 번역, 날짜 형식)로 사용할 수 있습니다.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>언어(심볼)</strong><br /> </td> 
   <td> <strong>기본 시스템 사전</strong><br /> </td> 
   <td> <strong>달력 관리</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 독일어(de)<br /> </td> 
   <td> yes<br /> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 영어(영어)<br /> </td> 
   <td> yes<br /> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 영어(미국)(en_US)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 영어(영국)(en_GB)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 아랍어(ar)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 중국어(zh)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 한국어(ko)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 덴마크어(da)<br /> </td> 
   <td> yes<br /> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 스페인어(es)<br /> </td> 
   <td> yes<br /> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 에스토니아어(et)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 핀란드어(fi)<br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 프랑스어(fr)<br /> </td> 
   <td> yes<br /> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 프랑스어(벨기에)(fr_BE)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 프랑스어(프랑스)(fr_FR)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 그리스어(el)<br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 히브리어(he)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 헝가리어(hu)<br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 인도네시아(id)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 아일랜드어(ga)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 이탈리아어(it)<br /> </td> 
   <td> yes<br /> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 이탈리아어(이탈리아)(it_IT)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 이탈리아어(스위스)(it_CH)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 일본어(ja)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 라트비아어(lv)<br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 리투아니아어(lt)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 몰타(mt)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 네덜란드어(nl)<br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 네덜란드어(벨기에)(nl_BE)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 네덜란드어(홀랜드)(nl_NL)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 노르웨이어(노르웨이)(no_NO)<br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 폴란드어(pl)<br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 포르투갈어(pt)<br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 포르투갈어(브라질)(pt_BR)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 포르투갈어(포르투갈)(pt_PT)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 러시아어(ru)<br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 슬로베니아어(sl)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 슬로바키아어(sk)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 스웨덴어(sv)<br /> </td> 
   <td> yes<br /> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 스웨덴어(핀란드)(sv_FI)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 스웨덴어(스웨덴)(sv_SE)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 체코어(cs)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 태국어(th)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 베트남어(vi)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 왈룬 (wa)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>기본적으로 제공되는 언어가 아닌 다른 언어를 추가하려면 번역 언어 [추가를 참조하십시오](#adding-a-translation-language)

## 예:여러 언어로 웹 애플리케이션 표시 {#example--displaying-a-web-application-in-several-languages}

다음 웹 양식을 4개 언어로 사용할 수 있습니다.영어, 프랑스어, 독일어 및 스페인어 문자 문자열은 모두 웹 양식의 **[!UICONTROL Translation]** 탭을 통해 번역되었습니다. 설문 조사가 게시될 때 기본 언어는 영어이므로 표준 URL을 사용하여 영어로 표시합니다.

![](assets/s_ncs_admin_survey_trad_sample_fr.png)

URL의 끝에 **?lang=fr** 을 추가하여 프랑스어로 표시합니다.

>[!NOTE]
>
>각 언어에 대한 기호 목록은 [양식 표시 언어 변경에 자세히 설명되어 있습니다](#changing-forms-display-language).

![](assets/s_ncs_admin_survey_trad_sample_en.png)

스페인어나 **?lang=es** 또는 **?lang=de** 를 추가하여표시할 수 있습니다.

>[!NOTE]
>
>이 웹 응용 프로그램에 다른 매개 변수가 이미 사용되고 있으면 add **&amp;lang=**.\
>예: **https://myserver/webApp/APP34?status=1&amp;lang=en**

## 고급 변환 구성 {#advanced-translation-configuration}

>[!CAUTION]
>
>이 섹션은 전문가 사용자에게만 해당됩니다.

### 시스템 문자열 번역 {#translating-the-system-strings}

시스템 문자열은 모든 웹 응용 프로그램에서 사용되는 기본 문자 문자열입니다. 예: **[!UICONTROL Next]** , **[!UICONTROL Previous]**, **[!UICONTROL Approve]** 버튼, **[!UICONTROL Loading]** 메시지 등 기본적으로 일부 언어에는 이러한 문자열에 대한 번역이 포함된 사전이 포함되어 있습니다. 언어 목록은 [양식 표시 언어 변경에 자세히 설명되어 있습니다](#changing-forms-display-language).

웹 응용 프로그램을 시스템 사전이 번역되지 않은 언어로 번역할 경우 일부 번역이 누락되었음을 알리는 경고 메시지가 나타납니다.

![](assets/s_ncs_admin_survey_trad_error.png)

언어를 추가하려면 다음 단계를 수행하십시오.

1. Adobe Campaign 트리으로 이동하고 을 클릭합니다 **[!UICONTROL Administration > Configuration > Global dictionary > System dictionary]** .
1. 창의 위쪽 섹션에서 번역할 시스템 문자열을 선택한 다음 아래 섹션 **[!UICONTROL Add]** 에서 을 클릭합니다.

   ![](assets/s_ncs_admin_survey_trad_system_translation.png)

1. 번역 언어를 선택하고 문자열의 번역을 입력합니다. 옵션을 선택하여 번역을 승인할 수 **[!UICONTROL Translation validated]** 있습니다.

   ![](assets/s_ncs_admin_survey_trad_system_translation2.png)

   >[!NOTE]
   >
   >번역 승인은 선택 사항이며 프로세스를 차단하지 않습니다.

>[!CAUTION]
>
>기본 시스템 문자열을 삭제하지 마십시오.

### 번역 언어 추가 {#adding-a-translation-language}

웹 응용 프로그램을 기본 언어 이외의 언어로 번역할 경우(양식 표시 언어 [변경](#changing-forms-display-language)참조), 새 번역 언어를 추가해야 합니다.

1. Adobe Campaign 트리의 **[!UICONTROL Administration > Platform > Itemized lists]** 노드를 클릭하고 목록에서 **[!UICONTROL Languages available for translation]** 선택합니다. 사용 가능한 번역 목록은 창의 아래 섹션에 표시됩니다.

   ![](assets/s_ncs_admin_survey_trad_new_itemized_list_1.png)

1. 단추를 **[!UICONTROL Add]** 클릭한 다음 이미지의 **[!UICONTROL Internal name]**&#x200B;및 **[!UICONTROL Label]** 식별자(플래그)를 입력합니다. 새 이미지를 추가하려면 관리자에게 문의하십시오.

   ![](assets/s_ncs_admin_survey_trad_new_itemized_list_2.png)

