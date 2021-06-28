---
product: campaign
title: 웹 애플리케이션 번역
description: 웹 애플리케이션 번역
audience: web
content-type: reference
topic-tags: web-applications
exl-id: 82c5c610-8161-4686-aa79-1b690e763765
source-git-commit: 360fd1ed8970c17c0687eaca0a4c1960d6f5838c
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 5%

---

# 웹 애플리케이션 번역{#translating-a-web-application}

Adobe Campaign DCE(디지털 콘텐츠 편집기)로 만든 웹 애플리케이션 페이지를 번역할 수 있습니다.

웹 애플리케이션의 **[!UICONTROL Properties]**&#x200B;에서 **[!UICONTROL Localization]** 탭을 통해 하나 이상의 추가 언어를 선택하는 경우, DCE로 편집된 페이지에서 HTML 콘텐츠 블록을 추가할 때 새로운 옵션을 사용할 수 있습니다.

이 옵션을 사용하면 블록 컨텐츠를 번역해야 하는지 여부를 나타낼 수 있습니다.

변환할 문자열은 응용 프로그램의 **[!UICONTROL Translations]** 탭을 통해 웹 응용 프로그램의 다른 문자열과 동일한 방법으로 수집됩니다. 자세한 정보는 이 [페이지](translating-a-web-form.md)를 참조하십시오.

변환할 문자열에 플래그를 지정하려면 다음을 수행하십시오.

1. 웹 애플리케이션에서 DCE로 편집한 컨텐츠 페이지를 엽니다.

   ![](assets/dce_translation_3.png)

1. HTML 블록을 선택합니다.
1. 오른쪽의 매개 변수 블록에서 **[!UICONTROL Localization]** 옵션을 사용하여 선택한 블록의 컨텐츠에 플래그를 지정할 수 있습니다. 기본적으로 페이지 제목만 번역됩니다.

   ![](assets/dce_translation_1.png)

   >[!NOTE]
   >
   >문자열은 1023자를 초과할 수 없습니다.

   다음과 같은 세 가지 구체적인 사례가 있습니다.

   * 선택한 블록에 여러 개의 문자열/블록이 포함되어 있으면 번역할 단일 문자열로 플래그가 지정됩니다. 이 문자열에는 가 들어 있고, 이 문자열에는 가 들어 있습니다.
   * 여러 문자열이 포함된 블록에 플래그를 지정하고 이러한 문자열 중 적어도 하나가 이미 플래그가 지정된 경우 경고가 표시됩니다. 그런 다음 분리된 문자열에서 플래그를 제거하고 전체 블록을 추가할 수 있습니다.

      ![](assets/dce_translation_4.png)

   * 이미 플래그가 지정된 블록에 포함된 문자열에서 플래그를 제거하려면 문자열 변환 옵션을 직접 수정할 수 없습니다. 하지만 문자열을 포함하는 블록에 액세스하여 변경할 수 있습니다.

      ![](assets/dce_translation_2.png)

1. 문자열 플래그 지정을 마쳤으면 웹 애플리케이션으로 돌아가서 **[!UICONTROL Translations]** 탭을 선택합니다.
1. **[!UICONTROL Collect the strings to translate]**&#x200B;을(를) 선택합니다. DCE에 플래그가 지정된 문자열이 웹 애플리케이션의 문자열에 추가됩니다.

   >[!NOTE]
   >
   >문자열이 수집되면 DCE에서 번역 플래그를 제거하면 목록에서 제거되지 않습니다. 이를 통해 번역 메모리에 보관할 수 있습니다.

1. 문자열을 번역하고 승인합니다.

   그런 다음 웹 애플리케이션의 **[!UICONTROL Preview]** 탭에서 원하는 언어를 선택하여 번역을 미리 볼 수 있습니다.
