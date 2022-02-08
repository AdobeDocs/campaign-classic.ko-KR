---
product: campaign
title: 전자 메일 매개 변수
description: 이메일 게재와 관련된 옵션 및 설정에 대해 알아봅니다
exl-id: 1bb36e71-9f1a-4553-b266-eca3f48688e2
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '900'
ht-degree: 8%

---

# 이메일 매개 변수 {#email-parameters}

![](../../assets/common.svg)

이 섹션에서는 전자 메일 게재와 관련된 옵션 및 매개 변수를 제공합니다.

## 이메일 BCC {#email-bcc}

Adobe Campaign을 사용하면 메시지 타겟에 숨은 참조 이메일 주소를 추가하면 BCC를 통해 외부 시스템에 이메일을 저장할 수 있습니다.

옵션이 활성화되면 이 게재에 대해 전송된 모든 메시지의 정확한 복사본이 유지됩니다.

이메일 BCC 구성 및 모범 사례에 대한 자세한 내용은 [이 섹션](../../installation/using/email-archiving.md).

>[!NOTE]
>
>이메일 BCC는 선택적 기능입니다. 라이선스 계약을 확인하고 계정 관리자에게 문의하여 기능을 활성화하십시오.

새 게재 또는 게재 템플릿을 만들 때 기본적으로 이메일 BCC가 활성화되지 않습니다. 이메일 게재 또는 게재 템플릿 수준에서 수동으로 활성화해야 합니다.

>[!NOTE]
>
>향상된 MTA로 이메일 BCC를 사용하는 경우 이 옵션은 모든 게재에 대해 자동으로 활성화됩니다.

전자 메일 게재 템플릿에 대한 전자 메일 BCC를 활성화하려면 아래 단계를 수행하십시오.

1. 이동 **[!UICONTROL Campaign Management]** > **[!UICONTROL Deliveries]** 또는 **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Delivery templates]**.
1. 원하는 게재를 선택하거나 기본 제공 게재를 복제합니다 **이메일 게재** 템플릿을 선택한 다음 복제한 템플릿을 선택합니다.
1. 을(를) 클릭합니다. **속성** 버튼을 클릭합니다.
1. **[!UICONTROL Delivery]** 탭을 선택합니다. 
1. 을(를) 확인합니다. **이메일 BCC** 선택 사항입니다. 이 템플릿을 기반으로 하는 각 게재에 대해 전송된 모든 메시지의 사본은 구성된 이메일 숨은 참조 주소로 전송됩니다.

   ![](assets/s_ncs_user_wizard_archiving.png)

>[!NOTE]
>
>BCC 주소로 전송된 이메일을 열고 클릭스루하는 경우 **[!UICONTROL Total opens]** 및 **[!UICONTROL Clicks]** send analysis에서 계산되지 않을 수 있습니다.

## 메시지 형식 선택 {#selecting-message-formats}

전송된 이메일 메시지 형식을 변경할 수 있습니다. 이렇게 하려면 게재 속성을 편집하고 **[!UICONTROL Delivery]** 탭.

![](assets/s_ncs_user_wizard_email_param.png)

창의 아래 섹션에서 전자 메일 형식을 선택합니다.

* **[!UICONTROL Use recipient preferences]** (기본 모드)

   메시지 형식은 수신자 프로필에 저장된 데이터에 따라 정의되며 기본적으로 **[!UICONTROL email format]** 필드(@emailFormat). 수신자가 특정 형식으로 메시지를 수신하려는 경우에 보내는 형식입니다. 필드를 입력하지 않은 경우 다중 부분 대체 메시지가 전송됩니다(아래 참조).

* **[!UICONTROL Let recipient mail client choose the most appropriate format]**

   메시지에 다음 두 형식이 포함됩니다. 텍스트 및 HTML. 수신에 표시되는 형식은 수신자의 메일 소프트웨어(다중 파트 대체)의 구성에 따라 달라집니다.

   >[!IMPORTANT]
   >
   >이 옵션에는 문서의 두 버전이 모두 포함됩니다. 따라서 메시지 크기가 더 크기 때문에 게재 속도에 영향을 줍니다.

* **[!UICONTROL Send all messages in text format]**

   메시지는 텍스트 형식으로 전송됩니다. HTML 형식은 전송되지 않지만 수신자가 메시지를 클릭할 때만 미러 페이지에 사용됩니다.

>[!NOTE]
>
>전자 메일 콘텐츠 정의에 대한 자세한 내용은 [이 섹션](defining-the-email-content.md).

## 미러 페이지 생성 {#generating-mirror-page}

미러 페이지는 웹 브라우저를 통해 온라인으로 액세스할 수 있는 HTML 페이지입니다. 콘텐츠는 이메일과 동일합니다.

기본적으로 링크가 메일 콘텐츠에 삽입되면 미러 페이지가 생성됩니다. 개인화 블록 삽입에 대한 자세한 내용은 [개인화 블록](personalization-blocks.md).

게재 속성에서 **[!UICONTROL Mode]** 필드 **[!UICONTROL Validity]** 탭에서는 이 페이지의 생성 모드를 수정할 수 있습니다.

![](assets/s_ncs_user_wizard_miror_page_mode.png)

>[!IMPORTANT]
>
>미러 페이지를 만들 수 있도록 HTML 컨텐츠를 정의해야 합니다.

기본 모드 외에 다음 옵션도 사용할 수 있습니다.

* **[!UICONTROL Force the generation of the mirror page]**: 게재에 미러 페이지에 대한 링크가 삽입되지 않더라도 미러 페이지가 생성됩니다.
* **[!UICONTROL Do not generate the mirror page]**: 링크가 게재에 있어도 미러 페이지가 생성되지 않습니다.
* **[!UICONTROL Generates a mirror page accessible using only the message identifier]**: 이 옵션을 사용하면 게재 로그 창에서 개인화 정보를 사용하여 미러 페이지의 콘텐츠에 액세스할 수 있습니다. 이렇게 하려면 게재 종료 후 **[!UICONTROL Delivery]** 탭을 선택하고 미러 페이지를 보려는 수신자 줄을 선택합니다. **[!UICONTROL Display the mirror page for this message...]** 링크를 클릭합니다.

   ![](assets/s_ncs_user_wizard_miror_page_link.png)

## 문자 인코딩 {#character-encoding}

에서 **[!UICONTROL SMTP]** 게재 매개 변수의 탭, **[!UICONTROL Character encoding]** 섹션에서 특정 인코딩을 설정할 수 있습니다.

기본 인코딩은 UTF-8입니다. 일부 수신자의 전자 메일 공급자가 UTF-8 표준 인코딩을 지원하지 않는 경우 전자 메일 수신자에게 특수 문자를 적절히 표시하도록 특정 인코딩을 설정할 수 있습니다.

예를 들어 일본어 문자가 포함된 이메일을 보내려고 합니다. 일본에서 모든 문자가 수신자에게 올바르게 표시되도록 하려면 표준 UTF-8이 아닌 일본어 문자를 지원하는 인코딩을 사용할 수 있습니다.

이렇게 하려면 **[!UICONTROL Force the encoding used for messages]** 옵션 **[!UICONTROL Character encoding]** 섹션을 선택하고 표시되는 드롭다운 목록에서 인코딩을 선택합니다.

![](assets/s_ncs_user_email_del_properties_smtp_tab_encoding.png)

## 바운스 이메일 관리 {#managing-bounce-emails}

다음 **[!UICONTROL SMTP]** 게재 매개 변수의 탭을 사용하여 바운스 메일 관리를 구성할 수 있습니다.

기본적으로 바운스된 이메일은 플랫폼의 기본 오류 상자에 수신되지만 배달에 대한 특정 오류 주소를 정의할 수 있습니다.

이 화면에서 특정 주소를 정의하여 애플리케이션에서 자동으로 자격을 부여할 수 없는 경우 바운스 메일의 이유를 조사할 수도 있습니다. 이러한 각 필드에 대해 **개인화된 필드 추가** 아이콘을 사용하면 개인화 매개 변수를 추가할 수 있습니다.

![](assets/s_ncs_user_email_del_properties_smtp_tab.png)

바운스 메일 관리에 대한 자세한 내용은 [이 섹션](understanding-delivery-failures.md#bounce-mail-management).

## SMTP 헤더 추가 {#adding-smtp-headers}

게재에 SMTP 헤더를 추가할 수 있습니다. 이렇게 하려면 **[!UICONTROL SMTP]** 탭에서 사용할 수 있습니다.

이 창에 입력한 스크립트는 다음 양식에서 라인당 하나의 헤더를 참조해야 합니다. **name:value**.

필요한 경우 값이 자동으로 인코딩됩니다.

>[!IMPORTANT]
>
>추가 SMTP 헤더 삽입을 위한 스크립트 추가는 고급 사용자를 위해 예약되어 있습니다.
>
>이 스크립트의 구문은 다음과 같은 이 콘텐츠 형식의 요구 사항을 준수해야 합니다: 사용하지 않은 공간, 빈 줄 등이 없음.
