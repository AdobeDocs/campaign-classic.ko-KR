---
product: campaign
title: Adobe Campaign Classic을 사용하여 일본의 모바일에 전자 메일 보내기
description: 일본어 모바일에서 읽을 이메일을 구성, 디자인 및 보내는 방법을 알아봅니다.
audience: delivery
content-type: reference
topic-tags: sending-emails
exl-id: 44634227-2340-49c4-b330-740c739ea551
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---

# 일본의 모바일에 전자 메일 보내기 {#sending-emails-on-japanese-mobiles}

## 일본의 모바일에 대한 이메일 형식 {#email-formats-for-japanese-mobiles}

Adobe Campaign은 모바일에서 전자 메일에 대한 세 가지 특정 일본어 형식을 관리합니다.**Deco-mail** (DoCoMo mobiles), **Decore Mail**(Softbove) 및 **데코레이션 메일** (KDDI AU 모바일). 이러한 형식에는 특정 코딩, 구조 및 크기 제한이 적용됩니다. [이 섹션](#limitations-and-recommendations)의 제한 사항과 권장 사항에 대해 자세히 알아보십시오.

수신자가 이러한 형식 중 하나에서 메시지를 올바르게 수신하려면 해당 프로필에서 **[!UICONTROL Deco-mail (DoCoMo)]**, **[!UICONTROL Decore Mail (Softbank)]** 또는 **[!UICONTROL Decoration Mail (KDDI AU)]**&#x200B;를 선택하는 것이 좋습니다.

![](assets/deco-mail_03.png)

그러나 **[!UICONTROL Email format]** 옵션을 **[!UICONTROL Unknown]**, **[!UICONTROL HTML]** 또는 **[!UICONTROL Text]**&#x200B;로 두면 Adobe Campaign은 메시지가 올바르게 표시되도록 사용할 일본어 형식을 자동으로 감지합니다(이메일을 보낼 때).

이 자동 감지 시스템은 **[!UICONTROL Management of Email Formats]** 메일 규칙 세트에 정의된 사전 정의된 도메인 목록을 기반으로 합니다. 전자 메일 형식 관리에 대한 자세한 내용은 [이 페이지](../../installation/using/email-deliverability.md#managing-email-formats)를 참조하십시오.

## 제한 사항 및 권장 사항 {#limitations-and-recommendations}

일본 업체(소프트뱅크, DoCoMo, KDDI AU)가 운영하는 모바일에서 읽게 될 전자 메일 보내기에 특정한 수의 제한이 적용됩니다.

따라서 다음을 수행해야 합니다.

* JPEG 또는 GIF 형식의 이미지만 사용합니다
* 10,000바이트보다 절대적으로 낮은 텍스트 및 HTML 섹션으로 게재를 만듭니다(KDDI AU 및 DoCoMo의 경우)
* 100KB보다 작은 총 크기(인코딩 전)의 이미지를 사용합니다
* 메시지당 20개 이상의 이미지를 사용하지 마십시오
* 축소된 크기 HTML 형식을 사용합니다(각 연산자에 대해 제한된 수의 태그를 사용할 수 있음)

>[!NOTE]
>
>메시지를 만들 때 각 연산자와 관련된 제한 사항을 고려해야 합니다. 다음을 참조하십시오.
>
>* DoCoMo에 대해서는 [이 페이지](https://www.nttdocomo.co.jp/service/developer/make/content/deco_mail/index.html)를 참조하십시오
>* KDDI AU의 경우 이 페이지](https://www.au.com/ezfactory/tec/spec/decorations/template.html)를 참조하십시오.[
>* Softbank의 경우 [이 페이지](https://www.support.softbankmobile.co.jp/partner/home_tech3/index.cfm)를 참조하십시오


## 전자 메일 콘텐츠 테스트 {#testing-the-email-content}

### 메시지 미리 보기 {#previewing-the-message}

Adobe Campaign에서 메시지 형식이 일본어 모바일로 전송되도록 조정되었는지 확인할 수 있습니다.

콘텐츠를 정의하고 전자 메일 제목을 입력한 후 메시지를 만들 때 표시 및 서식을 확인할 수 있습니다.

컨텐츠 편집 창의 **[!UICONTROL Preview]** 탭에서 **[!UICONTROL More... > Deco-mail diagnostic]**&#x200B;을 클릭하면 다음 작업을 수행할 수 있습니다.

* HTML 콘텐츠 태그가 일본어 형식 제한을 준수하는지 확인합니다
* 메시지의 이미지 수가 형식(20개 이미지)에서 지정한 제한을 초과하지 않는지 확인합니다
* 총 메시지 크기 확인(100kB 미만)

   ![](assets/deco-mail_06.png)

### 유형화 규칙 {#running-typology-rule} 실행

증명 또는 게재를 보낼 때 미리 보기 진단 외에 두 번째 검사가 수행됩니다.분석 중에 특정 유형화 규칙 **[!UICONTROL Deco-mail check]**&#x200B;이 시작됩니다.

>[!IMPORTANT]
>
>이 유형화 규칙은 수신자 중 하나 이상이 **[!UICONTROL Deco-mail (DoCoMo)]**, **[!UICONTROL Decore Mail (Softbank)]** 또는 **[!UICONTROL Decoration Mail (KDDI AU)]** 형식으로 이메일을 수신하도록 구성된 경우에만 실행됩니다.

이 유형화 규칙을 사용하면 게재가 특히 전자 메일의 총 크기, HTML 및 텍스트 섹션의 크기, 메시지의 이미지 수 및 HTML 콘텐츠의 태그와 관련하여 일본 연산자가 정의한 [형식 제한](#limitations-and-recommendations)을 따르는지 확인할 수 있습니다.

### 증명 보내기 {#sending-proofs}

증명을 전송하여 게재를 테스트할 수 있습니다. 증명을 보낼 때 대체 주소를 사용하는 경우 사용되는 프로필의 이메일 형식에 해당하는 주소를 입력하십시오.

예를 들어, 이 프로필에 대한 이메일 형식이 **[!UICONTROL Decore Mail (Softbank)]**&#x200B;에 미리 정의된 경우 test@softbank.ne.jp으로 프로필 주소를 바꿀 수 있습니다.

![](assets/deco-mail_05.png)

## 메시지 보내기 {#sending-messages}

Campaign을 사용하여 일본어 전자 메일 형식을 사용하여 수신자에게 전자 메일을 보내려면 다음 두 가지 옵션을 사용할 수 있습니다.

* 두 개의 게재 만들기:일본어 수신자와 다른 수신자에 대한 한 가지 정보는 [이 섹션](#designing-a-specific-delivery-for-japanese-formats)을 참조하십시오.
* 단일 게재를 만들면 Adobe Campaign에서 사용할 형식을 자동으로 감지합니다. [이 섹션](#designing-a-delivery-for-all-formats)을 참조하십시오.

### 일본어 형식 {#designing-a-specific-delivery-for-japanese-formats}에 대한 특정 게재 디자인

다음 두 개의 게재가 포함된 워크플로우를 만들 수 있습니다.하나는 일본어 모바일에서 읽고 다른 하나는 표준 이메일 형식을 사용하는 수신자를 위해 읽어야 합니다.

이렇게 하려면 워크플로우에서 **[!UICONTROL Split]** 활동을 사용하고 일본어 전자 메일 형식(데코레이션 메일, 데코레이션 메일 및 데코어 메일)을 필터링 조건으로 정의합니다.

![](assets/deco-mail_08.png)

![](assets/deco-mail_07.png)

### 모든 형식에 대한 게재 디자인 {#designing-a-delivery-for-all-formats}

Adobe Campaign이 도메인에 따라 형식(전자 메일 형식이 **[!UICONTROL Unknown]**, **[!UICONTROL HTML]** 또는 **[!UICONTROL Text]** )을 동적으로 관리하는 경우 모든 수신자에게 동일한 게재를 보낼 수 있습니다.

표준 수신자와 마찬가지로 일본의 모바일에 있는 사용자에 대해 메시지 연락처가 올바르게 표시됩니다.

>[!IMPORTANT]
>
>각 일본어 이메일 형식(데코어 메일, 데코레이션 메일 및 데코어 메일)과 연관된 특수 기능을 고려해야 합니다. 제한 사항에 대한 자세한 내용은 [이 섹션](#limitations-and-recommendations)을 참조하십시오.
