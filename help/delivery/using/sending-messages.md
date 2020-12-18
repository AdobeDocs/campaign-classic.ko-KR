---
solution: Campaign Classic
product: campaign
title: Adobe Campaign Classic으로 이메일 보내기
description: 이메일 전달 매개 변수에 대한 자세한 내용
audience: delivery
content-type: reference
topic-tags: sending-emails
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 8%

---


# 이메일 보내기{#sending-an-email}

이메일을 승인하고 만드는 배달물의 수신자에게 보내려면 **[!UICONTROL Send]**&#x200B;을 클릭합니다.

게재의 유효성을 확인하고 전송할 때의 자세한 프로세스는 아래 섹션에 있습니다.

* [게재 유효성 검사](../../delivery/using/steps-validating-the-delivery.md)
* [게재 보내기](../../delivery/using/steps-sending-the-delivery.md)

아래 섹션에서는 이메일 전달과 관련된 매개 변수에 대해 자세히 설명합니다.

## 이메일 숨은 참조 {#archiving-emails}

Adobe Campaign을 사용하면 숨겨진 참조 이메일 주소를 메시지 대상에 추가하면 BCC를 통해 외부 시스템에 이메일을 저장할 수 있습니다. 이 옵션이 활성화되면 이 배달을 위해 보낸 모든 메시지의 정확한 사본이 유지됩니다.

이메일 BCC 구성 및 우수 사례에 대한 자세한 내용은 [이 섹션](../../installation/using/email-archiving.md)을 참조하십시오.

>[!NOTE]
>
>이메일 BCC는 선택적 기능입니다. 라이선스 계약을 확인하고 계정 관리자에게 문의하여 기능을 활성화하십시오.

새 배달 또는 배달 템플릿을 만들 때, 기본적으로 이메일 BCC가 활성화되지 않습니다. 이메일 배달 또는 배달 템플릿 수준에서 수동으로 활성화해야 합니다.

이메일 배달 템플릿에 대한 이메일 BCC를 활성화하려면 아래 단계를 수행하십시오.

1. **[!UICONTROL Campaign Management]** > **[!UICONTROL Deliveries]** 또는 **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Delivery templates]**&#x200B;로 이동합니다.
1. 원하는 배달을 선택하거나 기본 **이메일 배달** 템플릿을 복제한 다음, 중복된 템플릿을 선택합니다.
1. **속성** 단추를 클릭합니다.
1. **[!UICONTROL Delivery]** 탭을 선택합니다. 
1. **이메일 BCC** 옵션을 선택합니다. 이 템플릿을 기준으로 각 배달에 대해 보낸 모든 메시지 사본이 구성된 이메일 BCC 주소로 전송됩니다.

   ![](assets/s_ncs_user_wizard_archiving.png)

   >[!NOTE]
   >
   >BCC 주소로 보낸 이메일을 열고 클릭하는 경우, 전송 분석의 **[!UICONTROL Total opens]** 및 **[!UICONTROL Clicks]**&#x200B;에 있는 사항을 고려하여 일부 계산 오류가 발생할 수 있습니다.

## 미러 페이지 {#generating-the-mirror-page} 생성

미러 페이지는 웹 브라우저를 통해 온라인으로 액세스할 수 있는 HTML 페이지입니다. 컨텐츠는 이메일과 동일합니다.

기본적으로 링크가 메일 컨텐츠에 삽입되는 경우 미러 페이지가 생성됩니다. 개인화 블록 삽입에 대한 자세한 내용은 [개인화 블록](../../delivery/using/personalization-blocks.md)을 참조하십시오.

배달 속성에서 **[!UICONTROL Validity]** 탭의 **[!UICONTROL Mode]** 필드를 사용하여 이 페이지의 생성 모드를 수정할 수 있습니다.

![](assets/s_ncs_user_wizard_miror_page_mode.png)

>[!CAUTION]
>
>미러 페이지를 생성하기 위해 HTML 컨텐츠를 정의해야 합니다.

기본 모드 외에 다음 옵션도 사용할 수 있습니다.

* **[!UICONTROL Force the generation of the mirror page]** :게재에 미러 페이지에 대한 링크가 삽입되지 않아도 미러 페이지가 생성됩니다.
* **[!UICONTROL Do not generate the mirror page]** :배달에 링크가 있어도 미러 페이지가 생성되지 않습니다.
* **[!UICONTROL Generates a mirror page accessible using only the message identifier]** :이 옵션을 사용하면 배달 로그 창에서 개인화 정보를 사용하여 미러 페이지의 컨텐츠에 액세스할 수 있습니다. 이렇게 하려면 배달 종료 후 **[!UICONTROL Delivery]** 탭을 클릭하고 미러 페이지를 보려는 수신자 라인을 선택합니다. **[!UICONTROL Display the mirror page for this message...]** 링크를 클릭합니다.

   ![](assets/s_ncs_user_wizard_miror_page_link.png)

## 바운스 이메일 관리 {#managing-bounce-emails}

배달 매개 변수의 **[!UICONTROL SMTP]** 탭에서는 바운스 메일의 관리를 구성할 수 있습니다.

![](assets/s_ncs_user_email_del_properties_smtp_tab.png)

기본적으로 바운스된 이메일은 플랫폼의 기본 오류 상자에 표시되지만 배달에 대한 특정 오류 주소를 정의할 수 있습니다.

응용 프로그램에서 자동으로 자격을 부여할 수 없는 바운스 메일의 이유를 조사하기 위해 이 화면에서 특정 주소를 정의할 수도 있습니다. 이러한 각 필드에 대해 &#39;개인화된 필드 추가&#39; 아이콘을 사용하여 개인화 매개 변수를 추가할 수 있습니다.

## 문자 인코딩 {#character-encoding}

배달 매개 변수의 **[!UICONTROL SMTP]** 탭에서 **[!UICONTROL Character encoding]** 섹션을 사용하여 특정 인코딩을 설정할 수 있습니다.

기본 인코딩은 UTF-8입니다. 일부 받는 사람의 이메일 공급자가 UTF-8 표준 인코딩을 지원하지 않는 경우 이메일 수신자에게 특수 문자를 제대로 표시하도록 특정 인코딩을 설정할 수 있습니다.

예를 들어 일본어 문자가 포함된 이메일을 보낼 수 있습니다. 일본에서 모든 문자가 수신자에게 올바르게 표시되도록 하려면 표준 UTF-8이 아닌 일본어 문자를 지원하는 인코딩을 사용해야 합니다.

이렇게 하려면 **[!UICONTROL Character encoding]** 섹션에서 **[!UICONTROL Force the encoding used for messages]** 옵션을 선택하고 표시되는 드롭다운 목록에서 인코딩을 선택합니다.

![](assets/s_ncs_user_email_del_properties_smtp_tab_encoding.png)

## SMTP 헤더 추가 중 {#adding-smtp-headers}

SMTP 헤더를 배달에 추가할 수 있습니다. 이렇게 하려면 배달에서 **[!UICONTROL SMTP]** 탭의 관련 섹션을 사용하십시오.

이 창에 입력된 스크립트는 다음 양식에서 라인당 하나의 헤더를 참조해야 합니다.**name:value**.

필요한 경우 값이 자동으로 인코딩됩니다.

>[!CAUTION]
>
>추가 SMTP 헤더 삽입을 위한 스크립트 추가는 고급 사용자를 위해 예약되어 있습니다.
>
>이 스크립트의 구문은 다음과 같은 이 콘텐츠 형식의 요구 사항을 준수해야 합니다: 사용하지 않은 공간, 빈 줄 등이 없음.
