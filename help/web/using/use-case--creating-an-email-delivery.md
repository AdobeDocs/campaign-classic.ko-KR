---
title: '"사용 사례:이메일 배달 만들기"'
seo-title: '"사용 사례:이메일 배달 만들기"'
description: '"사용 사례:이메일 배달 만들기"'
seo-description: null
page-status-flag: never-activated
uuid: 7cd6329c-63d5-4cf0-9451-f0b4c2eaf0dd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: editing-html-content
discoiquuid: 4ec34980-62a2-47b9-b103-de4290925624
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 36beb1eca48c698634c7548e0f931ab3fe17c021

---


# 사용 사례:이메일 배달 만들기{#use-case-creating-an-email-delivery}

이 사용 사례에서는 Adobe Campaign DCE(Digital Content Editor)를 사용하여 이메일 배달을 디자인하는 단계를 알아봅니다.

Adobe의 최종 목표는 다음을 포함하는 개인화된 템플릿을 사용하여 전달을 만드는 것입니다.

* 받는 사람의 직접 주소(첫 번째 및 두 번째 이름 사용)
* 외부 URL에 대한 두 가지 유형의 링크
* 미러 페이지
* 웹 응용 프로그램에 대한 링크

>[!NOTE]
>
>시작하기 전에 향후 게재 컨텐츠를 호스팅하도록 **구성된 HTML 템플릿이** 하나 이상 있어야 합니다.
>
>전달에서 **[!UICONTROL Properties]** 탭에서 **[!UICONTROL Content editing mode]** ( **[!UICONTROL Advanced]** 탭)가 로 설정되어 있는지 확인합니다 **[!UICONTROL DCE]**. 편집기의 최적 작업을 확인하려면 컨텐츠 [편집 우수 사례를](../../web/using/content-editing-best-practices.md)참조하십시오.

## 1단계 - 배달 만들기 {#step-1---creating-a-delivery}

새 배달을 만들려면 캠페인 탭에 커서를 놓고 **배달을** 클릭합니다 ****. 그런 다음 **기존 배달** 목록 위에 있는 만들기 단추를 클릭합니다. 배달 만들기에 대한 자세한 내용은 [이 페이지를](../../delivery/using/about-email-channel.md)참조하십시오.

![](assets/delivery_step_1.png)

## 2단계 - 템플릿 선택 {#step-2---selecting-a-template}

배달 템플릿을 선택한 다음 배달 이름을 지정합니다. 이 이름은 Adobe Campaign 콘솔의 사용자만 볼 수 있고 수신자는 볼 수 없지만 이 제목은 배달 목록에 표시됩니다. 클릭 **[!UICONTROL Continue]**.

![](assets/dce_delivery_model.png)

## 3단계 - 컨텐츠 선택 {#step-3---selecting-a-content}

디지털 컨텐츠 편집기에는 다양한 구조(열, 텍스트 영역 등)가 포함된 다양한 기본 템플릿이 포함되어 있습니다.

사용할 컨텐츠 템플릿을 선택한 다음 **[!UICONTROL Start with the selected content]** 단추를 클릭하여 생성된 전달에 템플릿을 표시합니다.

![](assets/dce_select_model.png)

Adobe Campaign 외부에서 만든 HTML 컨텐츠를 선택하여 가져올 수도 **[!UICONTROL From a file]**&#x200B;있습니다.

![](assets/dce_select_from_file_template.png)

나중에 사용할 수 있도록 이 컨텐츠를 템플릿으로 저장할 수 있습니다. 개인화된 컨텐츠 템플릿이 만들어지면 템플릿 목록에서 미리 볼 수 있습니다. 자세한 내용은 템플릿 관리를 [참조하십시오](../../web/using/template-management.md).

>[!CAUTION]
>
>Adobe Campaign 웹 인터페이스를 ****&#x200B;사용하는 경우 HTML 컨텐츠 및 관련 이미지가 포함된 .zip 파일을 가져와야 합니다.

## 4단계 - 메시지 디자인 {#step-4---designing-the-message}

* 수신자의 첫 번째 및 두 번째 이름 표시

   수신자의 이름과 두 번째 이름을 전달의 텍스트 필드에 삽입하려면 선택한 텍스트 필드를 클릭한 다음 표시하려는 위치에 커서를 놓습니다. 팝업 도구 모음에서 첫 번째 아이콘을 클릭한 다음 을 **[!UICONTROL Personalization block]**&#x200B;클릭합니다. 을 **[!UICONTROL Greetings]**&#x200B;선택한 다음 을 클릭합니다 **[!UICONTROL OK]**.

   ![](assets/dce_personalizationblock_greetings.png)

* 이미지에 링크 삽입

   전달 받는 사람을 이미지를 통해 외부 주소로 가져오려면 관련 이미지를 클릭하여 팝업 도구 모음을 표시한 다음 커서를 첫 번째 아이콘 위에 놓고 을 클릭합니다 **[!UICONTROL Link to an external URL]**. 자세한 내용은 링크 [추가를 참조하십시오](../../web/using/editing-content.md#adding-a-link).

   ![](assets/dce_externalpage.png)

   URL 필드에 다음 형식을 **사용하여** 링크의 URL을 **입력한 다음**&#x200B;확인합니다.

   언제든지 창 오른쪽에 있는 섹션을 사용하여 링크를 변경할 수 있습니다.

* 텍스트에 링크 삽입

   외부 링크를 전달의 텍스트에 통합하려면 일부 텍스트 또는 텍스트 블록을 선택한 다음 팝업 도구 모음에서 첫 번째 아이콘을 클릭합니다. 을 **[!UICONTROL Link to an external URL]**&#x200B;클릭하고 **[!UICONTROL URL]** 필드에 링크 주소를 입력합니다. 자세한 내용은 링크 [추가를 참조하십시오](../../web/using/editing-content.md#adding-a-link).

   언제든지 창 오른쪽에 있는 섹션을 사용하여 링크를 변경할 수 있습니다.

   >[!CAUTION]
   >
   >필드에 입력한 텍스트가 **[!UICONTROL Label]** 원래 텍스트를 대체합니다.

* 미러 페이지 추가

   수신자가 웹 브라우저에서 전달 컨텐츠를 볼 수 있도록 하려면 미러 페이지에 대한 링크를 게재에 통합할 수 있습니다.

   게시된 링크를 볼 텍스트 필드를 클릭합니다. 팝업 도구 모음에서 첫 번째 아이콘을 클릭한 다음 **[!UICONTROL Personalization block]**&#x200B;을 **[!UICONTROL Link to Mirror Page (MirrorPage)]**&#x200B;선택합니다. 을 **[!UICONTROL Save]** 클릭하여 확인합니다.

   ![](assets/dce_mirrorpage.png)

   >[!CAUTION]
   >
   >개인화 블록 레이블은 전달의 원래 텍스트를 자동으로 대체합니다.

* 웹 애플리케이션에 대한 링크 통합

   디지털 컨텐츠 편집기를 사용하면 랜딩 페이지 또는 양식 페이지와 같은 Adobe Campaign 콘솔에서 웹 애플리케이션에 대한 링크를 통합할 수 있습니다. 자세한 내용은 웹 애플리케이션에 [대한](../../web/using/editing-content.md#link-to-a-web-application)링크를 참조하십시오.

   웹 응용 프로그램에 대한 링크의 텍스트 필드를 선택한 다음 첫 번째 아이콘을 클릭합니다. 웹 애플리케이션 **[!UICONTROL Link to a Web application]**&#x200B;필드 끝에 있는 아이콘을 클릭하여 원하는 애플리케이션을 **선택합니다** .

   ![](assets/dce_webapp.png)

   저장을 **클릭하여** 확인합니다.

   >[!NOTE]
   >
   >이 단계를 수행하려면 먼저 하나 이상의 웹 응용 프로그램을 저장해야 합니다. 콘솔의 **[!UICONTROL Campaigns > Web applications]** 탭에서 찾을 수 있습니다.

## 5단계 - 배달 저장 {#step-5---saving-the-delivery}

컨텐츠가 통합되면 저장을 클릭하여 배달을 **저장합니다**. 이제 **[!UICONTROL Campaigns > Deliveries]** 탭에 있는 배달 목록에 표시됩니다.
