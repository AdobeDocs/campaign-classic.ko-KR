---
product: campaign
title: Adobe Campaign Classic으로 일본어 모바일에서 이메일 보내기
description: 일본어 모바일에서 읽을 이메일을 구성, 디자인 및 전송하는 방법에 대해 알아봅니다
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Email, Email Design
role: User
exl-id: 44634227-2340-49c4-b330-740c739ea551
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 0%

---

# 일본어 모바일에서 이메일 보내기 {#sending-emails-on-japanese-mobiles}

## 일본어 모바일의 이메일 형식 {#email-formats-for-japanese-mobiles}

Adobe Campaign은 모바일에서 이메일에 대한 세 가지 특정 일본어 형식을 관리합니다. **데코메일** (DoCoMo 모바일), **메일 디코어** (Softbank 모바일) 및 **데코레이션 메일** (KDDI AU 모바일). 이러한 형식에는 특정 코딩, 구조 및 크기 제한이 적용됩니다. 에서 제한 사항 및 권장 사항에 대해 자세히 알아보십시오. [이 섹션](#limitations-and-recommendations).

수신자가 이러한 형식 중 하나로 메시지를 올바르게 수신하려면 다음을 선택하는 것이 좋습니다. **[!UICONTROL Deco-mail (DoCoMo)]**, **[!UICONTROL Decore Mail (Softbank)]** 또는 **[!UICONTROL Decoration Mail (KDDI AU)]** 해당 프로필에서:

![](assets/deco-mail_03.png)

하지만 **[!UICONTROL Email format]** 옵션 as **[!UICONTROL Unknown]**, **[!UICONTROL HTML]** 또는 **[!UICONTROL Text]**, Adobe Campaign은 메시지가 올바르게 표시되도록 사용할 일본어 형식을 자동으로 감지합니다(이메일을 보낼 때).

이 자동 탐지 시스템은 다음에 정의된 사전 정의된 도메인 목록을 기반으로 합니다 **[!UICONTROL Management of Email Formats]** 메일 규칙이 설정되었습니다. 전자 메일 형식 관리에 대한 자세한 내용은 [이 페이지](../../installation/using/email-deliverability.md#managing-email-formats).

## 제한 사항 및 권장 사항 {#limitations-and-recommendations}

일본 공급업체(Softbank, DoCoMo, KDDI AU)가 운영하는 모바일에서 읽을 이메일 전송에는 특정 수의 제한이 적용됩니다.

따라서 다음을 수행해야 합니다.

* JPEG 또는 GIF 형식의 이미지만 사용
* 10,000바이트보다 엄격히 낮은 텍스트 및 HTML 섹션으로 게재를 만듭니다(KDDI AU 및 DoCoMo의 경우).
* 총 크기(인코딩 전)가 100KB보다 작은 이미지 사용
* 메시지당 20개 이상의 이미지를 사용하지 않음
* 축소된 크기 HTML 형식 사용(각 연산자에 대해 제한된 수의 태그를 사용할 수 있음)

>[!NOTE]
>
>메시지를 만들 때는 각 연산자에 대한 제한 사항을 고려해야 합니다. 해당 제품 설명서를 참조하십시오.


## 이메일 콘텐츠 테스트 {#testing-the-email-content}

### 메시지 미리 보기 {#previewing-the-message}

Adobe Campaign을 사용하면 메시지 형식이 일본어 모바일로 전송되도록 조정되었는지 확인할 수 있습니다.

콘텐츠를 정의하고 이메일 제목을 입력하면 메시지가 만들어질 때 표시와 서식을 확인할 수 있습니다.

다음에서 **[!UICONTROL Preview]** 컨텐츠 편집 창의 탭에서 **[!UICONTROL More... > Deco-mail diagnostic]** 을 통해 다음을 수행할 수 있습니다.

* HTML 컨텐츠 태그가 일본어 형식 제한을 준수하는지 확인합니다
* 메시지의 이미지 수가 형식에 지정된 제한을 초과하지 않는지 확인합니다(이미지 20개).
* 총 메시지 크기 확인(100kB 미만)

  ![](assets/deco-mail_06.png)

### 유형화 규칙 실행 {#running-typology-rule}

미리 보기 진단 외에도 특정 유형화 규칙인 증명 또는 게재를 보낼 때 두 번째 확인이 수행됩니다. **[!UICONTROL Deco-mail check]**&#x200B;는 분석 중에 시작됩니다.

>[!IMPORTANT]
>
>이 유형화 규칙은 수신자 중 하나 이상이 이메일을 수신하도록 구성된 경우에만 실행됩니다 **[!UICONTROL Deco-mail (DoCoMo)]**, **[!UICONTROL Decore Mail (Softbank)]** 또는 **[!UICONTROL Decoration Mail (KDDI AU)]** 포맷.

이 유형화 규칙을 사용하면 게재에서 다음을 준수하는지 확인할 수 있습니다. [형식 제한](#limitations-and-recommendations) 일본어 연산자에 의해 정의됩니다. 특히 이메일의 전체 크기, HTML 및 텍스트 섹션의 크기, 메시지의 이미지 수 및 HTML 컨텐츠의 태그와 관련하여.

### 증명 보내기 {#sending-proofs}

증명을 전송하여 게재를 테스트할 수 있습니다. 증명을 보낼 때 대체 주소를 사용하고 있다면 사용한 프로필의 이메일 형식에 해당하는 주소를 입력하십시오.

예를 들어 이 프로필의 이메일 포맷이 미리 정의된 경우 프로필 주소를 test@softbank.ne.jp 로 바꿀 수 있습니다 **[!UICONTROL Decore Mail (Softbank)]**.

![](assets/deco-mail_05.png)

## 메시지 보내기 {#sending-messages}

Campaign을 사용하여 일본어 이메일 형식으로 수신자에게 이메일을 보내려면 다음 두 가지 옵션을 사용할 수 있습니다.

* 두 개의 게재 만들기: 일본어 수신자에 대한 게재 만들기와 다른 수신자에 대한 게재 만들기 - 참조 [이 섹션](#designing-a-specific-delivery-for-japanese-formats).
* 단일 게재를 만들면 Adobe Campaign에서 사용할 형식을 자동으로 검색합니다. 참조: [이 섹션](#designing-a-delivery-for-all-formats).

### 일본어 형식에 대한 특정 게재 디자인 {#designing-a-specific-delivery-for-japanese-formats}

두 개의 게재, 즉 일본어 모바일에서 읽을 수 있는 게재와 표준 이메일 형식을 사용하는 수신자용 게재를 포함하는 워크플로우를 만들 수 있습니다.

이렇게 하려면 **[!UICONTROL Split]** 워크플로우에서 활동을 만들고 일본어 이메일 형식(데코 메일, 데코 메일 및 데코 메일)을 필터링 조건으로 정의합니다.

![](assets/deco-mail_08.png)

![](assets/deco-mail_07.png)

### 모든 형식에 대한 게재 디자인 {#designing-a-delivery-for-all-formats}

Adobe Campaign이 도메인(이메일 형식이 정의된 프로필)에 따라 형식을 동적으로 관리하는 경우 **[!UICONTROL Unknown]**, **[!UICONTROL HTML]** 또는 **[!UICONTROL Text]** )을 클릭하여 모든 수신자에게 동일한 게재를 보낼 수 있습니다.

일본어 모바일의 사용자에게 표준 수신자와 마찬가지로 메시지 연락처가 올바르게 표시됩니다.

>[!IMPORTANT]
>
>각 일본어 전자 메일 형식(데코 메일, 데코 메일 및 데코 메일)과 관련된 특수 기능을 준수해야 합니다. 제한 사항에 대한 자세한 내용은 다음을 참조하십시오. [이 섹션](#limitations-and-recommendations).
