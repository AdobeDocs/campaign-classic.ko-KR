---
title: 웹 애플리케이션 번역
seo-title: 웹 애플리케이션 번역
description: 웹 애플리케이션 번역
seo-description: null
page-status-flag: never-activated
uuid: 7b24a872-d3d1-4473-a6f9-96ba2a0eee8b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-applications
discoiquuid: 328e5b2f-8596-4eda-8ac5-57cb29bfb691
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c9c9d5f96856ce9e19571bad032d2bf04eaa60bd

---


# 웹 애플리케이션 번역{#translating-a-web-application}

Adobe Campaign Digital 콘텐츠 편집기(DCE)로 만든 웹 애플리케이션 페이지를 번역할 수 있습니다.

웹 애플리케이션의 **[!UICONTROL Localization]** 탭을 통해 하나 이상의 언어를 추가로 선택하는 **[!UICONTROL Properties]** 경우 DCE로 편집한 페이지에서 HTML 컨텐츠 블록을 추가할 때 새로운 옵션을 사용할 수 있습니다.

이 옵션을 사용하면 블록 컨텐츠를 번역해야 하는지 여부를 지정할 수 있습니다.

변환할 문자열은 응용 프로그램의 **[!UICONTROL Translations]** 탭을 통해 웹 응용 프로그램의 다른 문자열과 동일한 방법으로 수집됩니다. For more on this, refer to [this page](../../web/using/translating-a-web-form.md).

변환할 문자열에 플래그를 지정하려면

1. 웹 애플리케이션에서 DCE로 편집한 컨텐츠 페이지를 엽니다.

   ![](assets/dce_translation_3.png)

1. HTML 블록을 선택합니다.
1. 오른쪽의 매개 변수 블록에서 이 **[!UICONTROL Localization]** 옵션을 사용하여 선택한 블록의 컨텐츠를 플래그를 지정할 수 있습니다. 기본적으로 페이지 제목만 번역됩니다.

   ![](assets/dce_translation_1.png)

   >[!NOTE]
   >
   >문자열은 1023자를 초과할 수 없습니다.

   세 가지 구체적인 사례가 있습니다.

   * 선택한 블록에 여러 문자열/블록이 포함되어 있으면 번역될 단일 문자열로 플래그가 지정됩니다. 이 문자열에는 이 블록 내의 요소의 HTML 코드가 포함됩니다.
   * 여러 문자열이 포함된 블록에 플래그를 지정하고 이러한 문자열 중 적어도 하나가 이미 플래그가 지정된 경우 경고가 표시됩니다. 그런 다음 분리된 문자열에서 플래그를 제거하고 전체 블록을 추가할 수 있습니다.

      ![](assets/dce_translation_4.png)

   * 이미 플래그가 지정된 블록의 문자열에서 플래그를 제거하려는 경우 문자열 변환 옵션을 직접 수정할 수 없습니다. 하지만 문자열을 변경하기 위해 문자열이 포함된 블록에 액세스할 수 있습니다.

      ![](assets/dce_translation_2.png)

1. 문자열 플래그를 완료한 후 웹 애플리케이션으로 돌아가서 **[!UICONTROL Translations]** 탭을 선택합니다.
1. 을 **[!UICONTROL Collect the strings to translate]**&#x200B;선택합니다. DCE에서 플래그 지정된 문자열이 웹 애플리케이션의 문자열에 추가됩니다.

   >[!NOTE]
   >
   >DCE에서 번역 플래그를 제거하면 문자열이 수집되면 목록에서 제거되지 않습니다. 이를 통해 번역 메모리에 보관할 수 있습니다.

1. 문자열을 번역 및 승인합니다.

   그런 다음 웹 애플리케이션의 **[!UICONTROL Preview]** 탭에서 원하는 언어를 선택하여 번역을 미리 볼 수 있습니다.

