---
solution: Campaign Classic
product: campaign
title: Adobe Campaign Classic을 사용하여 일본어 모바일에 이메일 보내기
description: 일본어 모바일에서 읽을 이메일을 구성, 디자인 및 전송하는 방법을 알아봅니다.
audience: delivery
content-type: reference
topic-tags: sending-emails
translation-type: tm+mt
source-git-commit: fe4262a1da011cb155651c5e786f19188139cff1
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---


# 일본어 모바일에 이메일 보내기 {#sending-emails-on-japanese-mobiles}

## 일본어 모바일 {#email-formats-for-japanese-mobiles} 전자 메일 형식

Adobe Campaign은 모바일에서 e-메일을 위한 3가지 특정 일본어 형식을 관리합니다.**데코메일**(DoCoMo mobiles), **데코어 메일**(Softbank 모바일) 및 **데코레이션 메일**(KDDI AU 모바일). 이러한 형식은 특정 코딩, 구조 및 크기 제한을 적용합니다. [이 섹션](#limitations-and-recommendations)에서 제한 사항 및 권장 사항에 대해 자세히 알아보십시오.

받는 사람이 이러한 형식 중 하나의 메시지를 제대로 수신하려면 해당 프로필에서 **[!UICONTROL Deco-mail (DoCoMo)]**, **[!UICONTROL Decore Mail (Softbank)]** 또는 **[!UICONTROL Decoration Mail (KDDI AU)]**&#x200B;를 선택하는 것이 좋습니다.

![](assets/deco-mail_03.png)

그러나 **[!UICONTROL Email format]** 옵션을 **[!UICONTROL Unknown]**, **[!UICONTROL HTML]** 또는 **[!UICONTROL Text]**&#x200B;으로 두면 Adobe Campaign은 메시지가 올바르게 표시되도록 사용할 일본어 형식을 자동으로 감지합니다(이메일을 보낼 때).

이 자동 감지 시스템은 **[!UICONTROL Management of Email Formats]** 메일 규칙 집합에 정의된 사전 정의된 도메인 목록을 기반으로 합니다. 이메일 형식 관리에 대한 자세한 내용은 [이 페이지](../../installation/using/email-deliverability.md#managing-email-formats)를 참조하십시오.

## 제한 사항 및 권장 사항 {#limitations-and-recommendations}

일본 업체(Softbank, DoCoMo, KDDI AU)가 운영하는 모바일에서 읽을 이메일 전송에는 특정한 수의 제한이 적용됩니다.

따라서 다음을 수행해야 합니다.

* JPEG 또는 GIF 형식의 이미지만 사용
* 10,000바이트보다 훨씬 낮은 텍스트 및 HTML 섹션이 포함된 배달 만들기(KDDI AU 및 DoCoMo의 경우)
* 100KB 미만의 전체 크기(인코딩 전)의 이미지 사용
* 메시지당 20개 이상의 이미지 사용 안 함
* 축소된 크기 HTML 형식 사용(각 연산자에 대해 제한된 태그 수 사용 가능)

>[!NOTE]
>
>메시지를 만들 때 각 연산자에 대한 제한 사항을 고려해야 합니다. 참조:
>
>* DoCoMo의 경우 [이 페이지](https://www.nttdocomo.co.jp/service/developer/make/content/deco_mail/index.html)를 참조하십시오.
>* KDDI AU의 경우 [이 페이지](https://www.au.com/ezfactory/tec/spec/decorations/template.html)를 참조하십시오.
>* Softbank의 경우 [이 페이지](https://www.support.softbankmobile.co.jp/partner/home_tech3/index.cfm)를 참조하십시오.


## 이메일 컨텐츠 테스트 {#testing-the-email-content}

### 메시지 {#previewing-the-message} 미리 보기

Adobe Campaign을 사용하면 메시지 형식이 일본어 모바일 형식으로 전송되도록 채택되었는지 확인할 수 있습니다.

컨텐츠를 정의하고 이메일 제목을 입력한 후 메시지가 작성되면 표시 및 서식을 확인할 수 있습니다.

내용 편집 창의 **[!UICONTROL Preview]** 탭에서 **[!UICONTROL More... > Deco-mail diagnostic]**&#x200B;을 클릭하면 다음 작업을 수행할 수 있습니다.

* HTML 컨텐츠 태그가 일본어 형식 제한에 부합하는지 확인
* 메시지의 이미지 수가 형식(20개 이미지)으로 지정한 제한을 초과하지 않는지 확인합니다.
* 총 메시지 크기 확인(100kB 미만)

   ![](assets/deco-mail_06.png)

### 유형 규칙 {#running-typology-rule} 실행

증명 또는 배달을 보낼 때 미리 보기 진단 외에 두 번째 검사가 수행됩니다.분석 중에 특정 유형 규칙 **[!UICONTROL Deco-mail check]**&#x200B;이 시작됩니다.

>[!IMPORTANT]
>
>이 유형 규칙은 받는 사람 중 적어도 하나가 **[!UICONTROL Deco-mail (DoCoMo)]**, **[!UICONTROL Decore Mail (Softbank)]** 또는 **[!UICONTROL Decoration Mail (KDDI AU)]** 형식으로 이메일을 수신하도록 구성된 경우에만 실행됩니다.

이 분류 규칙을 사용하면 이메일의 전체 크기, HTML 및 텍스트 섹션의 크기, 메시지의 이미지 수, HTML 컨텐츠의 태그와 관련하여, 특히 일본 연산자가 정의한 [형식 제약 조건](#limitations-and-recommendations)을 배달을 준수하도록 할 수 있습니다.

### 증명 보내기 {#sending-proofs}

교정본을 보내 배달 테스트를 수행할 수 있습니다. 증명 자료를 보낼 때 대체 주소를 사용하는 경우 사용되는 프로필의 이메일 형식에 해당하는 주소를 입력하십시오.

예를 들어 이 프로필의 이메일 형식이 **[!UICONTROL Decore Mail (Softbank)]**&#x200B;에 미리 정의된 경우 프로필 주소를 test@softbank.ne.jp으로 바꿀 수 있습니다.

![](assets/deco-mail_05.png)

## 메시지 보내기 {#sending-messages}

Adobe Campaign을 사용하여 일본어 이메일 형식의 수신자에게 이메일을 보내려면 다음 두 가지 옵션을 사용할 수 있습니다.

* 다음 두 가지 배달 만들기:하나는 일본어 수신자에게만 해당되며 다른 수신자는 이 섹션](#designing-a-specific-delivery-for-japanese-formats)을 참조하십시오.[
* 단일 배달을 만들면 Adobe Campaign에서 사용할 형식을 자동으로 검색합니다. 자세한 내용은 [이 섹션](#designing-a-delivery-for-all-formats)을 참조하십시오.

### 일본어 형식 {#designing-a-specific-delivery-for-japanese-formats}에 대한 특정 배달 디자인

다음 두 가지 제공을 포함하는 워크플로우를 만들 수 있습니다.일본어 모바일 및 표준 이메일 포맷을 사용하는 수신자를 위한 컨텐츠를 제공합니다.

이렇게 하려면 워크플로우에서 **[!UICONTROL Split]** 활동을 사용하고 일본어 이메일 형식(장식 메일, 데코레이션 메일 및 데코어 메일)을 필터링 조건으로 정의합니다.

![](assets/deco-mail_08.png)

![](assets/deco-mail_07.png)

### 모든 형식 {#designing-a-delivery-for-all-formats}에 대한 배달 디자인

Adobe Campaign이 도메인(a0/>, **[!UICONTROL HTML]** 또는 **[!UICONTROL Text]**&#x200B;로 정의된 이메일 형식의 프로파일을 포함한 프로파일)에 따라 형식을 동적으로 관리하는 경우 모든 받는 사람에게 동일한 배달을 보낼 수 있습니다.**[!UICONTROL Unknown]**

표준 수신자의 경우와 마찬가지로 일본어 모바일에 있는 사용자에 대해 메시지 연락처가 올바르게 표시됩니다.

>[!IMPORTANT]
>
>각 일본어 이메일 형식(장식 이메일, 데코레이션 메일 및 데코어 메일)과 관련된 특수 기능을 사용해야 합니다. 제한에 대한 자세한 내용은 [이 섹션](#limitations-and-recommendations)을 참조하십시오.
