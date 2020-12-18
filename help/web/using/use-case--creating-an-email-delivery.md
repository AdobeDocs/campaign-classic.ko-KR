---
solution: Campaign Classic
product: campaign
title: 사용 사례 - 이메일 배달 만들기
description: 이메일 배달 사용 사례 만들기
audience: web
content-type: reference
topic-tags: editing-html-content
translation-type: tm+mt
source-git-commit: 46aa896929c960abeb501642a5ffbbb56de4802e
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 0%

---


# 사용 사례: 이메일 게재 만들기{#use-case-creating-an-email-delivery}

이 경우 Adobe Campaign DCE(Digital Content Editor)를 사용하여 이메일 배달을 디자인하는 단계를 알아봅니다.

Adobe의 최종 목표는 다음 사항을 포함하는 개인화된 템플릿을 사용하여 전달을 만드는 것입니다.

* 받는 사람의 직접 주소(첫 번째 및 두 번째 이름 사용)
* 외부 URL에 대한 2가지 링크 유형
* 거울 페이지
* 웹 응용 프로그램에 대한 링크

>[!NOTE]
>
>시작하기 전에 나중에 배달할 내용을 호스팅하도록 하나 이상의 **HTML 템플릿**&#x200B;을(를) 구성해야 합니다.
>
>**[!UICONTROL Properties]** 배달에서 **[!UICONTROL Content editing mode]**(**[!UICONTROL Advanced]** 탭의)이 **[!UICONTROL DCE]**&#x200B;으로 설정되어 있는지 확인합니다. 편집기의 최적의 작업을 확인하려면 [컨텐츠 편집 우수 사례](../../web/using/content-editing-best-practices.md)를 참조하십시오.

## 1단계 - 배달 {#step-1---creating-a-delivery} 만들기

새 배달을 만들려면 **캠페인** 탭에 커서를 놓고 **배달**&#x200B;을 클릭합니다. 그런 다음 기존 배달 목록 위의 **만들기** 단추를 클릭합니다. 배달 만들기에 대한 자세한 내용은 [이 페이지](../../delivery/using/about-email-channel.md)를 참조하십시오.

![](assets/delivery_step_1.png)

## 2단계 - 템플릿 {#step-2---selecting-a-template} 선택

배달 템플릿을 선택한 다음 배달 이름을 지정합니다. 이 이름은 수신자가 아니라 Adobe Campaign 콘솔 사용자에게만 표시되지만 배달 목록에 이 제목이 표시됩니다. **[!UICONTROL Continue]**&#x200B;을(를) 클릭합니다.

![](assets/dce_delivery_model.png)

## 3단계 - 내용 선택 {#step-3---selecting-a-content}

디지털 컨텐츠 편집기에는 다양한 구조(열, 텍스트 영역 등)가 포함된 다양한 기본 템플릿이 포함되어 있습니다.

사용할 컨텐츠 템플릿을 선택한 다음 **[!UICONTROL Start with the selected content]** 단추를 클릭하여 만든 게재에 템플릿을 표시합니다.

![](assets/dce_select_model.png)

**[!UICONTROL From a file]**&#x200B;을 선택하여 Adobe Campaign 외부에서 만든 HTML 내용을 가져올 수도 있습니다.

![](assets/dce_select_from_file_template.png)

나중에 사용할 수 있도록 이 컨텐츠를 템플릿으로 저장할 수 있습니다. 개인화된 컨텐츠 템플릿이 작성되면 템플릿 목록에서 미리 볼 수 있습니다. 자세한 내용은 [템플릿 관리](../../web/using/template-management.md)를 참조하십시오.

>[!CAUTION]
>
>**Adobe Campaign 웹 인터페이스**&#x200B;를 사용하는 경우 HTML 내용 및 관련 이미지가 포함된 .zip 파일을 가져와야 합니다.

## 4단계 - 메시지 {#step-4---designing-the-message} 디자인

* 받는 사람의 이름 및 두 번째 이름 표시

   수신자의 첫 번째 및 두 번째 이름을 전달의 텍스트 필드에 삽입하려면 선택한 텍스트 필드를 클릭한 다음 표시하려는 위치에 커서를 놓습니다. 팝업 도구 모음에서 첫 번째 아이콘을 클릭한 다음 **[!UICONTROL Personalization block]**&#x200B;을 클릭합니다. **[!UICONTROL Greetings]**&#x200B;을 선택하고 **[!UICONTROL OK]**&#x200B;을 클릭합니다.

   ![](assets/dce_personalizationblock_greetings.png)

* 이미지에 링크 삽입

   전달 받는 사람을 이미지를 통해 외부 주소로 가져오려면 관련 이미지를 클릭하여 팝업 도구 모음을 표시하고 커서를 첫 번째 아이콘 위에 놓은 다음 **[!UICONTROL Link to an external URL]**&#x200B;을 클릭합니다. 자세한 내용은 [링크 추가](../../web/using/editing-content.md#adding-a-link)를 참조하십시오.

   ![](assets/dce_externalpage.png)

   **https://www.myURL.com** 형식을 사용하여 **URL** 필드에 링크의 URL을 입력한 다음 확인합니다.

   창의 오른쪽에 있는 섹션을 사용하여 링크를 언제든지 변경할 수 있습니다.

* 텍스트에 링크 삽입

   외부 링크를 전달의 텍스트에 통합하려면 일부 텍스트나 텍스트 블록을 선택한 다음 팝업 도구 모음에서 첫 번째 아이콘을 클릭합니다. **[!UICONTROL Link to an external URL]**&#x200B;을 클릭하고 링크 주소를 **[!UICONTROL URL]** 필드에 입력합니다. 자세한 내용은 [링크 추가](../../web/using/editing-content.md#adding-a-link)를 참조하십시오.

   창의 오른쪽에 있는 섹션을 사용하여 링크를 언제든지 변경할 수 있습니다.

   >[!CAUTION]
   >
   >**[!UICONTROL Label]** 필드에 입력한 텍스트가 원래 텍스트를 대체합니다.

* 미러 페이지 추가

   수신자가 웹 브라우저에서 배달 컨텐츠를 볼 수 있도록 미러 페이지에 대한 링크를 게재에 통합할 수 있습니다.

   게시된 링크를 볼 텍스트 필드를 클릭합니다. 팝업 도구 모음에서 첫 번째 아이콘을 클릭하고 **[!UICONTROL Personalization block]**, **[!UICONTROL Link to Mirror Page (MirrorPage)]** 순으로 선택합니다. **[!UICONTROL Save]**&#x200B;을 클릭하여 확인합니다.

   ![](assets/dce_mirrorpage.png)

   >[!CAUTION]
   >
   >개인화 블록 레이블은 전달의 원래 텍스트를 자동으로 대체합니다.

* 웹 애플리케이션에 대한 링크 통합

   디지털 컨텐츠 편집기를 사용하면 랜딩 페이지 또는 양식 페이지와 같은 Adobe Campaign 콘솔에서 웹 애플리케이션에 대한 링크를 통합할 수 있습니다. 자세한 내용은 [웹 응용 프로그램 링크](../../web/using/editing-content.md#link-to-a-web-application)를 참조하십시오.

   웹 응용 프로그램에 대한 링크의 텍스트 필드를 선택한 다음 첫 번째 아이콘을 클릭합니다. **[!UICONTROL Link to a Web application]**&#x200B;을 선택한 다음 **웹 응용 프로그램** 필드 끝에 있는 아이콘을 클릭하여 원하는 응용 프로그램을 선택합니다.

   ![](assets/dce_webapp.png)

   **저장**&#x200B;을 클릭하여 확인합니다.

   >[!NOTE]
   >
   >이 단계를 수행하려면 먼저 하나 이상의 웹 응용 프로그램을 저장해야 합니다. 이러한 항목은 콘솔의 **[!UICONTROL Campaigns > Web applications]** 탭에서 찾을 수 있습니다.

## 5단계 - 배달 {#step-5---saving-the-delivery} 저장

콘텐트가 통합되면 **저장**&#x200B;을 클릭하여 배달을 저장합니다. 이제 **[!UICONTROL Campaigns > Deliveries]** 탭에 있는 배달 목록에 표시됩니다.
