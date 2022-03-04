---
product: campaign
title: 사용 사례 - 이메일 게재 만들기
description: 사용 사례 - 이메일 게재 만들기
feature: Web Apps, Web Forms, Landing Pages
exl-id: e2679f12-459b-466d-9c82-60a28363b104
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 0%

---

# 활용 사례: 이메일 게재 만들기{#use-case-creating-an-email-delivery}

![](../../assets/common.svg)

이 사용 사례에서는 Adobe Campaign DCE(디지털 콘텐츠 편집기)를 사용하여 이메일 배달을 디자인하는 단계를 배웁니다.

Adobe의 최종 목표는 다음 사항을 포함하는 개인화된 템플릿으로 게재를 만드는 것입니다.

* 수신자의 직접 주소(이름과 두 번째 이름 사용)
* 외부 URL에 연결된 두 가지 유형의 링크
* 미러 페이지
* 웹 애플리케이션에 대한 링크

>[!NOTE]
>
>시작하기 전에 하나 이상이 있어야 합니다 **HTML 템플릿** 향후 게재 콘텐츠를 호스팅하도록 구성되었습니다.
>
>게재에서 **[!UICONTROL Properties]**, **[!UICONTROL Content editing mode]** ( **[!UICONTROL Advanced]** 탭)이 **[!UICONTROL DCE]**. 편집기의 최적 작업을 확인하려면 [콘텐츠 편집 모범 사례](content-editing-best-practices.md).

## 1단계 - 게재 만들기 {#step-1---creating-a-delivery}

새 게재를 만들려면 커서를 **캠페인** 탭을 클릭하고 **게재**. 다음 을(를) 클릭합니다. **만들기** 기존 게재 목록 위의 단추. 게재 만들기에 대한 자세한 내용은 [이 페이지](../../delivery/using/about-email-channel.md).

![](assets/delivery_step_1.png)

## 2단계 - 템플릿 선택 {#step-2---selecting-a-template}

게재 템플릿을 선택한 다음 게재의 이름을 지정합니다. 이 이름은 수신자가 아니라 Adobe Campaign 콘솔 사용자만 볼 수 있지만 게재 목록에는 이 제목이 표시됩니다. **[!UICONTROL Continue]**&#x200B;를 클릭합니다.

![](assets/dce_delivery_model.png)

## 3단계 - 컨텐츠 선택 {#step-3---selecting-a-content}

디지털 콘텐츠 편집기에는 다양한 구조(열, 텍스트 영역 등)가 있는 다양한 기본 제공 템플릿이 포함되어 있습니다.

사용할 콘텐츠 템플릿을 선택한 다음 **[!UICONTROL Start with the selected content]** 버튼을 클릭하여 만든 게재에서 템플릿을 표시합니다.

![](assets/dce_select_model.png)

을(를) 선택하여 Adobe Campaign 외부에서 만든 HTML 콘텐츠를 가져올 수도 있습니다 **[!UICONTROL From a file]**.

![](assets/dce_select_from_file_template.png)

나중에 사용할 수 있도록 이 컨텐츠를 템플릿으로 저장할 수 있습니다. 개인화된 콘텐츠 템플릿을 만들면 템플릿 목록에서 미리 볼 수 있습니다. 자세한 내용은 [템플릿 관리](template-management.md).

>[!CAUTION]
>
>를 사용하는 경우 **Adobe Campaign 웹 인터페이스** HTML 컨텐츠과 관련 이미지가 포함된 .zip 파일을 가져와야 합니다.

## 4단계 - 메시지 디자인 {#step-4---designing-the-message}

* 수신자의 이름과 두 번째 이름을 표시합니다

   수신자의 첫 번째 및 두 번째 이름을 게재의 텍스트 필드에 삽입하려면 선택한 텍스트 필드를 클릭한 다음 표시하려는 위치에 커서를 놓습니다. 팝업 도구 모음에서 첫 번째 아이콘을 클릭한 다음 **[!UICONTROL Personalization block]**. 선택 **[!UICONTROL Greetings]**&#x200B;를 클릭한 다음 **[!UICONTROL OK]**.

   ![](assets/dce_personalizationblock_greetings.png)

* 이미지에 링크 삽입

   이미지를 통해 게재 수신자를 외부 주소로 가져오려면 관련 이미지를 클릭하여 팝업 도구 모음을 표시하고 첫 번째 아이콘 위에 커서를 놓고 **[!UICONTROL Link to an external URL]**. 자세한 내용은 [링크 추가](editing-content.md#adding-a-link).

   ![](assets/dce_externalpage.png)

   에 링크의 URL을 입력합니다. **URL** 다음 형식을 사용하는 필드 **https://www.myURL.com**&#x200B;를 입력한 다음 확인합니다.

   언제든지 창 오른쪽의 섹션을 사용하여 링크를 변경할 수 있습니다.

* 텍스트에 링크 삽입

   외부 링크를 게재의 텍스트에 통합하려면 일부 텍스트나 텍스트 블록을 선택한 다음 팝업 도구 모음에서 첫 번째 아이콘을 클릭합니다. 클릭 **[!UICONTROL Link to an external URL]**&#x200B;에 링크 주소를 입력합니다. **[!UICONTROL URL]** 필드. 자세한 내용은 [링크 추가](editing-content.md#adding-a-link).

   언제든지 창 오른쪽의 섹션을 사용하여 링크를 변경할 수 있습니다.

   >[!CAUTION]
   >
   >에 입력한 텍스트 **[!UICONTROL Label]** 필드는 원래 텍스트를 대체합니다.

* 미러 페이지 추가

   수신자가 웹 브라우저에서 게재 콘텐츠를 볼 수 있도록 하려면 미러 페이지에 대한 링크를 게재에 통합할 수 있습니다.

   게시된 링크를 볼 텍스트 필드를 클릭합니다. 팝업 도구 모음에서 첫 번째 아이콘을 클릭하고 **[!UICONTROL Personalization block]**, 그런 다음 **[!UICONTROL Link to Mirror Page (MirrorPage)]**. 클릭 **[!UICONTROL Save]** 확인합니다.

   ![](assets/dce_mirrorpage.png)

   >[!CAUTION]
   >
   >개인화 블록 레이블은 게재의 원래 텍스트를 자동으로 대체합니다.

* 웹 애플리케이션에 대한 링크 통합

   디지털 콘텐츠 편집기를 사용하면 랜딩 페이지나 양식 페이지와 같은 Adobe Campaign 콘솔에서 웹 애플리케이션에 대한 링크를 통합할 수 있습니다. 자세한 내용은 [웹 응용 프로그램에 연결](editing-content.md#link-to-a-web-application).

   웹 응용 프로그램에 대한 링크의 텍스트 필드를 선택한 다음 첫 번째 아이콘을 클릭합니다. 선택 **[!UICONTROL Link to a Web application]**&#x200B;를 클릭한 다음, **웹 애플리케이션** 필드.

   ![](assets/dce_webapp.png)

   클릭 **저장** 확인합니다.

   >[!NOTE]
   >
   >이 단계를 수행하려면 미리 하나 이상의 웹 응용 프로그램을 저장해야 합니다. 다음 항목에서 찾을 수 있습니다. **[!UICONTROL Campaigns > Web applications]** 탭의 섹션을 참조하십시오.

## 5단계 - 게재 저장 {#step-5---saving-the-delivery}

컨텐츠가 통합되면 을(를) 클릭하여 게재를 저장합니다 **저장**. 이제 의 게재 목록에 표시됩니다. **[!UICONTROL Campaigns > Deliveries]** 탭.
